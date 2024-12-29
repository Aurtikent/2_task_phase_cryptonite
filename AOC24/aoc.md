# Day1

- There is a yt2mp3 converter which gives us a download.zip
- inside the zip there are 2 files `song.mp3`, `somg.mp3`
- `somg.mp3` is a windows lnk (shortcut) file, the power shell command does some malicious things and refers a raw github ps script `https://raw.githubusercontent.com/MM-WarevilleTHM/IS/refs/heads/main/IS.ps1`


## Questions: 
- Looks like the song.mp3 file is not what we expected! Run "exiftool song.mp3" in your terminal to find out the author of the song. Who is the author? 
`Tyler Ramsbey`

- The malicious PowerShell script sends stolen info to a C2 server. What is the URL of this C2 server?

`http://papash3ll.thm/data`


- Who is M.M? Maybe his Github profile page would provide clues?

`Mayor Malware`

- What is the number of commits on the GitHub repo where the issue was raised?
`1`

---

# Day2
- we have a Elastic SIEM Dashboard which is used for machine management and logging in large organisations.
- as per given reports the activity occurred on Dec 1st, 2024, between 0900 and 0930
- we get various events and by setting filters which can be used to build a complete overlook of what happend. 


## Questions:


What is the name of the account causing all the failed login attempts?
`service_admin`

How many failed logon attempts were observed?
`6791`

What is the IP address of Glitch?
`10.0.255.1`

When did Glitch successfully logon to ADM-01? Format: MMM D, YYYY HH:MM:SS.SSS
`Dec 1, 2024 08:54:39.000`

What is the decoded command executed by Glitch to fix the systems of Wareville?
`Install-WindowsUpdate -AcceptAll -AutoReboot`

---

# Day3

- Use The ELK dashboard to find different parameters, shell uploaded in the the webapp
- analysing the web app we see an open end point
- exploit it and upload shell.php to give the flag, and several other questiosn 

## Questions

BLUE: Where was the web shell uploaded to?
Answer format: /directory/directory/directory/filename.php

`/media/images/rooms/shell.php`

BLUE: What IP address accessed the web shell?

`10.11.83.34`


RED: What is the contents of the flag.txt?
`THM{Gl1tch_Was_H3r3}`

---

# Day4

- learned about different atomic tests and why they are used, 
- how to use the Atomic tests and read logs
- these test run and detail how the system might be vulnerable, 
- they can be used to set up rules in prevention / logging systems.



## Questions

What was the flag found in the .txt file that is found in the same directory as the PhishingAttachment.xslm artefact?
`THM{GlitchTestingForSpearphishing}`

What ATT&CK technique ID would be our point of interest?
`T1059`

What ATT&CK subtechnique ID focuses on the Windows Command Shell?
`T1059.003` 
What is the name of the Atomic Test to be simulated?
`Simulate BlackByte Ransomware Print Bombing`
What is the name of the file used in the test?
`Wareville_Ransomware.txt`
What is the flag found from this Atomic Test?
`THM{R2xpdGNoIGlzIG5vdCB0aGUgZW5lbXk=}`

---

# Day5 

- This Basically Teaches us about xxe vulnerablity 
- The xml parser can be vulnerable and read files on the system which can expose credetials, 

## QUESTIONS

What is the flag discovered after navigating through the wishes?
`THM{Brut3f0rc1n6_mY_w4y}`


What is the flag seen on the possible proof of sabotage?
`THM{m4y0r_m4lw4r3_b4ckd00rs}`

---

# Day6

- Teaches us about various evasion Techniques used by threat actors
- including encoding the payload to avoid detection, 
- Using YARA: Another Recursive Acronym or Yet Another Ridiculous Acronym we define rules to have EDR
- Use Floss to identify obsfucated strings in the malware bin, 

## Question
What is the flag displayed in the popup window after the EDR detects the malware?
`THM{GlitchWasHere}`

What is the flag found in the malstrings.txt document after running floss.exe, and opening the file in a text editor?
`THM{HiddenClue}`

---

# Day7

- Doing Log analysis on files provided by the Aws Cloudtrail, 
- Using tools like jq to analyse complex json Files like these,

