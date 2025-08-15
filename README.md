# IR ALÉM estou adicionando aqui porque já tinha salvo o notebook e para rodar de novo com os acréscimos demoraria muito.

## Ajuste Dinâmico do Threshold para Maximizar o F1

```python
import numpy as np
import matplotlib.pyplot as plt
from sklearn.metrics import f1_score

# Testar diferentes limiares e ver qual maximiza o F1
thresholds = np.linspace(0.1, 0.9, 9)
f1_scores = []

for t in thresholds:
    y_pred = (y_proba >= t).astype(int)
    f1_scores.append(f1_score(y_test, y_pred))

# Plotar a relação entre threshold e F1
plt.plot(thresholds, f1_scores, marker='o', color='b')
plt.title('Threshold vs F1 Score')
plt.xlabel('Threshold')
plt.ylabel('F1 Score')
plt.grid(True)
plt.show()

# Melhor threshold
best_threshold = thresholds[np.argmax(f1_scores)]
print(f"Melhor threshold: {best_threshold:.2f}")
```

## Visualização das Fraudes vs. Não Fraudes
```python
import seaborn as sns

# Plotar distribuição das classes em relação a 'Amount' (ou outra feature)
plt.figure(figsize=(10,6))
sns.histplot(df[df['Class'] == 0]['Amount'], color='blue', label='Não fraude', kde=True, stat='density', linewidth=0)
sns.histplot(df[df['Class'] == 1]['Amount'], color='red', label='Fraude', kde=True, stat='density', linewidth=0)
plt.title('Distribuição do Amount para Fraudes e Não Fraudes')
plt.xlabel('Amount')
plt.ylabel('Densidade')
plt.legend()
plt.show()
```
