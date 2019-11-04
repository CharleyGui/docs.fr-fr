---
title: "Comment : ajouter un gestionnaire d'événements à l'aide de code"
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- event handlers [WPF], adding
- XAML [WPF], adding event handlers
ms.assetid: 269c61e0-6bd9-4291-9bed-1c5ee66da486
ms.openlocfilehash: 457b8cf5c68096b20df7fe39f1cc3f40358f34d0
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/03/2019
ms.locfileid: "73460430"
---
# <a name="how-to-add-an-event-handler-using-code"></a>Comment : ajouter un gestionnaire d'événements à l'aide de code
Cet exemple montre comment ajouter un gestionnaire d’événements à un élément à l’aide de code.  
  
 Si vous souhaitez ajouter un gestionnaire d’événements à un élément [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] et que la page de balisage qui contient l’élément a déjà été chargée, vous devez ajouter le gestionnaire à l’aide du code. Si vous développez l’arborescence d’éléments pour une application entièrement à l’aide de code sans déclarer d’éléments à l’aide de [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], vous pouvez également appeler des méthodes spécifiques pour ajouter des gestionnaires d’événements à l’arborescence d’éléments construite.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant ajoute une nouvelle <xref:System.Windows.Controls.Button> à une page existante définie initialement dans [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]. Un fichier code-behind implémente une méthode de gestionnaire d’événements, puis ajoute cette méthode en tant que nouveau gestionnaire d’événements sur le <xref:System.Windows.Controls.Button>.  
  
 L' C# exemple utilise l’opérateur `+=` pour assigner un gestionnaire à un événement. Il s’agit du même opérateur que celui utilisé pour assigner un gestionnaire dans le modèle de gestion des événements common language runtime (CLR). Microsoft Visual Basic ne prend pas en charge cet opérateur comme un moyen d’ajouter des gestionnaires d’événements. Au lieu de cela, elle nécessite l’une des deux techniques suivantes :  
  
- Utilisez la méthode <xref:System.Windows.UIElement.AddHandler%2A>, ainsi qu’un opérateur `AddressOf`, pour référencer l’implémentation du gestionnaire d’événements.  
  
- Utilisez le mot clé `Handles` dans le cadre de la définition du gestionnaire d’événements. Cette technique n’est pas illustrée ici ; consultez [Visual Basic et gestion des événements WPF](visual-basic-and-wpf-event-handling.md).  
  
 [!code-xaml[RoutedEventAddRemoveHandler#XAML](~/samples/snippets/csharp/VS_Snippets_Wpf/RoutedEventAddRemoveHandler/CSharp/default.xaml#xaml)]  
  
 [!code-csharp[RoutedEventAddRemoveHandler#Handler](~/samples/snippets/csharp/VS_Snippets_Wpf/RoutedEventAddRemoveHandler/CSharp/default.xaml.cs#handler)]
 [!code-vb[RoutedEventAddRemoveHandler#Handler](~/samples/snippets/visualbasic/VS_Snippets_Wpf/RoutedEventAddRemoveHandler/VisualBasic/default.xaml.vb#handler)]  
  
> [!NOTE]
> L’ajout d’un gestionnaire d’événements dans la page de [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] initialement analysée est bien plus simple. Dans l’élément objet où vous souhaitez ajouter le gestionnaire d’événements, ajoutez un attribut qui correspond au nom de l’événement que vous souhaitez gérer. Spécifiez ensuite la valeur de cet attribut comme nom de la méthode de gestionnaire d’événements que vous avez définie dans le fichier code-behind de la page de [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]. Pour plus d’informations, consultez vue d’ensemble [du langage XAML (WPF)](../../../desktop-wpf/fundamentals/xaml.md) ou [vue d’ensemble des événements routés](routed-events-overview.md).  
  
## <a name="see-also"></a>Voir aussi

- [Vue d’ensemble des événements routés](routed-events-overview.md)
- [Rubriques de guide pratique](events-how-to-topics.md)
