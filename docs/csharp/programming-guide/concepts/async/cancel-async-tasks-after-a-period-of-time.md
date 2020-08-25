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
# <a name="cancel-async-tasks-after-a-period-of-time-c"></a><span data-ttu-id="57fa6-103">Annuler des tâches async après une période spécifique (C#)</span><span class="sxs-lookup"><span data-stu-id="57fa6-103">Cancel async tasks after a period of time (C#)</span></span>

<span data-ttu-id="57fa6-104">Vous pouvez annuler une opération asynchrone au bout d’un certain temps à l’aide de la <xref:System.Threading.CancellationTokenSource.CancelAfter%2A?displayProperty=nameWithType> méthode si vous ne souhaitez pas attendre la fin de l’opération.</span><span class="sxs-lookup"><span data-stu-id="57fa6-104">You can cancel an asynchronous operation after a period of time by using the <xref:System.Threading.CancellationTokenSource.CancelAfter%2A?displayProperty=nameWithType> method if you don't want to wait for the operation to finish.</span></span> <span data-ttu-id="57fa6-105">Cette méthode planifie l’annulation de toutes les tâches associées qui ne sont pas terminées dans le délai indiqué par l' `CancelAfter` expression.</span><span class="sxs-lookup"><span data-stu-id="57fa6-105">This method schedules the cancellation of any associated tasks that aren't complete within the period of time that's designated by the `CancelAfter` expression.</span></span>

