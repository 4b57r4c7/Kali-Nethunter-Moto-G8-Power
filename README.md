# Kernel за Moto G8 Power (sofiar, XT2041-3) – NetHunter експеримент

Сорс: [MotorolaMobilityLLC/kernel-msm @ MMI-RPES31.Q4U-47-35-12](https://github.com/MotorolaMobilityLLC/kernel-msm/tree/MMI-RPES31.Q4U-47-35-12)
(точно съвпада със стоковия Android 11 билд RPES31.Q4U-47-35-12, RETEU).

Билдът върви в GitHub Actions (`Actions → Build sofiar kernel → Run workflow`).
Резултатът е boot образ = **стоков ramdisk + стоков dtb + новото ядро**.

## Тест – САМО в RAM

```
fastboot boot boot-sofiar-test-*.img
```

`fastboot boot` не записва нищо по телефона. При проблем – рестарт и телефонът е на стоковия boot.
**Не флашвай** образа (`fastboot flash boot ...`), докато тестът не мине напълно (тъч, Wi-Fi, мрежа, IMEI).

## Файлове

- `stock/boot_a.img` – стоковият boot от телефона (без лични данни).
- `stock/kernel.config` – точната конфигурация, извадена от стоковото ядро (`extract-ikconfig`).
- `configs/sofiar-base.config` – задължителни промени (изключен `MODULE_SIG_FORCE`).
- `configs/*.config` – допълнителни фрагменти (напр. NetHunter), избират се при стартиране.

⚠️ Репото е публично – никога не качвай тук EFS/IMEI бекъпи (modemst*, fsg, persist и т.н.).
