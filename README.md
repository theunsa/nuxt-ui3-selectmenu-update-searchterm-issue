# To run

```
pnpm install && pnpm dev
```

# Issue

`@update:search-term` triggered when not expecting it to.

## To reproduce

### Method 1

- Just click on the SelectMenu without selecting anything (i.e. open and close it)
- You will notice it triggers the `@update:search-term` event even though no search term changes were made

### Method 2

- Select an item in the SelectMenu
- You will notice it triggers the `@update:search-term` event twice even though no search term changes were made
