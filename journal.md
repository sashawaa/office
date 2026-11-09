# Журнал выполнения работ

## 09.11.2026 — День 1

### Что сделали:
- Создан репозиторий на GitHub и клонирован на учебный компьютер
- Собрана топология в GNS3:
  - 1x Cisco RTR (маршрутизатор)
  - 1x Cisco SW (коммутатор с модулем NM-16ESW)
  - 4x RED OS 8 (IOT, CTRL, MON, DB)
  - 1x Windows Server 2019 (WIN — рабочее место администратора)
  - 1x Cloud (подключение к хост-машине)
- Настроена IP-адресация в подсети 192.168.10.0/24 (VLAN 10)
- Настроены интерфейсы на Cisco RTR (192.168.10.1) и Cisco SW (192.168.10.2)
- Настроены IP на машинах RED OS (192.168.10.11–14) и Windows Server (192.168.10.100)

### Как проверили:
- На REDOS8-1: `ip address show enp2s0` — получен адрес 192.168.10.11/24, статус UP
- На REDOS8-1: `ping -c 3 192.168.10.1` — 0% потерь, шлюз отвечает
- На Windows Server: `ipconfig` — адрес 192.168.10.100, маска 255.255.255.0, шлюз 192.168.10.1
- На Cisco RTR: `show ip interface brief` — GigabitEthernet0/0 в состоянии up/up

### Что получилось:
✅ Базовая сетевая связность внутри топологии работает корректно.
✅ Все устройства видят шлюз по умолчанию.
✅ Создана структура репозитория, заполнены README.md, .gitignore, journal.md.

### Скриншоты-доказательства:
- `proofs/redos_ip_check.png` — вывод ip address show на REDOS8-1
- `proofs/win_ipconfig.png` — вывод ipconfig на Windows Server
- `proofs/cisco_interfaces.png` — show ip interface brief на Cisco RTR