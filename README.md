# Workshop Website User Interfaces & Visualization

The User Interfaces & Visualization workshop has been held at the University of Applied Sciences Dresden almost every year since 1992. It is traditionally organized by the Faculty of Computer Science/Mathematics and the Faculty of Electrical Engineering of the Czech Technical University in Prague. It offers young scientists in particular the opportunity to present and discuss their current research results. The workshop is open to undergraduate and PhD students from both universities. The main goal is to create a credible simulation of a process where results of scientific work are presented to an international audience.

## Description

This repository holds the website for the workshop with Github Pages under [workshop-user-interfaces.github.io](https://workshop-user-interfaces.github.io/). Please see the website for the current organizers and contact info. Future organizers may be added to the Github organization [workshop-user-interfaces](https://github.com/workshop-user-interfaces). As always with Github pages, the website is based on [Jekyll](https://jekyllrb.com/) using a bare Jekyll basic project (see [Tutorials](https://jekyllrb.com/docs/step-by-step/01-setup/)).

## User Manual

### Change Workshop Description

The workshop description is fixed for every edition of the workshop and can be changed in the file `_config.yml` in the `description` field.

### Update to current edition

Prepare a new markdown file for the current year in the folder `_editions`.

Be sure to add the following to the front matter of the file (and remove it from the past edition):

```yaml
permalink: /
redirect_from:
  - /editions/20xy
```

Where `20xy` is the current edition you prepared in the corresponding markdown file `_editions/20xy.markdown`.

Feel free to copy the general content as a template from previous editions and adapt it. You are completely free to add your own content in the markdown section of the file. Be sure to use proper markdown syntax througout the file. 
