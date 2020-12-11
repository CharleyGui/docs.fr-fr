---
title: Comment gérer une exception à l’aide du Guide de programmation try-catch-C#
description: Découvrez comment gérer une exception à l’aide d’un bloc try-catch. Consultez un exemple de code et affichez des ressources supplémentaires disponibles.
ms.date: 12/09/2020
helpviewer_keywords:
- exception handling [C#], try/catch blocks
- exceptions [C#], try/catch blocks
- try/catch blocks [C#]
ms.assetid: ca8e3773-980e-4767-8633-7408540e9818
ms.openlocfilehash: b6368660dbe037123f5bb6ce52502d4a94fcfc3a
ms.sourcegitcommit: 9b877e160c326577e8aa5ead22a937110d80fa44
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97110518"
---
# <a name="how-to-handle-an-exception-using-trycatch-c-programming-guide"></a>Comment gérer une exception à l’aide de try/catch (Guide de programmation C#)

L’objectif d’un bloc [try-catch](../../language-reference/keywords/try-catch.md) est d’intercepter et de gérer une exception générée par du code opérationnel. Certaines exceptions peuvent être gérées dans un `catch` bloc et le problème résolu sans que l’exception soit levée à nouveau ; toutefois, plus souvent, la seule chose que vous pouvez faire est de vous assurer que l’exception appropriée est levée.

## <a name="example"></a>Exemple

Dans cet exemple, <xref:System.IndexOutOfRangeException> n’est pas l’exception la plus appropriée : est <xref:System.ArgumentOutOfRangeException> plus logique pour la méthode, car l’erreur est provoquée par l' `index` argument passé par l’appelant.

:::code language="csharp" source="snippets/exceptions/ExampleTryCatch.cs" id="ExampleTryCatch":::

## <a name="comments"></a>Commentaires

Le code qui provoque une exception est cloisonné dans le bloc `try`. Une instruction `catch` est ajoutée juste après pour gérer `IndexOutOfRangeException`, si elle se produit. Le bloc `catch` gère `IndexOutOfRangeException` et lève l’exception plus appropriée `ArgumentOutOfRangeException` à la place. Pour fournir à l’appelant autant d’informations que possible, pensez à spécifier l’exception d’origine comme <xref:System.Exception.InnerException%2A> de la nouvelle exception. Étant donné que la <xref:System.Exception.InnerException%2A> propriété est [en lecture seule](../../properties.md#read-only), vous devez l’assigner dans le constructeur de la nouvelle exception.
