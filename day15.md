# Day 15 (Friday, Feb 9) - File System/OS
*See Stevens book, this lecture is a summary of that (also see page 76)*

- File system is shared with other processes (programs)

**Keywords**: `open, close, write, lseek` (the `l` stands for `long`)

```c
open("file", O_RDONLY/WRONLY/RDUR | O_CREAT, 0600); // That last number is in octal.

off_t pos = lseek(int fd, off_t offset, int whence)

+/- SEEK_SET, SEEK_CUR, SEEK_END

write(fd, "hello", 5);
lseek(fd, -3, SEEK_CUR);

Supposedly you can find whatever you deleted in the last hour in `~./snapshot`
