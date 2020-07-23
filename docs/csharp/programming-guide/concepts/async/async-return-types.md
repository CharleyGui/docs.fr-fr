---
title: Types de retour async (C#)
description: Découvrez les types de retour que les méthodes Async peuvent avoir en C# avec des exemples de code pour chaque type et des ressources supplémentaires.
ms.date: 04/14/2020
ms.assetid: ddb2539c-c898-48c1-ad92-245e4a996df8
ms.openlocfilehash: 954e449356819595a3a974a6dece5349e53ec88a
ms.sourcegitcommit: 40de8df14289e1e05b40d6e5c1daabd3c286d70c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/22/2020
ms.locfileid: "86925382"
---
# <a name="async-return-types-c"></a>Types de retour async (C#)

Les méthodes async peuvent avoir les types de retour suivants :

- <xref:System.Threading.Tasks.Task%601>, pour une méthode async qui retourne une valeur.
- <xref:System.Threading.Tasks.Task>, pour une méthode async qui effectue une opération mais ne retourne aucune valeur.
- `void`, pour un gestionnaire d’événements.
- À compter de C# 7.0, tout type ayant une méthode `GetAwaiter` accessible. L’objet retourné par la méthode `GetAwaiter` doit implémenter l’interface <xref:System.Runtime.CompilerServices.ICriticalNotifyCompletion?displayProperty=nameWithType>.
- À compter de C# 8,0, <xref:System.Collections.Generic.IAsyncEnumerable%601> , pour une méthode Async qui retourne un *flux asynchrone*.

Pour plus d’informations sur les méthodes async, consultez [Programmation asynchrone avec async et await (C#)](./index.md).  
  
## <a name="tasktresult-return-type"></a>Type de retour de la tâche \<TResult\>  
Le <xref:System.Threading.Tasks.Task%601> type de retour est utilisé pour une méthode Async qui contient une instruction [Return](../../../language-reference/keywords/return.md) (C#) dans laquelle l’opérande est `TResult` .  
  
Dans l’exemple suivant, la méthode async `GetLeisureHours` contient une instruction `return` qui retourne un entier. La déclaration de méthode doit donc spécifier un type de retour `Task<int>`.  La méthode async <xref:System.Threading.Tasks.Task.FromResult%2A> est un espace réservé pour une opération qui retourne une chaîne.
  
:::code language="csharp" source="./snippets/async-return-types/async-returns1.cs" id="SnippetFirstExample":::

Quand la méthode `GetLeisureHours` est appelée à partir d’une expression await dans la méthode `ShowTodaysInfo`, cette expression récupère la valeur entière (la valeur de `leisureHours`) qui est stockée dans la tâche retournée par la méthode `GetLeisureHours`. Pour plus d’informations sur les expressions await, consultez [await](../../../language-reference/operators/await.md).  
  
Vous pouvez mieux comprendre comment `await` récupère le résultat d’un `Task<T>` en séparant l’appel à `GetLeisureHours` de l’application de `await` , comme le montre le code suivant. Un appel à la méthode `GetLeisureHours` qui n’est pas immédiatement attendue retourne un type `Task<int>`, comme vous pourriez l’attendre de la déclaration de la méthode. La tâche est assignée à la variable `integerTask` dans l’exemple. Comme `integerTask` est un <xref:System.Threading.Tasks.Task%601>, il contient une propriété <xref:System.Threading.Tasks.Task%601.Result> de type `TResult`. Dans ce cas, `TResult` représente un type entier. Quand `await` est appliqué à `integerTask`, l’expression await prend pour la valeur le contenu de la propriété <xref:System.Threading.Tasks.Task%601.Result%2A> de `integerTask`. La valeur est assignée à la variable `ret`.  
  
> [!IMPORTANT]
> <xref:System.Threading.Tasks.Task%601.Result%2A> est une propriété bloquante. Si vous essayez d’y accéder avant la fin de sa tâche, le thread actif est bloqué tant que la tâche n’est pas terminée et que la valeur n’est pas disponible. Dans la plupart des cas, vous devez accéder à la valeur avec `await` au lieu d’accéder directement à la propriété. <br/> L’exemple précédent récupérait la valeur de la propriété <xref:System.Threading.Tasks.Task%601.Result%2A> pour bloquer le thread principal afin de permettre à la méthode `ShowTodaysInfo` de terminer son exécution avant la fin de l’application.  

:::code language="csharp" source="./snippets/async-return-types/async-returns1a.cs" id="SnippetSecondVersion":::

## <a name="task-return-type"></a>Type de retour task  
Les méthodes async qui ne contiennent pas d’instruction `return` ou qui contiennent une instruction `return` ne retournant pas d’opérande ont généralement un type de retour <xref:System.Threading.Tasks.Task>. De telles méthodes retournent `void` si elles s’exécutent de façon synchrone. Si vous utilisez un type de retour <xref:System.Threading.Tasks.Task> pour une méthode async, une méthode d’appel peut utiliser un opérateur `await` pour suspendre l’achèvement de l’appelant jusqu’à ce que la méthode async soit terminée.  
  
Dans l’exemple suivant, la méthode async `WaitAndApologize` ne contient pas d’instruction `return`. Par conséquent, elle retourne un objet <xref:System.Threading.Tasks.Task>. Le retour `Task` d’un permet `WaitAndApologize` à d’être attendu. Le <xref:System.Threading.Tasks.Task> type n’inclut `Result` pas de propriété, car il n’a pas de valeur de retour.  

:::code language="csharp" source="./snippets/async-return-types/async-returns2.cs" id="SnippetTaskReturn":::

`WaitAndApologize` est attendue avec une instruction await au lieu d’une expression await, comme pour l’instruction d’appel d’une méthode synchrone retournant un type void. Dans ce cas, l’application d’un opérateur await ne génère pas de valeur.  
  
Comme dans l’exemple <xref:System.Threading.Tasks.Task%601> précédent, vous pouvez séparer l’appel à `WaitAndApologize` de l’application d’un opérateur await, comme l’illustre le code suivant. Cependant, n’oubliez pas qu’un type `Task` n’a pas de propriété `Result` et qu’aucune valeur n’est générée quand un opérateur await est appliqué à un type `Task`.  
  
Le code suivant sépare l’appel à la méthode `WaitAndApologize` de l’attente de la tâche que retourne la méthode.  

:::code language="csharp" source="./snippets/async-return-types/async-returns2a.cs" id="SnippetAwaitTask":::

## <a name="void-return-type"></a> Type de retour void

Vous utilisez le type de retour `void` dans les gestionnaires d’événements asynchrones, lesquels exigent un type de retour `void`. Pour les méthodes autres que les gestionnaires d’événements qui ne retournent pas de valeur, vous devez retourner <xref:System.Threading.Tasks.Task> à la place, car une méthode async qui retourne `void` ne peut pas être attendue. Tout appelant d’une telle méthode doit continuer à se terminer sans attendre la fin de la méthode Async appelée. L’appelant doit être indépendant des valeurs ou des exceptions générées par la méthode Async.  
  
L’appelant d’une méthode Async qui retourne void ne peut pas intercepter les exceptions levées à partir de la méthode, et ces exceptions non gérées sont susceptibles de provoquer l’échec de votre application. Si une méthode qui retourne un <xref:System.Threading.Tasks.Task> ou <xref:System.Threading.Tasks.Task%601> lève une exception, l’exception est stockée dans la tâche retournée. L’exception est levée une nouvelle fois lorsque la tâche est attendue. Par conséquent, veillez à ce qu’une méthode async capable de générer une exception ait le type de retour <xref:System.Threading.Tasks.Task> ou <xref:System.Threading.Tasks.Task%601> et que les appels à la méthode soient attendus.  
  
Pour plus d’informations sur la façon d’intercepter des exceptions dans les méthodes Async, consultez la section [exceptions dans les méthodes Async](../../../language-reference/keywords/try-catch.md#exceptions-in-async-methods) de l’article [try-catch](../../../language-reference/keywords/try-catch.md) .  
  
L’exemple suivant illustre le comportement d’un gestionnaire d’événements asynchrones. Dans l’exemple de code, un gestionnaire d’événements asynchrones doit permettre au thread principal de savoir quand il se termine. Le thread principal peut donc attendre la fin d’un gestionnaire d’événements asynchrones avant de quitter le programme.

:::code language="csharp" source="./snippets/async-return-types/async-returns3.cs":::

## <a name="generalized-async-return-types-and-valuetasktresult"></a>Types de retour async généralisés et ValueTask\<TResult\>

À compter de C# 7.0, une méthode async peut retourner tout type ayant une méthode `GetAwaiter` accessible.

Étant donné que <xref:System.Threading.Tasks.Task> et <xref:System.Threading.Tasks.Task%601> sont des types référence, l’allocation de mémoire dans des chemins critiques pour les performances, en particulier quand les allocations se produisent dans des boucles serrées, peuvent nuire aux performances. La prise en charge de types de retour généralisés signifie que vous pouvez retourner un type valeur léger au lieu d’un type référence pour éviter des allocations de mémoire supplémentaires.

Le .NET fournit la structure <xref:System.Threading.Tasks.ValueTask%601?displayProperty=nameWithType> comme implémentation légère d’une valeur retournant des tâches généralisées. Pour utiliser le type <xref:System.Threading.Tasks.ValueTask%601?displayProperty=nameWithType>, vous devez ajouter le package NuGet `System.Threading.Tasks.Extensions` à votre projet. L’exemple suivant utilise la structure <xref:System.Threading.Tasks.ValueTask%601> pour récupérer la valeur de deux dés.
  
:::code language="csharp" source="./snippets/async-return-types/async-valuetask.cs":::

## <a name="async-streams-with-iasyncenumerablet"></a>Flux asynchrones avec IAsyncEnumerable\<T\>

À compter de C# 8,0, une méthode Async peut retourner un *flux asynchrone*, représenté par <xref:System.Collections.Generic.IAsyncEnumerable%601> . Un flux asynchrone fournit un moyen d’énumérer les éléments lus à partir d’un flux lorsque des éléments sont générés dans des segments avec des appels asynchrones répétés. L’exemple suivant montre une méthode Async qui génère un flux asynchrone :

:::code language="csharp" source="./snippets/async-return-types/AsyncStreams.cs" id="SnippetGenerateAsyncStream":::

L’exemple précédent lit les lignes d’une chaîne de façon asynchrone. Une fois chaque ligne lue, le code énumère chaque mot de la chaîne. Les appelants énumèrent chaque mot à l’aide de l' `await foreach` instruction. La méthode attend quand elle doit lire de façon asynchrone la ligne suivante à partir de la chaîne source.

## <a name="see-also"></a>Voir aussi

- <xref:System.Threading.Tasks.Task.FromResult%2A>
- [Procédure pas à pas : accès au web avec async et await (C#)](./walkthrough-accessing-the-web-by-using-async-and-await.md)
- [Workflow de contrôle dans les programmes Async (C#)](./control-flow-in-async-programs.md)
- [Suppr](../../../language-reference/keywords/async.md)
- [await](../../../language-reference/operators/await.md)
