# Unix-File-System

Design a simple File System which makes the following assumptions:
   The File system resides on a disk that is 128 KB in size.
   There is only one root directory. No subdirectories are allowed.
   The File system supports at most 16 files.
   The maximum size of a file is 8 blocks where each block is 1KB in size.
   Each File has a unique name.
  
The layout of 128 KB disk is as follows:
   The first 1KB block is called the super block. It stores the free block list and index nodes (inode) for each file.
   The remaining 127 1KB blocks store data blocks of the files on your file system.
   The exact structure of the super block is as follows:
   The first 128 bytes stores the free block list. Each entry in this list indicates whether the corresponding block is free or in use (if the i-th byte is 0, it indicates that the block is free, else it is in use). Initially all blocks except the super block are free.
   Immediately following the free block list are the 16 index nodes, one for each file that is allowed in the file system. Initially, all inodes are free. Each inode stores the following information:
    char name[8];         //file name
    int size;             //file size (in no. of blocks)
    int blockPointers[8]; //direct blockPointers
    int used;             //0 -> inode is free, 1->in use
   
Note that each inode is 56 bytes in size; Since you have 16 of these, the total size of occupied by the inodes is 896 bytes. The free/used block information (mentioned above) is 128 byes. So the total space used in the super block is 1024 bytes.

You need to implement the following operations for your file system.
   create(char name[8], int size): create a new file with this name and with these many blocks. (You can assume that the file size is specified at file creation                                       time and the file does not grow or shrink from this point on)
   delete(char name[8]): delete the file with this name
   read(char name[8], int blockNum, char buf[1024]): read the specified block from this file into the specified buffer; blockNum can range from 0 to 7.
   write(char name[8], int blockNum, char buf[1024]): write the data in the buffer to the specified block in this file.
   ls(void): list the names of all files in the file system and their sizes.
