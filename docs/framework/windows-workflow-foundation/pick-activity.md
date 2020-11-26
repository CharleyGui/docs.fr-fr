---
title: Activité Pick
description: Dans Workflow Foundation, l’activité Pick simplifie la modélisation d’un ensemble de déclencheurs d’événements suivis de leurs gestionnaires correspondants.
ms.date: 03/30/2017
ms.assetid: b3e49b7f-0285-4720-8c09-11ae18f0d53e
ms.openlocfilehash: 6fc31679c20e24115e790bb50b0b5fa8dd62c705
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96246132"
---
# <a name="pick-activity"></a><span data-ttu-id="2f1ee-103">Activité Pick</span><span class="sxs-lookup"><span data-stu-id="2f1ee-103">Pick Activity</span></span>

<span data-ttu-id="2f1ee-104">L'activité <xref:System.Activities.Statements.Pick> simplifie la modélisation d'un jeu de déclencheurs d'événements suivis de leurs gestionnaires correspondants.</span><span class="sxs-lookup"><span data-stu-id="2f1ee-104">The <xref:System.Activities.Statements.Pick> activity simplifies the modeling of a set of event triggers followed by their corresponding handlers.</span></span>  <span data-ttu-id="2f1ee-105">Une activité <xref:System.Activities.Statements.Pick> contient une collection d'activités <xref:System.Activities.Statements.PickBranch>, où chaque <xref:System.Activities.Statements.PickBranch> est un couplage entre une activité <xref:System.Activities.Statements.PickBranch.Trigger%2A> et une activité <xref:System.Activities.Statements.PickBranch.Action%2A>.</span><span class="sxs-lookup"><span data-stu-id="2f1ee-105">A <xref:System.Activities.Statements.Pick> activity contains a collection of <xref:System.Activities.Statements.PickBranch> activities, where each <xref:System.Activities.Statements.PickBranch> is a pairing between a <xref:System.Activities.Statements.PickBranch.Trigger%2A> activity and an <xref:System.Activities.Statements.PickBranch.Action%2A> activity.</span></span>  <span data-ttu-id="2f1ee-106">Au moment de l’exécution, les déclencheurs de toutes les branches sont exécutés en parallèle.</span><span class="sxs-lookup"><span data-stu-id="2f1ee-106">At execution time, the triggers for all branches are executed in parallel.</span></span>  <span data-ttu-id="2f1ee-107">Une fois qu'un déclencheur a été exécuté, son action correspondante est exécutée, et tous les autres déclencheurs sont annulés.</span><span class="sxs-lookup"><span data-stu-id="2f1ee-107">When one trigger completes, then its corresponding action is executed, and all other triggers are canceled.</span></span>  <span data-ttu-id="2f1ee-108">Le comportement de l' [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] <xref:System.Activities.Statements.Pick> activité est similaire à l’activité .NET Framework 3,5 <xref:System.Workflow.Activities.ListenActivity> .</span><span class="sxs-lookup"><span data-stu-id="2f1ee-108">The behavior of the [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)]<xref:System.Activities.Statements.Pick> activity is similar to the .NET Framework 3.5 <xref:System.Workflow.Activities.ListenActivity> activity.</span></span>  
  
 <span data-ttu-id="2f1ee-109">La capture d’écran suivante de l’exemple du SDK [Utilisation de l’activité Pick](./samples/using-the-pick-activity.md) montre une activité Pick avec deux branches.</span><span class="sxs-lookup"><span data-stu-id="2f1ee-109">The following screenshot from the [Using the Pick Activity](./samples/using-the-pick-activity.md) SDK sample shows a Pick activity with two branches.</span></span>  <span data-ttu-id="2f1ee-110">Une branche a un déclencheur appelé **Read input**, une activité personnalisée qui lit l’entrée à partir de la ligne de commande.</span><span class="sxs-lookup"><span data-stu-id="2f1ee-110">One branch has a trigger called **Read input**, a custom activity that reads input from the command line.</span></span> <span data-ttu-id="2f1ee-111">La deuxième branche comporte un déclencheur d’activité <xref:System.Activities.Statements.Delay>.</span><span class="sxs-lookup"><span data-stu-id="2f1ee-111">The second branch has a <xref:System.Activities.Statements.Delay> activity trigger.</span></span> <span data-ttu-id="2f1ee-112">Si l’activité **lire l’entrée** reçoit des données avant la fin de l' <xref:System.Activities.Statements.Delay> activité, le <xref:System.Activities.Statements.Delay> délai sera annulé et un message d’accueil sera écrit dans la console.</span><span class="sxs-lookup"><span data-stu-id="2f1ee-112">If the **Read input** activity receives data before the <xref:System.Activities.Statements.Delay> activity finishes, <xref:System.Activities.Statements.Delay> Delay will be canceled and a greeting will be written to the console.</span></span>  <span data-ttu-id="2f1ee-113">Sinon, si l’activité **Read input** ne reçoit pas de données dans le délai alloué, elle est annulée et un message d’expiration du délai d’attente est écrit sur la console.</span><span class="sxs-lookup"><span data-stu-id="2f1ee-113">Otherwise, if the **Read input** activity does not receive data in the allotted time, then it will be canceled and a timeout message will be written to the console.</span></span>  <span data-ttu-id="2f1ee-114">C’est un modèle commun utilisé pour ajouter un délai d’attente à une action.</span><span class="sxs-lookup"><span data-stu-id="2f1ee-114">This is a common pattern used to add a timeout to any action.</span></span>  
  
 ![Activité Pick](./media/pick-activity/pick-activity-two-branches.jpg)  
  
