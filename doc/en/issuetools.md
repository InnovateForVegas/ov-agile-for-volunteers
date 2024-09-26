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

# Blue Sky - Agile for Volunteers - Issue Tools

Issue tracking tools have, over time, become useful for tracking a Backlog that may include User Stories, Tasks, Defects, and other such things.

Our initial implementation of Agile for Volunteers will focus on the tools we have available as of this writing, which means GitHub, including its per-repository Issue infrastructure.

## Issues and the Plan and Task structures

Using Issues or similar in the platform(s) of choice to track plan and task items along with bugs and defects is a good idea. Whether the platform of choice is Jira, GitHub Issues, or something else, or a combination, Issues are made to have these properties at a minimum

- A lifecycle with history
- An assignment and re-assignment capability to pass around active items
- Support in project management tools (eg GitHub Projects work directly with GitHub Issues)
- Labels or tags or some other metadata attachments
- Reporting tools based on Issues

Issues are the correct choice in general over, say, long-form documents such as this one (which is a Blue Sky document for ideation, not a planning document per se) or Discussions or other less-structure approaches which lack the associated tools and methods that come along with Issues.

Issues on their own can be managed using basic tools available with the associated platform (eg GitHub issues have some reporting features and bulk management options along with some keywords that can be used to convert comments to action to close an issue, etc), but these are minimal, good enough to enable Issue functionality but not necessarily idea for the load they will carry for Agile for Volunteers workflows. A Plan Issue hierarchy to factor Initiatives into digestible elements, associated Task Issues that indicate when Plan in the abstract is converted to Concrete Implementation, and of course associated of Bugs and Defects with particular Component Project Repositories and Assignees.

Some of the metadata we will need for Issue Linking and Visualizations of Issue Linking and possibly time/effort/expertise measurements for pace-keeping, will make use of data stored (and updated) in the Issue Description, which in the case of GitHub is stored as a Markdown block. This is not necessarily ideal, but is workable with some Markdown parsing and round-trip-safe updating when automation performs updates.

## Issue Linking

There are some facilities built in to the GitHub Issue infrastructure to make linking one issue to another via autolinks or explicit https links reasonably easy. However, this is not sufficient for our needs.

