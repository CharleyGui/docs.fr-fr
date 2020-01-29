---
title: Exceptions et gestion des exceptions - Guide de programmation C#
ms.date: 07/20/2015
helpviewer_keywords:
- exception handling [C#]
- exceptions [C#]
- C# language, exceptions
ms.assetid: 0001887f-4fa2-47e2-8034-2819477e2344
ms.openlocfilehash: b883012cf8f72247ff4e0b47a46eee1854e2d534
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76735648"
---
# <a name="exceptions-and-exception-handling-c-programming-guide"></a>Exceptions et gestion des exceptions (Guide de programmation C#)

Les fonctionnalités de gestion des exceptions du langage C# vous aident à gérer les situations inattendues ou exceptionnelles qui se produisent lorsqu’un programme est en cours d’exécution. La gestion des exceptions utilise les mots clés `try`, `catch` et `finally` pour tenter des actions susceptibles de ne pas réussir, pour gérer les défaillances lorsque vous pensez que c’est justifié et pour nettoyer ensuite les ressources. Les exceptions peuvent être générées par le common language runtime (CLR), par .NET Framework ou des bibliothèques tierces, ou par le code de l’application. Les exceptions sont créées avec le mot clé `throw`.

Dans de nombreux cas, une exception peut être levée non pas par une méthode appelée directement par votre code, mais par une autre méthode plus loin dans la pile des appels. Dans ce cas, le CLR déroule la pile à la recherche d’une méthode avec un bloc `catch` pour le type d’exception concerné et exécute le premier bloc `catch` de ce type qu’il trouve. S’il ne trouve pas de bloc `catch` dans la pile des appels, il termine le processus et affiche un message à l’utilisateur.

Dans cet exemple, une méthode teste la division par zéro et intercepte l’erreur. Sans la gestion des exceptions, ce programme se terminerait avec une erreur **DivideByZeroException non gérée**.

[!code-csharp[csProgGuideExceptions#18](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideExceptions/CS/Exceptions.cs#18)]

## <a name="exceptions-overview"></a>Vue d’ensemble des exceptions

Les exceptions ont les propriétés suivantes :

- Les exceptions sont des types qui dérivent tous en définitive de `System.Exception`.
- Utilisez un bloc `try` autour des instructions qui peuvent lever des exceptions.
- Dès qu’une exception se produit dans le bloc `try`, le flux de contrôle passe immédiatement au premier gestionnaire d’exceptions associé présent dans la pile des appels. En C#, le mot clé `catch` est utilisé pour définir un gestionnaire d’exceptions.
- Si aucun gestionnaire d’exceptions n’est présent pour une exception donnée, le programme s’arrête avec un message d’erreur.
- N’interceptez pas d’exception si vous ne pouvez pas la gérer tout en laissant l’application dans un état connu. Si vous interceptez `System.Exception`, levez-la à nouveau à l’aide du mot clé `throw` à la fin du bloc `catch`.
- Si un bloc `catch` définit une variable d’exception, vous pouvez l’utiliser pour obtenir plus d’informations sur le type d’exception qui s’est produit.
- Les exceptions peuvent être générées explicitement par un programme avec le mot clé `throw`.
- Les objets Exception contiennent des informations détaillées sur l'erreur, telles que l'état de la pile des appels et une description du texte de l'erreur.
- Le code qui se trouve dans un bloc `finally` est exécuté même si une exception est levée. Utilisez un bloc `finally` pour libérer des ressources, par exemple pour fermer tous les flux ou fichiers qui ont été ouverts dans le bloc `try`.
- Les exceptions gérées dans .NET Framework sont implémentées au-dessus du mécanisme de gestion structurée des exceptions de Win32. Pour plus d’informations, consultez les pages [Gestion structurée des exceptions (C/C++)](/cpp/cpp/structured-exception-handling-c-cpp) et [Cours intensif sur la gestion structurée des exceptions de Win32](http://bytepointer.com/resources/pietrek_crash_course_depths_of_win32_seh.htm).

## <a name="related-sections"></a>Rubriques connexes

Pour plus d’informations sur les exceptions et la gestion des exceptions, consultez les articles suivants :

- [Utilisation d’exceptions](using-exceptions.md)
- [Gestion des exceptions](exception-handling.md)
- [Création et levée d’exceptions](creating-and-throwing-exceptions.md)
- [Exceptions générées par le compilateur](compiler-generated-exceptions.md)
- [Comment gérer une exception à l’aide de try/C# catch (Guide de programmation)](how-to-handle-an-exception-using-try-catch.md)
- [Comment exécuter le code de nettoyage à l’aide de finally](how-to-execute-cleanup-code-using-finally.md)
- [Comment intercepter une exception non-CLS](how-to-catch-a-non-cls-exception.md)

## <a name="c-language-specification"></a>Spécification du langage C#

Pour plus d’informations, consultez [Exceptions](~/_csharplang/spec/exceptions.md) dans la [Spécification du langage C#](/dotnet/csharp/language-reference/language-specification/introduction). La spécification du langage est la source de référence pour la syntaxe C# et son utilisation.

## <a name="see-also"></a>Voir aussi

- <xref:System.SystemException>
- [Guide de programmation C#](../index.md)
- [Mots clés C#](../../language-reference/keywords/index.md)
- [throw](../../language-reference/keywords/throw.md)
- [try-catch](../../language-reference/keywords/try-catch.md)
- [try-finally](../../language-reference/keywords/try-finally.md)
- [try-catch-finally](../../language-reference/keywords/try-catch-finally.md)
- [Exceptions](../../../standard/exceptions/index.md)
