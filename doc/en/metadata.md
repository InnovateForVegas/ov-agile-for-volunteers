<!--
 Copyright (C) 2025 Innovate for Vegas Foundation
 
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

# Blue Sky - Agile for Volunteers - Metadata

Agile for Volunteers in service for an organization, with one or more initiatives, each with component projects, contributed to by teams of volunteers… all of these and more will have metadata associated with them which will require some administration not only of the metadata elements themselves, but the uses of the metadata elements to configure repositories, teams, permissions, and so on.

Use of these metadata will thus require a Schema to describe the data stored, and tools to create, edit, and consume metadata elements to configure repositories or other actions.

## Schema

The metadata we store needs structure to enable validation and interoperable use between various tools to accomplish a variety of tasks.

Formal specification is deferred into the Planning and Implementation phases (and may be iterative) but we certainly need some or all of

- Organization Information
  - Name and other org data
  - Pointer to TILE or FOAF or similar structured resources
  - Contact information for Agile for Volunteers questions
- Initiative Information
  - Label configuration
  - Personae definitions
  - Template constants as needed
- Component Project Information
  - Explicit component type (backend, frontend, etc)
  - Label overrides
  - Personae overrides
  - Component type-specific detail

There may be a variant requirement if platform is a factor (eg metadate detail for a GitHub-based organization versus one using a normal Website, or perhaps spread across multiple platforms?).

## Tools

If we assume a consistent schema and file structure, general access to the metadata itself would not require specific tools (eg stored as YAML or JSON or XML or an RDF container format or whatever is selected, there are many well-known ways to access these data for use).

What we do need, though, is tooling to administer metadata per organization, per initiative, per component project, and whatever other scenarios arise.

The section is purposely vague as the specific needs will likely vary per usage scenario and context, but this is bluesky so

- Create and initialize a metadata structure (directories, files with initial values)
- Compare upstream and local metadata structure or elements in context and report material differences
- Apply local variants to upstream metadata base schema and data to update local metadata as needed
- Present metadata in a publishable way (for generated html, etc)

The tools themselves will likely work best if they make a few assumptions and accept user input for entry-level use, but also enable more granular administration for multi-initiative oversight.