[Autolinked Issues and Pull Requests](https://docs.github.com/en/get-started/writing-on-github/working-with-advanced-formatting/autolinked-references-and-urls#issues-and-pull-requests)

### Intra-repo linking

In an Overview Component Repository, our Plan issues for an Initiative are structured by Theme, Epic, Feature, and (User) Story. Each Theme is made of one or more Epics, each Epic is made of one or more Features, each Feature is made of zero or more Stories.

In an implementation Component Project Repository, we have Task issues that may be split or merged, or associated with defect issues specific to the particular Component Repository.

If we would like to make use of graph tools for managing these relationships, and visualizing them, we need to be able to discover these relationships, parse them, and make use of them with graph tools (rdflib and RDF in general will figure into this scheme).

### Inter-repo linking

One the Plan side, we have abstract notions of what we will be doing, on the Task side we have concrete notions what it is we are making. We need to associate a Task from a Component Project Repository with a Feature or Story in the Plan hierarchy of the Overview Repository.

If we can use a consistent labeling scheme, we can create a collection of Issue links that connect any particular issue to any other issue, in any repository. If we continue to make use of graph tools such as RDF (Resource Description Framework), we can indicate specifically how the current issue is related to any other issue using the triple scheme of RDF.

## Markdown Parsing and Data Interchange

Several options exist for the unstructured data that is stored in a GitHub Issue (where something more powerful like Jira is used, there are more options for storage and management of structured issue data, that is something to examine but we can keep this example simple).

In some cases we will need to extract data from the Issue markdown text (not the comments, though these might be useful also), in other cases we may need to add or update some data in the Issue markdown text, and in still other cases we may need to extract some data and apply an update based on that data. All of these will require that the text of the Issue at any given time is only changed as it is intended to be, which is to say the tools and methods used to accomplish parsing, extraction, and updating must all be “round-trip safe” with a parse and update step with no change applied resulting in identical output compared to the input. This is an indication that applying a change will only change the intended information, leaving the balance of the issue text as was.

### Issue Linking Graph Data

One idea for storing graph data in markdown, is to use consistent labeling in an RDF (terse triple language, or .ttl, style notation) friendly scheme that will map directly to an RDF schema with those tags defined. The issue text block, for a Feature issue in this example, can contain header text as a label, and then something like

- :story URL_OF_STORY_ISSUE
- :epic URL_OF_EPIC_ISSUE

which would be marshalled into

URL_OF_THIS_ISSUE:
  a :feature;
  :story URL_OF_STORY_ISSUE ;
  :epic URL_OF_EPIC_ISSUE .

The unusual syntax we would embed in the issue markdown text is easily found (list markdown with leading - characters, then a :name is going to be uncommon) and it is close enough to .ttl or .n3 (Notation3) format to be recognizable (or familiar, at least) so that graphs will become a part of the Ubiquitous Language is use for all Agile for Volunteers Initiatives and Component Projects.

These structured blocks of text could be parsed, extracted, and use to construct actual Issue Graphs, connecting Initiative and Component Project Issues and their relationships, and this graph could be used to create visualizations, to search for a report on these relations in more useful ways that are available to a normal issue filter and report system, and there would be applications of this structured graph making others aware of issues in need of help, open for contribution, or generally available for participation, with the possibility of a top-level map of how these fit together.

### Issue Linking Visualization

Once a network graph is available representing relationships among the Plan, Task, and Defect issues within a Component Project and within the larger Initiative, it should be relatively easy (famous last words) to compose a graph representing how our Feature issue in the example above is related to the Story and Epic Issues, and perhaps to Task issues in one ore more Component Project repositories.

Converting a subgraph from the overall graph representation, to something like a Mermaid visualization (which is supported natively across many GitHub features) will enable a per-Issue visualization as to how any one issue fits with its neighbors. The scope of the graph (how many nodes and edges to represent) would be small.

The tool described herein would ideally place a Mermaid block into the Issue Markdown text without disturbing the other text.

### Time, Effort, Expertise and Pacing

One of the shortcomings of Agile (if the other is the daily stand-up meeting) is Story Points. These are an estimation tool best used among team members who work together frequently and over long periods of time (or at least, several agile iterations) so that the estimations reflected in the Points are meaningful. Even in these cases, Story Points do not always accomplish this and they are at times misused as a form of grading or other performance evaluation.

Given the nature of Agile for Volunteers and the Time, Effort, and Expertise a Volunteer might contribute to any part of an Initiative, it is difficult to presume the familiarity momentum that is part of the utility of Story Points. Also, and more important, a particular Task (implementation of a User Story, for example) may exist in multiple Component Projects using different languages or other tools, or they may not be Software at all… in this case, a single Story Points estimate makes little sense. We move the estimation and final value storage to the Task (and Defect) Issues, so that the individual(s) working on the Issue can and should store useful values with the Task issue, NOT with the Story issue.

The tool functionality here, then, is extraction of estimate and actual values (these are example terms, actual labels may vary) for collection and reporting. Given the lack of structured data features in the Issue Markdown text, we can do something similar as we have with Issue Linking above. Use of a Markdown heading as label text, and then something YAML-like (without the markdown language quotes, these disable the rich text editing in the GitHub Issue interface, unfortunately):

```yaml
(GitHubUserName):
  - Estimate:
    - effort: 10
    - expertise: 2
  - Actual:
    - effort: 8
    - expertise: 2.5
```

If there are other collaborators, multiple GitHubUserName values could be used in this structure, and extraction of these data, if the same structure with these key names is used, would be relatively easy.

In this example we assume use of the Torque scheme to keep track of effort and expertise applied as force on a disk, like pedaling a bicycle. More expertise provides more leverage, and effort could be expressed as a percentage of available effort over an iteration (these are ideas at this point). Torque as effort x expertise, but with these values preserved, can enable what we could call Pacing, so that Volunteers can adjust their efforts…

Extract the values in various phases (that is, an estimate might be available initially, with an actual value added when the task is “completed,” with the possibility of addition or removal of users… we presume a degree of flexibility). There should be no need to update the Issue markdown text when parsing and extracting the Torque data per Issue.
