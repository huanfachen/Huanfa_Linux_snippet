# Zip and unzip

## view the contents of a zip file using less

```
less 1.zip
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

