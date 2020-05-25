# lxc-jboss_eap-helloworld
Containerized EAP with helloworld deploy

To install:

1. download docker files to a directory (e.g., demo)
2. create a directory 'files' inside of demo (demo/files) <br/>
   <code>mkdir demo</code>
3. download required zips <br/>
   a. JBoss EAP 7.2.0 from Red Hat <br/>
      Download zip from https://access.redhat.com/jbossnetwork/restricted/listSoftware.html?downloadType=distributions&product=appplatform&version=7.2 <br/>
   b. JBoss EAP Quickstarts from Red Hat<br/>
      <code>wget https://github.com/jboss-developer/jboss-eap-quickstarts/archive/7.2.0.GA.zip </code><br/>
   c. Apache Maven - <br/>
      <code>wget https://apache.mirrors.lucidnetworks.net/maven/maven-3/3.6.3/binaries/apache-maven-3.6.3-bin.zip </code><br/>
4. Place them all in demo/files
5. Go to demo directory
6. Build the image and save to built in image registry<br/>
   <code>podman build -t eap_helloworld .</code>
7. Deploy image<br/>
   <code>podman run -d --rm -p 9990:9990 -p 9991:8080 eap_helloworld</code>
8. open firewall ports<br/>
   <code>firewall-cmd --add-port=9990/tcp --add-port=9991/tcp</code>
9. with your browser (firefox, chrome, etc.), goto<br/>
   a. Management Console - http://localhost:9990/<br/>
   b. HelloWorld Demo    - http://localhost:9991/<br/>
