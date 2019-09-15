---
title: Modèles d'événement faible
ms.date: 03/30/2017
helpviewer_keywords:
- weak event pattern implementation [WPF]
- event handlers [WPF], weak event pattern
- IWeakEventListener interface [WPF]
ms.assetid: e7c62920-4812-4811-94d8-050a65c856f6
ms.openlocfilehash: f4cbb22a3cdd7b966c36f6c8246b13b5c58e056d
ms.sourcegitcommit: 005980b14629dfc193ff6cdc040800bc75e0a5a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/14/2019
ms.locfileid: "70991785"
---
# <a name="weak-event-patterns"></a><span data-ttu-id="979df-102">Modèles d'événement faible</span><span class="sxs-lookup"><span data-stu-id="979df-102">Weak Event Patterns</span></span>
<span data-ttu-id="979df-103">Dans les applications, il est possible que les gestionnaires qui sont attachés à des sources d’événements ne soient pas détruits avec l’objet d’écouteur qui a attaché le gestionnaire à la source.</span><span class="sxs-lookup"><span data-stu-id="979df-103">In applications, it is possible that handlers that are attached to event sources will not be destroyed in coordination with the listener object that attached the handler to the source.</span></span> <span data-ttu-id="979df-104">Cette situation peut entraîner des fuites de mémoire.</span><span class="sxs-lookup"><span data-stu-id="979df-104">This situation can lead to memory leaks.</span></span> [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]<span data-ttu-id="979df-105">introduit un modèle de conception qui peut être utilisé pour résoudre ce problème, en fournissant une classe de gestionnaire dédiée pour des événements particuliers et en implémentant une interface sur les écouteurs de cet événement.</span><span class="sxs-lookup"><span data-stu-id="979df-105">introduces a design pattern that can be used to address this issue, by providing a dedicated manager class for particular events and implementing an interface on listeners for that event.</span></span> <span data-ttu-id="979df-106">Ce modèle de conception est connu sous le nom de *modèle d’événement faible*.</span><span class="sxs-lookup"><span data-stu-id="979df-106">This design pattern is known as the *weak event pattern*.</span></span>  
  
