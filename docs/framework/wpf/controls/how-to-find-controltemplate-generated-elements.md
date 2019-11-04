---
title: Rechercher des éléments générés par ControlTemplate
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ControlTemplates [WPF], finding elements
- finding ControlTemplate elements [WPF]
ms.assetid: d7b25447-ceff-4bb4-9be5-fd7c40ef00af
ms.openlocfilehash: 232ee7d2859059591c9beff753f45781598a8127
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/03/2019
ms.locfileid: "73460708"
---
# <a name="how-to-find-controltemplate-generated-elements"></a>Rechercher des éléments générés par ControlTemplate
Cet exemple montre comment rechercher des éléments générés par un <xref:System.Windows.Controls.ControlTemplate>.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant montre un style qui crée un <xref:System.Windows.Controls.ControlTemplate> simple pour la classe <xref:System.Windows.Controls.Button> :  
  
 [!code-xaml[FindGeneratedItems#CT](~/samples/snippets/csharp/VS_Snippets_Wpf/FindGeneratedItems/CSharp/Window1.xaml#ct)]  
  
 Pour rechercher un élément dans le modèle une fois que le modèle a été appliqué, vous pouvez appeler la méthode <xref:System.Windows.FrameworkTemplate.FindName%2A> de l' <xref:System.Windows.Controls.Control.Template%2A>. L’exemple suivant crée une boîte de message qui affiche la valeur de largeur réelle du <xref:System.Windows.Controls.Grid> dans le modèle de contrôle :  
  
 [!code-csharp[FindGeneratedItems#CTFindElement](~/samples/snippets/csharp/VS_Snippets_Wpf/FindGeneratedItems/CSharp/Window1.xaml.cs#ctfindelement)]
 [!code-vb[FindGeneratedItems#CTFindElement](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FindGeneratedItems/VisualBasic/Window1.xaml.vb#ctfindelement)]  
  
## <a name="see-also"></a>Voir aussi

- [Rechercher des éléments générés par DataTemplate](../data/how-to-find-datatemplate-generated-elements.md)
- [Application d’un style et création de modèles](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
- [Portées de nom XAML WPF](../advanced/wpf-xaml-namescopes.md)
- [Arborescences dans WPF](../advanced/trees-in-wpf.md)
