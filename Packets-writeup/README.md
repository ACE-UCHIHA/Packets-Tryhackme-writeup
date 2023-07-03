<h1 align="center">
  <br>
  <a href="https://tryhackme.com/room/packets"><img src="/Packets-writeup/img/img1.PNG"></a>
  <br>
  Packets Writeup
  <br>
</h1>

## Table of Contents

- [Task 1](#lets-start-from-task-1-in-task-1-theyre-telling-you-to-download-the-pcapng-file-so-obviously-download-it)
- [Task 2](#now-lets-get-into-task-2-in-task-2-the-first-question-is-)
  -    [Question 1](#q1-when-was-the-first-packet-captured-format--year-month-date-hoursminutesseconds)
  -    [Question 2](#q2-when-was-the-last-packet-captured-format--year-month-date-hoursminutesseconds)
  -    [Question 3](#q3-how-many-packets-were-captured)
  -    [Question 4](#q4-what-is-the-sha256-hash-of-the-file)
  -    [Question 5](#q5-what-is-the-md5-hash-of-the-file)
- [Task 3](#task-3)
  -    [Question 1](#q1-how-many-icmp-packets-were-captured-with-parcentage)
  -    [Question 2](#q2-there-was-an-icmp-ping-request-packet-which-did-not-receive-any-response-back-what-is-the-packet-number)
  -    [Question 3](#q3-what-was-thr-source-ip-of-the-above-packet)
  -    [Question 4](#q4-what-was-thr-destination-ip-of-the-above-packet)
  -    [Question 5](#q5-what-is-the-length-of-the-packet)
  -    [Question 6](#q6-in-which-country-standard-time-was-the-packet-captured)
  -    [Question 7](#q7--when-the-packet-was-captured-format--year-month-date-hoursminutesseconds)
  -    [Question 8](#q8-what-is-the-data-value-of-the-packet)
  -    [Question 9](#q9-decode-the-value)
  -    [Question 10](#q10-in-the-decoded-strings-there-was--an-username-and-a-password-what-are-those)          
- [Task 4](#task-4)
  -    [Question 1](#q1--how-many-ftp-packets-were-captured-with-parcentage)
  -    [Question 2](#q2-what-was-the-users-first-username-and-password-that-tried-to-login-to-frp-server-format-usernamepassword)
  -    [Question 3](#q3-what-was-the-users-last-username-and-password-that-tried-to-login-to-frp-server-format-usernamepassword)
  -    [Question 4](#q4-what-was-the-users-last-username-and-password-that-tried-to-login-to-frp-server-format-usernamepassword)
  -    [Question 5](#q5-which-file-is-seems-to-be-malicious-format-file-extension)
  -    [Question 6](#q6-what-is-the-md5-hash-of-the-malicious-file)
  -    [Question 7](#q7-what-is-the-md5-hash-of-the-normal-file)
  -    [Question 8](#q8-what-is-the-file-size-of-malicious-file-format-in-bytes)
  -    [Question 9](#q9-what-is-the-file-size-of-noraml-file-format-in-bytes)
  -    [Question 10](#q10-in-which-which-directory-was-the-normal-file-located)
  -    [Question 11](#q11-in-which-which-directory-was-the-malicious-file-located)
  -    [Question 12](#q12-what-is-the-ip-of-the-device-that-was-infected-by-the-malicious-file)
- [Task 5](#task-5)
  -    [Question 1](#q1-how-many-http-packets-were-captured-with-parcentage)
  -    [Question 2](#q2-what-is-the-file-downloaded-via-http-from-uploaded-files-of-the-website)
  -    [Question 4](#q4--what-is-the-flag-displayed-in-the-file)
  -    [Question 5](#q5-what-was-the-full-request-uri-for-the-file-full-value)
  -    [Question 6](#q6-what-was-the-user-agent-full-value)




## Let's start from Task 1. In task 1 they're telling you to download the pcapng file so obviously download it.

## Now let's get into Task 2. In Task 2 the first question is : 
#### Q1: When was the first packet captured? (Format : Year-Month-Date Hours:Minutes:Seconds)

Okey so we have to open the thmcaptureh4x0r3rr0r.pcapng file in wireshark then we'll see a packet at the top which is no 1 ( numbers are defined in the left first column). After selecting the first file we have to look at the " Packet Details Pane " . If we drop down the first row "Frame 1:" we'll be able to see the content that was in the Frame 1 . If we look at the contents we'll see a row named Arrival time.
There you'll get the answer of the Q1.

<img src="/Packets-writeup/img/img2.PNG"><br>


#### Q2: When was the last packet captured? (Format : Year-Month-Date Hours:Minutes:Seconds)

This is similar to the Q1 all you have to do is just naviagte to the bottom of the list and select the last packet and look for the date & time like you did in the Q1.
<img src="/Packets-writeup/img/img3.PNG"><br>

#### Q3: How many packets were captured?

To see how many packets were captured you have look at the bottom of you're wiresahrk UI there is a status bar there. There you should see how many packets are there and how many are displayed.
<img src="/Packets-writeup/img/img4.PNG"><br>

#### Q4: What is the SHA256 hash of the file?

To get the SHA256 hash of a file first select the file then look at the top of you're wireshark UI. There is a Toolbar. On the toolbar click the Statistics option then click the capture file properties or you can use  Ctrl+Alt+Shift+C and a page should pop up there you'll be able the find the SHA256 hash.
<img src="/Packets-writeup/img/img5.PNG"><br>
<img src="/Packets-writeup/img/img6.png"><br>
<img src="/Packets-writeup/img/img7.PNG"><br>

 #### Q5: What is the MD5 hash of the file?

So I used a Python script to get the hash. here's the script:

### MD5 encryption py script

```python
import hashlib

def calculate_md5(file_path):
    with open(file_path, 'rb') as f:
        md5_hash = hashlib.md5()
        for chunk in iter(lambda: f.read(4096), b''):
            md5_hash.update(chunk)
    return md5_hash.hexdigest()

extracted_file_path = r'path/to/your/pcapng/file'
md5_hash = calculate_md5(extracted_file_path)
print("MD5 Hash:", md5_hash)
```


## Task 3
#### Q1: How many ICMP packets were captured? (with parcentage)

This is similar to the [Task 2](#now-lets-get-into-task-2-in-task-2-the-first-question-is-) [Question 3](#q3-how-many-packets-were-captured) but slightly different because you have too filter out the other packets that are not ICMP(Internet Control Message Protocol). So for that go to the display filter and input icmp then hit enter and you should get only the ICMP packets on your screen. Now look at the status bar at the bottom there you should see how many ICMP packets were captured with percentage.

#### Q2: There was an ICMP ping request packet, which did not receive any response back. What is the packet number?

First filter the ICMP packets then search for the packets with no response there should be written (no response found!) on the right of the packet.
<img src="/Packets-writeup/img/img8.PNG"><br>
#### Q3: What was thr source IP of the above packet?

after you locate that package look at the third column of the list (the third column is for the source IP).
<img src="/Packets-writeup/img/img9.PNG"><br>
#### Q4: What was thr destination IP of the above packet?

after you locate that package look at the fourth column of the list (the fourth column is for the destination IP).
#### Q5: What is the length of the packet?

after you locate that package look at the sixth column of the list (the sixth column is for the length).
<img src="/Packets-writeup/img/img10.PNG"><br>
#### Q6: In which country standard time was the packet captured?

For this select the packet similar to [Task 2](#now-lets-get-into-task-2-in-task-2-the-first-question-is-) [Question 1](#q1-when-was-the-first-packet-captured-format--year-month-date-hoursminutesseconds) look for the Arrival time and you should be able to see In which country standard time was the packet captured .
#### Q7:  When the packet was captured? (Format : Year-Month-Date Hours:Minutes:Seconds)

It's in the Arrival time too.
#### Q8: What is the data value of the packet?

Select the packet then look at the Packet Details Pane there you should see a drop-down bar named Internet Control Message Protocol. Drop it down.

Now drop-down the bar named Data and you should get a field name & Value. right click on it and copy the value.
<img src="/Packets-writeup/img/img11.PNG"><br>
#### Q9: Decode the value.

The value is in hex so decode it however you want. Use a tool or script. You should be able to do this much by your self.
#### Q10: In the decoded strings there was  an username and a password, what are those?

After decoding it you should get the username and password in the decoded value.

## Task 4

#### Q1:  How many FTP packets were captured? (with parcentage)

It's same as the [Task 3](#task-3) [Question 1](#q1-how-many-icmp-packets-were-captured-with-parcentage) just filter the FTP packets.

#### Q2: What was the user's first username and password that tried to login to frp server? (Format: username:password)

Use this for filter for filtering the USER packets.
```bash
ftp.request.command == "USER"
```
Use this for filter for filtering the PASS packets.
```bash
ftp.request.command == "PASS"
```
#### Q3: What was the user's last username and password that tried to login to ftp server? (Format: username:password)

It's same as [Task 4](#task-4) [Question 2](#q2-what-was-the-users-first-username-and-password-that-tried-to-login-to-frp-server-format-usernamepassword) just figure out whuch one was the first one and last one by yourself.

#### Q4: How many files were downloaded from the FTP server?

Use this filter to see the packtes that where captured when dowloading the files in FTP
```bash
ftp.request.command == "RETR"
```
#### Q5: Which file is seems to be malicious? (Format: File Extension)


If you're a Linux user then export those ftp files then take their hashes and check them on [virus total](https://www.virustotal.com/gui/home/search). Then you'll know which one is malicious.I have shown how to export the files in [Task 5](#task-5)  [Question 4](#q4--what-is-the-flag-displayed-in-the-file),
here's the URL of the virustotal website for checking the hash.
```bash
https://www.virustotal.com/gui/home/search
```

#### Q6: What is the MD5 hash of the malicious file? 

Okey so the malicious file CyberSec.pdf has a batch payload in it so if you download it windowsa your defender will remove it. So download it on linux and use the [MD5 encryption py script](#md5-encryption-py-script).
and don't worry windows there is nothing to fear because ["I am here"](https://github.com/ACE-UCHIHA). It took me some time but I got a website where you can analyze the pcapng file and the website also provides a tables with different infornmation about the files that are in the pcapng file like the CyberSrc.pdf, thm.png etc. and yes you guessed it in those information there is the MD5 hash of those files too. 
website URL: 
```url
https://lab.dynamite.ai/
```
go to the website upload the pcapng file then look at the left sidebar there should be a option named "Artifacts" click on that then go to the bottom of the page and you  should be able to see a table name "Interactive Data Table". In this table you'll find the MD5 hash.

#### Q7: What is the MD5 hash of the normal file? 

The normal file is thm.png to get the file you can use the methods in the [Task 4](#task-4) [Question 6](#q6-what-is-the-md5-hash-of-the-malicious-file) but now you can use both methods in windows and linux.

#### Q8: What is the file size of malicious file? (Format: In Bytes)

for this click on the malicious file look at the Packet Details Pane there you should see a row [Command response bytes: *****] . find this in the Packet Details Pane and you'll get the file size in bytes.

#### Q9: What is the file size of noraml file? (Format: In Bytes)

Same as [Task 4](#task-4) [Question 8](#q8-what-is-the-file-size-of-malicious-file-format-in-bytes) .

#### Q10: In which which directory was the normal file located?


for this click on the normal file look at the Packet Details Pane there you should see a row [Current working directory: ***-***] find this in the Packet Details Pane and you'll get the directory.


#### Q11: In which which directory was the malicious file located?

This is same as the [Task 4](#task-4) [Question 10](#q10-in-which-which-directory-was-the-normal-file-located) but you won't see any directory there because it was in the root directory. so there isn't any directory defined.

#### Q12: What is the IP of the device that was infected by the malicious file?

locate the malicious file then look for the source IP . and that is the IP you were looking for.



## Task 5:

#### Q1: How many HTTP packets were captured? (with parcentage)

same as [Task 3](#task-3) [Question 1](#q1-how-many-icmp-packets-were-captured-with-parcentage) & [Task 4](#task-4) [Question 1](#q1--how-many-ftp-packets-were-captured-with-parcentage)

#### Q2: What is the file downloaded via HTTP from uploaded files of the website?

So to get the file downloloaded via HTTP we need to filter the GET requests. Use this for that:
```bash
http.request.method == "GET"
```
then look for the file that was in the /uploads directory

#### Q4:  What is the flag displayed in the file?


To get the file click the File option in the tool bar then click Export Objects then click HTTP since the file was downloaded via HTTP. After that you'll get the list of files that were transmitted using HTTP . Now download the file that was in the /uploads directory.
<img src="/Packets-writeup/img/img12.PNG"><br>
<img src="/Packets-writeup/img/img13.png"><br>

#### Q5: What was the full request URI for the file? (Full Value)

click on the packets of the file then go to the Packets detail pane then drop-down the Hypertext Transfer Protocol after dropping it down you'll see 
```bash
[Full request URI: http://the/url/of/the/file]
```
<img src="/Packets-writeup/img/img14.PNG"><br>
#### Q6: What was the User-Agent? (Full Value)

Same as [Task 5](#task-5) [Question 5](#q5-what-was-the-full-request-uri-for-the-file-full-value) drop-down the Hypertext Transfer Protocol after dropping it down you'll see 
```bash
User-Agent: Mozilla/5.0 (***; Linux x**_**; rv:***.*) Gecko/******** Firefox/***.*\r\n
```

#

<h3>HOPE THIS WRITEUP HELPED YOU AND YOU LEANRED SOMETHING NEW </h3>
</hr>
<h2>IF YOU LIKED IT THEN LEAVE A STAR ^3^</h2>
<h1>PEACE <3</h1>
 
