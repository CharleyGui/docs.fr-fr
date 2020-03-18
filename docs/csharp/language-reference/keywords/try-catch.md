---
title: try-catch - Référence C#
ms.date: 07/20/2015
f1_keywords:
- try
- try_CSharpKeyword
- catch
- catch_CSharpKeyword
helpviewer_keywords:
- catch keyword [C#]
- try-catch statement [C#]
ms.assetid: cb5503c7-bfa1-4610-8fc2-ddcd2e84c438
ms.openlocfilehash: 3d4315a09869b77b4ae8cbb43646f9a96280b678
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79173469"
---
# <a name="try-catch-c-reference"></a>try-catch (référence C#)

L'instruction try-catch consiste en un bloc `try` suivi d'une ou plusieurs clauses `catch` qui spécifient des gestionnaires pour différentes exceptions.

Quand une exception est levée, le Common Language Runtime (CLR) recherche l'instruction `catch` qui gère cette exception. Si la méthode en cours d'exécution ne contient pas un tel bloc `catch`, le CLR examine la méthode qui a appelé la méthode actuelle, puis remonte la pile des appels. Si aucun bloc `catch` n'est trouvé, alors le CLR affiche un message d'exception non gérée à l'utilisateur et arrête l'exécution du programme.

Le bloc `try` contient le code protégé susceptible de provoquer l'exception. Le bloc est exécuté jusqu'à ce qu'une exception soit levée ou qu'il se soit correctement terminé. Par exemple, la tentative suivante d'effectuer un cast d'un objet `null` déclenche l'exception <xref:System.NullReferenceException> :

```csharp
object o2 = null;
try
{
    int i2 = (int)o2;   // Error
}
```

Bien que la clause `catch` puisse être utilisée sans arguments pour intercepter tout type d'exception, cette utilisation est déconseillée. En général, vous devez intercepter uniquement les exceptions desquelles vous savez comment récupérer. Par conséquent, vous devez toujours spécifier un argument d'objet dérivé de <xref:System.Exception?displayProperty=nameWithType>, par exemple :

```csharp
catch (InvalidCastException e)
{
}
```

Il est possible d'utiliser plusieurs clauses `catch` spécifiques dans la même instruction try-catch. Dans ce cas, l'ordre des clauses `catch` est important car les clauses `catch` sont examinées dans l'ordre. Interceptez les exceptions plus spécifiques avant les moins spécifiques. Le compilateur produit une erreur si vous organisez vos blocs catch de sorte qu'un bloc ultérieur ne puisse jamais être atteint.

L'utilisation d'arguments `catch` constitue un moyen de filtrer les exceptions à gérer.  Vous pouvez également utiliser un filtre d’exception qui examine l’exception pour déterminer si elle doit être prise en charge.  Si le filtre d’exception retourne la valeur false, la recherche d’un gestionnaire se poursuit.

```csharp
catch (ArgumentException e) when (e.ParamName == "…")
{
}
```

L'utilisation de filtres d'exceptions est préférable à une interception et une nouvelle levée (voir explication ci-dessous), car les filtres laissent la pile intact.  Si un gestionnaire ultérieur vide la pile, vous pouvez déterminer d'où l'exception provient à l'origine, au lieu de déterminer simplement le dernier emplacement auquel elle a été levée.  Une utilisation courante des expressions de filtre d'exception est liée à la journalisation.  Vous pouvez créer un filtre qui retourne toujours false et dont la sortie est journalisée. Vous pouvez journaliser les exceptions au fur et à mesure sans avoir à les prendre en charge et à les lever de nouveau.

Une instruction [throw](throw.md) peut être utilisée dans un bloc `catch` pour lever une nouvelle fois l’exception interceptée par l’instruction `catch`. L'exemple suivant extrait des informations sources d'une exception <xref:System.IO.IOException>, puis lève l'exception à la méthode parente.

```csharp
catch (FileNotFoundException e)
{
    // FileNotFoundExceptions are handled here.
}
catch (IOException e)
{
    // Extract some information from this exception, and then
    // throw it to the parent method.
    if (e.Source != null)
        Console.WriteLine("IOException source: {0}", e.Source);
    throw;
}
```

Vous pouvez intercepter une seule exception et lever une exception différente. Dans ce cas, spécifiez l'exception que vous interceptez en tant qu'exception interne, comme illustré dans l'exemple suivant.

```csharp
catch (InvalidCastException e)
{
    // Perform some action here, and then throw a new exception.
    throw new YourCustomException("Put your error message here.", e);
}
```

Vous pouvez également lever à nouveau une exception quand une condition spécifiée a la valeur true, comme illustré dans l'exemple suivant.

```csharp
catch (InvalidCastException e)
{
    if (e.Data == null)
    {
        throw;
    }
    else
    {
        // Take some action.
    }
}
```

> [!NOTE]
> Il est également possible d’utiliser un filtre d’exception pour obtenir un résultat similaire d’une manière souvent plus claire (sans modifier la pile, comme expliqué précédemment dans ce document). L’exemple suivant a un comportement similaire à l’exemple précédent pour les appelants. La fonction lève et retourne `InvalidCastException` à l’appelant quand `e.Data` a une valeur `null`.
>
> ```csharp
> catch (InvalidCastException e) when (e.Data != null)
> {
>     // Take some action.
> }
> ```

Dans un bloc `try`, initialisez uniquement les variables qui y sont déclarées. Sinon, une exception peut se produire avant la fin de l'exécution du bloc. Par exemple, dans l'exemple de code suivant, la variable `n` est initialisée à l'intérieur du bloc `try`. Une tentative d'utilisation de cette variable en dehors du bloc `try` dans l'instruction `Write(n)` génère une erreur du compilateur.

```csharp
static void Main()
{
    int n;
    try
    {
        // Do not initialize this variable here.
        n = 123;
    }
    catch
    {
    }
    // Error: Use of unassigned local variable 'n'.
    Console.Write(n);
}
```

Pour plus d’informations sur l’interception, consultez [try-catch-finally](try-catch-finally.md).

## <a name="exceptions-in-async-methods"></a>Exceptions dans les méthodes async

Une méthode async est marquée par un modificateur [async](async.md) et contient généralement une ou plusieurs expressions ou instructions await. Une expression await applique l’opérateur [await](../operators/await.md) à un <xref:System.Threading.Tasks.Task> ou <xref:System.Threading.Tasks.Task%601>.

Quand le contrôle atteint un `await` dans la méthode async, la progression de la méthode est interrompue jusqu'à ce que la tâche attendue se termine. Quand la tâche est terminée, l’exécution peut reprendre dans la méthode. Pour plus d’informations, consultez [Programmation asynchrone avec Async et Await](../../programming-guide/concepts/async/index.md) et [Flux de contrôle dans les programmes Async](../../programming-guide/concepts/async/control-flow-in-async-programs.md).

La tâche terminée à laquelle `await` est appliqué peut être dans un état d'erreur en raison d'une exception non gérée dans la méthode qui retourne la tâche. L'attente de la tâche lève une exception. Une tâche peut également se terminer dans un état annulé si le processus asynchrone qui la retourne est annulé. L'attente d'une tâche annulée lève une `OperationCanceledException`. Pour plus d’informations sur la façon d’annuler un processus asynchrone, consultez [Réglage de votre application Async](../../programming-guide/concepts/async/fine-tuning-your-async-application.md).

Pour intercepter l'exception, attendez la tâche dans un bloc `try`, puis interceptez l'exception dans le bloc `catch` associé. Pour obtenir un exemple, consultez la section [Exemple de la méthode async](#async-method-example).

Une tâche peut être dans un état d'erreur car plusieurs exceptions se sont produites dans la méthode async attendue. Par exemple, la tâche peut être le résultat d'un appel à <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType>. Quand vous attendez une telle tâche, une seule des exceptions est interceptée et vous ne pouvez pas prévoir laquelle. Pour obtenir un exemple, consultez la section [Exemple Task.WhenAll](#taskwhenall-example).

## <a name="example"></a> Exemple

Dans l'exemple suivant, le bloc `try` contient un appel à la méthode `ProcessString` qui risque de provoquer une exception. La clause `catch` clause contient le gestionnaire d'exceptions qui affiche simplement un message à l'écran. Quand l'instruction `throw` est appelée depuis `MyMethod`, le système recherche l'instruction `catch` et affiche le message `Exception caught`.

[!code-csharp[csrefKeywordsExceptions#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsExceptions/CS/csrefKeywordsExceptions.cs#2)]

## <a name="two-catch-blocks-example"></a>Exemple de deux blocs catch

Dans l'exemple suivant, deux blocs catch sont utilisés, et l'exception la plus spécifique, qui apparaît la première, est interceptée.

Pour intercepter l'exception la moins spécifique, vous pouvez remplacer l'instruction throw dans `ProcessString` par l'instruction suivante : `throw new Exception()`.

Si vous placez le bloc catch le moins spécifique en premier dans l'exemple, le message d'erreur suivant s'affiche : `A previous catch clause already catches all exceptions of this or a super type ('System.Exception')`.

[!code-csharp[csrefKeywordsExceptions#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsExceptions/CS/csrefKeywordsExceptions.cs#3)]

## <a name="async-method-example"></a>Exemple de la méthode async

L'exemple suivant illustre la gestion des exceptions pour les méthodes async. Pour intercepter une exception levée par une tâche async, placez l'expression `await` dans un bloc `try` et interceptez-la dans un bloc `catch`.

Supprimez les marques de commentaire de la ligne `throw new Exception` dans l'exemple pour illustrer la gestion des exceptions. La propriété `IsFaulted` de la tâche a la valeur `True`, la propriété `Exception.InnerException` de la tâche a la valeur de l'exception et l'exception est interceptée dans le bloc `catch`.

Supprimez les marques de commentaire de la ligne `throw new OperationCanceledException` pour montrer ce qui se passe quand vous annulez un processus asynchrone. La propriété `IsCanceled` de la tâche a la valeur `true` et l'exception est interceptée dans le bloc `catch`. Sous certaines conditions qui s'appliquent à cet exemple, la propriété `IsFaulted` de la tâche a la valeur `true` et `IsCanceled` a la valeur `false`.

[!code-csharp[csAsyncExceptions#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csasyncexceptions/cs/class1.cs#2)]  

## <a name="taskwhenall-example"></a>Exemple Task.WhenAll

L’exemple suivant illustre la gestion des exceptions quand plusieurs tâches peuvent entraîner plusieurs exceptions. Le bloc `try` attend la tâche retournée par un appel à <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType>. La tâche est terminée quand les trois tâches auxquelles WhenAll est appliqué sont terminées.

Chacune de ces trois tâches provoque une exception. Le bloc `catch` itère au sein des exceptions, qui sont trouvent dans la propriété `Exception.InnerExceptions` de la tâche retournée par <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType>.

[!code-csharp[csAsyncExceptions#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csasyncexceptions/cs/class1.cs#4)]

## <a name="c-language-specification"></a>spécification du langage C#

Pour plus d’informations, consultez la section [Instruction try](~/_csharplang/spec/statements.md#the-try-statement) de la [spécification du langage C#](~/_csharplang/spec/introduction.md).

## <a name="see-also"></a>Voir aussi

- [Référence C](../index.md)
- [Guide de programmation C#](../../programming-guide/index.md)
- [Mots clés C#](index.md)
- [Instructions try, throw et catch (C++)](/cpp/cpp/try-throw-and-catch-statements-cpp)
- [Jeter](throw.md)
- [try-finally](try-finally.md)
- [Comment : Jeter explicitement des exceptions](../../../standard/exceptions/how-to-explicitly-throw-exceptions.md)
