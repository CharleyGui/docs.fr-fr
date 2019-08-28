---
title: Utilisation de l'activité Pick
ms.date: 03/30/2017
ms.assetid: b89be812-a247-4025-b0e3-ffb20db027a6
ms.openlocfilehash: 03b9ff7f552ad0cdcfbe9c46121a2f46f35de52a
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/27/2019
ms.locfileid: "70037880"
---
# <a name="using-the-pick-activity"></a><span data-ttu-id="34fc9-102">Utilisation de l'activité Pick</span><span class="sxs-lookup"><span data-stu-id="34fc9-102">Using the Pick Activity</span></span>
<span data-ttu-id="34fc9-103">Cet exemple montre comment utiliser l'activité <xref:System.Activities.Statements.Pick>.</span><span class="sxs-lookup"><span data-stu-id="34fc9-103">This sample demonstrates how to use the <xref:System.Activities.Statements.Pick> activity.</span></span>

 <span data-ttu-id="34fc9-104">L'activité <xref:System.Activities.Statements.Pick> fournit une modélisation de contrôle basée sur les événements.</span><span class="sxs-lookup"><span data-stu-id="34fc9-104">The <xref:System.Activities.Statements.Pick> activity provides event-based control modeling.</span></span> <span data-ttu-id="34fc9-105">Le comportement est semblable à celui de l’instruction `switch` de C#, qui exécute une seule des branches dans l’instruction `switch`.</span><span class="sxs-lookup"><span data-stu-id="34fc9-105">It behaves similar to the C# `switch` statement, which executes only one of the branches in the `switch` statement.</span></span> <span data-ttu-id="34fc9-106">Contrairement à l’instruction `switch` dans laquelle une branche est exécutée en fonction d’une valeur, l’activité <xref:System.Activities.Statements.Pick> exécute une branche en fonction de l’exécution d’une activité.</span><span class="sxs-lookup"><span data-stu-id="34fc9-106">Unlike the `switch` statement in which a branch is executed based upon on a value, the <xref:System.Activities.Statements.Pick> activity executes a branch based upon how an activity completes.</span></span>

 <span data-ttu-id="34fc9-107">Cet exemple invite un utilisateur à taper son nom sur la console dans une période de temps donné.</span><span class="sxs-lookup"><span data-stu-id="34fc9-107">This sample prompts a user to type in their name on the console within a given time period.</span></span> <span data-ttu-id="34fc9-108">L’activité <xref:System.Activities.Statements.Pick> dans l’exemple a deux branches qui sont exécutées selon si l’utilisateur tape son nom dans les 5 secondes ou non.</span><span class="sxs-lookup"><span data-stu-id="34fc9-108">The <xref:System.Activities.Statements.Pick> activity in the sample has two branches that are executed based upon whether the user types in their name within 5 seconds or not.</span></span> <span data-ttu-id="34fc9-109">Si l'utilisateur tape son nom dans les 5 secondes, la première branche, qui contient une activité `ReadLine` personnalisée est exécutée ; sinon, l'autre branche, qui contient une activité <xref:System.Activities.Statements.Delay> est exécutée.</span><span class="sxs-lookup"><span data-stu-id="34fc9-109">If the user types in their name within 5 seconds, the first branch is executed, which contains a custom `ReadLine` activity; otherwise the other branch is executed, which contains a <xref:System.Activities.Statements.Delay> activity.</span></span> <span data-ttu-id="34fc9-110">Une fois qu'un nom d'utilisateur est tapé sur la console, il est imprimé sur la console.</span><span class="sxs-lookup"><span data-stu-id="34fc9-110">Once a user’s name is typed in on the console, the user’s name is printed on the console.</span></span> <span data-ttu-id="34fc9-111">Si rien n'est entré dans les 5 secondes, l'opération expire.</span><span class="sxs-lookup"><span data-stu-id="34fc9-111">If an input is not entered within 5 seconds, the operation is timed out.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="34fc9-112">Démonstrations</span><span class="sxs-lookup"><span data-stu-id="34fc9-112">Demonstrates</span></span>
 <span data-ttu-id="34fc9-113">Activité <xref:System.Activities.Statements.Pick></span><span class="sxs-lookup"><span data-stu-id="34fc9-113"><xref:System.Activities.Statements.Pick> activity.</span></span>

