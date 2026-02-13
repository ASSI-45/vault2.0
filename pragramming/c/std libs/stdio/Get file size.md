-- -
```c
off_t get_file_size(FILE *file) {
    fseeko(file, 0, SEEK_END);
    off_t size = ftello(file);
    rewind(file);
    return size;
}
```