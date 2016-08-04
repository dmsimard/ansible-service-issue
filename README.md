# ansible-service-issue
Just a service issue reproducer for https://github.com/ansible/ansible-modules-core/issues/593

    # < Install docker >
    pip install git+https://github.com/ansible/ansible-container
    git clone https://github.com/dmsimard/ansible-service-issue
    cd ansible-service-issue
    ansible-container build

    No DOCKER_HOST environment variable found. Assuming UNIX socket at /var/run/docker.sock
    Starting Docker Compose engine to build your images...
    Attaching to ansible_ansible-container_1
    Cleaning up Ansible Container builder...
    Attaching to ansible_httpd_1, ansible_ansible-container_1
    ansible-container_1  |
    ansible-container_1  | PLAY [all] *********************************************************************
    ansible-container_1  |
    ansible-container_1  | TASK [setup] *******************************************************************
    ansible-container_1  | ok: [httpd]
    ansible-container_1  |
    ansible-container_1  | TASK [Enable systemd integration (1/2)] ****************************************
    ansible-container_1  | changed: [httpd]
    ansible-container_1  |
    ansible-container_1  | TASK [Enable systemd integration (2/2)] ****************************************
    ansible-container_1  | changed: [httpd] => (item=rm -f /lib/systemd/system/multi-user.target.wants/*)
    ansible-container_1  | changed: [httpd] => (item=rm -f /etc/systemd/system/*.wants/*)
    ansible-container_1  | changed: [httpd] => (item=rm -f /lib/systemd/system/local-fs.target.wants/*)
    ansible-container_1  | changed: [httpd] => (item=rm -f /lib/systemd/system/sockets.target.wants/*udev*)
    ansible-container_1  | changed: [httpd] => (item=rm -f /lib/systemd/system/sockets.target.wants/*initctl*)
    ansible-container_1  | changed: [httpd] => (item=rm -f /lib/systemd/system/basic.target.wants/*)
    ansible-container_1  | changed: [httpd] => (item=rm -f /lib/systemd/system/anaconda.target.wants/*)
    ansible-container_1  |
    ansible-container_1  | TASK [Install httpd] ***********************************************************
    ansible-container_1  | ok: [httpd]
    ansible-container_1  |
    ansible-container_1  | TASK [Enable and start httpd] **************************************************
    ansible-container_1  | fatal: [httpd]: FAILED! => {"changed": false, "failed": true, "msg": "no service or tool found for: httpd"}
    ansible-container_1  | ...ignoring
    ansible-container_1  |
    ansible-container_1  | TASK [Register unit files] *****************************************************
    ansible-container_1  | changed: [httpd]
    ansible-container_1  |
    ansible-container_1  | TASK [Print unit files] ********************************************************
    ansible-container_1  | ok: [httpd] => {
    ansible-container_1  |     "msg": [
    ansible-container_1  |         "UNIT FILE                              STATE   ",
    ansible-container_1  |         "proc-sys-fs-binfmt_misc.automount      static  ",
    ansible-container_1  |         "dev-hugepages.mount                    static  ",
    ansible-container_1  |         "dev-mqueue.mount                       static  ",
    ansible-container_1  |         "proc-sys-fs-binfmt_misc.mount          static  ",
    ansible-container_1  |         "sys-fs-fuse-connections.mount          static  ",
    ansible-container_1  |         "sys-kernel-config.mount                static  ",
    ansible-container_1  |         "sys-kernel-debug.mount                 static  ",
    ansible-container_1  |         "tmp.mount                              disabled",
    ansible-container_1  |         "systemd-ask-password-console.path      static  ",
    ansible-container_1  |         "systemd-ask-password-wall.path         static  ",
    ansible-container_1  |         "autovt@.service                        disabled",
    ansible-container_1  |         "blk-availability.service               disabled",
    ansible-container_1  |         "console-getty.service                  disabled",
    ansible-container_1  |         "console-shell.service                  disabled",
    ansible-container_1  |         "container-getty@.service               static  ",
    ansible-container_1  |         "dbus-org.freedesktop.hostname1.service static  ",
    ansible-container_1  |         "dbus-org.freedesktop.locale1.service   static  ",
    ansible-container_1  |         "dbus-org.freedesktop.login1.service    static  ",
    ansible-container_1  |         "dbus-org.freedesktop.machine1.service  static  ",
    ansible-container_1  |         "dbus-org.freedesktop.network1.service  invalid ",
    ansible-container_1  |         "dbus-org.freedesktop.timedate1.service static  ",
    ansible-container_1  |         "dbus.service                           static  ",
    ansible-container_1  |         "debug-shell.service                    disabled",
    ansible-container_1  |         "dracut-cmdline.service                 static  ",
    ansible-container_1  |         "dracut-initqueue.service               static  ",
    ansible-container_1  |         "dracut-mount.service                   static  ",
    ansible-container_1  |         "dracut-pre-mount.service               static  ",
    ansible-container_1  |         "dracut-pre-pivot.service               static  ",
    ansible-container_1  |         "dracut-pre-trigger.service             static  ",
    ansible-container_1  |         "dracut-pre-udev.service                static  ",
    ansible-container_1  |         "dracut-shutdown.service                static  ",
    ansible-container_1  |         "emergency.service                      static  ",
    ansible-container_1  |         "fstrim.service                         static  ",
    ansible-container_1  |         "getty@.service                         disabled",
    ansible-container_1  |         "halt-local.service                     static  ",
    ansible-container_1  |         "htcacheclean.service                   static  ",
    ansible-container_1  |         "httpd.service                          disabled",
    ansible-container_1  |         "initrd-cleanup.service                 static  ",
    ansible-container_1  |         "initrd-parse-etc.service               static  ",
    ansible-container_1  |         "initrd-switch-root.service             static  ",
    ansible-container_1  |         "initrd-udevadm-cleanup-db.service      static  ",
    ansible-container_1  |         "kmod-static-nodes.service              static  ",
    ansible-container_1  |         "messagebus.service                     static  ",
    ansible-container_1  |         "quotaon.service                        static  ",
    ansible-container_1  |         "rc-local.service                       static  ",
    ansible-container_1  |         "rdisc.service                          disabled",
    ansible-container_1  |         "rescue.service                         static  ",
    ansible-container_1  |         "serial-getty@.service                  disabled",
    ansible-container_1  |         "systemd-ask-password-console.service   static  ",
    ansible-container_1  |         "systemd-ask-password-wall.service      static  ",
    ansible-container_1  |         "systemd-backlight@.service             static  ",
    ansible-container_1  |         "systemd-binfmt.service                 static  ",
    ansible-container_1  |         "systemd-bootchart.service              disabled",
    ansible-container_1  |         "systemd-firstboot.service              static  ",
    ansible-container_1  |         "systemd-fsck-root.service              static  ",
    ansible-container_1  |         "systemd-fsck@.service                  static  ",
    ansible-container_1  |         "systemd-halt.service                   static  ",
    ansible-container_1  |         "systemd-hibernate-resume@.service      static  ",
    ansible-container_1  |         "systemd-hibernate.service              static  ",
    ansible-container_1  |         "systemd-hostnamed.service              static  ",
    ansible-container_1  |         "systemd-hwdb-update.service            static  ",
    ansible-container_1  |         "systemd-hybrid-sleep.service           static  ",
    ansible-container_1  |         "systemd-initctl.service                static  ",
    ansible-container_1  |         "systemd-journal-catalog-update.service static  ",
    ansible-container_1  |         "systemd-journal-flush.service          static  ",
    ansible-container_1  |         "systemd-journald.service               static  ",
    ansible-container_1  |         "systemd-kexec.service                  static  ",
    ansible-container_1  |         "systemd-localed.service                static  ",
    ansible-container_1  |         "systemd-logind.service                 static  ",
    ansible-container_1  |         "systemd-machine-id-commit.service      static  ",
    ansible-container_1  |         "systemd-machined.service               static  ",
    ansible-container_1  |         "systemd-modules-load.service           static  ",
    ansible-container_1  |         "systemd-nspawn@.service                disabled",
    ansible-container_1  |         "systemd-poweroff.service               static  ",
    ansible-container_1  |         "systemd-quotacheck.service             static  ",
    ansible-container_1  |         "systemd-random-seed.service            static  ",
    ansible-container_1  |         "systemd-readahead-collect.service      disabled",
    ansible-container_1  |         "systemd-readahead-done.service         static  ",
    ansible-container_1  |         "systemd-readahead-drop.service         disabled",
    ansible-container_1  |         "systemd-readahead-replay.service       disabled",
    ansible-container_1  |         "systemd-reboot.service                 static  ",
    ansible-container_1  |         "systemd-remount-fs.service             static  ",
    ansible-container_1  |         "systemd-rfkill@.service                static  ",
    ansible-container_1  |         "systemd-shutdownd.service              static  ",
    ansible-container_1  |         "systemd-suspend.service                static  ",
    ansible-container_1  |         "systemd-sysctl.service                 static  ",
    ansible-container_1  |         "systemd-timedated.service              static  ",
    ansible-container_1  |         "systemd-tmpfiles-clean.service         static  ",
    ansible-container_1  |         "systemd-tmpfiles-setup-dev.service     static  ",
    ansible-container_1  |         "systemd-tmpfiles-setup.service         static  ",
    ansible-container_1  |         "systemd-udev-settle.service            static  ",
    ansible-container_1  |         "systemd-udev-trigger.service           static  ",
    ansible-container_1  |         "systemd-udevd.service                  static  ",
    ansible-container_1  |         "systemd-update-done.service            static  ",
    ansible-container_1  |         "systemd-update-utmp-runlevel.service   static  ",
    ansible-container_1  |         "systemd-update-utmp.service            static  ",
    ansible-container_1  |         "systemd-user-sessions.service          static  ",
    ansible-container_1  |         "systemd-vconsole-setup.service         static  ",
    ansible-container_1  |         "-.slice                                static  ",
    ansible-container_1  |         "machine.slice                          static  ",
    ansible-container_1  |         "system.slice                           static  ",
    ansible-container_1  |         "user.slice                             static  ",
    ansible-container_1  |         "dbus.socket                            static  ",
    ansible-container_1  |         "syslog.socket                          static  ",
    ansible-container_1  |         "systemd-initctl.socket                 static  ",
    ansible-container_1  |         "systemd-journald.socket                static  ",
    ansible-container_1  |         "systemd-networkd.socket                disabled",
    ansible-container_1  |         "systemd-shutdownd.socket               static  ",
    ansible-container_1  |         "systemd-udevd-control.socket           static  ",
    ansible-container_1  |         "systemd-udevd-kernel.socket            static  ",
    ansible-container_1  |         "basic.target                           static  ",
    ansible-container_1  |         "bluetooth.target                       static  ",
    ansible-container_1  |         "cryptsetup-pre.target                  static  ",
    ansible-container_1  |         "cryptsetup.target                      static  ",
    ansible-container_1  |         "ctrl-alt-del.target                    disabled",
    ansible-container_1  |         "default.target                         enabled ",
    ansible-container_1  |         "emergency.target                       static  ",
    ansible-container_1  |         "final.target                           static  ",
    ansible-container_1  |         "getty.target                           static  ",
    ansible-container_1  |         "graphical.target                       static  ",
    ansible-container_1  |         "halt.target                            disabled",
    ansible-container_1  |         "hibernate.target                       static  ",
    ansible-container_1  |         "hybrid-sleep.target                    static  ",
    ansible-container_1  |         "initrd-fs.target                       static  ",
    ansible-container_1  |         "initrd-root-fs.target                  static  ",
    ansible-container_1  |         "initrd-switch-root.target              static  ",
    ansible-container_1  |         "initrd.target                          static  ",
    ansible-container_1  |         "kexec.target                           disabled",
    ansible-container_1  |         "local-fs-pre.target                    static  ",
    ansible-container_1  |         "local-fs.target                        static  ",
    ansible-container_1  |         "machines.target                        disabled",
    ansible-container_1  |         "multi-user.target                      enabled ",
    ansible-container_1  |         "network-online.target                  static  ",
    ansible-container_1  |         "network-pre.target                     static  ",
    ansible-container_1  |         "network.target                         static  ",
    ansible-container_1  |         "nss-lookup.target                      static  ",
    ansible-container_1  |         "nss-user-lookup.target                 static  ",
    ansible-container_1  |         "paths.target                           static  ",
    ansible-container_1  |         "poweroff.target                        disabled",
    ansible-container_1  |         "printer.target                         static  ",
    ansible-container_1  |         "reboot.target                          disabled",
    ansible-container_1  |         "remote-fs-pre.target                   static  ",
    ansible-container_1  |         "remote-fs.target                       disabled",
    ansible-container_1  |         "rescue.target                          disabled",
    ansible-container_1  |         "rpcbind.target                         static  ",
    ansible-container_1  |         "runlevel0.target                       disabled",
    ansible-container_1  |         "runlevel1.target                       disabled",
    ansible-container_1  |         "runlevel2.target                       static  ",
    ansible-container_1  |         "runlevel3.target                       static  ",
    ansible-container_1  |         "runlevel4.target                       static  ",
    ansible-container_1  |         "runlevel5.target                       static  ",
    ansible-container_1  |         "runlevel6.target                       disabled",
    ansible-container_1  |         "shutdown.target                        static  ",
    ansible-container_1  |         "sigpwr.target                          static  ",
    ansible-container_1  |         "sleep.target                           static  ",
    ansible-container_1  |         "slices.target                          static  ",
    ansible-container_1  |         "smartcard.target                       static  ",
    ansible-container_1  |         "sockets.target                         static  ",
    ansible-container_1  |         "sound.target                           static  ",
    ansible-container_1  |         "suspend.target                         static  ",
    ansible-container_1  |         "swap.target                            static  ",
    ansible-container_1  |         "sysinit.target                         static  ",
    ansible-container_1  |         "system-update.target                   static  ",
    ansible-container_1  |         "time-sync.target                       static  ",
    ansible-container_1  |         "timers.target                          static  ",
    ansible-container_1  |         "umount.target                          static  ",
    ansible-container_1  |         "fstrim.timer                           disabled",
    ansible-container_1  |         "systemd-readahead-done.timer           static  ",
    ansible-container_1  |         "systemd-tmpfiles-clean.timer           static  ",
    ansible-container_1  |         "",
    ansible-container_1  |         "169 unit files listed."
    ansible-container_1  |     ]
    ansible-container_1  | }
    ansible-container_1  |
    ansible-container_1  | TASK [Check existence of canary] ***********************************************
    ansible-container_1  | failed: [httpd] (item=/run/systemd/system/) => {"changed": true, "cmd": ["ls", "-al", "/run/systemd/system/"], "delta": "0:00:00.010253", "end": "2016-08-04 22:59:33.294416", "failed": true, "item": "/run/systemd/system/", "rc": 2, "start": "2016-08-04 22:59:33.284163", "stderr": "ls: cannot access /run/systemd/system/: No such file or directory", "stdout": "", "stdout_lines": [], "warnings": []}
    ansible-container_1  | failed: [httpd] (item=/dev/.run/systemd/) => {"changed": true, "cmd": ["ls", "-al", "/dev/.run/systemd/"], "delta": "0:00:00.009781", "end": "2016-08-04 22:59:33.570516", "failed": true, "item": "/dev/.run/systemd/", "rc": 2, "start": "2016-08-04 22:59:33.560735", "stderr": "ls: cannot access /dev/.run/systemd/: No such file or directory", "stdout": "", "stdout_lines": [], "warnings": []}
    ansible-container_1  | failed: [httpd] (item=/dev/.systemd/) => {"changed": true, "cmd": ["ls", "-al", "/dev/.systemd/"], "delta": "0:00:00.009796", "end": "2016-08-04 22:59:33.851090", "failed": true, "item": "/dev/.systemd/", "rc": 2, "start": "2016-08-04 22:59:33.841294", "stderr": "ls: cannot access /dev/.systemd/: No such file or directory", "stdout": "", "stdout_lines": [], "warnings": []}
    ansible-container_1  | ...ignoring
    ansible-container_1  |
    ansible-container_1  | TASK [fail] ********************************************************************
    ansible-container_1  | fatal: [httpd]: FAILED! => {"changed": false, "failed": true, "msg": "Failed as requested from task"}
    ansible-container_1  |
    ansible-container_1  | NO MORE HOSTS LEFT *************************************************************
    ansible-container_1  | 	to retry, use: --limit @main.retry
    ansible-container_1  |
    ansible-container_1  | PLAY RECAP *********************************************************************
    ansible-container_1  | httpd                      : ok=8    changed=3    unreachable=0    failed=1
    ansible-container_1  |
    ansible_ansible-container_1 exited with code 2
    Aborting on container exit...
    Stopping ansible_httpd_1 ... done
    Ansible playbook run failed.
    Cleaning up Ansible Container builder...
    Ansible build failed
