---
title: Utilisation d'exceptions - Guide de programmation C#
description: Découvrez comment utiliser des exceptions. Les exceptions sont levées par du code qui rencontre une erreur et interceptées par du code qui corrige l’erreur.
ms.date: 12/09/2020
helpviewer_keywords:
- exception handling [C#], about exception handling
- exceptions [C#], about exceptions
ms.assetid: 71472c62-320a-470a-97d2-67995180389d
ms.openlocfilehash: 30a7c3eecb599493dfa74d664c4899836c1b9276
ms.sourcegitcommit: 9b877e160c326577e8aa5ead22a937110d80fa44
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97110219"
---
# <a name="use-exceptions-c-programming-guide"></a>Utiliser des exceptions (Guide de programmation C#)

En C#, les erreurs qui se produisent dans le programme au moment de l’exécution sont propagées à travers le programme à l’aide du mécanisme des exceptions. Les exceptions sont levées par le code qui rencontre une erreur et interceptées par le code qui peut corriger l’erreur. Les exceptions peuvent être levées par le Runtime .NET ou par le code d’un programme. Une fois qu’une exception est levée, elle se propage jusqu’en haut de la pile des appels, jusqu’à ce qu’une instruction `catch` soit trouvée pour l’exception. Les exceptions non interceptées sont gérées par un gestionnaire d’exceptions génériques fourni par le système qui affiche une boîte de dialogue.

Les exceptions sont représentées par des classes dérivées de <xref:System.Exception>. Cette classe identifie le type d’exception et contient des propriétés comportant des détails sur l’exception. Lever une exception implique de créer une instance d’une classe dérivée d’une exception, de configurer éventuellement les propriétés de l’exception, puis de lever l’objet à l’aide du mot clé `throw`. Par exemple :

:::code language="csharp" source="snippets/exceptions/Program.cs" id="ThrowException":::

Après la levée d’une exception, le runtime vérifie l’instruction actuelle pour voir si elle se trouve dans un bloc `try`. Si tel est le cas, tous les blocs `catch` associés au bloc `try` font l’objet d’un contrôle permettant de déterminer s’ils peuvent intercepter l’exception. Les blocs `Catch` spécifient généralement des types d’exception ; si le type du bloc `catch` est identique à celui de l’exception ou d’une classe de base de l’exception, le bloc `catch` peut gérer la méthode. Par exemple :

:::code language="csharp" source="snippets/exceptions/Program.cs" id="CatchException":::

Si l’instruction qui lève une exception ne se trouve pas dans un `try` bloc ou si le `try` bloc qui l’englobe n’a pas de `catch` bloc correspondant, le runtime vérifie la méthode d’appel pour obtenir une `try` instruction et des `catch` blocs. Le runtime continue jusqu’à la pile appelante, à la recherche d’un bloc `catch` compatible. Une fois le bloc `catch` trouvé et exécuté, le contrôle est passé à l’instruction suivante après le bloc `catch`.

Une instruction `try` peut contenir plusieurs blocs `catch`. La première `catch` instruction qui peut gérer l’exception est exécutée ; toutes les `catch` instructions suivantes, même si elles sont compatibles, sont ignorées. Les blocs catch doivent toujours être classés du plus spécifique (ou le plus dérivé) au moins spécifique. Par exemple :

:::code language="csharp" source="snippets/exceptions/CatchOrder.cs":::

Avant que le bloc `catch` ne soit exécuté, le runtime vérifie la présence de blocs `finally`. `Finally` les blocs permettent au programmeur de nettoyer tout état ambigu qui peut être laissé à partir d’un `try` bloc abandonné, ou de libérer des ressources externes (telles que des handles graphiques, des connexions de base de données ou des flux de fichiers) sans attendre que le garbage collector dans le runtime finalise les objets. Par exemple :

:::code language="csharp" source="snippets/exceptions/Program.cs" id="TestFinally":::

En cas de `WriteByte()` levée d’une exception, le code du deuxième `try` bloc qui tente de rouvrir le fichier échoue si `file.Close()` n’est pas appelé, et le fichier reste verrouillé. Étant donné que les blocs `finally` sont exécutés même si une exception est levée, le bloc `finally` de l’exemple précédent autorise la fermeture correcte du fichier et permet d’éviter une erreur.

Si aucun bloc `catch` compatible n’est trouvé sur la pile des appels après la levée d’une exception, l’une des trois situations suivantes se produit :

- Si l’exception se trouve dans un finaliseur, le finaliseur est abandonné et le finaliseur de base, le cas échéant, est appelé.
- Si la pile des appels contient un constructeur statique ou un initialiseur de champ statique, une <xref:System.TypeInitializationException> est levée, avec l’exception d’origine assignée à la propriété <xref:System.Exception.InnerException%2A> de la nouvelle exception.
- Si le début du thread est atteint, le thread est terminé.
