# Zip and unzip

## view the contents of a zip file using less

```
less 1.zip
```

## Creating a zip file and adding files to this zip

```
# Syntax
zip [options] zipfile files_list
```

**-r Option:** To zip a directory recursively, use the -r option with the zip command and it will recursively zips the files in a directory. This option helps you to zip all the files present in the specified directory.

If -r is not used, the folder will be added to the zip but the files in the folder are not added.

```
zip -r zip_file.zip file_1 folder_1
```

Given an existing zip file, if you want to remove a file from the zip archive, you can use the **-d option**

```
zip test.zip 1.txt 2.txt
# remove 1.txt
zip -d test.zip 1.txt
less test.zip
# to add 1.txt back to the test.zip
zip test.zip 1.txt
```

If you want to update a file in the zip archive, you can use the **-u option**

```
zip test.zip 1.txt 2.txt
# update 1.txt
zip -u test.zip 1.txt
```

## Unzip to a folder with the same name as the file

Option 1 is to use the `unar` command:

```
# assume that test.zip contains two files, 1.txt and 2.txt
unar test.zip
# will create a new folder called test that contains 1.txt and 2.txt
# if the zip file only contains one file, no folder will be created

# if you want to force a folder to be created regardless of the number of files
unar -d test.zip
```

Option 2 is to use unzip with some parameters

```
f=test.zip; unzip "$f" -d "${f%.zip}"
```

## Iterate over all subfolders and unzip all zip files in each subfolder

Option 1: note that it is necessary to exclude the `.` path from the find command. Otherwise, the `cd ..` command in the for loop will take you out of the current folder.

```bash
for d in $(find . -maxdepth 1 -type d -not -path '.')
do
  cd $d
#  echo $d
  for zip_file in $(find . -name "*.zip")
  do
        #echo $zip_file
        unzip $zip_file
  done
  cd ..
done
```

Option 2: this is more concise but the grammar is complicated (TBH I don't completely understand it but it works)

```
# https://stackoverflow.com/a/22384233/4667568
find . -iname '*.zip' -exec sh -c 'unzip -o -d "${0%.*}" "$0"' '{}' ';'
```

