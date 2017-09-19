# Leak report

Calloc was called on line 41 in strip, and is used to return the cleaned string. Strip is called in is_clean on line 63, and is_clean is called in main at line 88. The memory allocated is never freed.

The result needs to be freed. (Ideally after it's returned, but I think freeing it beforehand also works if nothing happens between result being freed and result being returned.)
