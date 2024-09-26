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

# Blue Sky - Agile for Volunteers - Repository Tools

Agile for Volunteers will take advantage of the use of multiple repositories (rather than a single or monorepo) to partition different parts of an Initiative into Component Project repositories.

The reasons for this approach include:

- A canonical repository layout to begin with can be adapted for a particular Component Project as needed without upsetting a Monorepo
- A single Component Project repository may be implementing the Component(s) using some particular programming language or architecture regardless of other Component Project repositories
- Any individual Component Project repository can make use of GitHub Project tools, iteration starts and ends, private or public access, team membership, and so on
- Component Projects across multiple repositories implies a Microservices approach, but this is not required as a matter of deployment (see submodule, subtree, subrepo features of git)
- While we often presume GitHub is used to track software projects, indeed Agile for Volunteers is about Volunteers contributing to and collaborating on a variety of Initiatives, so that any Component Project might be anything *but* software. A single monorepo approach may make this flexibility more difficult, especially with non-software-familiar collaboration
- Newcomers to a Cohort or Organization might be able to identify an area of interest in a particular Component Project rather than jumping in to a Monorepo architecture
- More…

There are some tools available to manage some aspects of GitHub repositories, though they do not appear to focus so much on multi-repo management. To that end, there are a few particular needs we need to address.

## GitHub Repo Configuration

GitHub does support Repository Templates, and these may be useful. However, these may appear as opaque starting points and may require a large number of templates to accommodate different types of Component Project repositories.

We will assert here, that repository configuration via composition will make this easier, especially if we are able to re-configure a repository if needed, making use of the visibility of the composition. In other words, rather than starting with a template and making changes to the instance in question, we can see where the setting is we need to change, change it, and apply the change to any or all Component Repositories.

## Component Projects and Repositories

Different Component Project types will need slightly different Configuration.

Ideally, the variations will be small enough to warrant specialization without introducing confusion through inconsistency. This is yet anther reason to have composable repositories, so that experimentation does not require manual re-configuration through any Agile for Volunteers evolutionary development period.

## Discussions

In the case of GitHub Repositories, each can enable a Discussion feature which can be made interactive for those with Read access to the Repository. This is the likely option to select but may not always be.

As part of the Workflow UI/UX elements of Agile for Volunteers, Discussion forms are a part of the overall design, guiding any individual through the particular Agile for Volunteers Discussion starters. Note that the default GitHub Discussion categories may remain, and additional categories may be added, or removed, as needed.

GitHub API support for configuration of Discussion features may be lacking at the time of this writing, but ideally we can accomplish any or all of these to start:

- add/edit/remove a Discussion Section
- add/edit/remove a Discussion Category
  - Configure the Discussion Category with Title, Description, and associated Emoji icon
- configure discussion settings as needed

Pretty simple, but Discussion capabilities are an essential communication function if there is intent to include those who are not immersed in the Initiative, Agile for Volunteers workflow, Iterations, and so on. The ability to make good use of a Discussion feature (as part of GitHub, or elsewhere such that there is some coupling between Component Project and Discussion) is important and worthwhile to pursue and automate.

## Access

Repository Access configuration can be as simple as marking a Component Project repository as Public or Private (this may be useful for short periods of time, or in general; not all repositories need be public at all times in all cases).

As well, GitHub supports Team association with a particular Repository; with the presumption of support for Whole Team, Persistent Team, and Atomic Team groupings and access controls, it will be useful and important to be able to

- Add and remove members of any team frequently (Atomic Teams in particular)
- Display team hierarchies in useful ways (the GitHub UI is not good, as of this writing)

## Labels

GitHub enables assignment of a collection of Labels to Discussion and Issue items, which we may use in a variety of ways to structure our various Issues and Discussion items.

Most useful, a common set of Labels used across all Component Project repositories within a single Initiative. Consistent use will aid in reporting on and classifying different issues across repositories using a consistent metadata scheme realized through use of the labels.

At the time of this writing, a collection of Labels created with this usage model in mind, has been created as a YAML document, which can be parsed into the needed values to create, update, or delete one or more Labels from each Repository. At the time of this writing, a sample GitHub command line tool example can be used to create or force an update to Labels extract from the YAML file, as one functional example.

Label management needs are relatively simple:

- audit the Labels configured per Component Repository
- sync Labels across Component Repositories assuming they are all associated with a single Initiative
- enable removal and update, in addition to creation, during an automated or interactive Label management session
- consider a sync or super-sync option to use an Initiative-level Label collection definition applied with sync across all Component Repos

## Configuration Storage

Any Component Project repository will have per-repo configurations to synchronize and keep current.

Suggest a universal directory for such configuration, easily-identified and seemingly otherwise-unused, perhaps

.agilefv

at the root of each repository, where a repository is the Component Project unit.

Configuration items may include

- per-form and per-template modifications as suggested in [Form Tools](formtools.md)
- default values for issue assignments (also configurable per-form on GitHub with an additional YAML document in the form footer)
- default Teams by team name (for Whole Team, Persistent Team, and Atomic Team and uses of these references as needed)
- any other configuration for automated maintenance or similar

## Local vs Remote

In some cases, a repository can be manipulated in useful ways locally (eg in a cloned working tree) and then committed. This is most likely going to be maintenance of the local modifications used to compose forms and templates, beyond what the forms and templates tools would do.

Mostly, repository manipulation (or mutation if you prefer) will take place via a GitHub API, or an appropriate interface on other platforms, to accomplish the tasks described above, and whatever else we need.
