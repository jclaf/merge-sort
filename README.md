# Merge Sort Algorithm

- **Ce code implémente le tri par fusion (merge sort), un algorithme de tri efficace et stable basé sur la récursion et la fusion de sous-tableaux triés.**
- **Il trie le tableau donné en place, sans retourner de nouvelle liste.**
- **C’est un excellent choix pour trier de grands ensembles de données, surtout si la stabilité du tri est importante.**
---

## Description du Code

### 1. Fonction `merge_sort(array)`

#### a. **Cas de base**

```python
if len(array) <= 1:
    return
```
- **Si le tableau a 0 ou 1 élément, il est déjà trié** : on ne fait rien.

#### b. **Découpage du tableau**

```python
middle_point = len(array) // 2
left_part = array[:middle_point]
right_part = array[middle_point:]
```
- **On coupe le tableau en deux** :
    - `left_part` : de l’indice 0 à `middle_point - 1`
    - `right_part` : de `middle_point` à la fin

#### c. **Tri récursif des deux moitiés**

```python
merge_sort(left_part)
merge_sort(right_part)
```
- **On trie récursivement chaque moitié** (c’est là que la récursion intervient).

#### d. **Fusion des deux moitiés triées**

```python
left_array_index = 0
right_array_index = 0
sorted_index = 0

while left_array_index < len(left_part) and right_array_index < len(right_part):
    if left_part[left_array_index] < right_part[right_array_index]:
        array[sorted_index] = left_part[left_array_index]
        left_array_index += 1
    else:
        array[sorted_index] = right_part[right_array_index]
        right_array_index += 1
    sorted_index += 1
```
- **On compare les éléments des deux moitiés** :
    - On place le plus petit dans le tableau original.
    - On avance dans la moitié d’où vient l’élément choisi.
    - On continue jusqu’à ce qu’une des deux moitiés soit épuisée.

#### e. **Ajout des éléments restants**

```python
while left_array_index < len(left_part):
    array[sorted_index] = left_part[left_array_index]
    left_array_index += 1
    sorted_index += 1

while right_array_index < len(right_part):
    array[sorted_index] = right_part[right_array_index]
    right_array_index += 1
    sorted_index += 1
```
- **On ajoute les éléments restants** (s’il en reste dans l’une des deux moitiés).

---

### 2. Exemple d’utilisation

```python
if __name__ == '__main__':
    numbers = [4, 10, 6, 14, 2, 1, 8, 5]
    print('Unsorted array: ')
    print(numbers)
    merge_sort(numbers)
```
- **On affiche le tableau non trié, puis on applique le tri par fusion.**
- Après l’appel, `numbers` sera trié en place.

---

## Algorithme Utilisé

### **Tri par fusion (Merge Sort)**

#### **Principe**
- **Diviser** : On coupe le tableau en deux moitiés.
- **Récursivement trier** chaque moitié.
- **Fusionner** les deux moitiés triées en un seul tableau trié.

#### **Caractéristiques**
- **Complexité temporelle** : O(n log n) dans tous les cas (meilleur, moyen, pire).
- **Complexité spatiale** : O(n) (car il faut des tableaux temporaires pour la fusion).
- **Stable** : Oui (conserve l’ordre des éléments égaux).
- **Non-in-place** dans la version classique, mais ici le tri se fait en place dans le tableau original (grâce à la réécriture des éléments).

#### **Avantages**
- Très efficace pour les grands tableaux.
- Prévisible (toujours O(n log n)).

#### **Limites**
- Utilise de la mémoire supplémentaire pour les sous-tableaux.
- Moins efficace que le tri rapide (quick sort) pour de petits tableaux.

---
