---
title: 'Procédure : annuler un bloc de dataflow'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Task Parallel Library, dataflows
- dataflow blocks, canceling in TPL
- TPL dataflow library,canceling dataflow blocks
ms.assetid: fbddda0d-da3b-4ec8-a1d6-67ab8573fcd7
ms.openlocfilehash: 530c231deeaba007975849ab6dc41f4da6a859ea
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84285545"
---
# <a name="how-to-cancel-a-dataflow-block"></a><span data-ttu-id="a252c-102">Procédure : annuler un bloc de dataflow</span><span class="sxs-lookup"><span data-stu-id="a252c-102">How to: Cancel a Dataflow Block</span></span>
<span data-ttu-id="a252c-103">Ce document montre comment activer l’annulation dans votre application.</span><span class="sxs-lookup"><span data-stu-id="a252c-103">This document demonstrates how to enable cancellation in your application.</span></span> <span data-ttu-id="a252c-104">Cet exemple utilise des Windows Forms pour montrer où les éléments de travail sont actifs dans un pipeline de flux de données, ainsi que les effets de l’annulation.</span><span class="sxs-lookup"><span data-stu-id="a252c-104">This example uses Windows Forms to show where work items are active in a dataflow pipeline and also the effects of cancellation.</span></span>  

[!INCLUDE [tpl-install-instructions](../../../includes/tpl-install-instructions.md)]
  
## <a name="to-create-the-windows-forms-application"></a><span data-ttu-id="a252c-105">Pour créer une Application Windows Forms</span><span class="sxs-lookup"><span data-stu-id="a252c-105">To Create the Windows Forms Application</span></span>  
  
1. <span data-ttu-id="a252c-106">Créez un projet C# ou **Application Windows Forms** Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="a252c-106">Create a C# or Visual Basic **Windows Forms Application** project.</span></span> <span data-ttu-id="a252c-107">Dans les étapes suivantes, le projet est nommé `CancellationWinForms`.</span><span class="sxs-lookup"><span data-stu-id="a252c-107">In the following steps, the project is named `CancellationWinForms`.</span></span>  
  
2. <span data-ttu-id="a252c-108">Dans le concepteur de formulaires pour le formulaire principal, Form1.cs (Form1.vb pour Visual Basic), ajoutez un contrôle <xref:System.Windows.Forms.ToolStrip>.</span><span class="sxs-lookup"><span data-stu-id="a252c-108">On the form designer for the main form, Form1.cs (Form1.vb for Visual Basic), add a <xref:System.Windows.Forms.ToolStrip> control.</span></span>  
  
3. <span data-ttu-id="a252c-109">Ajoutez un contrôle <xref:System.Windows.Forms.ToolStripButton> au contrôle <xref:System.Windows.Forms.ToolStrip>.</span><span class="sxs-lookup"><span data-stu-id="a252c-109">Add a <xref:System.Windows.Forms.ToolStripButton> control to the <xref:System.Windows.Forms.ToolStrip> control.</span></span> <span data-ttu-id="a252c-110">Définissez la propriété <xref:System.Windows.Forms.ToolStripItem.DisplayStyle%2A> sur <xref:System.Windows.Forms.ToolStripItemDisplayStyle.Text> et la propriété <xref:System.Windows.Forms.ToolStripItem.Text%2A> sur **Ajouter des éléments de travail**.</span><span class="sxs-lookup"><span data-stu-id="a252c-110">Set the <xref:System.Windows.Forms.ToolStripItem.DisplayStyle%2A> property to <xref:System.Windows.Forms.ToolStripItemDisplayStyle.Text> and the <xref:System.Windows.Forms.ToolStripItem.Text%2A> property to **Add Work Items**.</span></span>  
  
4. <span data-ttu-id="a252c-111">Ajoutez un deuxième contrôle <xref:System.Windows.Forms.ToolStripButton> au contrôle <xref:System.Windows.Forms.ToolStrip>.</span><span class="sxs-lookup"><span data-stu-id="a252c-111">Add a second <xref:System.Windows.Forms.ToolStripButton> control to the <xref:System.Windows.Forms.ToolStrip> control.</span></span> <span data-ttu-id="a252c-112">Définissez la propriété <xref:System.Windows.Forms.ToolStripItem.DisplayStyle%2A> sur <xref:System.Windows.Forms.ToolStripItemDisplayStyle.Text>, la propriété <xref:System.Windows.Forms.ToolStripItem.Text%2A> sur **Annuler** et la propriété <xref:System.Windows.Forms.ToolStripItem.Enabled%2A> sur `False`.</span><span class="sxs-lookup"><span data-stu-id="a252c-112">Set the <xref:System.Windows.Forms.ToolStripItem.DisplayStyle%2A> property to <xref:System.Windows.Forms.ToolStripItemDisplayStyle.Text>, the <xref:System.Windows.Forms.ToolStripItem.Text%2A> property to **Cancel**, and the <xref:System.Windows.Forms.ToolStripItem.Enabled%2A> property to `False`.</span></span>  
  
