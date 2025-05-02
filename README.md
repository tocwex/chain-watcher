# `%chain-watcher`

A soft fork of [Urbit] core's `%eth-watcher` agent for more general use cases.

Thanks to @ryjm (~littel-wolfur) and @rabsef-bicrym (~rabsef-bicrym) for their
work on [`%make`](https://github.com/deathtothecorporation/make), the starting
point for this project.

## Build/Develop

Make sure the following dependencies are installed on your development machine:

- [`GNU Make`](https://www.gnu.org/software/make/)
- [`durploy`](https://github.com/sidnym-ladrut/durploy)
- [`peru`](https://github.com/buildinspace/peru?tab=readme-ov-file#installation)

All of the following commands assume that the current working directory is this
repository's base directory. Also, before running any development commands, you
first need a running Urbit ship. Deploy one on your local machine with:

```bash
durploy ship zod
```

### Development Workflows

In order to continuously test back-end code changes as they're made, run:

```bash
durploy desk -w zod fund ./out/desk/
```

### Deployment Workflows

To generate a new full desk from the existing base desk, run the following
command:

```bash
make desk
```

To deploy a new desk onto your development ship, run:

```bash
make ship-desk IN_SHIP=zod
```

To perform a versioned release:

```bash
make release IN_SHIP=zod IN_RVER=X.Y.Z
```


[urbit]: https://urbit.org
[durploy]: https://github.com/sidnym-ladrut/durploy
