Kitchensink on OpenShift
=========================

This is the kitchensink JBoss Quickstart app.  You can find more info @ https://docs.jboss.org/author/display/AS71/Kitchensink+quickstart

Running on OpenShift
--------------------

Create an account at http://openshift.redhat.com/

Create a jbossas-7 application

    rhc app create -a kitchensink -t jbossas-7 --from-code git://github.com/openshift/kitchensink-example.git

That's it, you can now checkout your application at:

    http://kitchensink-$namespace.rhcloud.com

PostgreSQL as a backend
-----------------------
By default, this quickstart uses H2 as the backend, but you may use
PostgreSQL.

To do this, add PostgreSQL cartridge to your application:

    rhc cartridge add postgresql-8.4 -a kitchensink

Edit `src/main/resources/META-INF/persistence.xml` so that the data
source points to `java:jboss/datasources/PostgreSQLDS`:

    <jta-data-source>java:jboss/datasources/PostgreSQLDS</jta-data-source>

Commit this change, and push.
