---
title: Modèles d'événement faible
ms.date: 03/30/2017
helpviewer_keywords:
- weak event pattern implementation [WPF]
- event handlers [WPF], weak event pattern
- IWeakEventListener interface [WPF]
ms.assetid: e7c62920-4812-4811-94d8-050a65c856f6
ms.openlocfilehash: 61e7f6d29cf9275004238ca776d5af9bf027004f
ms.sourcegitcommit: 83ecdf731dc1920bca31f017b1556c917aafd7a0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/12/2019
ms.locfileid: "67859914"
---
# <a name="weak-event-patterns"></a><span data-ttu-id="fcb7e-102">Modèles d'événement faible</span><span class="sxs-lookup"><span data-stu-id="fcb7e-102">Weak Event Patterns</span></span>
<span data-ttu-id="fcb7e-103">Dans les applications, il est possible que les gestionnaires qui sont attachés à des sources d’événements ne seront pas détruits en coordination avec l’objet écouteur qui joint le gestionnaire à la source.</span><span class="sxs-lookup"><span data-stu-id="fcb7e-103">In applications, it is possible that handlers that are attached to event sources will not be destroyed in coordination with the listener object that attached the handler to the source.</span></span> <span data-ttu-id="fcb7e-104">Cette situation peut entraîner des fuites de mémoire.</span><span class="sxs-lookup"><span data-stu-id="fcb7e-104">This situation can lead to memory leaks.</span></span> [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] <span data-ttu-id="fcb7e-105">introduit un modèle de conception qui peut être utilisé pour résoudre ce problème, en fournissant une classe de gestionnaire dédiée pour des événements particuliers et en implémentant une interface sur les écouteurs de cet événement.</span><span class="sxs-lookup"><span data-stu-id="fcb7e-105">introduces a design pattern that can be used to address this issue, by providing a dedicated manager class for particular events and implementing an interface on listeners for that event.</span></span> <span data-ttu-id="fcb7e-106">Ce modèle de conception est appelé le *modèle d’événement faible*.</span><span class="sxs-lookup"><span data-stu-id="fcb7e-106">This design pattern is known as the *weak event pattern*.</span></span>  
  
