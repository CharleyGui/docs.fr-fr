---
title: Inférence de type
description: Découvrez comment le F# compilateur déduit les types de valeurs, les variables, les paramètres et les valeurs de retour.
ms.date: 05/16/2016
ms.openlocfilehash: 4b18c1a67a8b7ddadb4fb334ea4736e9fd29feb0
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/30/2019
ms.locfileid: "68630179"
---
# <a name="type-inference"></a>Inférence de type

Cette rubrique décrit comment le F# compilateur déduit les types de valeurs, de variables, de paramètres et de valeurs de retour.

## <a name="type-inference-in-general"></a>Inférence de type en général

L’idée de l’inférence de type est que vous n’avez pas besoin de spécifier F# les types de constructions, sauf lorsque le compilateur ne peut pas déduire le type de façon concluante. L’omission des informations de type explicite ne signifie F# pas qu’il s’agit d’un langage dynamiquement F# typé ou que les valeurs de sont faiblement typées. F#est un langage statiquement typé, ce qui signifie que le compilateur déduit un type exact pour chaque construction pendant la compilation. S’il n’y a pas assez d’informations pour que le compilateur déduire les types de chaque construction, vous devez fournir des informations de type supplémentaires, généralement en ajoutant des annotations de type explicites quelque part dans le code.

## <a name="inference-of-parameter-and-return-types"></a>Inférence des types de paramètres et de retour

Dans une liste de paramètres, vous n’avez pas besoin de spécifier le type de chaque paramètre. Et pourtant, F# est un langage typé statiquement, et par conséquent, chaque valeur et expression a un type défini au moment de la compilation. Pour les types que vous ne spécifiez pas explicitement, le compilateur déduit le type en fonction du contexte. Si le type n’est pas spécifié, il est déduit comme étant générique. Si le code utilise une valeur de façon incohérente, de façon à ce qu’il n’y ait pas de type déduit unique qui satisfait à toutes les utilisations d’une valeur, le compilateur signale une erreur.

Le type de retour d’une fonction est déterminé par le type de la dernière expression dans la fonction.

Par exemple, dans le code suivant, les `a` types de paramètres et `b` et le type de retour sont `int` tous déduits comme étant `100` , car le `int`littéral est de type.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-3/snippet301.fs)]

Vous pouvez influencer l’inférence de type en modifiant les littéraux. `100` Si vous faites un `uint32` en ajoutant le suffixe `u`, les types de, `a`et `b`sont déduits `uint32`de la valeur de retour.

Vous pouvez également influencer l’inférence de type à l’aide d’autres constructions qui impliquent des restrictions sur le type, telles que des fonctions et des méthodes qui fonctionnent avec un seul type particulier.

En outre, vous pouvez appliquer des annotations de type explicites à des paramètres de fonction ou de méthode ou à des variables dans des expressions, comme indiqué dans les exemples suivants. Des erreurs sont générées si des conflits se produisent entre différentes contraintes.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-3/snippet302.fs)]

Vous pouvez également spécifier explicitement la valeur de retour d’une fonction en fournissant une annotation de type après tous les paramètres.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-3/snippet303.fs)]

Une annotation de type est souvent utile sur un paramètre lorsque le paramètre est un type d’objet et que vous souhaitez utiliser un membre.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-3/snippet304.fs)]

## <a name="automatic-generalization"></a>Généralisation automatique

Si le code de la fonction n’est pas dépendant du type d’un paramètre, le compilateur considère que le paramètre est générique. C’est ce que l’on appelle la *généralisation automatique*, et il peut s’agir d’une puissante aide à écrire du code générique sans complexité croissante.

Par exemple, la fonction suivante combine deux paramètres de n’importe quel type en un tuple.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-3/snippet305.fs)]

Le type est déduit comme étant

```fsharp
'a -> 'b -> 'a * 'b
```

## <a name="additional-information"></a>Informations supplémentaires

L’inférence de type est décrite plus en détail F# dans la spécification du langage.

## <a name="see-also"></a>Voir aussi

- [Généralisation automatique](./generics/automatic-generalization.md)
