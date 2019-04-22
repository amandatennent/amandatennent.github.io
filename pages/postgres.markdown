---
layout: default
title: Postgres
permalink: /pages/postgres
---
## Some useful snippets of information when using Postgres

### psql
*The interactive terminal for working with Postgres*

List databases:  
`\list`

List tables in current database:  
`\dt`

Switch databases:  
`\connect DifferentDatabase`

Copy data to csv:  
`\copy table_name to '~/Downloads/file_name.csv' delimiter ',' csv header`