## <a name="why-implement-the-weak-event-pattern"></a><span data-ttu-id="fcb7e-107">Pourquoi implémenter le modèle d’événement faible ?</span><span class="sxs-lookup"><span data-stu-id="fcb7e-107">Why Implement the Weak Event Pattern?</span></span>  
 <span data-ttu-id="fcb7e-108">Écoute des événements peut entraîner des fuites de mémoire.</span><span class="sxs-lookup"><span data-stu-id="fcb7e-108">Listening for events can lead to memory leaks.</span></span> <span data-ttu-id="fcb7e-109">La technique standard pour écouter un événement consiste à utiliser la syntaxe spécifique au langage qui attache un gestionnaire à un événement sur une source.</span><span class="sxs-lookup"><span data-stu-id="fcb7e-109">The typical technique for listening to an event is to use the language-specific syntax that attaches a handler to an event on a source.</span></span> <span data-ttu-id="fcb7e-110">Par exemple, dans C#, que la syntaxe est : `source.SomeEvent += new SomeEventHandler(MyEventHandler)`.</span><span class="sxs-lookup"><span data-stu-id="fcb7e-110">For example, in C#, that syntax is: `source.SomeEvent += new SomeEventHandler(MyEventHandler)`.</span></span>  
  
 <span data-ttu-id="fcb7e-111">Cette technique crée une référence forte à partir de la source d’événements à l’écouteur d’événements.</span><span class="sxs-lookup"><span data-stu-id="fcb7e-111">This technique creates a strong reference from the event source to the event listener.</span></span> <span data-ttu-id="fcb7e-112">En règle générale, y attacher un gestionnaire d’événements pour un écouteur de provoque l’écouteur avoir une durée de vie d’objet qui est influencée par la durée de vie de la source (à moins que le Gestionnaire d’événements est supprimé explicitement).</span><span class="sxs-lookup"><span data-stu-id="fcb7e-112">Ordinarily, attaching an event handler for a listener causes the listener to have an object lifetime that is influenced by the object lifetime of the source (unless the event handler is explicitly removed).</span></span> <span data-ttu-id="fcb7e-113">Toutefois, dans certaines circonstances, vous pouvez la durée de vie de l’écouteur à être contrôlé par d’autres facteurs, tels que si elle appartient actuellement à l’arborescence visuelle de l’application et non par la durée de vie de la source.</span><span class="sxs-lookup"><span data-stu-id="fcb7e-113">But in certain circumstances, you might want the object lifetime of the listener to be controlled by other factors, such as whether it currently belongs to the visual tree of the application, and not by the lifetime of the source.</span></span> <span data-ttu-id="fcb7e-114">Chaque fois que la durée de vie source s’étend au-delà de la durée de vie de l’écouteur, le modèle d’événement normal entraîne une fuite de mémoire : l’écouteur est maintenu actif plus longtemps que prévu.</span><span class="sxs-lookup"><span data-stu-id="fcb7e-114">Whenever the source object lifetime extends beyond the object lifetime of the listener, the normal event pattern leads to a memory leak: the listener is kept alive longer than intended.</span></span>  
  
 <span data-ttu-id="fcb7e-115">Le modèle d’événement faible est conçu pour résoudre ce problème de fuite de mémoire.</span><span class="sxs-lookup"><span data-stu-id="fcb7e-115">The weak event pattern is designed to solve this memory leak problem.</span></span> <span data-ttu-id="fcb7e-116">Le modèle d’événement faible peut être utilisé chaque fois qu’un écouteur doit s’inscrire à un événement, mais l’écouteur ne sait pas explicitement quand annuler l’inscription.</span><span class="sxs-lookup"><span data-stu-id="fcb7e-116">The weak event pattern can be used whenever a listener needs to register for an event, but the listener does not explicitly know when to unregister.</span></span> <span data-ttu-id="fcb7e-117">Le modèle d’événement faible peut également servir à chaque fois que la durée de vie de la source dépasse la durée de vie utile de l’écouteur.</span><span class="sxs-lookup"><span data-stu-id="fcb7e-117">The weak event pattern can also be used whenever the object lifetime of the source exceeds the useful object lifetime of the listener.</span></span> <span data-ttu-id="fcb7e-118">(Dans ce cas, *utile* est déterminée par vous.) Le modèle d’événement faible permet à l’écouteur pour vous inscrire et recevoir l’événement sans affecter les caractéristiques de durée de vie d’objet de l’écouteur en aucune façon.</span><span class="sxs-lookup"><span data-stu-id="fcb7e-118">(In this case, *useful* is determined by you.) The weak event pattern allows the listener to register for and receive the event without affecting the object lifetime characteristics of the listener in any way.</span></span> <span data-ttu-id="fcb7e-119">En effet, la référence implicite à partir de la source ne détermine pas si l’écouteur est éligible pour le garbage collection.</span><span class="sxs-lookup"><span data-stu-id="fcb7e-119">In effect, the implied reference from the source does not determine whether the listener is eligible for garbage collection.</span></span> <span data-ttu-id="fcb7e-120">La référence est une référence faible, d'où le nom du modèle d’événement faible et les API connexes.</span><span class="sxs-lookup"><span data-stu-id="fcb7e-120">The reference is a weak reference, thus the naming of the weak event pattern and the related APIs.</span></span> <span data-ttu-id="fcb7e-121">L’écouteur peut être le garbage collector ou détruit, et la source peut continuer sans conserver des références de gestionnaire non-collectable à un objet détruit.</span><span class="sxs-lookup"><span data-stu-id="fcb7e-121">The listener can be garbage collected or otherwise destroyed, and the source can continue without retaining noncollectible handler references to a now destroyed object.</span></span>  
  
