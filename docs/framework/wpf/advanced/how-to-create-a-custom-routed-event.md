---
title: 'Procédure : Créer un événement routé personnalisé'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- routed events [WPF], creating
- events [WPF], routing
ms.assetid: b79f459a-1c3f-4045-b2d4-1659cc8eaa3c
ms.openlocfilehash: cbfb88af4e35e3f090248982bb14d6b7a3a03cef
ms.sourcegitcommit: 24a4a8eb6d8cfe7b8549fb6d823076d7c697e0c6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/23/2019
ms.locfileid: "68401465"
---
# <a name="how-to-create-a-custom-routed-event"></a>Procédure : Créer un événement routé personnalisé
Pour que votre événement personnalisé prenne en charge le routage d’événements, <xref:System.Windows.RoutedEvent> vous devez <xref:System.Windows.EventManager.RegisterRoutedEvent%2A> inscrire un à l’aide de la méthode. Cet exemple montre les principes de base de la création d’un événement routé personnalisé.  
  
## <a name="example"></a>Exemple  
 Comme indiqué dans l’exemple suivant, vous devez d’abord <xref:System.Windows.RoutedEvent> inscrire un <xref:System.Windows.EventManager.RegisterRoutedEvent%2A> à l’aide de la méthode. Par Convention, le <xref:System.Windows.RoutedEvent> nom de champ statique doit se terminer par l' ***événement***de suffixe. Dans cet exemple, le nom de l’événement est `Tap` et la stratégie de routage de l’événement <xref:System.Windows.RoutingStrategy.Bubble>est. Après l’appel d’inscription, vous pouvez fournir des accesseurs d’événement common language runtime (CLR) d’ajout et de suppression pour l’événement.  
  
 Notez que, même si l’événement est déclenché au moyen de la méthode virtuelle `OnTap` dans cet exemple, la manière dont vous déclenchez votre événement ou dont votre événement répond aux modifications dépend de vos besoins.  
  
 Notez également que cet exemple implémente fondamentalement une sous-classe entière <xref:System.Windows.Controls.Button>de; cette sous-classe est générée comme un assembly distinct, puis instanciée en tant que classe [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] personnalisée sur une page distincte. Pour illustrer le concept, les contrôles sous-classés peuvent être insérés dans des arborescences composées d’autres contrôles. Dans cette situation, les événements personnalisés de ces contrôles ont exactement les mêmes fonctionnalités de routage d’événement que tout élément [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] natif.  
  
 [!code-csharp[RoutedEventCustom#CustomClass](~/samples/snippets/csharp/VS_Snippets_Wpf/RoutedEventCustom/CSharp/SDKSampleLibrary/class1.cs#customclass)]
 [!code-vb[RoutedEventCustom#CustomClass](~/samples/snippets/visualbasic/VS_Snippets_Wpf/RoutedEventCustom/VB/SDKSampleLibrary/Class1.vb#customclass)]  
  
 [!code-xaml[RoutedEventCustom#Page](~/samples/snippets/csharp/VS_Snippets_Wpf/RoutedEventCustom/CSharp/RoutedEventCustomApp/default.xaml#page)]  
  
 Les événements de tunneling sont créés de la même façon <xref:System.Windows.RoutedEvent.RoutingStrategy%2A> , mais <xref:System.Windows.RoutingStrategy.Tunnel> avec la valeur dans l’appel d’inscription. Par convention, les événements de tunneling dans [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] sont précédés du préfixe « Preview ».  
  
 Pour voir un exemple du fonctionnement des événements de propagation, consultez [Guide pratique pour gérer un événement routé](how-to-handle-a-routed-event.md).  
  
## <a name="see-also"></a>Voir aussi

- [Vue d’ensemble des événements routés](routed-events-overview.md)
- [Vue d’ensemble des entrées](input-overview.md)
- [Vue d’ensemble de la création de contrôles](../controls/control-authoring-overview.md)
