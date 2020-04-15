---
title: Types de retour async (C#)
ms.date: 04/14/2020
ms.assetid: ddb2539c-c898-48c1-ad92-245e4a996df8
ms.openlocfilehash: 73a6e1924652c8635377547e2faddc864ac5540a
ms.sourcegitcommit: c91110ef6ee3fedb591f3d628dc17739c4a7071e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/15/2020
ms.locfileid: "81389131"
---
# <a name="async-return-types-c"></a>Types de retour async (C#)

Les méthodes async peuvent avoir les types de retour suivants :

- <xref:System.Threading.Tasks.Task%601>, pour une méthode async qui retourne une valeur.
- <xref:System.Threading.Tasks.Task>, pour une méthode async qui effectue une opération mais ne retourne aucune valeur.
- `void`, pour un gestionnaire d’événements.
- À compter de C# 7.0, tout type ayant une méthode `GetAwaiter` accessible. L’objet retourné par la méthode `GetAwaiter` doit implémenter l’interface <xref:System.Runtime.CompilerServices.ICriticalNotifyCompletion?displayProperty=nameWithType>.
- En commençant par C 8.0, <xref:System.Collections.Generic.IAsyncEnumerable%601>, pour une méthode async qui retourne un flux *async*.

Pour plus d’informations sur les méthodes async, consultez [Programmation asynchrone avec async et await (C#)](./index.md).  
  
## <a name="tasktresult-return-type"></a> Task\<TResult\>, type de retour  
Le <xref:System.Threading.Tasks.Task%601> type de retour est utilisé pour une méthode async qui contient `TResult`une déclaration de [retour](../../../language-reference/keywords/return.md) (C) dans laquelle l’opéra est .  
  
Dans l’exemple suivant, la méthode async `GetLeisureHours` contient une instruction `return` qui retourne un entier. La déclaration de méthode doit donc spécifier un type de retour `Task<int>`.  La méthode async <xref:System.Threading.Tasks.Task.FromResult%2A> est un espace réservé pour une opération qui retourne une chaîne.
  
:::code language="csharp" source="./snippets/async-returns1.cs" id="SnippetFirstExample":::

Quand la méthode `GetLeisureHours` est appelée à partir d’une expression await dans la méthode `ShowTodaysInfo`, cette expression récupère la valeur entière (la valeur de `leisureHours`) qui est stockée dans la tâche retournée par la méthode `GetLeisureHours`. Pour plus d’informations sur les expressions await, consultez [await](../../../language-reference/operators/await.md).  
  
Vous pouvez mieux `await` comprendre comment récupère `Task<T>` le résultat d’un en séparant l’appel à `GetLeisureHours` partir de l’application de `await`, comme le code suivant montre. Un appel à la méthode `GetLeisureHours` qui n’est pas immédiatement attendue retourne un type `Task<int>`, comme vous pourriez l’attendre de la déclaration de la méthode. La tâche est assignée à la variable `integerTask` dans l’exemple. Comme `integerTask` est un <xref:System.Threading.Tasks.Task%601>, il contient une propriété <xref:System.Threading.Tasks.Task%601.Result> de type `TResult`. Dans ce cas, `TResult` représente un type entier. Quand `await` est appliqué à `integerTask`, l’expression await prend pour la valeur le contenu de la propriété <xref:System.Threading.Tasks.Task%601.Result%2A> de `integerTask`. La valeur est assignée à la variable `ret`.  
  
> [!IMPORTANT]
> <xref:System.Threading.Tasks.Task%601.Result%2A> est une propriété bloquante. Si vous essayez d’y accéder avant la fin de sa tâche, le thread actif est bloqué tant que la tâche n’est pas terminée et que la valeur n’est pas disponible. Dans la plupart des cas, vous devez accéder à la valeur avec `await` au lieu d’accéder directement à la propriété. <br/> L’exemple précédent récupérait la valeur de la propriété <xref:System.Threading.Tasks.Task%601.Result%2A> pour bloquer le thread principal afin de permettre à la méthode `ShowTodaysInfo` de terminer son exécution avant la fin de l’application.  

:::code language="csharp" source="./snippets/async-returns1a.cs" id="SnippetSecondVersion":::

## <a name="task-return-type"></a>Type de retour task  
Les méthodes async qui ne contiennent pas d’instruction `return` ou qui contiennent une instruction `return` ne retournant pas d’opérande ont généralement un type de retour <xref:System.Threading.Tasks.Task>. De telles méthodes retournent `void` si elles s’exécutent de façon synchrone. Si vous utilisez un type de retour <xref:System.Threading.Tasks.Task> pour une méthode async, une méthode d’appel peut utiliser un opérateur `await` pour suspendre l’achèvement de l’appelant jusqu’à ce que la méthode async soit terminée.  
  
Dans l’exemple suivant, la méthode async `WaitAndApologize` ne contient pas d’instruction `return`. Par conséquent, elle retourne un objet <xref:System.Threading.Tasks.Task>. Le `Task` retour `WaitAndApologize` d’un permet d’être attendu. Le <xref:System.Threading.Tasks.Task> type n’inclut `Result` pas une propriété parce qu’elle n’a aucune valeur de retour.  

:::code language="csharp" source="./snippets/async-returns2.cs" id="SnippetTaskReturn":::

`WaitAndApologize` est attendue avec une instruction await au lieu d’une expression await, comme pour l’instruction d’appel d’une méthode synchrone retournant un type void. Dans ce cas, l’application d’un opérateur await ne génère pas de valeur.  
  
Comme dans l’exemple <xref:System.Threading.Tasks.Task%601> précédent, vous pouvez séparer l’appel à `WaitAndApologize` de l’application d’un opérateur await, comme l’illustre le code suivant. Cependant, n’oubliez pas qu’un type `Task` n’a pas de propriété `Result` et qu’aucune valeur n’est générée quand un opérateur await est appliqué à un type `Task`.  
  
Le code suivant sépare l’appel à la méthode `WaitAndApologize` de l’attente de la tâche que retourne la méthode.  

:::code language="csharp" source="./snippets/async-returns2a.cs" id="SnippetAwaitTask":::

## <a name="void-return-type"></a> Type de retour void

Vous utilisez le type de retour `void` dans les gestionnaires d’événements asynchrones, lesquels exigent un type de retour `void`. Pour les méthodes autres que les gestionnaires d’événements qui ne retournent pas de valeur, vous devez retourner <xref:System.Threading.Tasks.Task> à la place, car une méthode async qui retourne `void` ne peut pas être attendue. Tout appelant d’une telle méthode doit continuer à se terminer sans attendre la fin de la méthode async appelée. L’appelant doit être indépendant de toutes les valeurs ou exceptions générées par la méthode async.  
  
L’appelant d’une méthode async de retour vide ne peut pas attraper les exceptions jetées de la méthode, et ces exceptions non manipulées sont susceptibles de causer votre demande d’échec. Si une méthode <xref:System.Threading.Tasks.Task> qui <xref:System.Threading.Tasks.Task%601> renvoie une exception ou jette une exception, l’exception est stockée dans la tâche retournée. L’exception est ressurinue lorsque la tâche est attendue. Par conséquent, veillez à ce qu’une méthode async capable de générer une exception ait le type de retour <xref:System.Threading.Tasks.Task> ou <xref:System.Threading.Tasks.Task%601> et que les appels à la méthode soient attendus.  
  
Pour plus d’informations sur la façon d’attraper les exceptions dans les méthodes async, voir les [exceptions dans async Méthodes](../../../language-reference/keywords/try-catch.md#exceptions-in-async-methods) section de [l’article try-catch.](../../../language-reference/keywords/try-catch.md)  
  
L’exemple suivant illustre le comportement d’un gestionnaire d’événements asynchrones. Dans l’exemple de code, un gestionnaire d’événement async doit faire savoir au thread principal quand il se termine. Le thread principal peut donc attendre la fin d’un gestionnaire d’événements asynchrones avant de quitter le programme.

:::code language="csharp" source="./snippets/async-returns3.cs":::

## <a name="generalized-async-return-types-and-valuetasktresult"></a>Types de retour async généralisés et ValueTask\<TResult\>

À compter de C# 7.0, une méthode async peut retourner tout type ayant une méthode `GetAwaiter` accessible.

Étant donné que <xref:System.Threading.Tasks.Task> et <xref:System.Threading.Tasks.Task%601> sont des types référence, l’allocation de mémoire dans des chemins critiques pour les performances, en particulier quand les allocations se produisent dans des boucles serrées, peuvent nuire aux performances. La prise en charge de types de retour généralisés signifie que vous pouvez retourner un type valeur léger au lieu d’un type référence pour éviter des allocations de mémoire supplémentaires.

Le .NET fournit la structure <xref:System.Threading.Tasks.ValueTask%601?displayProperty=nameWithType> comme implémentation légère d’une valeur retournant des tâches généralisées. Pour utiliser le type <xref:System.Threading.Tasks.ValueTask%601?displayProperty=nameWithType>, vous devez ajouter le package NuGet `System.Threading.Tasks.Extensions` à votre projet. L’exemple suivant utilise la structure <xref:System.Threading.Tasks.ValueTask%601> pour récupérer la valeur de deux dés.
  
:::code language="csharp" source="./snippets/async-valuetask.cs":::

## <a name="async-streams-with-iasyncenumerablet"></a>Async coule avec IAsyncEnumerable\<T\>

En commençant par C 8.0, une méthode async peut retourner <xref:System.Collections.Generic.IAsyncEnumerable%601>un *flux async*, représenté par . Un flux async fournit un moyen d’énumérer les éléments lus à partir d’un flux lorsque les éléments sont générés en morceaux avec des appels asynchrones répétés. L’exemple suivant montre une méthode async qui génère un flux async:

:::code language="csharp" source="./snippets/AsyncStreams.cs" id="SnippetGenerateAsyncStream":::

L’exemple précédent lit les lignes d’une chaîne asynchrone. Une fois chaque ligne lue, le code énumère chaque mot de la chaîne. Les appelants énuméreraient chaque `await foreach` mot à l’aide de la déclaration. La méthode attend quand il a besoin de lire asynchronement la ligne suivante à partir de la chaîne source.

## <a name="see-also"></a>Voir aussi

- <xref:System.Threading.Tasks.Task.FromResult%2A>
- [Procédure pas à pas : accès au web avec async et await (C#)](./walkthrough-accessing-the-web-by-using-async-and-await.md)
- [Flux de contrôle dans les programmes Async (C)](./control-flow-in-async-programs.md)
- [async](../../../language-reference/keywords/async.md)
- [Attendent](../../../language-reference/operators/await.md)
