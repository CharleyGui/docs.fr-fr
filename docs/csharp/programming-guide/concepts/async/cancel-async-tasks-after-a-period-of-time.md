---
title: Annuler des tâches asynchrones après une période de temps (C#)
description: Découvrez comment planifier l’annulation de toutes les tâches associées qui ne sont pas terminées dans un laps de temps donné.
ms.date: 08/19/2020
ms.topic: tutorial
ms.assetid: 194282c2-399f-46da-a7a6-96674e00b0b3
ms.openlocfilehash: ad9064f8f45a737982ffc35ab4ea2395ddae9016
ms.sourcegitcommit: 9c45035b781caebc63ec8ecf912dc83fb6723b1f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/25/2020
ms.locfileid: "88811416"
---
# <a name="cancel-async-tasks-after-a-period-of-time-c"></a>Annuler des tâches async après une période spécifique (C#)

Vous pouvez annuler une opération asynchrone au bout d’un certain temps à l’aide de la <xref:System.Threading.CancellationTokenSource.CancelAfter%2A?displayProperty=nameWithType> méthode si vous ne souhaitez pas attendre la fin de l’opération. Cette méthode planifie l’annulation de toutes les tâches associées qui ne sont pas terminées dans le délai indiqué par l' `CancelAfter` expression.

Cet exemple ajoute au code développé dans [annuler une liste de tâches (C#)](cancel-an-async-task-or-a-list-of-tasks.md) pour télécharger une liste de sites Web et afficher la longueur du contenu de chacun d’eux.

Ce didacticiel contient les sections suivantes :

> [!div class="checklist"]
>
> - Mise à jour d’une application console .NET existante
> - Planification d’une annulation

## <a name="prerequisites"></a>Prérequis

Ce didacticiel requiert les éléments suivants :

- Vous êtes censé avoir créé une application dans le didacticiel [annuler une liste de tâches (C#)](cancel-an-async-task-or-a-list-of-tasks.md)
- [.NET 5,0 ou kit de développement logiciel (SDK) ultérieur](https://dotnet.microsoft.com/download/dotnet/5.0)
- Environnement de développement intégré (IDE)
  - [Nous vous recommandons Visual Studio, Visual Studio Code ou Visual Studio pour Mac](https://visualstudio.microsoft.com)

## <a name="update-application-entry-point"></a>Mettre à jour le point d’entrée de l’application

Remplacez la `Main` méthode existante par le code suivant :

```csharp
static async Task Main()
{
    Console.WriteLine("Application started.");

    try
    {
        s_cts.CancelAfter(3500);

        await SumPageSizesAsync();
    }
    catch (TaskCanceledException)
    {
        Console.WriteLine("\nTasks cancelled: timed out.\n");
    }

    Console.WriteLine("Application ending.");
}
```

La méthode mise à jour `Main` écrit quelques messages d’instructions dans la console. Dans le bloc [try](../../../language-reference/keywords/try-catch.md), un appel à <xref:System.Threading.CancellationTokenSource.CancelAfter(System.Int32)?displayProperty=nameWithType> pour planifier une annulation. Cela signalera l’annulation après un certain laps de temps.

Ensuite, la `SumPageSizesAsync` méthode est attendue. Si le traitement de toutes les URL se produit plus rapidement que l’annulation planifiée, l’application se termine. Toutefois, si l’annulation planifiée est déclenchée avant le traitement de toutes les URL, une <xref:System.Threading.Tasks.TaskCanceledException> est levée.

### <a name="example-application-output"></a>Exemple de sortie d’application

```console
Application started.

https://docs.microsoft.com                                       37,357
https://docs.microsoft.com/aspnet/core                           85,589
https://docs.microsoft.com/azure                                398,939
https://docs.microsoft.com/azure/devops                          73,663

Tasks cancelled: timed out.

Application ending.
```

## <a name="complete-example"></a>Exemple complet

Le code suivant est le texte complet du fichier *Program.cs* pour l’exemple.

:::code language="csharp" source="snippets/cancel-tasks/cancel-task-after-period-of-time/Program.cs":::

## <a name="see-also"></a>Voir aussi

- <xref:System.Threading.CancellationToken>
- <xref:System.Threading.CancellationTokenSource>
- [Programmation asynchrone avec Async et await (C#)](index.md)
- [Annuler une liste de tâches (C#)](cancel-an-async-task-or-a-list-of-tasks.md)
