# Recon - It's to KeyZ 250 - NeverlanCTF
## Chall
It look like N30 has been keeping passwords secret with some software he wrote, but he should know better than to rely on proprietary software for security.

It looks like he left the repo public too!

(file passwords.keyz)

## Solving
To take a look at the repository, i tried to find his github, searching for N30 is not successful, but i found his social pages in https://neverlanctf.com/creators and saw his real name on Linkedin(Zane Durkin), then i searched and found a github.

https://github.com/durkinza

We can see a repository called "KeyZ", and that's it, this is the public repository, we have to clone this 

    $ git clone https://github.com/durkinza/KeyZ.git
    $ cd KeyZ
    $ make
    $ ./key -help
    
    $ Usage: key {-s | -g } -[oqd] file key
       key -[hnkpv] file
	-h		Show help
	-g		Get data
	-n		For returning header values of file (k, v, p)
	-s		Set data
	-o		Set to no overwrite
	-q		For silencing misuse messages
	-d		Set debugging

	(Only available when creating a new key file)
	-k		For setting key value size (default: 32)
	-p		For setting number of rows in file (default: 64)
	-v		For setting max value size of file (default: 331)

Well, -g to get data, so...

    $ ./key -g password.keyz
    $ ERROR(key): no key was specified for key file 'passwords.keyz'

Probably the key is so hidden, right? Well, the answer is no.

    $ cat passwords.keyz
    KEYZ @Kflag,�;�{Z&�7_1
    
@Kflag is a kind suspicious.

    $ ./key -g password.keyz flag
    $ flag{bu7_1ts_pr0pr1etary}

We hit the bull's eye!
