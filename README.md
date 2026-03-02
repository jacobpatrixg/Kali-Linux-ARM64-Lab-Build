# Kali-Linux-ARM64-Lab-Build
Kali Linux Lab Build & System Optimization (Apple Silicon)
<img width="962" height="838" alt="Screenshot 2026-03-02 at 12 28 24 AM" src="https://github.com/user-attachments/assets/ed41a917-79fd-484b-8f4f-1f498568b320" />


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
   <img width="960" height="830" alt="Screenshot 2026-03-02 at 12 24 36 AM" src="https://github.com/user-attachments/assets/5394d095-58a8-4f44-8ab9-4a7a10befff4" />

   
3. Automated Reconnaissance Validation
- The Issue: Verification of tool integrity post-installation
- The Solution: Conducted an aggressive Nmap scan (nmap -A) against the local host to verify service detection, OS fingerprinting, and script engine functionality.

Key Skills Demonstrated
- Linux Administration: DPKG repair, APT package management, and kernel-level troubleshooting.
- Storage Engineering: GParted, partition geometry, swap management
- Virtualization: Apple Silicon (ARM64) virtualization using UTM/QEMU
- Security Tooling: Network reconnaissance and service versioning via Nmap

Verification & Testing

<img width="788" height="605" alt="Screenshot 2026-03-02 at 12 27 25 AM" src="https://github.com/user-attachments/assets/64c18458-dcee-4ff9-8b0c-4d1eceb5787d" />
