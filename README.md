# Informe de Escaneo de Puertos y Vulnerabilidades

## Análisis de Metasploitable utilizando Nessus y Herramientas de Escaneo de Puertos

**Nombre**: Nicolás Vidal, Analista en Ciberseguridad  
**Fecha**: 20 de marzo de 2025  

---

## Resumen Ejecutivo

Este informe detalla los resultados del escaneo de puertos y vulnerabilidades realizados en la máquina **Metasploitable** utilizando la herramienta **Nessus**. El objetivo principal fue identificar puertos abiertos y vulnerabilidades críticas que pudieran representar un riesgo para la seguridad del sistema.  

Se encontraron **10 puertos abiertos** y **16 vulnerabilidades** (8 críticas y 8 de severidad alta) que requieren atención inmediata. Este informe se centrará en las vulnerabilidades más críticas debido a su impacto potencial en la seguridad del sistema.

---

## Metodología

### Descripción del Entorno
- **Herramientas utilizadas**: Nessus.
- **Entorno de pruebas**: 
  - **Kali Linux**: Utilizado para la instalación de Nessus y la ejecución de los escaneos.
  - **Metasploitable**: Máquina objetivo con servicios vulnerables configurados.

### Proceso de Escaneo
1. **Escaneo de Puertos**: Se utilizó Nessus para identificar los puertos abiertos en Metasploitable. Aunque Nessus es una herramienta potente, se recomienda complementar este proceso con **Nmap** para obtener resultados más detallados y menos ruidosos.
2. **Escaneo de Vulnerabilidades**: Se realizó un escaneo avanzado con Nessus para detectar vulnerabilidades en los servicios expuestos.

---

## Resultados del Escaneo de Puertos

Se identificaron **10 puertos abiertos** en Metasploitable, los cuales exponen servicios potencialmente vulnerables. A continuación, se detallan los puertos y servicios asociados:

| Puerto | Servicio  | Estado  |
|--------|-----------|---------|
| 111    | RPC       | Abierto |
| 139    | NetBIOS   | Abierto |
| 445    | SMB       | Abierto |
| 2049   | NFS       | Abierto |
| 35059  | Desconocido| Abierto |
| 39340  | Desconocido| Abierto |
| 50113  | Desconocido| Abierto |
| 51028  | Desconocido| Abierto |
| 51496  | Desconocido| Abierto |
| 53603  | Desconocido| Abierto |

---

## Análisis de Vulnerabilidades

Se detectaron **16 vulnerabilidades** de alta criticidad (8 críticas y 8 de severidad alta). A continuación, se detallan las más relevantes:

### Vulnerabilidades Críticas

1. **UnrealIRCd Backdoor Detection**  
   - **Descripción**: El servidor IRC remoto es una versión de UnrealIRCd que contiene una puerta trasera, lo que permite a un atacante ejecutar código arbitrario en el sistema afectado.  
   - **Solución**: Se recomienda reinstalar el software descargándolo desde una fuente confiable y verificando su integridad mediante checksums MD5/SHA1.

2. **VNC Server 'password' Password**  
   - **Descripción**: El servidor VNC está protegido con una contraseña débil ("password"). Un atacante podría explotar esta vulnerabilidad para tomar el control del sistema.  
   - **Solución**: Cambiar la contraseña del servidor VNC por una más segura.

3. **Apache Tomcat AJP Connector Request Injection (Ghostcat)**  
   - **Descripción**: Vulnerabilidad en el conector AJP de Apache Tomcat que permite la inyección de solicitudes y la exposición de archivos sensibles.  
   - **Solución**: Actualizar Apache Tomcat a la última versión y deshabilitar el conector AJP si no es necesario.

4. **Bind Shell Backdoor Detection**  
   - **Descripción**: Se detectó un shell inverso en el sistema, lo que permite a un atacante obtener acceso remoto.  
   - **Solución**: Investigar y eliminar el backdoor, y asegurar los servicios expuestos.

5. **SSL Version 2 and 3 Protocol Detection**  
   - **Descripción**: El servidor soporta versiones obsoletas de SSL (v2 y v3), lo que lo hace vulnerable a ataques como POODLE.  
   - **Solución**: Deshabilitar SSLv2 y SSLv3, y utilizar TLS 1.2 o superior.

