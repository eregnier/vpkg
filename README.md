# vpkg 
vpkg is a package manager written on [V](https://github.com/vlang/v) for V. It demonstrates the basic functions of a package manager and was never originally intended as a design proposal for a future package manager that was stated on [V's website](https://vlang.io/).

## The approach
vpkg's approach is to incorporate the ideas taken from centralized and decentralized package managers.
- Centralized, popular packages are being listed on to a single [`registry.json`](registry/registry.json) file.
- Uses a single, JSON file for storing package information as well as it's dependencies. (In this case, [`.vpkg.json`](.vpkg.json))
- Packages stored from the `registry.json` file can be obtained through a simple `vpkg get [package name]` while the rest uses regular Git URLs.

But there are some things that make's vpkg unique:
- Downloads and installs the modules to a single folder. (For now, it maybe in your project folder or your compiler's `vlib` folder).
- Instead of installing many modules per project, it shares the common modules to reduce project file size and download times.

## How it works
- User instructs to fetch a package
- vpkg will detect if it's a git url or not
- For git, it's clones the repo to the temporary folder created inside the project directory.
- If it's not, it will scan to the registry, then clones the repo to the temp folder.
- Once they are all fetched, they will be moved into the common modules folder. For now, it will be installed to the `vlib` folder.
- Deletes the temporary folder created earlier and finish.

TODO
- Mechanism for updating packages
- Lockfile for easy tracking of modules

## Development
1. Download and install [v-args](https://github.com/nedpals/v-args) and place it into the folder where your vpkg source code is located.
2. Run the registry server using `http-server` or similar tools.

## Copyright
(C) 2019 [Ned Palacios](https://github.com/nedpals)
