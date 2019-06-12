---
title: Opérateurs C#
ms.date: 04/30/2019
f1_keywords:
- cs.operators
helpviewer_keywords:
- boolean operators [C#]
- expressions [C#], operators
- logical operators [C#]
- operators [C#]
- Visual C#, operators
- indirection operators [C#]
- assignment operators [C#]
- shift operators [C#]
- relational operators [C#]
- bitwise operators [C#]
- address operators [C#]
- keywords [C#], operators
- arithmetic operators [C#]
ms.assetid: 0301e31f-22ad-49af-ac3c-d5eae7f0ac43
ms.openlocfilehash: c6b83779a630c6d797968d79635793e229751f93
ms.sourcegitcommit: 34593b4d0be779699d38a9949d6aec11561657ec
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/11/2019
ms.locfileid: "66833271"
---
# <a name="c-operators"></a>Opérateurs C#

C# fournit plusieurs opérateurs prédéfinis pris en charge par les types intégrés. Par exemple, les [opérateurs arithmétiques](arithmetic-operators.md) effectuent des opérations arithmétiques avec des opérandes de types numériques intégrés et les [opérateurs logiques booléens](boolean-logical-operators.md) effectuent des opérations logiques avec les opérandes [bool](../keywords/bool.md).

Un type défini par l’utilisateur peut surcharger certains opérateurs pour définir le comportement correspondant des opérandes de ce type. Pour plus d’informations, consultez l’article sur le mot clé [opérateur](../keywords/operator.md).

Les sections suivantes listent les opérateurs C# de la priorité la plus élevée à la plus basse. Les opérateurs inclus dans chaque section partagent le même niveau de priorité.

## <a name="primary-operators"></a>Opérateurs principaux

Ce sont les opérateurs dont la priorité est la plus élevée.

[x.y](member-access-operators.md#member-access-operator-) : accès au membre.

[x?.y](member-access-operators.md#null-conditional-operators--and-) : accès au membre conditionnel Null. Retourne `null` si l’opérande de gauche prend la valeur `null`.

[x?[y]](member-access-operators.md#null-conditional-operators--and-) : accès à l’indexeur de type ou d’élément de tableau conditionnel Null. Retourne `null` si l’opérande de gauche prend la valeur `null`.

[f(x)](member-access-operators.md#invocation-operator-) : appel de méthode ou appel de délégué.

[un&#91;x&#93;](member-access-operators.md#indexer-operator-) : accès à l’indexeur de type ou d’élément de tableau.

[x++](arithmetic-operators.md#increment-operator-) : incrément suffixé. Retourne la valeur de x et met à jour l'emplacement de stockage avec la valeur de x augmentée de un (ajoute généralement l'entier 1).

[x--](arithmetic-operators.md#decrement-operator---) : décrément suffixé. Retourne la valeur de x et met à jour l'emplacement de stockage avec la valeur de x diminuée de un (soustrait généralement l'entier 1).

[new](../keywords/new-operator.md) : instanciation de type.

[typeof](../keywords/typeof.md) : retourne l’objet <xref:System.Type> qui représente l’opérande.

[checked](../keywords/checked.md) : active le contrôle de dépassement de capacité pour les opérations sur les entiers.

[unchecked](../keywords/unchecked.md) : désactive le contrôle de dépassement de capacité pour les opérations sur les entiers. Il s'agit du comportement de compilateur par défaut.

[default(T)](../../programming-guide/statements-expressions-operators/default-value-expressions.md) – produit la valeur par défaut du type T.

[nameof](../keywords/nameof.md) : obtient le nom simple (non qualifié) d’une variable, d’un type ou d’un membre sous forme de chaîne constante.

[delegate](../../programming-guide/statements-expressions-operators/anonymous-methods.md) : déclare et retourne une instance de délégué.

[sizeof](../keywords/sizeof.md) : retourne la taille en octets de l’opérande du type.

[stackalloc](stackalloc.md) : alloue un bloc de mémoire dans la pile.

[->](pointer-related-operators.md#pointer-member-access-operator--) : indirection de pointeur associé à l’accès au membre.

## <a name="unary-operators"></a>Les opérateurs unaires.

Ces opérateurs ont une priorité supérieure à celle de la section suivante et une priorité inférieure à celle de la section précédente.

[+x](addition-operator.md) : retourne la valeur de x.

[-x](subtraction-operator.md) : négation numérique.

[\!x](boolean-logical-operators.md#logical-negation-operator-) : négation logique.

[~x](bitwise-and-shift-operators.md#bitwise-complement-operator-) : complément au niveau du bit.

[++x](arithmetic-operators.md#increment-operator-) : incrément préfixé. Retourne la valeur de x après avoir mis à jour l'emplacement de stockage avec la valeur de x augmentée de un (ajoute généralement l'entier 1).

[--x](arithmetic-operators.md#decrement-operator---) : décrément préfixé. Retourne la valeur de x après avoir mis à jour l’emplacement de stockage avec la valeur de x diminuée d’une unité (soustrait généralement l’entier 1).

[(T)x](invocation-operator.md) : cast de type.

[await](../keywords/await.md) : attend un `Task`.

[&x](pointer-related-operators.md#address-of-operator-) – adresse d’une variable.

[*x](pointer-related-operators.md#pointer-indirection-operator-) – indirection de pointeur ou déréférencement.

[Opérateur true ](true-false-operators.md) : retourne la valeur [bool](../keywords/bool.md) `true` pour indiquer qu’un opérande est true.

[Opérateur false](true-false-operators.md) : retourne la valeur [bool](../keywords/bool.md) `true` pour indiquer qu’un opérande est false.

## <a name="multiplicative-operators"></a>Opérateurs multiplicatifs

Ces opérateurs ont une priorité supérieure à celle de la section suivante et une priorité inférieure à celle de la section précédente.

[x * y](arithmetic-operators.md#multiplication-operator-) : multiplication.

[x / y](arithmetic-operators.md#division-operator-) : division. Si les opérandes sont des entiers, le résultat est un entier tronqué vers zéro (par exemple, `-7 / 2 is -3`).

[x % y](arithmetic-operators.md#remainder-operator-) : reste. Si les opérandes sont des entiers, cet opérateur renvoie le reste de la division de x par y.  Si `q = x / y` et `r = x % y`, alors `x = q * y + r`.

## <a name="additive-operators"></a>Opérateurs additifs

Ces opérateurs ont une priorité supérieure à celle de la section suivante et une priorité inférieure à celle de la section précédente.

[x + y](arithmetic-operators.md#addition-operator-) : addition.

[x – y](arithmetic-operators.md#subtraction-operator--) : soustraction.

## <a name="shift-operators"></a>Opérateurs de décalage

Ces opérateurs ont une priorité supérieure à celle de la section suivante et une priorité inférieure à celle de la section précédente.

[x <\<  y](bitwise-and-shift-operators.md#left-shift-operator-) : décalage des bits vers la gauche et remplissage avec zéro à droite.

[x >> y](bitwise-and-shift-operators.md#right-shift-operator-) : décalage des bits vers la droite. Si l'opérande de gauche est `int` ou `long`, alors les bits de gauche sont remplis avec le bit de signe. Si l'opérande de gauche est `uint` ou `ulong`, alors les bits de gauche sont remplis avec zéro.

## <a name="relational-and-type-testing-operators"></a>Opérateurs relationnels et de test de type

Ces opérateurs ont une priorité supérieure à celle de la section suivante et une priorité inférieure à celle de la section précédente.

[x \< y](comparison-operators.md#less-than-operator-) : inférieur à (true si x est inférieur à y).

[x > y](comparison-operators.md#greater-than-operator-) : supérieur à (true si x est supérieur à y).

[x \<= y](comparison-operators.md#less-than-or-equal-operator-) : supérieur ou égal à.

[x >= y](comparison-operators.md#greater-than-or-equal-operator-) : supérieur ou égal à.

[is](../keywords/is.md) : compatibilité du type. Retourne true si l’opérande de gauche évalué peut être converti en type spécifié dans l’opérande de droite (type statique).

[as](../keywords/as.md) : conversion de type. Retourne l'opérande de gauche converti en type spécifié par l'opérande de droite (type statique), mais `as` retourne `null` où `(T)x` lèverait une exception.

## <a name="equality-operators"></a>Opérateurs d'égalité

Ces opérateurs ont une priorité supérieure à celle de la section suivante et une priorité inférieure à celle de la section précédente.

[x == y](equality-operators.md#equality-operator-) : égalité. Par défaut, pour les types de référence autres que `string`, cet opérateur retourne l'égalité de référence (test d'identité). Toutefois, des types peuvent surcharger `==`, donc si votre objectif est de tester l'identité, il est préférable d'utiliser la méthode `ReferenceEquals` sur `object`.

[x != y](equality-operators.md#inequality-operator-) : différent. Consultez le commentaire sur `==`. Si un type surcharge `==`, alors il doit surcharger `!=`.

## <a name="logical-and-operator"></a>Opérateur AND logique

Cet opérateur a une priorité supérieure à celle de la section suivante et une priorité inférieure à celle de la section précédente.

`x & y` – [AND logique](boolean-logical-operators.md#logical-and-operator-) dans le cas des opérandes `bool` ou [AND logique au niveau du bit](bitwise-and-shift-operators.md#logical-and-operator-) dans le cas des opérandes de type intégral.

## <a name="logical-xor-operator"></a>Opérateur XOR logique

Cet opérateur a une priorité supérieure à celle de la section suivante et une priorité inférieure à celle de la section précédente.

`x ^ y` – [XOR logique](boolean-logical-operators.md#logical-exclusive-or-operator-) dans le cas des opérandes `bool` ou [XOR logique au niveau du bit](bitwise-and-shift-operators.md#logical-exclusive-or-operator-) dans le cas des opérandes de type intégral.

## <a name="logical-or-operator"></a>Opérateur OU logique

Cet opérateur a une priorité supérieure à celle de la section suivante et une priorité inférieure à celle de la section précédente.

`x | y` – [OR logique](boolean-logical-operators.md#logical-or-operator-) dans le cas des opérandes `bool` ou [OR logique au niveau du bit](bitwise-and-shift-operators.md#logical-or-operator-) dans le cas des opérandes de type intégral.

## <a name="conditional-and-operator"></a>Opérateur AND conditionnel

Cet opérateur a une priorité supérieure à celle de la section suivante et une priorité inférieure à celle de la section précédente.

[x && y](boolean-logical-operators.md#conditional-logical-and-operator-) : ET logique. Si le premier opérande prend la valeur false, C# n’évalue pas le second opérande.

## <a name="conditional-or-operator"></a>Opérateur OR conditionnel

Cet opérateur a une priorité supérieure à celle de la section suivante et une priorité inférieure à celle de la section précédente.

[x &#124;&#124; y](boolean-logical-operators.md#conditional-logical-or-operator-) : OU logique. Si le premier opérande prend la valeur true, C# n’évalue pas le second opérande.

## <a name="null-coalescing-operator"></a>Opérateur de fusion de Null

Cet opérateur a une priorité supérieure à celle de la section suivante et une priorité inférieure à celle de la section précédente.

[x ?? y](null-coalescing-operator.md) : retourne `x` si non `null` ; dans le cas contraire, retourne `y`.

## <a name="conditional-operator"></a>Opérateur conditionnel

Cet opérateur a une priorité supérieure à celle de la section suivante et une priorité inférieure à celle de la section précédente.

[t ? x : y](conditional-operator.md) : si le test `t` prend la valeur true, alors évalue et retourne `x` ; sinon, évalue et retourne `y`.

## <a name="assignment-and-lambda-operators"></a>Opérateurs d’affectation et lambda

Ces opérateurs ont une priorité supérieure à celle de la section suivante et une priorité inférieure à celle de la section précédente.

[x = y](assignment-operator.md) : affectation.

[x += y](arithmetic-operators.md#compound-assignment) : incrément. Additionne la valeur de `y` à la valeur de `x`, stocke le résultat dans `x` et retourne la nouvelle valeur. Si `x` désigne un [événement](../keywords/event.md), `y` doit être une méthode appropriée que C# ajoute en tant que gestionnaire d’événements.

[x -= y](arithmetic-operators.md#compound-assignment) : décrément. Soustrait la valeur de `y` de la valeur de `x`, stocke le résultat dans `x` et retourne la nouvelle valeur. Si `x` désigne un [événement](../keywords/event.md), `y` doit être une méthode appropriée que C# supprime en tant que gestionnaire d’événements.

[x *= y](arithmetic-operators.md#compound-assignment) : affectation de multiplication. Multiplie la valeur de `y` par la valeur de `x`, stocke le résultat dans `x` et retourne la nouvelle valeur.

[x /= y](arithmetic-operators.md#compound-assignment) : affectation de division. Divise la valeur de `x` par la valeur de `y`, stocke le résultat dans `x` et retourne la nouvelle valeur.

[x %= y](arithmetic-operators.md#compound-assignment) : assignation de reste. Divise la valeur de `x` par la valeur de `y`, stocke le reste dans `x` et retourne la nouvelle valeur.

[x &= y](boolean-logical-operators.md#compound-assignment) : affectation ET. Assigne l'opérateur AND à la valeur de `y` et la valeur de `x`, stocke le résultat dans `x` et retourne la nouvelle valeur.

[x &#124;= y](boolean-logical-operators.md#compound-assignment) : affectation OU. Assigne l'opérateur OR à la valeur de `y` et la valeur de `x`, stocke le résultat dans `x` et retourne la nouvelle valeur.

[x ^= y](boolean-logical-operators.md#compound-assignment) : affectation XOR. Assigne l'opérateur XOR à la valeur de `y` et la valeur de `x`, stocke le résultat dans `x` et retourne la nouvelle valeur.

[x <<= y](bitwise-and-shift-operators.md#compound-assignment) : affectation de décalage vers la gauche. Décale la valeur de `x` vers la gauche de `y` places, stocke le résultat dans `x` et retourne la nouvelle valeur.

[x >>= y](bitwise-and-shift-operators.md#compound-assignment) : affectation de décalage vers la droite. Décale la valeur de `x` vers la droite de `y` places, stocke le résultat dans `x` et retourne la nouvelle valeur.

[=>](lambda-operator.md) : déclaration lambda.

## <a name="see-also"></a>Voir aussi

- [Référence C#](../index.md)
- [Guide de programmation C#](../../programming-guide/index.md)
- [C#](../../index.md)
- [Opérateurs surchargeables](../../programming-guide/statements-expressions-operators/overloadable-operators.md)
- [Mots clés C#](../keywords/index.md)
