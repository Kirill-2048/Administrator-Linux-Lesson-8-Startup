Administrator-Linux-Lesson-8-Startup

# Редактирование файла /etc/default/grub

#GRUB_TIMEOUT_STYLE=hidden

GRUB_TIMEOUT=20

update-grub

# Вход без пароля. Способ 1.
## Перезагрузка
Попадаем в меню загрузчика
Нажимаем e (edit)
В конце строки, начинающейся с linux, добавляем init=/bin/bash

![Скриншот1](https://github.com/user-attachments/assets/6ed12b4f-e892-409f-9177-1624ad14f16a)

сtrl-x для загрузки системы

root@ubuntu:~# mount -o remount,rw /

## Меняем пароль пользователя
root@ubuntu:~# passwd username
## Перезагружаем машину reboot -f и заходим в систему с новым паролем (который задали сами).

# Вход без пароля. Способ 2 (через Advanced Options)

![Скриншот2](https://github.com/user-attachments/assets/6f0f24f4-0942-40a2-ab79-8ad96471eb00)

Требует пароль root:

![Скриншот3](https://github.com/user-attachments/assets/bdb471af-09a1-4947-aafb-c9f1308f27f8)

Вывод: загрузиться без пароля не получается. Работает только способ №1.

## Переименование VG
root@ubuntu:~# vgs

  VG        #PV #LV #SN Attr   VSize   VFree
  
  ubuntu-vg   1   1   0 wz--n- <23,00g 11,50g
  
  
  Имя VG -   ubuntu-vg.
  

root@ubuntu:~# vgrename ubuntu-vg ubuntu-otus

  Volume group "ubuntu-vg" successfully renamed to "ubuntu-otus"

# Правка /boot/grub/grub.cfg
Меняем ubuntu--vg на ubuntu—otus.

# Перезагрузка.
root@ubuntu:~# vgs

  VG          #PV #LV #SN Attr   VSize   VFree
  
  ubuntu-otus   1   1   0 wz--n- <23,00g 11,50g
  
  
  Имя VG -   ubuntu-otus.
  
Переименование VG произошло успешно.

