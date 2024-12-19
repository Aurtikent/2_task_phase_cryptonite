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

#Day2
- we have a Elastic SIEM Dashboard which is used for machine management and logging in large organisations.
- as per given reports the activity occurred on Dec 1st, 2024, between 0900 and 0930
- we get various events and by setting filters which can be used to build a complete overlook of what happend. 


## QUestions:


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

#Day3

- 

