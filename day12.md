# Lecture 12 (Fri, Feb 2, 2018)

`stdio` library:
fopen
`buffread()` reads 8 writes.

**<stdio.h> version:**
```c
int main(int argc, char* argv[]) {
    FILE* in, out;

    in = fopen(argv[1], "r");
    out = fopen(argv[2], "w");

    stdio_cat(in, out);
    fclose(in);
    fclose(out);
    
    return 0;
}

void stdio_cat(FILE* infile, FILE *outfile) {
   int c;

    while ((c = getc(infile) != EOF)
        putc(c, outfile); 
}
```

**UNIX I/O version:**

Implicitly defined:
- `O_CREAT`
- `O_TRUNC`
- `O_APPEND`
```c
#define BUFFER_SIZE 256
#define USAGE_ERR "u used it wrong lmaoo"

int main(int argc, char* argv[]) {
    int infile_descriptor, outfile_descriptor;

    if (argc != 3)
        printf("%s\n", USAGE_ERR);

    infile_descriptor = open(argv[1], O_RDONLY);

    if (infile_descriptor == -1) {
        perror(argv[1);
        exit(EXIT_FAILURE);
    }

    outfile_descriptor = open(argv[2], O_WRONLY | O_CREAT | O_TRUNC);

    if (outfile_descriptor == -1) {
        perror(argv[2]);
        exit(EXIT_FAILURE);
    }

    unix_cat(infile_descriptor, outfile_descriptor);

    if ((close(infile_descriptor) == -1) || (close(outfile_descriptor) == -1) {
        perror();
        exit(EXIT_FAILURE);
    }

    exit(EXIT_SUCCESS);
}

void unix_cat(int infd, outfd) {
    char buf[BUFFER_SIZE];
    int n;

    while ((n = read(infd, buf, BUFFER_SIZE)) > 0) {
        if (write(outfd, buf, n) == -1) {
            perror();
            exit(EXIT_FAILURE);
        }
    }

    if (n < 0) {
        perror();
        exit(EXIT_FAILURE);
    }
}   
```
