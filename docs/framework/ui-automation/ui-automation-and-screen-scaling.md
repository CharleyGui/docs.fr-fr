---
title: Mise à l'échelle de l'écran et UI Automation
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- scaling, screens
- screens, scaling
- UI (user interface), automation
- UI Automation
ms.assetid: 4380cad7-e509-448f-b9a5-6de042605fd4
ms.openlocfilehash: ceab7db1f9eeb47ec020e220ec702af8181855e2
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74442480"
---
# <a name="ui-automation-and-screen-scaling"></a>Mise à l'échelle de l'écran et UI Automation
> [!NOTE]
> Cette documentation s'adresse aux développeurs .NET Framework qui souhaitent utiliser les classes [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] managées définies dans l'espace de noms <xref:System.Windows.Automation>. Pour obtenir les dernières informations sur [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], consultez [API Windows Automation : UI Automation](/windows/win32/winauto/entry-uiauto-win32).  
  
Starting with Windows Vista, Windows enables users to change the dots per inch (dpi) setting so that most user interface (UI) elements on the screen appear larger. Although this feature has long been available in Windows, in previous versions the scaling had to be implemented by applications. Starting with Windows Vista, the Desktop Window Manager performs default scaling for all applications that do not handle their own scaling. Les applications clientes UI Automation doivent prendre en compte cette fonctionnalité.  
  
<a name="Scaling_in_Windows_Vista"></a>   
## <a name="scaling-in-windows-vista"></a>Mise à l’échelle dans Windows Vista  
 The default dpi setting is 96, which means that 96 pixels occupy a width or height of one notional inch. La mesure exacte d’un « pouce » dépend de la taille et de la résolution physique du moniteur. Par exemple, sur un moniteur d’une largeur de 12 pouces, pour une résolution horizontale de 1 280 pixels, une ligne horizontale de 96 pixels s’étend sur 9/10e de pouce.  
  
 Changing the dpi setting is not the same as changing the screen resolution. With dpi scaling, the number of physical pixels on the screen remains the same. Toutefois, la mise à l’échelle est appliquée à la taille et à l’emplacement des éléments [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] . Cette mise à l’échelle peut être effectuée automatiquement par le Gestionnaire de fenêtrage (DWM, Desktop Window Manager) pour le bureau et pour les applications qui ne demandent pas explicitement à ne pas être mises à l’échelle.  
  
 In effect, when the user sets the scale factor to 120 dpi, a vertical or horizontal inch on the screen becomes bigger by 25 percent. Toutes les dimensions sont ajustées en conséquence. Le décalage d’une fenêtre d’application par rapport aux bords supérieur et gauche de l’écran augmente de 25 %. If application scaling is enabled and the application is not dpi-aware, the size of the window increases in the same proportion, along with the offsets and sizes of all [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] elements it contains.  
  
> [!NOTE]
> By default, the DWM does not perform scaling for non-dpi-aware applications when the user sets the dpi to 120, but does perform it when the dpi is set to a custom value of 144 or higher. Toutefois, l’utilisateur peut remplacer le comportement par défaut.  
  
 La mise à l’échelle de l’écran pose de nouveaux défis pour les applications qui sont concernées d’une manière ou d’une autre par les coordonnées d’écran. L’écran contient maintenant deux systèmes de coordonnées : l’un physique et l’autre logique. Les coordonnées physiques d’un point correspondent au décalage réel en pixels par rapport au point d’origine en haut à gauche. Les coordonnées logiques correspondent aux décalages tels qu’ils seraient si les pixels eux-mêmes étaient mis à l’échelle.  
  
 Supposons que vous concevez une boîte de dialogue avec un bouton aux coordonnées (100, 48). When this dialog box is displayed at the default 96 dpi, the button is located at physical coordinates of (100, 48). At 120 dpi, it is located at physical coordinates of (125, 60). But the logical coordinates are the same at any dpi setting: (100, 48).  
  
 Logical coordinates are important, because they make the behavior of the operating system and applications consistent regardless of the dpi setting. Par exemple, <xref:System.Windows.Forms.Cursor.Position%2A?displayProperty=nameWithType> retourne normalement les coordonnées logiques. If you move the cursor over an element in a dialog box, the same coordinates are returned regardless of the dpi setting. If you draw a control at (100, 100), it is drawn to those logical coordinates, and will occupy the same relative position at any dpi setting.  
  
