Core system security
1. Keep your system updated

    Regularly apply security patches to the Linux kernel and all installed software.
    On Debian and Ubuntu, you can enable automatic security updates.
    For critical server environments, consider solutions for live patching, which can apply updates to the kernel without requiring a reboot.

2. Remove unnecessary software and services

    Minimize the system's "attack surface" by removing any software packages and services that are not essential for your work.
    Periodically review and disable unused services to prevent them from becoming an entry point for attackers.

3. Manage user accounts and privileges

    Use the principle of least privilege: Only give users the permissions they need to do their jobs.
    Disable the root login: For remote access via SSH, disable the ability to log in directly as the root user. Instead, use a standard user account and elevate privileges with sudo when necessary.
    Enforce strong passwords: Configure strong password policies that require complexity, length, and regular changes. Utilize multi-factor authentication (MFA) for an extra layer of protection.

4. Secure your boot process

    Protect the BIOS/UEFI with a strong password to prevent unauthorized changes.
    Disable booting from external media, such as USB drives, in the BIOS/UEFI settings.
    Enable full-disk encryption during installation to protect data if the physical hardware is compromised or stolen.

Network security
5. Configure a firewall

    Enable and properly configure a firewall, such as iptables, nftables, or ufw (Uncomplicated Firewall), to control incoming and outgoing network traffic.
    Close all ports that are not in active use to reduce the potential for an attack.
    Consider using an Intrusion Prevention System (IPS) like Fail2ban, which automatically bans IP addresses that show malicious behavior.

6. Harden SSH remote access

    Disable password authentication for SSH and rely on secure, cryptographic key pairs instead.
    Change the default SSH port from 22 to a less common one to deter automated scanning attacks.
    Set an idle timeout in your SSH configuration to automatically disconnect inactive sessions.

File and data protection
7. Enforce mandatory access controls

    Use a framework like SELinux (on Red Hat/CentOS) or AppArmor (on Ubuntu/Debian) to enforce Mandatory Access Control (MAC) policies.
    For Ubuntu, you can check AppArmor's status with the aa-status command.

8. Manage file and directory permissions

    Regularly audit file permissions to ensure that sensitive files and directories are not exposed to unauthorized users.
    Follow the principle of least privilege for file and directory permissions.

9. Implement backups

    Regularly back up your data to ensure that you can recover from a system failure, ransomware attack, or other incident.
    Consider storing backups offsite or on a separate, air-gapped system for maximum resilience.

Monitoring and auditing
10. Monitor system activity

    Enable and configure robust logging and auditing to gain visibility into system activities and detect potential security incidents.
    Use tools like auditd to monitor security-relevant system calls.
    Consider sending logs to a remote, secure server to prevent attackers from deleting their tracks.

11. Perform regular audits

    Use security auditing tools like Lynis to scan your system and check against best practices.
    Regularly conduct audits to identify and address security weaknesses.
