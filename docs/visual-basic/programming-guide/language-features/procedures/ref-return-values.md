---
title: Valeurs de retour de référence
ms.date: 04/28/2017
helpviewer_keywords:
- variables [Visual Basic]
- ref return values [Visual Basic]
- ref returns [Visual Basic]
ms.assetid: 5ef0cc69-eb3a-4a67-92a2-78585f223cb5
ms.openlocfilehash: 2d2a302a899fbde549161469f281d3e580bcb71f
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74352535"
---
# <a name="support-for-reference-return-values-visual-basic"></a>Prise en charge des valeurs de retour de référence (Visual Basic)

À partir C# de 7,0, C# le langage prend en charge les *valeurs de retour de référence*. L’une des façons de comprendre les valeurs de retour de référence est qu’elles sont l’opposé des arguments passés par référence à une méthode. Lorsqu’un argument passé par référence est modifié, les modifications sont reflétées dans la valeur de la variable sur l’appelant. Lorsqu’une méthode fournit une valeur de retour de référence à un appelant, les modifications apportées à la valeur de retour de référence par l’appelant sont répercutées dans les données de la méthode appelée.

Visual Basic ne vous autorise pas à créer des méthodes avec des valeurs de retour de référence, mais vous permet d’utiliser des valeurs de retour de référence. En d’autres termes, vous pouvez appeler une méthode avec une valeur de retour de référence et modifier cette valeur de retour, et les modifications apportées à la valeur de retour de référence sont reflétées dans les données de la méthode appelée.

## <a name="modifying-the-ref-return-value-directly"></a>Modification directe de la valeur de retour de référence

Pour les méthodes qui s’exécutent toujours et qui n’ont pas de paramètres `ByRef`, vous pouvez modifier directement la valeur de retour de référence. Pour ce faire, affectez la nouvelle valeur aux expressions qui retourne la valeur de retour de référence.

L’exemple C# suivant définit une méthode `NumericValue.IncrementValue` qui incrémente une valeur interne et la retourne en tant que valeur de retour de référence.

[!code-csharp[Ref-Return](../../../../../samples/snippets/visualbasic/programming-guide/language-features/procedures/ref-returns1.cs)]

La valeur de retour de référence est ensuite modifiée par l’appelant dans l’exemple de Visual Basic suivant. Notez que la ligne avec l’appel de méthode `NumericValue.IncrementValue` n’affecte pas de valeur à la méthode. Au lieu de cela, elle assigne une valeur à la valeur de retour de référence retournée par la méthode.

[!code-vb[Ref-Return](../../../../../samples/snippets/visualbasic/programming-guide/language-features/procedures/use-ref-returns1.vb)]

## <a name="using-a-helper-method"></a>Utilisation d’une méthode d’assistance

Dans d’autres cas, la modification directe de la valeur de retour de référence d’un appel de méthode peut ne pas toujours être souhaitable. Par exemple, une méthode de recherche qui retourne une chaîne peut ne pas toujours trouver de correspondance. Dans ce cas, vous souhaitez modifier la valeur de retour de référence uniquement si la recherche est réussie.

L’exemple C# suivant illustre ce scénario. Il définit une classe `Sentence` écrite dans C# comprend une méthode `FindNext` qui recherche le mot suivant dans une phrase qui commence par une sous-chaîne spécifiée. La chaîne est retournée comme valeur de retour de référence et une variable `Boolean` passée par référence à la méthode indique si la recherche a réussi. La valeur de retour de référence indique que l’appelant peut non seulement lire la valeur retournée ; Il peut également le modifier, et cette modification est reflétée dans les données contenues en interne dans la classe `Sentence`.

[!code-csharp[Ref-Return](../../../../../samples/snippets/visualbasic/getting-started/ref-returns.cs)]

La modification directe de la valeur de retour de référence dans ce cas n’est pas fiable, car l’appel de la méthode peut ne pas trouver de correspondance et retourner le premier mot de la phrase. Dans ce cas, l’appelant va modifier par inadvertance le premier mot de la phrase. Cela peut être évité par l’appelant qui retourne une `null` (ou `Nothing` dans Visual Basic). Mais dans ce cas, toute tentative de modification d’une chaîne dont la valeur est `Nothing` lève une <xref:System.NullReferenceException>. Si peut également être évité par l’appelant qui retourne <xref:System.String.Empty?displayProperty=nameWithType>, mais cela nécessite que l’appelant définisse une variable de chaîne dont la valeur est <xref:System.String.Empty?displayProperty=nameWithType>. Alors que l’appelant peut modifier cette chaîne, la modification elle-même n’a aucun effet, car la chaîne modifiée n’a aucune relation avec les mots de la phrase stockée par la classe `Sentence`.

La meilleure façon de gérer ce scénario consiste à passer la valeur de retour de référence par référence à une méthode d’assistance. La méthode d’assistance contient ensuite la logique permettant de déterminer si l’appel de la méthode a réussi et, si tel est le cas, de modifier la valeur de retour de référence. L’exemple suivant fournit une implémentation possible.

[!code-vb[Ref-Return](../../../../../samples/snippets/visualbasic/getting-started/ref-return-helper.vb#1)]

## <a name="see-also"></a>Voir aussi

- [Passage d’arguments par valeur et par référence](passing-arguments-by-value-and-by-reference.md)
- [Procédures dans Visual Basic](index.md)
