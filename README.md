# File

Basic file operations for use in Storyscript.

```
# Write some content to a file.
file write path:"/tmp/foo" content:"Hello world!"

# Read the file just written to.
str = file read path:"/tmp/foo" type:"string"

# Check if foo exists.
exists = file exists path:"/tmp/foo"
```
