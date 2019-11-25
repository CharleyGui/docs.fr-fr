---
title: Déclaration et déclenchement des événements
ms.date: 07/20/2015
helpviewer_keywords:
- declarations [Visual Basic], events
- events [Visual Basic], walkthroughs
- declaring events [Visual Basic], walkthroughs
- events [Visual Basic], declaring
- events [Visual Basic], raising
- raising events [Visual Basic], walkthroughs
ms.assetid: 8ffb3be8-097d-4d3c-b71e-04555ebda2a2
ms.openlocfilehash: 6f4c303604f9cf55b4ecd500636e0d2772b6234c
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74345085"
---
# <a name="walkthrough-declaring-and-raising-events-visual-basic"></a><span data-ttu-id="a7306-102">Procédure pas à pas : déclaration et déclenchement des événements (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a7306-102">Walkthrough: Declaring and Raising Events (Visual Basic)</span></span>
<span data-ttu-id="a7306-103">This walkthrough demonstrates how to declare and raise events for a class named `Widget`.</span><span class="sxs-lookup"><span data-stu-id="a7306-103">This walkthrough demonstrates how to declare and raise events for a class named `Widget`.</span></span> <span data-ttu-id="a7306-104">After you complete the steps, you might want to read the companion topic, [Walkthrough: Handling Events](../../../../visual-basic/programming-guide/language-features/events/walkthrough-handling-events.md), which shows how to use events from `Widget` objects to provide status information in an application.</span><span class="sxs-lookup"><span data-stu-id="a7306-104">After you complete the steps, you might want to read the companion topic, [Walkthrough: Handling Events](../../../../visual-basic/programming-guide/language-features/events/walkthrough-handling-events.md), which shows how to use events from `Widget` objects to provide status information in an application.</span></span>  
  
## <a name="the-widget-class"></a><span data-ttu-id="a7306-105">The Widget Class</span><span class="sxs-lookup"><span data-stu-id="a7306-105">The Widget Class</span></span>  
 <span data-ttu-id="a7306-106">Assume for the moment that you have a `Widget` class.</span><span class="sxs-lookup"><span data-stu-id="a7306-106">Assume for the moment that you have a `Widget` class.</span></span> <span data-ttu-id="a7306-107">Your `Widget` class has a method that can take a long time to execute, and you want your application to be able to put up some kind of completion indicator.</span><span class="sxs-lookup"><span data-stu-id="a7306-107">Your `Widget` class has a method that can take a long time to execute, and you want your application to be able to put up some kind of completion indicator.</span></span>  
  
 <span data-ttu-id="a7306-108">Of course, you could make the `Widget` object show a percent-complete dialog box, but then you would be stuck with that dialog box in every project in which you used the `Widget` class.</span><span class="sxs-lookup"><span data-stu-id="a7306-108">Of course, you could make the `Widget` object show a percent-complete dialog box, but then you would be stuck with that dialog box in every project in which you used the `Widget` class.</span></span> <span data-ttu-id="a7306-109">A good principle of object design is to let the application that uses an object handle the user interface—unless the whole purpose of the object is to manage a form or dialog box.</span><span class="sxs-lookup"><span data-stu-id="a7306-109">A good principle of object design is to let the application that uses an object handle the user interface—unless the whole purpose of the object is to manage a form or dialog box.</span></span>  
  
 <span data-ttu-id="a7306-110">The purpose of `Widget` is to perform other tasks, so it is better to add a `PercentDone` event and let the procedure that calls `Widget`'s methods handle that event and display status updates.</span><span class="sxs-lookup"><span data-stu-id="a7306-110">The purpose of `Widget` is to perform other tasks, so it is better to add a `PercentDone` event and let the procedure that calls `Widget`'s methods handle that event and display status updates.</span></span> <span data-ttu-id="a7306-111">The `PercentDone` event can also provide a mechanism for canceling the task.</span><span class="sxs-lookup"><span data-stu-id="a7306-111">The `PercentDone` event can also provide a mechanism for canceling the task.</span></span>  
  
#### <a name="to-build-the-code-example-for-this-topic"></a><span data-ttu-id="a7306-112">To build the code example for this topic</span><span class="sxs-lookup"><span data-stu-id="a7306-112">To build the code example for this topic</span></span>  
  
1. <span data-ttu-id="a7306-113">Open a new Visual Basic Windows Application project and create a form named `Form1`.</span><span class="sxs-lookup"><span data-stu-id="a7306-113">Open a new Visual Basic Windows Application project and create a form named `Form1`.</span></span>  
  
2. <span data-ttu-id="a7306-114">Add two buttons and a label to `Form1`.</span><span class="sxs-lookup"><span data-stu-id="a7306-114">Add two buttons and a label to `Form1`.</span></span>  
  
