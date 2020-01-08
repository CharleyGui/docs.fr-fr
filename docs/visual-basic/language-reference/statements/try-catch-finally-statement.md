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
ms.custom: seodec18
ms.openlocfilehash: eb04b6cff0847009407e38a3696e9be7c700356c
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/25/2019
ms.locfileid: "75337332"
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

## <a name="parts"></a>Parties

|Terme|Définition|
|---|---|
|`tryStatements`|Option facultative. Instruction (s) où une erreur peut se produire. Il peut s'agir d'une instruction composée.|
|`Catch`|Option facultative. Plusieurs blocs de `Catch` autorisés. Si une exception se produit lors du traitement du bloc `Try`, chaque instruction `Catch` est examinée dans l’ordre textuel pour déterminer si elle gère l’exception, avec `exception` représentant l’exception qui a été levée.|
|`exception`|Option facultative. Tout nom de variable. La valeur initiale de l'argument `exception` est la valeur de l'erreur levée. Utilisé avec `Catch` pour spécifier l’erreur interceptée. En cas d’omission, l’instruction `Catch` intercepte toute exception.|
|`type`|Option facultative. Spécifie le type de filtre de classe. Si la valeur de `exception` est du type spécifié par `type` ou d’un type dérivé, l’identificateur est lié à l’objet d’exception.|
|`When`|Option facultative. Une instruction `Catch` avec une clause `When` intercepte les exceptions uniquement lorsque `expression` prend la valeur `True`. Une clause `When` est appliquée uniquement après avoir vérifié le type de l’exception, et `expression` peut faire référence à l’identificateur représentant l’exception.|
|`expression`|Option facultative. Doit être implicitement convertible en `Boolean`. Toute expression qui décrit un filtre générique. Généralement utilisé pour filtrer par numéro d’erreur. Utilisé avec `When` mot clé pour spécifier les circonstances dans lesquelles l’erreur est interceptée.|
|`catchStatements`|Option facultative. Instruction (s) pour gérer les erreurs qui se produisent dans le bloc de `Try` associé. Il peut s'agir d'une instruction composée.|
|`Exit Try`|Option facultative. Mot clé qui sort de la structure `Try...Catch...Finally`. L’exécution reprend avec le code qui suit immédiatement l’instruction `End Try`. L’instruction `Finally` est toujours exécutée. Non autorisé dans les blocs `Finally`.|
|`Finally`|Option facultative. Un bloc `Finally` est toujours exécuté lorsque l’exécution quitte une partie de l’instruction `Try...Catch`.|
|`finallyStatements`|Option facultative. Instruction (s) qui sont exécutées une fois que toutes les autres opérations de traitement des erreurs se sont produites.|
|`End Try`|Met fin à la structure `Try...Catch...Finally`.|

## <a name="remarks"></a>Notes

Si vous vous attendez à ce qu’une exception particulière se produise pendant une section de code particulière, placez le code dans un bloc `Try` et utilisez un bloc `Catch` pour conserver le contrôle et gérer l’exception, le cas échéant.

Une instruction `Try…Catch` se compose d’un bloc `Try` suivi d’une ou plusieurs clauses `Catch`, qui spécifient des gestionnaires pour différentes exceptions. Quand une exception est levée dans un bloc `Try`, Visual Basic recherche l’instruction `Catch` qui gère l’exception. Si une instruction `Catch` correspondante est introuvable, Visual Basic examine la méthode qui a appelé la méthode actuelle, et ainsi de suite la pile des appels. Si aucun bloc de `Catch` n’est trouvé, Visual Basic affiche un message d’exception non gérée à l’utilisateur et arrête l’exécution du programme.

Vous pouvez utiliser plusieurs instructions `Catch` dans une instruction `Try…Catch`. Dans ce cas, l’ordre des clauses de `Catch` est significatif, car ils sont examinés dans l’ordre. Interceptez les exceptions plus spécifiques avant les moins spécifiques.

Les conditions d’instruction `Catch` suivantes sont les moins spécifiques et interceptent toutes les exceptions qui dérivent de la classe <xref:System.Exception>. En général, vous devez utiliser l’une de ces variations comme dernier bloc de `Catch` dans la structure de `Try...Catch...Finally`, après avoir intercepté toutes les exceptions spécifiques que vous attendez. Le workflow de contrôle ne peut jamais atteindre un bloc de `Catch` qui suit l’une de ces variantes.

- Le `type` est `Exception`, par exemple : `Catch ex As Exception`

