---
title: "Procédure : S'abonner et se désabonner d’événements - Guide de programmation C#"
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- event handlers [C#], creating
- Code Editor, event handlers
- events [C#], creating using the IDE
ms.assetid: 6319f39f-282c-4173-8a62-6c4657cf51cd
ms.openlocfilehash: 365ea55a112a4a04964a8271f2f7e5591a3b0d5d
ms.sourcegitcommit: 621a5f6df00152006160987395b93b5b55f7ffcd
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66301044"
---
# <a name="how-to-subscribe-to-and-unsubscribe-from-events-c-programming-guide"></a><span data-ttu-id="43e35-102">Procédure : S'abonner et se désabonner d’événements (Guide de programmation C#)</span><span class="sxs-lookup"><span data-stu-id="43e35-102">How to: Subscribe to and Unsubscribe from Events (C# Programming Guide)</span></span>
<span data-ttu-id="43e35-103">Vous vous abonnez à un événement publié par une autre classe lorsque vous voulez écrire du code personnalisé qui doit être appelé quand cet événement est déclenché.</span><span class="sxs-lookup"><span data-stu-id="43e35-103">You subscribe to an event that is published by another class when you want to write custom code that is called when that event is raised.</span></span> <span data-ttu-id="43e35-104">Par exemple, vous pouvez vous abonner à l’événement `click` d’un bouton pour permettre à votre application de réagir lorsque l’utilisateur clique sur le bouton.</span><span class="sxs-lookup"><span data-stu-id="43e35-104">For example, you might subscribe to a button's `click` event in order to make your application do something useful when the user clicks the button.</span></span>  
  
### <a name="to-subscribe-to-events-by-using-the-visual-studio-ide"></a><span data-ttu-id="43e35-105">Pour s’abonner aux événements à l’aide de l’IDE de Visual Studio</span><span class="sxs-lookup"><span data-stu-id="43e35-105">To subscribe to events by using the Visual Studio IDE</span></span>  
  
1. <span data-ttu-id="43e35-106">Si vous ne voyez pas la fenêtre **Propriétés**, en mode **Création**, cliquez sur le formulaire ou le contrôle pour lequel vous voulez créer un gestionnaire d’événements, puis sélectionnez **Propriétés**.</span><span class="sxs-lookup"><span data-stu-id="43e35-106">If you cannot see the **Properties** window, in **Design** view, right-click the form or control for which you want to create an event handler, and select **Properties**.</span></span>  
  
2. <span data-ttu-id="43e35-107">En haut de la fenêtre **Propriétés**, cliquez sur l’icône **Événements**.</span><span class="sxs-lookup"><span data-stu-id="43e35-107">On top of the **Properties** window, click the **Events** icon.</span></span>  
  
3. <span data-ttu-id="43e35-108">Double-cliquez sur l’événement que vous voulez créer, par exemple l’événement `Load`.</span><span class="sxs-lookup"><span data-stu-id="43e35-108">Double-click the event that you want to create, for example the `Load` event.</span></span>  
  
     <span data-ttu-id="43e35-109">Visual C# crée une méthode de gestionnaire d’événements vide et l’ajoute à votre code.</span><span class="sxs-lookup"><span data-stu-id="43e35-109">Visual C# creates an empty event handler method and adds it to your code.</span></span> <span data-ttu-id="43e35-110">Vous pouvez également ajouter le code manuellement en mode **Code**.</span><span class="sxs-lookup"><span data-stu-id="43e35-110">Alternatively you can add the code manually in **Code** view.</span></span> <span data-ttu-id="43e35-111">Par exemple, les lignes de code suivantes déclarent une méthode de gestionnaire d’événements qui est appelée lorsque la classe `Form` déclenche l’événement `Load`.</span><span class="sxs-lookup"><span data-stu-id="43e35-111">For example, the following lines of code declare an event handler method that will be called when the `Form` class raises the `Load` event.</span></span>  
  
     [!code-csharp[csProgGuideEvents#11](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideEvents/CS/Events.cs#11)]  
  
     <span data-ttu-id="43e35-112">La ligne de code qui est nécessaire pour s’abonner à l’événement est aussi générée automatiquement dans la méthode `InitializeComponent`, dans le fichier Form1.Designer.cs de votre projet.</span><span class="sxs-lookup"><span data-stu-id="43e35-112">The line of code that is required to subscribe to the event is also automatically generated in the `InitializeComponent` method in the Form1.Designer.cs file in your project.</span></span> <span data-ttu-id="43e35-113">Elle ressemble à ceci :</span><span class="sxs-lookup"><span data-stu-id="43e35-113">It resembles this:</span></span>  
  
    ```csharp
    this.Load += new System.EventHandler(this.Form1_Load);  
    ```  
  
### <a name="to-subscribe-to-events-programmatically"></a><span data-ttu-id="43e35-114">Pour s’abonner aux événements par programmation</span><span class="sxs-lookup"><span data-stu-id="43e35-114">To subscribe to events programmatically</span></span>  
  
1. <span data-ttu-id="43e35-115">Définissez une méthode de gestionnaire d’événements dont la signature correspond à la signature du délégué de l’événement.</span><span class="sxs-lookup"><span data-stu-id="43e35-115">Define an event handler method whose signature matches the delegate signature for the event.</span></span> <span data-ttu-id="43e35-116">Par exemple, si l’événement est basé sur le type délégué <xref:System.EventHandler>, le code suivant représente le stub de méthode :</span><span class="sxs-lookup"><span data-stu-id="43e35-116">For example, if the event is based on the <xref:System.EventHandler> delegate type, the following code represents the method stub:</span></span>  
  
    ```csharp
    void HandleCustomEvent(object sender, CustomEventArgs a)  
    {  
       // Do something useful here.  
    }  
    ```  
  
2. <span data-ttu-id="43e35-117">Utilisez l’opérateur d’assignation d’addition (`+=`) pour attacher votre gestionnaire d’événements à l’événement.</span><span class="sxs-lookup"><span data-stu-id="43e35-117">Use the addition assignment operator (`+=`) to attach your event handler to the event.</span></span> <span data-ttu-id="43e35-118">Dans l’exemple suivant, nous allons supposer qu’un objet nommé `publisher` a un événement nommé `RaiseCustomEvent`.</span><span class="sxs-lookup"><span data-stu-id="43e35-118">In the following example, assume that an object named `publisher` has an event named `RaiseCustomEvent`.</span></span> <span data-ttu-id="43e35-119">Notez que la classe d’abonné nécessite une référence à la classe d’éditeur pour s’abonner à ses événements.</span><span class="sxs-lookup"><span data-stu-id="43e35-119">Note that the subscriber class needs a reference to the publisher class in order to subscribe to its events.</span></span>  
  
    ```csharp
    publisher.RaiseCustomEvent += HandleCustomEvent;  
    ```  
  
     <span data-ttu-id="43e35-120">Notez que la syntaxe précédente est une nouveauté du langage C# 2.0.</span><span class="sxs-lookup"><span data-stu-id="43e35-120">Note that the previous syntax is new in C# 2.0.</span></span> <span data-ttu-id="43e35-121">Elle équivaut exactement à la syntaxe du C# 1.0, dans laquelle le délégué d’encapsulation doit être explicitement créé à l’aide du mot clé `new` :</span><span class="sxs-lookup"><span data-stu-id="43e35-121">It is exactly equivalent to the C# 1.0 syntax in which the encapsulating delegate must be explicitly created by using the `new` keyword:</span></span>  
  
    ```csharp
    publisher.RaiseCustomEvent += new CustomEventHandler(HandleCustomEvent);  
    ```  
  
     <span data-ttu-id="43e35-122">Vous pouvez également ajouter un gestionnaire d’événements à l’aide d’une expression lambda :</span><span class="sxs-lookup"><span data-stu-id="43e35-122">An event handler can also be added by using a lambda expression:</span></span>  
  
    ```csharp
    public Form1()  
    {  
        InitializeComponent();  
        // Use a lambda expression to define an event handler.  
        this.Click += (s,e) => { MessageBox.Show(  
           ((MouseEventArgs)e).Location.ToString());};  
    }  
    ```  
  
     <span data-ttu-id="43e35-123">Pour plus d'informations, voir [Procédure : Utiliser des expressions lambda en dehors de LINQ](../../../csharp/programming-guide/statements-expressions-operators/how-to-use-lambda-expressions-outside-linq.md).</span><span class="sxs-lookup"><span data-stu-id="43e35-123">For more information, see [How to: Use Lambda Expressions Outside LINQ](../../../csharp/programming-guide/statements-expressions-operators/how-to-use-lambda-expressions-outside-linq.md).</span></span>  
  
### <a name="to-subscribe-to-events-by-using-an-anonymous-method"></a><span data-ttu-id="43e35-124">Pour s’abonner aux événements à l’aide d’une méthode anonyme</span><span class="sxs-lookup"><span data-stu-id="43e35-124">To subscribe to events by using an anonymous method</span></span>  
  
- <span data-ttu-id="43e35-125">Si vous savez que vous n’aurez pas à vous désabonner d’un événement, vous pouvez utiliser l’opérateur d’assignation d’addition (`+=`) pour attacher une méthode anonyme à l’événement.</span><span class="sxs-lookup"><span data-stu-id="43e35-125">If you will not have to unsubscribe to an event later, you can use the addition assignment operator (`+=`) to attach an anonymous method to the event.</span></span> <span data-ttu-id="43e35-126">Dans l’exemple suivant, nous supposons qu’un objet nommé `publisher` a un événement nommé `RaiseCustomEvent`, et qu’une classe `CustomEventArgs` a également été définie pour contenir des informations d’événements spécialisés.</span><span class="sxs-lookup"><span data-stu-id="43e35-126">In the following example, assume that an object named `publisher` has an event named `RaiseCustomEvent` and that a `CustomEventArgs` class has also been defined to carry some kind of specialized event information.</span></span> <span data-ttu-id="43e35-127">Notez que la classe d’abonné nécessite une référence à `publisher` pour s’abonner à ses événements.</span><span class="sxs-lookup"><span data-stu-id="43e35-127">Note that the subscriber class needs a reference to `publisher` in order to subscribe to its events.</span></span>  
  
    ```csharp
    publisher.RaiseCustomEvent += delegate(object o, CustomEventArgs e)  
    {  
      string s = o.ToString() + " " + e.ToString();  
      Console.WriteLine(s);  
    };  
    ```  
  
     <span data-ttu-id="43e35-128">Il est important de noter que vous ne pourrez pas vous désabonner facilement d’un événement si vous avez utilisé une fonction anonyme pour vous y inscrire.</span><span class="sxs-lookup"><span data-stu-id="43e35-128">It is important to notice that you cannot easily unsubscribe from an event if you used an anonymous function to subscribe to it.</span></span> <span data-ttu-id="43e35-129">Pour vous désinscrire dans ce scénario, accédez au code dans lequel vous vous êtes abonné à l’événement, stockez la méthode anonyme dans une variable de délégué, puis ajoutez le délégué à l’événement.</span><span class="sxs-lookup"><span data-stu-id="43e35-129">To unsubscribe in this scenario, it is necessary to go back to the code where you subscribe to the event, store the anonymous method in a delegate variable, and then add the delegate to the event.</span></span> <span data-ttu-id="43e35-130">En général, nous recommandons de ne pas utiliser de fonctions anonymes pour vous abonner aux événements si vous devez vous en désabonner plus tard dans votre code.</span><span class="sxs-lookup"><span data-stu-id="43e35-130">In general, we recommend that you do not use anonymous functions to subscribe to events if you will have to unsubscribe from the event at some later point in your code.</span></span> <span data-ttu-id="43e35-131">Pour plus d’informations sur les fonctions anonymes, consultez [Fonctions anonymes](../../../csharp/programming-guide/statements-expressions-operators/anonymous-functions.md).</span><span class="sxs-lookup"><span data-stu-id="43e35-131">For more information about anonymous functions, see [Anonymous Functions](../../../csharp/programming-guide/statements-expressions-operators/anonymous-functions.md).</span></span>  
  
## <a name="unsubscribing"></a><span data-ttu-id="43e35-132">Désabonnement</span><span class="sxs-lookup"><span data-stu-id="43e35-132">Unsubscribing</span></span>  
 <span data-ttu-id="43e35-133">Pour éviter que votre gestionnaire d’événements ne soit appelé lorsque l’événement est déclenché, désabonnez-vous de l’événement.</span><span class="sxs-lookup"><span data-stu-id="43e35-133">To prevent your event handler from being invoked when the event is raised, unsubscribe from the event.</span></span> <span data-ttu-id="43e35-134">Pour empêcher les fuites de ressources, vous devez vous désabonner des événements avant d’éliminer un objet d’abonné.</span><span class="sxs-lookup"><span data-stu-id="43e35-134">In order to prevent resource leaks, you should unsubscribe from events before you dispose of a subscriber object.</span></span> <span data-ttu-id="43e35-135">Tant que vous êtes abonné à un événement, le délégué de multidiffusion qui se trouve sous l’événement, dans l’objet de publication, comporte une référence au délégué qui encapsule le gestionnaire d’événements de l’abonné.</span><span class="sxs-lookup"><span data-stu-id="43e35-135">Until you unsubscribe from an event, the multicast delegate that underlies the event in the publishing object has a reference to the delegate that encapsulates the subscriber's event handler.</span></span> <span data-ttu-id="43e35-136">Tant que l’objet de publication contient cette référence, le garbage collection ne supprime pas l’objet d’abonné.</span><span class="sxs-lookup"><span data-stu-id="43e35-136">As long as the publishing object holds that reference, garbage collection will not delete your subscriber object.</span></span>  
  
#### <a name="to-unsubscribe-from-an-event"></a><span data-ttu-id="43e35-137">Pour se désabonner d’un événement</span><span class="sxs-lookup"><span data-stu-id="43e35-137">To unsubscribe from an event</span></span>  
  
- <span data-ttu-id="43e35-138">Utilisez l’opérateur d’assignation de soustraction (`-=`) pour vous désabonner d’un événement :</span><span class="sxs-lookup"><span data-stu-id="43e35-138">Use the subtraction assignment operator (`-=`) to unsubscribe from an event:</span></span>  
  
    ```csharp
    publisher.RaiseCustomEvent -= HandleCustomEvent;  
    ```  
  
     <span data-ttu-id="43e35-139">Lorsque tous les abonnés se sont désabonnés d’un événement, l’instance d’événement de la classe d’éditeur est définie sur `null`.</span><span class="sxs-lookup"><span data-stu-id="43e35-139">When all subscribers have unsubscribed from an event, the event instance in the publisher class is set to `null`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="43e35-140">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="43e35-140">See also</span></span>

- [<span data-ttu-id="43e35-141">Événements</span><span class="sxs-lookup"><span data-stu-id="43e35-141">Events</span></span>](../../../csharp/programming-guide/events/index.md)
- [<span data-ttu-id="43e35-142">event</span><span class="sxs-lookup"><span data-stu-id="43e35-142">event</span></span>](../../../csharp/language-reference/keywords/event.md)
- [<span data-ttu-id="43e35-143">Guide pratique pour publier des événements conformes aux indications du .NET Framework</span><span class="sxs-lookup"><span data-stu-id="43e35-143">How to: Publish Events that Conform to .NET Framework Guidelines</span></span>](../../../csharp/programming-guide/events/how-to-publish-events-that-conform-to-net-framework-guidelines.md)
- [<span data-ttu-id="43e35-144">- et -=, opérateurs</span><span class="sxs-lookup"><span data-stu-id="43e35-144">- and -= operators</span></span>](../../language-reference/operators/subtraction-operator.md)
- [<span data-ttu-id="43e35-145">+ et +=, opérateurs</span><span class="sxs-lookup"><span data-stu-id="43e35-145">+ and += operators</span></span>](../../language-reference/operators/addition-operator.md)
