<!--
 Copyright (C) 2024 Innovate for Vegas Foundation
 
 This file is part of ov-agile-for-volunteers.
 
 ov-agile-for-volunteers is free software: you can redistribute it and/or modify
 it under the terms of the GNU General Public License as published by
 the Free Software Foundation, either version 3 of the License, or
 (at your option) any later version.
 
 ov-agile-for-volunteers is distributed in the hope that it will be useful,
 but WITHOUT ANY WARRANTY; without even the implied warranty of
 MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
 GNU General Public License for more details.
 
 You should have received a copy of the GNU General Public License
 along with ov-agile-for-volunteers.  If not, see <https://www.gnu.org/licenses/>.
-->

# Blue Sky - Agile for Volunteers - Team Tools

GitHub as our primary (initial) platform for Agile for Volunteers, supports the notion of Teams within an organization, which we make use of.

There are three main types of Teams defined for Agile for Volunteers, which we can implement using this hierarchical Teams feature within a a GitHub Organization. This may be realized in other ways with different platforms.

Note that GitHub in particular enables OutSide Collaborators to be added to Repositories, but not to Teams. As of this writing it is not clear if there is a way to make this Outside Collaborator feature work in a consistent way with the Teams feature, but it may be worthwhile to consider how this might work.

Generally speaking, for any given Team there are existing facilities for some membership maintenance and settings management, however some automation will be essential over time. We need to do something like

- List Teams (with Team Icons), individually and hierarchically (without membership)
- List membership (with account avatar, etc)
- List Team hierarchy membership (this is implemented poorly, if at all, which is arguable, with GitHub´s Team feature)
- Add Team Member with log line
- Remove Team Member with log line

Log lines should be saveable so that, over time, a Contributors list (for attribution, at least) with some detail should be available. That is, there is a strong possibility that some Team Members may not make direct Contributions to any GitHub Repository so that the git commit history can be audited for the Contributor list. This additional information, assuming it is captured consistently, can be used as an additional check to attempt to include **all** contributors.

## Whole Team

This is all participants contributing to an Initiative in any way. A top-level Team can be used to contain all participants, members of this Whole Team, where these members may not be members of other Initiative Whole Teams (this may be of interest to large organizations with many Initiatives and Many Many Participants). While this may seem pedantic, determining who is working on, or a part of, which Initiative as an organization and its Initiative and Component Project counts grow will be something of a chore, the Teams feature is there for this, at least.

The ability to display Whole Team membership in various and creative ways as part of an Initiative public-facing website or web content, etc, would be useful and valuable.

## Persistent Team

All regular participants on any Component Project, such that these contributors will tend to be default assignees for Issues, will triage these issues, oversee general Component Project repository health, participate in code reviews or external pull requests, and so on. There is a Persistent Team for each and every Component Project Repository, enabling granular selection, use in default assignee fields, for @ messaging, and so on.

The membership of persistent teams will ideally change slowly if there is change.

## Atomic Teams

For purposes of committing Volunteer Time, Effort, and Expertise to one or more Tasks attached to any Component Project, members are added to an Atomic Team per Component Project repository (and yes, they are part of the Initiative Whole Team in general).

For any particular Iteration, a participant for that Iteration is added to the Atomic Team for that Component Project Repository.

One participant, with their individual GitHub Username, can be added to any number of Atomic Teams, based on the Iteration time frames of any of the relevant Component Projects.

Any member of a Persistent Team is also a member of an Atomic Team for the same Component Project Repository. This is important for consistent messaging, for example (any messages relevant to an Iteration can be addressed to the Iteration Team name using the GitHub @ addressing scheme).