- L’instruction n’a pas de variable `exception`, par exemple : `Catch`

Lorsqu’une instruction `Try…Catch…Finally` est imbriquée dans un autre bloc `Try`, Visual Basic examine d’abord chaque instruction `Catch` dans le bloc `Try` le plus profond. Si aucune instruction `Catch` correspondante n’est trouvée, la recherche passe aux instructions `Catch` du bloc `Try…Catch…Finally` externe.

Les variables locales d’un bloc de `Try` ne sont pas disponibles dans un bloc `Catch`, car il s’agit de blocs distincts. Si vous souhaitez utiliser une variable dans plusieurs blocs, déclarez la variable en dehors de la structure `Try...Catch...Finally`.

> [!TIP]
> L’instruction `Try…Catch…Finally` est disponible sous la forme d’un extrait de code IntelliSense. Dans le gestionnaire des extraits de code, développez **modèles de code-If, for each, try catch, Property, etc**, puis la **gestion des erreurs (exceptions)** . Pour plus d'informations, consultez [Code Snippets](/visualstudio/ide/code-snippets).

## <a name="finally-block"></a>Finally (bloc)

Si vous avez une ou plusieurs instructions qui doivent s’exécuter avant de quitter la structure `Try`, utilisez un bloc `Finally`. Le contrôle passe au bloc `Finally` juste avant qu’il ne soit en dehors de la structure `Try…Catch`. Cela est vrai même si une exception se produit n’importe où dans la structure `Try`.

Un bloc `Finally` est utile pour exécuter tout code qui doit s’exécuter même en cas d’exception. Le contrôle est passé au bloc `Finally`, quelle que soit la façon dont le bloc `Try...Catch` s’arrête.

Le code d’un bloc `Finally` s’exécute même si votre code rencontre une instruction `Return` dans un bloc `Try` ou `Catch`. Le contrôle ne passe pas d’un bloc `Try` ou `Catch` au bloc `Finally` correspondant dans les cas suivants :

- Une [instruction end](end-statement.md) est rencontrée dans le bloc `Try` ou `Catch`.

- Une <xref:System.StackOverflowException> est levée dans le bloc `Try` ou `Catch`.

Il n’est pas possible de transférer explicitement l’exécution dans un bloc `Finally`. Le transfert de l’exécution en dehors d’un bloc de `Finally` n’est pas valide, sauf par le biais d’une exception.

Si une instruction `Try` ne contient pas au moins un bloc `Catch`, elle doit contenir un bloc `Finally`.

> [!TIP]
> Si vous n’avez pas besoin d’intercepter des exceptions spécifiques, l’instruction `Using` se comporte comme un bloc `Try…Finally` et garantit la suppression des ressources, quelle que soit la façon dont vous quittez le bloc. Cela est vrai même avec une exception non gérée. Pour plus d’informations, consultez [using, instruction](using-statement.md).

## <a name="exception-argument"></a>Argument d’exception

L’argument de `exception` de bloc `Catch` est une instance de la classe <xref:System.Exception> ou une classe qui dérive de la classe `Exception`. L’instance de la classe `Exception` correspond à l’erreur qui s’est produite dans le bloc `Try`.

Les propriétés de l’objet `Exception` permettent d’identifier la cause et l’emplacement d’une exception. Par exemple, la propriété <xref:System.Exception.StackTrace%2A> répertorie les méthodes appelées qui ont conduit à l’exception, ce qui vous permet de trouver où l’erreur s’est produite dans le code. <xref:System.Exception.Message%2A> retourne un message décrivant l’exception. <xref:System.Exception.HelpLink%2A> retourne un lien vers un fichier d’aide associé. <xref:System.Exception.InnerException%2A> retourne l’objet `Exception` à l’origine de l’exception actuelle ou retourne `Nothing` s’il n’y a pas de `Exception`d’origine.

## <a name="considerations-when-using-a-trycatch-statement"></a>Considérations à prendre en compte lors de l’utilisation d’un bloc try... Catch (instruction)

Utilisez une instruction `Try…Catch` uniquement pour signaler l’occurrence d’événements de programme inhabituels ou imprévus. Les raisons sont les suivantes :

- L’interception des exceptions au moment de l’exécution crée une surcharge supplémentaire et est susceptible d’être plus lente que la pré-vérification pour éviter les exceptions.

- Si un bloc de `Catch` n’est pas géré correctement, l’exception peut ne pas être signalée correctement aux utilisateurs.

