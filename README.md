As an experiment, I asked Claude Code to design an MCU for the Caravel platform using OpenLane and sky130 PDK. The results are saved here.

Claude's sandbox was the biggest problem. If you ask an AI to design a chip, make sure it can:

1. Access PyPI (`pypi.org` and `files.pythonhosted.org`).
2. Use OpenLane 2, not OpenLane 1.
3. Add cache.nixos.org to allow OpenLane 2’s own Nix tool environment.

With only GitHub reachable, Claude built the toolchain from source and release binaries, and patched OpenLane 1 to work with the newer OpenROAD it could get. That took hours, and the sandbox's 2 cores made each full flow run take an hour or more.

Claude first built the RAM from 4096 flip-flops, and OpenROAD's hold fixing on those took hours, so I suggested SRAM22. That worked.

Where it got to: an RV32E MCU (UART, GPIO, timer, 2 KB SRAM22) verified in simulation against a reference model. An earlier flip-flop-RAM version passed Magic DRC and Netgen LVS. The SRAM22 version routed cleanly but needs one more run after a pin fix in the SRAM's LEF. The Caravel wrapper is not hardened yet.

- [`caravel/README.md`](caravel/README.md): the design, how to run the simulations, results.
- [`CLAUDE.md`](CLAUDE.md): Claude's notes on what went wrong and how it was worked around. Claude Code loads it automatically when working in this repo.
