
### To show arch:
bun install;
arch; node -e 'console.log(process.arch)'; bun script-node-arch; bun script-via-bun; bun script-via-bun-force; bun script-via-node


### To show arch assumed in postinstall:
rm -rf node_modules
rm bun.lockb
bun install

Even doing the following provides no way to influence the arch:

rm -rf node_modules
rm bun.lockb
bun --bun install

---

note:
 - the arch is taken as `x64` whenever a script is ran without '--bun'.
 - the terminal is not rosetta
 - the node version is silicon

Am confused why running a script via bun would alter the process.arch. This isn't ordinarily a problem but is when the postinstall scripts ran

--- 

Output:

```
📚  31/12 11:36:38   main ●  ~/dev/assorted/repros/bun-arm64
$ bun install; arch; node -e 'console.log(process.arch)'; bun script-node-arch; bun script-via-bun; bun script-via-bun-force; bun script-via-node
bun install v1.0.20 (09d51486)

Checked 1 install across 2 packages (no changes) [102.00ms]
arm64
x64
$ node -e 'console.log(process.arch)'
x64
$ bun ./my-script.js
arm64
$ bun --bun ./my-script.js
arm64
$ node ./my-script.js
x64
```
