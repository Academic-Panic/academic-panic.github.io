<!-- # Academic Panic -->
[![ci-academic-panic-application](https://github.com/Academic-Panic/academic-panic-application/actions/workflows/ci.yml/badge.svg)](https://github.com/Academic-Panic/academic-panic-application/actions/workflows/ci.yml)
## Table of contents

- [Overview](#overview)
- [Goals](#goals)
- [User Flow](#user-flow)
- [Mockups](#mockups)
- [Application Screenshots](#application-screenshots)
- [Milestones](#milestones)
- [Deployment](#deployment)
- [Technologies Used](#technologies-used)
<!-- - [Team](#team) -->
- [Team Contract](#team-contract)
- [Team Organization](#team-organization)


## Overview

Academic Panic is a web application for UH Manoa students to connect with their
peers to engage in more effective and collaborative learning with
- a study session planning system that can notify other students of,
- a course review and rating system, and
- a "friends" system to connect students without disclosing sensitive
information,

## Goals

The goals of the project are as follows:
- provide UH Manoa students with a collaborative study/tutoring resource,
- encourage networking and community amongst UH Manoa students, and
- provide a platform for students to share honest (yet respectful) opinions
about courses that will be visible by all users.

## User Flow

- User visits webpage inspired by GitHub's design and sees landing page
displaying planned sessions and participants count.
- User creates account with email/username, password, potential headshot, and
course table (course name, year, semester, instructor, TA/grader checkboxes,
passion checkbox).
<!-- - Account creation may generate a unique ID number. -->
- Landing page updates to display planned sessions for friends and public.
- User can create a study session by filling out details like course, location,
date & time, purpose, and privacy (public or friends-only).
<!-- - Friends-only broadcasts share all information with applicable users, while -->
<!-- public broadcasts hide details until the user commits to attending. -->
- "My Profile" page allows user to view/edit current courses, see friends, and
add them via email/ID number (friendships formed through mutual requests, no
confirmation system).
<!-- - User can rescind friend request or terminate friendship on friends' list. -->


## Mockups
### Landing Page Mockup
![LP Mockup](AP_LandingM.png)

### Application(Sign Up) Page Mockup
![LP Application](AP_ApplicationM.png)

### Sessions Page Mockup
![LP Sessions](AP_SessionsM.png)

### Add Session Page Mockup
![LP AddSessions](AP_AddSessionM.png)

### Agreement/Rules Page Mockup
![LP Agreement](AP_AgreementM.png)

## Application Screenshots
### Milestone 1 Screenshots
#### Landing Page
![LP Landing Page](AP_Landing.png)

#### Sign Up Page
![LP SignUp Page](AP_SignUp.png)

#### Log In Page
![LP LogIn Page](AP_LogIn.png)

## Milestones
[M1 Project Page](https://github.com/orgs/Academic-Panic/projects/1/views/1) - Milestone 1 Issues

[M2 Project Page](https://github.com/orgs/Academic-Panic/projects/3) - Milestone 2 Issues

[M3 Project Page](https://github.com/orgs/Academic-Panic/projects/4) - Milestone 3 Issues

## Deployment
Our application is deployed on vercel in the following link, [Academic Panic](https://academic-panic-application.vercel.app/)

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

Additionally, we will use [Vercel](https://vercel.com/) as our deployment
platform.

## Team Contract
[Academic Panic Contract](https://docs.google.com/document/d/1t8T_RfazQbLVfYcnKgaXLSmiIFlE0KpDmrwTd28IiKA/edit?tab=t.0#heading=h.cwlg4wpeg4ei)

## Team Organization
[Academic Panic Organization page](https://github.com/Academic-Panic)
