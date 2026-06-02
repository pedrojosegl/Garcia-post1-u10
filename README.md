# Post-Contenido 1 – Unidad 10: Memorias del Computador
Arquitectura de Computadores | Ingeniería de Sistemas – UFPS 2026

## Checkpoint 1 – Caché del sistema
- L1d: 48K
- L1i: 32K
- L2:  1280K
- L3:  12288K

## Compilación
gcc -O0 -o cache_bench cache_bench.c

## Ejecución
./cache_bench

## Análisis
El acceso secuencial mantiene latencia estable (~0.5 ns/byte) en todos
los niveles gracias al prefetcher de hardware.

El acceso aleatorio expone la jerarquía:
- Arrays <= 1 MB (L1/L2): diferencia mínima, datos en caché.
- 4 MB: rand sube a 2.9 ns → L2 miss, accede a L3.
- 16 MB: rand sube a 11.8 ns → L3 miss, accede a RAM.
- 64 MB: rand llega a 15.6 ns → L3 miss + TLB miss simultáneos.
