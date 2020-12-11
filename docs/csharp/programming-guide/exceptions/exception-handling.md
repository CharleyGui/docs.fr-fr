---
title: Gestion des exceptions - Guide de programmation C#
description: En savoir plus sur la gestion des exceptions. Consultez des exemples d’instructions Try-Catch, try-finally et try-catch-finally.
ms.date: 12/09/2020
helpviewer_keywords:
- exception handling [C#], about exception handling
- exceptions [C#], handling
ms.assetid: b4e4ecf2-b907-4e58-891f-2563762258e9
ms.openlocfilehash: fabf1413ba498232e67f45460195fe96e25fab0a
ms.sourcegitcommit: 9b877e160c326577e8aa5ead22a937110d80fa44
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97110193"
---
# <a name="exception-handling-c-programming-guide"></a>Gestion des exceptions (Guide de programmation C#)

Un bloc [try](../../language-reference/keywords/try-catch.md) est utilisé par les programmeurs C# pour partitionner du code susceptible d’être affecté par une exception. Des blocs [catch](../../language-reference/keywords/try-catch.md) associés sont utilisés pour gérer les exceptions générées. Un bloc [finally](../../language-reference/keywords/try-finally.md) contient du code qui est exécuté, qu’une exception soit levée ou non dans le `try` bloc, par exemple la libération de ressources qui sont allouées dans le `try` bloc. Un bloc `try` doit être associé à un ou plusieurs blocs `catch`, à un bloc `finally`, ou aux deux.

Les exemples suivants montrent une instruction `try-catch`, une instruction `try-finally` et une instruction `try-catch-finally`.

:::code language="csharp" source="snippets/exceptions/Program.cs" id="TryCatchStructure":::

:::code language="csharp" source="snippets/exceptions/Program.cs" id="TryFinallyStructure":::

:::code language="csharp" source="snippets/exceptions/Program.cs" id="TryCatchFinallyStructure":::

Un bloc `try` sans bloc `catch` ou `finally` provoque une erreur du compilateur.

## <a name="catch-blocks"></a>Blocs catch

Un bloc `catch` peut spécifier le type d’exception à intercepter. La spécification de type est appelée *filtre d’exception*. Le type d’exception doit être dérivé de <xref:System.Exception>. En général, ne spécifiez pas <xref:System.Exception> comme filtre d’exception, sauf si vous savez comment gérer toutes les exceptions susceptibles d’être levées dans le `try` bloc ou si vous avez inclus une instruction [throw](../../language-reference/keywords/throw.md) à la fin de votre `catch` bloc.

Plusieurs `catch` blocs avec différentes classes d’exception peuvent être chaînés ensemble. Les blocs `catch` sont évalués de haut en bas dans votre code, mais un seul bloc `catch` est exécuté pour chaque exception levée. Le premier bloc `catch` qui spécifie le type exact ou une classe de base de l’exception levée est exécuté. Si aucun `catch` bloc ne spécifie une classe d’exception correspondante, un `catch` bloc qui n’a pas de type est sélectionné, s’il est présent dans l’instruction. Il est important de placer `catch` les blocs avec les classes d’exception les plus spécifiques (autrement dit, les plus dérivées).

Interceptez les exceptions lorsque les conditions suivantes sont vraies :

- Vous savez pourquoi l’exception a été levée et vous pouvez implémenter une récupération spécifique, par exemple inviter l’utilisateur à entrer un nouveau nom de fichier quand vous interceptez un objet <xref:System.IO.FileNotFoundException>.
- Vous pouvez créer et lever une nouvelle exception plus spécifique.
  :::code language="csharp" source="snippets/exceptions/Program.cs" id="ThrowMoreSpecificException":::
- Vous voulez traiter partiellement une exception avant de la transmettre en vue d’un traitement supplémentaire. Dans l’exemple suivant, un `catch` bloc est utilisé pour ajouter une entrée à un journal des erreurs avant de lever à nouveau l’exception.
  :::code language="csharp" source="snippets/exceptions/Program.cs" id="RethrowError":::

Vous pouvez également spécifier des *filtres d’exception* pour ajouter une expression booléenne à une clause catch. Ils indiquent qu’une clause catch spécifique correspond uniquement lorsque cette condition est vraie. Dans l’exemple suivant, les deux clauses catch utilisent la même classe d’exception, mais une condition supplémentaire est vérifiée pour créer un autre message d’erreur :

:::code language="csharp" source="snippets/exceptions/ExceptionFilter.cs" ID="DemonstrateExceptionFilter":::

Un filtre d’exception qui retourne toujours `false` peut être utilisé pour examiner toutes les exceptions, mais ne pas les traiter. Une utilisation courante consiste à enregistrer les exceptions :

:::code language="csharp" source="snippets/exceptions/ExceptionFilter.cs" ID="ShowExceptionFilter":::

La `LogException` méthode retourne toujours `false` , aucune `catch` clause utilisant ce filtre d’exception ne correspond à. La clause catch peut être générale, l’utilisation de <xref:System.Exception?displayProperty=nameWithType> et les clauses ultérieures peuvent traiter des classes d’exception plus spécifiques.

## <a name="finally-blocks"></a>Blocs Finally

Un bloc `finally` vous permet de nettoyer les actions qui sont exécutées dans un bloc `try`. S’il est présent, le bloc `finally` s’exécute en dernier, après le bloc `try` et tout bloc `catch` mis en correspondance. Un `finally` bloc s’exécute toujours, qu’une exception soit levée ou qu’un `catch` bloc correspondant au type d’exception soit trouvé.

Le bloc `finally` peut être utilisé pour libérer des ressources telles que des flux de fichiers, des connexions de base de données et des handles graphiques, sans attendre que le récupérateur de mémoire dans le runtime finalise les objets. Pour plus d’informations, consultez l' [instruction using](../../language-reference/keywords/using-statement.md).

Dans l’exemple suivant, le bloc `finally` est utilisé pour fermer un fichier ouvert dans le bloc `try`. Notez que l’état du handle de fichier est vérifié avant la fermeture du fichier. Si le `try` bloc ne peut pas ouvrir le fichier, le descripteur de fichier a toujours la valeur `null` et le `finally` bloc ne tente pas de le fermer. Au lieu de cela, si le fichier est ouvert avec succès dans le `try` bloc, le `finally` bloc ferme le fichier ouvert.

:::code language="csharp" source="snippets/exceptions/Program.cs" id="CleanupIfNotNull":::

## <a name="c-language-specification"></a>Spécification du langage C#

Pour plus d’informations, consultez [Exceptions](~/_csharplang/spec/exceptions.md) et [Instruction try](~/_csharplang/spec/statements.md#the-try-statement) dans la [spécification du langage C#](/dotnet/csharp/language-reference/language-specification/introduction). La spécification du langage est la source de référence pour la syntaxe C# et son utilisation.
  
## <a name="see-also"></a>Voir aussi

- [Référence C#](../../language-reference/index.md)
- [try-catch](../../language-reference/keywords/try-catch.md)
- [try-finally](../../language-reference/keywords/try-finally.md)
- [try-catch-finally](../../language-reference/keywords/try-catch-finally.md)
- [using, instruction](../../language-reference/keywords/using-statement.md)
