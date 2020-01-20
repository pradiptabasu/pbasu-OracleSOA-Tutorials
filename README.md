# pbasu-OracleSOA-Tutorials

__**Processing No Namespace XML Messages SOA 11g**__
* http://sathyam-soa.blogspot.com/2013/11/processing-no-namespace-xml-messages.html
* http://soacrux.blogspot.com/2010/12/processing-xml-input-without-namespace.html
* 
* 
* 

* https://technology.amis.nl/2015/11/27/processing-large-xml-files-in-the-soa-suite/
* http://www.ateam-oracle.com/rest-adapter-and-json-translator-in-soaosb-12-1-3-2
* http://yatanveersingh.blogspot.com/2010/06/reading-xml-file-using-file-adapter-in.html
* 
* 

__**Dynamic Credential & Dynamic Endpoint**__
* https://www.baigzeeshan.com/2015/10/how-to-pass-dynamic-credentials-to-web.html
* https://www.oracle.com/technetwork/topics/soa/dynamic-endpoints-100390.html
* http://oraclesoasuitetips.blogspot.com/2014/08/dynamically-setting-csf-key.html
* https://subscription.packtpub.com/book/application_development/9781849683883/10/ch10lvl1sec70/adding-keys-to-a-credential-store
* https://community.oracle.com/thread/2622139
* http://soa-howto.blogspot.com/2008/09/how-to-set-security-credentials.html
* http://ofmxperts.blogspot.com/2011/12/how-to-set-security-credentials.html
* https://dzone.com/articles/get-credential-store-framework-key-inside-soa-comp
* http://biemond.blogspot.com/2010/08/http-basic-authentication-with-soa.html
* https://subscription.packtpub.com/book/application_development/9781849683883/10/ch10lvl1sec71/invoking-an-http-basic-secured-web-service
* https://subscription.packtpub.com/book/application_development/9781849683883/10/ch10lvl1sec67/restricting-a-composite-to-authenticated-users-with-http-basic-security
* https://stackoverflow.com/questions/47081479/bpel-12c-call-webservices-with-basic-authentication
* https://blogs.oracle.com/ardaeralp/bpel-calling-web-services-with-http-basic-authentication
* https://community.oracle.com/thread/1013997
* https://www.albinsblog.com/2012/06/invoking-web-service-from-composite.html#.XMiRE2gzbIU
* http://oraclesoasuitetips.blogspot.com/2014/08/dynamically-setting-csf-key.html
* 
* 

__**Dynamic Variable values which changes with environment**__
* https://sswaro.wordpress.com/handle-dynamic-parameter-using-bpel-preference-property/
* http://learn-oraclesoa.blogspot.com/2013/05/setting-and-getting-preferences-soa.html
* https://technology.amis.nl/2008/01/06/oracle-bpel-process-manager-most-efficient-way-to-manage-dynamic-process-level-cross-instance-data/
* https://intelligentpathways.com.au/blog/soa-environment-reference-deployment-approaches/
* https://osb11g.blogspot.com/2016/06/soa-using-oragetpreference-in-bpel.html
* 
* 

__**Opaque Schema**__
* https://technology.amis.nl/2014/08/06/opaque-does-not-mean-just-pass-anything-in-it-has-to-be-base64-jca-adapters/
* https://redthunder.blog/2016/11/22/teaching-how-to-use-the-oracle-osbsoa-jms-adapter-bpel-and-mediator/
* https://blogs.oracle.com/fusionmiddlewaresupport/jms-step-4-how-to-create-an-11g-bpel-process-which-writes-a-message-based-on-an-xml-schema-to-a-jms-queue-v2
* http://oraclefuzion.blogspot.com/2011/02/reading-opaque-data-in-bpel.html
* https://www.tavant.com/blog/osb-tip-proxy-service-which-can-take-any-xml-data-any-jms-queue-oracle-service-bus
* 
* 

__** One-way & Two-way SSL Setup**__
* https://technology.amis.nl/2014/08/17/soa-suite-12c-configuring-gmail-as-the-inbound-email-provider-for-ums-imap-ssl/
* https://technology.amis.nl/2014/08/05/setup-gmail-as-mail-provider-for-soa-suite-12c-configure-smtp-certificate-in-trust-store/
* https://technology.amis.nl/2019/03/24/running-apache-kafka-on-minikube/
* https://javaoraclesoa.blogspot.com/2017/05/oracle-soa-suite-two-way-ssl-with-tls12.html
* https://svgonugu.com/2015/03/06/service-bus-12c-outbound-ssl/
* 
* 
openssl s_client -connect imap.gmail.com:993 > gmail-imap-cert.pem
Open the file you retrieved with OpenSSL – gmail-imap-cert.pem in my case – in an editor (such as vi).

