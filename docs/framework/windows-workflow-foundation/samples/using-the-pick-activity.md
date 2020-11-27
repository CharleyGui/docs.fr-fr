---
title: Utilisation de l'activité Pick
ms.date: 03/30/2017
ms.assetid: b89be812-a247-4025-b0e3-ffb20db027a6
ms.openlocfilehash: df8570a61c7bfbfacc00b0896156135ecf2a0c32
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96267453"
---
# <a name="using-the-pick-activity"></a><span data-ttu-id="a4af4-102">Utilisation de l'activité Pick</span><span class="sxs-lookup"><span data-stu-id="a4af4-102">Using the Pick Activity</span></span>

<span data-ttu-id="a4af4-103">Cet exemple montre comment utiliser l'activité <xref:System.Activities.Statements.Pick>.</span><span class="sxs-lookup"><span data-stu-id="a4af4-103">This sample demonstrates how to use the <xref:System.Activities.Statements.Pick> activity.</span></span>

 <span data-ttu-id="a4af4-104">L'activité <xref:System.Activities.Statements.Pick> fournit une modélisation de contrôle basée sur les événements.</span><span class="sxs-lookup"><span data-stu-id="a4af4-104">The <xref:System.Activities.Statements.Pick> activity provides event-based control modeling.</span></span> <span data-ttu-id="a4af4-105">Le comportement est semblable à celui de l’instruction `switch` de C#, qui exécute une seule des branches dans l’instruction `switch`.</span><span class="sxs-lookup"><span data-stu-id="a4af4-105">It behaves similar to the C# `switch` statement, which executes only one of the branches in the `switch` statement.</span></span> <span data-ttu-id="a4af4-106">Contrairement à l’instruction `switch` dans laquelle une branche est exécutée en fonction d’une valeur, l’activité <xref:System.Activities.Statements.Pick> exécute une branche en fonction de l’exécution d’une activité.</span><span class="sxs-lookup"><span data-stu-id="a4af4-106">Unlike the `switch` statement in which a branch is executed based upon on a value, the <xref:System.Activities.Statements.Pick> activity executes a branch based upon how an activity completes.</span></span>

 <span data-ttu-id="a4af4-107">Cet exemple invite un utilisateur à taper son nom sur la console dans une période de temps donné.</span><span class="sxs-lookup"><span data-stu-id="a4af4-107">This sample prompts a user to type in their name on the console within a given time period.</span></span> <span data-ttu-id="a4af4-108">L’activité <xref:System.Activities.Statements.Pick> dans l’exemple a deux branches qui sont exécutées selon si l’utilisateur tape son nom dans les 5 secondes ou non.</span><span class="sxs-lookup"><span data-stu-id="a4af4-108">The <xref:System.Activities.Statements.Pick> activity in the sample has two branches that are executed based upon whether the user types in their name within 5 seconds or not.</span></span> <span data-ttu-id="a4af4-109">Si l'utilisateur tape son nom dans les 5 secondes, la première branche, qui contient une activité `ReadLine` personnalisée est exécutée ; sinon, l'autre branche, qui contient une activité <xref:System.Activities.Statements.Delay> est exécutée.</span><span class="sxs-lookup"><span data-stu-id="a4af4-109">If the user types in their name within 5 seconds, the first branch is executed, which contains a custom `ReadLine` activity; otherwise the other branch is executed, which contains a <xref:System.Activities.Statements.Delay> activity.</span></span> <span data-ttu-id="a4af4-110">Une fois qu'un nom d'utilisateur est tapé sur la console, il est imprimé sur la console.</span><span class="sxs-lookup"><span data-stu-id="a4af4-110">Once a user’s name is typed in on the console, the user’s name is printed on the console.</span></span> <span data-ttu-id="a4af4-111">Si rien n'est entré dans les 5 secondes, l'opération expire.</span><span class="sxs-lookup"><span data-stu-id="a4af4-111">If an input is not entered within 5 seconds, the operation is timed out.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="a4af4-112">Illustre le</span><span class="sxs-lookup"><span data-stu-id="a4af4-112">Demonstrates</span></span>

 <span data-ttu-id="a4af4-113">Activité <xref:System.Activities.Statements.Pick></span><span class="sxs-lookup"><span data-stu-id="a4af4-113"><xref:System.Activities.Statements.Pick> activity.</span></span>

