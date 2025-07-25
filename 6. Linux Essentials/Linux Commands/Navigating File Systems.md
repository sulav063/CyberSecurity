### Basic Navigation
```bash
pwd                 # Show current directory
cd                  # Go to home directory
cd /path/to/dir     # Go to specific directory
cd ..               # Move up one level
cd -                # Return to previous directory
cd ~                # Jump to home directory (alternative)
pushd /path         # Push directory onto stack and change to it
popd                # Return to previous directory from stack
dirs -v             # List directory stack with numbering
```

---
### Listing Files and Info
```bash
ls                  # List contents
ls -a               # Include hidden files
ls -l               # Long listing with details
ls -la              # Long listing including hidden files
ls -lh              # Long listing with human-readable sizes
file filename       # Determine file type
stat file.txt       # Display detailed file information
ls -R               # Recursively list directory contents
```

---
### Creating, Copying, Moving
```bash
touch file.txt      # Create empty file
mkdir newdir        # Create directory
mkdir -p dir/subdir # Create directory and parent directories as needed
cp file1 file2      # Copy file1 to file2
cp -r dir1 dir2     # Copy directory recursively
cp file.txt /dir/   # Copy file to directory
mv file.txt /dir/   # Move file
mv file1 file2      # Rename file1 to file2
rsync -av file.txt /dir/ # Synchronize files with advanced options
```

---
### Deleting and Inspecting
```bash
rm file.txt         # Delete file
rm -r dir           # Delete directory recursively
rmdir dir           # Remove empty directory
rm -f file.txt      # Force delete file without confirmation
find . -type f -delete # Delete all files in current directory
lsattr -a           # List file attributes
chattr +i file.txt  # Make file immutable
```