## <a name="why-implement-the-weak-event-pattern"></a><span data-ttu-id="979df-107">Pourquoi implémenter le modèle d’événement faible ?</span><span class="sxs-lookup"><span data-stu-id="979df-107">Why Implement the Weak Event Pattern?</span></span>  
 <span data-ttu-id="979df-108">L’écoute des événements peut entraîner des fuites de mémoire.</span><span class="sxs-lookup"><span data-stu-id="979df-108">Listening for events can lead to memory leaks.</span></span> <span data-ttu-id="979df-109">La technique classique pour écouter un événement consiste à utiliser la syntaxe spécifique au langage qui attache un gestionnaire à un événement sur une source.</span><span class="sxs-lookup"><span data-stu-id="979df-109">The typical technique for listening to an event is to use the language-specific syntax that attaches a handler to an event on a source.</span></span> <span data-ttu-id="979df-110">Par exemple, dans C#, cette syntaxe est : `source.SomeEvent += new SomeEventHandler(MyEventHandler)`.</span><span class="sxs-lookup"><span data-stu-id="979df-110">For example, in C#, that syntax is: `source.SomeEvent += new SomeEventHandler(MyEventHandler)`.</span></span>  
  
 <span data-ttu-id="979df-111">Cette technique crée une référence forte de la source de l’événement à l’écouteur d’événements.</span><span class="sxs-lookup"><span data-stu-id="979df-111">This technique creates a strong reference from the event source to the event listener.</span></span> <span data-ttu-id="979df-112">En règle générale, l’attachement d’un gestionnaire d’événements pour un écouteur amène l’écouteur à avoir une durée de vie d’objet influencée par la durée de vie de l’objet de la source (sauf si le gestionnaire d’événements est supprimé explicitement).</span><span class="sxs-lookup"><span data-stu-id="979df-112">Ordinarily, attaching an event handler for a listener causes the listener to have an object lifetime that is influenced by the object lifetime of the source (unless the event handler is explicitly removed).</span></span> <span data-ttu-id="979df-113">Toutefois, dans certaines circonstances, vous souhaiterez peut-être que la durée de vie des objets de l’écouteur soit contrôlée par d’autres facteurs, par exemple s’il appartient actuellement à l’arborescence d’éléments visuels de l’application, et non par la durée de vie de la source.</span><span class="sxs-lookup"><span data-stu-id="979df-113">But in certain circumstances, you might want the object lifetime of the listener to be controlled by other factors, such as whether it currently belongs to the visual tree of the application, and not by the lifetime of the source.</span></span> <span data-ttu-id="979df-114">Chaque fois que la durée de vie de l’objet source s’étend au-delà de la durée de vie des objets de l’écouteur, le modèle d’événement normal entraîne une fuite de mémoire : l’écouteur reste actif plus longtemps que prévu.</span><span class="sxs-lookup"><span data-stu-id="979df-114">Whenever the source object lifetime extends beyond the object lifetime of the listener, the normal event pattern leads to a memory leak: the listener is kept alive longer than intended.</span></span>  
  
 <span data-ttu-id="979df-115">Le modèle d’événement faible est conçu pour résoudre ce problème de fuite de mémoire.</span><span class="sxs-lookup"><span data-stu-id="979df-115">The weak event pattern is designed to solve this memory leak problem.</span></span> <span data-ttu-id="979df-116">Le modèle d’événement faible peut être utilisé chaque fois qu’un écouteur doit s’inscrire pour un événement, mais l’écouteur ne sait pas explicitement quand annuler l’inscription.</span><span class="sxs-lookup"><span data-stu-id="979df-116">The weak event pattern can be used whenever a listener needs to register for an event, but the listener does not explicitly know when to unregister.</span></span> <span data-ttu-id="979df-117">Le modèle d’événement faible peut également être utilisé chaque fois que la durée de vie d’objet de la source dépasse la durée de vie d’objet utile de l’écouteur.</span><span class="sxs-lookup"><span data-stu-id="979df-117">The weak event pattern can also be used whenever the object lifetime of the source exceeds the useful object lifetime of the listener.</span></span> <span data-ttu-id="979df-118">(Dans ce cas, *utile* est déterminé par vous.) Le modèle d’événement faible permet à l’écouteur de s’inscrire pour recevoir l’événement sans affecter les caractéristiques de durée de vie des objets de l’écouteur de quelque manière que ce soit.</span><span class="sxs-lookup"><span data-stu-id="979df-118">(In this case, *useful* is determined by you.) The weak event pattern allows the listener to register for and receive the event without affecting the object lifetime characteristics of the listener in any way.</span></span> <span data-ttu-id="979df-119">En effet, la référence implicite de la source ne détermine pas si l’écouteur est éligible pour garbage collection.</span><span class="sxs-lookup"><span data-stu-id="979df-119">In effect, the implied reference from the source does not determine whether the listener is eligible for garbage collection.</span></span> <span data-ttu-id="979df-120">La référence est une référence faible, donc la dénomination du modèle d’événement faible et les API associées.</span><span class="sxs-lookup"><span data-stu-id="979df-120">The reference is a weak reference, thus the naming of the weak event pattern and the related APIs.</span></span> <span data-ttu-id="979df-121">L’écouteur peut être récupéré par le garbage collector ou détruit, et la source peut continuer sans conserver les références de gestionnaire non collectées à un objet désormais détruit.</span><span class="sxs-lookup"><span data-stu-id="979df-121">The listener can be garbage collected or otherwise destroyed, and the source can continue without retaining noncollectible handler references to a now destroyed object.</span></span>  
  
