---
title: "Comment : gérer plusieurs événements à l'aide des propriétés d'événements"
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- event properties [.NET Framework]
- multiple events [.NET Framework]
- event handling [.NET Framework], with multiple events
- events [.NET Framework], multiple
ms.assetid: 30047cba-e2fd-41c6-b9ca-2ad7a49003db
ms.openlocfilehash: c5be541c1a40c5d16a0502e76adef24f6a41cc89
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84288470"
---
# <a name="how-to-handle-multiple-events-using-event-properties"></a><span data-ttu-id="1dcf4-102">Comment : gérer plusieurs événements à l'aide des propriétés d'événements</span><span class="sxs-lookup"><span data-stu-id="1dcf4-102">How to: Handle Multiple Events Using Event Properties</span></span>
<span data-ttu-id="1dcf4-103">Pour utiliser des propriétés d'événements, définissez les propriétés d'événements dans la classe qui déclenche les événements, puis affectez les délégués pour les propriétés d'événements dans les classes qui gèrent les événements.</span><span class="sxs-lookup"><span data-stu-id="1dcf4-103">To use event properties, you define the event properties in the class that raises the events, and then set the delegates for the event properties in classes that handle the events.</span></span> <span data-ttu-id="1dcf4-104">Pour implémenter plusieurs propriétés d'événements dans une classe, la classe doit stocker et maintenir le délégué défini pour chaque événement en interne.</span><span class="sxs-lookup"><span data-stu-id="1dcf4-104">To implement multiple event properties in a class, the class must internally store and maintain the delegate defined for each event.</span></span> <span data-ttu-id="1dcf4-105">Une approche courante consiste à implémenter une collection de délégués indexée par une clé d’événement.</span><span class="sxs-lookup"><span data-stu-id="1dcf4-105">A typical approach is to implement a delegate collection that is indexed by an event key.</span></span>  
  
 <span data-ttu-id="1dcf4-106">Pour stocker les délégués pour chaque événement, vous pouvez utiliser la classe <xref:System.ComponentModel.EventHandlerList> ou implémenter votre propre collection.</span><span class="sxs-lookup"><span data-stu-id="1dcf4-106">To store the delegates for each event, you can use the <xref:System.ComponentModel.EventHandlerList> class, or implement your own collection.</span></span> <span data-ttu-id="1dcf4-107">La classe de collection doit fournir des méthodes pour le paramétrage, l’accès et la récupération du délégué de gestionnaire d’événements selon la clé d’événement.</span><span class="sxs-lookup"><span data-stu-id="1dcf4-107">The collection class must provide methods for setting, accessing, and retrieving the event handler delegate based on the event key.</span></span> <span data-ttu-id="1dcf4-108">Par exemple, vous pouvez utiliser une classe <xref:System.Collections.Hashtable> ou dériver une classe personnalisée de la classe <xref:System.Collections.DictionaryBase>.</span><span class="sxs-lookup"><span data-stu-id="1dcf4-108">For example, you could use a <xref:System.Collections.Hashtable> class, or derive a custom class from the <xref:System.Collections.DictionaryBase> class.</span></span> <span data-ttu-id="1dcf4-109">Les détails de l’implémentation de la collection de délégués ne doivent pas être exposés à l’extérieur de votre classe.</span><span class="sxs-lookup"><span data-stu-id="1dcf4-109">The implementation details of the delegate collection do not need to be exposed outside your class.</span></span>  
  
 <span data-ttu-id="1dcf4-110">Chaque propriété d'événement dans la classe définit une méthode d'accesseur add et une méthode d'accesseur remove.</span><span class="sxs-lookup"><span data-stu-id="1dcf4-110">Each event property within the class defines an add accessor method and a remove accessor method.</span></span> <span data-ttu-id="1dcf4-111">L'accesseur add pour une propriété d'événement ajoute l'instance de délégué d'entrée à la collection de délégués.</span><span class="sxs-lookup"><span data-stu-id="1dcf4-111">The add accessor for an event property adds the input delegate instance to the delegate collection.</span></span> <span data-ttu-id="1dcf4-112">L'accesseur remove pour une propriété d'événement supprime l'instance de délégué d'entrée de la collection de délégués.</span><span class="sxs-lookup"><span data-stu-id="1dcf4-112">The remove accessor for an event property removes the input delegate instance from the delegate collection.</span></span> <span data-ttu-id="1dcf4-113">Les accesseurs de propriété d'événement utilisent la clé prédéfinie pour la propriété d'événement pour ajouter et supprimer des instances de la collection de délégués.</span><span class="sxs-lookup"><span data-stu-id="1dcf4-113">The event property accessors use the predefined key for the event property to add and remove instances from the delegate collection.</span></span>  
  
