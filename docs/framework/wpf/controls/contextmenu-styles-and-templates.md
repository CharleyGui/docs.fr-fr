---
title: Styles et modèles ContextMenu
ms.date: 03/30/2017
helpviewer_keywords:
- templates [WPF], ContextMenu
- parts [WPF], ContextMenu
- ContextMenu [WPF], styles and templates
- styles [WPF], ContextMenu
- ControlTemplate [WPF], ContextMenu
- states [WPF], ContextMenu
ms.assetid: 342d1f17-c406-4f94-8f55-867c5f3ea511
ms.openlocfilehash: 4112306dab648d022e171401f5b9b362f2c91fdc
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/03/2019
ms.locfileid: "73460764"
---
# <a name="contextmenu-styles-and-templates"></a>Styles et modèles ContextMenu
Cette rubrique décrit les styles et les modèles du contrôle <xref:System.Windows.Controls.ContextMenu>. Vous pouvez modifier le <xref:System.Windows.Controls.ControlTemplate> par défaut pour attribuer une apparence unique au contrôle. Pour plus d’informations, consultez [Personnalisation de l'apparence d'un contrôle existant en créant un ControlTemplate](customizing-the-appearance-of-an-existing-control.md).  
  
## <a name="contextmenu-parts"></a>Composants ContextMenu  
 Le contrôle <xref:System.Windows.Controls.ContextMenu> n’a pas de parties nommées.  
  
 Lorsque vous créez un <xref:System.Windows.Controls.ControlTemplate> pour un <xref:System.Windows.Controls.ContextMenu>, votre modèle peut contenir un <xref:System.Windows.Controls.ItemsPresenter> dans un <xref:System.Windows.Controls.ScrollViewer>. (Le <xref:System.Windows.Controls.ItemsPresenter> affiche chaque élément du <xref:System.Windows.Controls.ContextMenu>; le <xref:System.Windows.Controls.ScrollViewer> permet de faire défiler le contrôle).  Si le <xref:System.Windows.Controls.ItemsPresenter> n’est pas l’enfant direct du <xref:System.Windows.Controls.ScrollViewer>, vous devez attribuer au <xref:System.Windows.Controls.ItemsPresenter> le nom, `ItemsPresenter`.  
  
## <a name="contextmenu-states"></a>États de ContextMenu  
 Le tableau suivant répertorie les États visuels du contrôle <xref:System.Windows.Controls.ContextMenu>.  
  
|Nom VisualState|Nom VisualStateGroup|Description|  
|-|-|-|  
|Valide|ValidationStates|Le contrôle utilise la classe <xref:System.Windows.Controls.Validation> et la propriété jointe <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> est `false`.|  
|InvalidFocused|ValidationStates|La propriété jointe <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> est `true` a le focus.|  
|InvalidUnfocused|ValidationStates|La propriété jointe <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> est `true` a le contrôle n’a pas le focus.|  
  
## <a name="contextmenu-controltemplate-example"></a>ContextMenu ControlTemplate, exemple  
 L’exemple suivant montre comment définir une <xref:System.Windows.Controls.ControlTemplate> pour le contrôle <xref:System.Windows.Controls.ContextMenu>.  
  
 [!code-xaml[ControlTemplateExamples#ContextMenu](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/menu.xaml#contextmenu)]  
  
 Le <xref:System.Windows.Controls.ControlTemplate> utilise les ressources suivantes.  
  
 [!code-xaml[ControlTemplateExamples#Resources](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 Pour voir l’exemple complet, consultez [Styling with ControlTemplates Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating) (Exemple de style avec ControlTemplates).  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.FrameworkElement.Style%2A>
- <xref:System.Windows.Controls.ControlTemplate>
- [Styles et modèles Control](control-styles-and-templates.md)
- [Personnalisation des contrôles](control-customization.md)
- [Application d’un style et création de modèles](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
- [Personnalisation de l’apparence d’un contrôle existant en créant un ControlTemplate](customizing-the-appearance-of-an-existing-control.md)
