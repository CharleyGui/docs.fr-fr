---
title: 'Comment : appliquer un FocusVisualStyle à un contrôle'
ms.date: 03/30/2017
helpviewer_keywords:
- properties [WPF], FocusVisualStyle
- FocusVisualStyle property [WPF]
ms.assetid: 363de99e-8ecc-438c-ac4a-f9147432ebd6
ms.openlocfilehash: b44330ee7554f953389556bd62ff49db120b5db9
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/03/2019
ms.locfileid: "73459806"
---
# <a name="how-to-apply-a-focusvisualstyle-to-a-control"></a>Comment : appliquer un FocusVisualStyle à un contrôle
Cet exemple montre comment créer un style de focus visuel dans les ressources et appliquer le style à un contrôle à l’aide de la propriété <xref:System.Windows.FrameworkElement.FocusVisualStyle%2A>.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant définit un style qui crée une composition de contrôle supplémentaire qui s’applique uniquement lorsque le contrôle est axé sur le clavier dans le [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)]. Pour ce faire, vous devez définir un style avec un <xref:System.Windows.Controls.ControlTemplate>, puis référencer ce style en tant que ressource lors de la définition de la propriété <xref:System.Windows.FrameworkElement.FocusVisualStyle%2A>.  
  
 Un rectangle externe ressemblant à une bordure est placé en dehors de la zone rectangulaire. Sauf modification contraire, le dimensionnement du style utilise le <xref:System.Windows.FrameworkElement.ActualHeight%2A> et <xref:System.Windows.FrameworkElement.ActualWidth%2A> du contrôle rectangulaire où le style de focus visuel est appliqué. Cet exemple définit des valeurs négatives pour le <xref:System.Windows.FrameworkElement.Margin%2A> pour que la bordure apparaisse légèrement en dehors du contrôle ayant le focus.  
  
 [!code-xaml[FEFocusVisualStyle#XAML](~/samples/snippets/csharp/VS_Snippets_Wpf/FEFocusVisualStyle/CS/page1.xaml#xaml)]  
  
 Un <xref:System.Windows.FrameworkElement.FocusVisualStyle%2A> est additif pour tout style de modèle de contrôle qui provient d’un style explicite ou d’un style de thème. le style principal d’un contrôle peut toujours être créé à l’aide d’un <xref:System.Windows.Controls.ControlTemplate> et définir ce style sur la propriété <xref:System.Windows.FrameworkElement.Style%2A>.  
  
 Les styles visuels de focus doivent être utilisés de manière cohérente sur un thème ou une interface utilisateur, plutôt que d’utiliser un autre pour chaque élément pouvant être actif. Pour plus d’informations, consultez la rubrique [stylisation du focus dans les contrôles et FocusVisualStyle](styling-for-focus-in-controls-and-focusvisualstyle.md).  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.FrameworkElement.FocusVisualStyle%2A>
- [Application d’un style et création de modèles](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
- [FocusVisualStyle et application d'un style au focus dans les contrôles](styling-for-focus-in-controls-and-focusvisualstyle.md)
