#sr-due 
Назначение: описывает демон/процесс и его жизненный цикл. Ключевые секции/поля:
- \[Unit]: Description=, Requires=, Wants=, Before=, After=
- \[Service]:
	- Type=: simple (по умолчанию), forking, notify, oneshot, idle
	- ExecStart=, ExecStartPre=, ExecStartPost=, ExecReload=, ExecStop=
	- Restart= (on-failure | always | ...), RestartSec=, StartLimitIntervalSec=, StartLimitBurst=
	- User=, Group=, Environment=, EnvironmentFile=
	- WorkingDirectory=, TimeoutStartSec=, TimeoutStopSec=
	- KillMode= (control-group|process|mixed), KillSignal=, SuccessExitStatus=
- \[Install]: WantedBy=/RequiredBy= (к каким target привязывать)

Команды:
```bash
systemctl start|stop|restart <name>.service
systemctl enable|disable <name>.service
systemctl status <name>.service
systemctl cat/show <name>.service
```
[[Obsidian Vault/Rebrain/Studying/Linux Internals/Systemd/Units/service|service]]
[[Units]]