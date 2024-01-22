# Workshop Website

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
