Zip and Unzip are command line utilities that allow you to compress and extract files and directories on Linux.

To use Zip, you can use the following syntax:

```
zip [options] archive_name.zip file1 file2 directory1 directory2 ...
```
For example, to create a zip archive of a directory named "mydir", you can run the following command:

```
zip -r mydir.zip mydir/
```
Here, -r option tells zip to recursively include all files and directories inside "mydir".

To use Unzip, you can use the following syntax:

```
unzip archive_name.zip
```
For example, to extract the contents of a zip archive named "mydir.zip", you can run the following command:

```
unzip mydir.zip
```
By default, unzip will extract the contents of the archive to the current directory.

You can also specify an alternate destination directory by using the -d option, like this:

```
unzip mydir.zip -d /path/to/destination/
```
There are many more options available for both zip and unzip. You can see the full documentation by typing man zip or man unzip in your terminal.



