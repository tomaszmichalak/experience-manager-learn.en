---
title: Trigger AEM workflow on HTM5 Form Submission
seo-title:Trigger AEM Workflow on HTML5 Form Submission
description: Continue filling mobile form in offline mode and submit mobile form to trigger AEM workflow
seo-description: Continue filling mobile form in offline mode and submit mobile form to trigger AEM workflow
feature: mobile-forms
topics: development
audience: developer
doc-type: article
activity: implement
version: 6.4,6.5
---

# Handle PDF Submission

In this part we will create a simple servlet to handle the pdf submission from Acrobat/Reader. This servlet is deployed on the AEM publish instance. This servlet will make a POST call to a servlet running in an AEM author instance. The servlet running in AEM author instance will then save the submitted data as a nt:file node in the crx repository of the AEM instance.

The following is the code of the servlet which handles the PDF submission. In this servlet we make a POST call to a servlet mounted on **/bin/startworkflow
** in a AEM instance. This servlet saves the form data in the crx repository.

```java{.line-numbers}

package com.aemforms.handlepdfsubmission.core.servlets;
import java.io.ByteArrayOutputStream;
import java.io.IOException;
import java.io.UnsupportedEncodingException;
import java.nio.charset.StandardCharsets;
import java.util.ArrayList;
import java.util.List;
import javax.servlet.Servlet;
import javax.servlet.ServletInputStream;
import javax.servlet.ServletOutputStream;

import org.apache.http.NameValuePair;
import org.apache.http.client.ClientProtocolException;
import org.apache.http.client.entity.UrlEncodedFormEntity;
import org.apache.http.client.methods.HttpPost;
import org.apache.http.impl.client.CloseableHttpClient;
import org.apache.http.impl.client.HttpClients;
import org.apache.http.message.BasicNameValuePair;
import org.apache.sling.api.SlingHttpServletRequest;
import org.apache.sling.api.SlingHttpServletResponse;
import org.apache.sling.api.servlets.SlingAllMethodsServlet;
import org.osgi.service.component.annotations.Component;
import org.slf4j.Logger;
import org.slf4j.LoggerFactory;
@Component(service={Servlet.class}, property={"sling.servlet.methods=post", "sling.servlet.paths=/bin/handlepdfsubmit"})
public class HandlePDFSubmission extends SlingAllMethodsServlet {

private static Logger logger = LoggerFactory.getLogger(HandlePDFSubmission.class);
protected void doPost(SlingHttpServletRequest request,SlingHttpServletResponse response)
{
ByteArrayOutputStream result = new ByteArrayOutputStream();
try {
        ServletInputStream is = request.getInputStream();
        byte[] buffer = new byte[1024];
        int length;
        while ((length = is.read(buffer)) != -1) {
            result.write(buffer, 0, length);
    }
    logger.debug(result.toString(StandardCharsets.UTF_8.name()));
    } catch (IOException e1) {
        e1.printStackTrace();
    }
    HttpPost postReq = new HttpPost("http://localhost:4502/bin/startworkflow");
    postReq.addHeader("Authorization", "Basic YWRtaW46YWRtaW4=");
    CloseableHttpClient httpClient = HttpClients.createDefault();
    List<NameValuePair> urlParameters = new ArrayList<NameValuePair>();
    logger.debug("added url parameters");
try {
        urlParameters.add(new BasicNameValuePair("xmlData", result.toString(StandardCharsets.UTF_8.name())));
        postReq.setEntity(new UrlEncodedFormEntity(urlParameters));
        httpClient.execute(postReq);
        logger.debug("Sent request to author instance");
        ServletOutputStream sout = response.getOutputStream();
        sout.print("Your form was successfully submitted");
    } catch (UnsupportedEncodingException e) {
        e.printStackTrace();
    } catch (ClientProtocolException e) {
        e.printStackTrace();
    } catch (IOException e) {
        e.printStackTrace();
    }


}
}

```