## <a name="best-practices"></a><span data-ttu-id="2f1ee-116">Meilleures pratiques</span><span class="sxs-lookup"><span data-stu-id="2f1ee-116">Best practices</span></span>  

 <span data-ttu-id="2f1ee-117">Lors de l'utilisation de Pick, la branche exécutée est la branche dont le déclencheur a fini de s'exécuter en premier.</span><span class="sxs-lookup"><span data-stu-id="2f1ee-117">When using Pick, the branch that executes is the branch whose trigger completes first.</span></span>  <span data-ttu-id="2f1ee-118">Conceptuellement, tous les déclencheurs s'exécutent en parallèle, et un déclencheur peut avoir exécuté la majorité de sa logique avant d'être annulé par la fin de l'exécution d'un autre déclencheur.</span><span class="sxs-lookup"><span data-stu-id="2f1ee-118">Conceptually, all triggers execute in parallel, and one trigger may have executed the majority of its logic before it is canceled by the completion of another trigger.</span></span>  <span data-ttu-id="2f1ee-119">Par conséquent, lors de l'utilisation de l'activité Pick, il est recommandé de traiter le déclencheur en tant que représentant d'un événement unique et d'y inclure le minimum de logique possible.</span><span class="sxs-lookup"><span data-stu-id="2f1ee-119">With this in mind, a general guideline to follow when using the Pick activity is to treat the trigger as representing a single event, and to put as little logic as possible into it.</span></span>  <span data-ttu-id="2f1ee-120">Idéalement, le déclencheur doit contenir juste assez de logique pour recevoir un événement, et la totalité du traitement de cet événement doit être placée dans l'action de la branche.</span><span class="sxs-lookup"><span data-stu-id="2f1ee-120">Ideally, the trigger should contain just enough logic to receive an event, and all the processing of that event should go into the action of the branch.</span></span>  <span data-ttu-id="2f1ee-121">Cette méthode réduit le chevauchement entre l'exécution des déclencheurs.</span><span class="sxs-lookup"><span data-stu-id="2f1ee-121">This method minimizes the amount of overlap between the execution of the triggers.</span></span>  <span data-ttu-id="2f1ee-122">Prenons l'exemple d'un <xref:System.Activities.Statements.Pick> avec deux déclencheurs, où chaque déclencheur contient une activité <xref:System.ServiceModel.Activities.Receive> suivie d'une logique supplémentaire.</span><span class="sxs-lookup"><span data-stu-id="2f1ee-122">For example, consider a <xref:System.Activities.Statements.Pick> with two triggers, where each trigger contains a <xref:System.ServiceModel.Activities.Receive> activity followed by additional logic.</span></span>  <span data-ttu-id="2f1ee-123">Si la logique supplémentaire ajoute un point inactif, il est possible que les deux activités <xref:System.ServiceModel.Activities.Receive> s'exécutent correctement.</span><span class="sxs-lookup"><span data-stu-id="2f1ee-123">If the additional logic introduces an idle point, then there is the possibility of both <xref:System.ServiceModel.Activities.Receive> activities completing successfully.</span></span>  <span data-ttu-id="2f1ee-124">Un déclencheur sera exécuté entièrement, tandis que l'autre ne le sera que partiellement.</span><span class="sxs-lookup"><span data-stu-id="2f1ee-124">One trigger will fully complete, while another will partially complete.</span></span>  <span data-ttu-id="2f1ee-125">Dans certains scénarios, il n'est pas possible d'accepter un message et de terminer ensuite partiellement le traitement.</span><span class="sxs-lookup"><span data-stu-id="2f1ee-125">In some scenarios, accepting a message, and then partially completing the processing of it is unacceptable.</span></span>  <span data-ttu-id="2f1ee-126">Par conséquent, si des activités de messagerie intégrées WF, telles que <xref:System.ServiceModel.Activities.Receive> et <xref:System.ServiceModel.Activities.SendReply>, sont utilisées alors que <xref:System.ServiceModel.Activities.Receive> est utilisé communément dans le déclencheur, <xref:System.ServiceModel.Activities.SendReply> et toute autre logique doivent être placées dans l'action dans la mesure du possible.</span><span class="sxs-lookup"><span data-stu-id="2f1ee-126">Therefore, when using WF built-in messaging activities such as <xref:System.ServiceModel.Activities.Receive> and <xref:System.ServiceModel.Activities.SendReply>, while <xref:System.ServiceModel.Activities.Receive> is commonly used in the trigger, <xref:System.ServiceModel.Activities.SendReply> and other logic should be put in the action whenever possible.</span></span>  
  
