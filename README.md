# PNPM Monorepo Bug when using `up -Li`

## Steps to reproduce

1. created new folder
2. pnpm init
3. add `pnpm-workspace.yaml`
4. add `.npmrc`
5. run `pnpm add -DE @types/node@20.16.11`
6. create `apps/test`
7. create `apps/second-test`
8. `cd` into `apps/test`
9. run `pnpm init`
10. run `pnpm add -DE @types/node@20.16.11 ramda@0.29.0`
11. `cd` into `apps/second-test`
12. run `pnpm init`
13. run `pnpm add -DE @types/node@20.16.11 ramda@0.29.0`
14. `cd` into project root
15. check lockfile and see that all references, versions, and specifiers for `ramda` are `0.29.0`
16. `cd` into `apps/test`
17. run `pnpm up -Li`
18. _only_ select `@types/node` to update, and hit enter
19. `cd` into project root
20. check lockfile and note that the specifiers for `ramda` are still `0.29.0`, but the versions have incorrectly been updated to the latest version

