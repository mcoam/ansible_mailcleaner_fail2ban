# ansible_mailcleaner_fail2ban

##### Funcionamiento

1. Archivo `exim2.conf`: Contiene la reglas para el match del `jail`
2. Archivo `iptables-repeater.conf`: Configura toda la acción a realizar con las ip que fallan con la auth 
3. Archivo `ip.blocklist.exim2`: Contiene las direcciones ip que se van bloqueando por intentos fallidos

* La política del `jail` esta configurada denteo del archivo `jail.conf` y es la siguiente:
```json
      [exim2-repeater]
      enabled  = true
      filter   = exim2
      action   = iptables-repeater[name=exim2]
      logpath  = /var/mailcleaner/log/exim_stage1/mainlog
      maxretry = 10
      findtime = 31536000
      bantime  = 31536000
