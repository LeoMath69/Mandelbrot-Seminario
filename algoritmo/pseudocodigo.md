# Algoritmo para la estimación de la dimensión fractal del conjunto de Mandelbrot

## Método de Box Counting

**Entrada:**
- Dominio del plano complejo: \([-2,1]\times[-1.5,1.5]\).
- Resolución de la malla: \(2048\times2048\).
- Número máximo de iteraciones: \(N_{\max}=500\).
- Escalas de conteo: \(4,8,16,32,64,128,256\) píxeles.

**Procedimiento:**

1. Construir una malla de puntos complejos \(c=x+iy\) sobre el dominio establecido.
2. Inicializar \(z_0=0\) para cada punto de la malla.
3. Aplicar iterativamente la relación
   \[
   z_{n+1}=z_n^2+c.
   \]
4. Evaluar el criterio de escape \(|z_n|>2\), hasta alcanzar el número máximo de iteraciones.
5. Construir una máscara que identifique los puntos que no escaparon durante las iteraciones establecidas.
6. Identificar la frontera de la aproximación mediante la comparación de cada punto con sus ocho vecinos.
7. Para cada escala seleccionada, dividir la malla en cajas cuadradas.
8. Contar las cajas que contienen al menos un punto de la frontera y obtener \(N(\varepsilon)\).
9. Calcular los valores
   \[
   x=\log(1/\varepsilon),\qquad y=\log N(\varepsilon).
   \]
10. Aplicar el método de mínimos cuadrados para ajustar una recta:
    \[
    y=mx+b.
    \]
11. Obtener la pendiente \(m\), el intercepto \(b\) y el coeficiente de determinación \(R^2\).
12. Representar gráficamente los resultados del conteo de cajas y el ajuste lineal.

**Salida:**

- Aproximación computacional del conjunto de Mandelbrot.
- Representación de la frontera aproximada.
- Conteo de cajas para las escalas seleccionadas.
- Estimación numérica de la dimensión de caja mediante la pendiente del ajuste lineal.
