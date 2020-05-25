# lxc-jboss_eap-helloworld
Containerized EAP with helloworld deploy

To install:

1. download docker files to a directory (e.g., demo)
2. create a directory 'files' inside of demo (demo/files)
   mkdir demo
3. download required zips
   a. JBoss EAP 7.2.0 from Red Hat
      Download zip from https://access.redhat.com/jbossnetwork/restricted/listSoftware.html?downloadType=distributions&product=appplatform&version=7.2
   b. JBoss EAP Quickstarts from Red Hat
      wget https://github.com/jboss-developer/jboss-eap-quickstarts/archive/7.2.0.GA.zip
   c. Apache Maven - 
      wget https://apache.mirrors.lucidnetworks.net/maven/maven-3/3.6.3/binaries/apache-maven-3.6.3-bin.zip
4. Place them all in demo/files
5. Go to demo directory
6. Build the image and save to built in image registry
   podman build -t eap_helloworld .
7. Deploy image
   podman run -d --rm -p 9990:9990 -p 9991:8080 eap_helloworld
8. open firewall ports
   firewall-cmd --add-port=9990/tcp --add-port=9991/tcp
9. with your browser (firefox, chrome, etc.), goto
   a. Management Console - http://localhost:9990/
   b. HelloWorld Demo    - http://localhost:9991/
