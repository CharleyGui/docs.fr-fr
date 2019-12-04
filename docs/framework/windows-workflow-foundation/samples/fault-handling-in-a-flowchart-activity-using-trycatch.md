---
title: Gestion des erreurs dans une activité Flowchart à l'aide de TryCatch
ms.date: 03/30/2017
ms.assetid: 50922964-bfe0-4ba8-9422-0e7220d514fd
ms.openlocfilehash: 8e3ca59bc9743300a230877a6fbcbed5468a1589
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74710838"
---
# <a name="fault-handling-in-a-flowchart-activity-using-trycatch"></a><span data-ttu-id="214b3-102">Gestion des erreurs dans une activité Flowchart à l'aide de TryCatch</span><span class="sxs-lookup"><span data-stu-id="214b3-102">Fault Handling in a Flowchart Activity Using TryCatch</span></span>

<span data-ttu-id="214b3-103">Cet exemple montre comment l'activité <xref:System.Activities.Statements.TryCatch> peut être utilisée dans une activité de flux de contrôle complexe.</span><span class="sxs-lookup"><span data-stu-id="214b3-103">This sample shows how the <xref:System.Activities.Statements.TryCatch> activity can be used within a complex control flow activity.</span></span>

<span data-ttu-id="214b3-104">Dans cet exemple, un code promotionnel et un nombre d'enfants sont passés en tant que variables à une activité <xref:System.Activities.Statements.Flowchart> qui calcule une remise basée sur des formules qui correspondent au code promotionnel.</span><span class="sxs-lookup"><span data-stu-id="214b3-104">In this sample, a promotion code and number of children are passed as variables to a <xref:System.Activities.Statements.Flowchart> activity that calculates a discount based on formulae that correspond to the promotion code.</span></span> <span data-ttu-id="214b3-105">L'exemple inclut les versions du code impératif et du concepteur de workflow de l'exemple.</span><span class="sxs-lookup"><span data-stu-id="214b3-105">The sample includes imperative code and workflow designer versions of the sample.</span></span>

<span data-ttu-id="214b3-106">Le tableau suivant décrit en détail les variables pour l'activité `CreateFlowchartWithFaults`.</span><span class="sxs-lookup"><span data-stu-id="214b3-106">The following table details the variables for the `CreateFlowchartWithFaults` activity.</span></span>

|<span data-ttu-id="214b3-107">Parameters</span><span class="sxs-lookup"><span data-stu-id="214b3-107">Parameters</span></span>|<span data-ttu-id="214b3-108">Description</span><span class="sxs-lookup"><span data-stu-id="214b3-108">Description</span></span>|
|----------------|-----------------|
|<span data-ttu-id="214b3-109">promoCode</span><span class="sxs-lookup"><span data-stu-id="214b3-109">promoCode</span></span>|<span data-ttu-id="214b3-110">Code de promotion.</span><span class="sxs-lookup"><span data-stu-id="214b3-110">The promotion code.</span></span> <span data-ttu-id="214b3-111">Type : chaîne</span><span class="sxs-lookup"><span data-stu-id="214b3-111">Type: String</span></span><br /><br /> <span data-ttu-id="214b3-112">Valeurs possibles avec la description entre parenthèses :</span><span class="sxs-lookup"><span data-stu-id="214b3-112">The possible values with description in parentheses:</span></span><br /><br /> <span data-ttu-id="214b3-113">-Single (unique)</span><span class="sxs-lookup"><span data-stu-id="214b3-113">-   Single (Single)</span></span><br /><span data-ttu-id="214b3-114">-MNK (marié sans enfants.)</span><span class="sxs-lookup"><span data-stu-id="214b3-114">-   MNK (Married with no kids.)</span></span><br /><span data-ttu-id="214b3-115">-MWK (marié avec les enfants.)</span><span class="sxs-lookup"><span data-stu-id="214b3-115">-   MWK (Married with kids.)</span></span>|
|<span data-ttu-id="214b3-116">numKids</span><span class="sxs-lookup"><span data-stu-id="214b3-116">numKids</span></span>|<span data-ttu-id="214b3-117">Nombre d'enfants.</span><span class="sxs-lookup"><span data-stu-id="214b3-117">The number of children.</span></span> <span data-ttu-id="214b3-118">Type : int</span><span class="sxs-lookup"><span data-stu-id="214b3-118">Type: int</span></span>|

<span data-ttu-id="214b3-119">L'activité `CreateFlowchartWithFaults` utilise une activité <xref:System.Activities.Statements.FlowSwitch%601> qui active l'argument `promoCode` et calcule la remise à l'aide de la formule suivante.</span><span class="sxs-lookup"><span data-stu-id="214b3-119">The `CreateFlowchartWithFaults` activity uses a <xref:System.Activities.Statements.FlowSwitch%601> activity that switches on the `promoCode` argument and calculates the discount using the following formula.</span></span>

