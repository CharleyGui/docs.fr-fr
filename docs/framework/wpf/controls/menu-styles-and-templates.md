---
title: Styles et modèles Menu
description: En savoir plus sur les styles et les modèles pour le Windows Presentation Foundation le contrôle Menu. Modifiez le ControlTemplate pour attribuer une apparence unique au contrôle.
ms.date: 03/30/2017
helpviewer_keywords:
- styles [WPF], Menu
- ControlTemplate [WPF], Menu
- Menu [WPF], styles and templates
- states [WPF], Menu
- templates [WPF], Menu
- parts [WPF], Menu
ms.assetid: b89da183-9b87-42c6-ac53-731a42c7b09e
ms.openlocfilehash: 5187e4a479609686e39e043808931141ca52078c
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/24/2020
ms.locfileid: "87164548"
---
# <a name="menu-styles-and-templates"></a>Styles et modèles Menu
Cette rubrique décrit les styles et les modèles pour le <xref:System.Windows.Controls.Menu> contrôle. Vous pouvez modifier la valeur par défaut <xref:System.Windows.Controls.ControlTemplate> pour que le contrôle donne une apparence unique. Pour plus d’informations, consultez [créer un modèle pour un contrôle](../../../desktop-wpf/themes/how-to-create-apply-template.md).  
  
## <a name="menu-parts"></a>Éléments de menu  
 Le <xref:System.Windows.Controls.Menu> contrôle n’a pas de parties nommées.  
  
 Lorsque vous créez un <xref:System.Windows.Controls.ControlTemplate> pour un <xref:System.Windows.Controls.Menu> , votre modèle peut contenir un <xref:System.Windows.Controls.ItemsPresenter> dans un <xref:System.Windows.Controls.ScrollViewer> . (Le <xref:System.Windows.Controls.ItemsPresenter> affiche chaque élément dans <xref:System.Windows.Controls.Menu> ; le <xref:System.Windows.Controls.ScrollViewer> permet de faire défiler le contrôle).  Si le <xref:System.Windows.Controls.ItemsPresenter> n’est pas l’enfant direct de <xref:System.Windows.Controls.ScrollViewer> , vous devez fournir le <xref:System.Windows.Controls.ItemsPresenter> nom, `ItemsPresenter` .  
  
## <a name="menu-states"></a>États du menu  
 Le tableau suivant répertorie les États visuels du <xref:System.Windows.Controls.Menu> contrôle.  
  
|Nom VisualState|Nom VisualStateGroup|Description|  
|-|-|-|  
|Valide|ValidationStates|Le contrôle utilise la <xref:System.Windows.Controls.Validation> classe et la <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> propriété jointe est `false` .|  
|InvalidFocused|ValidationStates|La <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> propriété jointe a `true` le contrôle a le focus.|  
|InvalidUnfocused|ValidationStates|La <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> propriété jointe `true` a le contrôle n’a pas le focus.|  
  
## <a name="menuitem-parts"></a>Éléments MenuItem  
 Le tableau suivant répertorie les parties nommées du <xref:System.Windows.Controls.Menu> contrôle.  
  
|Élément|Type|Description|  
|-|-|-|  
|PART_Popup|<xref:System.Windows.Controls.Primitives.Popup>|Zone du sous-menu.|  
  
 Lorsque vous créez un <xref:System.Windows.Controls.ControlTemplate> pour un <xref:System.Windows.Controls.MenuItem> , votre modèle peut contenir un <xref:System.Windows.Controls.ItemsPresenter> dans un <xref:System.Windows.Controls.ScrollViewer> . (Le <xref:System.Windows.Controls.ItemsPresenter> affiche chaque élément dans <xref:System.Windows.Controls.MenuItem> ; le <xref:System.Windows.Controls.ScrollViewer> permet de faire défiler le contrôle).  Si le <xref:System.Windows.Controls.ItemsPresenter> n’est pas l’enfant direct de <xref:System.Windows.Controls.ScrollViewer> , vous devez fournir le <xref:System.Windows.Controls.ItemsPresenter> nom, `ItemsPresenter` .  
  
## <a name="menuitem-states"></a>États MenuItem  
 Le tableau suivant répertorie les États visuels du <xref:System.Windows.Controls.MenuItem> contrôle.  
  
|Nom VisualState|Nom VisualStateGroup|Description|  
|-|-|-|  
|Valide|ValidationStates|Le contrôle utilise la <xref:System.Windows.Controls.Validation> classe et la <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> propriété jointe est `false` .|  
|InvalidFocused|ValidationStates|La <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> propriété jointe a `true` le contrôle a le focus.|  
|InvalidUnfocused|ValidationStates|La <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> propriété jointe `true` a le contrôle n’a pas le focus.|  
  
## <a name="menu-and-menuitem-controltemplate-example"></a>Exemple de menu et MenuItem ControlTemplate  
 L’exemple suivant montre comment définir un <xref:System.Windows.Controls.ControlTemplate> pour le <xref:System.Windows.Controls.Menu> contrôle.  
  
 [!code-xaml[ControlTemplateExamples#Menu](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/menu.xaml#menu)]  
  
 L’exemple suivant montre comment définir un <xref:System.Windows.Controls.ControlTemplate> pour le <xref:System.Windows.Controls.MenuItem> contrôle.  
  
 [!code-xaml[ControlTemplateExamples#MenuItem](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/menu.xaml#menuitem)]  
  
 L’exemple suivant définit le `MenuScrollViewer` , qui est utilisé dans l’exemple précédent.  
  
 [!code-xaml[ControlTemplateExamples#MenuScrollViewer](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/menu.xaml#menuscrollviewer)]  
  
 Les <xref:System.Windows.Controls.ControlTemplate> exemples utilisent une ou plusieurs des ressources suivantes.  
  
 [!code-xaml[ControlTemplateExamples#Resources](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 Pour voir l’exemple complet, consultez [Styling with ControlTemplates Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating) (Exemple de style avec ControlTemplates).  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.FrameworkElement.Style%2A>
- <xref:System.Windows.Controls.ControlTemplate>
- [Styles et modèles Control](control-styles-and-templates.md)
- [Personnalisation des contrôles](control-customization.md)
- [Application d'un style et création de modèles](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
- [Créer un modèle pour un contrôle](../../../desktop-wpf/themes/how-to-create-apply-template.md)
