# Bowfolios

## Table of contents

-   [Overview](#overview)
-   [Mockups](#mockups)
-   [User Guide](#user-guide)
-   [Developer Guide](#developer-guide)
-   [Team](#team)

## Overview

Academic Panic is a web application for UH Manoa students to connect with their
peers to engage in more effective and collaborative learning with
- a study session planning system that can notify other students of,
- a course review and rating system,
- a "friends" system to connect students without disclosing sensitive
information,
- 

The goal of the project is as follows:
- provide UH Manoa students with a collaborative study/tutoring resource,
- encourage networking and community amongst UH Manoa students, and
- provide a platform for students to share honest [respectful] opinions about
courses that will be visible by all users.

## Technologies Used

Academic Panic is built upon the
[nextjs-application-template](https://ics-software-engineering.github.io/nextjs-application-template/),
which employs the following technologies:

- [React](https://reactjs.org/) for component-based UI implementation and
routing,
- [React Bootstrap](https://react-bootstrap.github.io/) as a CSS Framework for
UI design,
- [Next.js](https://nextjs.org/) as a web framework built on top of React with
additional structures, featuers, and optimization,
- [React Hook Form](https://www.react-hook-form.com/) for form development,
- [NextAuth.js](https://next-auth.js.org/) for user registration, authorization,
and authentication,
- [Sweet Alert](https://sweetalert.js.org/) for successful/failed database
updates, and
- [ESLint](http://eslint.org/) for consistent code quality using the [Next.js ESLint
Rules](https://nextjs.org/docs/app/building-your-application/configuring/eslint)
and the [AirBnB Javascript Style Guide](https://github.com/airbnb/javascript).

It also provides code that implements a variety of useful design
concepts, including:

-   Three primary collections (Profiles, Projects, Interests) as well as
    three "join" Collections (ProfilesInterests, ProfilesProjects, and
    ProjectsInterests) that implement many-to-many relationships between
    them.
-   Top-level index pages (Profiles, Interests, and Projects) that show
    how to manipulate these six collections in various ways.
-   Initialization code to define default Profiles, Interests, and
    Projects and relations between them.
-   A simple Filter page to illustrate how to perform simple queries on
    the database and display the results.
-   Use of Meteor Methods to illustrate how to simplify implementation
    of multiple collection updates.
-   Use of indexes to enforce uniqueness of certain fields in the
    collections, enabling them to serve as primary keys.
-   Authentication using the built-in Meteor accounts package along with
    Sign Up and Sign In pages.
-   Authorization examples: certain pages are public (Profiles,
    Projects, Interests), while other pages require login (AddProject,
    Filter).
-   Use of Meteor Assets to initialize the database (helpful when
    initialization exceeds settings file size limits).

## User Guide

This section provides a walkthrough of the Bowfolios user interface and
its capabilities.

TODO: FILL OUT LATER

## Developer Guide

This section provides information of interest to Meteor developers
wishing to use this code base as a basis for their own development
tasks.

### Installation

First, [install Meteor](https://www.meteor.com/install).

Second, visit the [Bowfolios application github
page](https://github.com/bowfolios/bowfolios), and click the "Use this
template" button to create your own repository initialized with a copy
of this application. Alternatively, you can download the sources as a
zip file or make a fork of the repo. However you do it, download a copy
of the repo to your local computer.

Third, cd into the bowfolios/app directory and install libraries with:

:::: {.language-plaintext .highlighter-rouge}
::: highlight
``` highlight
$ meteor npm install
```
:::
::::

Fourth, run the system with:

:::: {.language-plaintext .highlighter-rouge}
::: highlight
``` highlight
$ meteor npm run start
```
:::
::::

If all goes well, the application will appear at
<http://localhost:3000>.

### Application Design

Bowfolios is based upon
[meteor-application-template-react](https://ics-software-engineering.github.io/meteor-application-template-react/)
and
[meteor-example-form-react](https://ics-software-engineering.github.io/meteor-example-form-react/).
Please use the videos and documentation at those sites to better
acquaint yourself with the basic application design and form processing
in Bowfolios.

### Data model

As noted above, the Bowfolios data model consists of three "primary"
collections (Projects, Profiles, and Interests), as well as three "join"
Collections (ProfilesProjects, ProfilesInterests, and
ProjectsInterests). To understand this design choice, consider the
situation where you want to specify the projects associated with a
Profile.

Design choice #1: Provide a field in Profile collection called
"Projects", and fill it with an array of project names. This choice
works great when you want to display a Profile and indicate the Projects
it's associated with. But what if you want to go the other direction:
display a Project and all of the Profiles associated with it? Then you
have to do a sequential search through all of the Profiles, then do a
sequential search through that array field looking for a match. That's
computationally expensive and also just silly.

Design choice #2: Provide a "join" collection where each document
contains two fields: Profile name and Project name. Each entry indicates
that there is a relationship between those two entities. Now, to find
all the Projects associated with a Profile, just search this collection
for all the documents that match the Profile, then extract the Project
field. Going the other way is just as easy: to find all the Profiles
associated with a Project, just search the collection for all documents
matching the Project, then extract the Profile field.

Bowfolios implements Design choice #2 to provide pair-wise relations
between all three of its primary collections:

![](/images/data-model.png)

The fields in boldface (Email for Profiles, and Name for Projects and
Interests) indicate that those fields must have unique values so that
they can be used as a primary key for that collection. This constraint
is enforced in the schema definition associated with that collection.

## Initialization

The [config](https://github.com/bowfolios/bowfolios/tree/main/config)
directory is intended to hold settings files. The repository contains
one file:
[config/settings.development.json](https://github.com/bowfolios/bowfolios/blob/main/config/settings.development.json).

This file contains default definitions for Profiles, Projects, and
Interests and the relationships between them. Consult the walkthrough
video for more details.

The settings.development.json file contains a field called
"loadAssetsFile". It is set to false, but if you change it to true, then
the data in the file app/private/data.json will also be loaded. The code
to do this illustrates how to initialize a system when the initial data
exceeds the size limitations for the settings file.

### Quality Assurance

#### ESLint

BowFolios includes a
[.eslintrc](https://github.com/bowfolios/bowfolios/blob/main/app/.eslintrc)
file to define the coding style adhered to in this application. You can
invoke ESLint from the command line as follows:

:::: {.language-plaintext .highlighter-rouge}
::: highlight
``` highlight
meteor npm run lint
```
:::
::::

Here is sample output indicating that no ESLint errors were detected:

:::: {.language-plaintext .highlighter-rouge}
::: highlight
``` highlight
$ meteor npm run lint

> bowfolios@ lint /Users/philipjohnson/github/bowfolios/bowfolios/app
> eslint --quiet --ext .jsx --ext .js ./imports ./tests

$
```
:::
::::

ESLint should run without generating any errors.

It's significantly easier to do development with ESLint integrated
directly into your IDE (such as IntelliJ).

#### End to End Testing

BowFolios uses [TestCafe](https://devexpress.github.io/testcafe/) to
provide automated end-to-end testing.

The BowFolios end-to-end test code employs the page object model design
pattern. In the [bowfolios tests/
directory](https://github.com/bowfolios/bowfolios/tree/main/app/tests),
the file
[tests.testcafe.js](https://github.com/bowfolios/bowfolios/blob/main/app/tests/tests.testcafe.js)
contains the TestCafe test definitions. The remaining files in the
directory contain "page object models" for the various pages in the
system (i.e. Home, Landing, Interests, etc.) as well as one component
(navbar). This organization makes the test code shorter, easier to
understand, and easier to debug.

To run the end-to-end tests in development mode, you must first start up
a BowFolios instance by invoking
`meteor npm run start`{.language-plaintext .highlighter-rouge} in one
console window.

Then, in another console window, start up the end-to-end tests with:

:::: {.language-plaintext .highlighter-rouge}
::: highlight
``` highlight
meteor npm run testcafe
```
:::
::::

You will see browser windows appear and disappear as the tests run. If
the tests finish successfully, you should see the following in your
second console window:

:::: {.language-plaintext .highlighter-rouge}
::: highlight
``` highlight
$ meteor npm run testcafe

> bowfolios@ testcafe /Users/philipjohnson/github/bowfolios/bowfolios/app
> testcafe chrome tests/*.testcafe.js

 Running tests in:
 - Chrome 86.0.4240.111 / macOS 10.15.7

 Bowfolios localhost test with default db
 ✓ Test that landing page shows up
 ✓ Test that signin and signout work
 ✓ Test that signup page, then logout works
 ✓ Test that profiles page displays
 ✓ Test that interests page displays
 ✓ Test that projects page displays
 ✓ Test that home page display and profile modification works
 ✓ Test that addProject page works
 ✓ Test that filter page works


 9 passed (40s)

 $
```
:::
::::

You can also run the testcafe tests in "continuous integration mode".
This mode is appropriate when you want to run the tests using a
continuous integration service like Jenkins, Semaphore, CircleCI, etc.
In this case, it is problematic to already have the server running in a
separate console, and you cannot have the browser window appear and
disappear.

To run the testcafe tests in continuous integration mode, first ensure
that BowFolios is not running in any console.

Then, invoke `meteor npm run testcafe-ci`{.language-plaintext
.highlighter-rouge}. You will not see any windows appear. When the tests
finish, the console should look like this:

:::: {.language-plaintext .highlighter-rouge}
::: highlight
``` highlight
$ meteor npm run testcafe-ci

> bowfolios@ testcafe-ci /Users/philipjohnson/github/bowfolios/bowfolios/app
> testcafe chrome:headless tests/*.testcafe.js -q --app "meteor npm run start"

 Running tests in:
 - Chrome 86.0.4240.111 / macOS 10.15.7

 Bowfolios localhost test with default db
 ✓ Test that landing page shows up (unstable)
 ✓ Test that signin and signout work
 ✓ Test that signup page, then logout works
 ✓ Test that profiles page displays
 ✓ Test that interests page displays
 ✓ Test that projects page displays
 ✓ Test that home page display and profile modification works
 ✓ Test that addProject page works
 ✓ Test that filter page works


 9 passed (56s)

$
```
:::
::::

All the tests pass, but the first test is marked as "unstable". At the
time of writing, TestCafe fails the first time it tries to run a test in
this mode, but subsequent attempts run normally. To prevent the test run
from failing due to this problem with TestCafe, we enable [testcafe
quarantine
mode](https://devexpress.github.io/testcafe/documentation/guides/basic-guides/run-tests.html#quarantine-mode).

The only impact of quarantine mode should be that the first test is
marked as "unstable".

## From mockup to production

Bowfolios is meant to illustrate the use of Meteor for developing an
initial proof-of-concept prototype. For a production application,
several additional security-related changes must be implemented:

-   Use of email-based password specification for users, and/or use of
    an alternative authentication mechanism.
-   Use of https so that passwords are sent in encrypted format.
-   Removal of the insecure package, and the addition of Meteor Methods
    to replace client-side DB updates.

(Note that these changes do not need to be implemented for ICS 314,
although they are relatively straightforward to accomplish.)

## Team

BowFolios is designed, implemented, and maintained by [Philip
Johnson](https://philipmjohnson.org) and [Cam
Moore](https://cammoore.github.io/).

[[bowfolios.github.io](https://github.com/bowfolios/bowfolios) is
maintained by
[bowfolios](https://github.com/bowfolios).]{.site-footer-owner} [This
page was generated by [GitHub
Pages](https://pages.github.com).]{.site-footer-credits}
:::::::::::::::::