|<span data-ttu-id="214b3-120">Valeur de `promoCode`</span><span class="sxs-lookup"><span data-stu-id="214b3-120">Value of `promoCode`</span></span>|<span data-ttu-id="214b3-121">Remise (%)</span><span class="sxs-lookup"><span data-stu-id="214b3-121">Discount (%)</span></span>|
|--------------------------|--------------------|
|<span data-ttu-id="214b3-122">Single</span><span class="sxs-lookup"><span data-stu-id="214b3-122">Single</span></span>|<span data-ttu-id="214b3-123">10</span><span class="sxs-lookup"><span data-stu-id="214b3-123">10</span></span>|
|<span data-ttu-id="214b3-124">MNK</span><span class="sxs-lookup"><span data-stu-id="214b3-124">MNK</span></span>|<span data-ttu-id="214b3-125">15</span><span class="sxs-lookup"><span data-stu-id="214b3-125">15</span></span>|
|<span data-ttu-id="214b3-126">MWK</span><span class="sxs-lookup"><span data-stu-id="214b3-126">MWK</span></span>|<span data-ttu-id="214b3-127">15 + (1 – 1/`numberOfKids`)\*10 **Remarque :** ce calcul peut éventuellement lever une <xref:System.DivideByZeroException>.</span><span class="sxs-lookup"><span data-stu-id="214b3-127">15 + (1 – 1/`numberOfKids`)\*10 **Note:**  Potentially, this calculation can throw a <xref:System.DivideByZeroException>.</span></span> <span data-ttu-id="214b3-128">Par conséquent, le calcul de la remise est inclus dans un wrapper dans une activité <xref:System.Activities.Statements.TryCatch> qui intercepte l'exception <xref:System.DivideByZeroException> et définit la remise à zéro.</span><span class="sxs-lookup"><span data-stu-id="214b3-128">So, the discount calculation is wrapped in a <xref:System.Activities.Statements.TryCatch> activity that catches the <xref:System.DivideByZeroException> exception and sets the discount to zero.</span></span>|

#### <a name="to-use-this-sample"></a><span data-ttu-id="214b3-129">Pour utiliser cet exemple</span><span class="sxs-lookup"><span data-stu-id="214b3-129">To use this sample</span></span>

1. <span data-ttu-id="214b3-130">À l’aide de Visual Studio 2010, ouvrez le fichier solution FlowchartWithFaultHandling. sln.</span><span class="sxs-lookup"><span data-stu-id="214b3-130">Using Visual Studio 2010, open the FlowchartWithFaultHandling.sln solution file.</span></span>

2. <span data-ttu-id="214b3-131">Pour générer la solution, appuyez sur Ctrl+Maj+B.</span><span class="sxs-lookup"><span data-stu-id="214b3-131">To build the solution, press CTRL+SHIFT+B.</span></span>

3. <span data-ttu-id="214b3-132">Pour exécuter la solution, appuyez sur F5.</span><span class="sxs-lookup"><span data-stu-id="214b3-132">To run the solution, press F5.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="214b3-133">Les exemples peuvent déjà être installés sur votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="214b3-133">The samples may already be installed on your computer.</span></span> <span data-ttu-id="214b3-134">Recherchez le répertoire (par défaut) suivant avant de continuer.</span><span class="sxs-lookup"><span data-stu-id="214b3-134">Check for the following (default) directory before continuing.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> <span data-ttu-id="214b3-135">Si ce répertoire n’existe pas, accédez à [Windows Communication Foundation (WCF) et Windows Workflow Foundation (WF) exemples pour .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) pour télécharger tous les exemples Windows Communication Foundation (WCF) et [!INCLUDE[wf1](../../../../includes/wf1-md.md)].</span><span class="sxs-lookup"><span data-stu-id="214b3-135">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="214b3-136">Cet exemple se trouve dans le répertoire suivant.</span><span class="sxs-lookup"><span data-stu-id="214b3-136">This sample is located in the following directory.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Built-InActivities\FlowChartWithFaultHandling`

## <a name="see-also"></a><span data-ttu-id="214b3-137">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="214b3-137">See also</span></span>

- [<span data-ttu-id="214b3-138">Workflows d’organigramme</span><span class="sxs-lookup"><span data-stu-id="214b3-138">Flowchart Workflows</span></span>](../flowchart-workflows.md)
- [<span data-ttu-id="214b3-139">Exceptions</span><span class="sxs-lookup"><span data-stu-id="214b3-139">Exceptions</span></span>](../exceptions.md)
