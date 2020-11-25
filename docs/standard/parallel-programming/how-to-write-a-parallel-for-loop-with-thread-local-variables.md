---
title: 'Procédure : écrire une boucle Parallel.For avec des variables locales de thread'
description: Consultez un exemple d’écriture d’une boucle Parallel. for dans .NET qui utilise des variables de thread local, qui stockent et récupèrent l’État dans chaque tâche distincte de la boucle.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- parallel for loops, how to use local state
ms.assetid: 68384064-7ee7-41e2-90e3-71f00bde01bb
ms.openlocfilehash: f3adcfa98f4004f283b24bcd31dc243c18c2644c
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95729367"
---
# <a name="how-to-write-a-parallelfor-loop-with-thread-local-variables"></a>Procédure : écrire une boucle Parallel.For avec des variables locales de thread

Cet exemple montre comment utiliser des variables de thread local pour stocker et récupérer l’état de chaque tâche créée par une boucle <xref:System.Threading.Tasks.Parallel.For%2A>. En utilisant des données de thread local, vous pouvez éviter la surcharge liée à la synchronisation d’un grand nombre d’accès à un état partagé. Au lieu d’écrire dans une ressource partagée à chaque itération, vous calculez et stockez la valeur jusqu’à ce que toutes les itérations de la tâche soient terminées. Vous pouvez ensuite écrire une fois le résultat final dans la ressource partagée ou le transmettre à une autre méthode.  
  
## <a name="example"></a>Exemple  

 L'exemple suivant appelle la méthode <xref:System.Threading.Tasks.Parallel.For%60%601%28System.Int32%2CSystem.Int32%2CSystem.Func%7B%60%600%7D%2CSystem.Func%7BSystem.Int32%2CSystem.Threading.Tasks.ParallelLoopState%2C%60%600%2C%60%600%7D%2CSystem.Action%7B%60%600%7D%29> pour calculer la somme des valeurs d'un tableau qui contient un million d'éléments. La valeur de chaque élément est égale à son index.  
  
 [!code-csharp[TPL_Parallel#05](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_parallel/cs/forandforeach_simple.cs#05)]
 [!code-vb[TPL_Parallel#05](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_parallel/vb/forwiththreadlocal.vb#05)]  
  
 Les deux premiers paramètres de chaque méthode <xref:System.Threading.Tasks.Parallel.For%2A> spécifient les valeurs d'itération initiale et finale. Dans cette surcharge de la méthode, le troisième paramètre indique où vous initialisez votre état local. Dans ce contexte, « état local » signifie une variable dont la durée de vie commence juste avant la première itération de la boucle sur le thread actuel et se termine juste après la dernière itération.  
  
 Le type du troisième paramètre est un délégué <xref:System.Func%601> où `TResult` représente le type de la variable destinée à stocker l'état de thread local. Son type est défini par l’argument de type générique fourni au moment de l’appel de la méthode <xref:System.Threading.Tasks.Parallel.For%60%601%28System.Int32%2CSystem.Int32%2CSystem.Func%7B%60%600%7D%2CSystem.Func%7BSystem.Int32%2CSystem.Threading.Tasks.ParallelLoopState%2C%60%600%2C%60%600%7D%2CSystem.Action%7B%60%600%7D%29> générique, en l’occurrence <xref:System.Int64>. L’argument de type indique au compilateur le type de la variable temporaire à utiliser pour stocker l’état de thread local. Dans cet exemple, l'expression `() => 0` (ou `Function() 0` dans Visual Basic) initialise la variable de thread local à zéro. Si l'argument de type générique est un type de référence ou un type de valeur défini par l'utilisateur, l'expression ressemble à ceci :  
  
```csharp  
() => new MyClass()  
```  
  
```vb  
Function() new MyClass()  
```  
  
 Le quatrième paramètre définit la logique de la boucle. Il doit correspondre à un délégué ou à une expression lambda dont la signature est `Func<int, ParallelLoopState, long, long>` en C# ou `Func(Of Integer, ParallelLoopState, Long, Long)` en Visual Basic. Le premier paramètre est la valeur du compteur de boucle pour cette itération de la boucle. Le deuxième est un objet <xref:System.Threading.Tasks.ParallelLoopState> qui permet de quitter la boucle ; cet objet est fourni par la classe <xref:System.Threading.Tasks.Parallel> à chaque occurrence de la boucle. Le troisième paramètre est la variable de thread local. Le dernier paramètre est le type de retour. Dans ce cas, le type est <xref:System.Int64>, car c’est ce type que nous avons spécifié dans l’argument de type <xref:System.Threading.Tasks.Parallel.For%2A>. Cette variable est nommée `subtotal` et est retournée par l'expression lambda. La valeur de retour est utilisée pour initialiser `subtotal` à chaque itération suivante de la boucle. Vous pouvez également considérer ce dernier paramètre comme une valeur transmise à chaque itération, puis communiquée au délégué `localFinally` quand la dernière itération est terminée.  
  
 Le cinquième paramètre définit la méthode qui est appelée une fois, après la fin de toutes les itérations sur un thread particulier. Le type de l'argument d'entrée correspond de nouveau à l'argument de type de la méthode <xref:System.Threading.Tasks.Parallel.For%60%601%28System.Int32%2CSystem.Int32%2CSystem.Func%7B%60%600%7D%2CSystem.Func%7BSystem.Int32%2CSystem.Threading.Tasks.ParallelLoopState%2C%60%600%2C%60%600%7D%2CSystem.Action%7B%60%600%7D%29> et au type retourné par l'expression lambda du corps. Dans cet exemple, la valeur est ajoutée à une variable à portée de classe d'une façon thread-safe en appelant la méthode <xref:System.Threading.Interlocked.Add%2A?displayProperty=nameWithType>. L'utilisation d'une variable de thread local nous a évité d'écrire dans cette variable de classe à chaque itération de la boucle.  
  
 Pour plus d’informations sur l’utilisation d’expressions lambda, consultez [Expressions lambda en PLINQ et dans la bibliothèque parallèle de tâches](lambda-expressions-in-plinq-and-tpl.md).  
  
## <a name="see-also"></a>Voir aussi

- [Parallélisme des données](data-parallelism-task-parallel-library.md)
- [Programmation parallèle](index.md)
- [Bibliothèque parallèle de tâches](task-parallel-library-tpl.md)
- [Expressions lambda dans PLINQ et TPL](lambda-expressions-in-plinq-and-tpl.md)
