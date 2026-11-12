# Workshop Website User Interfaces & Visualization

The User Interfaces & Visualization workshop has been held at the University of Applied Sciences Dresden almost every year since 1992. It is traditionally organized by the Faculty of Computer Science/Mathematics and the Faculty of Electrical Engineering of the Czech Technical University in Prague. It offers young scientists in particular the opportunity to present and discuss their current research results. The workshop is open to undergraduate and PhD students from both universities. The main goal is to create a credible simulation of a process where results of scientific work are presented to an international audience.

## Description

This repository holds the website for the workshop with Github Pages under [workshop-user-interfaces.github.io](https://workshop-user-interfaces.github.io/). Please see the website for the current organizers and contact info. Future organizers may be added to the Github organization [workshop-user-interfaces](https://github.com/workshop-user-interfaces). As always with Github pages, the website is based on [Jekyll](https://jekyllrb.com/) using a bare Jekyll basic project (see [Tutorials](https://jekyllrb.com/docs/step-by-step/01-setup/)).

## Local development

```sh
bundle install
bundle exec jekyll serve
```

The site is then available at <http://localhost:4000>.

## User Manual

### Change Workshop Description

The workshop description is fixed for every edition of the workshop and can be changed in the file `_config.yml` in the `description` field.

### Update to current edition

Each edition has its own folder in `_editions`, with the edition page in
`_editions/<year>/index.markdown`.

Be sure to add the following to the front matter of the current edition
(and remove it from the past edition):

```yaml
permalink: /
redirect_from:
  - /editions/20xy
```

Where `20xy` is the current edition you prepared in the corresponding file
`_editions/20xy/index.markdown`.

Feel free to copy the general content as a template from previous editions and adapt it. You are completely free to add your own content in the markdown section of the file. Be sure to use proper markdown syntax througout the file.

Older editions use an explicit permalink such as `/editions/2025/` so their
public URLs remain stable.

### Repository layout

```text
_editions/
  2025/
    index.markdown       # edition page
  2026/
    index.markdown
_program/
  2025/
    11-27/
      1400-opening.markdown
      1430-rojickova.markdown
  2026/
    _template.markdown   # ignored by Jekyll, copy it for new items
_includes/
  program.html           # generates the timetable
_sass/
  _program.scss          # timetable and accordion styling
```

`_editions` contains the edition pages. `_program` is a Jekyll collection
with `output: false`: the talk files are read as data and rendered as part
of their edition page, but are not published as separate pages. Jekyll
requires collection directories at the top level, so the year-named
subfolder in `_program` mirrors the edition's folder in `_editions`.

### Adding a program item

Create a Markdown file in `_program/<year>/<MM-DD>/`, for example
`_program/2026/11-26/1400-example-talk.markdown`:

```markdown
---
edition: 2026
date: "2026-11-26"
start: "14:00"
end: "14:30"          # optional
type: talk
title: "Title of the talk"
speakers: "First Last"
room: "Room Z 336"    # optional
---

The abstract goes here. Markdown is supported.
```

Leave the body empty for items that have no abstract. The item is then
shown as a normal timetable entry without an accordion.

The following front matter keys are supported:

| Key        | Required | Description                                                        |
| ---------- | -------- | ------------------------------------------------------------------ |
| `edition`  | yes      | Edition year, for example `2026`                                   |
| `date`     | yes      | Day of the item, `YYYY-MM-DD`                                      |
| `start`    | yes      | Start time, preferably zero-padded (`09:30`, `14:00`)              |
| `end`      | no       | End time                                                           |
| `type`     | no       | `talk` (default), `break`, `lunch`, `demo`, `social`, `opening`, `closing`, `other` |
| `title`    | yes      | Title or label                                                     |
| `speakers` | no       | Speaker(s), displayed below the title                              |
| `room`     | no       | Room for this item; the first room of a day is used as fallback    |
| `canceled` | no       | Set to `true` to strike through the title                          |
| `note`     | no       | Extra note below the item, e.g. a cancellation reason              |

Zero-padded start times are recommended because program items are sorted by
their `start` value.

### Breaks, lunch and other non-talk items

```markdown
---
edition: 2026
date: "2026-11-27"
start: "15:30"
type: break
title: "Coffee break"
---
```

```markdown
---
edition: 2026
date: "2026-11-27"
start: "12:30"
type: lunch
title: "Lunch"
---
```

```markdown
---
edition: 2026
date: "2026-11-27"
start: "16:30"
type: demo
title: "Demo Session"
---
```

### Cancelled talks

```markdown
---
edition: 2025
date: "2025-11-28"
start: "12:00"
type: talk
title: "Persona by Prompt"
speakers: "Nora Havel"
canceled: true
note: "Canceled due to illness"
---
```

### Day headings and rooms

The day headings are generated from the item dates. To use a custom heading
or a room for the whole day, add `program_days` to the edition front matter:

```yaml
program_days:
  - date: "2026-11-26"
    label: "Thursday, 26.11.2026"
    location: "Room Z 336, HTW Dresden"
  - date: "2026-11-27"
    label: "Friday, 27.11.2026"
    location: "Room Z 336, HTW Dresden"
```

### Enabling the generated program on an edition page

In the edition's `index.markdown`, replace the hand-written program table with:

```markdown
## Program
{: .extra-space-bottom }

{% include program.html %}
```

The include uses `page.year` by default. An explicit year can be passed with
`{% include program.html edition=2025 %}`.

If there are no program items for the edition, the include shows
`page.program_placeholder` (or "The program will be announced soon.").
The 2026 edition uses `tba`.

Older editions keep their existing hand-written tables until their program is
migrated. To migrate one, split the table into one file per entry as described
above and replace the table with the include.
