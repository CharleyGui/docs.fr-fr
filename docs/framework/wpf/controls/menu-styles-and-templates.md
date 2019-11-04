---
title: Styles et modèles Menu
ms.date: 03/30/2017
helpviewer_keywords:
- styles [WPF], Menu
- ControlTemplate [WPF], Menu
- Menu [WPF], styles and templates
- states [WPF], Menu
- templates [WPF], Menu
- parts [WPF], Menu
ms.assetid: b89da183-9b87-42c6-ac53-731a42c7b09e
ms.openlocfilehash: 979ed7292a0f6582753305d1a7704c48aa751003
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/03/2019
ms.locfileid: "73460212"
---
# <a name="menu-styles-and-templates"></a>Styles et modèles Menu
Cette rubrique décrit les styles et les modèles du contrôle <xref:System.Windows.Controls.Menu>. Vous pouvez modifier le <xref:System.Windows.Controls.ControlTemplate> par défaut pour attribuer une apparence unique au contrôle. Pour plus d’informations, consultez [Personnalisation de l'apparence d'un contrôle existant en créant un ControlTemplate](customizing-the-appearance-of-an-existing-control.md).  
  
## <a name="menu-parts"></a>Éléments de menu  
 Le contrôle <xref:System.Windows.Controls.Menu> n’a pas de parties nommées.  
  
 Lorsque vous créez un <xref:System.Windows.Controls.ControlTemplate> pour un <xref:System.Windows.Controls.Menu>, votre modèle peut contenir un <xref:System.Windows.Controls.ItemsPresenter> dans un <xref:System.Windows.Controls.ScrollViewer>. (Le <xref:System.Windows.Controls.ItemsPresenter> affiche chaque élément du <xref:System.Windows.Controls.Menu>; le <xref:System.Windows.Controls.ScrollViewer> permet de faire défiler le contrôle).  Si le <xref:System.Windows.Controls.ItemsPresenter> n’est pas l’enfant direct du <xref:System.Windows.Controls.ScrollViewer>, vous devez attribuer au <xref:System.Windows.Controls.ItemsPresenter> le nom, `ItemsPresenter`.  
  
## <a name="menu-states"></a>États du menu  
 Le tableau suivant répertorie les États visuels du contrôle <xref:System.Windows.Controls.Menu>.  
  
|Nom VisualState|Nom VisualStateGroup|Description|  
|-|-|-|  
|Valide|ValidationStates|Le contrôle utilise la classe <xref:System.Windows.Controls.Validation> et la propriété jointe <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> est `false`.|  
|InvalidFocused|ValidationStates|La propriété jointe <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> est `true` a le focus.|  
|InvalidUnfocused|ValidationStates|La propriété jointe <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> est `true` a le contrôle n’a pas le focus.|  
  
## <a name="menuitem-parts"></a>Éléments MenuItem  
 Le tableau suivant répertorie les parties nommées du contrôle <xref:System.Windows.Controls.Menu>.  
  
|Élément|Tapez|Description|  
|-|-|-|  
|PART_Popup|<xref:System.Windows.Controls.Primitives.Popup>|Zone du sous-menu.|  
  
 Lorsque vous créez un <xref:System.Windows.Controls.ControlTemplate> pour un <xref:System.Windows.Controls.MenuItem>, votre modèle peut contenir un <xref:System.Windows.Controls.ItemsPresenter> dans un <xref:System.Windows.Controls.ScrollViewer>. (Le <xref:System.Windows.Controls.ItemsPresenter> affiche chaque élément du <xref:System.Windows.Controls.MenuItem>; le <xref:System.Windows.Controls.ScrollViewer> permet de faire défiler le contrôle).  Si le <xref:System.Windows.Controls.ItemsPresenter> n’est pas l’enfant direct du <xref:System.Windows.Controls.ScrollViewer>, vous devez attribuer au <xref:System.Windows.Controls.ItemsPresenter> le nom, `ItemsPresenter`.  
  
## <a name="menuitem-states"></a>États MenuItem  
 Le tableau suivant répertorie les États visuels du contrôle <xref:System.Windows.Controls.MenuItem>.  
  
|Nom VisualState|Nom VisualStateGroup|Description|  
|-|-|-|  
|Valide|ValidationStates|Le contrôle utilise la classe <xref:System.Windows.Controls.Validation> et la propriété jointe <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> est `false`.|  
|InvalidFocused|ValidationStates|La propriété jointe <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> est `true` a le focus.|  
|InvalidUnfocused|ValidationStates|La propriété jointe <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> est `true` a le contrôle n’a pas le focus.|  
  
## <a name="menu-and-menuitem-controltemplate-example"></a>Exemple de menu et MenuItem ControlTemplate  
 L’exemple suivant montre comment définir une <xref:System.Windows.Controls.ControlTemplate> pour le contrôle <xref:System.Windows.Controls.Menu>.  
  
 [!code-xaml[ControlTemplateExamples#Menu](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/menu.xaml#menu)]  
  
 L’exemple suivant montre comment définir une <xref:System.Windows.Controls.ControlTemplate> pour le contrôle <xref:System.Windows.Controls.MenuItem>.  
  
 [!code-xaml[ControlTemplateExamples#MenuItem](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/menu.xaml#menuitem)]  
  
 L’exemple suivant définit le `MenuScrollViewer`, qui est utilisé dans l’exemple précédent.  
  
 [!code-xaml[ControlTemplateExamples#MenuScrollViewer](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/menu.xaml#menuscrollviewer)]  
  
 Les exemples de <xref:System.Windows.Controls.ControlTemplate> utilisent une ou plusieurs des ressources suivantes.  
  
 [!code-xaml[ControlTemplateExamples#Resources](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 Pour voir l’exemple complet, consultez [Styling with ControlTemplates Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating) (Exemple de style avec ControlTemplates).  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.FrameworkElement.Style%2A>
- <xref:System.Windows.Controls.ControlTemplate>
- [Styles et modèles Control](control-styles-and-templates.md)
- [Personnalisation des contrôles](control-customization.md)
- [Application d’un style et création de modèles](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
- [Personnalisation de l’apparence d’un contrôle existant en créant un ControlTemplate](customizing-the-appearance-of-an-existing-control.md)