3. <span data-ttu-id="a7306-115">Nommez les objets de la façon indiquée dans le tableau suivant.</span><span class="sxs-lookup"><span data-stu-id="a7306-115">Name the objects as shown in the following table.</span></span>  
  
    |<span data-ttu-id="a7306-116">Objet</span><span class="sxs-lookup"><span data-stu-id="a7306-116">Object</span></span>|<span data-ttu-id="a7306-117">Property</span><span class="sxs-lookup"><span data-stu-id="a7306-117">Property</span></span>|<span data-ttu-id="a7306-118">Paramètre</span><span class="sxs-lookup"><span data-stu-id="a7306-118">Setting</span></span>|  
    |------------|--------------|-------------|  
    |`Button1`|`Text`|<span data-ttu-id="a7306-119">Start Task</span><span class="sxs-lookup"><span data-stu-id="a7306-119">Start Task</span></span>|  
    |`Button2`|`Text`|<span data-ttu-id="a7306-120">Annuler</span><span class="sxs-lookup"><span data-stu-id="a7306-120">Cancel</span></span>|  
    |`Label`|<span data-ttu-id="a7306-121">`(Name)`, `Text`</span><span class="sxs-lookup"><span data-stu-id="a7306-121">`(Name)`, `Text`</span></span>|<span data-ttu-id="a7306-122">lblPercentDone, 0</span><span class="sxs-lookup"><span data-stu-id="a7306-122">lblPercentDone, 0</span></span>|  
  
4. <span data-ttu-id="a7306-123">On the **Project** menu, choose **Add Class** to add a class named `Widget.vb` to the project.</span><span class="sxs-lookup"><span data-stu-id="a7306-123">On the **Project** menu, choose **Add Class** to add a class named `Widget.vb` to the project.</span></span>  
  
#### <a name="to-declare-an-event-for-the-widget-class"></a><span data-ttu-id="a7306-124">To declare an event for the Widget class</span><span class="sxs-lookup"><span data-stu-id="a7306-124">To declare an event for the Widget class</span></span>  
  
