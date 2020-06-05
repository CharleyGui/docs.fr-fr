---
title: Essayer... Catch... Finally, instruction
description: Apprenez à utiliser la gestion des exceptions avec Visual Basic instructions try/catch/finally.
ms.date: 12/07/2018
f1_keywords:
- vb.Try...Catch...Finally
- vb.when
- vb.Finally
- vb.Catch
- vb.Try
helpviewer_keywords:
- Try...Catch...Finally statements
- Try statement [Visual Basic]
- try-catch exception handling, Try...Catch...Finally statements
- error handling, while running code
- Try statement [Visual Basic], Try...Catch...Finally
- Finally keyword [Visual Basic], Try...Catch...Finally
- Catch statement [Visual Basic]
- When keyword [Visual Basic]
- Visual Basic code, handling errors while running
- structured exception handling, Try...Catch...Finally statements
ms.assetid: d6488026-ccb3-42b8-a810-0d97b9d6472b
ms.openlocfilehash: 22f1611786a3da512632b5b547b7ef141c8f65c6
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84391766"
---
# <a name="trycatchfinally-statement-visual-basic"></a>Try...Catch...Finally, instruction (Visual Basic)

Fournit un moyen de gérer certaines ou toutes les erreurs possibles qui peuvent se produire dans un bloc de code donné, tout en continuant d’exécuter du code.

## <a name="syntax"></a>Syntaxe

```vb
Try
    [ tryStatements ]
    [ Exit Try ]
[ Catch [ exception [ As type ] ] [ When expression ]
    [ catchStatements ]
    [ Exit Try ] ]
[ Catch ... ]
[ Finally
    [ finallyStatements ] ]
End Try
```

## <a name="parts"></a>Éléments

|Terme|Définition|
|---|---|
|`tryStatements`|Facultatif. Instruction (s) où une erreur peut se produire. Il peut s'agir d'une instruction composée.|
|`Catch`|Facultatif. `Catch`Blocs multiples autorisés. Si une exception se produit lors du traitement du `Try` bloc, chaque `Catch` instruction est examinée dans l’ordre textuel pour déterminer si elle gère l’exception, avec `exception` représentant l’exception qui a été levée.|
|`exception`|Facultatif. Tout nom de variable. La valeur initiale de l'argument `exception` est la valeur de l'erreur levée. Utilisé avec `Catch` pour spécifier l’erreur interceptée. En cas d’omission, l' `Catch` instruction intercepte toute exception.|
|`type`|Facultatif. Spécifie le type de filtre de classe. Si la valeur de `exception` est du type spécifié par `type` ou d’un type dérivé, l’identificateur est lié à l’objet d’exception.|
|`When`|Facultatif. Une `Catch` instruction avec une `When` clause intercepte les exceptions uniquement lorsque a la `expression` valeur `True` . Une `When` clause est appliquée uniquement après avoir vérifié le type de l’exception et `expression` peut faire référence à l’identificateur représentant l’exception.|
|`expression`|Facultatif. Doit être implicitement convertible en `Boolean` . Toute expression qui décrit un filtre générique. Généralement utilisé pour filtrer par numéro d’erreur. Utilisé avec `When` le mot clé pour spécifier les circonstances dans lesquelles l’erreur est interceptée.|
|`catchStatements`|Facultatif. Instruction (s) pour gérer les erreurs qui se produisent dans le `Try` bloc associé. Il peut s'agir d'une instruction composée.|
|`Exit Try`|Facultatif. Mot clé qui s’arrête hors de la `Try...Catch...Finally` structure. L’exécution reprend avec le code qui suit immédiatement l' `End Try` instruction. L' `Finally` instruction est toujours exécutée. Non autorisé dans les `Finally` blocs.|
|`Finally`|Facultatif. Un `Finally` bloc est toujours exécuté lorsque l’exécution quitte une partie de l' `Try...Catch` instruction.|
|`finallyStatements`|Facultatif. Instruction (s) qui sont exécutées une fois que toutes les autres opérations de traitement des erreurs se sont produites.|
|`End Try`|Met fin à la `Try...Catch...Finally` structure.|

## <a name="remarks"></a>Notes

Si vous vous attendez à ce qu’une exception particulière se produise au cours d’une section de code particulière, placez le code dans un `Try` bloc et utilisez un `Catch` bloc pour conserver le contrôle et gérer l’exception, le cas échéant.

Une `Try…Catch` instruction se compose d’un `Try` bloc suivi d’une ou `Catch` de plusieurs clauses, qui spécifient des gestionnaires pour différentes exceptions. Quand une exception est levée dans un `Try` bloc, Visual Basic recherche l' `Catch` instruction qui gère l’exception. Si une `Catch` instruction correspondante est introuvable, Visual Basic examine la méthode qui a appelé la méthode actuelle, et ainsi de suite la pile des appels. Si aucun `Catch` bloc n’est trouvé, Visual Basic affiche un message d’exception non gérée à l’utilisateur et arrête l’exécution du programme.