## <a name="discussion"></a><span data-ttu-id="34fc9-114">Discussion</span><span class="sxs-lookup"><span data-stu-id="34fc9-114">Discussion</span></span>
 <span data-ttu-id="34fc9-115">L'exemple inclut un workflow de concepteur et un workflow encodé.</span><span class="sxs-lookup"><span data-stu-id="34fc9-115">The sample includes a Designer workflow and coded workflow.</span></span>

 <span data-ttu-id="34fc9-116">Flux de travail du concepteur la version du concepteur de l’exemple montre comment créer un flux de travail dans le concepteur.</span><span class="sxs-lookup"><span data-stu-id="34fc9-116">Designer Workflow The Designer version of the sample demonstrates how to create a workflow in the designer.</span></span> <span data-ttu-id="34fc9-117">Les fichiers suivants sont inclus :</span><span class="sxs-lookup"><span data-stu-id="34fc9-117">The following files are included:</span></span>

- <span data-ttu-id="34fc9-118">Program.cs: Comprend la `Main` fonction qui exécute l’exemple de flux de travail.</span><span class="sxs-lookup"><span data-stu-id="34fc9-118">Program.cs : Includes the `Main` function that executes the sample workflow.</span></span>

- <span data-ttu-id="34fc9-119">ReadString.cs: Activité personnalisée qui lit une entrée de la console.</span><span class="sxs-lookup"><span data-stu-id="34fc9-119">ReadString.cs: A custom activity that reads some input from the console.</span></span>

- <span data-ttu-id="34fc9-120">Sequence1. xaml: Flux de travail créé à l’aide du concepteur qui utilise Pick.</span><span class="sxs-lookup"><span data-stu-id="34fc9-120">Sequence1.xaml: A workflow created using the designer that uses Pick.</span></span>

 <span data-ttu-id="34fc9-121">Flux de travail codé la version codée de l’exemple montre comment créer un flux de travail dans le concepteur.</span><span class="sxs-lookup"><span data-stu-id="34fc9-121">Coded Workflow The coded version of the sample demonstrates how to create a workflow in the designer.</span></span> <span data-ttu-id="34fc9-122">Les fichiers suivants sont inclus :</span><span class="sxs-lookup"><span data-stu-id="34fc9-122">The following files are included:</span></span>

- <span data-ttu-id="34fc9-123">Program.cs: Comprend la `Main` fonction qui exécute l’exemple de flux de travail.</span><span class="sxs-lookup"><span data-stu-id="34fc9-123">Program.cs : Includes the `Main` function that executes the sample workflow.</span></span>

- <span data-ttu-id="34fc9-124">ReadString.cs: Activité personnalisée qui lit une entrée de la console.</span><span class="sxs-lookup"><span data-stu-id="34fc9-124">ReadString.cs: A custom activity that reads some input from the console.</span></span>

#### <a name="to-use-this-sample"></a><span data-ttu-id="34fc9-125">Pour utiliser cet exemple</span><span class="sxs-lookup"><span data-stu-id="34fc9-125">To use this sample</span></span>

1. <span data-ttu-id="34fc9-126">À l’aide de Visual Studio 2010, ouvrez le fichier solution Pick. sln.</span><span class="sxs-lookup"><span data-stu-id="34fc9-126">Using Visual Studio 2010, open the Pick.sln solution file.</span></span>

2. <span data-ttu-id="34fc9-127">Pour générer la solution, appuyez sur Ctrl+Maj+B.</span><span class="sxs-lookup"><span data-stu-id="34fc9-127">To build the solution, press CTRL+SHIFT+B.</span></span>

3. <span data-ttu-id="34fc9-128">Pour exécuter la solution, appuyez sur F5.</span><span class="sxs-lookup"><span data-stu-id="34fc9-128">To run the solution, press F5.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="34fc9-129">Les exemples peuvent déjà être installés sur votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="34fc9-129">The samples may already be installed on your machine.</span></span> <span data-ttu-id="34fc9-130">Recherchez le répertoire (par défaut) suivant avant de continuer.</span><span class="sxs-lookup"><span data-stu-id="34fc9-130">Check for the following (default) directory before continuing.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> <span data-ttu-id="34fc9-131">Si ce répertoire n’existe pas, accédez à [Windows Communication Foundation (WCF) et Windows Workflow Foundation (WF) exemples pour .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) pour télécharger tous les exemples Windows Communication Foundation (WCF [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ) et.</span><span class="sxs-lookup"><span data-stu-id="34fc9-131">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="34fc9-132">Cet exemple se trouve dans le répertoire suivant.</span><span class="sxs-lookup"><span data-stu-id="34fc9-132">This sample is located in the following directory.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Built-InActivities\Pick`
