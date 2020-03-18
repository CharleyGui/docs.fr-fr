---
title: 'Comment : déclencher et utiliser des événements'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- events [.NET Framework], raising
- raising events
- events [.NET Framework], samples
ms.assetid: 42afade7-3a02-4f2e-868b-95845f302f8f
ms.openlocfilehash: 256b5ae9ac2145e339136985872dfa5423aca730
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/15/2020
ms.locfileid: "73131587"
---
# <a name="how-to-raise-and-consume-events"></a><span data-ttu-id="0170a-102">Comment : déclencher et utiliser des événements</span><span class="sxs-lookup"><span data-stu-id="0170a-102">How to: Raise and Consume Events</span></span>
<span data-ttu-id="0170a-103">Les exemples de cette rubrique montrent comment utiliser des événements.</span><span class="sxs-lookup"><span data-stu-id="0170a-103">The examples in this topic show how to work with events.</span></span> <span data-ttu-id="0170a-104">Ils incluent des exemples du délégué <xref:System.EventHandler>, le délégué <xref:System.EventHandler%601> et un délégué personnalisé, pour illustrer les événements avec et sans données.</span><span class="sxs-lookup"><span data-stu-id="0170a-104">They include examples of the <xref:System.EventHandler> delegate, the <xref:System.EventHandler%601> delegate, and a custom delegate, to illustrate events with and without data.</span></span>  
  
 <span data-ttu-id="0170a-105">Les exemples utilisent les concepts décrits dans l’article [Événements](../../../docs/standard/events/index.md).</span><span class="sxs-lookup"><span data-stu-id="0170a-105">The examples use concepts described in the [Events](../../../docs/standard/events/index.md) article.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0170a-106"> Exemple</span><span class="sxs-lookup"><span data-stu-id="0170a-106">Example</span></span>  
 <span data-ttu-id="0170a-107">Le premier exemple montre comment déclencher et consommer un événement n’ayant pas de données.</span><span class="sxs-lookup"><span data-stu-id="0170a-107">The first example shows how to raise and consume an event that doesn't have data.</span></span> <span data-ttu-id="0170a-108">Il contient une classe nommée `Counter` qui possède un événement nommé `ThresholdReached`.</span><span class="sxs-lookup"><span data-stu-id="0170a-108">It contains a class named `Counter` that has an event named `ThresholdReached`.</span></span> <span data-ttu-id="0170a-109">Cet événement est déclenché lorsqu’une valeur de compteur atteint ou dépasse un seuil.</span><span class="sxs-lookup"><span data-stu-id="0170a-109">This event is raised when a counter value equals or exceeds a threshold value.</span></span> <span data-ttu-id="0170a-110">Le délégué <xref:System.EventHandler> est associé à l’événement, car aucune donnée d’événement n’est fournie.</span><span class="sxs-lookup"><span data-stu-id="0170a-110">The <xref:System.EventHandler> delegate is associated with the event, because no event data is provided.</span></span>  
  
 [!code-csharp[EventsOverview#5](../../../samples/snippets/csharp/VS_Snippets_CLR/eventsoverview/cs/programnodata.cs#5)]
 [!code-vb[EventsOverview#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/eventsoverview/vb/module1nodata.vb#5)]  
  
## <a name="example"></a><span data-ttu-id="0170a-111"> Exemple</span><span class="sxs-lookup"><span data-stu-id="0170a-111">Example</span></span>  
 <span data-ttu-id="0170a-112">L’exemple suivant montre comment déclencher et consommer un événement qui fournit des données.</span><span class="sxs-lookup"><span data-stu-id="0170a-112">The next example shows how to raise and consume an event that provides data.</span></span> <span data-ttu-id="0170a-113">Le délégué <xref:System.EventHandler%601> est associé à l’événement, et une instance d’un objet de données d’événement personnalisé est fournie.</span><span class="sxs-lookup"><span data-stu-id="0170a-113">The <xref:System.EventHandler%601> delegate is associated with the event, and an instance of a custom event data object is provided.</span></span>  
  
 [!code-cpp[EventsOverview#6](../../../samples/snippets/cpp/VS_Snippets_CLR/eventsoverview/cpp/programwithdata.cpp#6)]
 [!code-csharp[EventsOverview#6](../../../samples/snippets/csharp/VS_Snippets_CLR/eventsoverview/cs/programwithdata.cs#6)]
 [!code-vb[EventsOverview#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/eventsoverview/vb/module1withdata.vb#6)]  
  
## <a name="example"></a><span data-ttu-id="0170a-114"> Exemple</span><span class="sxs-lookup"><span data-stu-id="0170a-114">Example</span></span>  
 <span data-ttu-id="0170a-115">L'exemple suivant montre comment déclarer un délégué pour un événement.</span><span class="sxs-lookup"><span data-stu-id="0170a-115">The next example shows how to declare a delegate for an event.</span></span> <span data-ttu-id="0170a-116">Le délégué est nommé `ThresholdReachedEventHandler`.</span><span class="sxs-lookup"><span data-stu-id="0170a-116">The delegate is named `ThresholdReachedEventHandler`.</span></span> <span data-ttu-id="0170a-117">Ce n’est qu’une illustration.</span><span class="sxs-lookup"><span data-stu-id="0170a-117">This is just an illustration.</span></span> <span data-ttu-id="0170a-118">En règle générale, il est inutile de déclarer un délégué pour un événement, car vous pouvez utiliser le délégué <xref:System.EventHandler> ou le délégué <xref:System.EventHandler%601>.</span><span class="sxs-lookup"><span data-stu-id="0170a-118">Typically, you do not have to declare a delegate for an event, because you can use either the <xref:System.EventHandler> or the <xref:System.EventHandler%601> delegate.</span></span> <span data-ttu-id="0170a-119">Vous devez déclarer un délégué uniquement dans de rares cas, par exemple, pour rendre votre classe disponible pour le code hérité qui ne peut pas utiliser des classes génériques.</span><span class="sxs-lookup"><span data-stu-id="0170a-119">You should declare a delegate only in rare scenarios, such as making your class available to legacy code that cannot use generics.</span></span>  
  
 [!code-csharp[EventsOverview#7](../../../samples/snippets/csharp/VS_Snippets_CLR/eventsoverview/cs/programwithdelegate.cs#7)]
 [!code-vb[EventsOverview#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/eventsoverview/vb/module1withdelegate.vb#7)]  
  
## <a name="see-also"></a><span data-ttu-id="0170a-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="0170a-120">See also</span></span>

- [<span data-ttu-id="0170a-121">Événements</span><span class="sxs-lookup"><span data-stu-id="0170a-121">Events</span></span>](../../../docs/standard/events/index.md)