Vous pouvez utiliser plusieurs `Catch` instructions dans une `Try…Catch` instruction. Dans ce cas, l’ordre des `Catch` clauses est significatif, car ils sont examinés dans l’ordre. Interceptez les exceptions plus spécifiques avant les moins spécifiques.

Les `Catch` conditions d’instruction suivantes sont les moins spécifiques et interceptent toutes les exceptions qui dérivent de la <xref:System.Exception> classe. En principe, vous devez utiliser l’une de ces variations comme dernier `Catch` bloc de la `Try...Catch...Finally` structure, après avoir intercepté toutes les exceptions spécifiques que vous attendez. Le workflow de contrôle ne peut jamais atteindre un `Catch` bloc qui suit l’une de ces variantes.

- `type`Est `Exception` , par exemple :`Catch ex As Exception`

- L’instruction n’a pas `exception` de variable, par exemple :`Catch`

Lorsqu’une `Try…Catch…Finally` instruction est imbriquée dans un autre `Try` bloc, Visual Basic examine d’abord chaque `Catch` instruction dans le bloc le plus profond `Try` . Si aucune `Catch` instruction correspondante n’est trouvée, la recherche se poursuit sur les `Catch` instructions du `Try…Catch…Finally` bloc externe.

Les variables locales d’un `Try` bloc ne sont pas disponibles dans un `Catch` bloc, car il s’agit de blocs distincts. Si vous souhaitez utiliser une variable dans plusieurs blocs, déclarez la variable en dehors de la `Try...Catch...Finally` structure.

> [!TIP]
> L' `Try…Catch…Finally` instruction est disponible sous la forme d’un extrait de code IntelliSense. Dans le gestionnaire des extraits de code, développez **modèles de code-If, for each, try catch, Property, etc**, puis la **gestion des erreurs (exceptions)**. Pour plus d’informations, consultez [Extraits de code](/visualstudio/ide/code-snippets).

## <a name="finally-block"></a>Finally (bloc)

Si vous avez une ou plusieurs instructions qui doivent s’exécuter avant de quitter la `Try` structure, utilisez un `Finally` bloc. Le contrôle est passé au `Finally` bloc juste avant qu’il ne soit en dehors de la `Try…Catch` structure. Cela est vrai même si une exception se produit n’importe où dans la `Try` structure.

Un `Finally` bloc est utile pour exécuter tout code qui doit s’exécuter même en cas d’exception. Le contrôle est passé au `Finally` bloc, quelle que soit la façon dont le `Try...Catch` bloc s’arrête.

Le code d’un `Finally` bloc s’exécute même si votre code rencontre une `Return` instruction dans un `Try` bloc ou `Catch` . Le contrôle ne passe pas d' `Try` un `Catch` bloc ou au `Finally` bloc correspondant dans les cas suivants :

- Une [instruction end](end-statement.md) est rencontrée dans `Try` le `Catch` bloc ou.

- Une <xref:System.StackOverflowException> est levée dans le `Try` `Catch` bloc ou.

Il n’est pas possible de transférer explicitement l’exécution dans un `Finally` bloc. Le transfert de l’exécution en dehors d’un `Finally` bloc n’est pas valide, sauf par le biais d’une exception.

Si une `Try` instruction ne contient pas au moins un `Catch` bloc, elle doit contenir un `Finally` bloc.

> [!TIP]
> Si vous n’avez pas besoin d’intercepter des exceptions spécifiques, l' `Using` instruction se comporte comme un `Try…Finally` bloc et garantit la suppression des ressources, quelle que soit la façon dont vous quittez le bloc. Cela est vrai même avec une exception non gérée. Pour plus d’informations, consultez [using, instruction](using-statement.md).

## <a name="exception-argument"></a>Argument d’exception

L' `Catch` `exception` argument de bloc est une instance de la <xref:System.Exception> classe ou une classe qui dérive de la `Exception` classe. L' `Exception` instance de classe correspond à l’erreur qui s’est produite dans le `Try` bloc.

Les propriétés de l' `Exception` objet permettent d’identifier la cause et l’emplacement d’une exception. Par exemple, la <xref:System.Exception.StackTrace%2A> propriété répertorie les méthodes appelées qui ont conduit à l’exception, ce qui vous permet de trouver où l’erreur s’est produite dans le code. <xref:System.Exception.Message%2A>retourne un message qui décrit l’exception. <xref:System.Exception.HelpLink%2A>retourne un lien vers un fichier d’aide associé. <xref:System.Exception.InnerException%2A>retourne l' `Exception` objet qui a provoqué l’exception actuelle, ou retourne `Nothing` s’il n’y a pas d’objet d’origine `Exception` .

