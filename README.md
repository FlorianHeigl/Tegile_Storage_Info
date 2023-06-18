# Tegile_Storage_Info


## Goal of this project

- create documentation for Tegile Storage Arrays.
- make it available for users that cannot have the proper support otherwise.
- draw a distinct line separating vendor-owned documentation that could be
made inaccessible
- empower users by giving some option to do self-service at their own discretion

If vendor docs are referenced, it should be in form of a link or the document title, and a description of the content.
Raw content cannot be included here.

## Status of the hardware

### EOL overview

Most are now EOL or will be by end of the year.
Warranty extensions, Sales of upgrades etc. apparently have been declined by the customer representatives.
There used to be a forever or 5 year or something upgrade policy.
If that applies to your system, you might still be entitled to service.

### Abandoned Software

Development activity is very, very low. This is not just a case of "the system is so stable it needs no changes".
Major developments of the open source ZFS tree have not been ported to Zebi even though they are now stable and readily available.

### Stability

there was an increase in customer complaints, generally the 'stable' version is supposed to be 3.11, of which there are multiple releases.
since the customer base is dwindling and updates will not proactively reach all customers you should in general stay on the release that works for you.
Within limits - it likely should be a 3.11, it should have already have re-factored SATA Doms, and if possible, it should already be a version that supports NDMP or S3 backups.


See [Reddit](https://www.reddit.com/search/?q=tegile) if you want to investigate further.


### Trademark notices

DDN, Tintri by DDN and Nexenta by DDN are trademarks owned by DataDirect Networks. All other trademarks are the property of their respective owners.
INTELLIFLASH is a trademark of INTELLIFLASH BY DDN, INC.. 
(https://trademarks.justia.com/864/00/intelliflash-86400865.html)
