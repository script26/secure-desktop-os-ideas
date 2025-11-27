# secure-desktop-os-ideas
secure ideas (the MOST secure desktop setup WITH performance for Linux that you will find as of now):

- using a minimalist or maybe security focused based os, like alpine linux or secureblue
  - use alpine linux if ya dont like systemd (minimalist openrc, thus secure, but will need to setup a lot),
    and don't like glibc and prefer minimalist musl
  - use secureblue for its trivalent browser
- but we aren't installing user apps on these base oses, we will use virt-manager.
- if you want to do anything gpu intensive, you can install Venus (virt-io) gpu virtualization drivers
  for near native gpu performance, without needing to buy another frickin gpu
  just for your local ai

# Host OS Security
- wayland only for gui isolation
- disable root access
- kernel ASLR
- kernel security compilation features enable in KConfig
- hardened malloc frum graphene os
- sysctl hardening?
- hidepid=2 for minimalized kernel leaks (/proc, /sys)
- read-only partition (eroFS (better just because its faster)/squashFS)+ noexec for user directories
- selinux/apparmor (selinux is better, more granular)
- hardened software compilation flags (PIE positional independent executable)
- secure boot (unfortunately no verified boot, hardware does not exist for that)
- dm-verity / fs-verity (fs-verity better for granularity, can possibly use it to verify read-only vm images?)
- dmcrypt / fscrypt + metadata encryption (fscrypt + metadata encryption better for granularity)
- run as many system services as non privileged user
- run as many services isolated from each other
- apply mandatory access control to init system PID 1
- disable ttys?
- disable all boot information at boot
- no unnecessary kernel modules, do not enable any DMA (direct memory access, like firewall,
  thunderbolt) kernel module
- DO NOT install any user software on host os, that should be in virtual machines

# Guest OS Security
- you should care about the guest os security as well, so disable any unnecessary kernel modules to absolute
  minimum
- unikernals is interesting, can run only the app needed, but im not sure how you would pass gui bridge to it

# Q&A
Why not qubes os/chrome os?
- chromeos is good for its verified boot, and hardened base os
- qubes os, it is even more secure in some ways than chromeos (except lack of verified boot, heads is ok but its just user attestation),
  but i thought it was too limiting (yes it doesn't have gpu accel for security, but now you can't run
  your own local ai, or maybe you're a gamer)
- chromeos wasn't too limiting, and there was even a steam vm (borealis) for gaming, you could even import different games
  on it like minecraft for absolute near native gpu performance
- this setup was inspired by qubes os and chromeos, grapheneos kicksecure whonix

Why not just use flatpak?
- flatpak has too many permissions that are permissive, you can see
  that many programs ask demanding over privileged permissions BY DEFAULT
- there are shell exploits, can easily bypass the fake "sandboxing" flatpak does 