## <a name="considerations-when-using-a-trycatch-statement"></a>Considérations à prendre en compte lors de l’utilisation d’un bloc try... Catch (instruction)

Utilisez une `Try…Catch` instruction uniquement pour signaler l’occurrence d’événements de programme inattendus ou imprévus. Les raisons sont les suivantes :

- L’interception des exceptions au moment de l’exécution crée une surcharge supplémentaire et est susceptible d’être plus lente que la pré-vérification pour éviter les exceptions.

- Si un `Catch` bloc n’est pas géré correctement, l’exception peut ne pas être signalée correctement aux utilisateurs.

- La gestion des exceptions rend un programme plus complexe.

Vous n’avez pas toujours besoin `Try…Catch` d’une instruction pour vérifier une condition qui est susceptible de se produire. L’exemple suivant vérifie si un fichier existe avant d’essayer de l’ouvrir. Cela réduit le besoin d’intercepter une exception levée par la <xref:System.IO.File.OpenText%2A> méthode.

[!code-vb[VbVbalrStatements#94](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#94)]

Assurez-vous que le code des `Catch` blocs peut signaler correctement les exceptions aux utilisateurs, que ce soit via une journalisation thread-safe ou des messages appropriés. Sinon, les exceptions peuvent rester inconnues.

## <a name="async-methods"></a>Méthodes Async

Si vous marquez une méthode avec le modificateur [Async](../modifiers/async.md) , vous pouvez utiliser l’opérateur [await](../operators/await-operator.md) dans la méthode. Une instruction avec l' `Await` opérateur interrompt l’exécution de la méthode jusqu’à ce que la tâche attendue se termine. La tâche représente un travail en cours. Lorsque la tâche associée à l’opérateur se `Await` termine, l’exécution reprend dans la même méthode. Pour plus d’informations, consultez [Control flow in Async Programs](../../programming-guide/concepts/async/control-flow-in-async-programs.md).

Une tâche retournée par une méthode Async peut se terminer par un état d’erreur, ce qui indique qu’elle s’est terminée en raison d’une exception non gérée. Une tâche peut également se terminer par un état annulé, ce qui entraîne `OperationCanceledException` la levée d’une exception dans l’expression await. Pour intercepter l’un ou l’autre type d’exception, placez l' `Await` expression associée à la tâche dans un `Try` bloc, puis interceptez l’exception dans le `Catch` bloc. Un exemple est fourni plus loin dans cette rubrique.

Une tâche peut être dans un état d’erreur, car plusieurs exceptions étaient responsables de son erreur. Par exemple, la tâche peut être le résultat d'un appel à <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType>. Lorsque vous attendez une telle tâche, l’exception interceptée n’est qu’une des exceptions, et vous ne pouvez pas prédire l’exception qui sera interceptée. Un exemple est fourni plus loin dans cette rubrique.

Une `Await` expression ne peut pas se trouver à l’intérieur d’un `Catch` bloc ou d’un `Finally` bloc.

## <a name="iterators"></a>Iterators

Une fonction ou un `Get` accesseur d’itérateur effectue une itération personnalisée sur une collection. Un itérateur utilise une instruction [yield](yield-statement.md) pour retourner chaque élément de la collection un par un. Vous appelez une fonction d’itérateur à l’aide [d’un pour chaque... Instruction suivante](for-each-next-statement.md).

Une `Yield` instruction peut se trouver à l’intérieur d’un `Try` bloc. Un `Try` bloc qui contient une `Yield` instruction peut avoir des `Catch` blocs et peut avoir un `Finally` bloc. Pour obtenir un exemple, consultez la section « blocs try dans Visual Basic » d' [itérateurs](../../programming-guide/concepts/iterators.md) .

Une `Yield` instruction ne peut pas être à l’intérieur d’un `Catch` bloc ou d’un `Finally` bloc.

Si le `For Each` corps (en dehors de la fonction d’itérateur) lève une exception, un `Catch` bloc de la fonction d’itérateur n’est pas exécuté, mais un `Finally` bloc dans la fonction d’itérateur est exécuté. Un `Catch` bloc à l’intérieur d’une fonction d’itérateur intercepte uniquement les exceptions qui se produisent à l’intérieur de la fonction Iterator.

## <a name="partial-trust-situations"></a>Situations de confiance partielle

Dans les situations de confiance partielle, telles qu’une application hébergée sur un partage réseau, `Try...Catch...Finally` n’intercepte pas les exceptions de sécurité qui se produisent avant l’appel de la méthode qui contient l’appel. L’exemple suivant, quand vous le placez sur un partage de serveur et que vous exécutez à partir de là, génère l’erreur « System. Security. SecurityException : échec de la demande ». Pour plus d’informations sur les exceptions de sécurité, consultez la <xref:System.Security.SecurityException> classe.

[!code-vb[VbVbalrStatements#85](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#85)]

Dans une telle situation de confiance partielle, vous devez placer l' `Process.Start` instruction dans un distinct `Sub` . L’appel initial à l' `Sub` opération échoue. Cela permet `Try...Catch` à de l’intercepter avant `Sub` que le qui contient `Process.Start` ne démarre et que l’exception de sécurité soit produite.

## <a name="examples"></a>Exemples

### <a name="the-structure-of-trycatchfinally"></a>Structure de try... Catch... Suivie

L’exemple suivant illustre la structure de l' `Try...Catch...Finally` instruction.

[!code-vb[VbVbalrStatements#86](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#86)]  

### <a name="exception-in-a-method-called-from-a-try-block"></a>Exception dans une méthode appelée à partir d’un bloc try

Dans l’exemple suivant, la `CreateException` méthode lève une exception `NullReferenceException` . Le code qui génère l’exception n’est pas dans un `Try` bloc. Par conséquent, la `CreateException` méthode ne gère pas l’exception. La `RunSample` méthode gère l’exception, car l’appel à la `CreateException` méthode se trouve dans un `Try` bloc.

L’exemple comprend `Catch` des instructions pour plusieurs types d’exceptions, classées du plus spécifique au plus général.

[!code-vb[VbVbalrStatements#91](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#91)]

### <a name="the-catch-when-statement"></a>Instruction catch when

L’exemple suivant montre comment utiliser une `Catch When` instruction pour filtrer sur une expression conditionnelle. Si l’expression conditionnelle a la valeur `True` , le code du `Catch` bloc s’exécute.

[!code-vb[VbVbalrStatements#92](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#92)]

### <a name="nested-try-statements"></a>Instructions Try imbriquées

L’exemple suivant contient une `Try…Catch` instruction contenue dans un `Try` bloc. Le `Catch` bloc interne lève une exception dont `InnerException` la propriété a la valeur de l’exception d’origine. Le `Catch` bloc externe signale sa propre exception et l’exception interne.

[!code-vb[VbVbalrStatements#93](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#93)]

### <a name="exception-handling-for-async-methods"></a>Gestion des exceptions pour les méthodes Async

L'exemple suivant illustre la gestion des exceptions pour les méthodes async. Pour intercepter une exception qui s’applique à une tâche asynchrone, l' `Await` expression se trouve dans un `Try` bloc de l’appelant et l’exception est interceptée dans le `Catch` bloc.

Supprimez les marques de commentaire de la ligne `Throw New Exception` dans l'exemple pour illustrer la gestion des exceptions. L’exception est interceptée dans le `Catch` bloc, la propriété de la tâche `IsFaulted` a la valeur et la `True` propriété de la tâche `Exception.InnerException` a la valeur de l’exception.

Supprimez les marques de commentaire de la ligne `Throw New OperationCancelledException` pour montrer ce qui se passe quand vous annulez un processus asynchrone. L’exception est interceptée dans le `Catch` bloc et la propriété de la tâche `IsCanceled` a la valeur `True` . Toutefois, dans certaines conditions qui ne s’appliquent pas à cet exemple, `IsFaulted` a la valeur `True` et `IsCanceled` a la valeur `False` .

[!code-vb[csAsyncExceptions#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/csasyncexceptions/vb/class1.vb#1)]

### <a name="handling-multiple-exceptions-in-async-methods"></a>Gestion de plusieurs exceptions dans les méthodes Async

L’exemple suivant illustre la gestion des exceptions quand plusieurs tâches peuvent entraîner plusieurs exceptions. Le `Try` bloc a l' `Await` expression de la tâche qui a été <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType> retournée. La tâche est terminée lorsque les trois tâches auxquelles <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType> est appliqué sont terminées.

Chacune de ces trois tâches provoque une exception. Le `Catch` bloc itère au sein des exceptions, qui se trouvent dans la `Exception.InnerExceptions` propriété de la tâche `Task.WhenAll` retournée.

[!code-vb[csAsyncExceptions#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/csasyncexceptions/vb/class1.vb#3)]

## <a name="see-also"></a>Voir aussi

- <xref:Microsoft.VisualBasic.Information.Err%2A>
- <xref:System.Exception>
- [Exit (instruction)](exit-statement.md)
- [On Error (instruction)](on-error-statement.md)
- [Bonnes pratiques pour l’utilisation des extraits de code](/visualstudio/ide/best-practices-for-using-code-snippets)
- [Gestion des exceptions](../../../standard/parallel-programming/exception-handling-task-parallel-library.md)
- [Throw (instruction)](throw-statement.md)
