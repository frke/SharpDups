# SharpDups
Fast duplicate file search via parallel processing with C#.

The tool will find duplicate files using Map/Reduce method. It accepts a list of files and then perform the duplicate checking. It could be extended easily to support file search filter etc.


**Logic:**

1. Group files with same size
2. Check first/middle/last bytes for quick hash
3. Group files with same quick hash by comparing the bytes in the header/middle and end of the file
4. Get progressive hash for files with same quick hash, if intermediate hash is different, discard the remaining comparison
5. Group files with same full hash


**Methods:**

 - V1: uses sequential processing
 - V2: uses parallel processing, 3 times faster with 5 worker threads
 - V3: use parallel processing and progressive hashing

**Features:**
 - Fast, with parallel processing via MapReduce
 - Really fast, drastically reduce I/O read, typically only read 5-10% of all content, 20GB, 300K+ files took 75 seconds.