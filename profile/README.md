# OOPS

**O**rbistoun, **o**bSCEne, **P**rosperous, **S**ELFish.

Four projects aimed at one platform: an emulator, a conformance probe, remote management,
and the file formats underneath them.

| | | |
|---|---|---|
| **[Orbistoun](https://github.com/project-oops/Orbistoun)** | the emulator | attempts to reimplement what a title runs on, so its code can run natively |
| **[obSCEne](https://github.com/project-oops/obSCEne)** | the probe | a guest that interrogates whatever runs it and reports what it found |
| **[Prosperous](https://github.com/project-oops/Prosperous)** | the instrument | remote management for anything that runs Orbis software |
| **[SELFish](https://github.com/project-oops/SELFish)** | the formats | read, write and build tools for the platform's own file formats |

Underneath them, **[oops-libs](https://github.com/project-oops/oops-libs)** — the build
stamp, logging, paths and the in-app documentation viewer. A fifth repository and **not** a
fifth project.

## What it is for

**Running Orbis software on an ordinary computer, from a codebase that can be published.**

The second half is the constraint that shapes everything. It is not difficult to make an
emulator work by copying what the hardware does; it is difficult to make one whose every
behaviour can be explained from a lawful source — and only that kind can be shared, packaged
or accepted from a contributor. So no firmware, no keys, no decrypted titles, no
disassembly, and where a fact came from is recorded beside the fact.

That constraint is why there are four projects instead of one.

## The oracle problem

An emulator of an undocumented platform can tell you *that* a guest died, and almost never
*whether an answer was right*. There is no specification to test against, because the
specification is the thing being reconstructed. Each project removes one unknown:

- **obSCEne removes the guest.** It is a program we wrote, so what it asks for is known
  exactly and what came back can be judged. A commercial title can only tell you it stopped.
- **Prosperous removes the emulator.** The same probe on real hardware answers what the
  platform does, rather than what some reimplementation of it does.
- **SELFish removes the parser.** When two projects disagree about a file, one shared and
  cited reader beats two independent readings.

## Where to start

**[OOPS](https://github.com/project-oops/OOPS)** is the development entry point — clone it
and you have everything, arranged so it builds:

```bash
git clone --recurse-submodules https://github.com/project-oops/OOPS
cd OOPS
./bin/oops doctor
```

The separate repositories are how each project reaches the people who *use* it. A person who
wants to run a conformance probe against their emulator downloads it; a person changing how
the probe works clones OOPS.
