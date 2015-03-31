# Basic Command Line Exercises

## Clone the repo

    git clone https://github.com/juliusv/cli_exercises.git
    cd cli_exercises

## Exercises

1. How many lines does the "words" file contain?
2. How many lines in the "words" file contain the word "foo" anywhere on the line?
3. Print the "words" file in reverse lexicographic order
4. Print the lines of the "words" file which contain "foo" in reverse lexicographic order
5. Same as 4., but exclude words containing single quotes
6. Same as 5., but replace all occurrences of "foo" with "fa"
7. How many files underneath /etc end with ".conf"?
8. Which lines are different between the "words" and "words2" dictionary files?
9. How long has it been since your computer was started?
10. How many free bytes do you have left on your root (/) filesystem?
11. How many bytes does the "cli_exercises" directory take up?
12. How large is the "words" file in bytes?
13. How many unique visitors (unique IP addresses) does the "access.log" file contain?
14. Same as 13., but restrict this to only hits on March 8th
15. Same as 14., but instead of counting them, write the visitors' IP addresses to a new file, named "access_mar_8.log"
16. Print the first and last 20 lines of "access.log" into a new file named "short.log"

## Answers

1. `wc -l words`

      or

   `wc -l <words`

      or

   `cat words | wc -l`
2. `grep foo words | wc -l`
3. `sort -r words`
4. `grep foo words | sort -r`
5. `grep foo words | grep -v "'" | sort -r`

      or

   `grep foo words | grep -v \' | sort -r`
6. `grep foo words | grep -v "'" | sed 's/foo/fa/' | sort -r`
7. `find /etc -name "*.conf" | wc -l`
8. `diff -u words words2`

      or

   `diff -u words{,2}`
9. `uptime -s`
10. `df -h /`
11. `du`
12. `ls -l words | cut -d" " -f5`

      or

    `wc -c words`
13. `cut -f1 -d" " access.log | sort -u | wc -l`

      or

    `awk '{ print $1 }' access.log | sort -u | wc -l`
14. `grep '07/Mar/2004' access.log | cut -f1 -d" " | sort -u | wc -l`
15. `grep '07/Mar/2004' access.log | cut -f1 -d" " | sort -u > access_mar_8.log`
16. `head -n 20 access.log > short.log; tail -n 20 access.log >> short.log`

      or

    `(head -n 20 access.log && tail -n 20 access.log) > short.log`
