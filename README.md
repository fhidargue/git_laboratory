## Caso 3
```{r}
library(mosaicData)
```



## Caso 4
### Hipótesis

$H_0:$ El tipo de delito es independiente a quien comete el acto.

$H_1:$ Hay una relación entre el tipo de delito y quien lo comete.

Dado que es una prueba de independencia, se debe realizar una prueba de cola derecha.

### Prueba
```{r}
x.square.crimenes <- chisq.test(matrix(c(12,379,727,39,106,642),3,2), FALSE)
x.square.crimenes
```
Se tiene los siguientes resultados:

* Grado de libertad: $gl = (columnas -1)*(filas -1 ) = (3-1)*(2-1) = 2$
* $X_{obs}^2 = 119.33$

El $X_{obs}^2$ obtenido si es comparado al $X_c^2$($X_c^2$ = $X_{0.95,2}^2$ = 5.99146) es mucho mayor a este, esta gran diferencia viene de los pocos grados de libertad de que depende la funcion de distribución Chi-cuadrado.

### Conclusion
Como el valor p (indicado por p-value) < $2.2e-16$ y $a = 0.05$ => p < $a$ y  que $X_{obs}^2 > X_c^2$, se puede rechazar $H_0$.  
Por lo tanto se puede considerar que hay una relación entre quien comete el delito y que tipo de delito es cometido.


## Caso 5
### Hipótesis

$H_0:$ La fuerza de impacto en g's no varia según el tipo de auto.

$H_1:$ La fuerza de impacto en g's varia según el tipo de auto.

Dado que es una prueba de tipo ANOVA, se debe realizar una prueba de cola derecha.

### Prueba
```{r}
datos <- read.csv("D:/autos.csv", sep = ";")
anova.g.autos <- aov(g ~ tipo_auto, data = datos)
anova.g.autos
summary(anova.g.autos)
```


```{r}
TukeyHSD(anova.g.autos)
```



### Conclusion
Como el valor p (indicado por Pr(>F) de la prueba aov) es igual a 0.0445 y $a = 0.05$ => p < $a$ se puede rechazar $H_0$.  
Por lo tanto se puede considerar que hay una diferencia entre la furza de impacto que sufre un conductor dependiendo del tipo de automovil. Gracias a la pruba Tukey se puede observar que los autos grandes (G) son los que ejercen menor fuerza de desaceleración de e los tres tipos, ya que en el campo diff se muestra que hay una diferencia negativa entre este tipo de auto y las fuerzas de desaceleración en autos compactos (C) y una diferencia positiva cuando se saca la diferencia entre los autos medianos (M) y este tipo de autos. Además, los autos compactos son los que ejercen mayor cantidad de g's, ya que en la diferencia entre los autos medianos (M) y este tipo de auto la diferencia es negativa sugiriendo que tiene en promedio las mayores fuerzas de desaceleración al maniquí de pruba.