6. **Apache Tomcat SEoL (<= 5.5.x)**  
   - **Descripción**: Versión vulnerable de Apache Tomcat que ya no recibe soporte ni actualizaciones de seguridad.  
   - **Solución**: Actualizar a una versión soportada de Apache Tomcat.

7. **Debian OpenSSH/OpenSSL Package Random Number Generator Weakness**  
   - **Descripción**: Debilidad en la generación de números aleatorios en paquetes de OpenSSH/OpenSSL, lo que compromete la seguridad de las conexiones SSL.  
   - **Solución**: Actualizar los paquetes afectados.

8. **VNC Server 'password' Password**  
   - **Descripción**: El servidor VNC está protegido con una contraseña débil ("password"). Un atacante podría explotar esta vulnerabilidad para tomar el control del sistema.  
   - **Solución**: Cambiar la contraseña del servidor VNC por una más segura.

---

### Vulnerabilidades de Severidad Alta

1. **ISC BIND Service Downgrade / Reflected DoS**  
   - **Descripción**: Vulnerabilidad en el servicio BIND que permite ataques de denegación de servicio (DoS).  
   - **Solución**: Actualizar el servicio BIND a la última versión.

2. **NFS Shares World Readable**  
   - **Descripción**: Los recursos compartidos de NFS son accesibles públicamente, lo que expone información sensible.  
   - **Solución**: Restringir el acceso a los recursos compartidos de NFS.

3. **SSL DROWN Attack Vulnerability**  
   - **Descripción**: Vulnerabilidad que permite descifrar conexiones SSL/TLS mediante el ataque DROWN.  
   - **Solución**: Deshabilitar SSLv2 y actualizar los certificados.

4. **SSL Medium Strength Cipher Suites Supported (SWEET32)**  
   - **Descripción**: El servidor soporta suites de cifrado de fuerza media, lo que lo hace vulnerable a ataques SWEET32.  
   - **Solución**: Deshabilitar suites de cifrado obsoletas.

5. **SSL RC4 Cipher Suites Supported (Bar Mitzvah)**  
   - **Descripción**: El servidor soporta suites de cifrado RC4, lo que lo hace vulnerable a ataques Bar Mitzvah.  
   - **Solución**: Deshabilitar RC4 y utilizar cifrados más seguros.

6. **Samba Badlock Vulnerability**  
   - **Descripción**: Vulnerabilidad en Samba que permite a un atacante escalar privilegios.  
   - **Solución**: Actualizar Samba a la última versión.

7. **rlogin Service Detection**  
   - **Descripción**: El servicio rlogin está activo, lo que representa un riesgo de seguridad.  
   - **Solución**: Deshabilitar el servicio rlogin.

8. **rsh Service Detection**  
   - **Descripción**: El servicio rsh está activo, lo que representa un riesgo de seguridad.  
   - **Solución**: Deshabilitar el servicio rsh.

---

## Recomendaciones

1. **Actualizaciones de Software**: Asegúrese de que todos los servicios y aplicaciones estén actualizados a sus últimas versiones.
2. **Configuración Segura**: Deshabilite servicios innecesarios y configure contraseñas seguras.
3. **Monitoreo Continuo**: Implemente herramientas de monitoreo para detectar actividades sospechosas.
4. **Cifrado**: Utilice protocolos de cifrado modernos (TLS 1.2 o superior) y deshabilite cifrados obsoletos.

---

## Conclusión

El análisis de Metasploitable reveló múltiples vulnerabilidades críticas y de alta severidad que representan un riesgo significativo para la seguridad del sistema. Se recomienda abordar estas vulnerabilidades de inmediato para mitigar posibles ataques. Este informe destaca la importancia de realizar escaneos de seguridad periódicos y mantener los sistemas actualizados.

---

## Anexos

### Capturas de Pantalla
- Resultados de Nessus: [Ver capturas](https://github.com/Naickoo/Informe-Escaneo-Nessus/tree/main/Escaneo%20con%20nessus)

### Enlaces de Instalación y Documentación de Nessus
- **Instalación de Nessus Essentials**: [Guía de instalación](https://es-la.tenable.com/products/nessus/nessus-essentials)
- **Documentación oficial de Nessus**: [Documentación de Nessus](https://docs.tenable.com/nessus/)

---
