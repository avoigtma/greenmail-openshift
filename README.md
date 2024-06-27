# greenmail-openshift

Build and deploy [GreenMail][greenmail_project_site] on OpenShift.

## Greenmail

From the [GreenMail][greenmail_project_site] ReadMe:

> GreenMail allows developers to test email-based applications, services or systems without access to a live mail server.
Developers can send, receive, and verify emails by embedding GreenMail in a unit test or running it as a standalone container.
GreenMail acts as a virtual (mocking/sandbox) mail server and supports common mail protocols SMTP, IMAP and POP3.

References: 

* [Greenmail Project site][greenmail_project_site]
* [Greenmail Github Repo][greenmail_github_site]

## Build for OpenShift

* Create a custom "build" image based upon RHEL UBI8
    * add Maven 3.9.6 (as Greenmail requires Maven 3.9.x which is not yet available in RHEL 8/9 at time of this writing
    * add OpenJDK-11 for building
    * build Greenmail from the source
* Create Greenmail Runtime Container Image based upon Red Hat 'ubi8/openjdk-11-runtime' base image.


## Deploy

```shell
oc login ...
oc new-project greenmail
oc apply -f openshift
```


[greenmail_project_site]: https://greenmail-mail-test.github.io/greenmail/
[greenmail_github_site]: https://github.com/greenmail-mail-test/greenmail