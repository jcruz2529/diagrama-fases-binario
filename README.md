# Diagrama de Fases Binario — Sistema Etanol/Agua

Herramienta en Python para calcular y visualizar el diagrama de fases de equilibrio líquido-vapor de una mezcla binaria, usando la ecuación de Antoine y resolución numérica con SciPy.

## ¿Qué hace?

- El usuario selecciona los dos componentes del sistema
- Calcula la curva de burbuja — temperatura donde el líquido empieza a hervir
- Calcula la curva de rocío — temperatura donde el vapor empieza a condensar
- Grafica ambas curvas en el diagrama de fases
- Exporta los resultados a CSV

## Ejemplo de uso

```
Componentes disponibles: ['Etanol', 'Agua']
Ingresa un componente: Etanol
Componentes disponibles: ['Etanol', 'Agua']
Ingresa un componente: Agua

Resultados exportados a diagrama_fases_etanol_agua.csv
```

## Fundamento matemático

**Presión de vapor** — Ecuación de Antoine:

```
log10(P) = A - B / (C + T)
```

**Curva de burbuja** — dado x (fracción líquida), encuentra T donde:

```
x·P_etanol(T) + (1-x)·P_agua(T) = P_total
```

**Curva de rocío** — dado y (fracción vapor), encuentra T donde:

```
y/P_etanol(T) + (1-y)/P_agua(T) = 1/P_total
```

Ambas ecuaciones se resuelven numéricamente con `scipy.optimize.fsolve`.

## Constantes de Antoine utilizadas

| Componente | A | B | C |
|-----------|---|---|---|
| Etanol | 8.1122 | 1592.864 | 226.184 |
| Agua | 7.9668 | 1668.210 | 228.000 |

Presión en mmHg, convertida a kPa (× 0.133322). Temperatura en °C.

## Requisitos

```
numpy
scipy
matplotlib
pandas
```

Instalación:

```bash
pip install numpy scipy matplotlib pandas
```

## Estructura del proyecto

```
diagrama-fases-binario/
│
├── diagrama_fases.py                    # Script principal
├── diagrama_fases_etanol_agua.csv       # Resultados exportados
└── README.md
```

## Resultados esperados

- Agua pura (x=0): T_burbuja = T_rocío ≈ 100°C
- Etanol puro (x=1): T_burbuja = T_rocío ≈ 78°C
- La curva de rocío siempre está por encima de la curva de burbuja

## Autor

Justin Cruz — Estudiante de Ingeniería Química  
Universidad Técnica de Machala (UTMACHALA)  
GitHub: github.com/jcruz2529