## <a name="who-should-implement-the-weak-event-pattern"></a><span data-ttu-id="979df-122">Qui doit implémenter le modèle d’événement faible ?</span><span class="sxs-lookup"><span data-stu-id="979df-122">Who Should Implement the Weak Event Pattern?</span></span>  
 <span data-ttu-id="979df-123">L’implémentation du modèle d’événement faible est particulièrement intéressante pour les auteurs de contrôle.</span><span class="sxs-lookup"><span data-stu-id="979df-123">Implementing the weak event pattern is interesting primarily for control authors.</span></span> <span data-ttu-id="979df-124">En tant qu’auteur de contrôle, vous êtes en grande partie responsable du comportement et de la relation contenant-contenu de votre contrôle, ainsi que de l’impact qu’il a sur les applications dans lesquelles il est inséré.</span><span class="sxs-lookup"><span data-stu-id="979df-124">As a control author, you are largely responsible for the behavior and containment of your control and the impact it has on applications in which it is inserted.</span></span> <span data-ttu-id="979df-125">Cela comprend le comportement de durée de vie des objets de contrôle, en particulier la gestion du problème de fuite de mémoire décrit.</span><span class="sxs-lookup"><span data-stu-id="979df-125">This includes the control object lifetime behavior, in particular the handling of the described memory leak problem.</span></span>  
  
 <span data-ttu-id="979df-126">Certains scénarios se prêtent par nature à l’application du modèle d’événement faible.</span><span class="sxs-lookup"><span data-stu-id="979df-126">Certain scenarios inherently lend themselves to the application of the weak event pattern.</span></span> <span data-ttu-id="979df-127">La liaison de données est un scénario de ce type.</span><span class="sxs-lookup"><span data-stu-id="979df-127">One such scenario is data binding.</span></span> <span data-ttu-id="979df-128">Dans la liaison de données, il est courant que l’objet source soit complètement indépendant de l’objet d’écouteur, qui est la cible d’une liaison.</span><span class="sxs-lookup"><span data-stu-id="979df-128">In data binding, it is common for the source object to be completely independent of the listener object, which is a target of a binding.</span></span> <span data-ttu-id="979df-129">De nombreux aspects [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] de la liaison de données ont déjà le modèle d’événement faible qui est appliqué dans la manière dont les événements sont implémentés.</span><span class="sxs-lookup"><span data-stu-id="979df-129">Many aspects of [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] data binding already have the weak event pattern applied in how the events are implemented.</span></span>  
  
## <a name="how-to-implement-the-weak-event-pattern"></a><span data-ttu-id="979df-130">Comment implémenter le modèle d’événement faible</span><span class="sxs-lookup"><span data-stu-id="979df-130">How to Implement the Weak Event Pattern</span></span>  
 <span data-ttu-id="979df-131">Il existe trois façons d’implémenter un modèle d’événement faible.</span><span class="sxs-lookup"><span data-stu-id="979df-131">There are three ways to implement weak event pattern.</span></span> <span data-ttu-id="979df-132">Le tableau suivant répertorie les trois approches et fournit des conseils sur l’utilisation de chacune d’elles.</span><span class="sxs-lookup"><span data-stu-id="979df-132">The following table lists the three approaches and provides some guidance for when you should use each.</span></span>  
  
