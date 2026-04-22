# Simulacion-Monte-Carlo-Paralela

¿Qué hace este proyecto?
Simula la propagación de una epidemia en una población de 1 millón de personas (grilla 1000×1000) durante 365 días, usando el modelo SIR. Se comparan dos versiones: una secuencial y una paralela, midiendo cuánto se acelera al usar más núcleos.

El modelo
Cada celda es una persona en uno de 4 estados: Susceptible → Infectada → Recuperada / Fallecida. Cada día, un susceptible puede contagiarse si tiene vecinos infectados. Los parámetros son β=0.30, γ=0.05, μ=0.002, lo que da un R₀≈6.
La versión paralela
La grilla se divide en franjas horizontales, una por núcleo. Cada núcleo procesa su franja de forma independiente. Los bordes se manejan con ghost-cells (una fila extra copiada del bloque vecino) para que el contagio entre franjas funcione correctamente.

Estructura
proyecto/
├── sequential/sir_sequential.py
├── parallel/sir_parallel.py
├── results/          ← scaling.csv + gráficas
└── animations/       ← GIF comparativo