## <a name="using-the-pick-activity-in-the-designer"></a><span data-ttu-id="2f1ee-127">Utilisation de l'activité Pick dans le concepteur</span><span class="sxs-lookup"><span data-stu-id="2f1ee-127">Using the Pick activity in the designer</span></span>  

 <span data-ttu-id="2f1ee-128">Pour utiliser l’activité Pick dans le concepteur, recherchez **Pick** et **PickBranch** dans la boîte à outils.</span><span class="sxs-lookup"><span data-stu-id="2f1ee-128">To use Pick in the designer, find **Pick** and **PickBranch** in the toolbox.</span></span>  <span data-ttu-id="2f1ee-129">Faites glisser **Pick** pour le déposer sur le canevas.</span><span class="sxs-lookup"><span data-stu-id="2f1ee-129">Drag and drop **Pick** onto the canvas.</span></span>  <span data-ttu-id="2f1ee-130">Par défaut, toute nouvelle activité **Pick** créée dans le concepteur contient deux branches.</span><span class="sxs-lookup"><span data-stu-id="2f1ee-130">By default, a new **Pick** Activity in the designer will contain two branches.</span></span>  <span data-ttu-id="2f1ee-131">Pour ajouter des branches supplémentaires, faites glisser l’activité **PickBranch** et déposez-la à côté des branches existantes.</span><span class="sxs-lookup"><span data-stu-id="2f1ee-131">To add additional branches, drag the **PickBranch** activity and drop it next to existing branches.</span></span> <span data-ttu-id="2f1ee-132">Les activités peuvent être déposées sur l’activité **Pick** dans la zone **Trigger** ou dans la zone **Action** de n’importe quelle activité **PickBranch**.</span><span class="sxs-lookup"><span data-stu-id="2f1ee-132">Activities can be dropped onto the **Pick** Activity into either the **Trigger** area or the **Action** area of any **PickBranch**.</span></span>  
  
