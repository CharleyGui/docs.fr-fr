---
title: "Comment : gérer plusieurs événements à l'aide des propriétés d'événements"
description: Découvrez comment gérer de nombreux événements à l’aide des propriétés d’événement. Définir des collections déléguées, des clés d’événement & des propriétés d’événement. Implémentez les méthodes d’accesseur Add & Remove.
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
ms.openlocfilehash: 5b528aa2145ba703ce605ce22ae7d643f1e5b8d0
ms.sourcegitcommit: 5fd4696a3e5791b2a8c449ccffda87f2cc2d4894
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2020
ms.locfileid: "84769013"
---
# <a name="how-to-handle-multiple-events-using-event-properties"></a>Comment : gérer plusieurs événements à l'aide des propriétés d'événements
Pour utiliser des propriétés d'événements, définissez les propriétés d'événements dans la classe qui déclenche les événements, puis affectez les délégués pour les propriétés d'événements dans les classes qui gèrent les événements. Pour implémenter plusieurs propriétés d'événements dans une classe, la classe doit stocker et maintenir le délégué défini pour chaque événement en interne. Une approche courante consiste à implémenter une collection de délégués indexée par une clé d’événement.  
  
 Pour stocker les délégués pour chaque événement, vous pouvez utiliser la classe <xref:System.ComponentModel.EventHandlerList> ou implémenter votre propre collection. La classe de collection doit fournir des méthodes pour le paramétrage, l’accès et la récupération du délégué de gestionnaire d’événements selon la clé d’événement. Par exemple, vous pouvez utiliser une classe <xref:System.Collections.Hashtable> ou dériver une classe personnalisée de la classe <xref:System.Collections.DictionaryBase>. Les détails de l’implémentation de la collection de délégués ne doivent pas être exposés à l’extérieur de votre classe.  
  
 Chaque propriété d'événement dans la classe définit une méthode d'accesseur add et une méthode d'accesseur remove. L'accesseur add pour une propriété d'événement ajoute l'instance de délégué d'entrée à la collection de délégués. L'accesseur remove pour une propriété d'événement supprime l'instance de délégué d'entrée de la collection de délégués. Les accesseurs de propriété d'événement utilisent la clé prédéfinie pour la propriété d'événement pour ajouter et supprimer des instances de la collection de délégués.  
  
### <a name="to-handle-multiple-events-using-event-properties"></a>Pour gérer plusieurs événements à l'aide de propriétés d'événements  
  
1. Définissez une collection de délégués dans la classe qui déclenche les événements.  
  
2. Définissez une clé pour chaque événement.  
  
3. Définissez les propriétés d'événements dans la classe qui déclenche les événements.  
  
4. Utilisez la collection de délégués pour implémenter les méthodes d'accesseur add et remove pour les propriétés d'événements.  
  
5. Utilisez les propriétés d'événements publiques pour ajouter et supprimer des délégués de gestionnaire d'événements dans les classes qui gèrent les événements.  
  
## <a name="example"></a>Exemple  
 L'exemple C# suivant implémente les propriétés d'événements `MouseDown` et `MouseUp`, à l'aide d'un <xref:System.ComponentModel.EventHandlerList> pour stocker le délégué de chaque événement. Les mots clés des constructions des propriétés d'événements sont en gras.  
  
 [!code-cpp[Conceptual.Events.Other#31](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.events.other/cpp/example3.cpp#31)]
 [!code-csharp[Conceptual.Events.Other#31](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.events.other/cs/example3.cs#31)]
 [!code-vb[Conceptual.Events.Other#31](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.events.other/vb/example3.vb#31)]  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.ComponentModel.EventHandlerList?displayProperty=nameWithType>
- [Événements](index.md)
- <xref:System.Web.UI.Control.Events%2A?displayProperty=nameWithType>
- [Comment : déclarer des événements personnalisés pour économiser la mémoire](../../visual-basic/programming-guide/language-features/events/how-to-declare-custom-events-to-conserve-memory.md)
