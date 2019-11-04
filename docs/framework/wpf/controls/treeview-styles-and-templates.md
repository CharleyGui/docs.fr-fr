---
title: Styles et modèles TreeView
ms.date: 03/30/2017
helpviewer_keywords:
- ControlTemplate [WPF], TreeView
- templates [WPF], TreeView
- parts [WPF], TreeView
- states [WPF], TreeView
- styles [WPF], TreeView
- TreeView [WPF], styles and templates
ms.assetid: a49adb77-0202-4caa-b94a-8bb110d7fa9a
ms.openlocfilehash: f6dbe54324a5ad5e2f85719d819c035abfd644b1
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/03/2019
ms.locfileid: "73460186"
---
# <a name="treeview-styles-and-templates"></a>Styles et modèles TreeView
Cette rubrique décrit les styles et les modèles du contrôle <xref:System.Windows.Controls.TreeView>. Vous pouvez modifier le <xref:System.Windows.Controls.ControlTemplate> par défaut pour attribuer une apparence unique au contrôle. Pour plus d’informations, consultez [Personnalisation de l'apparence d'un contrôle existant en créant un ControlTemplate](customizing-the-appearance-of-an-existing-control.md).  
  
## <a name="treeview-parts"></a>Composants TreeView  
 Le contrôle <xref:System.Windows.Controls.TreeView> n’a pas de parties nommées.  
  
 Lorsque vous créez un <xref:System.Windows.Controls.ControlTemplate> pour un <xref:System.Windows.Controls.TreeView>, votre modèle peut contenir un <xref:System.Windows.Controls.ItemsPresenter> dans un <xref:System.Windows.Controls.ScrollViewer>. (Le <xref:System.Windows.Controls.ItemsPresenter> affiche chaque élément du <xref:System.Windows.Controls.TreeView>; le <xref:System.Windows.Controls.ScrollViewer> permet de faire défiler le contrôle).  Si le <xref:System.Windows.Controls.ItemsPresenter> n’est pas l’enfant direct du <xref:System.Windows.Controls.ScrollViewer>, vous devez attribuer au <xref:System.Windows.Controls.ItemsPresenter> le nom, `ItemsPresenter`.  
  
## <a name="treeview-states"></a>États TreeView  
 Le tableau suivant répertorie les États visuels du contrôle <xref:System.Windows.Controls.TreeView>.  
  
|Nom VisualState|Nom VisualStateGroup|Description|  
|-|-|-|  
|Valide|ValidationStates|Le contrôle utilise la classe <xref:System.Windows.Controls.Validation> et la propriété jointe <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> est `false`.|  
|InvalidFocused|ValidationStates|La propriété jointe <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> est `true` a le focus.|  
|InvalidUnfocused|ValidationStates|La propriété jointe <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> est `true` a le contrôle n’a pas le focus.|  
  
## <a name="treeviewitem-parts"></a>Parties de TreeViewItem  
 Le tableau suivant répertorie les parties nommées du contrôle <xref:System.Windows.Controls.TreeViewItem>.  
  
|Élément|Tapez|Description|  
|----------|----------|-----------------|  
|PART_Header|<xref:System.Windows.FrameworkElement>|Élément visuel qui contient le contenu d’en-tête du contrôle <xref:System.Windows.Controls.TreeView>.|  
  
## <a name="treeviewitem-states"></a>États de TreeViewItem  
 Le tableau suivant répertorie les États visuels pour <xref:System.Windows.Controls.TreeViewItem> contrôle.  
  
|Nom VisualState|Nom VisualStateGroup|Description|  
|----------------------|---------------------------|-----------------|  
|Normale|CommonStates|État par défaut.|  
|MouseOver|CommonStates|Le pointeur de la souris est positionné sur le <xref:System.Windows.Controls.TreeViewItem>.|  
|Disabled|CommonStates|Le <xref:System.Windows.Controls.TreeViewItem> est désactivé.|  
|Avec focus|FocusStates|Le <xref:System.Windows.Controls.TreeViewItem> a le focus.|  
|Sans focus|FocusStates|Le <xref:System.Windows.Controls.TreeViewItem> n’a pas le focus.|  
|Étendu|ExpansionStates|Le contrôle <xref:System.Windows.Controls.TreeViewItem> est développé.|  
|Collapsed|ExpansionStates|Le contrôle <xref:System.Windows.Controls.TreeViewItem> est réduit.|  
|HasItems|HasItemsStates|Le <xref:System.Windows.Controls.TreeViewItem> a des éléments.|  
|Noitems|HasItemsStates|Le <xref:System.Windows.Controls.TreeViewItem> n’a pas d’éléments.|  
|Selected|SelectionStates|La <xref:System.Windows.Controls.TreeViewItem> est sélectionnée.|  
|SelectedInactive|SelectionStates|La <xref:System.Windows.Controls.TreeViewItem> est sélectionnée, mais elle n’est pas active.|  
|Non sélectionné|SelectionStates|La <xref:System.Windows.Controls.TreeViewItem> n’est pas sélectionnée.|  
|Valide|ValidationStates|Le contrôle utilise la classe <xref:System.Windows.Controls.Validation> et la propriété jointe <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> est `false`.|  
|InvalidFocused|ValidationStates|La propriété jointe <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> est `true` a le focus.|  
|InvalidUnfocused|ValidationStates|La propriété jointe <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> est `true` a le contrôle n’a pas le focus.|  
  
## <a name="treeview-controltemplate-example"></a>Exemple de ControlTemplate TreeView  
 L’exemple suivant montre comment définir une <xref:System.Windows.Controls.ControlTemplate> pour le contrôle <xref:System.Windows.Controls.TreeView> et ses types associés.  
  
 [!code-xaml[ControlTemplateExamples#TreeView](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/treeview.xaml#treeview)]  
  
 L’exemple précédent utilise une ou plusieurs des ressources suivantes.  
  
 [!code-xaml[ControlTemplateExamples#Resources](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 Pour voir l’exemple complet, consultez [Styling with ControlTemplates Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating) (Exemple de style avec ControlTemplates).  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.FrameworkElement.Style%2A>
- <xref:System.Windows.Controls.ControlTemplate>
- [Styles et modèles Control](control-styles-and-templates.md)
- [Personnalisation des contrôles](control-customization.md)
- [Application d’un style et création de modèles](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
- [Personnalisation de l’apparence d’un contrôle existant en créant un ControlTemplate](customizing-the-appearance-of-an-existing-control.md)
