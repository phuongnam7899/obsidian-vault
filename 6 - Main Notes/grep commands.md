2025-07-10 15:13

Tags: [[Linux]] 

---

- Basic:
```sh
grep [options] pattern [file...]
```

# Options
## Basic
| Option | Description                                                   | Example                    |
| ------ | ------------------------------------------------------------- | -------------------------- |
| -i     | Case-==insensitive== search                                   | grep -i "error" file.txt   |
| -n     | Show ==line numbers==                                         | grep -n "pattern" file.txt |
| -v     | ==Invert== match (show non-matching lines)                    | grep -v "debug" file.txt   |
| -w     | Match ==whole words== only                                    | grep -w "test" file.txt    |
| -c     | ==Count== matching lines                                      | grep -c "error" file.txt   |
| -l     | ==List files== ==containing== pattern                         | grep -l "TODO" *.txt       |
| -L     | ==List files NOT containing== pattern                         | grep -L "TODO" *.txt       |
| -r     | ==Recursive== search in directories                           | grep -r "pattern" /path/   |
| -R     | Recursive with symlinks                                       | grep -R "pattern" .        |
| -q     | ==Quiet== mode (no output, exit status only)                  | grep -q "pattern" file.txt |
| -o     | Let the output be only the matching parts, not the whole line |                            |

## Context Options
| Option | Description                         | Example                        |
| ------ | ----------------------------------- | ------------------------------ |
| -A n   | Show n lines after match            | grep -A 3 "error" file.txt     |
| -B n   | Show n lines before match           | grep -B 3 "error" file.txt     |
| -C n   | Show n lines before and after match | grep -C 5 "exception" file.txt |

## Regular Expression Options

| Option | Description                      | Example                            |                    |
| ------ | -------------------------------- | ---------------------------------- | ------------------ |
| -E     | Extended regex (same as egrep)   | grep -E "pattern1\\                | pattern2" file.txt |
| -F     | Fixed strings (no regex, faster) | grep -F "literal.string" file.txt  |                    |
| -e     | Specify multiple patterns        | grep -e "error" -e "warn" file.txt |                    |
| -f     | Read patterns from file          | grep -f patterns.txt file.txt      |                    |

## File Filtering Options

| Option                       | Description                        | Example                                        |
| ---------------------------- | ---------------------------------- | ---------------------------------------------- |
| --include                    | Only search files matching pattern | grep -r --include="*.java" "class" .           |
| --exclude                    | Skip files matching pattern        | grep -r --exclude="*.log" "error" .            |
| --exclude-dir                | Skip directories                   | grep -r --exclude-dir=node_modules "pattern" . |
| --binary-files=without-match | Skip binary files                  | grep --binary-files=without-match "text" *     |

## Common Regex Patterns

|Pattern|Description|Example|
|---|---|---|
|^pattern|Line starts with pattern|grep "^Error" file.txt|
|pattern$|Line ends with pattern|grep "completed$" file.txt|
|^$|Empty lines|grep "^$" file.txt|
|.|Any single character|grep "a.c" file.txt|
|.*|Zero or more characters|grep "start.*end" file.txt|
|[0-9]|Any digit|grep "[0-9]" file.txt|
|[a-zA-Z]|Any letter|grep "[a-zA-Z]" file.txt|
|[^0-9]|Not a digit|grep "[^0-9]" file.txt|


# Common use cases
| Use Case                   | Command                                  | Description                          |                           |                                    |
| -------------------------- | ---------------------------------------- | ------------------------------------ | ------------------------- | ---------------------------------- |
| Find errors in logs        | grep -i "error" /var/log/app.log         | Case-insensitive error search        |                           |                                    |
| Multiple severity levels   | grep -E "error\\                         | warn\\                               | fail" app.log             | Find errors, warnings, or failures |
| Count occurrences          | grep -o "pattern" file.txt \\            | wc -l                                | Count pattern occurrences |                                    |
| Today's log entries        | grep "$(date '+%Y-%m-%d')" app.log       | Filter by today's date               |                           |                                    |
| Context around errors      | grep -A 5 -B 5 "Exception" app.log       | Show 5 lines before/after exceptions |                           |                                    |
| Search specific file types | grep -r --include="*.java" "TODO" .      | Only search Java files               |                           |                                    |
| Exclude directories        | grep -r --exclude-dir=target "pattern" . | Skip target directory                |                           |                                    |

---
# References


- Create a static site in storage account with the HTML that we sent
- When