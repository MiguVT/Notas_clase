Primero comprobamos que la tarjeta WiFi soporta el modo Hosted Network
win + r -> cmd -> ejecutar ```netsh wlan show drivers```

![image](https://github.com/user-attachments/assets/88d16600-0f8b-4e09-9a17-5038095f5266)


Creamos la red:
```netsh wlan set hostednetwork mode=allow ssid=Mi_RED13 key=Contra13```
![image](https://github.com/user-attachments/assets/a9bf3253-2115-463f-8c9d-58611a1cbb6a)

Iniciamos la red:
```netsh wlan start hostednetwork```
![image](https://github.com/user-attachments/assets/dc46ac1d-8bf6-440b-a0b0-3f1ba65c05e8)

Compartimos el acceso a internet:
vamos a Panel de control > Redes e Internet > Centro de redes y recursos compartidos.
Buscamos la conexión principal a internet (en clase es Ethernet).
Hacemos clic derecho sobre ella y selecciona Propiedades.
En la pestaña Compartir marco "Permitir que otros usuarios de la red se conecten a través de la conexión a Internet de este equipo".
En Conexión de red doméstica, seleccionamos la red ad hoc que hemos creado

![image](https://github.com/user-attachments/assets/e89419db-3bdc-46ed-adb7-d0e8b2a2f1fe)



Comprobamos que funcione:
![image](https://github.com/user-attachments/assets/1a7e6ea5-875c-4968-80ea-88eb71938579)




Detenemos la red:
```
netsh wlan stop hostednetwork
```
![image](https://github.com/user-attachments/assets/9ca22cab-36f1-4eb3-a6b8-1652704460e4)

