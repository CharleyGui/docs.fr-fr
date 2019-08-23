---
title: 'Procédure : Lier un ornement à un élément'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- UIElements [WPF], binding adorners to
- adorners [WPF], binding to specified UIElements
ms.assetid: b2101611-a0ee-4137-bdb8-9b3673d2e6b9
ms.openlocfilehash: e8c7eb929042bfe1455bfc9bf459fc466de5c397
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69923492"
---
# <a name="how-to-bind-an-adorner-to-an-element"></a>Procédure : Lier un ornement à un élément
Cet exemple montre comment lier par programmation un ornement à un spécifié <xref:System.Windows.UIElement>.  
  
## <a name="example"></a>Exemples  
 Pour lier un ornement à un particulier <xref:System.Windows.UIElement>, procédez comme suit:  
  
1. Appelez la `static` méthode <xref:System.Windows.Documents.AdornerLayer.GetAdornerLayer%2A> pour obtenir un <xref:System.Windows.Documents.AdornerLayer> objet pour que <xref:System.Windows.UIElement> le soit orné. <xref:System.Windows.Documents.AdornerLayer.GetAdornerLayer%2A>parcourt l’arborescence d’éléments visuels, en commençant au **UIElement**spécifié, et retourne la première couche d’ornement trouvée. (Si aucune couche d’ornement n’est trouvée, la méthode retourne Null.)  
  
2. Appelez la <xref:System.Windows.Documents.AdornerLayer.Add%2A> méthode pour lier l’ornement à l' **UIElement**cible.  
  
 L’exemple suivant lie un SimpleCircleAdorner (illustré ci-dessus) à <xref:System.Windows.Controls.TextBox> un *myTextBox*nommé.  
  
 [!code-csharp[Adorners_SimpleCircleAdorner#_AdornSingleElement](~/samples/snippets/csharp/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/CSharp/Window1.xaml.cs#_adornsingleelement)]
 [!code-vb[Adorners_SimpleCircleAdorner#_AdornSingleElement](~/samples/snippets/visualbasic/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/VisualBasic/Window1.xaml.vb#_adornsingleelement)]  
  
> [!NOTE]
> L’utilisation du [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] pour lier un ornement à un autre élément n’est pas prise en charge pour l’instant.  
  
## <a name="see-also"></a>Voir aussi

- [Vue d’ensemble des ornements](adorners-overview.md)
