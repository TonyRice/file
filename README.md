# File

Basic file operations for use in Storyscript.

```
# Create a directory
file mkdir path:"/tmp"

# Write some content to a file.
file write path:"/tmp/foo" content:"Hello world!"

# Read the file just written to.
str = file read path:"/tmp/foo" type:"string"

# Read and write raw bytes
http server as client
  when client listen method:"post" path:"/" as r
    if r.file and r.file["body"]
        file write path:"/file.zip" content: r.file["body"]
        # reads the content in raw form
        r write content: (file read path:"/file.zip" raw: true)
    else
        r write content: "Hello World"

# Check if foo exists.
exists = file exists path:"/tmp/foo"

# Create a directory
file mkdir path:"/tmp"
```
