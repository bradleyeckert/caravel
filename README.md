As an experiment, I asked Claude Code to design an MCU for the Caravel platform using OpenLane and sky130 PDK. The results are saved here.

Claude's sandbox was the biggest problem. If you ask an AI to design a chip, make sure it can:

1. Access PyPI.
2. Use OpenLane 2, not OpenLane 1.
3. Add cache.nixos.org to allow OpenLane 2’s own Nix tool environment.

Claude was spending a lot of time on OpenRAM, so I suggested SRAM22. That worked.
