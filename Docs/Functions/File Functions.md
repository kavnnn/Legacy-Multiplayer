# File Functions

---

## `fileOpen`

### Description
Opens a file relative to the current executing resource sandbox. Automatically creates missing parent directories when opening in write or append modes.

### Parameters
| Parameter | Type | Description |
|---|---|---|
| path | string | Resource-relative path to the file. |
| mode | string | *(Optional)* Open mode (`"r"`, `"w"`, `"a"`, `"r+"`, `"w+"`, `"a+"`, `"rb"`, `"wb"`, etc. Default: `"r"`). |

### Return Type
```text
CFile (or nil)
```

### Return Value
Returns an open `CFile` handle userdata on success, or `nil` if the file could not be opened or accessed.

### Example
```lua
local file = fileOpen("data/config.json", "w")
```

---

## `fileClose`

### Description
Closes an open file handle and releases all underlying OS file locks.

### Parameters
| Parameter | Type | Description |
|---|---|---|
| file | CFile | The open file handle to close. |

### Return Type
```text
boolean
```

### Return Value
Returns `true` if the file was successfully closed, or `false` if the handle is invalid or was already closed.

### Example
```lua
fileClose(file)
```

---

## `fileRead`

### Description
Reads up to `size` bytes from an open file starting from its current seek position. Preserves binary data without corruption.

### Parameters
| Parameter | Type | Description |
|---|---|---|
| file | CFile | The open file handle. |
| size | integer | Number of bytes to read. |

### Return Type
```text
string (or nil)
```

### Return Value
Returns the read bytes as a `string`, or `nil` if the handle is invalid or closed.

### Example
```lua
local chunk = fileRead(file, 1024)
```

---

## `fileReadAll`

### Description
Reads all remaining bytes from the current seek position to the end of the file.

### Parameters
| Parameter | Type | Description |
|---|---|---|
| file | CFile | The open file handle. |

### Return Type
```text
string (or nil)
```

### Return Value
Returns the entire remaining contents as a `string`, or `nil` on error.

### Example
```lua
local content = fileReadAll(file)
```

---

## `fileWrite`

### Description
Writes raw string or binary data to an open file handle.

### Parameters
| Parameter | Type | Description |
|---|---|---|
| file | CFile | The open file handle. |
| data | string | The string or binary data to write. |

### Return Type
```text
integer
```

### Return Value
Returns the number of bytes successfully written to the file, or `0` on failure.

### Example
```lua
local bytesWritten = fileWrite(file, "Hello Legacy Server!\n")
```

---

## `fileSeek`

### Description
Sets the read/write position indicator for an open file.

### Parameters
| Parameter | Type | Description |
|---|---|---|
| file | CFile | The open file handle. |
| offset | integer | Byte offset to seek. |
| origin | string | *(Optional)* Seek origin: `"set"` (from beginning), `"current"` / `"cur"` (from current pos), `"end"` (from end). Default: `"set"`. |

### Return Type
```text
boolean
```

### Return Value
Returns `true` if repositioning succeeded, or `false` on failure.

### Example
```lua
fileSeek(file, 0, "set") -- Seek to beginning
fileSeek(file, 0, "end") -- Seek to end
```

---

## `fileTell`

### Description
Retrieves the current byte position indicator of an open file.

### Parameters
| Parameter | Type | Description |
|---|---|---|
| file | CFile | The open file handle. |

### Return Type
```text
integer (or nil)
```

### Return Value
Returns the current byte offset as an integer, or `nil` if the handle is invalid.

### Example
```lua
local position = fileTell(file)
```

---

## `fileFlush`

### Description
Flushes unwritten buffered data of an open file to the physical disk.

### Parameters
| Parameter | Type | Description |
|---|---|---|
| file | CFile | The open file handle. |

### Return Type
```text
boolean
```

### Return Value
Returns `true` on success, or `false` on failure.

### Example
```lua
fileFlush(file)
```

---

## `fileSize`

### Description
Retrieves the total size in bytes of an open file handle.

### Parameters
| Parameter | Type | Description |
|---|---|---|
| file | CFile | The open file handle. |

### Return Type
```text
integer (or nil)
```

### Return Value
Returns the file size in bytes, or `nil` if the handle is invalid.