## Store the submitted data in crx repository

The next step is to store the submitted data in the crx repository. The servlet mounted on /bin/startworkflow saves the submitted data. Following is the code

```java{.line-numbers}
import java.io.BufferedReader;
import java.io.ByteArrayInputStream;
import java.io.IOException;
import java.io.InputStream;
import java.io.InputStreamReader;
import java.util.UUID;

import javax.jcr.Binary;
import javax.jcr.Node;
import javax.jcr.RepositoryException;
import javax.jcr.Session;
import javax.servlet.Servlet;
import javax.servlet.ServletOutputStream;

import org.apache.sling.api.SlingHttpServletRequest;
import org.apache.sling.api.SlingHttpServletResponse;
import org.apache.sling.api.resource.Resource;
import org.apache.sling.api.servlets.SlingAllMethodsServlet;
import org.osgi.service.component.annotations.Component;
import org.osgi.service.component.annotations.Reference;
import org.slf4j.Logger;
import org.slf4j.LoggerFactory;

import com.mergeandfuse.getserviceuserresolver.GetResolver;
@Component(service={Servlet.class}, property={"sling.servlet.methods=get", "sling.servlet.paths=/bin/startworkflow"})
public class StartWorkflow extends SlingAllMethodsServlet {
@Reference
GetResolver getResolver;
private static Logger logger = LoggerFactory.getLogger(StartWorkflow.class);
protected void doPost(SlingHttpServletRequest request,SlingHttpServletResponse response)
{
String xmlData = null;
System.out.println("in start workflow");
response.setContentType("text/html;charset=UTF-8");
if(request.getParameter("xmlData")!=null)
{
    logger.debug("The form was submitted from Acrobat/Reader");
        xmlData = request.getParameter("xmlData");
    System.out.println("in start workflow"+xmlData);
}
else {
    logger.debug("Mobile Form submission");
    StringBuffer stringBuffer = new StringBuffer();
    String line = null;
    try {
        InputStreamReader isReader = new InputStreamReader(request.getInputStream(), "UTF-8");
        BufferedReader reader = new BufferedReader(isReader);
        while ((line = reader.readLine()) != null)
            stringBuffer.append(line);
    } catch (Exception e) {
        logger.debug("Error"+e.getMessage());
    }
    xmlData = new String(stringBuffer);
}
Resource r = getResolver.getFormsServiceResolver().getResource("/content/pdfsubmissions");
Session session = r.getResourceResolver().adaptTo(Session.class);
logger.debug("Got reosurce pdfsubmissions"+r.getPath());
UUID uidName = UUID.randomUUID();
Node xmlDataFilesNode = r.adaptTo(Node.class);
InputStream is = new ByteArrayInputStream(xmlData.getBytes());
Binary binary;
try {
    Node xmlFileNode = xmlDataFilesNode.addNode(uidName.toString(),"nt:file");
    logger.debug("Added nt file node");
    Node jcrContent = xmlFileNode.addNode("jcr:content","nt:resource");
    logger.debug("Added jcr content");
    binary = session.getValueFactory().createBinary(is);
    jcrContent.setProperty("jcr:data", binary);
    session.save();
} catch (RepositoryException e) {
    // TODO Auto-generated catch block
    e.printStackTrace();
}



response.setContentType("text/plain;charset=UTF-8");
try {
    ServletOutputStream sout = response.getOutputStream();
    sout.print("Your form was successfully submitted");
} catch (IOException e) {
    // TODO Auto-generated catch block
    e.printStackTrace();
}


}
}



```

A workflow launcher is configured to trigger every time a new resource of type nt:file is created under the content/pdfsubmissions node. This workflow will create non-interactive or a static pdf by merging the submitted data with the xdp template. The generated pdf is then assigned to a user for review and approval.
To store the submitted data under /content/pdfsubmissions node, we make use of GetResolver service allows us to save the submitted data using the fd-service system user which is available in every AEM Forms installation. 
 