5. <span data-ttu-id="a252c-113">Ajoutez quatre objets <xref:System.Windows.Forms.ToolStripProgressBar> au contrôle <xref:System.Windows.Forms.ToolStrip>.</span><span class="sxs-lookup"><span data-stu-id="a252c-113">Add four <xref:System.Windows.Forms.ToolStripProgressBar> objects to the <xref:System.Windows.Forms.ToolStrip> control.</span></span>  
  
## <a name="creating-the-dataflow-pipeline"></a><span data-ttu-id="a252c-114">Création du pipeline de flux de données</span><span class="sxs-lookup"><span data-stu-id="a252c-114">Creating the Dataflow Pipeline</span></span>  
 <span data-ttu-id="a252c-115">Cette section décrit comment créer le pipeline de flux de données qui traite les éléments de travail et met à jour les barres de progression.</span><span class="sxs-lookup"><span data-stu-id="a252c-115">This section describes how to create the dataflow pipeline that processes work items and updates the progress bars.</span></span>  
  
### <a name="to-create-the-dataflow-pipeline"></a><span data-ttu-id="a252c-116">Pour créer le pipeline de flux de données</span><span class="sxs-lookup"><span data-stu-id="a252c-116">To Create the Dataflow Pipeline</span></span>  
  
1. <span data-ttu-id="a252c-117">Dans votre projet, ajoutez une référence à System.Threading.Tasks.Dataflow.dll.</span><span class="sxs-lookup"><span data-stu-id="a252c-117">In your project, add a reference to System.Threading.Tasks.Dataflow.dll.</span></span>  
  