<span data-ttu-id="57fa6-106">Cet exemple ajoute au code développé dans [annuler une liste de tâches (C#)](cancel-an-async-task-or-a-list-of-tasks.md) pour télécharger une liste de sites Web et afficher la longueur du contenu de chacun d’eux.</span><span class="sxs-lookup"><span data-stu-id="57fa6-106">This example adds to the code that's developed in [Cancel a list of tasks (C#)](cancel-an-async-task-or-a-list-of-tasks.md) to download a list of websites and to display the length of the contents of each one.</span></span>

<span data-ttu-id="57fa6-107">Ce didacticiel contient les sections suivantes :</span><span class="sxs-lookup"><span data-stu-id="57fa6-107">This tutorial covers:</span></span>

> [!div class="checklist"]
>
> - <span data-ttu-id="57fa6-108">Mise à jour d’une application console .NET existante</span><span class="sxs-lookup"><span data-stu-id="57fa6-108">Updating an existing .NET console application</span></span>
> - <span data-ttu-id="57fa6-109">Planification d’une annulation</span><span class="sxs-lookup"><span data-stu-id="57fa6-109">Scheduling a cancellation</span></span>

## <a name="prerequisites"></a><span data-ttu-id="57fa6-110">Prérequis</span><span class="sxs-lookup"><span data-stu-id="57fa6-110">Prerequisites</span></span>

<span data-ttu-id="57fa6-111">Ce didacticiel requiert les éléments suivants :</span><span class="sxs-lookup"><span data-stu-id="57fa6-111">This tutorial requires the following:</span></span>

- <span data-ttu-id="57fa6-112">Vous êtes censé avoir créé une application dans le didacticiel [annuler une liste de tâches (C#)](cancel-an-async-task-or-a-list-of-tasks.md)</span><span class="sxs-lookup"><span data-stu-id="57fa6-112">You're expected to have created an application in the [Cancel a list of tasks (C#)](cancel-an-async-task-or-a-list-of-tasks.md) tutorial</span></span>
- [<span data-ttu-id="57fa6-113">.NET 5,0 ou kit de développement logiciel (SDK) ultérieur</span><span class="sxs-lookup"><span data-stu-id="57fa6-113">.NET 5.0 or later SDK</span></span>](https://dotnet.microsoft.com/download/dotnet/5.0)
- <span data-ttu-id="57fa6-114">Environnement de développement intégré (IDE)</span><span class="sxs-lookup"><span data-stu-id="57fa6-114">Integrated development environment (IDE)</span></span>
  - [<span data-ttu-id="57fa6-115">Nous vous recommandons Visual Studio, Visual Studio Code ou Visual Studio pour Mac</span><span class="sxs-lookup"><span data-stu-id="57fa6-115">We recommend Visual Studio, Visual Studio Code, or Visual Studio for Mac</span></span>](https://visualstudio.microsoft.com)

## <a name="update-application-entry-point"></a><span data-ttu-id="57fa6-116">Mettre à jour le point d’entrée de l’application</span><span class="sxs-lookup"><span data-stu-id="57fa6-116">Update application entry point</span></span>

<span data-ttu-id="57fa6-117">Remplacez la `Main` méthode existante par le code suivant :</span><span class="sxs-lookup"><span data-stu-id="57fa6-117">Replace the existing `Main` method with the following:</span></span>

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

<span data-ttu-id="57fa6-118">La méthode mise à jour `Main` écrit quelques messages d’instructions dans la console.</span><span class="sxs-lookup"><span data-stu-id="57fa6-118">The updated `Main` method writes a few instructional messages to the console.</span></span> <span data-ttu-id="57fa6-119">Dans le bloc [try](../../../language-reference/keywords/try-catch.md), un appel à <xref:System.Threading.CancellationTokenSource.CancelAfter(System.Int32)?displayProperty=nameWithType> pour planifier une annulation.</span><span class="sxs-lookup"><span data-stu-id="57fa6-119">Within the [try catch](../../../language-reference/keywords/try-catch.md), a call to <xref:System.Threading.CancellationTokenSource.CancelAfter(System.Int32)?displayProperty=nameWithType> to schedule a cancellation.</span></span> <span data-ttu-id="57fa6-120">Cela signalera l’annulation après un certain laps de temps.</span><span class="sxs-lookup"><span data-stu-id="57fa6-120">This will signal cancellation after a period of time.</span></span>

<span data-ttu-id="57fa6-121">Ensuite, la `SumPageSizesAsync` méthode est attendue.</span><span class="sxs-lookup"><span data-stu-id="57fa6-121">Next, the `SumPageSizesAsync` method is awaited.</span></span> <span data-ttu-id="57fa6-122">Si le traitement de toutes les URL se produit plus rapidement que l’annulation planifiée, l’application se termine.</span><span class="sxs-lookup"><span data-stu-id="57fa6-122">If processing all of the URLs occurs faster than the scheduled cancellation, the application ends.</span></span> <span data-ttu-id="57fa6-123">Toutefois, si l’annulation planifiée est déclenchée avant le traitement de toutes les URL, une <xref:System.Threading.Tasks.TaskCanceledException> est levée.</span><span class="sxs-lookup"><span data-stu-id="57fa6-123">However, if the scheduled cancellation is triggered before all of the URLs are processed, a <xref:System.Threading.Tasks.TaskCanceledException> is thrown.</span></span>

### <a name="example-application-output"></a><span data-ttu-id="57fa6-124">Exemple de sortie d’application</span><span class="sxs-lookup"><span data-stu-id="57fa6-124">Example application output</span></span>

```console
Application started.

https://docs.microsoft.com                                       37,357
https://docs.microsoft.com/aspnet/core                           85,589
https://docs.microsoft.com/azure                                398,939
https://docs.microsoft.com/azure/devops                          73,663

Tasks cancelled: timed out.

Application ending.
```

## <a name="complete-example"></a><span data-ttu-id="57fa6-125">Exemple complet</span><span class="sxs-lookup"><span data-stu-id="57fa6-125">Complete example</span></span>

<span data-ttu-id="57fa6-126">Le code suivant est le texte complet du fichier *Program.cs* pour l’exemple.</span><span class="sxs-lookup"><span data-stu-id="57fa6-126">The following code is the complete text of the *Program.cs* file for the example.</span></span>

:::code language="csharp" source="snippets/cancel-tasks/cancel-task-after-period-of-time/Program.cs":::

## <a name="see-also"></a><span data-ttu-id="57fa6-127">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="57fa6-127">See also</span></span>

- <xref:System.Threading.CancellationToken>
- <xref:System.Threading.CancellationTokenSource>
- [<span data-ttu-id="57fa6-128">Programmation asynchrone avec Async et await (C#)</span><span class="sxs-lookup"><span data-stu-id="57fa6-128">Asynchronous programming with async and await (C#)</span></span>](index.md)
- [<span data-ttu-id="57fa6-129">Annuler une liste de tâches (C#)</span><span class="sxs-lookup"><span data-stu-id="57fa6-129">Cancel a list of tasks (C#)</span></span>](cancel-an-async-task-or-a-list-of-tasks.md)
