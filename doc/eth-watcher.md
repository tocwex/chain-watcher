# `%eth-watcher` vs. `%scanner` vs. `%chain-watcher`

First, a brief history of these agents:

- [`%eth-watcher`][eth-watcher]: Arvo's built-in Ethereum chain watching agent
- [`%scanner`][scanner]: Vaporware's soft fork of `%eth-watcher` for [`%make`][make]
- [`%chain-watcher`][chain-watcher]: [~tocwex]'s soft fork of `%scanner` for its
  projects

The `eth-watcher.diff` file included with this primer contains the sum
difference between `%eth-watcher` (in its [iteration as of Arvo
410k][eth-watcher]) and `%scanner` (in its [final Vaporware
iteration][scanner]). These differences can be summarized as follows:

1. `%scanner` replaces the L2 batching parameter in `%eth-watcher` with an
   optional `confirms` parameter (the number of confirmations before accepting
   and propagating a block; default 15).
2. `%scanner` restores the ability of the agent to perform eager block fetches
   (that is, block fetches before confirmations), which was removed from
   `%eth-watcher` during the L2 integration.
3. `%scanner` omits a special chain querying scaling clause that was included
   in `%eth-watcher` to avoid over-querying state in the early blocks of the
   Azimuth contract.
4. `%eth-watcher` performs a permissions check in `+on-poke` where `%scanner`
   does not.
5. `%scanner` excludes the state history from `%eth-watcher` (versions `%0`
   through `%6`) and the corresponding `+on-load` logic.

Originally, `%scanner` was used by [~tocwex] for difference #1 above;
`%eth-watcher` *requires* its incoming blocks to reach 30 confirmations (>6
minutes lag time) before accepting them, where `%scanner` allows this
confirmation count to be configured on a per-watch basis.

As the chain needs of the [~tocwex] projects grew, these modest edits ended
up being insufficient, which is ultimately why `%chain-watcher` was developed.


[~tocwex]: https://tocwexsyndicate.com

[make]: https://github.com/deathtothecorporation/make
[chain-watcher]: https://github.com/tocwex/chain-watcher

[eth-watcher]: https://raw.githubusercontent.com/urbit/urbit/refs/tags/410k/pkg/arvo/app/eth-watcher.hoon
[scanner]: https://raw.githubusercontent.com/tocwex/chain-watcher/c4eb14051aea1995b11b347377a8ffeea06d65d5/desk/app/scanner.hoon
