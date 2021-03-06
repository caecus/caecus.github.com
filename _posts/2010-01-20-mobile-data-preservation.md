---
layout: post
published: true
title: Mobile Data Preservation
snippet: This post documents my attempts to preserve my personal data as I migrated my phone from Windows Mobile to Android.
tags:
 - backup
 - android
---

I have recently upgraded my phone from a Windows Mobile 6.1 to an Android 2.1 device. As with any OS upgrade, whether its on a computer or mobile phone, preserving your data is always a problem.

Most of my data is stored in “the cloud” as follows:
Google Calendar Sync for events, contacts and email,
Remember The Milk’s “MilkSync” for tasks,
“Shozu” and “PicasaWeb” for pictures
“Evernote” for notes.

So the only data left to be preserved were my SMS messages; with no obvious solution.

After some searching, I discovered this [helpful article](http://homebrew.binaervarianz.de/index.php?/archives/13-How-to-move-Contacts-and-SMS-from-WindowsMobile-to-Android.html) by Mario Mlynek. The article describes using  [PIMBackup](http://www.dotfred.net/default.htm), which can extract a variety of data from the Windows Mobile phone into a proprietary file format, and [SMS Backup & Restore](http://android.riteshsahu.com/2009/11/sms-backup-restore.html) to transfer the data.

Unfortunately, it was not as simple as passing the data directly from one application to the other. The user is required to perform a transformation of the CSV-esque data into XML. To perform this transformation, any multi-line messages has to be changed to a single line with HTML break tags. The file must then be put through a Perl script, which Mario had developed. At this stage, I had to perform some minor modifications to get it to work. My version of the script can be downloaded [here](http://docs.google.com/leaf?id=0ByfedSopdUCoMjI3MGQ5YTUtOGE1MC00YTNjLTk2NDEtMGZiNzZiZDhmZWYy&hl=en_GB).

Finally, you place the sms.xml file onto the Android phone, via Bluetooth or an alternate browser as the default browser fails to recognise the file type. The messages can then be restored so that the dates, content and threading is as though the messages were originally sent to the Android phone. If you want to ensure that none of the new messages are pruned, you should remember to modify Android's messaging application so that it doesn't delete old messages before performing the restoration.

However, a problem arose once my 11,500 messages were restored - The Android messaging application doesn't handle long messages threads particularly well. With one particular person, there were over 4,000 messages! This made me realise the benefit in pruning messages, however, I didn’t want to lose all of the valuable information that I had restored.

After a little searching around, I found a SMS backup solution called [SMS Backup](http://code.google.com/p/android-sms/). This solution automatically transfers all your messages to Gmail using IMAP. It can mark the messages as read and store them with a particular label. As a result, you are able to view and search all or your archived messages, either through Gmail’s web interface, or on the Gmail Android application. Once the initial backup was performed (200 messages at a time), I was able to re-enable SMS pruning. As a result I had a faster phone and the knowledge that another area of my personal data is archived, secured and searchable.
