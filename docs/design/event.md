# Events

## Abstract
Events are created by administrators and serve to notify, track, stream, group and award LoS Game Night players.

## Lifecycle
1. [Create](#Create) (**admin**) 
2. [RSVP](#RSVP) (**user, streamer, team captain**, up until scheduled time -15 minutes)
3. [Team Assignment](#Team-Assignment) (**admin**)
4. [Live](#Live) (**streamers**)
5. [Awards](#Awards) (**admin, user**)
6. [Post Live](#Post-Live) (**user**)

## Use Cases
<h3 id="Create">Create</h3>
- **Actor:** Admin
- **Preconditions:** None

As an admin, I want to create events so that players may [RSVP](#RSVP). 

Admins can only create events which are scheduled in the future. Multiple events can be scheduled to occur at the same time. When an event is created, the admin should be able to cause a discord bot to broadcast the event creation including a URL that users can click from within Discord to land at the event page where they can RSVP. An admin should also be able to notify email subscribed users that the event has been created.


<h3 id="RSVP">RSVP</h3>
- **Actor:** User, Streamer, Team Captain
- **Preconditions:** The event has been created by an admin. The event *is not* scheduled to begin in 15 minutes or less.

As a user, I want to RSVP to events so that the event owner can track attendance to the event and [assign me to a team](#Team-Assignment).

Users will mark "Attending" or "Not Attending" to complete the RSVP process. Team Captains can mark the same choices as a user, but also can mark "Attending as Team Captain."  Similarly, streamers can make the same choices as a user, but also can mark "Attending as a Streamer." Streamers who are also team captains will have all 4 choices available and can mark up to 2 choices.
#### Choice Exclusivity
- Not Attending is a **mutually exclusive** choice.
- Attending is a **mutually exclusive** choice.
- Attending as a Streamer and Attending as a Team Captain are **not mutually exclusive** choices with each other, however they *are* **mutually exclusive** with Attending and Not Attending.

#### Choice Permutations
- Attending
- Not Attending
- Attending as a Streamer
- Attending as a Team Captain
- Attending as a Streamer | Attending as a Captain


<h3 id="Team-Assignment">Team Assignment</h3>
- **Actor:** Admin
- **Preconditions:** There are at least 2 people Attending as a Team Captain. The event *is* scheduled to begin in 15 minutes or less.

As an admin, I want to assign users to teams so that the attendees have a team captain to follow when the event goes [Live](#Live).

The event admin will see a relative experience score for each attendee. This score will help the admin to normalize the teams. In future releases, the system should perform this action for the admin. Team assignment should also hinge upon attendee favorite status. Users will be able to mark other users as favorite team mates and the admin should partner these favorites together as much as possible within reason.
#### A note on favorite reasonableness
The goal of Game Night is to foster a fun, communal environment for all attendees. Should an admin form a team that utterly imbalances the other teams to such a level where the other teams have no hope of winning a game, the comaraderie fostered by partnering favorited players together will be outweighed by the feels-bad-man experience imposed on the rest of the attendees. Statistically speaking, teams should have an average relative experience score within one standard deviation of all other teams. If the mean is 50, a team should have a score no higher than 84 and no lower than 16.


<h3 id="Live">Live</h3>
- **Actor:** Streamer
- **Preconditions:** The current time falls within the event begin and end times.

As a streamer, I want my stream to be embedded directly into the LoS Gaming App while the event I am streaming remains live.


<h3 id="Awards">Awards</h3>
- **Actor:** Admin
- **Precondition:** The current time is after the event end time.

As an admin, I want to award attendees for participating in the Game Night event.

Awards should be distributed such that players who have won the least amount of rewards are favored. The system should be responsible for selecting the award winners and must use a set of weighted variables for the selection process. TODO(mlynam): come up with the vars and the algorithm


<h3 id="Post-Live">Post Live</h3>
- **Actor:** User
- **Precondition:** The current time is after the event end time.

As a user, I want to view Twitch VoDs or YouTube videos that streamers have produced which cover the post-live event.

