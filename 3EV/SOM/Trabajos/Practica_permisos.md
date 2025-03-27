![image](https://github.com/user-attachments/assets/c22a50b2-f737-4c7e-a756-30795791742b)# **Práctica: Archivos, permisos y usuarios en Linux**

## **Objetivo**
Familiarizarse con los tipos de archivos en Linux, su gestión básica, permisos, propietarios y comandos relevantes. Usare WebVM ya que suele gustarme probar las nuevas tecnologia y es algo que con el tiempo cada vez sera muy importante, es lo mismo que virtualizar con una aplicacion pero desde la web con la api que tiene los navegadores.
Debido a las limitaciones de el sistema operativo de WebVM, lo hare tanto en VMWare como en WebVM.

---

### **1. Crear un fichero con touch**
```bash
touch prueba
```
![image](https://github.com/user-attachments/assets/ca7a53e5-86b2-4a3b-8d2e-c01fe54c2e84)
![image](https://github.com/user-attachments/assets/07704fae-beec-4be3-a887-c1df0e5d4fcb)


Verifica su comportamiento con:
```bash
man touch
```
WebVM no contiene el comando man
![image](https://github.com/user-attachments/assets/7e17c92a-fd33-4cef-99c8-187381c5ae47)

---

### **2. Ver tipo de fichero con `ls -l`**
```bash
ls -l prueba
```
- El primer carácter (-) indica que es un fichero normal.

Referencia (Tambien lo tengo en el cuaderno): [https://en.wikipedia.org/wiki/Unix_file_types](https://en.wikipedia.org/wiki/Unix_file_types)
![image](https://github.com/user-attachments/assets/fb56715b-3162-45ab-80d2-e83345caec4c)
![image](https://github.com/user-attachments/assets/79ccc11a-e287-49c8-9eef-20fab0f5afa2)


---

### **3. Usar `file` para analizar el tipo**
```bash
file prueba
```
- Nos indica que es un archivo vacío (empty).
![image](https://github.com/user-attachments/assets/247def79-0ef8-42b0-8d78-9a79d6b86c62)
![image](https://github.com/user-attachments/assets/4c0ec69d-db21-4132-a726-6d33d06033ef)

---

### **4. Editar el archivo con nano y repetir `file`**
```bash
nano prueba
```
Escribe algo y guarda.
```bash
file prueba
```
- Ahora indica "ASCII text" o similar.
![image](https://github.com/user-attachments/assets/6384b6e6-c793-4710-ae83-6da5d4416d88)
![image](https://github.com/user-attachments/assets/eeab6460-314c-4baa-a6e5-7b3105bab847)

---

### **5. Descargar una página con wget**
WebVM no tiene internet.
```bash
wget www.miguvt.com
```
Como no funciona wget en la vm porque las webs protegen contra agentes como wget, he decidido hacer una web simple en local.

```bash
file index.html
```
![image](https://github.com/user-attachments/assets/9c8cc968-cbcd-40a2-951e-9d923233b267)

---

### **6. Cambiar nombre y volver a ejecutar `file`**
```bash
mv index.html index
file index
```
- Se reconoce igualmente como HTML por su contenido.
![image](https://github.com/user-attachments/assets/f2e44d76-5c30-482e-a969-8dbab2920519)


---

### **7. Directorios en Linux**
```bash
ls -l ~
file ~/Escritorio
```
WebVM:
![image](https://github.com/user-attachments/assets/c8c55313-ba58-4ae4-89ee-240aead141d2)
El comprotamiento en ubuntu es diferente ya sea porque es una version mas antigua o algo parecido.
![image](https://github.com/user-attachments/assets/ae61c389-9353-4a0c-8af8-1151a074fce4)

---

### **8. Crear archivos y verificar permisos**
```bash
nano mensaje
nano f1
nano f2
nano f3
ls -l
```
![image](https://github.com/user-attachments/assets/1c28026e-ee4e-4dc8-bf0a-fef0da83f272)

---

### **9. Denegar permisos al resto**
```bash
chmod o-rwx f1 f2 f3
ls -l
```
![image](https://github.com/user-attachments/assets/6b576f18-4e10-4a1b-b5cd-5782a8afe626)

---

### **10. Denegar lectura y ejecución a todos en f1**
```bash
chmod ugo-rx f1
ls -l
```
![image](https://github.com/user-attachments/assets/89128f6a-8292-4535-86d8-092c38c89d6e)

Intentar acceder a `f1`.
![image](https://github.com/user-attachments/assets/530e9319-8c38-44a9-95a7-61ad92a27ee3)

---

### **11. Dar lectura al propietario de f1**
```bash
chmod u+r f1
ls -l
cat f1
```
![image](https://github.com/user-attachments/assets/4ca9b880-f2ad-4f2e-ab78-4bbe25c7a3d3)

---

### **12. Quitar permiso de escritura y editar**
```bash
chmod u-w f1
nano f1
```
- Nano indicará que no se puede guardar.
![image](https://github.com/user-attachments/assets/9b6086da-36d6-48a1-bb46-042d0392e2e7)


---

### **13. Cambiar permisos de lectura y ejecución**
```bash
chmod ug=rx,o= f1 f2
ls -l
```
![image](https://github.com/user-attachments/assets/3286a7e7-5d2a-41c1-9262-02ea92a68a75)
![image](https://github.com/user-attachments/assets/9f9944f9-f291-4428-937c-884fb6b25347)
No tengo permisos

---

### **14. Cambiar permisos específicos a "mensaje"**
```bash
chmod ug=rx,o= mensaje
ls -l
```
![image](https://github.com/user-attachments/assets/e8805894-a4f0-4f63-820d-bdebe1c6a78b)


---

### **15. Quitar todos los permisos a "mensaje"**
```bash
chmod 000 mensaje
./mensaje
```
![image](https://github.com/user-attachments/assets/6a0d730d-feed-4d2a-a151-d8c4b85951f5)
No es posible, ya que no tenemos permisos

---

### **16. Dar permisos detallados a "mensaje"**
```bash
chmod u=rw,g=r,o= mensaje
ls -l
```
![image](https://github.com/user-attachments/assets/5da4623c-b0b2-4e47-b5af-aaa57c64d73c)

---

### **17. Permisos específicos variados**
```bash
chmod u=rw,g=x,o=rx mensaje
ls -l
```
![image](https://github.com/user-attachments/assets/295b2644-5bb7-499e-8cef-dcb9b8775332)
Lo mismo, seguimos sin permisos
---

### **18. Crear directorios y ficheros**
```bash
mkdir dir1 dir2 dir3
nano dir1/fich11
nano dir2/fich22
nano dir3/fich33
cp mensaje dir3/
```
![image](https://github.com/user-attachments/assets/b8cb7453-8309-419e-bc2a-2c6ba53a5c15)


---

### **19. Quitar permisos de lectura/escritura/ejecución**
```bash
chmod a-r dir1
chmod a-w dir2
chmod a-x dir3
```
![image](https://github.com/user-attachments/assets/8218fdae-ae1b-4bdb-ba71-f76a24334546)

---

### **20. Listar dir1**
```bash
ls dir1
```
- Error: permiso denegado.
![image](https://github.com/user-attachments/assets/c9dbb1b8-a004-4574-a1fd-e09700f8fc39)

---

### **21. Acceder a dir1 y ver contenido de fich11**
```bash
cd dir1
less fich11
```
- Si me deja, en ubuntu no dejaria, aqui a lo que no tengo acceso es a leer la carpeta, los archivos si.
![image](https://github.com/user-attachments/assets/89c38398-d138-42ff-93f4-c429fbd9ad8d)

---

### **22. Acceder a dir2, ver y modificar fich22**
```bash
cd ~/dir2
ls
cat fich22
nano fich22
```
- Sorprendentemente, se puede modificar (falta permiso de escritura pero deja escribirlo). En ubuntu no deja.
![image](https://github.com/user-attachments/assets/cfce6fde-9a4c-4c2a-b310-3400d3a02147)
![image](https://github.com/user-attachments/assets/a24c6f6f-a027-49ad-bf03-f1f3be870fa4)


---

### **23. Acceder a dir3 desde escritorio**
```bash
ls dir3
cat dir3/fich33
nano dir3/archivo.txt
rm dir3/archivo.txt
```
- Por mi logica fallaria por falta de ejecución. Este SO si me deja, en Ubuntu no dejaria.
![image](https://github.com/user-attachments/assets/af4bf11e-62f7-4ec0-9dfd-f79f48cec90a)


---

### **24. Crear nuevo usuario**
```bash
sudo adduser nuevo
```
[captura: sudo adduser nuevo] - El comando lo ejecutare en ubuntu

---

### **25. Crear dir4, fich41 y fich42 con permisos**
```bash
mkdir dir4
nano dir4/fich41
nano dir4/fich42
chmod 660 dir4/fich41
```
![image](https://github.com/user-attachments/assets/80c8fc31-17bf-4248-8eb6-584940480402)

---

### **26. Iniciar sesión como "nuevo" y leer fich41**
```bash
su - nuevo
cat ~/dir4/fich41
```
- Permiso denegado.
[captura: cat fich41] - Lo hare en ubuntu

---

### **27. Cambiar propietario de fich41**
```bash
exit
sudo chown nuevo dir4/fich41
```
[captura: ls -l dir4] - Lo hare en ubuntu

---

### **28. Acceder como nuevo**
```bash
su - nuevo
cat ~/dir4/fich41
```
- Accede correctamente.
[captura: cat fich41] - Tmb lo hare en ubuntu

---

### **29. Cambiar grupo de fich41**
```bash
exit
sudo chgrp nuevo dir4/fich41
```
[captura: ls -l dir4] - Lo hare en ubuntu

---

### **30. Acceder de nuevo como "nuevo"**
```bash
su - nuevo
cat ~/dir4/fich41
```
- Tiene permisos si pertenece al grupo.
[captura: cat fich41] - Lo hare en ubuntu

---

### **31. Umask para archivos sólo del propietario**
```bash
umask 077
nano fich44
ls -l fich44
```
[captura: umask 077 y ls -l fich44] - Lo hare en ubuntu



Los que pone [captura: umask 077 y ls -l fich44] es para hacerlo en mi casa ya que el vmware va mas fluido y me cuesta menos.
