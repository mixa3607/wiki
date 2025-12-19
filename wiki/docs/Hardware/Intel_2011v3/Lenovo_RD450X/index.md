# Lenovo RD450x
Поделие сумрачного китайского гения.
Вероятно поставлялась в дата центры крупных китайский компаний, типа Tencent и baidu по спец заказу.
На сайте Lenovo тех. поддержка не доступна. Гарантийный срок на эти платы закончился.

![board](./image.png)

## BMC
Лучший бмц это `3.24.1145` взять можно [тут же](./R3_24_1145.ima.gz)

- картинка работает
- прошивка BIOS работает
- управление питанием работает

### Прощивка и восстановление маков после зашивки
Шить можно через тулы из [архива](./v12000.zip).

Восстановление по мануалу из https://forums.overclockers.ru/viewtopic.php?p=18321593#p18321593

```shell
# channel 1 это shared c mac 6c:0b:84:d7:09:cd
sudo ipmitool raw 0x0c 0x01 1 0xc2 0x00
sudo ipmitool lan set 0x01 macaddr 6c:0b:84:d7:09:cd
sudo ipmitool lan set 1 vlan id off
sudo ipmitool mc reset cold
```

При попытке восстановить оба мака бмц у меня всегда уходил в себя и помогала только перешивка с 0, но можете погуглить этот бред

```
ipmitool lan print 1
ipmitool lan set 0x01 access on
ipmitool raw 0x0c 0x01 0x01 0xc2 0x00
ipmitool lan set 0x01 macaddr 6c:0b:84:d7:09:ce
ipmitool lan set 1 vlan id off

ipmitool lan print 8
ipmitool lan set 0x08 access on
ipmitool raw 0x0c 0x01 0x01 0xc2 0x01
ipmitool lan set 0x08 macaddr 6c:0b:84:d7:09:ce

ipmitool mc reset cold


sudo ipmitool raw 0x0c 0x01 1 0xc2 0x00
sudo ipmitool lan set 0x01 macaddr 6c:0b:84:d7:09:cd
sudo ipmitool lan set 1 vlan id off
sudo ipmitool mc reset cold

sudo ipmitool raw 0x0c 0x01 8 0xc2 0x00
sudo ipmitool lan set 8 macaddr 6c:0b:84:d7:09:cd
sudo ipmitool mc reset cold
```

### Белый экран в хроме
- Открой фаерфоксом

### Управление вертушками и прочие вкусности
Для вертушек смотрите блок [3.3 Set Fan Configuration Command](./ilide.info-bmc-command-list-specification-v0-1-1-pr_646b123c9b98b7853889bca2070d7ab6.pdf)

## BIOS
Стабильный и фичастый [биос с оверов](https://forums.overclockers.ru/viewtopic.php?p=18490614#p18490614) [клон в этой репе](./rd450m3v4.rom.gz):

- есть бифурк
- едет 2400мгц
- в системе виден ipmi
