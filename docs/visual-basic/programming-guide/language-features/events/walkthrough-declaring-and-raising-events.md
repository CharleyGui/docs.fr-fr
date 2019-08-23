---
title: Déclaration et déclenchement d’événements (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- declarations [Visual Basic], events
- events [Visual Basic], walkthroughs
- declaring events [Visual Basic], walkthroughs
- events [Visual Basic], declaring
- events [Visual Basic], raising
- raising events [Visual Basic], walkthroughs
ms.assetid: 8ffb3be8-097d-4d3c-b71e-04555ebda2a2
ms.openlocfilehash: 20e2b0efbf40597049c515134f408927f18d5603
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69956339"
---
# <a name="walkthrough-declaring-and-raising-events-visual-basic"></a><span data-ttu-id="8d7e0-102">Procédure pas à pas : Déclaration et déclenchement d’événements (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8d7e0-102">Walkthrough: Declaring and Raising Events (Visual Basic)</span></span>
<span data-ttu-id="8d7e0-103">Cette procédure pas à pas montre comment déclarer et déclencher des événements pour `Widget`une classe nommée.</span><span class="sxs-lookup"><span data-stu-id="8d7e0-103">This walkthrough demonstrates how to declare and raise events for a class named `Widget`.</span></span> <span data-ttu-id="8d7e0-104">Une fois les étapes terminées, vous souhaiterez peut-être lire la [rubrique d’accompagnement, procédure pas à pas: Gestion des](../../../../visual-basic/programming-guide/language-features/events/walkthrough-handling-events.md)événements, qui montre comment utiliser des événements `Widget` d’objets pour fournir des informations d’État dans une application.</span><span class="sxs-lookup"><span data-stu-id="8d7e0-104">After you complete the steps, you might want to read the companion topic, [Walkthrough: Handling Events](../../../../visual-basic/programming-guide/language-features/events/walkthrough-handling-events.md), which shows how to use events from `Widget` objects to provide status information in an application.</span></span>  
  
## <a name="the-widget-class"></a><span data-ttu-id="8d7e0-105">Classe widget</span><span class="sxs-lookup"><span data-stu-id="8d7e0-105">The Widget Class</span></span>  
 <span data-ttu-id="8d7e0-106">Supposons que vous ayez une `Widget` classe.</span><span class="sxs-lookup"><span data-stu-id="8d7e0-106">Assume for the moment that you have a `Widget` class.</span></span> <span data-ttu-id="8d7e0-107">Votre `Widget` classe a une méthode qui peut prendre beaucoup de temps pour s’exécuter, et vous souhaitez que votre application puisse mettre en place un type d’indicateur d’achèvement.</span><span class="sxs-lookup"><span data-stu-id="8d7e0-107">Your `Widget` class has a method that can take a long time to execute, and you want your application to be able to put up some kind of completion indicator.</span></span>  
  
 <span data-ttu-id="8d7e0-108">Bien entendu, vous pouvez faire en `Widget` sorte que l’objet affiche une boîte de dialogue de pourcentage de réalisation, mais vous serez alors bloqué avec cette boîte de dialogue dans chaque projet `Widget` dans lequel vous avez utilisé la classe.</span><span class="sxs-lookup"><span data-stu-id="8d7e0-108">Of course, you could make the `Widget` object show a percent-complete dialog box, but then you would be stuck with that dialog box in every project in which you used the `Widget` class.</span></span> <span data-ttu-id="8d7e0-109">Un bon principe de la conception d’objets est de permettre à l’application qui utilise un objet de gérer l’interface utilisateur, à moins que l’objectif entier de l’objet ne soit de gérer un formulaire ou une boîte de dialogue.</span><span class="sxs-lookup"><span data-stu-id="8d7e0-109">A good principle of object design is to let the application that uses an object handle the user interface—unless the whole purpose of the object is to manage a form or dialog box.</span></span>  
  
 <span data-ttu-id="8d7e0-110">L’objectif de `Widget` est d’effectuer d’autres tâches. il est donc préférable d’ajouter `PercentDone` un événement et de laisser la procédure `Widget`qui appelle les méthodes pour gérer cet événement et afficher les mises à jour de l’État.</span><span class="sxs-lookup"><span data-stu-id="8d7e0-110">The purpose of `Widget` is to perform other tasks, so it is better to add a `PercentDone` event and let the procedure that calls `Widget`'s methods handle that event and display status updates.</span></span> <span data-ttu-id="8d7e0-111">L' `PercentDone` événement peut également fournir un mécanisme d’annulation de la tâche.</span><span class="sxs-lookup"><span data-stu-id="8d7e0-111">The `PercentDone` event can also provide a mechanism for canceling the task.</span></span>  
  
#### <a name="to-build-the-code-example-for-this-topic"></a><span data-ttu-id="8d7e0-112">Pour générer l’exemple de code pour cette rubrique</span><span class="sxs-lookup"><span data-stu-id="8d7e0-112">To build the code example for this topic</span></span>  
  
1. <span data-ttu-id="8d7e0-113">Ouvrez un nouveau Visual Basic projet d’application Windows et créez un formulaire `Form1`nommé.</span><span class="sxs-lookup"><span data-stu-id="8d7e0-113">Open a new Visual Basic Windows Application project and create a form named `Form1`.</span></span>  
  
2. <span data-ttu-id="8d7e0-114">Ajoutez deux boutons et une étiquette à `Form1`.</span><span class="sxs-lookup"><span data-stu-id="8d7e0-114">Add two buttons and a label to `Form1`.</span></span>  
  
3. <span data-ttu-id="8d7e0-115">Nommez les objets de la façon indiquée dans le tableau suivant.</span><span class="sxs-lookup"><span data-stu-id="8d7e0-115">Name the objects as shown in the following table.</span></span>  
  
    |<span data-ttu-id="8d7e0-116">Objet</span><span class="sxs-lookup"><span data-stu-id="8d7e0-116">Object</span></span>|<span data-ttu-id="8d7e0-117">Propriété</span><span class="sxs-lookup"><span data-stu-id="8d7e0-117">Property</span></span>|<span data-ttu-id="8d7e0-118">Paramètre</span><span class="sxs-lookup"><span data-stu-id="8d7e0-118">Setting</span></span>|  
    |------------|--------------|-------------|  
    |`Button1`|`Text`|<span data-ttu-id="8d7e0-119">Démarrer la tâche</span><span class="sxs-lookup"><span data-stu-id="8d7e0-119">Start Task</span></span>|  
    |`Button2`|`Text`|<span data-ttu-id="8d7e0-120">Annuler</span><span class="sxs-lookup"><span data-stu-id="8d7e0-120">Cancel</span></span>|  
    |`Label`|<span data-ttu-id="8d7e0-121">`(Name)`, `Text`</span><span class="sxs-lookup"><span data-stu-id="8d7e0-121">`(Name)`, `Text`</span></span>|<span data-ttu-id="8d7e0-122">lblPercentDone, 0</span><span class="sxs-lookup"><span data-stu-id="8d7e0-122">lblPercentDone, 0</span></span>|  
  
4. <span data-ttu-id="8d7e0-123">Dans le menu **projet** , choisissez **Ajouter une classe** pour ajouter une classe `Widget.vb` nommée au projet.</span><span class="sxs-lookup"><span data-stu-id="8d7e0-123">On the **Project** menu, choose **Add Class** to add a class named `Widget.vb` to the project.</span></span>  
  
#### <a name="to-declare-an-event-for-the-widget-class"></a><span data-ttu-id="8d7e0-124">Pour déclarer un événement pour la classe widget</span><span class="sxs-lookup"><span data-stu-id="8d7e0-124">To declare an event for the Widget class</span></span>  
  
- <span data-ttu-id="8d7e0-125">Utilisez le `Event` mot clé pour déclarer un événement dans `Widget` la classe.</span><span class="sxs-lookup"><span data-stu-id="8d7e0-125">Use the `Event` keyword to declare an event in the `Widget` class.</span></span> <span data-ttu-id="8d7e0-126">Notez qu’un événement peut avoir `ByVal` des `ByRef` arguments et, `Widget`comme `PercentDone` le montre l’événement de:</span><span class="sxs-lookup"><span data-stu-id="8d7e0-126">Note that an event can have `ByVal` and `ByRef` arguments, as `Widget`'s `PercentDone` event demonstrates:</span></span>  
  
     [!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnWalkthroughDeclaringAndRaisingEvents/VB/Widget.vb#1)]  
  
 <span data-ttu-id="8d7e0-127">Lorsque l’objet appelant reçoit un `PercentDone` événement, l' `Percent` argument contient le pourcentage de la tâche qui est terminé.</span><span class="sxs-lookup"><span data-stu-id="8d7e0-127">When the calling object receives a `PercentDone` event, the `Percent` argument contains the percentage of the task that is complete.</span></span> <span data-ttu-id="8d7e0-128">L' `Cancel` argument peut avoir la `True` valeur pour annuler la méthode qui a déclenché l’événement.</span><span class="sxs-lookup"><span data-stu-id="8d7e0-128">The `Cancel` argument can be set to `True` to cancel the method that raised the event.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="8d7e0-129">Vous pouvez déclarer des arguments d’événement de la même façon que des arguments de procédures, avec les exceptions suivantes: Les événements ne `Optional` peuvent `ParamArray` pas avoir d’arguments ou, et les événements n’ont pas de valeurs de retour.</span><span class="sxs-lookup"><span data-stu-id="8d7e0-129">You can declare event arguments just as you do arguments of procedures, with the following exceptions: Events cannot have `Optional` or `ParamArray` arguments, and events do not have return values.</span></span>  
  
 <span data-ttu-id="8d7e0-130">L' `PercentDone` événement est déclenché par la `LongTask` méthode de la `Widget` classe.</span><span class="sxs-lookup"><span data-stu-id="8d7e0-130">The `PercentDone` event is raised by the `LongTask` method of the `Widget` class.</span></span> <span data-ttu-id="8d7e0-131">`LongTask`accepte deux arguments: la durée pendant laquelle la méthode prétend exécuter le travail, et l’intervalle de temps minimal avant `LongTask` les pauses pour déclencher l' `PercentDone` événement.</span><span class="sxs-lookup"><span data-stu-id="8d7e0-131">`LongTask` takes two arguments: the length of time the method pretends to be doing work, and the minimum time interval before `LongTask` pauses to raise the `PercentDone` event.</span></span>  
  
#### <a name="to-raise-the-percentdone-event"></a><span data-ttu-id="8d7e0-132">Pour déclencher l’événement PercentDone</span><span class="sxs-lookup"><span data-stu-id="8d7e0-132">To raise the PercentDone event</span></span>  
  
1. <span data-ttu-id="8d7e0-133">Pour simplifier l’accès à `Timer` la propriété utilisée par cette classe, ajoutez `Imports` une instruction en haut de la section déclarations de votre module de classe, au `Class Widget` -dessus de l’instruction.</span><span class="sxs-lookup"><span data-stu-id="8d7e0-133">To simplify access to the `Timer` property used by this class, add an `Imports` statement to the top of the declarations section of your class module, above the `Class Widget` statement.</span></span>  
  
     [!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnWalkthroughDeclaringAndRaisingEvents/VB/Widget.vb#2)]  
  
2. <span data-ttu-id="8d7e0-134">Ajoutez le code suivant à la classe `Widget` :</span><span class="sxs-lookup"><span data-stu-id="8d7e0-134">Add the following code to the `Widget` class:</span></span>  
  
     [!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnWalkthroughDeclaringAndRaisingEvents/VB/Widget.vb#3)]  
  
 <span data-ttu-id="8d7e0-135">Lorsque votre application appelle la `LongTask` méthode, la `Widget` classe déclenche l' `PercentDone` événement toutes `MinimumInterval` les secondes.</span><span class="sxs-lookup"><span data-stu-id="8d7e0-135">When your application calls the `LongTask` method, the `Widget` class raises the `PercentDone` event every `MinimumInterval` seconds.</span></span> <span data-ttu-id="8d7e0-136">Lorsque l’événement est retourné `LongTask` , vérifie si l’argument `Cancel` a la valeur `True`.</span><span class="sxs-lookup"><span data-stu-id="8d7e0-136">When the event returns, `LongTask` checks to see if the `Cancel` argument was set to `True`.</span></span>  
  
 <span data-ttu-id="8d7e0-137">Quelques exclusions de responsabilité sont nécessaires ici.</span><span class="sxs-lookup"><span data-stu-id="8d7e0-137">A few disclaimers are necessary here.</span></span> <span data-ttu-id="8d7e0-138">Par souci de simplicité `LongTask` , la procédure suppose que vous savez à l’avance le temps nécessaire à la tâche.</span><span class="sxs-lookup"><span data-stu-id="8d7e0-138">For simplicity, the `LongTask` procedure assumes you know in advance how long the task will take.</span></span> <span data-ttu-id="8d7e0-139">Ce n’est presque jamais le cas.</span><span class="sxs-lookup"><span data-stu-id="8d7e0-139">This is almost never the case.</span></span> <span data-ttu-id="8d7e0-140">La Division des tâches en segments de taille égale peut être difficile, et souvent ce qui est le plus important pour les utilisateurs est simplement le temps qui s’écoule avant qu’ils ne reçoivent une indication qu’un événement se produit.</span><span class="sxs-lookup"><span data-stu-id="8d7e0-140">Dividing tasks into chunks of even size can be difficult, and often what matters most to users is simply the amount of time that passes before they get an indication that something is happening.</span></span>  
  
 <span data-ttu-id="8d7e0-141">Vous avez peut-être repéré un autre défaut dans cet exemple.</span><span class="sxs-lookup"><span data-stu-id="8d7e0-141">You may have spotted another flaw in this sample.</span></span> <span data-ttu-id="8d7e0-142">La `Timer` propriété retourne le nombre de secondes qui se sont écoulées depuis minuit; par conséquent, l’application est bloquée si elle est démarrée juste avant minuit.</span><span class="sxs-lookup"><span data-stu-id="8d7e0-142">The `Timer` property returns the number of seconds that have passed since midnight; therefore, the application gets stuck if it is started just before midnight.</span></span> <span data-ttu-id="8d7e0-143">Une approche plus prudente de la mesure du temps consisterait à prendre en considération des conditions de limites, ou à les éviter, à `Now`l’aide de propriétés telles que.</span><span class="sxs-lookup"><span data-stu-id="8d7e0-143">A more careful approach to measuring time would take boundary conditions such as this into consideration, or avoid them altogether, using properties such as `Now`.</span></span>  
  
 <span data-ttu-id="8d7e0-144">Maintenant que la `Widget` classe peut déclencher des événements, vous pouvez passer à la procédure pas à pas suivante.</span><span class="sxs-lookup"><span data-stu-id="8d7e0-144">Now that the `Widget` class can raise events, you can move to the next walkthrough.</span></span> <span data-ttu-id="8d7e0-145">[Procédure pas à pas : La gestion](../../../../visual-basic/programming-guide/language-features/events/walkthrough-handling-events.md) des événements montre comment `WithEvents` utiliser pour associer un gestionnaire d’événements `PercentDone` à l’événement.</span><span class="sxs-lookup"><span data-stu-id="8d7e0-145">[Walkthrough: Handling Events](../../../../visual-basic/programming-guide/language-features/events/walkthrough-handling-events.md) demonstrates how to use `WithEvents` to associate an event handler with the `PercentDone` event.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8d7e0-146">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8d7e0-146">See also</span></span>

- <xref:Microsoft.VisualBasic.DateAndTime.Timer%2A>
- <xref:Microsoft.VisualBasic.DateAndTime.Now%2A>
- [<span data-ttu-id="8d7e0-147">Procédure pas à pas : Gestion des événements</span><span class="sxs-lookup"><span data-stu-id="8d7e0-147">Walkthrough: Handling Events</span></span>](../../../../visual-basic/programming-guide/language-features/events/walkthrough-handling-events.md)
- [<span data-ttu-id="8d7e0-148">Événements</span><span class="sxs-lookup"><span data-stu-id="8d7e0-148">Events</span></span>](../../../../visual-basic/programming-guide/language-features/events/index.md)