- La gestion des exceptions rend un programme plus complexe.

Vous n’avez pas toujours besoin d’une instruction `Try…Catch` pour vérifier une condition qui est susceptible de se produire. L’exemple suivant vérifie si un fichier existe avant d’essayer de l’ouvrir. Cela réduit le besoin d’intercepter une exception levée par la méthode <xref:System.IO.File.OpenText%2A>.

[!code-vb[VbVbalrStatements#94](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#94)]

Assurez-vous que le code des blocs `Catch` peut signaler correctement les exceptions aux utilisateurs, que ce soit via une journalisation thread-safe ou des messages appropriés. Sinon, les exceptions peuvent rester inconnues.

## <a name="async-methods"></a>Méthodes Async

Si vous marquez une méthode avec le modificateur [Async](../modifiers/async.md) , vous pouvez utiliser l’opérateur [await](../operators/await-operator.md) dans la méthode. Une instruction avec l’opérateur `Await` interrompt l’exécution de la méthode jusqu’à ce que la tâche attendue se termine. La tâche représente un travail en cours. Lorsque la tâche associée à l’opérateur `Await` se termine, l’exécution reprend dans la même méthode. Pour plus d’informations, consultez [Control flow in Async Programs](../../../visual-basic/programming-guide/concepts/async/control-flow-in-async-programs.md).

Une tâche retournée par une méthode Async peut se terminer par un état d’erreur, ce qui indique qu’elle s’est terminée en raison d’une exception non gérée. Une tâche peut également se terminer par un état d’annulation, ce qui entraîne la levée d’une `OperationCanceledException` en dehors de l’expression await. Pour intercepter l’un ou l’autre type d’exception, placez l’expression `Await` associée à la tâche dans un bloc `Try`, puis interceptez l’exception dans le bloc `Catch`. Un exemple est fourni plus loin dans cette rubrique.

Une tâche peut être dans un état d’erreur, car plusieurs exceptions étaient responsables de son erreur. Par exemple, la tâche peut être le résultat d'un appel à <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType>. Lorsque vous attendez une telle tâche, l’exception interceptée n’est qu’une des exceptions, et vous ne pouvez pas prédire l’exception qui sera interceptée. Un exemple est fourni plus loin dans cette rubrique.

Une expression `Await` ne peut pas se trouver à l’intérieur d’un bloc `Catch` ou d’un bloc `Finally`.

## <a name="iterators"></a>Iterators

Une fonction d’itérateur ou un accesseur `Get` effectue une itération personnalisée sur une collection. Un itérateur utilise une instruction [yield](yield-statement.md) pour retourner chaque élément de la collection un par un. Vous appelez une fonction d’itérateur à l’aide [d’un pour chaque... Instruction suivante](for-each-next-statement.md).

Une instruction `Yield` peut se trouver à l’intérieur d’un bloc `Try`. Un bloc `Try` qui contient une instruction `Yield` peut avoir des blocs `Catch` et peut avoir un bloc `Finally`. Pour obtenir un exemple, consultez la section « blocs try dans Visual Basic » d' [itérateurs](../../programming-guide/concepts/iterators.md) .

Une instruction `Yield` ne peut pas se trouver à l’intérieur d’un bloc `Catch` ou d’un bloc `Finally`.

Si le corps de `For Each` (en dehors de la fonction d’itérateur) lève une exception, un bloc `Catch` dans la fonction d’itérateur n’est pas exécuté, mais un bloc `Finally` dans la fonction d’itérateur est exécuté. Un bloc de `Catch` à l’intérieur d’une fonction d’itérateur intercepte uniquement les exceptions qui se produisent à l’intérieur de la fonction d’itérateur.

## <a name="partial-trust-situations"></a>Situations de confiance partielle

Dans les situations de confiance partielle, telles qu’une application hébergée sur un partage réseau, `Try...Catch...Finally` n’intercepte pas les exceptions de sécurité qui se produisent avant l’appel de la méthode qui contient l’appel. L’exemple suivant, quand vous le placez sur un partage de serveur et que vous exécutez à partir de là, génère l’erreur « System. Security. SecurityException : échec de la demande ». Pour plus d’informations sur les exceptions de sécurité, consultez la classe <xref:System.Security.SecurityException>.

[!code-vb[VbVbalrStatements#85](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#85)]

Dans une telle situation de confiance partielle, vous devez placer l’instruction `Process.Start` dans un `Sub`distinct. L’appel initial de l' `Sub` échoue. Cela permet à `Try...Catch` de l’intercepter avant que le `Sub` contenant `Process.Start` soit démarré et que l’exception de sécurité soit produite.

## <a name="examples"></a>Exemples

### <a name="the-structure-of-trycatchfinally"></a>Structure de try... Catch... Suivie

L’exemple suivant illustre la structure de l’instruction `Try...Catch...Finally`.

[!code-vb[VbVbalrStatements#86](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#86)]  

### <a name="exception-in-a-method-called-from-a-try-block"></a>Exception dans une méthode appelée à partir d’un bloc try

Dans l’exemple suivant, la méthode `CreateException` lève une `NullReferenceException`. Le code qui génère l’exception n’est pas dans un bloc `Try`. Par conséquent, la méthode `CreateException` ne gère pas l’exception. La méthode `RunSample` gère l’exception, car l’appel à la méthode `CreateException` se trouve dans un bloc `Try`.

L’exemple comprend des instructions `Catch` pour plusieurs types d’exceptions, classées du plus spécifique au plus général.

[!code-vb[VbVbalrStatements#91](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#91)]

### <a name="the-catch-when-statement"></a>Instruction catch when

L’exemple suivant montre comment utiliser une instruction `Catch When` pour filtrer sur une expression conditionnelle. Si l’expression conditionnelle a la valeur `True`, le code du bloc `Catch` s’exécute.

[!code-vb[VbVbalrStatements#92](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#92)]

### <a name="nested-try-statements"></a>Instructions Try imbriquées

L’exemple suivant contient une instruction `Try…Catch` qui est contenue dans un bloc `Try`. Le bloc `Catch` interne lève une exception dont la propriété `InnerException` a la valeur de l’exception d’origine. Le bloc de `Catch` externe signale sa propre exception et l’exception interne.

[!code-vb[VbVbalrStatements#93](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#93)]

### <a name="exception-handling-for-async-methods"></a>Gestion des exceptions pour les méthodes Async

L'exemple suivant illustre la gestion des exceptions pour les méthodes async. Pour intercepter une exception qui s’applique à une tâche asynchrone, l’expression `Await` se trouve dans un bloc `Try` de l’appelant, et l’exception est interceptée dans le bloc `Catch`.

Supprimez les marques de commentaire de la ligne `Throw New Exception` dans l'exemple pour illustrer la gestion des exceptions. L’exception est interceptée dans le bloc `Catch`, la propriété `IsFaulted` de la tâche a la valeur `True`et la propriété `Exception.InnerException` de la tâche a la valeur de l’exception.

Supprimez les marques de commentaire de la ligne `Throw New OperationCancelledException` pour montrer ce qui se passe quand vous annulez un processus asynchrone. L’exception est interceptée dans le bloc `Catch` et la propriété `IsCanceled` de la tâche a la valeur `True`. Toutefois, dans certaines conditions qui ne s’appliquent pas à cet exemple, `IsFaulted` est défini sur `True` et `IsCanceled` est défini sur `False`.

[!code-vb[csAsyncExceptions#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/csasyncexceptions/vb/class1.vb#1)]

### <a name="handling-multiple-exceptions-in-async-methods"></a>Gestion de plusieurs exceptions dans les méthodes Async

L’exemple suivant illustre la gestion des exceptions quand plusieurs tâches peuvent entraîner plusieurs exceptions. Le bloc de `Try` a l’expression `Await` pour la tâche qui <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType> retournée. La tâche est terminée lorsque les trois tâches auxquelles <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType> est appliqué sont terminées.

Chacune de ces trois tâches provoque une exception. Le bloc `Catch` itère au sein des exceptions, qui se trouvent dans la propriété `Exception.InnerExceptions` de la tâche que `Task.WhenAll` retournée.

[!code-vb[csAsyncExceptions#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/csasyncexceptions/vb/class1.vb#3)]

## <a name="see-also"></a>Voir aussi

- <xref:Microsoft.VisualBasic.Information.Err%2A>
- <xref:System.Exception>
- [Exit (instruction)](exit-statement.md)
- [On Error (instruction)](on-error-statement.md)
- [Bonnes pratiques d’utilisation des extraits de code](/visualstudio/ide/best-practices-for-using-code-snippets)
- [Gestion des exceptions](../../../standard/parallel-programming/exception-handling-task-parallel-library.md)
- [Throw (instruction)](throw-statement.md)