## <a name="who-should-implement-the-weak-event-pattern"></a><span data-ttu-id="fcb7e-122">Qui doit implémenter le modèle d’événement faible ?</span><span class="sxs-lookup"><span data-stu-id="fcb7e-122">Who Should Implement the Weak Event Pattern?</span></span>  
 <span data-ttu-id="fcb7e-123">L’implémentation du modèle d’événement faible est intéressante principalement pour les auteurs de contrôles.</span><span class="sxs-lookup"><span data-stu-id="fcb7e-123">Implementing the weak event pattern is interesting primarily for control authors.</span></span> <span data-ttu-id="fcb7e-124">En tant qu’auteur de contrôle, il vous incombe en grande partie pour le comportement et la relation contenant-contenu de votre contrôle et l’impact sur les applications dans lequel elle est insérée.</span><span class="sxs-lookup"><span data-stu-id="fcb7e-124">As a control author, you are largely responsible for the behavior and containment of your control and the impact it has on applications in which it is inserted.</span></span> <span data-ttu-id="fcb7e-125">Cela inclut le comportement de durée de vie l’objet contrôle, notamment la gestion du problème de fuite de mémoire décrit.</span><span class="sxs-lookup"><span data-stu-id="fcb7e-125">This includes the control object lifetime behavior, in particular the handling of the described memory leak problem.</span></span>  
  
 <span data-ttu-id="fcb7e-126">Certains scénarios, par nature, se prêtent à l’application du modèle d’événement faible.</span><span class="sxs-lookup"><span data-stu-id="fcb7e-126">Certain scenarios inherently lend themselves to the application of the weak event pattern.</span></span> <span data-ttu-id="fcb7e-127">Un tel scénario est la liaison de données.</span><span class="sxs-lookup"><span data-stu-id="fcb7e-127">One such scenario is data binding.</span></span> <span data-ttu-id="fcb7e-128">Dans la liaison de données, il est courant de l’objet source soit complètement indépendante de l’objet de l’écouteur, qui est une cible d’une liaison.</span><span class="sxs-lookup"><span data-stu-id="fcb7e-128">In data binding, it is common for the source object to be completely independent of the listener object, which is a target of a binding.</span></span> <span data-ttu-id="fcb7e-129">De nombreuses tâches associées [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] déjà une liaison de données ont le modèle d’événement faible appliqué dans la façon dont les événements sont implémentées.</span><span class="sxs-lookup"><span data-stu-id="fcb7e-129">Many aspects of [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] data binding already have the weak event pattern applied in how the events are implemented.</span></span>  
  
## <a name="how-to-implement-the-weak-event-pattern"></a><span data-ttu-id="fcb7e-130">Comment implémenter le modèle d’événement faible</span><span class="sxs-lookup"><span data-stu-id="fcb7e-130">How to Implement the Weak Event Pattern</span></span>  
 <span data-ttu-id="fcb7e-131">Il existe trois façons d’implémenter le modèle d’événement faible.</span><span class="sxs-lookup"><span data-stu-id="fcb7e-131">There are three ways to implement weak event pattern.</span></span> <span data-ttu-id="fcb7e-132">Le tableau suivant répertorie les trois approches et fournit quelques conseils pour l’utilisation de chacun.</span><span class="sxs-lookup"><span data-stu-id="fcb7e-132">The following table lists the three approaches and provides some guidance for when you should use each.</span></span>  
  
