# File

Basic file operations for use in Storyscript. This should be used for working
with files temporarily as files are deleted after an app is finished running.

```
# Create a directory
file mkdir path:"/tmp"

# Write some content to a file.
file write path:"/tmp/foo" content:"Hello world!"

# Read the file just written to.
str = file read path:"/tmp/foo"

# Write some content to a file as raw bytes.
file write path:"/tmp/foo" content:"Hello world!" binary: true

# Read the file just written to as a raw data
str = file read path:"/tmp/foo" binary: true

# Read the file just written to as a string
str = file read path:"/tmp/foo" binary: false

# Read and write raw bytes
http server as client
  when client listen method:"post" path:"/" as r
    # the file service receives the zip file,
    # and we write it to the filesystem using raw
    # bytes.
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

# Check if tmp is a directory
isdir = file isDir path: "/tmp"

# Check if foo is a file
isfile = file isFile path: "/tmp/foo"

# Remove a file
file removeFile path: "/tmp/foo"

# Remove a directory and it's contents
file removeDir path: "/tmp"
```
