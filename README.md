# In-Class Exercise 3

# Part 1 Grep

## Tasks

+ Count the number of “ERROR”s in the log file
    <br/> grep "ERROR" logfile.txt
    <br/> 4 "ERROR"s excluding 1 "ERRORS"

+ Find all the “warning”s case insensitive
    <br/> grep -i "warning" logfile.txt
    <br/> [2025-03-01 08:17:45] WARNING: High memory usage detected (78%)
    <br/> [2025-03-01 08:28:33] WARNING: Multiple failed login attempts for user: johnson

+ Find all the lines NOT containing “INFO”
    <br/> grep -nv "INFO" logfile.txt
    <br/> 3, 4, 6, 9, 13, 14

+ Find all the lines that match the whole word “ERROR”
    <br/> grep -wn "ERROR" logfile.txt
    <br/> 4, 6, 9, 13

# Part 2 Sed
## Tasks
+ Print Lines 10-20
    <br/> sed -n "10,20p" sed_practice_file.txt

+ Remove all empty lines
    <br/> sed "/^$/d" sed_practice_file.txt

+ Replace all "apple" with "orange"
    <br/> sed "s/apple/orange/g" sed_practice_file.txt

# Part 3 Awk
## Tasks

+ Find the average salary of all employees
    <br/> awk 'NR > 1 {sum += $3; ++cnt} END {print sum/cnt}' employees.txt
    <br/> 72400

+ Print the names of all the students who got at least a 90
    <br/> awk '$4 >= 90 {print $2}' grades.txt
    <br/> Alex, Claire, Alex

+ Print all the paths and dates of any logs with status 404 OR 500
    <br/> awk 'NR > 1 && ($3 == 404 || $3 == 500) {print $4, $1}' serverlog.txt