### <a name="to-handle-multiple-events-using-event-properties"></a><span data-ttu-id="1dcf4-114">Pour gérer plusieurs événements à l'aide de propriétés d'événements</span><span class="sxs-lookup"><span data-stu-id="1dcf4-114">To handle multiple events using event properties</span></span>  
  
1. <span data-ttu-id="1dcf4-115">Définissez une collection de délégués dans la classe qui déclenche les événements.</span><span class="sxs-lookup"><span data-stu-id="1dcf4-115">Define a delegate collection within the class that raises the events.</span></span>  
  
2. <span data-ttu-id="1dcf4-116">Définissez une clé pour chaque événement.</span><span class="sxs-lookup"><span data-stu-id="1dcf4-116">Define a key for each event.</span></span>  
  
3. <span data-ttu-id="1dcf4-117">Définissez les propriétés d'événements dans la classe qui déclenche les événements.</span><span class="sxs-lookup"><span data-stu-id="1dcf4-117">Define the event properties in the class that raises the events.</span></span>  
  
4. <span data-ttu-id="1dcf4-118">Utilisez la collection de délégués pour implémenter les méthodes d'accesseur add et remove pour les propriétés d'événements.</span><span class="sxs-lookup"><span data-stu-id="1dcf4-118">Use the delegate collection to implement the add and remove accessor methods for the event properties.</span></span>  
  
5. <span data-ttu-id="1dcf4-119">Utilisez les propriétés d'événements publiques pour ajouter et supprimer des délégués de gestionnaire d'événements dans les classes qui gèrent les événements.</span><span class="sxs-lookup"><span data-stu-id="1dcf4-119">Use the public event properties to add and remove event handler delegates in the classes that handle the events.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1dcf4-120">Exemple</span><span class="sxs-lookup"><span data-stu-id="1dcf4-120">Example</span></span>  
 <span data-ttu-id="1dcf4-121">L'exemple C# suivant implémente les propriétés d'événements `MouseDown` et `MouseUp`, à l'aide d'un <xref:System.ComponentModel.EventHandlerList> pour stocker le délégué de chaque événement.</span><span class="sxs-lookup"><span data-stu-id="1dcf4-121">The following C# example implements the event properties `MouseDown` and `MouseUp`, using an <xref:System.ComponentModel.EventHandlerList> to store each event's delegate.</span></span> <span data-ttu-id="1dcf4-122">Les mots clés des constructions des propriétés d'événements sont en gras.</span><span class="sxs-lookup"><span data-stu-id="1dcf4-122">The keywords of the event property constructs are in bold type.</span></span>  
  
 [!code-cpp[Conceptual.Events.Other#31](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.events.other/cpp/example3.cpp#31)]
 [!code-csharp[Conceptual.Events.Other#31](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.events.other/cs/example3.cs#31)]
 [!code-vb[Conceptual.Events.Other#31](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.events.other/vb/example3.vb#31)]  
  
## <a name="see-also"></a><span data-ttu-id="1dcf4-123">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="1dcf4-123">See also</span></span>

- <xref:System.ComponentModel.EventHandlerList?displayProperty=nameWithType>
- [<span data-ttu-id="1dcf4-124">Événements</span><span class="sxs-lookup"><span data-stu-id="1dcf4-124">Events</span></span>](index.md)
- <xref:System.Web.UI.Control.Events%2A?displayProperty=nameWithType>
- [<span data-ttu-id="1dcf4-125">Comment : déclarer des événements personnalisés pour économiser la mémoire</span><span class="sxs-lookup"><span data-stu-id="1dcf4-125">How to: Declare Custom Events To Conserve Memory</span></span>](../../visual-basic/programming-guide/language-features/events/how-to-declare-custom-events-to-conserve-memory.md)
