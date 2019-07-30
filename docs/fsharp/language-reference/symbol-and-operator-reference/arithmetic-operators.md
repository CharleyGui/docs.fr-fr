---
title: Opérateurs arithmétiques
description: En savoir plus sur les opérateurs arithmétiques qui sont F# disponibles dans le langage de programmation.
ms.date: 04/04/2018
ms.openlocfilehash: b783a0134541f11f06dde83af97676699b797da1
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/30/2019
ms.locfileid: "68630782"
---
# <a name="arithmetic-operators"></a>Opérateurs arithmétiques

Cette rubrique décrit les opérateurs arithmétiques qui sont disponibles F# dans le langage.

## <a name="summary-of-binary-arithmetic-operators"></a>Résumé des opérateurs arithmétiques binaires

Le tableau suivant récapitule les opérateurs arithmétiques binaires disponibles pour les types unboxed intégrale et à virgule flottante.

|Opérateur binaire|Notes|
|---------------|-----|
|`+`(addition, plus)|Désactivée. Condition de dépassement possible lorsque des nombres sont ajoutés ensemble et que la somme dépasse la valeur absolue maximale prise en charge par le type.|
|`-`(soustraction, moins)|Désactivée. Condition de dépassement de capacité négatif lorsque les types non signés sont soustraits ou lorsque les valeurs à virgule flottante sont trop petites pour être représentées par le type.|
|`*`(multiplication, Times)|Désactivée. Condition de dépassement possible lorsque les nombres sont multipliés et que le produit dépasse la valeur absolue maximale prise en charge par le type.|
|`/`(Division, divisé par)|La division par zéro provoque <xref:System.DivideByZeroException> une pour les types intégraux. Pour les types à virgule flottante, la division par zéro vous donne les valeurs `+Infinity` à virgule flottante spéciales ou. `-Infinity` Il peut également y avoir une condition de dépassement de capacité négatif quand un nombre à virgule flottante est trop petit pour être représenté par le type.|
|`%`(reste, REM)|Retourne le reste d’une opération de division. Le signe du résultat est le même que le signe du premier opérande.|
|`**`(élévation à la puissance)|Condition de dépassement possible lorsque le résultat dépasse la valeur absolue maximale pour le type.<br /><br />L’opérateur d’élévation à la puissance fonctionne uniquement avec les types à virgule flottante.|

## <a name="summary-of-unary-arithmetic-operators"></a>Résumé des opérateurs arithmétiques unaires

Le tableau suivant récapitule les opérateurs arithmétiques unaires qui sont disponibles pour les types intégraux et à virgule flottante.

|Unaire, opérateur|Notes|
|--------------|-----|
|`+`formelle|Peut être appliqué à n’importe quelle expression arithmétique. Ne modifie pas le signe de la valeur.|
|`-`(négation, Negative)|Peut être appliqué à n’importe quelle expression arithmétique. Modifie le signe de la valeur.|

Le comportement au niveau du dépassement de capacité positif ou négatif pour les types intégraux consiste à encapsuler. Cela génère un résultat incorrect. Le dépassement sur les entiers est un problème potentiellement sérieux qui peut contribuer aux problèmes de sécurité lorsque le logiciel n’est pas écrit pour en tenir compte. S’il s’agit d’un problème pour votre application, envisagez d' `Microsoft.FSharp.Core.Operators.Checked`utiliser les opérateurs checked dans.

## <a name="summary-of-binary-comparison-operators"></a>Résumé des opérateurs de comparaison binaires

Le tableau suivant présente les opérateurs de comparaison binaires disponibles pour les types intégraux et à virgule flottante. Ces opérateurs retournent des `bool`valeurs de type.

Les nombres à virgule flottante ne doivent jamais être comparés directement, car la représentation à virgule flottante IEEE ne prend pas en charge une opération d’égalité exacte. Deux nombres que vous pouvez facilement vérifier comme égaux en inspectant le code peuvent en fait avoir différentes représentations de bits.

|Opérateur|Notes|
|--------|-----|
|`=`(égalité, égal à)|Il ne s’agit pas d’un opérateur d’assignation. Elle est utilisée uniquement pour la comparaison. Il s’agit d’un opérateur générique.|
|`>`(supérieur à)|Il s’agit d’un opérateur générique.|
|`<`(inférieur à)|Il s’agit d’un opérateur générique.|
|`>=`(supérieur ou égal à)|Il s’agit d’un opérateur générique.|
|`<=`(inférieur ou égal à)|Il s’agit d’un opérateur générique.|
|`<>`(différent de)|Il s’agit d’un opérateur générique.|

## <a name="overloaded-and-generic-operators"></a>Opérateurs génériques et surchargés

Tous les opérateurs présentés dans cette rubrique sont définis dans l’espace de noms **Microsoft. FSharp. Core. Operators** . Certains des opérateurs sont définis à l’aide de paramètres de type résolus statiquement. Cela signifie qu’il existe des définitions individuelles pour chaque type spécifique qui fonctionne avec cet opérateur. Tous les opérateurs arithmétiques et binaires unaires et binaires sont dans cette catégorie. Les opérateurs de comparaison sont génériques et, par conséquent, fonctionnent avec n’importe quel type, pas seulement des types arithmétiques primitifs. Les types d’Union et d’enregistrement discriminés ont leurs propres implémentations personnalisées qui F# sont générées par le compilateur. Les types de classe utilisent <xref:System.Object.Equals%2A>la méthode.

Les opérateurs génériques sont personnalisables. Pour personnaliser les fonctions de comparaison, substituez <xref:System.Object.Equals%2A> pour fournir votre propre comparaison d’égalité personnalisée, puis implémentez. <xref:System.IComparable> L' <xref:System.IComparable?displayProperty=nameWithType> interface possède une méthode unique, la <xref:System.IComparable.CompareTo%2A> méthode.

## <a name="operators-and-type-inference"></a>Opérateurs et inférence de type

L’utilisation d’un opérateur dans une expression limite l’inférence de type sur cet opérateur. En outre, l’utilisation d’opérateurs empêche la généralisation automatique, car l’utilisation d’opérateurs implique un type arithmétique. En l’absence d’autres informations, le F# compilateur déduit `int` comme type d’expressions arithmétiques. Vous pouvez remplacer ce comportement en spécifiant un autre type. Ainsi, les types d’arguments et le `function1` type de retour de dans le code suivant sont `int`déduits comme étant `function2` , mais les types pour `float`sont déduits comme étant.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet3501.fs)]

## <a name="see-also"></a>Voir aussi

- [Informations de référence des symboles et opérateurs](index.md)
- [Surcharge d'opérateur](../operator-overloading.md)
- [Opérateurs au niveau du bit](bitwise-operators.md)
- [Opérateurs booléens](boolean-operators.md)
