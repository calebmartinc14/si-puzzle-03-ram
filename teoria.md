# Teoría · Pieza 03: Memoria RAM

**Grupo:** Caleb Martín · Daniel Prades

## Conceptos clave

- **RAM (Random Access Memory):** memoria principal del ordenador. Guarda temporalmente el sistema operativo, los programas abiertos y los datos que usa la CPU.
- **Volátil:** pierde su contenido al apagar o reiniciar el equipo. El SSD/HDD, en cambio, guarda los datos de forma permanente.
- **DRAM (Dynamic RAM):** cada bit se guarda en un condensador con un transistor. Como el condensador pierde carga, hay que refrescarlo miles de veces por segundo.
- **Matriz filas/columnas:** los bits se organizan en filas y columnas. El controlador activa una fila, selecciona la columna y el módulo envía el dato a la CPU.
- **Memoria virtual:** uso del disco como RAM de emergencia cuando la RAM no basta. Reduce mucho el rendimiento.
- **MT/s:** millones de transferencias por segundo. En DDR hay dos transferencias por ciclo de reloj.
- **Ancho de banda (GB/s):** datos que se mueven por segundo. DDR5-5600 ≈ 44,8 GB/s por módulo.
- **Latencia CAS (CL):** ciclos que tarda la RAM en responder a una lectura. Menor valor = más rápida.
- **Timings:** serie de tiempos internos (CAS, RAS to CAS Delay, RAS Precharge Time), p. ej. 40-40-40.
- **Doble canal:** dos módulos trabajando en paralelo hacia la CPU. Mejora el rendimiento.
- **ECC:** detecta y corrige errores de datos. Típica en servidores.
- **XMP (Intel) / EXPO (AMD):** perfiles de la BIOS/UEFI que activan la velocidad y los timings anunciados.
- **PMIC:** chip de gestión de alimentación integrado en el módulo DDR5.

## Tabla resumen

| Tipo | Dato clave | Cuándo se usa |
|---|---|---|
| DDR3 (2007) | 800–2133 MT/s · 1,5 V | Equipos antiguos |
| DDR4 (2014) | 2133–3200 MT/s · 1,2 V | Equipos no muy antiguos; solo con placas DDR4 |
| DDR5 (2021) | 4800–6400+ MT/s · 1,1 V · 2 subcanales de 32 bits, PMIC, ECC interno | Estándar en PCs nuevos |
| UDIMM | Módulo de 288 pines (DDR5) | PCs de sobremesa |
| SO-DIMM | Formato más pequeño | Portátiles |
| LPDDR5 / 5X | Bajo consumo, normalmente soldada | Portátiles finos, móviles y tablets |
| GDDR6 / 6X | Ancho de banda muy alto | Tarjetas gráficas |
| ECC UDIMM / RDIMM | Corrección de errores | Servidores y estaciones de trabajo |

## Datos que hay que saberse

- DDR4 y DDR5 **no son compatibles**: cambian conectores, señales y controladores.
- DDR5 usa **dos subcanales de 32 bits**; DDR4, un canal de 64 bits.
- DDR5 sin XMP/EXPO funciona a **4800 MT/s y 1,1 V** (perfil JEDEC). Con XMP puede llegar a 5600 MT/s con 1,25 V.
- **DDR5-5600 = PC5-44800** → 5600 MT/s × 8 bytes = 44,8 GB/s.
- Capacidades habituales: 8, 16, 32 o 64 GB. Con 8 GB basta para ofimática; para vídeo o máquinas virtuales conviene 32 GB.
- Herramientas: **CPU-Z, HWiNFO, AIDA64** (frecuencia, timings, canales) y **MemTest86** (estabilidad y errores).
- **Averías típicas:** no arranca o da pitidos, pantallazos azules, reinicios aleatorios, errores en MemTest86, el sistema detecta menos memoria de la instalada.
- **Al instalar:** descargar la electricidad estática, oír el "clic" de las pestañas y usar las ranuras que activan el doble canal.

## Preguntas tipo test (8)

1. ¿Por qué se dice que la RAM es volátil?
    - a) Porque se calienta mucho al trabajar
    - b) Porque pierde su contenido al apagar el equipo ← correcta
    - c) Porque solo guarda datos del sistema operativo
    - d) Porque su velocidad cambia con el tiempo
    - Explicación: la RAM solo conserva la información mientras recibe energía. El disco, en cambio, guarda los datos de forma permanente.

2. ¿Por qué la DRAM necesita refrescarse constantemente?
    - a) Porque los transistores se desgastan con el uso
    - b) Porque el bus de memoria pierde la señal
    - c) Porque los condensadores que guardan los bits pierden carga ← correcta
    - d) Porque la CPU borra los datos antiguos
    - Explicación: cada bit se guarda en un condensador que se descarga con el tiempo, y por eso se refresca miles de veces por segundo.

3. ¿Cómo está organizado un módulo DDR5 respecto a DDR4?
    - a) Dos subcanales independientes de 32 bits, frente al único canal de 64 bits de DDR4 ← correcta
    - b) Un único canal de 128 bits
    - c) Cuatro canales de 16 bits
    - d) Igual que DDR4, pero con más voltaje
    - Explicación: DDR5 divide el módulo en dos subcanales de 32 bits, lo que mejora la eficiencia de acceso. Además incorpora PMIC y ECC interno.

4. ¿Cuál es el ancho de banda aproximado de un módulo DDR5-5600?
    - a) 5,6 GB/s
    - b) 28 GB/s
    - c) 56 GB/s
    - d) 44,8 GB/s ← correcta
    - Explicación: 5600 MT/s × 8 bytes (bus de 64 bits) = 44.800 MB/s = 44,8 GB/s, de ahí la denominación PC5-44800.

5. En una memoria con latencia CL40, ¿qué indica el valor 40?
    - a) Los GB de capacidad del módulo
    - b) Los ciclos de reloj que tarda en responder tras una orden de lectura ← correcta
    - c) El voltaje en décimas de voltio
    - d) El número de transferencias por segundo
    - Explicación: CL es la latencia CAS, medida en ciclos de reloj. Cuanto menor sea, más rápida responde la RAM.

6. ¿Se pueden mezclar módulos DDR4 y DDR5 en el mismo equipo?
    - a) Sí, si tienen la misma capacidad
    - b) Sí, si se activa XMP
    - c) No, porque conectores, señales y controladores son diferentes ← correcta
    - d) Solo en portátiles con SO-DIMM
    - Explicación: son generaciones incompatibles entre sí. Cada placa base y procesador admite solo un tipo.

7. ¿Qué formato de RAM se usa normalmente en un portátil?
    - a) SO-DIMM ← correcta
    - b) UDIMM
    - c) RDIMM
    - d) GDDR6
    - Explicación: SO-DIMM es el formato reducido para portátiles. UDIMM es el de sobremesa, RDIMM es de servidores y GDDR6 es para tarjetas gráficas.

8. Instalas RAM DDR5 de 5600 MT/s y el sistema la muestra a 4800 MT/s. ¿Cuál es la causa más probable?
    - a) El módulo está defectuoso
    - b) La placa no admite DDR5
    - c) Falta activar el doble canal
    - d) No se ha activado el perfil XMP/EXPO en la BIOS ← correcta
    - Explicación: sin XMP/EXPO, la RAM arranca con el perfil JEDEC estándar (4800 MT/s y 1,1 V en DDR5). Activando el perfil se alcanza la velocidad anunciada.
