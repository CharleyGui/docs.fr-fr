---
title: 'Comment : déclencher et utiliser des événements'
description: Déclenchez & utiliser des événements dans .NET. Consultez les exemples qui utilisent le délégué EventHandler, le <TEventArgs> délégué eventhandler & un délégué personnalisé.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- events [.NET], raising
- raising events
- events [.NET], samples
ms.assetid: 42afade7-3a02-4f2e-868b-95845f302f8f
ms.openlocfilehash: 22e62dd8e14696273923873353b1bd19d8507ab7
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95697452"
---
# <a name="how-to-raise-and-consume-events"></a>Comment : déclencher et utiliser des événements

Les exemples de cette rubrique montrent comment utiliser des événements. Ils incluent des exemples du délégué <xref:System.EventHandler>, le délégué <xref:System.EventHandler%601> et un délégué personnalisé, pour illustrer les événements avec et sans données.  
  
 Les exemples utilisent les concepts décrits dans l’article [Événements](index.md).  
  
## <a name="example"></a>Exemple  

 Le premier exemple montre comment déclencher et consommer un événement n’ayant pas de données. Il contient une classe nommée `Counter` qui possède un événement nommé `ThresholdReached`. Cet événement est déclenché lorsqu’une valeur de compteur atteint ou dépasse un seuil. Le délégué <xref:System.EventHandler> est associé à l’événement, car aucune donnée d’événement n’est fournie.  
  
 [!code-csharp[EventsOverview#5](../../../samples/snippets/csharp/VS_Snippets_CLR/eventsoverview/cs/programnodata.cs#5)]
 [!code-vb[EventsOverview#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/eventsoverview/vb/module1nodata.vb#5)]  
  
## <a name="example"></a>Exemple  

 L’exemple suivant montre comment déclencher et consommer un événement qui fournit des données. Le délégué <xref:System.EventHandler%601> est associé à l’événement, et une instance d’un objet de données d’événement personnalisé est fournie.  
  
 [!code-cpp[EventsOverview#6](../../../samples/snippets/cpp/VS_Snippets_CLR/eventsoverview/cpp/programwithdata.cpp#6)]
 [!code-csharp[EventsOverview#6](../../../samples/snippets/csharp/VS_Snippets_CLR/eventsoverview/cs/programwithdata.cs#6)]
 [!code-vb[EventsOverview#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/eventsoverview/vb/module1withdata.vb#6)]  
  
## <a name="example"></a>Exemple  

 L'exemple suivant montre comment déclarer un délégué pour un événement. Le délégué est nommé `ThresholdReachedEventHandler`. Ce n’est qu’une illustration. En règle générale, il est inutile de déclarer un délégué pour un événement, car vous pouvez utiliser le délégué <xref:System.EventHandler> ou le délégué <xref:System.EventHandler%601>. Vous devez déclarer un délégué uniquement dans de rares cas, par exemple, pour rendre votre classe disponible pour le code hérité qui ne peut pas utiliser des classes génériques.  
  
 [!code-csharp[EventsOverview#7](../../../samples/snippets/csharp/VS_Snippets_CLR/eventsoverview/cs/programwithdelegate.cs#7)]
 [!code-vb[EventsOverview#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/eventsoverview/vb/module1withdelegate.vb#7)]  
  
## <a name="see-also"></a>Voir aussi

- [Événements](index.md)
