# secure-desktop-os-ideas
secure ideas:

- using a minimalist or maybe security focused based os, like alpine linux or secureblue
  - use alpine linux if ya dont like systemd (minimalist openrc, thus secure, but will need to setup a lot),
    and don't like glibc and prefer minimalist musl
  - use secureblue for its trivalent browser
- but we aren't installing user apps on these base oses, we will use virt-manager.
- if you want to do anything gpu intensive, you can install Venus (virt-io) gpu
  for near native gpu performance, without needing to buy another frickin gpu
  just for your local ai

- you should care about the guest os security as well, so disable any unnecessary kernel modules to absolute
  minimum
- unikernals is interesting, can run only the app needed, but im not sure how you would pass gui bridge to it

# qna
Why not qubes os/chrome os?
- chromeos is good for its verified boot, and hardened base os
- qubes os, it is even more secure than chromeos (except lack of verified boot, heads is ok),
  but i thought it was too limiting (yes it doesn't have gpu accel for security, but now you can't run
  your own local ai, or maybe you're a gamer)
- chromeos wasn't too limiting, and there was even a steam vm (borealis) for gaming, you could even import different games
  on it like minecraft for absolute near native gpu performance
- this setup was inspired by qubes os and chromeos

Why not just use flatpak?
- flatpak has too many permissions that are permissive, you can see
  that many programs ask demanding over privileged permissions BY DEFAULT
- there are shell exploits, can easily bypass the fake "sandboxing" flatpak does 