<a name="Scaling_in_UI_Automation_Clients"></a>   
## <a name="scaling-in-ui-automation-clients"></a>Mise à l’échelle dans les clients UI Automation  
 The [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] API does not use logical coordinates. Les méthodes et propriétés suivantes retournent des coordonnées physiques ou les utilisent comme paramètres.  
  
- <xref:System.Windows.Automation.AutomationElement.GetClickablePoint%2A>  
  
- <xref:System.Windows.Automation.AutomationElement.TryGetClickablePoint%2A>  
  
- <xref:System.Windows.Automation.AutomationElement.ClickablePointProperty>  
  
- <xref:System.Windows.Automation.AutomationElement.FromPoint%2A>  
  
- <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.BoundingRectangle%2A>  
  
 By default, a UI Automation client application running in a non-96- dpi environment will not be able to obtain correct results from these methods and properties. Par exemple, comme la position du curseur est exprimée en coordonnées logiques, le client ne peut pas simplement passer ces coordonnées à <xref:System.Windows.Automation.AutomationElement.FromPoint%2A> pour obtenir l’élément situé sous le curseur. En outre, l’application n’est pas en mesure de placer correctement les fenêtres en dehors de sa zone cliente.  
  
 La solution comporte deux parties.  
  
1. First, make the client application dpi-aware. Pour cela, appelez la fonction [!INCLUDE[TLA#tla_win32](../../../includes/tlasharptla-win32-md.md)] `SetProcessDPIAware` au démarrage. En code managé, la déclaration suivante rend cette fonction disponible.  
  
     [!code-csharp[Highlighter#101](../../../samples/snippets/csharp/VS_Snippets_Wpf/Highlighter/CSharp/NativeMethods.cs#101)]
     [!code-vb[Highlighter#101](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/Highlighter/VisualBasic/NativeMethods.vb#101)]  
  
     This function makes the entire process dpi-aware, meaning that all windows that belong to the process are unscaled. In the [Highlighter Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Accessibility/Highlighter), for instance, the four windows that make up the highlight rectangle are located at the physical coordinates obtained from UI Automation, not the logical coordinates. If the sample were not dpi-aware, the highlight would be drawn at the logical coordinates on the desktop, which would result in incorrect placement in a non-96- dpi environment.  
  
2. Pour obtenir les coordonnées du curseur, appelez la fonction [!INCLUDE[TLA#tla_win32](../../../includes/tlasharptla-win32-md.md)] `GetPhysicalCursorPos`. L’exemple suivant montre comment déclarer et utiliser cette fonction.  
  
     [!code-csharp[UIAClient_snip#185](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAClient_snip/CSharp/ClientForm.cs#185)]
     [!code-vb[UIAClient_snip#185](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAClient_snip/VisualBasic/ClientForm.vb#185)]  
  
> [!CAUTION]
> N’utilisez pas <xref:System.Windows.Forms.Cursor.Position%2A?displayProperty=nameWithType>. Le comportement de cette propriété en dehors des fenêtres clientes dans un environnement à l’échelle n’est pas défini.  
  
 If your application performs direct cross-process communication with non- dpi-aware applications, you may have convert between logical and physical coordinates by using the [!INCLUDE[TLA#tla_win32](../../../includes/tlasharptla-win32-md.md)] functions `PhysicalToLogicalPoint` and `LogicalToPhysicalPoint`.  
  
## <a name="see-also"></a>Voir aussi

- [Highlighter Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Accessibility/Highlighter)