- <span data-ttu-id="a7306-125">Use the `Event` keyword to declare an event in the `Widget` class.</span><span class="sxs-lookup"><span data-stu-id="a7306-125">Use the `Event` keyword to declare an event in the `Widget` class.</span></span> <span data-ttu-id="a7306-126">Note that an event can have `ByVal` and `ByRef` arguments, as `Widget`'s `PercentDone` event demonstrates:</span><span class="sxs-lookup"><span data-stu-id="a7306-126">Note that an event can have `ByVal` and `ByRef` arguments, as `Widget`'s `PercentDone` event demonstrates:</span></span>  
  
     [!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnWalkthroughDeclaringAndRaisingEvents/VB/Widget.vb#1)]  
  
 <span data-ttu-id="a7306-127">When the calling object receives a `PercentDone` event, the `Percent` argument contains the percentage of the task that is complete.</span><span class="sxs-lookup"><span data-stu-id="a7306-127">When the calling object receives a `PercentDone` event, the `Percent` argument contains the percentage of the task that is complete.</span></span> <span data-ttu-id="a7306-128">The `Cancel` argument can be set to `True` to cancel the method that raised the event.</span><span class="sxs-lookup"><span data-stu-id="a7306-128">The `Cancel` argument can be set to `True` to cancel the method that raised the event.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="a7306-129">You can declare event arguments just as you do arguments of procedures, with the following exceptions: Events cannot have `Optional` or `ParamArray` arguments, and events do not have return values.</span><span class="sxs-lookup"><span data-stu-id="a7306-129">You can declare event arguments just as you do arguments of procedures, with the following exceptions: Events cannot have `Optional` or `ParamArray` arguments, and events do not have return values.</span></span>  
  
 <span data-ttu-id="a7306-130">The `PercentDone` event is raised by the `LongTask` method of the `Widget` class.</span><span class="sxs-lookup"><span data-stu-id="a7306-130">The `PercentDone` event is raised by the `LongTask` method of the `Widget` class.</span></span> <span data-ttu-id="a7306-131">`LongTask` takes two arguments: the length of time the method pretends to be doing work, and the minimum time interval before `LongTask` pauses to raise the `PercentDone` event.</span><span class="sxs-lookup"><span data-stu-id="a7306-131">`LongTask` takes two arguments: the length of time the method pretends to be doing work, and the minimum time interval before `LongTask` pauses to raise the `PercentDone` event.</span></span>  
  
#### <a name="to-raise-the-percentdone-event"></a><span data-ttu-id="a7306-132">To raise the PercentDone event</span><span class="sxs-lookup"><span data-stu-id="a7306-132">To raise the PercentDone event</span></span>  
  
1. <span data-ttu-id="a7306-133">To simplify access to the `Timer` property used by this class, add an `Imports` statement to the top of the declarations section of your class module, above the `Class Widget` statement.</span><span class="sxs-lookup"><span data-stu-id="a7306-133">To simplify access to the `Timer` property used by this class, add an `Imports` statement to the top of the declarations section of your class module, above the `Class Widget` statement.</span></span>  
  
     [!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnWalkthroughDeclaringAndRaisingEvents/VB/Widget.vb#2)]  
  
2. <span data-ttu-id="a7306-134">Ajoutez le code suivant à la classe `Widget` :</span><span class="sxs-lookup"><span data-stu-id="a7306-134">Add the following code to the `Widget` class:</span></span>  
  
     [!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnWalkthroughDeclaringAndRaisingEvents/VB/Widget.vb#3)]  
  
 <span data-ttu-id="a7306-135">When your application calls the `LongTask` method, the `Widget` class raises the `PercentDone` event every `MinimumInterval` seconds.</span><span class="sxs-lookup"><span data-stu-id="a7306-135">When your application calls the `LongTask` method, the `Widget` class raises the `PercentDone` event every `MinimumInterval` seconds.</span></span> <span data-ttu-id="a7306-136">When the event returns, `LongTask` checks to see if the `Cancel` argument was set to `True`.</span><span class="sxs-lookup"><span data-stu-id="a7306-136">When the event returns, `LongTask` checks to see if the `Cancel` argument was set to `True`.</span></span>  
  
 <span data-ttu-id="a7306-137">A few disclaimers are necessary here.</span><span class="sxs-lookup"><span data-stu-id="a7306-137">A few disclaimers are necessary here.</span></span> <span data-ttu-id="a7306-138">For simplicity, the `LongTask` procedure assumes you know in advance how long the task will take.</span><span class="sxs-lookup"><span data-stu-id="a7306-138">For simplicity, the `LongTask` procedure assumes you know in advance how long the task will take.</span></span> <span data-ttu-id="a7306-139">This is almost never the case.</span><span class="sxs-lookup"><span data-stu-id="a7306-139">This is almost never the case.</span></span> <span data-ttu-id="a7306-140">Dividing tasks into chunks of even size can be difficult, and often what matters most to users is simply the amount of time that passes before they get an indication that something is happening.</span><span class="sxs-lookup"><span data-stu-id="a7306-140">Dividing tasks into chunks of even size can be difficult, and often what matters most to users is simply the amount of time that passes before they get an indication that something is happening.</span></span>  
  
 <span data-ttu-id="a7306-141">You may have spotted another flaw in this sample.</span><span class="sxs-lookup"><span data-stu-id="a7306-141">You may have spotted another flaw in this sample.</span></span> <span data-ttu-id="a7306-142">The `Timer` property returns the number of seconds that have passed since midnight; therefore, the application gets stuck if it is started just before midnight.</span><span class="sxs-lookup"><span data-stu-id="a7306-142">The `Timer` property returns the number of seconds that have passed since midnight; therefore, the application gets stuck if it is started just before midnight.</span></span> <span data-ttu-id="a7306-143">A more careful approach to measuring time would take boundary conditions such as this into consideration, or avoid them altogether, using properties such as `Now`.</span><span class="sxs-lookup"><span data-stu-id="a7306-143">A more careful approach to measuring time would take boundary conditions such as this into consideration, or avoid them altogether, using properties such as `Now`.</span></span>  
  
 <span data-ttu-id="a7306-144">Now that the `Widget` class can raise events, you can move to the next walkthrough.</span><span class="sxs-lookup"><span data-stu-id="a7306-144">Now that the `Widget` class can raise events, you can move to the next walkthrough.</span></span> <span data-ttu-id="a7306-145">[Walkthrough: Handling Events](../../../../visual-basic/programming-guide/language-features/events/walkthrough-handling-events.md) demonstrates how to use `WithEvents` to associate an event handler with the `PercentDone` event.</span><span class="sxs-lookup"><span data-stu-id="a7306-145">[Walkthrough: Handling Events](../../../../visual-basic/programming-guide/language-features/events/walkthrough-handling-events.md) demonstrates how to use `WithEvents` to associate an event handler with the `PercentDone` event.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a7306-146">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a7306-146">See also</span></span>

- <xref:Microsoft.VisualBasic.DateAndTime.Timer%2A>
- <xref:Microsoft.VisualBasic.DateAndTime.Now%2A>
- [<span data-ttu-id="a7306-147">Procédure pas à pas : gestion des événements</span><span class="sxs-lookup"><span data-stu-id="a7306-147">Walkthrough: Handling Events</span></span>](../../../../visual-basic/programming-guide/language-features/events/walkthrough-handling-events.md)
- [<span data-ttu-id="a7306-148">Événements</span><span class="sxs-lookup"><span data-stu-id="a7306-148">Events</span></span>](../../../../visual-basic/programming-guide/language-features/events/index.md)
