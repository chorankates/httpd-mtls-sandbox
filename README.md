# httpd-mtls-sandbox
sandbox for testing httpd (apache2) mTLS configuration

## http://localhost:80 -> https://localhost:443

[000-default.conf](000-default.conf) is a modified version of [000-default.orig](000-default.orig) that contains settings that forces the redirect of all connections to :80 to redirect to :443, while :443 connections are internally proxied to :8000

### notes
  * `a2enmod proxy* ssl*` should be run to enable the relevant apache modules

  * these settings can be made in any `<VirtualHost>` declaration, using default for POC

  * sample `SSLCertificateFile` [certificate.pem](certificate.pem) and `SSLCertificateKeyFile` [key.pem](key.pem) provided, per existing config, will need to be placed in `/root/`

  * `SSLProtocol` should not be specified at this point, but `SSLEngine` does need to be on


## mTLS

TODO: flesh this out

## link dump

  * https://deliciousbrains.com/ssl-certificate-authority-for-local-https-development/

  * http://www.cafesoft.com/products/cams/ps/docs32/admin/ConfiguringApache2ForSSLTLSMutualAuthentication.html#Configuring_Apache_to_Require_a_Client_Certificate

  * https://httpd.apache.org/docs/current/mod/mod_ssl.html

  * https://www.ibm.com/support/knowledgecenter/en/SSMNED_5.0.0/com.ibm.apic.cmc.doc/task_apionprem_gernerate_self_signed_openSSL.html
