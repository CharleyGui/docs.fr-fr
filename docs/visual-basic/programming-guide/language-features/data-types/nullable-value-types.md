---
title: Types valeur Nullable-Visual Basic
ms.date: 07/20/2015
f1_keywords:
- vb.Nullable
helpviewer_keywords:
- nullable types [Visual Basic]
- '? [Visual Basic]'
- types [Visual Basic], nullable
- nullable types [Visual Basic]
- data types [Visual Basic], nullable
ms.assetid: 9ac3b602-6f96-4e6d-96f7-cd4e81c468a6
ms.openlocfilehash: 1fb8f8d1657b8eab6b15858c2a6607cbde82e542
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/07/2019
ms.locfileid: "73732936"
---
# <a name="nullable-value-types-visual-basic"></a>Types valeur Nullable (Visual Basic)

Parfois, vous utilisez un type valeur qui n’a pas de valeur définie dans certaines circonstances. Par exemple, un champ dans une base de données peut être obligé de faire la distinction entre avoir une valeur assignée explicite et ne pas avoir de valeur assignée. Les types valeur peuvent être étendus pour prendre leurs valeurs normales ou une valeur null. Une telle extension est appelée un *type Nullable*.

Chaque type Nullable est construit à partir de la structure <xref:System.Nullable%601> générique. Prenons l’exemple d’une base de données qui effectue le suivi des activités liées au travail. L’exemple suivant construit un type de `Boolean` Nullable et déclare une variable de ce type. Vous pouvez écrire la déclaration de trois manières :