## <a name="using-the-pick-activity-in-code"></a><span data-ttu-id="2f1ee-133">Utilisation de l'activité Pick dans le code</span><span class="sxs-lookup"><span data-stu-id="2f1ee-133">Using the Pick Activity in code</span></span>  

 <span data-ttu-id="2f1ee-134">L’activité <xref:System.Activities.Statements.Pick> est utilisée en remplissant sa collection <xref:System.Activities.Statements.Pick.Branches%2A> avec les activités <xref:System.Activities.Statements.PickBranch>.</span><span class="sxs-lookup"><span data-stu-id="2f1ee-134">The <xref:System.Activities.Statements.Pick> activity is used by populating its <xref:System.Activities.Statements.Pick.Branches%2A> collection with <xref:System.Activities.Statements.PickBranch> activities.</span></span> <span data-ttu-id="2f1ee-135">Chaque activité <xref:System.Activities.Statements.PickBranch> a une propriété <xref:System.Activities.Statements.PickBranch.Trigger%2A> de type <xref:System.Activities.Activity>.</span><span class="sxs-lookup"><span data-stu-id="2f1ee-135">The <xref:System.Activities.Statements.PickBranch> activities each have a <xref:System.Activities.Statements.PickBranch.Trigger%2A> property of type <xref:System.Activities.Activity>.</span></span> <span data-ttu-id="2f1ee-136">Une fois que l'activité spécifiée a été exécutée, l'action <xref:System.Activities.Statements.PickBranch.Action%2A> est exécutée à son tour.</span><span class="sxs-lookup"><span data-stu-id="2f1ee-136">When the specified activity completes execution, the <xref:System.Activities.Statements.PickBranch.Action%2A> executes.</span></span>  
  
 <span data-ttu-id="2f1ee-137">L'exemple de code suivant montre comment utiliser une activité <xref:System.Activities.Statements.Pick> pour implémenter un délai d'attente pour une activité qui lit une ligne de la console.</span><span class="sxs-lookup"><span data-stu-id="2f1ee-137">The following code example demonstrates how to use a <xref:System.Activities.Statements.Pick> activity to implement a timeout for an activity that reads a line from the console.</span></span>  
  
```csharp  
Sequence body = new Sequence()  
{  
    Variables = { name },  
    Activities =
   {  
       new System.Activities.Statements.Pick  
        {  
           Branches =
           {  
               new PickBranch  
               {  
                   Trigger = new ReadLine  
                   {  
                      Result = name,  
                      BookmarkName = "name"  
                   },  
                   Action = new WriteLine
                   {
                       Text = ExpressionServices.Convert<string>(ctx => "Hello " +
                           name.Get(ctx))
                   }  
               },  
               new PickBranch  
               {  
                   Trigger = new Delay  
                   {  
                      Duration = new TimeSpan(0, 0, 5)  
                   },  
                   Action = new WriteLine  
                   {  
                      Text = "Time is up."  
                   }  
               }  
           }  
       }  
   }  
};  
```  
  
```xaml  
<Sequence xmlns="http://schemas.microsoft.com/netfx/2009/xaml/activities" xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml">  
  <Sequence.Variables>  
    <Variable x:TypeArguments="x:String" Name="username" />  
  </Sequence.Variables>  
  <Pick>  
    <PickBranch>  
      <PickBranch.Trigger>  
        <ReadLine BookmarkName="name" Result="username" />  
      </PickBranch.Trigger>  
      <WriteLine>[String.Concat("Hello ", username)]</WriteLine>  
    </PickBranch>  
    <PickBranch>  
      <PickBranch.Trigger>  
        <Delay>00:00:05</Delay>  
      </PickBranch.Trigger>  
      <WriteLine>Time is up.</WriteLine>  
    </PickBranch>  
  </Pick>  
</Sequence>  
```
