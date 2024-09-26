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

# Blue Sky - Agile for Volunteers - Form Tools

Agile for Volunteers should be usable and useful to a full range of Volunteers, from experienced and tools-savvy to newcomer and perhaps a bit reticent about jumping in to any sort of collaboration management.

Web pages and apps have set a usability bar that we can achieve with some effort. We can create completely custom interfaces sometimes, we may develop our own tools and applications to accommodate broad adoption and diverse use cases, when the time comes. For the moment, we begin with the Issue Forms feature(s) support (in beta as of this writing) in GitHub.

One might being here at the [Issue and Pull Request Templates](https://docs.github.com/en/communities/using-templates-to-encourage-useful-issues-and-pull-requests/about-issue-and-pull-request-templates) page, but the essentials are these:

- Issue (and Discussion) forms are composed using YAML and follow a specific schema for GitHub use.
- Pull Request Templates, as well as Issue and Discussion Templates, are composed in Markdown (or GitHub Flavored Markup, GFM, to be precise)
- It will be a matter of preference whether so-called Blank submissions are allowed without the use of forms and/or templates.

Initially we will presume a prescribed collection of YAML-based Forms and Markdown-based Templates for use in a GitHub-based organization for Initiative collaboration.

## Tools

Authoring YAML and Markdown are fairly straightforward activities. However, as specifics of the overall Agile for Volunteers workflow develops (or, has developed, since this document has been authored after some initial experimentation), manually editing YAML files and Markdown, especially with any degree of customization across multiple dimensions becomes untenable for one person. This can only become more complicated with collaboration in-Initiative, and if Agile for Volunteers is to be broadly useful, a workflow for Form and Template management is essential.

It would make sense to have a per-Component-Project-repository configuration indicating which forms and templates will be used, and in which form, with customizations or other modifications as needed. It important to enable extension of the core workflow user experience, while a the same time preserving some degree of familiarity for external contributors and collaborators.

A Form and Template authoring and management workflow might take the latest upstream forms and templates as starting points and enable a structured merging scheme (that is, something more useful in the case of YAML-based forms than line-by-line merges, to preserve local initiative modifications for example). One approach might be to store form and template content and structure in such a way as a particular form might be built up from these elements, selected in a particular order, with any needed local modifications. This idea will require some evolution.

## Upstream Origin Component Project

Base Forms and Templates will ideally be maintained as a specific Component Project, in a Component Project Repository, with all of the expected workflow and process to facilitate collaboration here as well. We can and should presume that Forms and Templates, like everything else, might be adopted and deployed for Initiatives and by Cohorts making use of languages other than the American English origin of this very document.

Any use of Agile for Volunteers anywhere should be able to pull the latest Form or Template (individually or grouped in particular ways, by Component Project Type, Translated Language, etc) and build local versions of these as needed.
