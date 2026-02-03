

Langage d'automatisation :

- Python (pas besoin d'être compilé)
- PowerShell (pas besoin d'être compilé)
- Bash (pas besoin d'être compilé)
- vba
- JavaScript (besoin d'être compilé)
- C (besoin d'être compilé)


## Variables, constantes et types de données

Ce notebook présente les **variables**, **constantes** et **types de données** fondamentaux en Python : chaînes, entiers, flottants, booléens, tuples, dictionnaires, ensembles et listes. Chaque type est accompagné d'exemples pratiques et de démonstrations exécutables.

## Variables et constantes

Une **variable** est un espace mémoire qui stocke une valeur. Elle peut changer au cours du programme. Une **constante** est une variable que l'on décide de **ne pas modifier** après son initialisation (même si Python ne l'interdit pas techniquement). Par convention, les constantes sont écrites **en majuscules**.

## Les types de données de base

Python gère automatiquement le type des variables (typage dynamique). On peut utiliser la fonction `type()` pour connaître le type d'une variable.

## Les chaînes de caractères (`str`)

Les chaînes permettent de manipuler du texte. On peut les délimiter par des guillemets simples ' ou doubles ". Elles supportent la concaténation, le slicing et diverses méthodes utiles.

## Les booléens (`bool`)

Les valeurs booléennes ne peuvent être que `True` ou `False`. Elles sont souvent le résultat d'une comparaison logique.

## Les tuples (`tuple`)

Un **tuple** est une **collection ordonnée et immuable**. Cela signifie que **l’ordre des éléments est conservé**, mais qu’**on ne peut pas modifier son contenu après sa création** (pas d’ajout, de suppression ou de remplacement d’élément). Un tuple s’écrit entre **parenthèses `()`**, et ses éléments peuvent être de **types variés** : entiers, chaînes, listes, dictionnaires, etc. **Caractéristiques principales :**

- Ordonné → on peut accéder aux éléments par leur **index** (`tuple[0]`, `tuple[1]`, …)
- Immuable → on **ne peut pas** changer les éléments une fois le tuple créé
- Peut contenir **des doublons** (contrairement aux `set`)

**Utilité des tuples :**

- Stocker des **valeurs fixes** qui ne doivent pas changer (ex. coordonnées GPS, dimensions, constantes).
- Utiliser comme **clé de dictionnaire** (car immuables).
- Retourner **plusieurs valeurs** depuis une fonction (Python renvoie naturellement un tuple).

## Les listes (`list`)

Une liste est une **collection ordonnée et modifiable**. Elle est très utilisée pour stocker plusieurs valeurs dans un seul objet. Les éléments sont placés entre crochets [].

## Les ensembles (`set`)

Un ensemble est une **collection non ordonnée et sans doublons**. Il est pratique pour les opérations d'ensemble : union, intersection, différence.


## Les dictionnaires (`dict`)

Un dictionnaire stocke des **paires clé-valeur**. Les clés doivent être uniques et servent à accéder rapidement aux valeurs associées. Un dictionnaire peut contenir **d'autres dictionnaires**. C’est très utile pour représenter des structures de données complexes (par exemple : plusieurs personnes, produits, élèves…).

## Conversion entre types

Python permet de convertir les types avec les fonctions :

- `int()` : pour convertir une donnée en nombre entier
- `float()` : pour convertir une donnée en nombre à virgule flottante
- `str()` : pour convertir une donnée en chaîne de caractères
- `list()` : pour convertir une donnée en une liste
- `tuple()` : pour convertir une donnée (comme une liste par exemple), en tuple
- `set()` : pour convertir une donnée (comme une liste par exemple) en set

# Les structures conditionnelles
    
    Ce notebook couvre en profondeur les **conditions** en Python : opérateurs de comparaison, booléens, `if / elif / else`, opérateurs logiques, _truthiness_, expressions conditionnelles (ternaires), imbrication, et les pièges fréquents.
    
    
    1. Booléens et opérateurs de comparaison
    
    ### Définition
    
    Un booléen (ou valeur booléenne) est un type de donnée logique qui ne peut prendre que deux valeurs possibles :
    
    -  ![👉](https://canary.discord.com/assets/070ce105e9621145.svg) `True` (vrai)
    -  ![👉](https://canary.discord.com/assets/070ce105e9621145.svg) `False` (faux)
    
    Ce type sert à exprimer une condition logique, un état ou le résultat d’une comparaison. **Opérateurs de comparaison courants :**
    
    - `==` égalité
    - `!=` différence
    - `<`, `<=`, `>`, `>=`
    - `in` (appartenance), `not in`
    
    Les comparaisons **retournent un booléen**.
    
2. ## 
    
    2. La structure `if / elif / else`
    
    Syntaxe :
    
    `if condition_1:    bloc_1elif condition_2:    bloc_2else:    bloc_sinons`
    
    Notez bien l'utilisation des ":" à la fin des lignes précédent les blocs. Les blocs, eux, sont déterminés par **l'indentation**. Dès qu'une condition est vraie, son bloc s'exécute et **les autres ne sont pas évaluées**. Les conditions `elif` et `else` sont optionnelles. Vous pouvez avoir uniquement un `if`. ![⚠️](https://canary.discord.com/assets/fb6fd920c79bd504.svg) **Attention** : un `elif` ou un `else` ne peuvent pas être utilisés sans `if` !
    
    
    3. Opérateurs logiques : `and`, `or`, `not`
    
    - `A and B` est vrai si **A ET B** sont vrais.
    - `A or B` est vrai si **au moins l'un** des deux est vrai.
    - `not A` inverse la vérité de `A`.
    
    Ces opérateurs **sont à court-circuit** :
    
    - Avec `and`, si `A` est faux, Python **n'évalue pas** `B`.
    - Avec `or`, si `A` est vrai, Python **n'évalue pas** `B`.
    
    
    4. Truthiness (valeurs évaluées comme vrai/faux)
    
    La **truthiness** (ou _valeur de vérité implicite_) désigne la **façon dont Python évalue une valeur comme "vraie" ou "fausse"**, même si ce n'est **pas un booléen explicite** (`True` ou `False`). Autrement dit, **toute valeur en Python peut être interprétée comme vraie ou fausse** lorsqu'elle est utilisée dans un contexte logique (par exemple dans un `if`). **Règle générale :**
    
    -  ![✅](https://canary.discord.com/assets/43b7ead1fb91b731.svg) **Valeurs considérées comme vraies ("truthy")** → Presque tout ce qui **n'est pas vide ou nul** : `1`, `"bonjour"`, `[1, 2]`, `{ 'clé': 'valeur' }`, etc.
    -  ![❌](https://canary.discord.com/assets/4f584fe7b12fcf02.svg) **Valeurs considérées comme fausses ("falsy")** → Les valeurs **vides ou nulles** : `0`, `0.0`, `''`, `[]`, `{}`, `set()`, `None`, `False`
    
     **![🧠](https://canary.discord.com/assets/8d4731884ff0e2cc.svg) À retenir :**
    
    > La **truthiness** est la capacité de Python à **interpréter automatiquement une valeur comme vraie ou fausse** dans un test logique, sans exiger qu'elle soit explicitement `True` ou `False`.

## Expression conditionnelle (ternaire)
    
    Forme compacte pour affecter une valeur selon une condition :
    
    `valeur = expression_si_vrai if condition else expression_si_faux`
    
    À utiliser pour des cas simples (lisibilité avant tout).
    
##  Imbrication vs. chaîne de `elif`
    
    Évitez les imbrications trop profondes. Préférez une **chaîne de `elif`** claire.
    
## Bonnes pratiques et pièges fréquents
    
    8. **Utiliser == pour comparer des valeurs**.
    9. **Attention à l'assignation vs. comparaison** : = assigne, == compare.
    10. **Comparer des types compatibles** (éviter 3 < '3').
    11. **Lisibilité** : préférez des conditions nommées (variables intermédiaires) si l'expression devient longue.
    12. **Chaînage de comparaisons** : Python permet 18 <= age < 65.
    13. **Court-circuit** : utile pour éviter des erreurs (ex. vérifier obj non nul avant obj.attr).
    14. **Ne pas abuser des ternaires** : au-delà d'un cas simple, préférez if.
    
2. ## 
    
## Mise en pratique
    
    ### Exercice 1 — Pair / impair
    
    --- Écrire un programme qui lit un entier `n` (déjà fourni) et affiche `pair` si `n` est pair, sinon `impair`. ![🧠](https://canary.discord.com/assets/8d4731884ff0e2cc.svg) **Pour aller plus loin :** vous pouvez aller récupérer le nombre avec une saisie utilisateur (`input()`). N'oubliez pas de vérifier les types. n = 8   if n % 2 == 0:   print("Pair") else:   print("Impair")
    
 Exercice 2 — Tarif réduit
    
    --- On applique un **tarif réduit** si l'utilisateur a **moins de 26 ans** **ou** est **bénéficiaire du RSA**. Sinon, tarif normal. Afficher `reduit` ou `normal`. age = 78 beneficiaire_rsa = False if age < 26 or beneficiaire_rsa:   print("Réduit") else:   print("Normal")
    
 Exercice 3 — Catégorisation de notes
    
    --- À partir d'une `note` sur 20, afficher :
    
    - `<10` : `ajourné`
    - `10 à 11.99` : `passable`
    - `12 à 13.99` : `assez bien`
    - `14 à 15.99` : `bien`
    - `>= 16` : `très bien`
    
    note = float(input("Note /")) if note < 10:   print("ajourné") elif note < 12:   print("passable") elif note < 14:   print("assez bien") elif note < 16:   print("bien") elif note >= 16:   print("tres bien")
    
Exercice 4 — Login très simplifié
    
    --- Demandez (via les variables déjà posées) `username` et `password`. Affichez `OK` si les deux correspondent aux références, sinon `KO`. **Références :** `ref_user = 'admin'`, `ref_pwd = '1234'` ref_user = 'admin' ref_pwd = '1234' username = 'admin'   # simule une saisie password = '1234'    # simule une saisie if username == ref_user and password == ref_pwd:   print("OK") else:   print("KO")
    


23Exercice 5 — Sécurité accès mineurs
    
    --- Affichez `autorisé` si l'utilisateur a 18 ans **ou plus**, sinon `refusé`. Faites-le en utilisant une expression conditionnelle (**ternaire**) age = 45 if age >= 18:   print("autorisé") else:   print("refusé")
