---
title: 'Comment : spécifier une position de menu contextuel personnalisée'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Popup control [WPF], specifying custom position
ms.assetid: 28c24f39-d3aa-4ee2-b950-384b4a5dab92
ms.openlocfilehash: b48dedc044b418062642af5c5bb40afab78a3c97
ms.sourcegitcommit: 1c1a1f9ec0bd1efb3040d86a79f7ee94e207cca5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/03/2020
ms.locfileid: "80635749"
---
# <a name="how-to-specify-a-custom-popup-position"></a>Comment : spécifier une position de menu contextuel personnalisée
Cet exemple montre comment spécifier une position personnalisée pour un <xref:System.Windows.Controls.Primitives.Popup> contrôle lorsque la <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> propriété est réglée à <xref:System.Windows.Controls.Primitives.PlacementMode.Custom>.  
  
## <a name="example"></a>Exemple  
 Lorsque <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> la propriété <xref:System.Windows.Controls.Primitives.PlacementMode.Custom>est <xref:System.Windows.Controls.Primitives.Popup> réglée à , <xref:System.Windows.Controls.Primitives.CustomPopupPlacementCallback> les appels d’une instance définie du délégué. Ce délégué retourne un ensemble de points possibles qui sont par rapport au coin supérieur <xref:System.Windows.Controls.Primitives.Popup>gauche de la zone cible et le coin supérieur gauche de la . Le <xref:System.Windows.Controls.Primitives.Popup> placement se produit au point qui offre la meilleure visibilité.  
  
 L’exemple suivant montre comment définir <xref:System.Windows.Controls.Primitives.Popup> la <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> position <xref:System.Windows.Controls.Primitives.PlacementMode.Custom>d’un en fixant la propriété à . Il montre également comment créer <xref:System.Windows.Controls.Primitives.CustomPopupPlacementCallback> et attribuer un <xref:System.Windows.Controls.Primitives.Popup>délégué afin de positionner le .  Le délégué de <xref:System.Windows.Controls.Primitives.CustomPopupPlacement> rappel renvoie deux objets.  Si <xref:System.Windows.Controls.Primitives.Popup> le est caché par un bord <xref:System.Windows.Controls.Primitives.Popup> d’écran à la première position, le est placé à la deuxième position.  
  
 [!code-xaml[PopupCustomPlacement#CustomPlacement](~/samples/snippets/csharp/VS_Snippets_Wpf/PopupCustomPlacement/CSharp/Window1.xaml#customplacement)]  
  
 [!code-csharp[PopupCustomPlacement#DelegateInstance](~/samples/snippets/csharp/VS_Snippets_Wpf/PopupCustomPlacement/CSharp/Window1.xaml.cs#delegateinstance)]
 [!code-vb[PopupCustomPlacement#DelegateInstance](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PopupCustomPlacement/visualbasic/window1.xaml.vb#delegateinstance)]  
  
 [!code-csharp[PopupCustomPlacement#DelegateDefinition](~/samples/snippets/csharp/VS_Snippets_Wpf/PopupCustomPlacement/CSharp/Window1.xaml.cs#delegatedefinition)]
 [!code-vb[PopupCustomPlacement#DelegateDefinition](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PopupCustomPlacement/visualbasic/window1.xaml.vb#delegatedefinition)]  
  
 Pour l’échantillon complet, voir [Popup Placement Sample](https://github.com/dotnet/docs/tree/master/samples/snippets/csharp/VS_Snippets_Wpf/PopupPositionSnippet/CS).  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Controls.Primitives.Popup>
- [Aperçu popup](popup-overview.md)
- [Articles comment faire](popup-how-to-topics.md)
