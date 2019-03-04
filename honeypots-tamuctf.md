# TAMUctf 2019 - All Honeypots

All of the challenges give us some malware logs(or even the malwares) to analyze and find something most common(CVE's, malware downloaded, username, ip's), consdering that the challs are kind of easy, i'll just post a simple solve for all of them and not chall per chall, i swear i'm not lazy, but i can't see need to post one by one.

## Solves

In cowrie i find the ip doing this command:

    sed -e '/\n/g' < cowrie.json cowrie.json.1 cowrie.json.2 cowrie.json.3 cowrie.json.4 lastlog.txt lastlog.txt.1 lastlog.txt.2 cowrie.json.2018-11-14 cowrie.json.2018-11-13 cowrie.json.2018-11-12 tty/20181115-035641-None-2i.log tty/20181115-143558-None-0i.log | sort | uniq -c | sort -nr | grep -o '[0-9]\{1,3\}\.[0-9]\{1,3\}\.[0-9]\{1,3\}\.[0-9]\{1,3\}' > ips

    sed -e 's/\s/\n/g' < ips | sort | uniq -c | sort -nr | head -10

    42022 211.143.198.161
    
    17598 172.25.0.2
    
    9958 109.248.9.103
    
    9920 5.188.86.173
    
    9320 5.188.86.212
    
    8660 5.188.86.172
    
    7916 109.248.9.101
    
    4790 5.188.86.216
    
    4114 109.248.9.102
    
    3986 110.52.28.54

The first flag is 211.143.198.161

In every chall i used this command:

    sed -e '/\n/g' < some_files.log some_files.json | sort | uniq -c | sort -nr | grep -o 'something'

Just changing something by need, the files, the grep or the **sed -e**, because of that i think this write-up is more than enough, now I'll show you some things that I had to do differently, which I find interesting to show.

## Glastopf - 2
What are the three most commonly requested url besides / get or post? (no slashes, all lowercase, alphabetical (`1.ext, a.ext, b.ext`))

**Solve**

    sed -e 's/\s/\n/g' < glastopf.log glastopf.log.1 glastopf.log.2 glastopf.log.3 glastopf.log.4 glastopf.log.2018-11-14 glastopf.log.2018-11-13 glastopf.log.2018-11-12 ../db/*  | sort | uniq -c | sort -nr | head -50

Here we have a order to follow, confg.php, 1.php, qq.php,

## Dionaea - 2
What is the common name for the most commonly downloaded malware?

**Solve**

To find the flag, we don't just have to find the most common, but we have to find the analysis by the virustotal using the md5.

Doing this we can find the WannaCry(md5: faaefef2bf9feaa56fd0866bc5a2872e)


And that's it, using this ideas it's possible to kill all the challs.
