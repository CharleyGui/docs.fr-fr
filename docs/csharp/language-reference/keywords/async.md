---
title: async - Référence C#
ms.date: 05/22/2017
f1_keywords:
- async_CSharpKeyword
helpviewer_keywords:
- async keyword [C#]
- async method [C#]
- async [C#]
ms.assetid: 16f14f09-b2ce-42c7-a875-e4eca5d50674
ms.openlocfilehash: 279ea2f9875681401c9c7acab922d9e4424e6827
ms.sourcegitcommit: 7476c20d2f911a834a00b8a7f5e8926bae6804d9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/11/2020
ms.locfileid: "88062533"
---
# <a name="async-c-reference"></a>async (référence C#)

Utilisez le modificateur `async` pour spécifier qu’une méthode, une [expression lambda](../operators/lambda-expressions.md) ou une [méthode anonyme](../operators/delegate-operator.md) sont asynchrones. Si vous utilisez ce modificateur sur une méthode ou une expression, il s’agit d’une *méthode async*. L’exemple suivant définit une méthode async nommée `ExampleMethodAsync` :
  
```csharp  
public async Task<int> ExampleMethodAsync()  
{  
    // . . . .  
}  
```  

Si vous débutez en programmation asynchrone ou que vous ne comprenez pas comment une méthode Async utilise l' [ `await` opérateur](../operators/await.md) pour effectuer un travail potentiellement long sans bloquer le thread de l’appelant, lisez l’introduction de la [programmation asynchrone avec Async et await](../../programming-guide/concepts/async/index.md). Le code suivant se trouve dans une méthode async et appelle la méthode <xref:System.Net.Http.HttpClient.GetStringAsync%2a?displayProperty=nameWithType> :
  
```csharp  
string contents = await httpClient.GetStringAsync(requestUrl);  
```  
  
Une méthode async s’exécute de façon synchrone jusqu’à ce qu’elle atteigne sa première expression `await`, où elle est suspendue jusqu’à ce que la tâche attendue soit terminée. Dans le même temps, le contrôle retourne à l'appelant de la méthode, comme le montre l'exemple indiqué dans la section suivante.  
  
Si la méthode que le mot clé `async` modifie ne contient pas une expression ou une instruction `await`, la méthode s'exécute de façon synchrone. Un avertissement du compilateur vous signale toutes les méthodes async qui ne contiennent pas d’instructions `await`, car cette situation peut indiquer une erreur. Consultez [Avertissement du compilateur (niveau 1) CS4014](../compiler-messages/cs4014.md).  
  
 Le mot clé `async` est contextuel, car il est un mot clé uniquement lorsqu'il modifie une méthode, une expression lambda ou une méthode anonyme. Dans tous les autres contextes, il est interprété comme un identificateur.  
  
## <a name="example"></a>Exemple  
L'exemple suivant montre la structure et le flux de contrôle entre un gestionnaire d'événements asynchrones, `StartButton_Click`, et une méthode async, `ExampleMethodAsync`. Le résultat de la méthode async est le nombre de caractères d’une page web. Le code convient pour une application WPF (Windows Presentation Foundation) ou une application du Windows Store que vous créez dans Visual Studio ; consultez les commentaires du code pour configurer l’application.  

Vous pouvez exécuter ce code dans Visual Studio en tant qu’application Windows Presentation Foundation (WPF) ou qu’application du Windows Store. Vous avez besoin d’un contrôle Button nommé `StartButton` et d’un contrôle Textbox nommé `ResultsTextBox`. N’oubliez pas de définir les noms et le gestionnaire afin d’obtenir un résultat semblable à ceci :  

```xaml
<Button Content="Button" HorizontalAlignment="Left" Margin="88,77,0,0" VerticalAlignment="Top" Width="75"  
        Click="StartButton_Click" Name="StartButton"/>  
<TextBox HorizontalAlignment="Left" Height="137" Margin="88,140,0,0" TextWrapping="Wrap"
         Text="&lt;Enter a URL&gt;" VerticalAlignment="Top" Width="310" Name="ResultsTextBox"/>  
```
  
Pour exécuter le code en tant qu’application WPF :  

- Collez ce code dans la classe `MainWindow` dans MainWindow.xaml.cs.  
- Ajoutez une référence à System.Net.Http.  
- Ajoutez une directive `using` à System.Net.Http.  
  
Pour exécuter le code comme une application du Windows Store :  

- Collez ce code dans la classe `MainPage` dans MainPage.xaml.cs.  
- Ajouter des directives using pour System.Net.Http et System.Threading.Tasks.  
  
[!code-csharp[wpf-async](../../../../samples/snippets/csharp/language-reference/keywords/async/wpf/mainwindow.xaml.cs#1)]
  
> [!IMPORTANT]
> Pour plus d’informations sur les tâches et sur le code qui s’exécute en attendant une tâche, consultez [Programmation asynchrone avec async et await](../../programming-guide/concepts/async/index.md). Pour obtenir un exemple WPF complet qui utilise des éléments similaires, consultez [Procédure pas à pas : accès au web avec Async et Await](../../programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md).  
  
## <a name="return-types"></a>Types de retour  
Une méthode async peut avoir les types de retour suivants :

- <xref:System.Threading.Tasks.Task>
- <xref:System.Threading.Tasks.Task%601>
- [void](../builtin-types/void.md). Les méthodes `async void` sont généralement déconseillées pour le code autre que les gestionnaires d’événements parce que les appelants ne peuvent pas `await` ces méthodes et doivent implémenter un mécanisme différent pour signaler les conditions d’erreur ou les complétions réussies.
- À compter de C# 7.0, tout type ayant une méthode `GetAwaiter` accessible. Le type `System.Threading.Tasks.ValueTask<TResult>` est une implémentation de ce genre. Il est disponible en ajoutant le package NuGet `System.Threading.Tasks.Extensions`.

La méthode async ne peut déclarer aucun paramètre [in](./in-parameter-modifier.md), [ref](./ref.md) ou [out](./out-parameter-modifier.md), ni avoir une [valeur de retour de référence](../../programming-guide/classes-and-structs/ref-returns.md), mais elle peut appeler des méthodes qui ont ces paramètres.  
  
Vous spécifiez `Task<TResult>` comme type de retour d’une méthode async si l’instruction [return](./return.md) de la méthode spécifie un opérande de type `TResult`. Utilisez `Task` si aucune valeur significative n'est retournée lorsque la méthode est terminée. En d'autres termes, un appel à la méthode retourne `Task`, mais lorsque `Task` est terminé, toute expression `await` qui attend `Task` prend la valeur `void`.  
  
Vous utilisez le type de retour `void` principalement pour définir les gestionnaires d'événements, qui ont besoin de ce type de retour. L'appelant d'une méthode async retournant `void` ne peut pas l'attendre et ne peut pas intercepter les exceptions levées par la méthode.  

À partir de C# 7.0, vous retournez un autre type, en général un type valeur, qui a une méthode `GetAwaiter` permettant de limiter les allocations de mémoire dans les sections de code critiques pour les performances.

Pour obtenir plus d’informations et des exemples, consultez [Types de retour Async](../../programming-guide/concepts/async/async-return-types.md).  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Runtime.CompilerServices.AsyncStateMachineAttribute>
- [await](../operators/await.md)
- [Procédure pas à pas : accès au Web avec Async et await](../../programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md)
- [Programmation asynchrone avec Async et await](../../programming-guide/concepts/async/index.md)