|<span data-ttu-id="979df-133">Approche</span><span class="sxs-lookup"><span data-stu-id="979df-133">Approach</span></span>|<span data-ttu-id="979df-134">Quand implémenter</span><span class="sxs-lookup"><span data-stu-id="979df-134">When to Implement</span></span>|  
|--------------|-----------------------|  
|<span data-ttu-id="979df-135">Utiliser une classe de gestionnaire d’événements faible existante</span><span class="sxs-lookup"><span data-stu-id="979df-135">Use an existing weak event manager class</span></span>|<span data-ttu-id="979df-136">Si l’événement auquel vous souhaitez vous abonner a un <xref:System.Windows.WeakEventManager>correspondant, utilisez le gestionnaire d’événements faible existant.</span><span class="sxs-lookup"><span data-stu-id="979df-136">If the event you want to subscribe to has a corresponding <xref:System.Windows.WeakEventManager>, use the existing weak event manager.</span></span> <span data-ttu-id="979df-137">Pour obtenir la liste des gestionnaires d’événements faibles inclus dans WPF, consultez la hiérarchie d’héritage dans <xref:System.Windows.WeakEventManager> la classe.</span><span class="sxs-lookup"><span data-stu-id="979df-137">For a list of weak event managers that are included with WPF, see the inheritance hierarchy in the <xref:System.Windows.WeakEventManager> class.</span></span> <span data-ttu-id="979df-138">Étant donné que les gestionnaires d’événements faibles inclus sont limités, vous devrez probablement choisir l’une des autres approches.</span><span class="sxs-lookup"><span data-stu-id="979df-138">Because the included weak event managers are limited, you will probably need to choose one of the other approaches.</span></span>|  
|<span data-ttu-id="979df-139">Utiliser une classe de gestionnaire d’événements faible générique</span><span class="sxs-lookup"><span data-stu-id="979df-139">Use a generic weak event manager class</span></span>|<span data-ttu-id="979df-140">Utilisez un générique <xref:System.Windows.WeakEventManager%602> lorsqu’un existant <xref:System.Windows.WeakEventManager> n’est pas disponible, vous avez besoin d’un moyen simple d’implémenter et vous ne vous inquiétez pas de l’efficacité.</span><span class="sxs-lookup"><span data-stu-id="979df-140">Use a generic <xref:System.Windows.WeakEventManager%602> when an existing <xref:System.Windows.WeakEventManager> is not available, you want an easy way to implement, and you are not concerned about efficiency.</span></span> <span data-ttu-id="979df-141">Le générique <xref:System.Windows.WeakEventManager%602> est moins efficace qu’un gestionnaire d’événements faible existant ou personnalisé.</span><span class="sxs-lookup"><span data-stu-id="979df-141">The generic <xref:System.Windows.WeakEventManager%602> is less efficient than an existing or custom weak event manager.</span></span> <span data-ttu-id="979df-142">Par exemple, la classe générique fait plus de réflexion pour découvrir l’événement en fonction du nom de l’événement.</span><span class="sxs-lookup"><span data-stu-id="979df-142">For example, the generic class does more reflection to discover the event given the event's name.</span></span> <span data-ttu-id="979df-143">En outre, le code permettant d’enregistrer l’événement à l' <xref:System.Windows.WeakEventManager%602> aide du générique est plus détaillé que l’utilisation d' <xref:System.Windows.WeakEventManager>un existant ou d’un personnalisé.</span><span class="sxs-lookup"><span data-stu-id="979df-143">Also, the code to register the event by using the generic <xref:System.Windows.WeakEventManager%602> is more verbose than using an existing or custom <xref:System.Windows.WeakEventManager>.</span></span>|  
|<span data-ttu-id="979df-144">Créer une classe de gestionnaire d’événements faibles personnalisée</span><span class="sxs-lookup"><span data-stu-id="979df-144">Create a custom weak event manager class</span></span>|<span data-ttu-id="979df-145">Créez un personnalisé <xref:System.Windows.WeakEventManager> lorsqu’un existant <xref:System.Windows.WeakEventManager> n’est pas disponible et que vous souhaitez obtenir une efficacité optimale.</span><span class="sxs-lookup"><span data-stu-id="979df-145">Create a custom <xref:System.Windows.WeakEventManager> when an existing <xref:System.Windows.WeakEventManager> is not available and you want the best efficiency.</span></span> <span data-ttu-id="979df-146">L’utilisation d' <xref:System.Windows.WeakEventManager> un personnalisé pour s’abonner à un événement est plus efficace, mais vous encourez le coût de l’écriture de code supplémentaire au début.</span><span class="sxs-lookup"><span data-stu-id="979df-146">Using a custom <xref:System.Windows.WeakEventManager> to subscribe to an event will be more efficient, but you do incur the cost of writing more code at the beginning.</span></span>|  
|<span data-ttu-id="979df-147">Utiliser un gestionnaire d’événements faibles tiers</span><span class="sxs-lookup"><span data-stu-id="979df-147">Use a third-party weak event manager</span></span>|<span data-ttu-id="979df-148">NuGet possède [plusieurs gestionnaires d’événements faibles](https://www.nuget.org/packages?q=weak+event+manager&prerel=false) et de nombreuses infrastructures WPF prennent également en charge le modèle (par exemple, consultez la [documentation de Prism sur l’abonnement aux événements faiblement couplés](https://github.com/PrismLibrary/Prism-Documentation/blob/master/docs/wpf/Communication.md#subscribing-to-events)).</span><span class="sxs-lookup"><span data-stu-id="979df-148">NuGet has [several weak event managers](https://www.nuget.org/packages?q=weak+event+manager&prerel=false) and many WPF frameworks also support the pattern (for instance, see [Prism's documentation on loosely coupled event subscription](https://github.com/PrismLibrary/Prism-Documentation/blob/master/docs/wpf/Communication.md#subscribing-to-events)).</span></span>|

 <span data-ttu-id="979df-149">Les sections suivantes décrivent comment implémenter le modèle d’événement faible.</span><span class="sxs-lookup"><span data-stu-id="979df-149">The following sections describe how to implement the weak event pattern.</span></span>  <span data-ttu-id="979df-150">Dans le cadre de cette discussion, l’événement auquel s’abonner a les caractéristiques suivantes.</span><span class="sxs-lookup"><span data-stu-id="979df-150">For purposes of this discussion, the event to subscribe to has the following characteristics.</span></span>  
  
- <span data-ttu-id="979df-151">Le nom de l' `SomeEvent`événement est.</span><span class="sxs-lookup"><span data-stu-id="979df-151">The event name is `SomeEvent`.</span></span>  
  
- <span data-ttu-id="979df-152">L’événement est déclenché par la `EventSource` classe.</span><span class="sxs-lookup"><span data-stu-id="979df-152">The event is raised by the `EventSource` class.</span></span>  
  
- <span data-ttu-id="979df-153">Le gestionnaire d’événements a le `SomeEventEventHandler` type : `EventHandler<SomeEventEventArgs>`(ou).</span><span class="sxs-lookup"><span data-stu-id="979df-153">The event handler has type: `SomeEventEventHandler` (or `EventHandler<SomeEventEventArgs>`).</span></span>  
  
- <span data-ttu-id="979df-154">L’événement passe un paramètre de type `SomeEventEventArgs` aux gestionnaires d’événements.</span><span class="sxs-lookup"><span data-stu-id="979df-154">The event passes a parameter of type `SomeEventEventArgs` to the event handlers.</span></span>  
  
### <a name="using-an-existing-weak-event-manager-class"></a><span data-ttu-id="979df-155">Utilisation d’une classe de gestionnaire d’événements faible existante</span><span class="sxs-lookup"><span data-stu-id="979df-155">Using an Existing Weak Event Manager Class</span></span>  
  
1. <span data-ttu-id="979df-156">Recherchez un gestionnaire d’événements faible existant.</span><span class="sxs-lookup"><span data-stu-id="979df-156">Find an existing weak event manager.</span></span>  
  
     <span data-ttu-id="979df-157">Pour obtenir la liste des gestionnaires d’événements faibles inclus dans WPF, consultez la hiérarchie d’héritage dans <xref:System.Windows.WeakEventManager> la classe.</span><span class="sxs-lookup"><span data-stu-id="979df-157">For a list of weak event managers that are included with WPF, see the inheritance hierarchy in the <xref:System.Windows.WeakEventManager> class.</span></span>  
  
2. <span data-ttu-id="979df-158">Utilisez le nouveau gestionnaire d’événements faible plutôt que le raccordement d’événement normal.</span><span class="sxs-lookup"><span data-stu-id="979df-158">Use the new weak event manager instead of the normal event hookup.</span></span>  
  
     <span data-ttu-id="979df-159">Par exemple, si votre code utilise le modèle suivant pour s’abonner à un événement :</span><span class="sxs-lookup"><span data-stu-id="979df-159">For example, if your code uses the following pattern to subscribe to an event:</span></span>  
  
    ```csharp  
    source.SomeEvent += new SomeEventEventHandler(OnSomeEvent);  
    ```  
  
     <span data-ttu-id="979df-160">Remplacez-le par le modèle suivant :</span><span class="sxs-lookup"><span data-stu-id="979df-160">Change it to the following pattern:</span></span>  
  
    ```csharp  
    SomeEventWeakEventManager.AddHandler(source, OnSomeEvent);  
    ```  
  
     <span data-ttu-id="979df-161">De même, si votre code utilise le modèle suivant pour se désabonner d’un événement :</span><span class="sxs-lookup"><span data-stu-id="979df-161">Similarly, if your code uses the following pattern to unsubscribe from an event:</span></span>  
  
    ```csharp  
    source.SomeEvent -= new SomeEventEventHandler(OnSomeEvent);  
    ```  
  
     <span data-ttu-id="979df-162">Remplacez-le par le modèle suivant :</span><span class="sxs-lookup"><span data-stu-id="979df-162">Change it to the following pattern:</span></span>  
  
    ```csharp  
    SomeEventWeakEventManager.RemoveHandler(source, OnSomeEvent);  
    ```  
  
### <a name="using-the-generic-weak-event-manager-class"></a><span data-ttu-id="979df-163">Utilisation de la classe de gestionnaire d’événements faible générique</span><span class="sxs-lookup"><span data-stu-id="979df-163">Using the Generic Weak Event Manager Class</span></span>  
  
1. <span data-ttu-id="979df-164">Utilisez la classe <xref:System.Windows.WeakEventManager%602> générique à la place de l’événement de raccordement normal.</span><span class="sxs-lookup"><span data-stu-id="979df-164">Use the generic <xref:System.Windows.WeakEventManager%602> class instead of the normal event hookup.</span></span>  
  
     <span data-ttu-id="979df-165">Quand vous utilisez <xref:System.Windows.WeakEventManager%602> pour inscrire des écouteurs d’événements, vous fournissez la source <xref:System.EventArgs> et le type de l’événement en tant que paramètres <xref:System.Windows.WeakEventManager%602.AddHandler%2A> de type à la classe et appelez comme indiqué dans le code suivant :</span><span class="sxs-lookup"><span data-stu-id="979df-165">When you use <xref:System.Windows.WeakEventManager%602> to register event listeners, you supply the event source and <xref:System.EventArgs> type as the type parameters to the class and call <xref:System.Windows.WeakEventManager%602.AddHandler%2A> as shown in the following code:</span></span>  
  
    ```csharp  
    WeakEventManager<EventSource, SomeEventEventArgs>.AddHandler(source, "SomeEvent", source_SomeEvent);  
    ```  
  
### <a name="creating-a-custom-weak-event-manager-class"></a><span data-ttu-id="979df-166">Création d’une classe de gestionnaire d’événements faibles personnalisée</span><span class="sxs-lookup"><span data-stu-id="979df-166">Creating a Custom Weak Event Manager Class</span></span>  
  
1. <span data-ttu-id="979df-167">Copiez le modèle de classe suivant dans votre projet.</span><span class="sxs-lookup"><span data-stu-id="979df-167">Copy the following class template to your project.</span></span>  
  
     <span data-ttu-id="979df-168">Cette classe hérite de la <xref:System.Windows.WeakEventManager> classe.</span><span class="sxs-lookup"><span data-stu-id="979df-168">This class inherits from the <xref:System.Windows.WeakEventManager> class.</span></span>  
  
     [!code-csharp[WeakEvents#WeakEventManagerTemplate](~/samples/snippets/csharp/VS_Snippets_Wpf/WeakEvents/CSharp/WeakEventManagerTemplate.cs#weakeventmanagertemplate)]  
  
2. <span data-ttu-id="979df-169">Remplacez le `SomeEventWeakEventManager` nom par votre propre nom.</span><span class="sxs-lookup"><span data-stu-id="979df-169">Replace the `SomeEventWeakEventManager` name with your own name.</span></span>  
  
3. <span data-ttu-id="979df-170">Remplacez les trois noms décrits précédemment par les noms correspondants pour votre événement.</span><span class="sxs-lookup"><span data-stu-id="979df-170">Replace the three names described previously with the corresponding names for your event.</span></span> <span data-ttu-id="979df-171">(`SomeEvent`, `EventSource`et )`SomeEventEventArgs`</span><span class="sxs-lookup"><span data-stu-id="979df-171">(`SomeEvent`, `EventSource`, and `SomeEventEventArgs`)</span></span>  
  
4. <span data-ttu-id="979df-172">Affectez à la visibilité (publique/interne/privée) de la classe de gestionnaire d’événements faible la même visibilité que l’événement qu’elle gère.</span><span class="sxs-lookup"><span data-stu-id="979df-172">Set the visibility (public / internal / private) of the weak event manager class to the same visibility as event it manages.</span></span>  
  
5. <span data-ttu-id="979df-173">Utilisez le nouveau gestionnaire d’événements faible plutôt que le raccordement d’événement normal.</span><span class="sxs-lookup"><span data-stu-id="979df-173">Use the new weak event manager instead of the normal event hookup.</span></span>  
  
     <span data-ttu-id="979df-174">Par exemple, si votre code utilise le modèle suivant pour s’abonner à un événement :</span><span class="sxs-lookup"><span data-stu-id="979df-174">For example, if your code uses the following pattern to subscribe to an event:</span></span>  
  
    ```csharp  
    source.SomeEvent += new SomeEventEventHandler(OnSomeEvent);  
    ```  
  
     <span data-ttu-id="979df-175">Remplacez-le par le modèle suivant :</span><span class="sxs-lookup"><span data-stu-id="979df-175">Change it to the following pattern:</span></span>  
  
    ```csharp  
    SomeEventWeakEventManager.AddHandler(source, OnSomeEvent);  
    ```  
  
     <span data-ttu-id="979df-176">De même, si votre code utilise le modèle suivant pour annuler l’abonnement à un événement :</span><span class="sxs-lookup"><span data-stu-id="979df-176">Similarly, if your code uses the following pattern to unsubscribe to an event:</span></span>  
  
    ```csharp  
    source.SomeEvent -= new SomeEventEventHandler(OnSome);  
    ```  
  
     <span data-ttu-id="979df-177">Remplacez-le par le modèle suivant :</span><span class="sxs-lookup"><span data-stu-id="979df-177">Change it to the following pattern:</span></span>  
  
    ```csharp  
    SomeEventWeakEventManager.RemoveHandler(source, OnSomeEvent);  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="979df-178">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="979df-178">See also</span></span>

- <xref:System.Windows.WeakEventManager>
- <xref:System.Windows.IWeakEventListener>
- [<span data-ttu-id="979df-179">Vue d’ensemble des événements routés</span><span class="sxs-lookup"><span data-stu-id="979df-179">Routed Events Overview</span></span>](routed-events-overview.md)
- [<span data-ttu-id="979df-180">Vue d’ensemble de la liaison de données</span><span class="sxs-lookup"><span data-stu-id="979df-180">Data Binding Overview</span></span>](../data/data-binding-overview.md)
