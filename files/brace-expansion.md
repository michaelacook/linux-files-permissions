# Brace expansion
- Pattern creation 
- Can be much more powerful than globbing
- Unlike globbing, can be used to create and search files

```bash 
echo {1..10}

1 2 3 4 5 6 7 8 9 10
```

- The pattern put into braces will be expanded by the command preceding it
- Pass multiple patterns into braces to search for multiple patterns 
- eg:

```bash 
ls file*.{jpg, png, gif}
```

- This will match any of the file extensions given

## Incremental ranges 
- Within a range passed into braces, you can also pass an increment number so that expansion is incremented by a number other than 1 
- eg:

```bash 
ls -1 photo_{1000..1100..7}*.jpg

photo_1000.jpg
photo_1007.jpg
photo_1014.jpg
photo_1021.jpg
```
---

- Brace expansion is powerful enough to make very tedious tasks fast 
- If you want to create 12 folders for 12 months and 31 folders inside each, you can do the following: 

```bash 
mkdir -p {1..12}/{1..31}
```

[Previous](file-globs.md)|[Next](extended-globs.md)