### Example
```lua
local size = fileSize(file)
```

---

## `fileGetSize`

### Description
Retrieves the size in bytes of a file on disk without having to manually open and close a handle.

### Parameters
| Parameter | Type | Description |
|---|---|---|
| path | string | Resource-relative path to the file. |

### Return Type
```text
integer (or nil)
```

### Return Value
Returns the file size in bytes, or `nil` if the file does not exist or is outside the sandbox.

### Example
```lua
local size = fileGetSize("data/config.json")
```

---

## `fileExists`

### Description
Checks whether a file exists and is a regular file within the resource sandbox.

### Parameters
| Parameter | Type | Description |
|---|---|---|
| path | string | Resource-relative path to check. |

### Return Type
```text
boolean
```

### Return Value
Returns `true` if the file exists, otherwise `false`.

### Example
```lua
if fileExists("data/config.json") then
    print("Found config!")
end
```

---

## `fileDelete`

### Description
Deletes a file within the resource sandbox.

### Parameters
| Parameter | Type | Description |
|---|---|---|
| path | string | Resource-relative path to delete. |

### Return Type
```text
boolean
```

### Return Value
Returns `true` if the file was deleted, or `false` if it does not exist or deletion failed.

### Example
```lua
fileDelete("data/temp.txt")
```

---

## `fileRename`

### Description
Renames or moves a file within the resource sandbox.

### Parameters
| Parameter | Type | Description |
|---|---|---|
| oldPath | string | Current resource-relative path. |
| newPath | string | New resource-relative path. |

### Return Type
```text
boolean
```

### Return Value
Returns `true` if renamed, or `false` on failure.

### Example
```lua
fileRename("data/old_config.json", "data/config.json")
```

---

## `directoryExists`

### Description
Checks whether a directory exists within the resource sandbox.

### Parameters
| Parameter | Type | Description |
|---|---|---|
| path | string | Resource-relative directory path. |

### Return Type
```text
boolean
```

### Return Value
Returns `true` if the directory exists, otherwise `false`.

### Example
```lua
if directoryExists("storage") then
    print("Directory exists")
end
```

---

## `directoryCreate`

### Description
Recursively creates a directory (and any missing parent directories) inside the resource directory.

### Parameters
| Parameter | Type | Description |
|---|---|---|
| path | string | Resource-relative directory path to create. |

### Return Type
```text
boolean
```

### Return Value
Returns `true` if created or already exists, otherwise `false`.

### Example
```lua
directoryCreate("storage/backups")
```

---

## `directoryDelete`

### Description
Recursively deletes a directory and its contents within the resource sandbox. (Cannot delete the root resource directory itself).

### Parameters
| Parameter | Type | Description |
|---|---|---|
| path | string | Resource-relative directory path to delete. |

### Return Type
```text
boolean
```

### Return Value
Returns `true` on success, or `false` on failure.

### Example
```lua
directoryDelete("storage/temp")
```

---

## `directoryList`

### Description
Lists all entries (files and subdirectories) inside a resource directory.

### Parameters
| Parameter | Type | Description |
|---|---|---|
| path | string | *(Optional)* Resource-relative directory path. Default: `""` (resource root). |

### Return Type
```text
table (array of strings)
```

### Return Value
Returns a 1-indexed Lua table containing the filenames / directory names within the folder.

### Example
```lua
local entries = directoryList("data")
for i, name in ipairs(entries) do
    print(i, name)
end
```

---

## `CFile` Object Methods

In addition to procedural functions, `CFile` instances support object-oriented method syntax:

- `file:read(size)` — Reads `size` bytes.
- `file:readAll()` — Reads all remaining bytes.
- `file:write(data)` — Writes data string.
- `file:seek(offset, [origin])` — Repositions file pointer.
- `file:tell()` — Gets current file pointer position.
- `file:flush()` — Flushes buffer to disk.
- `file:size()` — Returns file size in bytes.
- `file:close()` — Closes the file handle.
- `file:isOpen()` — Checks if file handle is currently open.
- `file:getPath()` — Returns relative path of the file.
- `file:getResource()` — Returns owning resource name.
- `file:getMode()` — Returns open mode string.
