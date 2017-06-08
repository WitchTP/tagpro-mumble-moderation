# TagPro Mumble Moderation Manager (TM3) #

## Features ##

TM3 is a web application that supports the following features:

- Login system for users
- Private moderation log for bans, unbans, warnings and mumble user notes
- Public moderation log for room modifications (includes granting and revoking mumble powers and usergroup modifications)
- Request system for players (involves channels, ACLs, appeals, etc.)
- Search feature for moderation log
- Search feature for appeals

### Login System ###

The admin has the power to create user accounts.
Each user is given certain roles that can be used to access certain features.
These roles are:

- Admin: create user accounts and edit user roles
- Log usergroup modifications
- Log channel modifications
- Log mumble user kicks, bans and unbans
- Log mumble user warnings and notes
- Log general announcements
- See IP addresses associated with requests
- Close requests

No user can create their own account; instead, an admin must create an account for the user.
Each newly-created account comes with a username and a randomized password that is displayed to the account creator.
Upon first login, the user is prompted to change their password by being presented with the password change screen.
To activate their account, the user must get past the password change screen.
This entails typing the current password, the new password, and a confirmation of this new password.
The user then has access to the whole application and can change their profile settings.

### Profile Settings ###

The user can access the password change screen from here.
The user can also modify their display name and set an email address for receiving notifications.
Finally the user can view their roles.
Note that only the user's display name and roles is public to others.

### Account Creation ###

This page is accessible only to users with admin privileges.
The user can specify a unique username in a textbox.
The user can then click a 'Create Account' button.
If the username is unique then a randomized password is generated and displayed to the user.
If the username is not unique then the user will be prompted to enter another username for the new account.

### Moderation Log ###

This feature consists of two parts: a log submission screen and a log search screen.
If the user has insufficient roles for a given screen, the user will not be able to access nor see a link to that screen.

The log submission pages are accessible only to users with the privileges to submit such logs.
Each log submission screen features a set of fields that the user needs to fill out before submission.
When a log is submitted, it is stored in the database with each recorded detail, the name of the submitter and the submission date.

The log search screens are accessible by any logged-in user, except where noted.
Each log search screen features a scrollable log showing each record arranged in reverse chronological order.
The page features a refresh button that allows the user to retrieve the latest records.
The user can also filter the list of records using a set of fields at the top of the page.
The set of provided filter fields consists of a start date field, an end date field, a submitter field and the set of submission data fields associated with the log type.
Each filter is combined using an `AND` operator.
Each text field uses a substring match for filtering.
If a date range is specified, the range is inclusive.
If a start or end date is not specified, the range is set at either the beginning or the end of time respectively.

#### Mumble user log submission ####

Upon navigating to the mumble user log submission screen, the user is presented with the following required fields:

- Name of the mumble user
- IP address of the mumble user
- Log type (kick, ban, warning, unban, rename, note) [Options available based on roles]
- Description

The submission button (Submit) is activated only when every field has been filled out.

#### Usergroup log submission ####

Upon navigating to the usergroup log submission screen, the user is presented with the following required fields:

- Usergroup name
- Log type (creation, deletion, rename, ACL change, user addition, user removal)
- Description

The submission button (Submit) is activated only when every field has been filled out.

#### Channel log submission ####

Upon navigating to the channel log submission screen, the user is presented with the following required fields:

- Mumble channel URL (mod can get this via the *Copy URL* button in Mumble)
- Log type (creation, deletion, rename, description change, ACL change)
- Description

The submission button (Submit) is activated only when every field has been filled out.

#### General announcement submission ####

Upon navigating to the general announcement submission screen, the user is presented with the following required fields:

- Description

The submission button (Submit) is activated only when every field has been filled out.

#### Mumble user log search ####

Upon navigating to the mumble user log search page, the user can view the whole log and apply filters.

#### Usergroup log search ####

Upon navigating to the usergroup log search page, the user can view the whole log and apply filters.

#### Channel log search ####

Upon navigating to the channel log search page, the user can view the whole log and apply filters.
This page is visible to the general public.

#### General announcement search ####

Upon navigating to the general announcement search page, the user can view the whole log and apply filters.
This page is visible to the general public.

### Request System ###

This feature is available to the general public.
It consists of three parts: a *request submission* screen, a *current requests* screen and a *closed requests* screen.

The *current requests* screen and the *closed requests* screen feature a scrollable log showing each record arranged in reverse chronological order.
The page features a refresh button that allows the user to retrieve the latest records.
The user can also filter the list of records using a set of fields at the top of the page.
The set of provided filter fields consists of a start date field, an end date field and the set of submission data fields associated with the request.
Each filter is combined with an `AND` operator.
Each text field uses a substring match for filtering.
If a date range is specified, the range is inclusive.
If a start or end date is not specified, the range is set at either the beginning or the end of time respectively.
If the user does not have sufficient privileges to view a record, the record is not presented with the search results.

#### Request submission ####

Upon navigating to the request submission screen, the user is presented with the following fields:

- Name (optional)
- Title (required)
- Description (required)
- A checkbox that marks a request as private

When the request is submitted, the application will record the user's IP address along with the request.

#### Current requests ####

Upon navigating to the current requests screen, the user can view the whole set of public open requests.
A public user will see the requester's name, the request title, the description and the date of submission.
An authenticated user can see both public and private open requests along with an extra field determining the request's privacy status.
An authenticated user with sufficient privileges will see the requester's IP address.

An authenticated user with the ability to close a request will see a *close* button next to each request.
Clicking on this button will present a confirmation dialog asking if the user is sure that the request should be closed.
Once a request is closed, it cannot be reopened.

#### Closed requests ####

Upon navigating to the closed requests screen, the user can view the whole set of public closed requests.
A public user will see the requester's name, the request title, the description and the date of submission.
An authenticated user can see both public and private open requests along with an extra field determining the request's privacy status.
An authenticated user with sufficient privileges will see the requester's IP address.
