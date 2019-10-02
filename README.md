# Utility for converting Helium Backup file into regular TAR file

This tool was originally available as Helium_ab2tar.zip, original copy seems to have vanished.

Archived for convenience here, all copyright (c) original authors.

## License

Originally written by xaos.cz @ XDA-Devs

Makefile by seXneo @ XDA-Devs

http://forum.xda-developers.com/showthread.php?t=2616961

## Usage:

    ab2tar_cut [.ab file] [temporary file]
    ab2tar_corr [temporary file] [.tar file]

## Modifying *telephony* database:

**WARNING!** In order to backup must have *root* ownership all following commands need to be executed with **sudo**!

1. Make a backup with **Carbon**.
2. Copy *.ab* file to *ab2tar* folder.
3. Run *ab2tar_cut* to create **temp** file.
4. Run *ab2tar_corr* to create **tgz** file from **temp** file.
5. Un-TAR **tgz** file and modify *apps/com.android.providers.telephony/cb/custom.cb* file.
6. Save and TAR with command:

    `tar -cvf ./fix.tgz apps/com.android.providers.telephony/cb/custom.cb`
7. Check the *fix.tgz* file by running `tar -tf ./fix.tgz` - it should output:

    `apps/com.android.providers.telephony/cb/custom.cb`
    
    **WARNING!** *apps/com* header is very important! There cannot be anything else!
8. Run *tar2ab_corr* to create **temp** file from **tgz** file.
9. Run *tar2ab_cut* to create **fix.ab** file from **temp** file.
10. Rename **fix.ab** to **com.android.providers.telephony.ab**.
11. Copy new *telephony.ab* file to your Android phone to *carbon/com.android.providers.telephony* folder.
12. Restore modified backup with **Carbon**.

