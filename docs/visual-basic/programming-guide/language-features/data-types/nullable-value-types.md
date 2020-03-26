---
title: Types valeur Nullable
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
ms.openlocfilehash: beed8262c50dc68330b8f03aa3d864ed2f8df0d5
ms.sourcegitcommit: 99b153b93bf94d0fecf7c7bcecb58ac424dfa47c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/25/2020
ms.locfileid: "80249680"
---
# <a name="nullable-value-types-visual-basic"></a>Types valeur Nullable (Visual Basic)

Parfois, vous travaillez avec un type de valeur qui n’a pas de valeur définie dans certaines circonstances. Par exemple, un champ dans une base de données peut avoir à faire la distinction entre avoir une valeur assignée qui est significative et ne pas avoir une valeur assignée. Les types de valeur peuvent être étendus pour prendre leurs valeurs normales ou une valeur nulle. Une telle extension est appelée un *type nul*.

Chaque type de valeur in <xref:System.Nullable%601> nullable est construit à partir de la structure générique. Envisagez une base de données qui suit les activités liées au travail. L’exemple suivant construit `Boolean` un type nul et déclare une variable de ce type. Vous pouvez écrire la déclaration de trois façons :

[!code-vb[VbVbalrNullableValue#1](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrNullableValue/VB/Class1.vb#1)]

La `ridesBusToWork` variable peut contenir `True`une valeur `False`de , une valeur de , ou aucune valeur du tout. Sa valeur initiale par défaut n’a aucune valeur, ce qui, dans ce cas, pourrait signifier que l’information n’a pas encore été obtenue pour cette personne. En revanche, `False` cela pourrait signifier que l’information a été obtenue et que la personne ne monte pas dans l’autobus pour se rendre au travail.

Vous pouvez déclarer des variables et des propriétés avec des types de valeur nul, et vous pouvez déclarer un tableau avec des éléments d’un type de valeur nul. Vous pouvez déclarer les procédures avec les types de valeur nuls comme `Function` paramètres, et vous pouvez retourner un type de valeur nul d’une procédure.

Vous ne pouvez pas construire un type nul sur `String`un type de référence tel qu’un tableau, un, ou une classe. Le type sous-jacent doit être un type de valeur. Pour plus d'informations, consultez [Value Types and Reference Types](value-types-and-reference-types.md).

## <a name="using-a-nullable-type-variable"></a>Utilisation d’une variable de type nul

Les membres les plus importants d’un <xref:System.Nullable%601.Value%2A> type de valeur nul sont ses propriétés et ses <xref:System.Nullable%601.HasValue%2A> propriétés. Pour une variable d’un <xref:System.Nullable%601.HasValue%2A> type de valeur nulle, vous indique si la variable contient une valeur définie. Si <xref:System.Nullable%601.HasValue%2A> `True`est , vous pouvez <xref:System.Nullable%601.Value%2A>lire la valeur de . Notez <xref:System.Nullable%601.HasValue%2A> que <xref:System.Nullable%601.Value%2A> `ReadOnly` les deux et sont des propriétés.

### <a name="default-values"></a>Valeurs par défaut

Lorsque vous déclarez une variable avec <xref:System.Nullable%601.HasValue%2A> un type de `False`valeur nul, sa propriété a une valeur par défaut de . Cela signifie que par défaut la variable n’a pas de valeur définie, au lieu de la valeur par défaut de son type de valeur sous-jacente. Dans l’exemple suivant, la variable `numberOfChildren` n’a initialement aucune `Integer` valeur définie, même si la valeur par défaut du type est de 0.

[!code-vb[VbVbalrNullableValue#2](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrNullableValue/VB/Class1.vb#2)]

Une valeur nulle est utile pour indiquer une valeur indéfinie ou inconnue. Si `numberOfChildren` elle avait `Integer`été déclarée comme, il n’y aurait aucune valeur qui pourrait indiquer que l’information n’est pas actuellement disponible.

### <a name="storing-values"></a>Stockage des valeurs

Vous stockez une valeur dans une variable ou une propriété d’un type de valeur nulle de la manière typique. L’exemple suivant attribue une `numberOfChildren` valeur à la variable déclarée dans l’exemple précédent.

[!code-vb[VbVbalrNullableValue#3](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrNullableValue/VB/Class1.vb#3)]

Si une variable ou une propriété d’un type de valeur nulle contient une valeur définie, vous pouvez la faire revenir à son état initial de ne pas avoir une valeur attribuée. Vous le faites en définissant `Nothing`la variable ou la propriété à , comme le montre l’exemple suivant.

[!code-vb[VbVbalrNullableValue#4](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrNullableValue/VB/Class1.vb#4)]

> [!NOTE]
> Bien que `Nothing` vous puissiez attribuer à une variable d’un `Nothing` type de valeur nulle, vous ne pouvez pas la tester en utilisant le signe égal. Comparaison qui utilise le `someVar = Nothing`signe égal, `Nothing`, évalue toujours à . Vous pouvez tester la <xref:System.Nullable%601.HasValue%2A> propriété `False`de la variable `Is` `IsNot` pour , ou tester en utilisant le ou l’opérateur.

### <a name="retrieving-values"></a>Récupération des valeurs

Pour récupérer la valeur d’une variable d’un type <xref:System.Nullable%601.HasValue%2A> de valeur nulle, vous devez d’abord tester sa propriété pour confirmer qu’elle a une valeur. Si vous essayez de <xref:System.Nullable%601.HasValue%2A> lire `False`la valeur quand <xref:System.InvalidOperationException> est, Visual Basic jette une exception. L’exemple suivant montre la façon `numberOfChildren` recommandée de lire la variable des exemples précédents.

[!code-vb[VbVbalrNullableValue#5](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrNullableValue/VB/Class1.vb#5)]

## <a name="comparing-nullable-types"></a>Comparaison des types nuls

Lorsque des `Boolean` variables où les variables sont `True`utilisées `False`dans `Nothing`les expressions Boolean, le résultat peut être , , ou . Ce qui suit est `And` `Or`le tableau de vérité pour et . Parce `b1` `b2` qu’et ont maintenant trois valeurs possibles, il ya neuf combinaisons à évaluer.

|b1|B2|b1 Et b2|b1 Ou b2|
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

Lorsque la valeur d’une variable `Nothing`boolean `true` ou `false`d’expression est , il n’est ni ni . Considérez l'exemple suivant.

[!code-vb[VbVbalrNullableValue#6](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrNullableValue/VB/Class1.vb#6)]

Dans cet `b1 And b2` exemple, `Nothing`évalue à . Par conséquent, `Else` la clause est `If` exécutée dans chaque énoncé, et la sortie est la suivante :

`Expression is not true`

`Expression is not false`

> [!NOTE]
> `AndAlso`et `OrElse`, qui utilisent l’évaluation en court-circuit, doivent évaluer `Nothing`leurs deuxièmes opérands lorsque le premier évalue à .

## <a name="propagation"></a>Propagation

Si l’un ou les deux opérands d’une opération arithmétique, comparaison, décalage ou type est un type de valeur nulable, le résultat de l’opération est également un type de valeur nul. Si les deux opérandes `Nothing`ont des valeurs qui ne le sont pas, l’opération est exécutée sur les valeurs sous-jacentes des opérandes, comme si ni l’un ni l’autre n’étaient un type de valeur nul. Dans l’exemple `compare1` suivant, les variables et `sum1` sont implicitement tapées. Si vous reposez le pointeur de souris au-dessus d’eux, vous verrez que le compilateur infère les types de valeur nul pour les deux d’entre eux.

[!code-vb[VbVbalrNullableValue#7](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrNullableValue/VB/Class1.vb#7)]

Si l’un ou les deux `Nothing`opérands `Nothing`ont une valeur de , le résultat sera .

[!code-vb[VbVbalrNullableValue#8](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrNullableValue/VB/Class1.vb#8)]

## <a name="using-nullable-types-with-data"></a>Utilisation de types nuls avec des données

Une base de données est l’un des endroits les plus importants pour utiliser des types de valeur nul. Tous les objets de base de données ne prennent pas actuellement en charge les types de valeur nuls, mais les adaptateurs de table générés par le concepteur le font. Voir [TableAdapter support for nullable types](/visualstudio/data-tools/fill-datasets-by-using-tableadapters#tableadapter-support-for-nullable-types).

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
- [Types de valeur nuls (C)](../../../../csharp/language-reference/builtin-types/nullable-value-types.md)
