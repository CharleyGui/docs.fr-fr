---
title: Types de retour async (C#)
ms.date: 05/29/2017
ms.assetid: ddb2539c-c898-48c1-ad92-245e4a996df8
ms.openlocfilehash: 9926fea5308f9088ad924bcc98d8deed319c6300
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79170037"
---
# <a name="async-return-types-c"></a>Types de retour async (C#)
Les méthodes async peuvent avoir les types de retour suivants :

- <xref:System.Threading.Tasks.Task%601>, pour une méthode async qui retourne une valeur.

- <xref:System.Threading.Tasks.Task>, pour une méthode async qui effectue une opération mais ne retourne aucune valeur.

- `void`, pour un gestionnaire d’événements.

- À compter de C# 7.0, tout type ayant une méthode `GetAwaiter` accessible. L’objet retourné par la méthode `GetAwaiter` doit implémenter l’interface <xref:System.Runtime.CompilerServices.ICriticalNotifyCompletion?displayProperty=nameWithType>.
  
Pour plus d’informations sur les méthodes async, consultez [Programmation asynchrone avec async et await (C#)](./index.md).  
  
Chaque type de retour est examiné dans l’une des sections suivantes, et vous trouverez un exemple complet qui utilise les trois types à la fin de la rubrique.  
  
## <a name="BKMK_TaskTReturnType"></a> Task\<TResult\>, type de retour  
Le type de retour <xref:System.Threading.Tasks.Task%601> est utilisé pour une méthode async qui contient une instruction [return](../../../language-reference/keywords/return.md) (C#) dans laquelle l’opérande est de type `TResult`.  
  
Dans l’exemple suivant, la méthode async `GetLeisureHours` contient une instruction `return` qui retourne un entier. La déclaration de méthode doit donc spécifier un type de retour `Task<int>`.  La méthode async <xref:System.Threading.Tasks.Task.FromResult%2A> est un espace réservé pour une opération qui retourne une chaîne.
  
[!code-csharp[return-value](../../../../../samples/snippets/csharp/programming-guide/async/async-returns1.cs)]

Quand la méthode `GetLeisureHours` est appelée à partir d’une expression await dans la méthode `ShowTodaysInfo`, cette expression récupère la valeur entière (la valeur de `leisureHours`) qui est stockée dans la tâche retournée par la méthode `GetLeisureHours`. Pour plus d’informations sur les expressions await, consultez [await](../../../language-reference/operators/await.md).  
  
Vous pouvez mieux comprendre comment cela se produit en séparant l’appel à `GetLeisureHours` de l’application de `await`, comme l’illustre le code suivant. Un appel à la méthode `GetLeisureHours` qui n’est pas immédiatement attendue retourne un type `Task<int>`, comme vous pourriez l’attendre de la déclaration de la méthode. La tâche est assignée à la variable `integerTask` dans l’exemple. Comme `integerTask` est un <xref:System.Threading.Tasks.Task%601>, il contient une propriété <xref:System.Threading.Tasks.Task%601.Result> de type `TResult`. Dans ce cas, `TResult` représente un type entier. Quand `await` est appliqué à `integerTask`, l’expression await prend pour la valeur le contenu de la propriété <xref:System.Threading.Tasks.Task%601.Result%2A> de `integerTask`. La valeur est assignée à la variable `ret`.  
  
> [!IMPORTANT]
> <xref:System.Threading.Tasks.Task%601.Result%2A> est une propriété bloquante. Si vous essayez d’y accéder avant la fin de sa tâche, le thread actif est bloqué tant que la tâche n’est pas terminée et que la valeur n’est pas disponible. Dans la plupart des cas, vous devez accéder à la valeur avec `await` au lieu d’accéder directement à la propriété. <br/> L’exemple précédent récupérait la valeur de la propriété <xref:System.Threading.Tasks.Task%601.Result%2A> pour bloquer le thread principal afin de permettre à la méthode `ShowTodaysInfo` de terminer son exécution avant la fin de l’application.  

[!code-csharp[return-value](../../../../../samples/snippets/csharp/programming-guide/async/async-returns1a.cs#1)]
  
## <a name="BKMK_TaskReturnType"></a> Type de retour Task  
Les méthodes async qui ne contiennent pas d’instruction `return` ou qui contiennent une instruction `return` ne retournant pas d’opérande ont généralement un type de retour <xref:System.Threading.Tasks.Task>. De telles méthodes retournent `void` si elles s’exécutent de façon synchrone. Si vous utilisez un type de retour <xref:System.Threading.Tasks.Task> pour une méthode async, une méthode d’appel peut utiliser un opérateur `await` pour suspendre l’achèvement de l’appelant jusqu’à ce que la méthode async soit terminée.  
  
Dans l’exemple suivant, la méthode async `WaitAndApologize` ne contient pas d’instruction `return`. Par conséquent, elle retourne un objet <xref:System.Threading.Tasks.Task>. Cela permet à `WaitAndApologize` d’être attendue. Notez que le type <xref:System.Threading.Tasks.Task> n’inclut pas de propriété `Result`, car il n’a pas de valeur de retour.  

[!code-csharp[return-value](../../../../../samples/snippets/csharp/programming-guide/async/async-returns2.cs)]  
  
`WaitAndApologize` est attendue avec une instruction await au lieu d’une expression await, comme pour l’instruction d’appel d’une méthode synchrone retournant un type void. Dans ce cas, l’application d’un opérateur await ne génère pas de valeur.  
  
Comme dans l’exemple <xref:System.Threading.Tasks.Task%601> précédent, vous pouvez séparer l’appel à `WaitAndApologize` de l’application d’un opérateur await, comme l’illustre le code suivant. Cependant, n’oubliez pas qu’un type `Task` n’a pas de propriété `Result` et qu’aucune valeur n’est générée quand un opérateur await est appliqué à un type `Task`.  
  
Le code suivant sépare l’appel à la méthode `WaitAndApologize` de l’attente de la tâche que retourne la méthode.  

[!code-csharp[return-value](../../../../../samples/snippets/csharp/programming-guide/async/async-returns2a.cs#1)]  

## <a name="BKMK_VoidReturnType"></a> Type de retour void

Vous utilisez le type de retour `void` dans les gestionnaires d’événements asynchrones, lesquels exigent un type de retour `void`. Pour les méthodes autres que les gestionnaires d’événements qui ne retournent pas de valeur, vous devez retourner <xref:System.Threading.Tasks.Task> à la place, car une méthode async qui retourne `void` ne peut pas être attendue. Tout appelant d’une telle méthode doit pouvoir continuer jusqu’à l’achèvement sans attendre que la méthode async soit terminée, et l’appelant doit être indépendant des valeurs ou des exceptions générées par la méthode async.  
  
L’appelant d’une méthode async qui retourne une valeur void ne peut pas intercepter les exceptions levées à partir de la méthode, et ces exceptions non gérées peuvent entraîner l’échec de votre application. Si une exception se produit dans une méthode async qui retourne <xref:System.Threading.Tasks.Task> ou <xref:System.Threading.Tasks.Task%601>, l’exception est stockée dans la tâche retournée et est à nouveau levée pendant l’attente de la tâche. Par conséquent, veillez à ce qu’une méthode async capable de générer une exception ait le type de retour <xref:System.Threading.Tasks.Task> ou <xref:System.Threading.Tasks.Task%601> et que les appels à la méthode soient attendus.  
  
Pour plus d’informations sur l’interception des exceptions dans les méthodes async, consultez la section [Exceptions dans les méthodes async](../../../language-reference/keywords/try-catch.md#exceptions-in-async-methods) de la rubrique [try-catch](../../../language-reference/keywords/try-catch.md).  
  
L’exemple suivant illustre le comportement d’un gestionnaire d’événements asynchrones. Notez que, dans l’exemple de code, un gestionnaire d’événements asynchrones doit informer le thread principal lorsqu’il a terminé. Le thread principal peut donc attendre la fin d’un gestionnaire d’événements asynchrones avant de quitter le programme.

[!code-csharp[return-value](../../../../../samples/snippets/csharp/programming-guide/async/async-returns3.cs)]  

## <a name="generalized-async-return-types-and-valuetasktresult"></a>Types de retour async généralisés et ValueTask\<TResult\>

À compter de C# 7.0, une méthode async peut retourner tout type ayant une méthode `GetAwaiter` accessible.

Étant donné que <xref:System.Threading.Tasks.Task> et <xref:System.Threading.Tasks.Task%601> sont des types référence, l’allocation de mémoire dans des chemins critiques pour les performances, en particulier quand les allocations se produisent dans des boucles serrées, peuvent nuire aux performances. La prise en charge de types de retour généralisés signifie que vous pouvez retourner un type valeur léger au lieu d’un type référence pour éviter des allocations de mémoire supplémentaires.

Le .NET fournit la structure <xref:System.Threading.Tasks.ValueTask%601?displayProperty=nameWithType> comme implémentation légère d’une valeur retournant des tâches généralisées. Pour utiliser le type <xref:System.Threading.Tasks.ValueTask%601?displayProperty=nameWithType>, vous devez ajouter le package NuGet `System.Threading.Tasks.Extensions` à votre projet. L’exemple suivant utilise la structure <xref:System.Threading.Tasks.ValueTask%601> pour récupérer la valeur de deux dés.
  
[!code-csharp[return-value](../../../../../samples/snippets/csharp/programming-guide/async/async-valuetask.cs)]

## <a name="see-also"></a>Voir aussi

- <xref:System.Threading.Tasks.Task.FromResult%2A>
- [Procédure pas à pas : accès au web avec async et await (C#)](./walkthrough-accessing-the-web-by-using-async-and-await.md)
- [Flux de contrôle dans les programmes Async (C)](./control-flow-in-async-programs.md)
- [Async](../../../language-reference/keywords/async.md)
- [Attendent](../../../language-reference/operators/await.md)
