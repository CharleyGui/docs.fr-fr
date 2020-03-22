---
title: Valeurs de retour Ref
ms.date: 04/28/2017
helpviewer_keywords:
- variables [Visual Basic]
- ref return values [Visual Basic]
- ref returns [Visual Basic]
ms.assetid: 5ef0cc69-eb3a-4a67-92a2-78585f223cb5
ms.openlocfilehash: f2a92c584dbb12a322e28435d797fa4d7c2f6dbb
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79186934"
---
# <a name="support-for-reference-return-values-visual-basic"></a>Prise en charge des valeurs de rendement de référence (Visual Basic)

À partir de C 7.0, la langue CMD prend en charge les *valeurs de retour de référence*. Une façon de comprendre les valeurs de rendement de référence est qu’elles sont à l’opposé des arguments qui sont adoptés en se référant à une méthode. Lorsqu’un argument adopté par référence est modifié, les modifications sont reflétées dans la valeur de la variable sur l’appelant. Lorsqu’une méthode fournit une valeur de retour de référence à un appelant, les modifications apportées à la valeur de rendement de référence par l’appelant sont reflétées dans les données de la méthode appelée.

Visual Basic ne vous permet pas d’écrire des méthodes avec des valeurs de retour de référence, mais il vous permet de consommer des valeurs de retour de référence. En d’autres termes, vous pouvez appeler une méthode avec une valeur de rendement de référence et modifier cette valeur de rendement, et les modifications apportées à la valeur de rendement de référence sont reflétées dans les données de la méthode appelées.

## <a name="modifying-the-ref-return-value-directly"></a>Modification directe de la valeur de retour de l’arbitre

Pour les méthodes qui `ByRef` réussissent toujours et n’ont pas de paramètres, vous pouvez modifier directement la valeur de retour de référence. Pour ce faire, vous attribuez la nouvelle valeur aux expressions qui retournent la valeur de rendement de référence.

L’exemple CMD suivant `NumericValue.IncrementValue` définit une méthode qui incrémente une valeur interne et la renvoie comme valeur de rendement de référence.

[!code-csharp[Ref-Return](../../../../../samples/snippets/visualbasic/programming-guide/language-features/procedures/ref-returns1.cs)]

La valeur de retour de référence est ensuite modifiée par l’appelant dans l’exemple visual basic suivant. Notez que la `NumericValue.IncrementValue` ligne avec l’appel de méthode n’attribue pas une valeur à la méthode. Au lieu de cela, il attribue une valeur à la valeur de rendement de référence retournée par la méthode.

[!code-vb[Ref-Return](../../../../../samples/snippets/visualbasic/programming-guide/language-features/procedures/use-ref-returns1.vb)]

## <a name="using-a-helper-method"></a>Utilisation d’une méthode d’aide

Dans d’autres cas, il n’est pas toujours souhaitable de modifier directement la valeur de retour de référence d’un appel de méthode. Par exemple, une méthode de recherche qui renvoie une chaîne peut ne pas toujours trouver une correspondance. Dans ce cas, vous souhaitez modifier la valeur de retour de référence uniquement si la recherche est réussie.

L’exemple suivant de CMD illustre ce scénario. Il définit `Sentence` une classe écrite en `FindNext` C comprend une méthode qui trouve le mot suivant dans une phrase qui commence par un sous-corde spécifié. La chaîne est retournée comme valeur de retour de référence et une variable `Boolean` passée par référence à la méthode indique si la recherche a réussi. La valeur de rendement de référence indique qu’en plus de lire la valeur retournée, l’appelant `Sentence` peut également la modifier et que la modification est reflétée dans les données contenues à l’interne dans la catégorie.

[!code-csharp[Ref-Return](../../../../../samples/snippets/visualbasic/getting-started/ref-returns.cs)]

Modifier directement la valeur de déclaration de référence dans ce cas n’est pas fiable, puisque l’appel de méthode peut ne pas trouver une correspondance et retourner le premier mot dans la phrase. Dans ce cas, l’appelant modifiera par inadvertance le premier mot de la phrase. Cela pourrait être empêché par `null` l’appelant de retourner un (ou `Nothing` dans Visual Basic). Mais dans ce cas, tenter de `Nothing` modifier une <xref:System.NullReferenceException>chaîne dont la valeur est jette un . Si cela peut également être <xref:System.String.Empty?displayProperty=nameWithType>empêché par le retour de l’appelant, <xref:System.String.Empty?displayProperty=nameWithType>mais cela exige que l’appelant définisse une variable de chaîne dont la valeur est . Bien que l’appelant puisse modifier cette chaîne, la modification elle-même ne sert à rien, puisque la chaîne modifiée n’a aucun rapport avec les mots de la phrase stockées par la `Sentence` classe.

La meilleure façon de gérer ce scénario est de passer la valeur de retour de référence par référence à une méthode d’aide. La méthode de l’aide contient alors la logique pour déterminer si l’appel de méthode a réussi et, si elle l’a fait, de modifier la valeur de retour de référence. L’exemple suivant fournit une mise en œuvre possible.

[!code-vb[Ref-Return](../../../../../samples/snippets/visualbasic/getting-started/ref-return-helper.vb#1)]

## <a name="see-also"></a>Voir aussi

- [Passer les arguments par valeur et par référence](passing-arguments-by-value-and-by-reference.md)
- [Procédures dans Visual Basic](index.md)
