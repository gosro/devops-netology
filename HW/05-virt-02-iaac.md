
# Домашнее задание к занятию "5.2. Применение принципов IaaC в работе с виртуальными машинами"

## Как сдавать задания

Обязательными к выполнению являются задачи без указания звездочки. Их выполнение необходимо для получения зачета и диплома о профессиональной переподготовке.

Задачи со звездочкой (*) являются дополнительными задачами и/или задачами повышенной сложности. Они не являются обязательными к выполнению, но помогут вам глубже понять тему.

Домашнее задание выполните в файле readme.md в github репозитории. В личном кабинете отправьте на проверку ссылку на .md-файл в вашем репозитории.

Любые вопросы по решению задач задавайте в чате учебной группы.

---

## Задача 1

- Опишите своими словами основные преимущества применения на практике IaaC паттернов.
IaaC патерны помогают оптимизировать работу и снизить cost of production, так же такоие паттерны спосубствуют быстрому исправлению багов и самое важное помогает наладить доставку быстрых релизов раз в неделю.
 
- Какой из принципов IaaC является основополагающим?
CI/CD, быстрая дотставка фиксов, процесс создание инфры такой же что и создание приложения, то есть инфра это код


## Задача 2

- Чем Ansible выгодно отличается от других систем управление конфигурациями?
Ансибл использует ssh протокол поэтому не приедтся устанавливать агенты на хосты, это экономит время и ресурсы
- Какой, на ваш взгляд, метод работы систем конфигурации более надёжный push или pull?
push и pull более надежный так как хост может и сам инифиировать получения конфигурации при определных случаях, но так же не отнимает возможность что то отправить на хост

## Задача 3

Установить на личный компьютер:

- VirtualBox
- Vagrant
- Ansible

*Приложить вывод команд установленных версий каждой из программ, оформленный в markdown.*
(base)  axid@MacBook-Pro-Givi  ~  VirtualBox --version
DEBUG: issetugid_for_AppKit was called by 0x7ff813d515d5 /System/Library/Frameworks/AppKit.framework/Versions/C/AppKit::_NSCheckForIllegalSetugidApp+0xb (via 0x7ff813d5137d)
DEBUG: issetugid_for_AppKit was called by 0x7ff813d515d5 /System/Library/Frameworks/AppKit.framework/Versions/C/AppKit::_NSCheckForIllegalSetugidApp+0xb (via 0x7ff813d6f489)

(base)  ✘ axid@MacBook-Pro-Givi  ~  vagrant --version
Vagrant 2.2.19

(base)  axid@MacBook-Pro-Givi  ~  ansible --version 
ansible [core 2.12.5]
  config file = None
  configured module search path = ['/Users/axid/.ansible/plugins/modules', '/usr/share/ansible/plugins/modules']
  ansible python module location = /usr/local/Cellar/ansible/5.8.0/libexec/lib/python3.10/site-packages/ansible
  ansible collection location = /Users/axid/.ansible/collections:/usr/share/ansible/collections
  executable location = /usr/local/bin/ansible
  python version = 3.10.4 (main, Apr 26 2022, 19:42:59) [Clang 13.1.6 (clang-1316.0.21.2)]
  jinja version = 3.1.2
  libyaml = True

## Задача 4 (*)

Воспроизвести практическую часть лекции самостоятельно.

- Создать виртуальную машину.
- Зайти внутрь ВМ, убедиться, что Docker установлен с помощью команды
```
docker ps
```

