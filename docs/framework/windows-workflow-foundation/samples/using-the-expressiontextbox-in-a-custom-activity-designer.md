---
title: Utilisation d'ExpressionTextBox dans un concepteur d'activités personnalisées
ms.date: 03/30/2017
ms.assetid: f82e73e7-a256-4a4d-82b7-c0d62f4ab5e7
ms.openlocfilehash: 6d3df9e18c7239f0e4695509d80edfd02e9a9d6f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79182769"
---
# <a name="using-the-expressiontextbox-in-a-custom-activity-designer"></a><span data-ttu-id="ba850-102">Utilisation d'ExpressionTextBox dans un concepteur d'activités personnalisées</span><span class="sxs-lookup"><span data-stu-id="ba850-102">Using the ExpressionTextBox in a Custom Activity Designer</span></span>
<span data-ttu-id="ba850-103">Cet exemple montre comment utiliser le <xref:System.Activities.Presentation.View.ExpressionTextBox> dans un concepteur d'activités personnalisées.</span><span class="sxs-lookup"><span data-stu-id="ba850-103">This sample shows how to use the <xref:System.Activities.Presentation.View.ExpressionTextBox> in a custom activity designer.</span></span> <span data-ttu-id="ba850-104">L'activité personnalisée, `MultiAssign`, assigne deux valeurs de chaîne à deux variables String.</span><span class="sxs-lookup"><span data-stu-id="ba850-104">The custom activity, `MultiAssign`, assigns two string values to two string variables.</span></span> <span data-ttu-id="ba850-105">Certains contrôles <xref:System.Activities.Presentation.View.ExpressionTextBox> sont liés à <xref:System.Activities.InArgument>s et d'autres à <xref:System.Activities.OutArgument>s.</span><span class="sxs-lookup"><span data-stu-id="ba850-105">Some <xref:System.Activities.Presentation.View.ExpressionTextBox> controls bind to <xref:System.Activities.InArgument>s and some bind to <xref:System.Activities.OutArgument>s.</span></span>

## <a name="sample-details"></a><span data-ttu-id="ba850-106">Détails de l'exemple</span><span class="sxs-lookup"><span data-stu-id="ba850-106">Sample details</span></span>
 <span data-ttu-id="ba850-107">Le `ArgumentToExpressionConverter` est le convertisseur de type utilisé lors de la liaison d’expressions aux arguments.</span><span class="sxs-lookup"><span data-stu-id="ba850-107">The `ArgumentToExpressionConverter` is the type converter used when binding expressions to arguments.</span></span> <span data-ttu-id="ba850-108">Affectez `ConverterParameter` ou `In` à `Out`.</span><span class="sxs-lookup"><span data-stu-id="ba850-108">The `ConverterParameter` must be set to `In` or `Out` as appropriate.</span></span> <span data-ttu-id="ba850-109">La fonction `InOut` n'est pas prise en charge.</span><span class="sxs-lookup"><span data-stu-id="ba850-109">`InOut` is not supported.</span></span>

 <span data-ttu-id="ba850-110">L’attribut `UseLocationExpression` est `OutArgument`utilisé sur s pour spécifier que l’expression doit être une expression de valeur L (« valeur gauche » ou « valeur de localisation »).</span><span class="sxs-lookup"><span data-stu-id="ba850-110">The `UseLocationExpression` attribute is used on `OutArgument`s to specify that the expression should be an L-value ("left value" or "location value") expression.</span></span> <span data-ttu-id="ba850-111">Dans la plupart des cas, une expression L-value est un identificateur Visual Basic valide utilisé pour indiquer que le `OutArgument` qui est retourné est un nom de variable ou d’argument.</span><span class="sxs-lookup"><span data-stu-id="ba850-111">In most cases, an L-value expression is a valid Visual Basic identifier used to indicate that the `OutArgument` being returned is a variable or argument name.</span></span>

 <span data-ttu-id="ba850-112">L'attribut `MaxLines` a la valeur un dans cet exemple et `MinLines` n'est pas défini.</span><span class="sxs-lookup"><span data-stu-id="ba850-112">The `MaxLines` attribute is set to one in this example and `MinLines` is not set.</span></span> <span data-ttu-id="ba850-113">Cela indique que le <xref:System.Activities.Presentation.View.ExpressionTextBox> a une taille fixe d'une ligne indépendamment de la quantité de texte tapée par l'utilisateur.</span><span class="sxs-lookup"><span data-stu-id="ba850-113">This indicates that the <xref:System.Activities.Presentation.View.ExpressionTextBox> is a fixed size of one line regardless of the amount of text typed by the user.</span></span> <span data-ttu-id="ba850-114">Pour permettre au <xref:System.Activities.Presentation.View.ExpressionTextBox> de s'agrandir pour s'ajuster à l'entrée d'utilisateur, affectez à `MaxLines` une valeur supérieure à `MinLines`.</span><span class="sxs-lookup"><span data-stu-id="ba850-114">To allow the <xref:System.Activities.Presentation.View.ExpressionTextBox> to grow to fit user input, set `MaxLines` greater than `MinLines`.</span></span>

 <span data-ttu-id="ba850-115">Un ExpressionTextBox peut être lié uniquement aux arguments et ne peut pas être lié aux propriétés CLR.</span><span class="sxs-lookup"><span data-stu-id="ba850-115">An ExpressionTextBox can only be bound to arguments, and cannot be bound to CLR properties.</span></span>

