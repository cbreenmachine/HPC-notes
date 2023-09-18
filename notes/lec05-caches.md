
# Caches and Virtual Memory

## A Case Study on Matrix operations

You can store a 2-dimensional matrix in two ways: squashed format (one long array) or 2D format (using one array per row).

Bottom line--store the data in a logically consistent way with how you want to access it.

Be able to assess locality qualitatively is important! See slides 19-20 of lec 5 for examples.

### Memory in C
// allocates
void *malloc(size_t number_of_bytes);

size_t sizeof(someType);

// releases dynamic memory allocated
void free (void * p)

It's not hard to actually move data (bus is big), rather, it's expensive to tell where the data are located. If you obey locality principle, then you will make fewer trips.