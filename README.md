# Schedule Files Guide

## Date Header

If you create a header \(using \# or the drop down menu\), the air science platform will look for a date reference in there. Dates must be in a limited format for the system to understand how to schedule them. Either **absolute dates** like:

* June 29
* 2021-06-29

Absolute dates must be month first if you are going to use just numbers... sorry that is how the default parser works.

Or relative dates like

* Week 2
* Monday

Week relative dates are assumed to be relative to the start of the schedule. Weekday names like "Monday" are assumed to be relative to the most recent "Week" date in file.

If useful we can also create recurring schedules for repetitive tasks like

* Every Wednesday
* Fridays

Where sections occur in a file is irrelevant \(other than relative dates\). **Do not put anything else besides a single relative or absolute date \(not both\) in the header.** Otherwise we will not be able to properly schedule.

## Available Files

* **Broadcast to Everyone -** Sends to every contact in our database
* **Broadcast to Unregistered** - Sends to contacts in our database who have not finished registration
* **Broadcast to parents** \(Future\) - Sends to parent contacts of registered students
* **Course** - Sends to registered students

## Action tags

_Action tags are used within dated sectionst to schedule actions for that day. Here are some available ones._

### Send

`send` Sends a text message on the user's preferred communication channel \(SMS for now\) at the default time.

You can also omit the send tag in schedule files, since send is the default action

{% file src=".gitbook/assets/alan\_step-1\_-identify-radio-lesson-1-1-.mp3" caption="Sends a robocall at the default time" %}

`@10am` Time tags are used to run this action at a particular time of day. If not specified the default time for that action is used. Times are all relative to the course timezone \(Kampala time\). They can be used for robocalls as well by putting them in the caption of the file.

{% file src=".gitbook/assets/alan\_step-1\_-identify-radio-lesson-1-1-.mp3" caption="@4pm" %}

### Assign

You can add tasks for the user by using the `assign` tag. All registered users will get these assignments as a queue of items to complete in the order they are assigned. When a task should no longer be available you can use the the `stop` tag to make it unavailable and stop presenting it to users. Each tag requires a link to a file that is the script for the task. For example:

`assign` [Intro Step: Lesson 1](sample-course/intro-step/intro-step-lesson-1.md)

`stop` [Intro Step: Lesson 1](sample-course/intro-step/intro-step-lesson-1.md)

There is no need to call stop for a task if you want users to be able to complete it anytime until the end of the course. The initial USSD menu will always highlight the most recently assigned and uncompleted task for the user to do.

If you have a blocking task that the user needs to complete in order to continue to any other task you can use the `require` tag. These tasks will need to be completed before any other task is available. Required tasks will be required in the order they are scheduled. Once a task is no longer required you can stop it as well.

`require` [Baseline Survey](sample-course/baseline-survey.md)

