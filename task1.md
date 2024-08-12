## Expected SARSA

Expected SARSA es una variante del algoritmo SARSA (State-Action-Reward-State-Action) para aprendizaje por refuerzo.

- Diferencias con SARSA:

La principal diferencia es que Expected SARSA utiliza el valor esperado de la acción siguiente en lugar de muestrear una acción específica como lo hace SARSA.
En SARSA, se actualiza el valor Q(s,a) usando la recompensa inmediata y el valor Q de la siguiente acción seleccionada:
Q(s,a) ← Q(s,a) + α[r + γQ(s',a') - Q(s,a)]
En Expected SARSA, se usa el valor esperado de las acciones posibles en el siguiente estado:
Q(s,a) ← Q(s,a) + α[r + γΣπ(a'|s')Q(s',a') - Q(s,a)]
Donde π(a'|s') es la probabilidad de tomar la acción a' en el estado s' según la política actual.

- Utilidad de las modificaciones:

Reduce la varianza en las actualizaciones, lo que puede llevar a un aprendizaje más estable.
Puede converger más rápidamente que SARSA en algunos entornos.
Es más robusto frente a políticas de exploración no óptimas durante el entrenamiento.


## n-step TD

n-step TD (Temporal Difference) es una generalización de los métodos TD que considera múltiples pasos futuros para las actualizaciones.

-  Diferencias con TD(0):

TD(0) solo considera la recompensa inmediata y la estimación del siguiente estado. n-step TD considera n pasos hacia el futuro antes de hacer una actualización.

-  Utilidad de esta modificación:

Permite un balance entre el sesgo y la varianza en el aprendizaje.
Puede acelerar el aprendizaje al propagar la información más rápidamente.

Combina aspectos de TD(0) y Monte Carlo, permitiendo ajustar el compromiso entre ambos.

-  Objetivo utilizado:

El objetivo en n-step TD es la suma de las recompensas sobre n pasos más el valor estimado del estado n pasos adelante:
Gt:t+n = Rt+1 + γRt+2 + ... + γ^(n-1)Rt+n + γ^n V(St+n)

## Diferencia entre SARSA y Q-learning

Las principales diferencias son:

Política de actualización:
SARSA es on-policy, lo que significa que aprende los valores Q para la política que está siguiendo actualmente.
Q-learning es off-policy, aprendiendo la política óptima independientemente de la política de exploración utilizada.

Fórmula de actualización:
SARSA: Q(s,a) ← Q(s,a) + α[r + γQ(s',a') - Q(s,a)]
Q-learning: Q(s,a) ← Q(s,a) + α[r + γ max_a' Q(s',a') - Q(s,a)]

Convergencia:
Q-learning converge a la política óptima si se explora suficientemente, incluso con una política de exploración subóptima.
SARSA converge a la política óptima solo si la exploración disminuye con el tiempo.

Comportamiento:
SARSA tiende a ser más conservador, considerando el riesgo asociado con la exploración.
Q-learning es más agresivo, siempre apuntando a la acción óptima.