Remove all the lines before the line that says —–BEGIN CERTIFICATE—– – but leave this line itself! Also remove all lines after the line with —–END CERTIFICATE—– but again, leave this line itself. Save the resulting file, for example as gmail-imp-certificate.txt (but you can pick any name you like).

WebLogic (on which SOA Suite is running) out of the default installation uses a special keystore. It does not use the cacerts store that is installed with the JDK or JRE but instead uses a file called DemoTrust.jks and typically located at %WL_HOME/server/lib/DemoTrust.jks. This trust store is “injected” into the JVM when the WebLogic domain is started: “-Djavax.net.ssl.trustStore=/opt/oracle/middleware12c/wlserver/server/lib/DemoTrust.jks”. We have the option of removing this start up parameter: remove “-Djavax.net.ssl.trustStore=%WL_HOME%\server\lib\DemoTrust.jks” in setDomainEnv.cmd  and then add the certificates to the default Java keystore (cacerts) or, the easier option, we can add the certificate to the DemoTrust keystore that WebLogic uses.

The command for doing this, looks as follows, in my environment at least:

/usr/java/latest/jre/bin/./keytool -import -alias imap.gmail.com -keystore /opt/oracle/middleware12c/wlserver/server/lib/DemoTrust.jks -file /var/log/weblogic/gmail-imap-certificate.txt


The default password for the keystore is DemoTrustKeyStorePassPhrase.

You will be asked explicitly whether you trust this certificate [and are certain about adding it to the keystore]. Obviously you will have to type y in order to confirm the addition to the keystore:







# __***REST Adapter SOA calling HTTPS***__
Please setup the certificates in both the demotrust.jks and trust stripes in EM console
* https://stackoverflow.com/questions/38232552/oracle-bpel-java-8u92-invoking-rest-service-using-https-gives-ssl-handshake-ex
* https://serverfault.com/questions/503751/certificate-verification-error-when-sending-a-service-request-from-weblogic
OK. It will sound wierd but it will work. We have the same SOA 12c setup but we are using Standard Java Trust keystore for managed SOA server.

I can see that you have modified setDomainEnv.sh to specify /u01/data/keystores/truststore.jks as your keystore.

In theory if the root cert is there in the cacerts in my case and truststore.jks in your case it should work. I can confirm that the SOAP services work fine with the keystore.

Somehow invoking REST service through REST adapter was failing due to cert error, same as yours.

Here's what made it to work:
Login to EM
Weblogic Domain -> Security -> Keystore
Select System (stripe) -> trust -> Hit the manage button
Here import the root cert of geotrustrootca.
Bounce the SOA server. Test your service. It should work fine.

What I dont understand is: System (stripe) -> trust = This is preconfigured as a demo trust store when you configure a domain. I have already change the keystore setting for managed server to use cacerts. Somehow it looks like this kss trust store is still referenced somewhere. The question is where?

Do share just in case you figure this one out. In the meantime the solution will get you going.





# DNS Checker
* https://dns.google.com/











https://stackoverflow.com/questions/47447734/how-to-get-the-ip-address-or-range-of-a-firebase-functions
https://groups.google.com/forum/#!msg/firebase-talk/eE6kAqDApU8/hgCcTIORCQAJ
https://stackoverflow.com/questions/27105700/how-to-setup-ec2-security-group-to-allow-working-with-firebase



https://www.quora.com/How-can-the-Amazon-API-Gateway-be-set-up-to-whitelist-specified-IP-addresses-for-access-to-AWS-Lambda




https://stackoverflow.com/questions/45529020/android-fcm-what-are-the-ips-and-ports-for-firewall
https://www.dnsqueries.com/en/dns_lookup.php
https://dnschecker.org/
https://ipinfo.io/AS15169
https://bgp.he.net/AS15169
https://serverfault.com/questions/535936/configuring-firewall-for-google-cloud-messaging-asn-15169
https://success.trendmicro.com/solution/1060693
https://firebase.google.com/docs/cloud-messaging/concept-options
https://www.site24x7.com/community/aws-security-groups-whitelisting
https://docs.aws.amazon.com/cli/latest/userguide/cli-services-ec2-sg.html
https://webmasters.stackexchange.com/questions/107411/how-do-i-whitelist-a-user-with-a-dynamic-ip-address-in-godaddy-plesk
https://serverfault.com/questions/187231/accessing-ip-restricted-server-from-dynamic-ip
https://community.akamai.com/customers/s/article/The-UGLY-Truth-Behind-the-Practice-of-IP-Whitelisting?language=en_US
https://securebox.comodo.com/whitelisted/
https://serverfault.com/questions/919090/aws-lambda-function-to-dynamically-add-and-remove-public-ip-to-security-group
https://www.rubix.nl/blogs/how-configure-aws-lambda-functions-use-outbound-fixed-ip/
https://medium.com/financial-engines-techblog/aws-lambdas-with-a-static-outgoing-ip-5174a1e70245
https://aws.amazon.com/blogs/security/how-to-automatically-update-your-security-groups-for-amazon-cloudfront-and-aws-waf-by-using-aws-lambda/
https://www.oodlestechnologies.com/blogs/Run-AWS-Lambda-function-with-Static-IP-address/