|<span data-ttu-id="fcb7e-133">Approche</span><span class="sxs-lookup"><span data-stu-id="fcb7e-133">Approach</span></span>|<span data-ttu-id="fcb7e-134">Moment auquel implémenter</span><span class="sxs-lookup"><span data-stu-id="fcb7e-134">When to Implement</span></span>|  
|--------------|-----------------------|  
|<span data-ttu-id="fcb7e-135">Utiliser une classe de gestionnaire d’événement faible existante</span><span class="sxs-lookup"><span data-stu-id="fcb7e-135">Use an existing weak event manager class</span></span>|<span data-ttu-id="fcb7e-136">Si l’événement que vous voulez vous abonner correspond un <xref:System.Windows.WeakEventManager>, utilisez le Gestionnaire d’événement faible existant.</span><span class="sxs-lookup"><span data-stu-id="fcb7e-136">If the event you want to subscribe to has a corresponding <xref:System.Windows.WeakEventManager>, use the existing weak event manager.</span></span> <span data-ttu-id="fcb7e-137">Pour obtenir la liste des gestionnaires d’événements faible qui sont inclus avec WPF, consultez la hiérarchie d’héritage dans le <xref:System.Windows.WeakEventManager> classe.</span><span class="sxs-lookup"><span data-stu-id="fcb7e-137">For a list of weak event managers that are included with WPF, see the inheritance hierarchy in the <xref:System.Windows.WeakEventManager> class.</span></span> <span data-ttu-id="fcb7e-138">Étant donné que les gestionnaires d’événements faible inclus sont limitées, vous devrez probablement choisir l’une des autres approches.</span><span class="sxs-lookup"><span data-stu-id="fcb7e-138">Because the included weak event managers are limited, you will probably need to choose one of the other approaches.</span></span>|  
|<span data-ttu-id="fcb7e-139">Utiliser une classe de gestionnaire d’événement faible générique</span><span class="sxs-lookup"><span data-stu-id="fcb7e-139">Use a generic weak event manager class</span></span>|<span data-ttu-id="fcb7e-140">Utiliser un générique <xref:System.Windows.WeakEventManager%602> lorsque existant <xref:System.Windows.WeakEventManager> est non disponible, vous cherchez un moyen simple d’implémenter, et vous ne le sont pas concernées par l’efficacité.</span><span class="sxs-lookup"><span data-stu-id="fcb7e-140">Use a generic <xref:System.Windows.WeakEventManager%602> when an existing <xref:System.Windows.WeakEventManager> is not available, you want an easy way to implement, and you are not concerned about efficiency.</span></span> <span data-ttu-id="fcb7e-141">Le modèle générique <xref:System.Windows.WeakEventManager%602> est moins efficace que d’un gestionnaire d’événements faibles existantes ou personnalisées.</span><span class="sxs-lookup"><span data-stu-id="fcb7e-141">The generic <xref:System.Windows.WeakEventManager%602> is less efficient than an existing or custom weak event manager.</span></span> <span data-ttu-id="fcb7e-142">Par exemple, la classe générique fait plus de réflexion pour découvrir l’événement étant donné le nom de l’événement.</span><span class="sxs-lookup"><span data-stu-id="fcb7e-142">For example, the generic class does more reflection to discover the event given the event's name.</span></span> <span data-ttu-id="fcb7e-143">En outre, le code pour inscrire l’événement à l’aide du modèle générique <xref:System.Windows.WeakEventManager%602> est plus longue que d’utiliser un existant ou personnalisé <xref:System.Windows.WeakEventManager>.</span><span class="sxs-lookup"><span data-stu-id="fcb7e-143">Also, the code to register the event by using the generic <xref:System.Windows.WeakEventManager%602> is more verbose than using an existing or custom <xref:System.Windows.WeakEventManager>.</span></span>|  
|<span data-ttu-id="fcb7e-144">Créer une classe de gestionnaire d’événement faible personnalisé</span><span class="sxs-lookup"><span data-stu-id="fcb7e-144">Create a custom weak event manager class</span></span>|<span data-ttu-id="fcb7e-145">Créer un personnalisé <xref:System.Windows.WeakEventManager> lorsque existant <xref:System.Windows.WeakEventManager> n’est pas disponible et que vous souhaitez plus d’efficacité.</span><span class="sxs-lookup"><span data-stu-id="fcb7e-145">Create a custom <xref:System.Windows.WeakEventManager> when an existing <xref:System.Windows.WeakEventManager> is not available and you want the best efficiency.</span></span> <span data-ttu-id="fcb7e-146">L’aide d’un <xref:System.Windows.WeakEventManager> pour vous abonner à un événement sera plus efficace, mais vous n’entraînent pas le coût de l’écriture de code plus au début.</span><span class="sxs-lookup"><span data-stu-id="fcb7e-146">Using a custom <xref:System.Windows.WeakEventManager> to subscribe to an event will be more efficient, but you do incur the cost of writing more code at the beginning.</span></span>|  
|<span data-ttu-id="fcb7e-147">Utiliser un gestionnaire d’événements faibles de tiers</span><span class="sxs-lookup"><span data-stu-id="fcb7e-147">Use a third-party weak event manager</span></span>|<span data-ttu-id="fcb7e-148">NuGet a [plusieurs gestionnaires d’événements faible](https://www.nuget.org/packages?q=weak+event+manager&prerel=false) et de nombreuses infrastructures WPF prennent également en charge le modèle (par exemple, consultez [documentation de Prism sur l’abonnement aux événements faiblement couplés](https://github.com/PrismLibrary/Prism-Documentation/blob/master/docs/wpf/Communication.md#subscribing-to-events)).</span><span class="sxs-lookup"><span data-stu-id="fcb7e-148">NuGet has [several weak event managers](https://www.nuget.org/packages?q=weak+event+manager&prerel=false) and many WPF frameworks also support the pattern (for instance, see [Prism's documentation on loosely coupled event subscription](https://github.com/PrismLibrary/Prism-Documentation/blob/master/docs/wpf/Communication.md#subscribing-to-events)).</span></span>|

 <span data-ttu-id="fcb7e-149">Les sections suivantes décrivent comment implémenter le modèle d’événement faible.</span><span class="sxs-lookup"><span data-stu-id="fcb7e-149">The following sections describe how to implement the weak event pattern.</span></span>  <span data-ttu-id="fcb7e-150">Pour les besoins de cette discussion, l’événement pour vous abonner à présente les caractéristiques suivantes.</span><span class="sxs-lookup"><span data-stu-id="fcb7e-150">For purposes of this discussion, the event to subscribe to has the following characteristics.</span></span>  
  
- <span data-ttu-id="fcb7e-151">Le nom de l’événement est `SomeEvent`.</span><span class="sxs-lookup"><span data-stu-id="fcb7e-151">The event name is `SomeEvent`.</span></span>  
  
- <span data-ttu-id="fcb7e-152">L’événement est déclenché par la `EventSource` classe.</span><span class="sxs-lookup"><span data-stu-id="fcb7e-152">The event is raised by the `EventSource` class.</span></span>  
  
- <span data-ttu-id="fcb7e-153">Le Gestionnaire d’événements a le type : `SomeEventEventHandler` (ou `EventHandler<SomeEventEventArgs>`).</span><span class="sxs-lookup"><span data-stu-id="fcb7e-153">The event handler has type: `SomeEventEventHandler` (or `EventHandler<SomeEventEventArgs>`).</span></span>  
  
- <span data-ttu-id="fcb7e-154">L’événement passe un paramètre de type `SomeEventEventArgs` aux gestionnaires d’événements.</span><span class="sxs-lookup"><span data-stu-id="fcb7e-154">The event passes a parameter of type `SomeEventEventArgs` to the event handlers.</span></span>  
  
### <a name="using-an-existing-weak-event-manager-class"></a><span data-ttu-id="fcb7e-155">À l’aide d’une classe de gestionnaire d’événements faible existante</span><span class="sxs-lookup"><span data-stu-id="fcb7e-155">Using an Existing Weak Event Manager Class</span></span>  
  
1. <span data-ttu-id="fcb7e-156">Recherchez un événement existant de faible manager.</span><span class="sxs-lookup"><span data-stu-id="fcb7e-156">Find an existing weak event manager.</span></span>  
  
     <span data-ttu-id="fcb7e-157">Pour obtenir la liste des gestionnaires d’événements faible qui sont inclus avec WPF, consultez la hiérarchie d’héritage dans le <xref:System.Windows.WeakEventManager> classe.</span><span class="sxs-lookup"><span data-stu-id="fcb7e-157">For a list of weak event managers that are included with WPF, see the inheritance hierarchy in the <xref:System.Windows.WeakEventManager> class.</span></span>  
  
2. <span data-ttu-id="fcb7e-158">Utilisez le nouveau gestionnaire d’événements faible au lieu de la connexion d’événements normal.</span><span class="sxs-lookup"><span data-stu-id="fcb7e-158">Use the new weak event manager instead of the normal event hookup.</span></span>  
  
     <span data-ttu-id="fcb7e-159">Par exemple, si votre code utilise le modèle suivant pour vous abonner à un événement :</span><span class="sxs-lookup"><span data-stu-id="fcb7e-159">For example, if your code uses the following pattern to subscribe to an event:</span></span>  
  
    ```  
    source.SomeEvent += new SomeEventEventHandler(OnSomeEvent);  
    ```  
  
     <span data-ttu-id="fcb7e-160">Modifier le modèle suivant :</span><span class="sxs-lookup"><span data-stu-id="fcb7e-160">Change it to the following pattern:</span></span>  
  
    ```  
    SomeEventWeakEventManager.AddHandler(source, OnSomeEvent);  
    ```  
  
     <span data-ttu-id="fcb7e-161">De même, si votre code utilise le modèle suivant pour vous désabonner d’un événement :</span><span class="sxs-lookup"><span data-stu-id="fcb7e-161">Similarly, if your code uses the following pattern to unsubscribe from an event:</span></span>  
  
    ```  
    source.SomeEvent -= new SomeEventEventHandler(OnSomeEvent);  
    ```  
  
     <span data-ttu-id="fcb7e-162">Modifier le modèle suivant :</span><span class="sxs-lookup"><span data-stu-id="fcb7e-162">Change it to the following pattern:</span></span>  
  
    ```  
    SomeEventWeakEventManager.RemoveHandler(source, OnSomeEvent);  
    ```  
  
### <a name="using-the-generic-weak-event-manager-class"></a><span data-ttu-id="fcb7e-163">À l’aide de la classe de gestionnaire d’événements faible générique</span><span class="sxs-lookup"><span data-stu-id="fcb7e-163">Using the Generic Weak Event Manager Class</span></span>  
  
1. <span data-ttu-id="fcb7e-164">Utiliser le modèle générique <xref:System.Windows.WeakEventManager%602> classe au lieu de la connexion d’événements normal.</span><span class="sxs-lookup"><span data-stu-id="fcb7e-164">Use the generic <xref:System.Windows.WeakEventManager%602> class instead of the normal event hookup.</span></span>  
  
     <span data-ttu-id="fcb7e-165">Lorsque vous utilisez <xref:System.Windows.WeakEventManager%602> pour inscrire les écouteurs d’événements, vous fournissez la source d’événements et <xref:System.EventArgs> type que les paramètres de type pour la classe et appelez <xref:System.Windows.WeakEventManager%602.AddHandler%2A> comme indiqué dans le code suivant :</span><span class="sxs-lookup"><span data-stu-id="fcb7e-165">When you use <xref:System.Windows.WeakEventManager%602> to register event listeners, you supply the event source and <xref:System.EventArgs> type as the type parameters to the class and call <xref:System.Windows.WeakEventManager%602.AddHandler%2A> as shown in the following code:</span></span>  
  
    ```  
    WeakEventManager<EventSource, SomeEventEventArgs>.AddHandler(source, "SomeEvent", source_SomeEvent);  
    ```  
  
### <a name="creating-a-custom-weak-event-manager-class"></a><span data-ttu-id="fcb7e-166">Création d’une classe de gestionnaire d’événements faible personnalisée</span><span class="sxs-lookup"><span data-stu-id="fcb7e-166">Creating a Custom Weak Event Manager Class</span></span>  
  
1. <span data-ttu-id="fcb7e-167">Copiez le modèle de classe suivant à votre projet.</span><span class="sxs-lookup"><span data-stu-id="fcb7e-167">Copy the following class template to your project.</span></span>  
  
     <span data-ttu-id="fcb7e-168">Cette classe hérite de la <xref:System.Windows.WeakEventManager> classe.</span><span class="sxs-lookup"><span data-stu-id="fcb7e-168">This class inherits from the <xref:System.Windows.WeakEventManager> class.</span></span>  
  
     [!code-csharp[WeakEvents#WeakEventManagerTemplate](~/samples/snippets/csharp/VS_Snippets_Wpf/WeakEvents/CSharp/WeakEventManagerTemplate.cs#weakeventmanagertemplate)]  
  
2. <span data-ttu-id="fcb7e-169">Remplacez le `SomeEventWeakEventManager` nom avec votre propre nom.</span><span class="sxs-lookup"><span data-stu-id="fcb7e-169">Replace the `SomeEventWeakEventManager` name with your own name.</span></span>  
  
3. <span data-ttu-id="fcb7e-170">Remplacez les trois noms décrits précédemment avec les noms correspondants pour votre événement.</span><span class="sxs-lookup"><span data-stu-id="fcb7e-170">Replace the three names described previously with the corresponding names for your event.</span></span> <span data-ttu-id="fcb7e-171">(`SomeEvent`, `EventSource`, et `SomeEventEventArgs`)</span><span class="sxs-lookup"><span data-stu-id="fcb7e-171">(`SomeEvent`, `EventSource`, and `SomeEventEventArgs`)</span></span>  
  
4. <span data-ttu-id="fcb7e-172">Définir la visibilité (publique / interne / privée) de la classe de gestionnaire d’événements faible pour la même visibilité que les événements qu’il gère.</span><span class="sxs-lookup"><span data-stu-id="fcb7e-172">Set the visibility (public / internal / private) of the weak event manager class to the same visibility as event it manages.</span></span>  
  
5. <span data-ttu-id="fcb7e-173">Utilisez le nouveau gestionnaire d’événements faible au lieu de la connexion d’événements normal.</span><span class="sxs-lookup"><span data-stu-id="fcb7e-173">Use the new weak event manager instead of the normal event hookup.</span></span>  
  
     <span data-ttu-id="fcb7e-174">Par exemple, si votre code utilise le modèle suivant pour vous abonner à un événement :</span><span class="sxs-lookup"><span data-stu-id="fcb7e-174">For example, if your code uses the following pattern to subscribe to an event:</span></span>  
  
    ```  
    source.SomeEvent += new SomeEventEventHandler(OnSomeEvent);  
    ```  
  
     <span data-ttu-id="fcb7e-175">Modifier le modèle suivant :</span><span class="sxs-lookup"><span data-stu-id="fcb7e-175">Change it to the following pattern:</span></span>  
  
    ```  
    SomeEventWeakEventManager.AddHandler(source, OnSomeEvent);  
    ```  
  
     <span data-ttu-id="fcb7e-176">De même, si votre code utilise le modèle suivant pour annuler l’abonnement à un événement :</span><span class="sxs-lookup"><span data-stu-id="fcb7e-176">Similarly, if your code uses the following pattern to unsubscribe to an event:</span></span>  
  
    ```  
    source.SomeEvent -= new SomeEventEventHandler(OnSome);  
    ```  
  
     <span data-ttu-id="fcb7e-177">Modifier le modèle suivant :</span><span class="sxs-lookup"><span data-stu-id="fcb7e-177">Change it to the following pattern:</span></span>  
  
    ```  
    SomeEventWeakEventManager.RemoveHandler(source, OnSomeEvent);  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="fcb7e-178">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="fcb7e-178">See also</span></span>

- <xref:System.Windows.WeakEventManager>
- <xref:System.Windows.IWeakEventListener>
- [<span data-ttu-id="fcb7e-179">Vue d’ensemble des événements routés</span><span class="sxs-lookup"><span data-stu-id="fcb7e-179">Routed Events Overview</span></span>](routed-events-overview.md)
- [<span data-ttu-id="fcb7e-180">Vue d’ensemble de la liaison de données</span><span class="sxs-lookup"><span data-stu-id="fcb7e-180">Data Binding Overview</span></span>](../data/data-binding-overview.md)