```
{
  "eventVersion": "1.10",
  "userIdentity": {
    "type": "IAMUser",
    "principalId": "AIDAXRMKYT5O5Y2GLD4ZG",
    "arn": "arn:aws:iam::518371450717:user/wareville_collector",
    "accountId": "518371450717",
    "accessKeyId": "AKIAXRMKYT5OZCZPGNZ7",
    "userName": "wareville_collector"
  },
  "eventTime": "2024-10-21T22:13:24Z",
  "eventSource": "s3.amazonaws.com",
  "eventName": "ListObjects",
  "awsRegion": "ap-southeast-1",
  "sourceIPAddress": "34.247.218.56",
  "userAgent": "[aws-sdk-go/0.24.0 (go1.22.6; linux; amd64)]",
  "requestParameters": {
    "bucketName": "aoc-cloudtrail-wareville",
    "Host": "aoc-cloudtrail-wareville.s3.ap-southeast-1.amazonaws.com",
    "prefix": ""
  },
  "responseElements": null,
  "additionalEventData": {
    "SignatureVersion": "SigV4",
    "CipherSuite": "TLS_AES_128_GCM_SHA256",
    "bytesTransferredIn": 0,
    "AuthenticationMethod": "AuthHeader",
    "x-amz-id-2": "yqniVtqBrL0jNyGlvnYeR3BvJJPlXdgxvjAwwWhTt9dLMbhgZugkhlH8H21Oo5kNLiq8vg5vLoj3BNl9LPEAqN5iHpKpZ1hVynQi7qrIDk0=",
    "bytesTransferredOut": 236375
  },
  "requestID": "YKEKJP7QX32B4NZB",
  "eventID": "fd80529f-d0af-4f44-8034-743d8d92bdcf",
  "readOnly": true,
  "resources": [
    {
      "type": "AWS::S3::Object",
      "ARNPrefix": "arn:aws:s3:::aoc-cloudtrail-wareville/"
    },
    {
      "accountId": "518371450717",
      "type": "AWS::S3::Bucket",
      "ARN": "arn:aws:s3:::aoc-cloudtrail-wareville"
    }
  ],
  "eventType": "AwsApiCall",
  "managementEvent": false,
  "recipientAccountId": "518371450717",
  "eventCategory": "Data",
  "tlsDetails": {
    "tlsVersion": "TLSv1.3",
    "cipherSuite": "TLS_AES_128_GCM_SHA256",
    "clientProvidedHostHeader": "aoc-cloudtrail-wareville.s3.ap-southeast-1.amazonaws.com"
  }
}

```
- use jq command to get what is needed, and get into picture what exactly happend, 

## questions 

What is the other activity made by the user glitch aside from the ListObject action?
`PutObject`

What is the source IP related to the S3 bucket activities of the user glitch?
`53.94.201.69`

Based on the eventSource field, what AWS service generates the ConsoleLogin event?
`signin.amazonaws.com`

When did the anomalous user trigger the ConsoleLogin event?
`2024-11-28T15:21:54Z`

What was the name of the user that was created by the mcskidy user?
`glitch`

What type of access was assigned to the anomalous user?
`AdministratorAccess`

Which IP does Mayor Malware typically use to log into AWS?
`53.94.201.69`

What is McSkidy's actual IP address?
`31.210.15.79`

What is the bank account number owned by Mayor Malware?
`2394 6912 7723 1294`

--- 

# Day 8

- Use the metasploit framework to generate reverse shellcode which can be executed on target machine to get a reverse shell. 
- following is the shell code used and the SHELLCODE_PLACEHOLDER is replaced with the power shell code generated by msfvenom. 
```
VrtAlloc = @"
using System;
using System.Runtime.InteropServices;

public class VrtAlloc{
    [DllImport("kernel32")]
    public static extern IntPtr VirtualAlloc(IntPtr lpAddress, uint dwSize, uint flAllocationType, uint flProtect);  
}
"@

Add-Type $VrtAlloc 

$WaitFor= @"
using System;
using System.Runtime.InteropServices;

public class WaitFor{
 [DllImport("kernel32.dll", SetLastError=true)]
    public static extern UInt32 WaitForSingleObject(IntPtr hHandle, UInt32 dwMilliseconds);   
}
"@

Add-Type $WaitFor

$CrtThread= @"
using System;
using System.Runtime.InteropServices;

public class CrtThread{
 [DllImport("kernel32", CharSet=CharSet.Ansi)]
    public static extern IntPtr CreateThread(IntPtr lpThreadAttributes, uint dwStackSize, IntPtr lpStartAddress, IntPtr lpParameter, uint dwCreationFlags, IntPtr lpThreadId);
  
}
"@
Add-Type $CrtThread   
```

![img_1](./assets/day8_1.png)

![img_2](./assets/day8_2.png)

## Questions 

What is the flag value once Glitch gets reverse shell on the digital vault using port 4444? Note: The flag may take around a minute to appear in the C:\Users\glitch\Desktop directory. You can view the content of the flag by using the command type C:\Users\glitch\Desktop\flag.txt.
`AOC{GOT _MY_ACCESS_B@CK007}`

---

# Day9

- Grc Compliance and how to acess risk
- Risk Mitigation and ways to perform an risk analysis

![day 9 img](./assets/Day9_1.png)

## Questions

What does GRC stand for?
`Governance, Risk, and Compliance`

What is the flag you receive after performing the risk assessment?
`THM{R15K_M4N4G3D}`

--- 

# Day10

- a macro refers to a set of programmed instructions designed to automate repetitive tasks
-
