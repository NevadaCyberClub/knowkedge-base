This can be solved pretty quickly using the hashcat program. The command
that I used was:
> hashcat -a 0 -m 0 test.hash rockyou.txt
-a is attack mode
-m is hash type
test.hash is the hashes
rockyou.txt is the dictionary

for more info on hashcat run the command:
> hashcat --help
below are the plaintext passwords in order

1. lovely1
2. 1q2w3e4r
3. 963852741
4. blue123
5. soccer12

creator: Kameron B.
