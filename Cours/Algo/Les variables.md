# Variables :

Un nom (pas de caractères spéciaux, pas d'espace, pas commencer par un chiffre) et une valeur (différents types de valeurs)

Prénom (affectation, initialisation) = "John" (chaine de caractère)

# Exemple de noms de variables :

DateJour = "23-09-2024"
anneeNaissance = 1988

# Convention de Nommage

camelCase

LowerCamelCase = camelCase
UpperCamelCase = CamelCase

snake_case = underscore

kebab-case (nom de fichier ou URL)

# Types de donnée

### Entiers (integer/int)
-∞ à +∞

### Décimaux
(float)

-∞ à +∞
à virgule 
3.4

### Chaîne de caractères

(string / str)

"entre guillemets"

### Booléen
(Booloan/ Bool)
True/False 
1/0

### Les opérations

Entiers/Décimaux :
- + addition
- - soustraction
- * multiplication
- // division entière 
- / division = résultat décimal
- ** puissance

#### String
- + concaténation
- "Salut " + "Ca va"

* * Multiplication en Python uniquement
"A" * 4 = "AAAA"

### Bool

And =            
Or =                                          Opération Logiques
Not =


### Algèbre de Boole 



| a   | b   | a ET b |
| --- | --- | ------ |
| F   | F   | F      |
| F   | V   | F      |
| V   | F   | F      |
| V   | V   | V      |

| a   | b   | a OU b |     |     | a   | NON A |
| --- | --- | ------ | --- | --- | --- | ----- |
| F   | F   | F      |     |     | F   | V     |
| F   | V   | V      |     |     | V   | F     |
| V   | F   | V      |     |     |     |       |
| V   | V   | V      |     |     |     |       |


| a   | b   | a ET b |
| --- | --- | ------ |
| 0   | 0   | 0 F    |
| 0   | 0   | 0 F    |
| 1   | 0   | 0 F    |
| 1   | 1   | 1 V    |

Lire de gauche à droite


|               | A   | B   | C   |     |
| ------------- | --- | --- | --- | --- |
| a = 7         | 7   | X   | X   |     |
| b = 5         | 7   | 5   | X   |     |
| c = 2         | 7   | 5   | 2   |     |
| a = b * c     | 10  | 5   | 2   |     |
| c = a+a       | 10  | 5   | 20  |     |
| b = c*3       | 10  | 40  | 20  |     |
| a = a + b + c | 70  | 40  | 20  |     |
| c = a - b + c | 70  | 40  | 50  |     |

|               | A   | B   | C   |     |
| ------------- | --- | --- | --- | --- |
| a = 2         | 7   | X   | X   |     |
| b = 3         | 7   | 5   | X   |     |
| c = 4         | 7   | 5   | 2   |     |
| c = a + 1     | 10  | 5   | 2   |     |
| c = a+a       | 10  | 5   | 20  |     |
| b = c*3       | 10  | 40  | 20  |     |
| a = a + b + c | 70  | 40  | 20  |     |
| c = a - b + c | 70  | 40  | 50  |     |

nom = input("Quel est votre nom : ")

print("Salut", nom)

