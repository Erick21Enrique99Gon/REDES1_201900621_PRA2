<img src='https://user-images.githubusercontent.com/36779113/128587817-1a6c2fdc-d106-4dd3-b092-104c8299bded.png' background='white'>

### Universidad de San Carlos de Guatemala
### Facultad de Ingeniería
### Escuela de Ciencias y Sistemas
### Redes de Computadoras 1
### Segundo Semestre 2024
---

<center>

|NOMBRE|CARNET|
|---|---|
|Erick Enrique González Chávez|201900621|
</center>

## creación de IP virtual con HSRP

### Configuracion R1
    enlable
    configure terminal
    no ip domain-lookup
    hostname R1
    int f0/0
    ip address 112.168.1.2 255.255.255.248
    no shutdown
    do write

    int f0/1
    ip address 112.168.2.2 255.255.255.248
    no shutdown
    do write

    int s1/0
    ip address 10.0.0.1 255.255.255.252
    no shutdown
    do write

### Configuracion R2
    enlable
    configure terminal
    no ip domain-lookup
    hostname R2
    int f0/0
    ip address 112.168.1.1 255.255.255.248
                standby 10 ip 112.168.0.1
                standby 10 priority 150
                standby 10 preempt
    no shutdown
    do write
    
    int f0/1
    ip address 112.168.0.2 255.255.255.0
    standby 10 ip 112.168.0.1
    standby 10 priority 150
    standby 10 preempt
    no shutdown
    do write

### Configuracion R3
    enlable
    configure terminal
    no ip domain-lookup
    hostname R3
    int f0/0
    ip address 112.168.2.1 255.255.255.248
    no shutdown
    do write

    int f0/1
    ip address 112.168.0.3 255.255.255.0
    standby 10 ip 112.168.0.1
    standby 10 priority 150
    standby 10 preempt
    no shutdown
    do write

### Configuracion R5
    enable
    configure terminal
    no ip domain-lookup
    hostname R5
    int f0/0
    ip address 112.178.1.2 255.255.255.248
    no shutdown
    do write

    int f0/1
    ip address 112.178.0.2 255.255.255.0
    standby 10 ip 112.178.0.1
    standby 10 priority 150
    standby 10 preempt
    no shutdown
    do write
    
### Configuracion R6
    enable
    configure terminal
    no ip domain-lookup
    hostname R6
    int f0/0
    ip address 112.178.2.2 255.255.255.248
    no shutdown
    do write

    int f0/1
    ip address 112.178.0.3 255.255.255.0
    standby 10 ip 112.178.0.1
    standby 10 priority 150
    standby 10 preempt
    no shutdown
    do write

### Configuracion R4
    enlable
    configure terminal
    no ip domain-lookup
    hostname R4
    int f0/0
    ip address 112.178.1.2 255.255.255.248
    no shutdown
    do write

    int f0/1
    ip address 112.178.2.2 255.255.255.248
    no shutdown
    do write

    int s1/0
    ip address 10.0.0.2 255.255.255.252
    no shutdown
    do write