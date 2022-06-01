# Moqui Marble ERP

[![license](http://img.shields.io/badge/license-CC0%201.0%20Universal-blue.svg)](https://github.com/moqui/MarbleERP/blob/master/LICENSE.md)
[![build](https://travis-ci.org/moqui/MarbleERP.svg)](https://travis-ci.org/moqui/MarbleERP)
[![release](http://img.shields.io/github/release/moqui/MarbleERP.svg)](https://github.com/moqui/MarbleERP/releases)
[![commits since release](http://img.shields.io/github/commits-since/moqui/MarbleERP/v2.2.0.svg)](https://github.com/moqui/MarbleERP/commits/master)
[![downloads](http://img.shields.io/github/downloads/moqui/MarbleERP/total.svg)](https://github.com/moqui/MarbleERP/releases)

[![Discourse Forum](https://img.shields.io/badge/moqui%20forum-discourse-blue.svg)](https://forum.moqui.org)
[![Google Group](https://img.shields.io/badge/google%20group-moqui-blue.svg)](https://groups.google.com/d/forum/moqui)
[![LinkedIn Group](https://img.shields.io/badge/linked%20in%20group-moqui-blue.svg)](https://www.linkedin.com/groups/4640689)
[![Stack Overflow](https://img.shields.io/badge/stack%20overflow-moqui-blue.svg)](http://stackoverflow.com/questions/tagged/moqui)

Moqui Marble ERP is a planning and management application for businesses that produce goods and services, and sell to individuals (B2C) and organizations (B2B). 

This is a comprehensive ERP application rather than being focused on goods like POP Commerce ERP or services like HiveMind PM & Admin. Part of the reason for the combination is that goods oriented businesses also have projects and tasks to manage even if they don't sell them, and services oriented businesses also have equipment and supplies to manage even if they don't sell goods.

Moqui Marble ERP is designed around business activities in 3 categories by the primary roles in the system: Internal, Supplier, and Customer. These activities fit into high level business processes such as Procure to Pay (Supplier interactions) and Order to Cash (Customer interactions), and are combined to support a complete end to end flow.

### Build and Run Locally

To get and locally run the latest Marble ERP you'll need JDK 8 or later (OpenJDK or Oracle), and either a git client or you can
use the binary download link on GitHub.

Java can be downloaded here (make sure to use the Download button under the **JDK** column, NOT the under the JRE column):

<http://www.oracle.com/technetwork/java/javase/downloads/index.html>

The following instructions use the Gradle Wrapper to build. You can optionally download and install Gradle
(from <http://www.gradle.org/downloads>) and use **gradle** instead of **./gradlew** in the example commands.

To download Moqui/Mantle/MarbleERP source and build/run locally use the following steps:

#### Step 1: Download Moqui Framework

Zip: <https://github.com/moqui/moqui-framework/archive/master.zip>

Git: <https://github.com/moqui/moqui-framework.git>

From either source you should put the contents in a **moqui** directory for the next steps. If you use the Zip download
change the directory name from **moqui-framework-master** to **moqui**. If you clone the Git repository clone it into
a **moqui** directory.

#### Step 2: Download Marble ERP and Dependencies

This is easy with the dependency configuration per component, and the Gradle get component tasks. With Gradle Wrapper
you don't need to install Gradle separately to do this. The MarbleERP component is configured by default in the Moqui
addons.xml file, so just run:

    $ ./gradlew getComponent -Pcomponent=MarbleERP

If you downloaded the zip archive for Moqui Framework this will download the zip archives for MarbleERP and each
component it depends on. If you cloned from the git repository this will clone all components from their repositories.

#### Step 3: Build and Load Data

From the **moqui** directory run:

    $ ./gradlew load

This will build Moqui and load seed and demo data from all components into an embedded H2 database.

#### Step 4: Run Moqui

From the **moqui** directory run:

    $ java -jar moqui.war

#### Step 5: Access the Marble ERP applications

In a browser go to:

<http://localhost:8080/qapps/marble>

Use the button in the lower-left corner of the screen login as John Doe.

### Setup Commands Quick Reference

Java 8 JDK is required (OpenJDK or Oracle): <http://www.oracle.com/technetwork/java/javase/downloads/index.html>

Here are command line steps for initial checkout, setup, and run:

    $ git clone git@github.com:moqui/moqui-framework.git moqui
    $ cd moqui
    $ ./gradlew getComponent -Pcomponent=MarbleERP
    $ ./gradlew load
    $ java -jar moqui.war

Here are steps for a basic update (for development with clean out and rebuild of database):

    $ cd moqui
    $ ./gradlew cleanAll gitPullAll
    $ ./gradlew load
    $ java -jar moqui.war

To use the application, in a browser go to: <http://localhost:8080/qapps/marble>
