Sometimes you may need to make a wordlist yourself as one might not
be readily available. All the musicals can be found at:
https://en.wikipedia.org/wiki/List_of_the_longest-running_Broadway_shows
you can either make a script to filter the table out, or you can use
a program such as:
https://wikitable2csv.ggor.de/
in order to automatically parse the table. You may need to do further
editing and trial and error to find how the wordlist should be formatted
such as no spaces, all lowercase, etc. In addition to a wordlist, rules
can be applied! Rules are just ways of modifying your wordlist programatically
to test even more possibilities! below was the command that can be used:

> hashcat -a 0 -m 0 test.hash musicals.txt -r path/to.rule

-r is the rule to be used


Below are the plaintext passwords with what rule can be used

1. cats (no rule needed)
2. grease (no rule needed)
3. annie32 (used dive.rule)
4. notlimah (used dive.rule or best64.rule)
5. 0kl@h0m@! (used dive.rule or leetspeak.rule)
6. dr8eamgirlsdr8eamgirls (used dive.rule)
