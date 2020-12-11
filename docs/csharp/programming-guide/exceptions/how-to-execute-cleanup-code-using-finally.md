---
title: Guide pratique pour exécuter le code de nettoyage à l’aide de finally (Guide de programmation C#)
description: Découvrez comment exécuter le code de nettoyage à l’aide d’une instruction’Finally'. Enfin, les instructions garantissent que tout nettoyage nécessaire d’objets se produit immédiatement.
ms.date: 12/09/2020
helpviewer_keywords:
- try/finally blocks [C#]
- exceptions [C#], try/finally block
- exception handling [C#], try/finally block
ms.assetid: 1b1e5aef-3f32-4a88-9d39-b5fffb33bdaf
ms.openlocfilehash: e9b5d3086488d3f7e3c0709317d6fafd15c439e8
ms.sourcegitcommit: 9b877e160c326577e8aa5ead22a937110d80fa44
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97110180"
---
# <a name="how-to-execute-cleanup-code-using-finally-c-programming-guide"></a>Comment exécuter le code de nettoyage à l’aide de finally (Guide de programmation C#)

L’objectif d’une instruction `finally` est de vérifier que le nettoyage nécessaire des objets, généralement ceux contenant des ressources externes, se produit immédiatement, même si une exception est levée. Un exemple de nettoyage de ce type est l’appel à <xref:System.IO.Stream.Close%2A> sur un <xref:System.IO.FileStream> immédiatement après son utilisation au lieu d’attendre que l’objet soit récupéré par garbage collection par le Common Language Runtime, comme suit :

:::code language="csharp" source="snippets/exceptions/Program.cs" ID="NoCleanup":::

## <a name="example"></a>Exemple

Pour transformer le code précédent en instruction `try-catch-finally`, le code de nettoyage est séparé du code actif comme suit.

:::code language="csharp" source="snippets/exceptions/Program.cs" ID="WithCleanup":::

Comme une exception peut se produire à tout moment dans le `try` bloc avant l' `OpenWrite()` appel, ou `OpenWrite()` si l’appel lui-même peut échouer, nous n’avons pas la garantie que le fichier est ouvert lorsque nous tentons de le fermer. Le `finally` bloc ajoute une vérification pour s’assurer que l' <xref:System.IO.FileStream> objet ne se trouve pas `null` avant d’appeler la <xref:System.IO.Stream.Close%2A> méthode. Sans la `null` vérification, le `finally` bloc pourrait lever sa propre <xref:System.NullReferenceException> , mais la levée d’exceptions dans des `finally` blocs doit être évitée si possible.

Une connexion de base de données est également susceptible d’être fermée dans un bloc `finally`. Le nombre de connexions à un serveur de base de données étant parfois limité, vous devez fermer les connexions de base de données le plus rapidement possible. Si une exception est levée avant que vous ne puissiez fermer votre connexion, l’utilisation du `finally` bloc est préférable à l’attente de garbage collection.

## <a name="see-also"></a>Voir aussi

- [using, instruction](../../language-reference/keywords/using-statement.md)
- [try-catch](../../language-reference/keywords/try-catch.md)
- [try-finally](../../language-reference/keywords/try-finally.md)
- [try-catch-finally](../../language-reference/keywords/try-catch-finally.md)
