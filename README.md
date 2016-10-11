# Deployment-service-servlet-received-file-download-request-for-file-security-SerializedSystemIni.dat

ERROR:


[grd@dayrhe security]$<Jan 14, 2015 8:34:01 PM EST> <Warning> <DeploymentService> <BEA-290074> <Deployment service servlet received file download request for file "security/SerializedSystemIni.dat". The file may exist, but download of this file is not allowed.>
<Jan 14, 2015 8:34:01 PM EST> <Warning> <DeploymentService> <BEA-290065> <Deployment service servlet encountered an Exception while handling the deployment datatransfer message for request id "13,349,318,400,352,671" from server "CodingQAEECAN06". Exception is: "java.lang.IllegalArgumentException: files list is empty
        at weblogic.deploy.service.datatransferhandlers.MultipartHelper.constructFilesHeaderValue(MultipartHelper.java:121)
        at weblogic.deploy.service.datatransferhandlers.MultipartResponse.setupMultiFileResponse(MultipartResponse.java:68)
        at weblogic.deploy.service.datatransferhandlers.MultipartResponse.init(MultipartResponse.java:36)
        at weblogic.deploy.service.datatransferhandlers.MultipartResponse.<init>(MultipartResponse.java:31)
        at weblogic.deploy.service.internal.transport.http.DeploymentServiceServlet.handleDataTransferRequest(DeploymentServiceServlet.java:901)
        at weblogic.deploy.service.internal.transport.http.DeploymentServiceServlet.internalDoPost(DeploymentServiceServlet.java:252)
        at weblogic.deploy.service.internal.transport.http.DeploymentServiceServlet.access$000(DeploymentServiceServlet.java:85)
        at weblogic.deploy.service.internal.transport.http.DeploymentServiceServlet$1.run(DeploymentServiceServlet.java:224)
        at weblogic.security.acl.internal.AuthenticatedSubject.doAs(AuthenticatedSubject.java:363)
        at weblogic.security.service.SecurityManager.runAs(SecurityManager.java:146)
        at weblogic.deploy.service.internal.transport.http.DeploymentServiceServlet.doPost(DeploymentServiceServlet.java:221)
        at javax.servlet.http.HttpServlet.service(HttpServlet.java:751)
        at javax.servlet.http.HttpServlet.service(HttpServlet.java:844)
        at weblogic.servlet.internal.StubSecurityHelper$ServletServiceAction.run(StubSecurityHelper.java:280)        at weblogic.servlet.internal.StubSecurityHelper$ServletServiceAction.run(StubSecurityHelper.java:254)

Truoubleshooting:


Take md5sum of SerializedSystemIni.dat file in both the machines in the domain path.

copy the file from Admin machine to other host machine.


Action performed:

[grd@dayrhe security]$ll
total 44
-rwxrwxrwx 1 grd grdaduser  4114 Jan 14 18:17 DefaultAuthenticatorInit.ldift
-rwxrwxrwx 1 grd grdaduser  2398 Jan 14 18:17 DefaultRoleMapperInit.ldift
-rwxrwxrwx 1 grd grdaduser  2510 Jan 14 18:17 DemoIdentity.jks
-rwxrwxrwx 1 grd grdaduser    64 Jan 14 18:17 SerializedSystemIni.dat
-rwxrwxrwx 1 grd grdaduser 22654 Jan 14 18:17 XACMLRoleMapperInit.ldift
[grd@dayrhe security]$md5sum SerializedSystemIni.dat
7622f4d0ac36e306486dd20f7e63a887  SerializedSystemIni.dat
[grd@dayrhegrdd007 security]$hostname -i
dayrhed
[grd@dayrhe security]$scp -r SerializedSystemIni.dat grd@10.7.35.128:/
[grd@dayrhe security]$pwd
/opt/grd/Oracle12.1.3/user_projects/domains/CodingQAEECAN/security
[grd@dayrhe security]$scp -r SerializedSystemIni.dat 
grd@dayrhe://opt/grd/Oracle12.1.3/user_projects/domains/CodingQAEECAN/security/
grd@dayrhe's password:
SerializedSystemIni.dat                                                                                                               100%   64     0.1KB/s   00:00
[grd@dayrhe security]$pwd
/opt/grd/Oracle12.1.3/user_projects/domains/CodingQAEECAN/security

