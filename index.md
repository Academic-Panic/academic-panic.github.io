# Academic Panic

## Table of contents

- [Overview](#overview)
<!-- - [Mockups](#mockups) -->
- [Goals](#goals)
- [User Flow](#user-flow)
- [Technologies Used](#technologies-used)
<!-- - [Team](#team) -->

## Overview

Academic Panic is a web application for UH Manoa students to connect with their
peers to engage in more effective and collaborative learning with
- a study session planning system that can notify other students of,
- a course review and rating system, and
- a "friends" system to connect students without disclosing sensitive
information,

<!-- ## Mockups -->
<!---->
<!-- TODO: INSERT MOCKUPS -->

## Goals

The goals of the project are as follows:
- provide UH Manoa students with a collaborative study/tutoring resource,
- encourage networking and community amongst UH Manoa students, and
- provide a platform for students to share honest [respectful] opinions about
courses that will be visible by all users.

## User Flow

 - User visits webpage inspired by GitHub's design, sees landing page displaying
 planned sessions and participants count.
- User creates account with email/username, password, optional headshot, and
course table (course name, year, semester, instructor, TA/grader checkboxes,
passion checkbox).
- Account creation generates unique ID number.
- Landing page updates to display planned sessions for friends and public.
- User can create a study session by filling out details like course, location,
date & time, purpose, and privacy (public or friends-only).
- Friends-only broadcasts share all information with applicable users, while
public broadcasts hide details until the user commits to attending.
- "My Profile" page allows user to view/edit current courses, see friends, and
add them via email/ID number (friendships formed through mutual requests, no
confirmation system).
- User can rescind friend request or terminate friendship on friends' list.

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

<!-- TODO: ADD DEPLOYMENT MECHANISM -->