SSL for the FCM in SOA
https://superuser.com/questions/97201/how-to-save-a-remote-server-ssl-certificate-locally-as-a-file
https://pki.goog/
http://www.freetutorialssubmit.com/compare-ssl-certificate-and-key-matches-with-openssl/1519
https://www.digicert.com/csr-ssl-installation/weblogic-8-12x.htm
https://blogs.oracle.com/jtc/installing-trusted-certificates-into-a-java-keystore
https://fusionmwgang.wordpress.com/2016/09/01/importing-certificates-in-weblogic-server/
http://prasaddomala.com/what-is-ssl-and-how-to-configure-ssl-keystores-certificates-for-oracle-weblogic-server/
https://r12siebel.wordpress.com/2011/09/20/demoidentity-jks-and-demotrust-jks-password/
http://oraclmiddleware.blogspot.com/2015/07/weblogic-demotrust-demoidentity-default.html
http://prasaddomala.com/what-is-ssl-and-how-to-configure-ssl-keystores-certificates-for-oracle-weblogic-server/
http://www.ateam-oracle.com/2-way-ssl-between-soa-and-osb
https://serverfault.com/questions/503751/certificate-verification-error-when-sending-a-service-request-from-weblogic
https://dev.tapjoy.com/faq/how-to-find-sender-id-and-api-key-for-gcm/
https://success.trendmicro.com/solution/1060693
https://docs.aws.amazon.com/pinpoint/latest/apireference/apps.html
https://www.site24x7.com/community/aws-security-groups-whitelisting
https://serverfault.com/questions/187231/accessing-ip-restricted-server-from-dynamic-ip
https://www.albinsblog.com/2014/03/wildcard-ssl-hostnameverifier-in.html#.XPpgBlwzbIU
https://thesmartpanda.com/weblogic-wildcard-host-name-verification/


https://middlewaresupport.wordpress.com/tag/hostname-verification/
http://weblogic-wonders.com/weblogic/2010/01/28/troubleshooting-ssl-issues/



 Modify the wlst.sh script by adding these:

CONFIG_JVM_ARGS="-Dweblogic.security.SSL.ignoreHostnameVerification=true
-Dweblogic.security.TrustKeyStore=DemoTrust"
export CONFIG_JVM_ARGS


-Dweblogic.security.SSL.ignoreHostnameVerification=true
-Dweblogic.security.SSL.enforceConstraints
-Dweblogic.security.SSL.trustedCAKeyStore 
-Dweblogic.security.SSL.nojce



These parameters were already added in setDomainEnv.sh:



How to repoint the SOA database repository using chghost introduced in 12.2.1.3? (Doc ID 2414575.1)


NOTE:1340777.1 - Interoperability Between Oracle WebLogic Server 11g and Microsoft.NET WCF 4.0 Using Secure Web Services - Part 1
NOTE:1340778.1 - Interoperability Between Microsoft.NET WCF 4.0 and Oracle WebLogic Server 11g Using Secure Web Service, Part 2
How to set Hostname Verification when BPEL invoke SSL SOAP request. (Doc ID 2290896.1)
Oracle E-Business Suite Integrated SOA Gateway Release Notes for Release 12.2.3 (Doc ID 1603897.1)


NOTE:1542834.1 - Accessing Weblogic via HTTPS Fails : SSL Configured to Terminate at OHS - FATAL Alert : BAD_CERTIFICATE in managed server log
NOTE:1092218.1 - WLS 10.3.x - Unable To Invoke Remote Web Service Due To Error: "Bad_certificate Fatal Error"
NOTE:2007773.1 - Error: javax.net.ssl.SSLException: Received Fatal Alert: bad_certificate When Starting the P6 Managed Server
NOTE:1557876.1 - How to Configure Web Services
NOTE:1311464.1 - javax.net.ssl.SSLKeyException:Fatal Alert:Bad_certificate Received When * found in Certificate Subject
NOTE:1474989.1 - How To Configure WebLogic Server To Support Wildcard Certificates
NOTE:1072744.1 - WebCenter/SOA Integration: Unable to Connect to SOA Server Due to FATAL Alert:BAD_CERTIFICATE - A Corrupt or Unuseable Certificate was Received.
NOTE:1488379.1 - SOA 11g: SSL Error in JDeveloper During Deployment, 'Received Fatal Alert: Bad_certificate'
NOTE:1225455.1 - E-SSL: Frequently Asked Questions about SSL Certificates on WebLogic

