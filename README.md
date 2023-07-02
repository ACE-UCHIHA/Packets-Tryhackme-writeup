# Table of Contents

- [Task1](#Task1)
- [Installation](#installation)
- [Task3](#Task3)
- [Contributing](#contributing)
- [License](#license)





Let's start from ##Task 1. In task 1 they're telling you to dowload the pcapng file so obviously download it.

Now let's get into Task 2. In Task 2 the first question is : 

When was the first packet captured? (Format : Year-Month-Date Hours:Minutes:Seconds)

Okey so we have to open the thmcaptureh4x0r3rr0r.pcapng file in wireshark then we'll see a packet at the top which is no 1 ( numbers are defined in the left first column). After selecting the first file we have to look at the " Packet Details Pane " . If we drop down the first row "Frame 1:" we'll be able to see the content that was in the Frame 1 . If we look at the contents we'll see a row named Arrival time.
There you'll get the answer of the Q1.


Q3: When was the last packet captured? (Format : Year-Month-Date Hours:Minutes:Seconds)

This is similar to the Q1 all you have to do is just naviagte to the bottom of the list and select the last packet and look for the dat & time like you did in the Q1.

Q3: How many packets were captured?

To see how many packets were captured you have look at the bottom of you're wiresahrk UI thre is a status bar there. There you should see how many packets are there and many the displayed.

Q4: What is the SHA256 hash of the file?

To get the SHA256 hash of a file first select the file then look at the top of you're wireshark UI. There is a Toolbar. On the toolbar click the Statistics option then click the capture file properties or you can use  Ctrl+Alt+Shift+C and a page should pop up there you'll be able the find the SHA256 hash.
 
Q5: What is the MD5 hash of the file?

So I used a Python script tp get the hash. here's the script:



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


## Task3 Q1: How many ICMP packets were captured? (with parcentage)


This is similar to the Task 2 Q3 but slightly different decause you have too filter out the other packets that are not ICMP(Internet Control Message Protocol). So for that go to the diplay filter and input icmp then hit enter and you should get only the ICMP packets on your screen. Now look at the status bar at the bottom there you should see how many ICMP packets were captured with parcentage.


Q2: There was an ICMP ping request packet, which did not receive any response back. What is the packet number?

First filter the ICMP packets then search for the packets with no response there should be written (no response found!) on the right of the packet.

Q3: What was thr source IP of the above packet?

after after you locate that package look at the third column of the the list (the third column is for the souce IP).

Q4: What was thr destination IP of the above packet?

after after you locate that package look at the fourth column of the the list (the fourth column is for the destination IP).

Q5: What is the length of the packet?

after after you locate that package look at the sixth column of the the list (the sixth column is for the length).

Q6: In which country standard time was the packet captured?

For this select the packet similar to Task 2 Q1 look for the Arrival time and you should be able to see In which country standard time was the packet captured .

Q7:  When the packet was captured? (Format : Year-Month-Date Hours:Minutes:Seconds)

It's in the Arrival time too.

Q8: What is the data value of the packet?

Select the packet then look the the Packet Details Pane there you should see a drop-dow bar named Internet Control Message Protocol. Drop it down and you should see this :

Now drop-down the bar named Data and you should get a field name & Value. right click on it and copy the value.

Q9: Decode the value.

The value is in hex so decode it however you want. Use a tool or script. You should be able to do this much by your self.

Q10: In the decoded strings there was  an username and a password, what are those?

After decoding it you should get the user name and password in the decoded value.


 
