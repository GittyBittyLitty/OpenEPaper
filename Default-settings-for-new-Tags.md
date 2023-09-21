By default, new Tags are not filled with content after they are connected. To assign the same content to each new Tag (for example, to an API), the following can be done:

A file with the name tag_defaults.json must be created in the root directory.

The content of the file can be taken from a configured Tag. Two parameters are important: **contentMode** and **modecfgjson**.

With the following content, all new Tags or all Tags that have no content assignment and have been rebooted are set to "Count days" and the counter is set to 1.

`{
  "contentMode": 2,
  "modecfgjson": "{\"counter\":\"1\",\"thresholdred\":\"\"}"
}`