Error repro for nextjs standalone bundling.

Problem: relative symlinks are copied from the root of a pnpm monorepo into the standalone output where they become invalid.

## Reproduce

```shell
pnpm i
cd web
pnpm build
ls -al .next/standalone/node_modules
```

```
ls -l web/.next/standalone/node_modules
lrwxr-xr-x 81 cyber  9 Sep 15:21 next -> ../../node_modules/.pnpm/next@12.3.0_biqbaboplfbrettd7655fr4n2y/node_modules/next
lrwxr-xr-x 56 cyber  9 Sep 15:21 react -> ../../node_modules/.pnpm/react@18.2.0/node_modules/react
```
