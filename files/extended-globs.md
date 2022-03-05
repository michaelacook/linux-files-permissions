# Extended Globs
- More powerful globs 
- match more than one character 
- group patterns inside parentheses by surrounding them with an outter set of parentheses
- standard globs can be used inside extended globs
- specify number of occurrences 
- match one group or another
- invert matches 
- similar to regular expressions 
- in some distributions, need to be enabled 
- To determine if extended globs are enabled, run `shopt | grep "extglob"` 
  - If they are not enabled, run `shopt -s extglob`
  - To make this persistent between user sessions it must be added the `~/.bashrc`

|Function|Extended Glob|Regular Expression|
|-|-|-|
|Group characters|(abc)|(abc)|
|Multiple patterns|(abc\|def)|(abc\|def)|
|Invert match|!(abc) ^(abc)||

### Specifying occurrences 

|Occurrences|Extended Glob|Regular Expression|
|-|-|-|
|0 or 1|?(abc)|(abc)?|
|Exactly 1|@(abc)|(abc)|
|1 or more|+(abc)|(abc)+|
|0 or more|\*(abc)|(abc)*|
