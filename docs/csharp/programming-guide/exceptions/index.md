---
title: Exceptions et gestion des exceptions - Guide de programmation C#
description: En savoir plus sur les exceptions et la gestion des exceptions. Ces fonctionnalités C# aident à traiter les situations inattendues ou exceptionnelles qui se produisent lorsqu’un programme est en cours d’exécution.
ms.date: 12/09/2020
helpviewer_keywords:
- exception handling [C#]
- exceptions [C#]
- C# language, exceptions
ms.assetid: 0001887f-4fa2-47e2-8034-2819477e2344
ms.openlocfilehash: 679171e6d397741ef44cb37fb770f6feba039fd9
ms.sourcegitcommit: 9b877e160c326577e8aa5ead22a937110d80fa44
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97110622"
---
# <a name="exceptions-and-exception-handling-c-programming-guide"></a>Exceptions et gestion des exceptions (Guide de programmation C#)

Les fonctionnalités de gestion des exceptions du langage C# vous aident à gérer les situations inattendues ou exceptionnelles qui se produisent lorsqu’un programme est en cours d’exécution. La gestion des exceptions utilise les `try` `catch` `finally` Mots clés, et pour essayer des actions qui peuvent échouer, pour gérer les défaillances lorsque vous décidez qu’il est raisonnable de le faire et pour nettoyer les ressources par la suite. Les exceptions peuvent être générées par le common language runtime (CLR), par les bibliothèques .NET ou tierces, ou par le code d’application. Les exceptions sont créées avec le mot clé `throw`.

Dans de nombreux cas, une exception peut être levée non pas par une méthode appelée directement par votre code, mais par une autre méthode plus loin dans la pile des appels. Quand une exception est levée, le CLR déroulera la pile, en recherchant une méthode avec un `catch` bloc pour le type d’exception spécifique, et exécutera le premier bloc de ce type `catch` que if trouve. S’il ne trouve pas de bloc `catch` dans la pile des appels, il termine le processus et affiche un message à l’utilisateur.

Dans cet exemple, une méthode teste la division par zéro et intercepte l’erreur. Sans la gestion des exceptions, ce programme se terminerait avec une erreur **DivideByZeroException non gérée**.

:::code language="csharp" source="snippets/exceptions/ExceptionTest.cs" ID="ExceptionTest":::

## <a name="exceptions-overview"></a>Vue d’ensemble des exceptions

Les exceptions ont les propriétés suivantes :

- Les exceptions sont des types qui dérivent tous en définitive de `System.Exception`.
- Utilisez un bloc `try` autour des instructions qui peuvent lever des exceptions.
- Dès qu’une exception se produit dans le bloc `try`, le flux de contrôle passe immédiatement au premier gestionnaire d’exceptions associé présent dans la pile des appels. En C#, le mot clé `catch` est utilisé pour définir un gestionnaire d’exceptions.
- Si aucun gestionnaire d’exceptions n’est présent pour une exception donnée, le programme s’arrête avec un message d’erreur.
- N’interceptez pas d’exception, sauf si vous pouvez la gérer et conserver l’application dans un état connu. Si vous interceptez `System.Exception`, levez-la de nouveau avec le mot clé `throw` à la fin du bloc `catch`.
- Si un bloc `catch` définit une variable d’exception, vous pouvez l’utiliser pour obtenir plus d’informations sur le type d’exception qui s’est produit.
- Les exceptions peuvent être générées explicitement par un programme avec le mot clé `throw`.
- Les objets Exception contiennent des informations détaillées sur l'erreur, telles que l'état de la pile des appels et une description du texte de l'erreur.
- Le code qui se trouve dans un bloc `finally` est exécuté même si une exception est levée. Utilisez un bloc `finally` pour libérer des ressources, par exemple pour fermer tous les flux ou fichiers qui ont été ouverts dans le bloc `try`.
- Les exceptions managées dans .NET sont implémentées par-dessus le mécanisme de gestion structurée des exceptions Win32. Pour plus d’informations, consultez les pages [Gestion structurée des exceptions (C/C++)](/cpp/cpp/structured-exception-handling-c-cpp) et [Cours intensif sur la gestion structurée des exceptions de Win32](http://bytepointer.com/resources/pietrek_crash_course_depths_of_win32_seh.htm).

## <a name="c-language-specification"></a>Spécification du langage C#

Pour plus d’informations, consultez [Exceptions](~/_csharplang/spec/exceptions.md) dans la [Spécification du langage C#](/dotnet/csharp/language-reference/language-specification/introduction). La spécification du langage est la source de référence pour la syntaxe C# et son utilisation.

## <a name="see-also"></a>Voir aussi

- <xref:System.SystemException>
- [Mots clés C#](../../language-reference/keywords/index.md)
- [lever](../../language-reference/keywords/throw.md)
- [try-catch](../../language-reference/keywords/try-catch.md)
- [try-finally](../../language-reference/keywords/try-finally.md)
- [try-catch-finally](../../language-reference/keywords/try-catch-finally.md)
- [Exceptions](../../../standard/exceptions/index.md)
