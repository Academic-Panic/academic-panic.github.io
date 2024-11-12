# Academic Panic: Proposal to Modify Study Buddy

We propose a modified variant of Study Buddy that de-emphasizes gamification and
augments the course listings to include associated semesters, instructors,
grades, involvements (student, TA, grader, etc.) to let a user decide whether
another user is capable of assisting our user in that specific course.

*Disclaimer: these opinions are ours --- of electrical computer and engineering
students taking 300-level courses or higher. They may not make sense outside our
context, and if so, some or all of these opinions should be discarded in regard
to designing a project that works best for ICS students of all grade levels.*

## Description of Study Buddy

In brief, the original [Study
Buddy](https://courses.ics.hawaii.edu/ics314f24/morea/final-project/reading-project-study-buddy.html)
is designed to facilitate students to actively seek out opportunities to give or
receive help from others in-person. It does so by having users list out courses
they have taken, and whether the student is a "grasshopper" (someone that needs
assistance) or a "sensei" (someone that is willing to provide assistance) in
each of those particular courses. Operating under the assumption that students
have an inherent inhibition in regard to seeking out assistance, there would be
some sort of gamification mechanic involved --- perhaps points --- that
encourages participation in study sessions either as a grasshopper or a sensei.
This would even translate to gift cards or other tangible rewards from the ICS
department to reward the "best" senseis and grasshoppers over some time
interval.

The project is an excellent idea, but we found certain design issues that we
wanted to address in our modification.

## Simplistic Sensei/Grasshopper Feature Associated with Courses

### Problem

Simply entering courses and an associated sensei/grasshopper label means that
users will have to self-evaluate their comprehension of the material and ability
to aid others. Additionally, it's possible that some individuals need more
assistance than others, or are more capable of teaching than others. Confining
those nuances to a singular binary feature associated with the different
courses, and may result in poor outcomes due to mismanaged expectations
regarding the assistance one can grant or need.

### Solution

We would like to maintain the sensei/grasshopper feature as that allows us to
handle sending notifications differently, but we would like to add the following
additional fields:
+ semester (term and year, e.g., Fall 2024),
+ instructor, and
+ association with the course (student, TA, grader).

The first 2 fields are used to allow other users to determine the "shape" of the
course as the student took it. Different semesters will have courses that run
differently, even if the course itself is the same. (For example, ICS 314 in
Fall 2024 used a new tech stack in its materials, which resulted in a bumpier
ride than the last due to residual outdated material, whereas ICS 314 in Spring
2024 went a lot smoother due to multiple semesters spent ironing out details in
the course website.) In the case where the semester field doesn't provide much
information, the instructor field would. Different instructors handle the same
material differently, and thanks to resources like [Rate My
Professors](https://www.ratemyprofessors.com/), students can learn more about
the style the instructor employed --- which will most likely hint at the style
that a sensei will tutor a user. (We may add clickable links to redirect
students to the relevant Rate My Professors page, or hand-roll our own
specifically for UH Manoa, but that goes beyond the basics.)

## Unhelpful, Complicating, and Potentially Harmful Gamification and Rewards

### Problem

The "inherent inhibition" seems to contradict most of our desire to actively
seek out assistance and help. This would most certainly apply to people in their
first semester of college, but typically dissipates with each semester.
Additionally, if an "inherent inhibition" is strong enough to prevent a student
from seeking out assistance, then it's possible that assistance isn't essential
for that student. (Loosely speaking, they'd accept help if it was served with
incentives or right in front of them, but if they aren't going to seek it out,
then perhaps they didn't need the help in the first place.) As such,
gamification is something that we find unnecessary, and its removal would
greatly simplify design and remove the need to implement "anticheat" methods for
individuals that seek to "farm" points without actually studying. This would
also remove a "rewards" system that translates into tangible, useful real-world
items like gift cards --- which may incentivize cheating more than the points
construct originally proposed.

### Solution

We discard the points and rewards used in gamification. The most gamified
mechanic we may implement is a public display of study sessions attended as a
sensei or grasshopper --- giving a similar metric of "experience" not unlike
upvotes and medals on Stack Overflow, or "karma" on Reddit.