A-Team Blog Reference for SOA Suite, BPM and OSB (Doc ID 1566562.1)

How to setup SOA CS to use CA verified SSL certificates? (Doc ID 2419512.1)

How to Terminate SSL at LBR, Another HTTP Server, Web Cache or OHS 11g - Including Steps for WLS Plugin (mod_wl_ohs) (Doc ID 1569732.1)

SOA 12c: Unable to find a valid certification path to the requested target when invoking an SSL service (Doc ID 1922364.1)

https://stackoverflow.com/questions/38232552/oracle-bpel-java-8u92-invoking-rest-service-using-https-gives-ssl-handshake-ex

https://www.avioconsulting.com/blog/soa-suite-12c-and-opss-keystore-service





Changing Oracle 11G SOA Suite Data Source (Repository) Passwords (Doc ID 1339818.1)
Monitoring, Administering and Troubleshooting Oracle SOA Suite and ADF (Doc ID 1351257.1)
Diagnosing oracle.xml.parser.v2.XMLParseException in the SOA Suite (Doc ID 1485583.1)
How to determine if Local Optimization is enabled in Oracle SOA Suite 12c (Doc ID 2081255.1)






# SSL related Links
* https://serverfault.com/questions/187231/accessing-ip-restricted-server-from-dynamic-ip
* https://thesmartpanda.com/weblogic-wildcard-host-name-verification/
* https://middlewaresupport.wordpress.com/tag/hostname-verification/
* http://weblogic-wonders.com/weblogic/2010/01/28/troubleshooting-ssl-issues/
* https://www.techsupper.com/2017/01/hostname-verification-failed.html
* https://khassoablog.wordpress.com/author/khasim7/page/22/
* https://erikwramner.wordpress.com/2011/10/31/ssl-issues-with-jdeveloper/
* https://svgonugu.com/tag/ssl/
* http://middlewaremagic.com/weblogic/?p=2887
* 
* 
* 



__** Flow trace Instance assosiation **__
* https://community.oracle.com/thread/4176784
* https://blog.darwin-it.nl/2018/09/split-your-flow-trace-in-bpel.html
* https://blog.darwin-it.nl/2018/09/split-your-flow-trace-in-bpel.html
* Decouple child instances from parent instance tree in SOA 11g (Doc ID 2278472.1)
* https://beatechnologies.wordpress.com/tag/oracle-soa-suite-11g/
* https://www.avioconsulting.com/blog/five-tools-debugging-oracle-soa-suite
* https://technology.amis.nl/2014/06/26/soa-suite-12c-first-look-at-sca-composite-features/
* https://dzone.com/articles/running-mediator-instances
* https://www.ateam-oracle.com/retrieve-bpel-payload-from-the-database-2
* https://docs.oracle.com/middleware/1221/osb/develop/GUID-560C6AB9-5FA3-4EC2-8D5E-7D27D16F4BFC.htm#OSBDV1753
* https://docs.oracle.com/middleware/11119/osb/develop/bpelpm.htm
* http://thoughtmate.blogspot.com/2010/11/ora-bpel-thru-osb-associating-message.html
* https://www.ateam-oracle.com/how-to-find-purgeable-instances-in-soabpm-12c
* https://www.orafaq.com/aggregator/sources/278?page=1
* https://docs.oracle.com/en/middleware/soa-suite/soa/12.2.1.3/administer/tracking-business-flow-instances.html#GUID-A6CAAB62-CD73-4D52-8E80-0B618B3C5B82
* https://tungsten.io/tracing-flows-through-virtual-networks-and-service-instances-in-openstack-and-opencontrail/
* https://thecattlecrew.net/2013/11/12/monitoring-large-flow-traces-with-oracle-soa-suite/
* 
* 
* 
* 
* 
* 
* 
* 
* 
* 
* 
* 
* 
* 
* 
* 
* 
* 
* 
* 
* 
* 




# SOA Async Process
* http://soacrux.blogspot.com/2012/03/invoking-soa11g-composite-using-direct.html
* https://javaoraclesoa.blogspot.com/2012/08/issues-and-solutions-when-testing-and.html
* https://javaoraclesoa.blogspot.com/2016/02/asynchronous-interaction-in-oracle-bpel.html
* http://ofmdeveloper.blogspot.com/2012/03/difference-between-async-sync-bpel.html
* https://oraclesoasolution.blogspot.com/2016/12/soa-11g-cloning.html?m=1
* http://soa-bpel-esb.blogspot.com/2010/06/
* https://www.mtroyal.ca/_ocsh/help/topics/help_urm_setup_urm_setup_html_help_rmdsg/help/cs_admin/cs_sysadmin_html_help/c05_security014.htm?tp=true&locale=en
* http://tomhofte.blogspot.com/2009/
* 
* 
* 
* 
* 
* 
* 
* 
* 
* 
* 
* 
