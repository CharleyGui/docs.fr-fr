---
title: 'Procédure : Orner les enfants d’un panneau'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- adorners [WPF], binding to children of Panels
- Panel control [WPF], binding adorners to children
ms.assetid: 4cc9b972-b472-4e5c-bdf3-3702d7fbb1f5
ms.openlocfilehash: 739ccaa0273e66c4650c35217a1156d64336dbbb
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69923527"
---
# <a name="how-to-adorn-the-children-of-a-panel"></a>Procédure : Orner les enfants d’un panneau
Cet exemple montre comment lier par programmation un ornement aux enfants d’un spécifié <xref:System.Windows.Controls.Panel>.  
  
## <a name="example"></a>Exemple  
 Pour lier un ornement aux enfants d’un <xref:System.Windows.Controls.Panel>, procédez comme suit:  
  
1. Déclarez un <xref:System.Windows.Documents.AdornerLayer> nouvel objet et appelez `static` la <xref:System.Windows.Documents.AdornerLayer.GetAdornerLayer%2A> méthode pour rechercher une couche d’ornement pour l’élément dont les enfants doivent être ornés.  
  
2. Énumérez les enfants de l’élément parent et appelez la <xref:System.Windows.Documents.AdornerLayer.Add%2A> méthode pour lier un ornement à chaque élément enfant.  
  
 L’exemple suivant lie un SimpleCircleAdorner (illustré ci-dessus) aux enfants d’un <xref:System.Windows.Controls.StackPanel> *myStackPanel*nommé.  
  
 [!code-csharp[Adorners_SimpleCircleAdorner#_AdornChildren](~/samples/snippets/csharp/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/CSharp/Window1.xaml.cs#_adornchildren)]
 [!code-vb[Adorners_SimpleCircleAdorner#_AdornChildren](~/samples/snippets/visualbasic/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/VisualBasic/Window1.xaml.vb#_adornchildren)]  
  
> [!NOTE]
> L’utilisation du [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] pour lier un ornement à un autre élément n’est pas prise en charge pour l’instant.  
  
## <a name="see-also"></a>Voir aussi

- [Vue d’ensemble des ornements](adorners-overview.md)
