
bun install;
arch; node -e 'console.log(process.arch)'; bun script-node-arch; bun script-via-bun; bun script-via-bun-force; bun script-via-node

note:
 - the arch is taken as `x64` whenever a script is ran without '--bun'.
 - the terminal is not rosetta
 - the node version is silicon

Am confused why running a script via bun would alter the process.arch. This isn't ordinarily a problem but is when the postinstall scripts ran