[!code-vb[VbVbalrNullableValue#1](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrNullableValue/VB/Class1.vb#1)]

La variable `ridesBusToWork` peut contenir une valeur de `True`, une valeur de `False`ou aucune valeur. Sa valeur par défaut initiale est aucune valeur, ce qui, dans ce cas, signifie que les informations n’ont pas encore été obtenues pour cette personne. En revanche, `False` peut signifier que les informations ont été obtenues et que la personne n’a pas la possibilité d’utiliser le bus pour fonctionner.

Vous pouvez déclarer des variables et des propriétés avec des types Nullable, et vous pouvez déclarer un tableau avec des éléments d’un type Nullable. Vous pouvez déclarer des procédures avec des types Nullable comme paramètres, et vous pouvez retourner un type Nullable à partir d’une procédure `Function`.

Vous ne pouvez pas construire un type Nullable sur un type référence, tel qu’un tableau, un `String`ou une classe. Le type sous-jacent doit être un type valeur. Pour plus d'informations, consultez [Value Types and Reference Types](value-types-and-reference-types.md).

## <a name="using-a-nullable-type-variable"></a>Utilisation d’une variable de type Nullable

Les membres les plus importants d’un type Nullable sont ses propriétés <xref:System.Nullable%601.HasValue%2A> et <xref:System.Nullable%601.Value%2A>. Pour une variable de type Nullable, <xref:System.Nullable%601.HasValue%2A> indique si la variable contient une valeur définie. Si <xref:System.Nullable%601.HasValue%2A> est `True`, vous pouvez lire la valeur à partir de <xref:System.Nullable%601.Value%2A>. Notez que les <xref:System.Nullable%601.HasValue%2A> et <xref:System.Nullable%601.Value%2A> sont des propriétés `ReadOnly`.

### <a name="default-values"></a>Valeurs par défaut

Quand vous déclarez une variable avec un type Nullable, sa propriété <xref:System.Nullable%601.HasValue%2A> a la valeur par défaut `False`. Cela signifie que, par défaut, la variable n’a pas de valeur définie, et non la valeur par défaut de son type de valeur sous-jacent. Dans l’exemple suivant, la variable `numberOfChildren` n’a aucune valeur définie, même si la valeur par défaut du type de `Integer` est 0.

[!code-vb[VbVbalrNullableValue#2](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrNullableValue/VB/Class1.vb#2)]

Une valeur null est utile pour indiquer une valeur non définie ou inconnue. Si `numberOfChildren` a été déclaré comme `Integer`, aucune valeur ne peut indiquer que les informations ne sont pas disponibles actuellement.

### <a name="storing-values"></a>Stocker des valeurs

Vous stockez une valeur dans une variable ou une propriété d’un type Nullable de la façon habituelle. L’exemple suivant affecte une valeur à la variable `numberOfChildren` déclarée dans l’exemple précédent.

[!code-vb[VbVbalrNullableValue#3](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrNullableValue/VB/Class1.vb#3)]

Si une variable ou une propriété d’un type Nullable contient une valeur définie, vous pouvez la forcer à revenir à son état initial qui n’a pas de valeur assignée. Pour ce faire, affectez à la variable ou à la propriété la valeur `Nothing`, comme le montre l’exemple suivant.

[!code-vb[VbVbalrNullableValue#4](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrNullableValue/VB/Class1.vb#4)]

> [!NOTE]
> Bien que vous puissiez assigner des `Nothing` à une variable d’un type Nullable, vous ne pouvez pas la tester pour `Nothing` à l’aide du signe égal. La comparaison qui utilise le signe égal, `someVar = Nothing`, est toujours évaluée à `Nothing`. Vous pouvez tester la propriété <xref:System.Nullable%601.HasValue%2A> de la variable pour `False`ou le tester à l’aide de l’opérateur `Is` ou `IsNot`.

### <a name="retrieving-values"></a>Récupération de valeurs

Pour récupérer la valeur d’une variable d’un type Nullable, vous devez d’abord tester sa propriété <xref:System.Nullable%601.HasValue%2A> pour confirmer qu’elle a une valeur. Si vous essayez de lire la valeur lorsque <xref:System.Nullable%601.HasValue%2A> est `False`, Visual Basic lève une exception <xref:System.InvalidOperationException>. L’exemple suivant illustre la méthode recommandée pour lire la variable `numberOfChildren` des exemples précédents.

[!code-vb[VbVbalrNullableValue#5](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrNullableValue/VB/Class1.vb#5)]

## <a name="comparing-nullable-types"></a>Comparaison des types Nullable

Lorsque la valeur null `Boolean` variables sont utilisées dans les expressions booléennes, le résultat peut être `True`, `False`ou `Nothing`. Voici la table de vérité pour `And` et `Or`. Étant donné que `b1` et `b2` ont désormais trois valeurs possibles, il existe neuf combinaisons à évaluer.

|B1|B2|B1 et B2|B1 ou B2|
|--------|--------|---------------|--------------|
|`Nothing`|`Nothing`|`Nothing`|`Nothing`|
|`Nothing`|`True`|`Nothing`|`True`|
|`Nothing`|`False`|`False`|`Nothing`|
|`True`|`Nothing`|`Nothing`|`True`|
|`True`|`True`|`True`|`True`|
|`True`|`False`|`False`|`True`|
|`False`|`Nothing`|`False`|`Nothing`|
|`False`|`True`|`False`|`True`|
|`False`|`False`|`False`|`False`|

Quand la valeur d’une variable ou d’une expression booléenne est `Nothing`, elle n’est ni `true` ni `false`. Prenons l'exemple suivant.

[!code-vb[VbVbalrNullableValue#6](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrNullableValue/VB/Class1.vb#6)]

Dans cet exemple, `b1 And b2` prend la valeur `Nothing`. Par conséquent, la clause `Else` est exécutée dans chaque instruction `If`, et la sortie est la suivante :

`Expression is not true`

`Expression is not false`

> [!NOTE]
> `AndAlso` et `OrElse`, qui utilisent l’évaluation de court-circuit, doivent évaluer leurs deux opérandes lorsque le premier est évalué à `Nothing`.

## <a name="propagation"></a>Propagation

Si l’un des opérandes d’une opération arithmétique, de comparaison, de décalage ou de type est Nullable, le résultat de l’opération est également Nullable. Si les deux opérandes ont des valeurs qui ne sont pas `Nothing`, l’opération est effectuée sur les valeurs sous-jacentes des opérandes, comme si aucun n’était un type Nullable. Dans l’exemple suivant, les variables `compare1` et `sum1` sont implicitement typées. Si vous placez le pointeur de la souris dessus, vous verrez que le compilateur déduit les types Nullable pour les deux.

[!code-vb[VbVbalrNullableValue#7](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrNullableValue/VB/Class1.vb#7)]

Si l’un des opérandes ou les deux ont la valeur `Nothing`, le résultat sera `Nothing`.

[!code-vb[VbVbalrNullableValue#8](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrNullableValue/VB/Class1.vb#8)]

## <a name="using-nullable-types-with-data"></a>Utilisation de types Nullable avec des données

Une base de données est l’un des emplacements les plus importants pour l’utilisation de types Nullable. Tous les objets de base de données ne prennent pas actuellement en charge les types Nullable, contrairement aux adaptateurs de table générés par le concepteur. Consultez [prise en charge de TableAdapter pour les types Nullable](/visualstudio/data-tools/fill-datasets-by-using-tableadapters#tableadapter-support-for-nullable-types).

## <a name="see-also"></a>Voir aussi

- <xref:System.InvalidOperationException>
- <xref:System.Nullable%601.HasValue%2A>
- [Types de données](index.md)
- [Types valeur et types référence](value-types-and-reference-types.md)
- [Dépannage des types de données](troubleshooting-data-types.md)
- [Remplir des datasets à l’aide de TableAdapters](/visualstudio/data-tools/fill-datasets-by-using-tableadapters)
- [If (opérateur)](../../../language-reference/operators/if-operator.md)
- [Inférence de type local](../variables/local-type-inference.md)
- [Is (opérateur)](../../../language-reference/operators/is-operator.md)
- [IsNot (opérateur)](../../../language-reference/operators/isnot-operator.md)
- [Types valeur Nullable (C#)](../../../../csharp/language-reference/builtin-types/nullable-value-types.md)
