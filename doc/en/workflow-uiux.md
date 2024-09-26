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

# Blue Sky - Agile for Volunteers - Workflow UX/UI

As of this writing, Agile for Volunteers is implemented using the GitHub platform, which includes facilities for rich Forms and markdown Templates to aid in consistent and useful contributor interactions with regard to Issue filing, Discussion, and Pull Request submission. Agile for Volunteers will take advantage of this facility to help with what we might call Live Onboarding of someone new to Agile for Volunteers and new to any particular Initiative or Component Project making use of Agile for Volunteers.

There is an Initiative and Component Project repository structure we use for Agile for Volunteers, with each Component Project benefiting in some cases from the tailoring of Forms and Templates to the specifics of the Component Project type in question (or the specific Component Project, perhaps), while still making substantial use of a consistent Form and Template base.

Use of Ubiquitous Language (visit the Glossary in the official Agile for Volunteers Documentation) will ideally accelerate acclimation to the workflow across Issue types, Component Projects, and Initiatives in general. One specific item, the collection of User Types to be used in User Stories (and elsewhere in similar context) should be maintained across an entire Initiative, used in all of its Component Project workflows, to continue the consistent use of language and reference.

All workflow elements should be internationalizable and localizable. That is, while they may be authored in American English (as is the case with this document), there should be some forethought regarding translation to other languages. The actual translations may be stored adjacent to the original source material (that is, pre-translation, not auto-translated on the platform), composition will ideally support this flexibility.

## Issue Forms

GitHub supports YAML-based Forms for Issues, which are rendered in place of a blank Markdown text area for a new Issue.

Depending on the type of element, some Label or Descriptive text may be left in the submission, but most annotation (markdown elements) and other useful Form elements are NOT included in rendering of the submission after the fact. This makes creation of usable forms that are friendly to in-place edits something of a challenge.

At the same time we need to make it easy for a newcomer to begin at the beginning, submitting a new issue, and have them walk through a workflow for that Issue that fits into the overall workflow for that Component Project.

Workflows can vary based on whether the Component Project is an Initiative Overview (Issues will be for Plan and Bug submissions), or a code-related Component Project (with Tasks and Defects) or some other Component Project which may require some additional consideration for media, ux, ui, co-creation, mechanical, or other non-software-oriented Component development.

Issue forms for Overview Component Projects should include

- Plan issues for
  - Theme
  - Epic
  - Feature
  - Story
- Bug issue (for external submissions that may not have insight into Component Project Structure)
- Repo issue (this is a meta issue for ToDo items related to the Repository itself, not the Initiative)

Issue forms for Component Project repositories should include

- Task issues
  - Story Task
  - Feature Task
  - Epic Task (these may be administrative or meta tasks, eg any pivots or large adaptations for a relevant epic)
  - Theme Task (these may be administrative or meta tasks, eg framework selection, initial repo config, etc)
- Defect issues
  - Relevant to the specific Component Project (eg triaged defect is almost certainly based in this particular repo)
  - Relevant to the specific Component Project AND one or more additional Component Projects (eg an Integration problem)
  - A general defect that may be the result of something in this repo but not a result of the focus of the Component Project

Issue Forms should be composable to accommodate customizations per Organization, Initiative, or Component Project, as needed.

## Discussion Forms

Discussion forms are very similar in structure and supported features to Issue Forms, within the GitHub platform.

The workflow in a Discussion context is less structured, but will still benefit from guidance provided in Discussion forms. References to a consistent set of User Types, for example, and of course use of Ubiquitous Language in general. We presume that someone who is not so familiar with Agile for Volunteers, with a particular Initiative, with Component Project structure, or anything else, can participate in a Discussion without additional familiarity. A good starting point for someone considering taking part in an Initiative in some way, or a way to enable some focused discussion in some cases, or more general discussion at the Initiative level.

GitHub provides facilities for per-repository Discussion categories, which may each have an associated Form, and which may be grouped into custom Sections within the Repository Discussion. This aligns with the Component Project repository scheme. Each Component Project repository enables its own iterations, has its own properties and design considerations, all of these are usable Discussion categories.

## Pull Request Templates

GitHub enables Pull Request Templates as pre-filled Markdown text, which the submitted should edit to provide particular pieces of information to the reviewer(s) and other Team members of the relevant Component Project.

We can ask for some particular details, such as submitted language familiarity in the cast of a translation pull request, and we can ask whether the submission includes substantial work by AI tools (along with references to those tools).