2. <span data-ttu-id="a252c-118">Vérifiez que Form1.cs (Form1.vb pour Visual Basic) contient les instructions `using` suivantes (`Imports` en Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="a252c-118">Ensure that Form1.cs (Form1.vb for Visual Basic) contains the following `using` statements (`Imports` in Visual Basic).</span></span>  
  
     [!code-csharp[TPLDataflow_CancellationWinForms#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_cancellationwinforms/cs/cancellationwinforms/form1.cs#1)]
     [!code-vb[TPLDataflow_CancellationWinForms#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_cancellationwinforms/vb/cancellationwinforms/form1.vb#1)]  
  
3. <span data-ttu-id="a252c-119">Ajouter la classe `WorkItem` comme un type interne de la classe `Form1`.</span><span class="sxs-lookup"><span data-stu-id="a252c-119">Add the `WorkItem` class as an inner type of the `Form1` class.</span></span>  
  
     [!code-csharp[TPLDataflow_CancellationWinForms#2](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_cancellationwinforms/cs/cancellationwinforms/form1.cs#2)]
     [!code-vb[TPLDataflow_CancellationWinForms#2](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_cancellationwinforms/vb/cancellationwinforms/form1.vb#2)]  
  
4. <span data-ttu-id="a252c-120">Ajoutez les membres de données suivants à la classe `Form1`.</span><span class="sxs-lookup"><span data-stu-id="a252c-120">Add the following data members to the `Form1` class.</span></span>  
  
     [!code-csharp[TPLDataflow_CancellationWinForms#3](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_cancellationwinforms/cs/cancellationwinforms/form1.cs#3)]
     [!code-vb[TPLDataflow_CancellationWinForms#3](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_cancellationwinforms/vb/cancellationwinforms/form1.vb#3)]  
  
5. <span data-ttu-id="a252c-121">Ajoutez la méthode suivante, `CreatePipeline`, à la classe `Form1`.</span><span class="sxs-lookup"><span data-stu-id="a252c-121">Add the following method, `CreatePipeline`, to the `Form1` class.</span></span>  
  
     [!code-csharp[TPLDataflow_CancellationWinForms#4](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_cancellationwinforms/cs/cancellationwinforms/form1.cs#4)]
     [!code-vb[TPLDataflow_CancellationWinForms#4](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_cancellationwinforms/vb/cancellationwinforms/form1.vb#4)]  
  
 <span data-ttu-id="a252c-122">Étant donné que les blocs de flux de données `incrementProgress` et `decrementProgress` agissent sur l’interface utilisateur, il est important que ces actions se produisent sur le thread de l’interface utilisateur.</span><span class="sxs-lookup"><span data-stu-id="a252c-122">Because the `incrementProgress` and `decrementProgress` dataflow blocks act on the user interface, it is important that these actions occur on the user-interface thread.</span></span> <span data-ttu-id="a252c-123">Pour cela, lors de la construction, chacun de ces objets fournit un objet <xref:System.Threading.Tasks.Dataflow.ExecutionDataflowBlockOptions> dont la propriété <xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions.TaskScheduler%2A> est définie sur <xref:System.Threading.Tasks.TaskScheduler.FromCurrentSynchronizationContext%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="a252c-123">To accomplish this, during construction these objects each provide a <xref:System.Threading.Tasks.Dataflow.ExecutionDataflowBlockOptions> object that has the <xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions.TaskScheduler%2A> property set to <xref:System.Threading.Tasks.TaskScheduler.FromCurrentSynchronizationContext%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="a252c-124">La méthode <xref:System.Threading.Tasks.TaskScheduler.FromCurrentSynchronizationContext%2A?displayProperty=nameWithType> crée un objet <xref:System.Threading.Tasks.TaskScheduler> qui effectue le travail dans le contexte actuel de synchronisation.</span><span class="sxs-lookup"><span data-stu-id="a252c-124">The <xref:System.Threading.Tasks.TaskScheduler.FromCurrentSynchronizationContext%2A?displayProperty=nameWithType> method creates a <xref:System.Threading.Tasks.TaskScheduler> object that performs work on the current synchronization context.</span></span> <span data-ttu-id="a252c-125">Étant donné que le constructeur `Form1` est appelé depuis le thread de l’interface utilisateur, les actions des blocs de flux de données `incrementProgress` et `decrementProgress` fonctionnent aussi sur le thread de l’interface utilisateur.</span><span class="sxs-lookup"><span data-stu-id="a252c-125">Because the `Form1` constructor is called from the user-interface thread, the actions for the `incrementProgress` and `decrementProgress` dataflow blocks also run on the user-interface thread.</span></span>  
  
 <span data-ttu-id="a252c-126">Cet exemple définit la propriété <xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions.CancellationToken%2A> lors de la construction des membres du pipeline.</span><span class="sxs-lookup"><span data-stu-id="a252c-126">This example sets the <xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions.CancellationToken%2A> property when it constructs the members of the pipeline.</span></span> <span data-ttu-id="a252c-127">Étant donné que la propriété <xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions.CancellationToken%2A> annule définitivement l’exécution du bloc de flux de données, l’ensemble du pipeline doit être recréé si l’utilisateur annule l’opération et souhaite par la suite ajouter d’autres éléments de travail au pipeline.</span><span class="sxs-lookup"><span data-stu-id="a252c-127">Because the <xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions.CancellationToken%2A> property permanently cancels dataflow block execution, the whole pipeline must be recreated after the user cancels the operation and then wants to add more work items to the pipeline.</span></span> <span data-ttu-id="a252c-128">Pour obtenir un exemple illustrant une autre méthode d’annulation d’un bloc de flux de données de sorte que les autres travaux puissent être effectués après l’annulation d’une opération, consultez [Walkthrough: Using Dataflow in a Windows Forms Application](walkthrough-using-dataflow-in-a-windows-forms-application.md) (Procédure pas à pas : utilisation d’un flux de données dans une application Windows Forms).</span><span class="sxs-lookup"><span data-stu-id="a252c-128">For an example that demonstrates an alternative way to cancel a dataflow block so that other work can be performed after an operation is canceled, see [Walkthrough: Using Dataflow in a Windows Forms Application](walkthrough-using-dataflow-in-a-windows-forms-application.md).</span></span>  
  
## <a name="connecting-the-dataflow-pipeline-to-the-user-interface"></a><span data-ttu-id="a252c-129">Connexion du pipeline de flux de données à l’interface utilisateur</span><span class="sxs-lookup"><span data-stu-id="a252c-129">Connecting the Dataflow Pipeline to the User Interface</span></span>  
 <span data-ttu-id="a252c-130">Cette section décrit comment connecter le pipeline de flux de données à l’interface utilisateur.</span><span class="sxs-lookup"><span data-stu-id="a252c-130">This section describes how to connect the dataflow pipeline to the user interface.</span></span> <span data-ttu-id="a252c-131">La création du pipeline et l’ajout d’éléments de travail au pipeline sont contrôlés par le gestionnaire d’événements pour le bouton **Add Work Items** (Ajouter des éléments de travail).</span><span class="sxs-lookup"><span data-stu-id="a252c-131">Both creating the pipeline and adding work items to the pipeline are controlled by the event handler for the **Add Work Items** button.</span></span> <span data-ttu-id="a252c-132">L’annulation est lancée par le bouton **Annuler**.</span><span class="sxs-lookup"><span data-stu-id="a252c-132">Cancellation is initiated by the **Cancel** button.</span></span> <span data-ttu-id="a252c-133">Lorsque l’utilisateur clique sur un de ces boutons, l’action appropriée est lancée de manière asynchrone.</span><span class="sxs-lookup"><span data-stu-id="a252c-133">When the user clicks either of these buttons, the appropriate action is initiated in an asynchronous manner.</span></span>  
  
### <a name="to-connect-the-dataflow-pipeline-to-the-user-interface"></a><span data-ttu-id="a252c-134">Pour connecter le pipeline de flux de données à l’interface utilisateur</span><span class="sxs-lookup"><span data-stu-id="a252c-134">To Connect the Dataflow Pipeline to the User Interface</span></span>  
  
1. <span data-ttu-id="a252c-135">Dans le concepteur de formulaires du formulaire principal, créez un gestionnaire d'événements pour l'événement <xref:System.Windows.Forms.ToolStripItem.Click> du bouton **Ajouter des éléments de travail**.</span><span class="sxs-lookup"><span data-stu-id="a252c-135">On the form designer for the main form, create an event handler for the <xref:System.Windows.Forms.ToolStripItem.Click> event for the **Add Work Items** button.</span></span>  
  
2. <span data-ttu-id="a252c-136">Implémentez l’événement <xref:System.Windows.Forms.ToolStripItem.Click> pour le bouton **Ajouter des éléments de travail**.</span><span class="sxs-lookup"><span data-stu-id="a252c-136">Implement the <xref:System.Windows.Forms.ToolStripItem.Click> event for the **Add Work Items** button.</span></span>  
  
     [!code-csharp[TPLDataflow_CancellationWinForms#5](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_cancellationwinforms/cs/cancellationwinforms/form1.cs#5)]
     [!code-vb[TPLDataflow_CancellationWinForms#5](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_cancellationwinforms/vb/cancellationwinforms/form1.vb#5)]  
  
3. <span data-ttu-id="a252c-137">Dans le concepteur de formulaires du formulaire principal, créez un gestionnaire d'événements pour le gestionnaire d’événements <xref:System.Windows.Forms.ToolStripItem.Click> du bouton **Annuler**.</span><span class="sxs-lookup"><span data-stu-id="a252c-137">On the form designer for the main form, create an event handler for the <xref:System.Windows.Forms.ToolStripItem.Click> event handler for the **Cancel** button.</span></span>  
  
4. <span data-ttu-id="a252c-138">Implémentez le gestionnaire d’événements <xref:System.Windows.Forms.ToolStripItem.Click> pour le bouton **Annuler**.</span><span class="sxs-lookup"><span data-stu-id="a252c-138">Implement the <xref:System.Windows.Forms.ToolStripItem.Click> event handler for the **Cancel** button.</span></span>  
  
     [!code-csharp[TPLDataflow_CancellationWinForms#6](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_cancellationwinforms/cs/cancellationwinforms/form1.cs#6)]
     [!code-vb[TPLDataflow_CancellationWinForms#6](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_cancellationwinforms/vb/cancellationwinforms/form1.vb#6)]  
  
## <a name="example"></a><span data-ttu-id="a252c-139">Exemple</span><span class="sxs-lookup"><span data-stu-id="a252c-139">Example</span></span>  
 <span data-ttu-id="a252c-140">L’exemple suivant montre le code complet pour Form1.cs (Form1.vb pour Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="a252c-140">The following example shows the complete code for Form1.cs (Form1.vb for Visual Basic).</span></span>  
  
 [!code-csharp[TPLDataflow_CancellationWinForms#100](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_cancellationwinforms/cs/cancellationwinforms/form1.cs#100)]
 [!code-vb[TPLDataflow_CancellationWinForms#100](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_cancellationwinforms/vb/cancellationwinforms/form1.vb#100)]  
  
 <span data-ttu-id="a252c-141">L'illustration suivante présente l'application en cours d'exécution.</span><span class="sxs-lookup"><span data-stu-id="a252c-141">The following illustration shows the running application.</span></span>  
  
 <span data-ttu-id="a252c-142">![Application Windows Forms](media/tpldataflow-cancellation.png "TPLDataflow_Cancellation")</span><span class="sxs-lookup"><span data-stu-id="a252c-142">![The Windows Forms Application](media/tpldataflow-cancellation.png "TPLDataflow_Cancellation")</span></span>  

## <a name="see-also"></a><span data-ttu-id="a252c-143">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a252c-143">See also</span></span>

- [<span data-ttu-id="a252c-144">Dataflow</span><span class="sxs-lookup"><span data-stu-id="a252c-144">Dataflow</span></span>](dataflow-task-parallel-library.md)