## <a name="discussion"></a><span data-ttu-id="a4af4-114">Discussions</span><span class="sxs-lookup"><span data-stu-id="a4af4-114">Discussion</span></span>

 <span data-ttu-id="a4af4-115">L'exemple inclut un workflow de concepteur et un workflow encodé.</span><span class="sxs-lookup"><span data-stu-id="a4af4-115">The sample includes a Designer workflow and coded workflow.</span></span>

 <span data-ttu-id="a4af4-116">Flux de travail du concepteur la version du concepteur de l’exemple montre comment créer un flux de travail dans le concepteur.</span><span class="sxs-lookup"><span data-stu-id="a4af4-116">Designer Workflow The Designer version of the sample demonstrates how to create a workflow in the designer.</span></span> <span data-ttu-id="a4af4-117">Les fichiers suivants sont inclus :</span><span class="sxs-lookup"><span data-stu-id="a4af4-117">The following files are included:</span></span>

- <span data-ttu-id="a4af4-118">Program.cs : inclut la fonction `Main` qui exécute l'exemple de workflow.</span><span class="sxs-lookup"><span data-stu-id="a4af4-118">Program.cs : Includes the `Main` function that executes the sample workflow.</span></span>

- <span data-ttu-id="a4af4-119">ReadString.cs : activité personnalisée qui lit une entrée de la console.</span><span class="sxs-lookup"><span data-stu-id="a4af4-119">ReadString.cs: A custom activity that reads some input from the console.</span></span>

- <span data-ttu-id="a4af4-120">Sequence1.xaml : workflow créé à l'aide du concepteur qui utilise Pick.</span><span class="sxs-lookup"><span data-stu-id="a4af4-120">Sequence1.xaml: A workflow created using the designer that uses Pick.</span></span>

 <span data-ttu-id="a4af4-121">Flux de travail codé la version codée de l’exemple montre comment créer un flux de travail dans le concepteur.</span><span class="sxs-lookup"><span data-stu-id="a4af4-121">Coded Workflow The coded version of the sample demonstrates how to create a workflow in the designer.</span></span> <span data-ttu-id="a4af4-122">Les fichiers suivants sont inclus :</span><span class="sxs-lookup"><span data-stu-id="a4af4-122">The following files are included:</span></span>

- <span data-ttu-id="a4af4-123">Program.cs : inclut la fonction `Main` qui exécute l'exemple de workflow.</span><span class="sxs-lookup"><span data-stu-id="a4af4-123">Program.cs : Includes the `Main` function that executes the sample workflow.</span></span>

- <span data-ttu-id="a4af4-124">ReadString.cs : activité personnalisée qui lit une entrée de la console.</span><span class="sxs-lookup"><span data-stu-id="a4af4-124">ReadString.cs: A custom activity that reads some input from the console.</span></span>

#### <a name="to-use-this-sample"></a><span data-ttu-id="a4af4-125">Pour utiliser cet exemple</span><span class="sxs-lookup"><span data-stu-id="a4af4-125">To use this sample</span></span>

1. <span data-ttu-id="a4af4-126">À l’aide de Visual Studio 2010, ouvrez le fichier solution Pick. sln.</span><span class="sxs-lookup"><span data-stu-id="a4af4-126">Using Visual Studio 2010, open the Pick.sln solution file.</span></span>

2. <span data-ttu-id="a4af4-127">Pour générer la solution, appuyez sur Ctrl+Maj+B.</span><span class="sxs-lookup"><span data-stu-id="a4af4-127">To build the solution, press CTRL+SHIFT+B.</span></span>

3. <span data-ttu-id="a4af4-128">Pour exécuter la solution, appuyez sur F5.</span><span class="sxs-lookup"><span data-stu-id="a4af4-128">To run the solution, press F5.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="a4af4-129">Les exemples peuvent déjà être installés sur votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="a4af4-129">The samples may already be installed on your machine.</span></span> <span data-ttu-id="a4af4-130">Recherchez le répertoire (par défaut) suivant avant de continuer.</span><span class="sxs-lookup"><span data-stu-id="a4af4-130">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="a4af4-131">Si ce répertoire n’existe pas, accédez à [Windows Communication Foundation (WCF) et Windows Workflow Foundation (WF) exemples pour .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) pour télécharger tous les exemples Windows Communication Foundation (WCF) et [!INCLUDE[wf1](../../../../includes/wf1-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="a4af4-131">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="a4af4-132">Cet exemple se trouve dans le répertoire suivant.</span><span class="sxs-lookup"><span data-stu-id="a4af4-132">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Built-InActivities\Pick`
