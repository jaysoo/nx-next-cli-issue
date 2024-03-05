
If you SIGINT or SIGTERM the `next build` command, it will exit with code `0`. This can be problematic for other tooling since the code indicates that the build has succeeded even though it did not.

## Example

If you use Next.js and Nx together, the build command receiving SIGINT or SIGTERM will result in the build being marked as successful, and the cached `.next` folder will be invalid.


e.g.

```
# Run this, then Ctrl+C the process before it finishes
npx nx build

# Run it again
npx nx build
```

The second command will be read from Nx cache, but the artifacts are invalid since the first build never finished.