(base)  ✘ axid@MacBook-Pro-Givi  ~/ansible-test/vagrant  sudo /Library/StartupItems/VirtualBox/VirtualBox restart
sudo: /Library/StartupItems/VirtualBox/VirtualBox: command not found
(base)  ✘ axid@MacBook-Pro-Givi  ~/ansible-test/vagrant  sudo "/Library/Application Support/VirtualBox/LaunchDaemons/VirtualBoxStartup.sh" restart
Loading VBoxDrv.kext
Loading VBoxUSB.kext
Loading VBoxNetFlt.kext
Loading VBoxNetAdp.kext
(base)  axid@MacBook-Pro-Givi  ~/ansible-test/vagrant  sudo vagrant up                                         
Bringing machine 'server1.netology' up with 'virtualbox' provider...
==> server1.netology: Checking if box 'bento/ubuntu-20.04' version '202112.19.0' is up to date...
==> server1.netology: Clearing any previously set network interfaces...
==> server1.netology: Preparing network interfaces based on configuration...
    server1.netology: Adapter 1: nat
    server1.netology: Adapter 2: hostonly
==> server1.netology: Forwarding ports...
    server1.netology: 22 (guest) => 20011 (host) (adapter 1)
    server1.netology: 22 (guest) => 2222 (host) (adapter 1)
==> server1.netology: Running 'pre-boot' VM customizations...
==> server1.netology: Booting VM...
==> server1.netology: Waiting for machine to boot. This may take a few minutes...
    server1.netology: SSH address: 127.0.0.1:2222
    server1.netology: SSH username: vagrant
    server1.netology: SSH auth method: private key
    server1.netology: 
    server1.netology: Vagrant insecure key detected. Vagrant will automatically replace
    server1.netology: this with a newly generated keypair for better security.
    server1.netology: 
    server1.netology: Inserting generated public key within guest...
    server1.netology: Removing insecure key from the guest if it's present...
    server1.netology: Key inserted! Disconnecting and reconnecting using new SSH key...
==> server1.netology: Machine booted and ready!
==> server1.netology: Checking for guest additions in VM...
==> server1.netology: Setting hostname...
==> server1.netology: Configuring and enabling network interfaces...
==> server1.netology: Mounting shared folders...
    server1.netology: /vagrant => /Users/axid/ansible-test/vagrant
==> server1.netology: Running provisioner: ansible...
    server1.netology: Running ansible-playbook...

PLAY [nodes] *******************************************************************

TASK [Gathering Facts] *********************************************************
ok: [server1.netology]

TASK [Create directory for ssh-keys] *******************************************
changed: [server1.netology]

TASK [Adding rsa-key in /Users/axid/.ssh/authorized_keys] **********************
changed: [server1.netology]

TASK [Checking DNS] ************************************************************
changed: [server1.netology]

TASK [Installing tools] ********************************************************
ok: [server1.netology] => (item=git)
ok: [server1.netology] => (item=curl)

TASK [Installing docker] *******************************************************
changed: [server1.netology]

TASK [Add the current user to docker group] ************************************
changed: [server1.netology]

PLAY RECAP *********************************************************************
server1.netology           : ok=7    changed=5    unreachable=0    failed=0    skipped=0    rescued=0    ignored=0   

(base)  axid@MacBook-Pro-Givi  ~/ansible-test/vagrant  ls
Vagrantfile ansible.cfg
(base)  axid@MacBook-Pro-Givi  ~/ansible-test/vagrant  vagrant ssh
The VirtualBox VM was created with a user that doesn't match the
current user running Vagrant. VirtualBox requires that the same user
be used to manage the VM that was created. Please re-run Vagrant with
that user. This is not a Vagrant issue.

The UID used to create the VM was: 0
Your UID is: 501
(base)  ✘ axid@MacBook-Pro-Givi  ~/ansible-test/vagrant  sudo vagrant ssh
Welcome to Ubuntu 20.04.3 LTS (GNU/Linux 5.4.0-91-generic x86_64)

 * Documentation:  https://help.ubuntu.com
 * Management:     https://landscape.canonical.com
 * Support:        https://ubuntu.com/advantage

 System information disabled due to load higher than 1.0


This system is built by the Bento project by Chef Software
More information can be found at https://github.com/chef/bento
Last login: Tue May 31 04:53:53 2022 from 10.0.2.2
vagrant@server1:~$ docker ps
CONTAINER ID   IMAGE     COMMAND   CREATED   STATUS    PORTS     NAMES
vagrant@server1:~$ 