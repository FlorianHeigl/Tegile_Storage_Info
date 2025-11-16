# Tegile_Storage_Info


## Goal of this project

- create open documentation for Tegile Storage Arrays.
- make it available for users that cannot have the proper support otherwise.
- draw a distinct line separating vendor-owned documentation that could be
made inaccessible
- empower users by giving some option to do self-service at their own discretion

If vendor docs are referenced, it should be in form of a link or the document title, and a description of the content.
I think original content cannot be included here, to uphold a free license.

## How to use

To read: Just look through the different files, there's no PDF version as of now.  
To write: Contributions are most welcome.


## Status of the hardware

### EOL overview

Most are now EOL or will be by end of the year 2023.
Warranty extensions, Sales of upgrades etc. apparently have been declined by the customer representatives.
There used to be a forever or 5 year or something upgrade policy.
If that applies to your system, you might still be entitled to service.

### Abandoned Software

Development is still taking place, but activitiy seems to be very, very low. This is not just a case of "the system is so stable it needs no changes".
Major developments of the open source ZFS tree have not been ported to Zebi even though they are now stable and readily available.
The download site is sometimes offline (https seems gone forever), either it's just in maintenance, or, not unlikely, it can be assumed this means the last customer(s) with a valid support contract had let it expire, some updates indicate they happen to sometimes find another forgotten client. :-/

### Stability

there was an increase in customer complaints, generally the 'stable' version is supposed to be 3.11, of which there are multiple releases.
since the customer base is dwindling and updates will not proactively reach all customers you should in general stay on the release that works for you.
Within limits - it likely should be a 3.11, it should have already have re-factored SATA Doms, and if possible, it should already be a version that supports NDMP or S3 backups.
The newest releases seem to have also added 2FA support, which is a great bonus, but it is unclear if it's possible to upgrade older systems to that code version.
There's a few messages saying they are for '-E1' revisions only.


See [Reddit](https://www.reddit.com/search/?q=tegile) if you want to investigate further.


## Contributing

- For content, various, or rather: any things would be of interest, but especially if you have existing API code or your own internal docs that could be stripped of sensitive and shared
- For code, help producing readthedocs manuals could be the best that we could do for other users
- Proof-reading and checking what others wrote, extending it or even just prioritizing
- making lists what is covered in the official docs and should be described for future generations
- Links to content that should be preserved but cannot be OSS should be left with a description (i.e. Visio Stencils)

### Donations

I can't find if I actually mentioned this, I'd absolutely appreciate some old Array and Disk/SSD for it.
I had to part from mine since proved increbibly valuable during a migration. Probably I'll get one more for debugging help, but that still leaves me short on SSDs or the late HDD types (12T+).


## Trademark notices

DDN, Tintri by DDN and Nexenta by DDN are trademarks owned by DataDirect Networks. All other trademarks are the property of their respective owners.
INTELLIFLASH is a trademark of INTELLIFLASH BY DDN, INC.. 
(https://trademarks.justia.com/864/00/intelliflash-86400865.html)
