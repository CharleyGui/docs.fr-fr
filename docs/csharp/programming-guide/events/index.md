---
title: Événements - Guide de programmation C#
ms.date: 07/20/2015
helpviewer_keywords:
- classes [C#], events
- C# language, events
- events [C#]
ms.assetid: a8e51b22-d294-44fb-9539-0072f06c4cb3
ms.openlocfilehash: 183f53a579bdd9f70deb16ca9157c377fa3aff3f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/15/2020
ms.locfileid: "75712310"
---
# <a name="events-c-programming-guide"></a><span data-ttu-id="194c7-102">Événements (Guide de programmation C#)</span><span class="sxs-lookup"><span data-stu-id="194c7-102">Events (C# Programming Guide)</span></span>
<span data-ttu-id="194c7-103">Les événements permettent à une [classe](../../language-reference/keywords/class.md) ou à un objet de notifier d’autres classes ou objets quand quelque chose de significatif se produit.</span><span class="sxs-lookup"><span data-stu-id="194c7-103">Events enable a [class](../../language-reference/keywords/class.md) or object to notify other classes or objects when something of interest occurs.</span></span> <span data-ttu-id="194c7-104">La classe qui envoie (ou *déclenche*) l’événement est appelée *publieur* et les classes qui reçoivent (ou *gèrent*) l’événement sont appelées *abonnés*.</span><span class="sxs-lookup"><span data-stu-id="194c7-104">The class that sends (or *raises*) the event is called the *publisher* and the classes that receive (or *handle*) the event are called *subscribers*.</span></span>  
  
<span data-ttu-id="194c7-105">Dans une application C# Windows Forms ou web classique, vous vous abonnez à des événements déclenchés par des contrôles, comme des boutons et des zones de liste.</span><span class="sxs-lookup"><span data-stu-id="194c7-105">In a typical C# Windows Forms or Web application, you subscribe to events raised by controls such as buttons and list boxes.</span></span> <span data-ttu-id="194c7-106">Vous pouvez utiliser l’IDE Visual C# pour parcourir les événements publiés par un contrôle et sélectionner ceux que vous voulez gérer.</span><span class="sxs-lookup"><span data-stu-id="194c7-106">You can use the Visual C# integrated development environment (IDE) to browse the events that a control publishes and select the ones that you want to handle.</span></span> <span data-ttu-id="194c7-107">L’IDE permet d’ajouter automatiquement une méthode de gestionnaire d’événements vide et le code pour vous abonner à l’événement.</span><span class="sxs-lookup"><span data-stu-id="194c7-107">The IDE provides an easy way to automatically add an empty event handler method and the code to subscribe to the event.</span></span> <span data-ttu-id="194c7-108">Pour plus d’informations, voir [Comment vous abonner et désabonner des événements](./how-to-subscribe-to-and-unsubscribe-from-events.md).</span><span class="sxs-lookup"><span data-stu-id="194c7-108">For more information, see [How to subscribe to and unsubscribe from events](./how-to-subscribe-to-and-unsubscribe-from-events.md).</span></span>
  
## <a name="events-overview"></a><span data-ttu-id="194c7-109">Vue d'ensemble des événements</span><span class="sxs-lookup"><span data-stu-id="194c7-109">Events Overview</span></span>  
 <span data-ttu-id="194c7-110">Les événements ont les propriétés suivantes :</span><span class="sxs-lookup"><span data-stu-id="194c7-110">Events have the following properties:</span></span>  
  
- <span data-ttu-id="194c7-111">Le publieur détermine quand un événement est déclenché ; les abonnés déterminent l’action entreprise en réponse à l’événement.</span><span class="sxs-lookup"><span data-stu-id="194c7-111">The publisher determines when an event is raised; the subscribers determine what action is taken in response to the event.</span></span>  
  
- <span data-ttu-id="194c7-112">Un événement peut avoir plusieurs abonnés.</span><span class="sxs-lookup"><span data-stu-id="194c7-112">An event can have multiple subscribers.</span></span> <span data-ttu-id="194c7-113">Un abonné peut gérer plusieurs événements provenant de plusieurs publieurs.</span><span class="sxs-lookup"><span data-stu-id="194c7-113">A subscriber can handle multiple events from multiple publishers.</span></span>  
  
- <span data-ttu-id="194c7-114">Les événements qui n’ont aucun abonné ne sont jamais déclenchés.</span><span class="sxs-lookup"><span data-stu-id="194c7-114">Events that have no subscribers are never raised.</span></span>  
  
- <span data-ttu-id="194c7-115">Les événements sont généralement utilisés pour signaler des actions de l’utilisateur, comme les clics de bouton ou les sélections de menu dans les interfaces utilisateur graphiques.</span><span class="sxs-lookup"><span data-stu-id="194c7-115">Events are typically used to signal user actions such as button clicks or menu selections in graphical user interfaces.</span></span>  
  
- <span data-ttu-id="194c7-116">Quand un événement a plusieurs abonnés, les gestionnaires d’événements sont appelées de façon synchrone quand un événement est déclenché.</span><span class="sxs-lookup"><span data-stu-id="194c7-116">When an event has multiple subscribers, the event handlers are invoked synchronously when an event is raised.</span></span> <span data-ttu-id="194c7-117">Pour appeler des événements de façon asynchrone, consultez [Calling Synchronous Methods Asynchronously](../../../standard/asynchronous-programming-patterns/calling-synchronous-methods-asynchronously.md).</span><span class="sxs-lookup"><span data-stu-id="194c7-117">To invoke events asynchronously, see [Calling Synchronous Methods Asynchronously](../../../standard/asynchronous-programming-patterns/calling-synchronous-methods-asynchronously.md).</span></span>  
  
- <span data-ttu-id="194c7-118">Dans la bibliothèque de classes .NET Framework, les événements sont basés sur le délégué <xref:System.EventHandler> et la classe de base <xref:System.EventArgs>.</span><span class="sxs-lookup"><span data-stu-id="194c7-118">In the .NET Framework class library, events are based on the <xref:System.EventHandler> delegate and the <xref:System.EventArgs> base class.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="194c7-119">Sections connexes</span><span class="sxs-lookup"><span data-stu-id="194c7-119">Related Sections</span></span>  
 <span data-ttu-id="194c7-120">Pour plus d'informations, consultez les pages suivantes :</span><span class="sxs-lookup"><span data-stu-id="194c7-120">For more information, see:</span></span>  
  
- [<span data-ttu-id="194c7-121">Comment s’abonner à des événements et s’en désabonner</span><span class="sxs-lookup"><span data-stu-id="194c7-121">How to subscribe to and unsubscribe from events</span></span>](./how-to-subscribe-to-and-unsubscribe-from-events.md)

- [<span data-ttu-id="194c7-122">Comment publier des événements conformes aux indications du .NET Framework</span><span class="sxs-lookup"><span data-stu-id="194c7-122">How to publish events that conform to .NET Framework Guidelines</span></span>](./how-to-publish-events-that-conform-to-net-framework-guidelines.md)

- [<span data-ttu-id="194c7-123">Comment déclencher des événements de la classe de base dans les classes dérivées</span><span class="sxs-lookup"><span data-stu-id="194c7-123">How to raise base class events in derived classes</span></span>](./how-to-raise-base-class-events-in-derived-classes.md)

- [<span data-ttu-id="194c7-124">Comment implémenter des événements d’interface</span><span class="sxs-lookup"><span data-stu-id="194c7-124">How to implement interface events</span></span>](./how-to-implement-interface-events.md)

- [<span data-ttu-id="194c7-125">Comment implémenter des accesseurs d’événement personnalisés</span><span class="sxs-lookup"><span data-stu-id="194c7-125">How to implement custom event accessors</span></span>](./how-to-implement-custom-event-accessors.md)

## <a name="c-language-specification"></a><span data-ttu-id="194c7-126">Spécification du langage C#</span><span class="sxs-lookup"><span data-stu-id="194c7-126">C# Language Specification</span></span>  

<span data-ttu-id="194c7-127">Pour plus d’informations, consultez [Événements](~/_csharplang/spec/classes.md#events) dans la [Spécification du langage C#](/dotnet/csharp/language-reference/language-specification/introduction).</span><span class="sxs-lookup"><span data-stu-id="194c7-127">For more information, see [Events](~/_csharplang/spec/classes.md#events) in the [C# Language Specification](/dotnet/csharp/language-reference/language-specification/introduction).</span></span> <span data-ttu-id="194c7-128">La spécification du langage est la source de référence pour la syntaxe C# et son utilisation.</span><span class="sxs-lookup"><span data-stu-id="194c7-128">The language specification is the definitive source for C# syntax and usage.</span></span>
  
## <a name="featured-book-chapters"></a><span data-ttu-id="194c7-129">Chapitres proposés</span><span class="sxs-lookup"><span data-stu-id="194c7-129">Featured Book Chapters</span></span>  
 <span data-ttu-id="194c7-130">[Delegates, Events, and Lambda Expressions](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/ff518994%28v=orm.10%29) (Délégués, événements et expressions lambda) dans [C# 3.0 Cookbook, Third Edition: More than 250 solutions for C# 3.0 programmers](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/ff518995%28v=orm.10%29)</span><span class="sxs-lookup"><span data-stu-id="194c7-130">[Delegates, Events, and Lambda Expressions](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/ff518994%28v=orm.10%29) in [C# 3.0 Cookbook, Third Edition: More than 250 solutions for C# 3.0 programmers](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/ff518995%28v=orm.10%29)</span></span>  
  
 <span data-ttu-id="194c7-131">[Delegates and Events](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/ff652490%28v=orm.10%29) dans [Learning C# 3.0: Master the fundamentals of C# 3.0](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/ff652493%28v=orm.10%29)</span><span class="sxs-lookup"><span data-stu-id="194c7-131">[Delegates and Events](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/ff652490%28v=orm.10%29) in [Learning C# 3.0: Master the fundamentals of C# 3.0](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/ff652493%28v=orm.10%29)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="194c7-132">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="194c7-132">See also</span></span>

- <xref:System.EventHandler>
- [<span data-ttu-id="194c7-133">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="194c7-133">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="194c7-134">Délégués</span><span class="sxs-lookup"><span data-stu-id="194c7-134">Delegates</span></span>](../delegates/index.md)
- [<span data-ttu-id="194c7-135">Création de gestionnaires d’événements dans Windows Forms</span><span class="sxs-lookup"><span data-stu-id="194c7-135">Creating Event Handlers in Windows Forms</span></span>](../../../framework/winforms/creating-event-handlers-in-windows-forms.md)
