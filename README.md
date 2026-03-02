# Kali-Linux-ARM64-Lab-Build
Kali Linux Lab Build & System Optimization (Apple Silicon)

 Objective:
To engineer a fully functional cybersecurity laboratory on a non-native ARM64 architecture (Apple M-series) while overcoming hardware-specific library conflicts and storage bottlenecks.

Technical Challenges & Solutions

1. DPKG Database Corruption & Dependency Resolution
  - The Issue: Encountered Sub-process /usr/bin/dpkg returned an error code (1) during a major distribution upgrade, caused by library conflicts in the libtirpc and rpcbind packages.
- The Solution: Performed manual triage of the /var/lib/dpkg/status file. I manually edited the package states to clear "Half-Installed" flags and used sudo apt install -f to force a clean dependency tree.

2. Live Filesystem Expansion & Partition Realignment
  - The Issue: The initial 20GB disk allocation was insufficient for the kali-linux-everything suite.
  - The Solution: * Expanded virtual disk capacity in the UTM/QEMU hypervisor to 60GB.
    - Used GParted to live-migrate the swap partition and expand the primary ext4 root to partition to fill the unallocated space
    - Successfully resized the filesystem without data loss or OS re-installation
   
3. Automated Reconnaissance Validation
- The Issue: Verification of tool integrity post-installation
- The Solution: Conducted an aggressive Nmap scan (nmap -A) against the local host to verify service detection, OS fingerprinting, and script engine functionality.

Key Skills Demonstrated
- Linux Administration: DPKG repair, APT package management, and kernel-level troubleshooting.
- Storage Engineering: GParted, partition geometry, swap management
- Virtualization: Apple Silicon (ARM64) virtualization using UTM/QEMU
- Security Tooling: Network reconnaissance and service versioning via Nmap