#### <a name="to-use-this-sample"></a><span data-ttu-id="ba850-116">Pour utiliser cet exemple</span><span class="sxs-lookup"><span data-stu-id="ba850-116">To use this sample</span></span>

1. <span data-ttu-id="ba850-117">À l’aide de Visual Studio 2010, ouvrez le fichier ExpressionTextBoxSample.sln.</span><span class="sxs-lookup"><span data-stu-id="ba850-117">Using Visual Studio 2010, open the ExpressionTextBoxSample.sln file.</span></span>

2. <span data-ttu-id="ba850-118">Pour générer la solution, appuyez sur Ctrl+Maj+B.</span><span class="sxs-lookup"><span data-stu-id="ba850-118">To build the solution, press CTRL+SHIFT+B.</span></span>

#### <a name="to-run-this-sample"></a><span data-ttu-id="ba850-119">Pour exécuter l'exemple</span><span class="sxs-lookup"><span data-stu-id="ba850-119">To run this sample</span></span>

1. <span data-ttu-id="ba850-120">Ajoutez une nouvelle application console de workflow à la solution.</span><span class="sxs-lookup"><span data-stu-id="ba850-120">Add a new Workflow Console Application to the solution.</span></span>

2. <span data-ttu-id="ba850-121">Ajoutez une référence au projet **ExpressionTextBoxSample** du nouveau projet Workflow Console Application.</span><span class="sxs-lookup"><span data-stu-id="ba850-121">Add a reference to the **ExpressionTextBoxSample** project from the new Workflow Console Application project.</span></span>

3. <span data-ttu-id="ba850-122">Générez la solution.</span><span class="sxs-lookup"><span data-stu-id="ba850-122">Build the solution.</span></span>

4. <span data-ttu-id="ba850-123">Faites glisser l’activité **MultiAssign** de la boîte à outils et laissez-la tomber dans le flux de travail.</span><span class="sxs-lookup"><span data-stu-id="ba850-123">Drag the **MultiAssign** activity from the toolbox and drop it into the workflow.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="ba850-124">Les exemples peuvent déjà être installés sur votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="ba850-124">The samples may already be installed on your machine.</span></span> <span data-ttu-id="ba850-125">Recherchez le répertoire (par défaut) suivant avant de continuer.</span><span class="sxs-lookup"><span data-stu-id="ba850-125">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="ba850-126">Si ce répertoire n’existe pas, rendez-vous sur [Windows Communication Foundation (WCF) et Windows Workflow Foundation (WF) Samples pour .NET Framework 4 pour](https://www.microsoft.com/download/details.aspx?id=21459) télécharger tous les Windows Communication Foundation (WCF) et [!INCLUDE[wf1](../../../../includes/wf1-md.md)] des échantillons.</span><span class="sxs-lookup"><span data-stu-id="ba850-126">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="ba850-127">Cet exemple se trouve dans le répertoire suivant.</span><span class="sxs-lookup"><span data-stu-id="ba850-127">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WF\Basic\CustomActivities\CustomActivityDesigners\ExpressionTextBox`  
  
## <a name="see-also"></a><span data-ttu-id="ba850-128">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ba850-128">See also</span></span>

- <xref:System.Activities.Presentation.View.ExpressionTextBox>
- [<span data-ttu-id="ba850-129">Développement d’applications avec le Concepteur de flux de travail</span><span class="sxs-lookup"><span data-stu-id="ba850-129">Developing Applications with the Workflow Designer</span></span>](/visualstudio/workflow-designer/developing-applications-with-the-workflow-designer)
