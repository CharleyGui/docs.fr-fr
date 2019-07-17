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
ms.openlocfilehash: 4e101fffbd7e53cadce0b621d73ade2d1459ba00
ms.sourcegitcommit: 4d8efe00f2e5ab42e598aff298d13b8c052d9593
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/16/2019
ms.locfileid: "68237442"
---
# <a name="ui-automation-and-screen-scaling"></a>Mise à l'échelle de l'écran et UI Automation
> [!NOTE]
>  Cette documentation s'adresse aux développeurs .NET Framework qui souhaitent utiliser les classes [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] managées définies dans l'espace de noms <xref:System.Windows.Automation>. Pour plus d’informations sur [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], consultez [Windows Automation API : UI Automation](https://go.microsoft.com/fwlink/?LinkID=156746).  
  
 [!INCLUDE[TLA#tla_longhorn](../../../includes/tlasharptla-longhorn-md.md)] permet aux utilisateurs de modifier le paramètre [!INCLUDE[TLA#tla_dpi](../../../includes/tlasharptla-dpi-md.md)] afin que la plupart des éléments [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)] apparaissent plus grands à l’écran. Cette fonctionnalité est disponible depuis longtemps dans [!INCLUDE[TLA#tla_win](../../../includes/tlasharptla-win-md.md)], mais la mise à l’échelle devait être implémentée par les applications dans les versions précédentes. Dans [!INCLUDE[TLA#tla_longhorn](../../../includes/tlasharptla-longhorn-md.md)], le Gestionnaire de fenêtrage effectue une mise à l’échelle par défaut pour toutes les applications qui ne gèrent pas leur propre mise à l’échelle. Les applications clientes UI Automation doivent prendre en compte cette fonctionnalité.  
  
<a name="Scaling_in_Windows_Vista"></a>   
## <a name="scaling-in-windows-vista"></a>Mise à l’échelle dans Windows Vista  
 La valeur par défaut du paramètre [!INCLUDE[TLA2#tla_dpi](../../../includes/tla2sharptla-dpi-md.md)] est 96, ce qui signifie que 96 pixels occupent la largeur ou la hauteur d’un pouce fictif. La mesure exacte d’un « pouce » dépend de la taille et de la résolution physique du moniteur. Par exemple, sur un moniteur d’une largeur de 12 pouces, pour une résolution horizontale de 1 280 pixels, une ligne horizontale de 96 pixels s’étend sur 9/10e de pouce.  
  
 La modification du paramètre [!INCLUDE[TLA2#tla_dpi](../../../includes/tla2sharptla-dpi-md.md)] n’est pas équivalente à la modification de la résolution de l’écran. Avec la mise à l’échelle [!INCLUDE[TLA2#tla_dpi](../../../includes/tla2sharptla-dpi-md.md)] , le nombre de pixels physiques sur l’écran reste le même. Toutefois, la mise à l’échelle est appliquée à la taille et à l’emplacement des éléments [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] . Cette mise à l’échelle peut être effectuée automatiquement par le Gestionnaire de fenêtrage (DWM, Desktop Window Manager) pour le bureau et pour les applications qui ne demandent pas explicitement à ne pas être mises à l’échelle.  
  
 En effet, quand l’utilisateur définit le facteur d’échelle à 120 [!INCLUDE[TLA2#tla_dpi](../../../includes/tla2sharptla-dpi-md.md)], un pouce vertical ou horizontal sur l’écran s’agrandit de 25 %. Toutes les dimensions sont ajustées en conséquence. Le décalage d’une fenêtre d’application par rapport aux bords supérieur et gauche de l’écran augmente de 25 %. Si la mise à l’échelle de l’application est activée et que l’application est sans prise en charge [!INCLUDE[TLA2#tla_dpi](../../../includes/tla2sharptla-dpi-md.md)], la taille de la fenêtre augmente dans les mêmes proportions, ainsi que les décalages et la taille de tous les éléments [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] qu’elle contient.  
  
> [!NOTE]
>  Par défaut, le Gestionnaire de fenêtrage n’effectue pas de mise à l’échelle pour les applications sans prise en charge[!INCLUDE[TLA2#tla_dpi](../../../includes/tla2sharptla-dpi-md.md)]quand l’utilisateur affecte au paramètre [!INCLUDE[TLA2#tla_dpi](../../../includes/tla2sharptla-dpi-md.md)] la valeur 120, mais effectue la mise à l’échelle lorsque le paramètre [!INCLUDE[TLA2#tla_dpi](../../../includes/tla2sharptla-dpi-md.md)] a une valeur personnalisée égale ou supérieure à 144. Toutefois, l’utilisateur peut remplacer le comportement par défaut.  
  
 La mise à l’échelle de l’écran pose de nouveaux défis pour les applications qui sont concernées d’une manière ou d’une autre par les coordonnées d’écran. L’écran contient maintenant deux systèmes de coordonnées : l’un physique et l’autre logique. Les coordonnées physiques d’un point correspondent au décalage réel en pixels par rapport au point d’origine en haut à gauche. Les coordonnées logiques correspondent aux décalages tels qu’ils seraient si les pixels eux-mêmes étaient mis à l’échelle.  
  
 Supposons que vous concevez une boîte de dialogue avec un bouton aux coordonnées (100, 48). Quand cette boîte de dialogue est affichée avec la valeur par défaut 96 [!INCLUDE[TLA2#tla_dpi](../../../includes/tla2sharptla-dpi-md.md)], le bouton se trouve aux coordonnées physiques (100, 48). À 120 [!INCLUDE[TLA2#tla_dpi](../../../includes/tla2sharptla-dpi-md.md)], il se trouve aux coordonnées physiques (125, 60). Mais les coordonnées logiques sont les mêmes quel que soit [!INCLUDE[TLA2#tla_dpi](../../../includes/tla2sharptla-dpi-md.md)] paramètre : (100, 48).  
  
 Les coordonnées logiques sont importantes, car elles assurent la cohérence du comportement du système d’exploitation et des applications quel que soit le paramètre [!INCLUDE[TLA2#tla_dpi](../../../includes/tla2sharptla-dpi-md.md)] . Par exemple, <xref:System.Windows.Forms.Cursor.Position%2A?displayProperty=nameWithType> retourne normalement les coordonnées logiques. Si vous placez le curseur au-dessus d’un élément dans une boîte de dialogue, les mêmes coordonnées sont retournées quelle que soit la valeur du paramètre [!INCLUDE[TLA2#tla_dpi](../../../includes/tla2sharptla-dpi-md.md)] . Si vous dessinez un contrôle à (100, 100), il est placé à ces coordonnées logiques et occupera la même position relative, quel que soit le paramètre [!INCLUDE[TLA2#tla_dpi](../../../includes/tla2sharptla-dpi-md.md)] .  
  
<a name="Scaling_in_UI_Automation_Clients"></a>   
## <a name="scaling-in-ui-automation-clients"></a>Mise à l’échelle dans les clients UI Automation  
 Le [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] API n’utilise pas les coordonnées logiques. Les méthodes et propriétés suivantes retournent des coordonnées physiques ou les utilisent comme paramètres.  
  
- <xref:System.Windows.Automation.AutomationElement.GetClickablePoint%2A>  
  
- <xref:System.Windows.Automation.AutomationElement.TryGetClickablePoint%2A>  
  
- <xref:System.Windows.Automation.AutomationElement.ClickablePointProperty>  
  
- <xref:System.Windows.Automation.AutomationElement.FromPoint%2A>  
  
- <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.BoundingRectangle%2A>  
  
 Par défaut, une application cliente UI Automation en cours d’exécution dans un environnement doté d’un paramètre [!INCLUDE[TLA2#tla_dpi](../../../includes/tla2sharptla-dpi-md.md)] différent de 96 n’est pas en mesure d’obtenir des résultats corrects à partir de ces méthodes et propriétés. Par exemple, comme la position du curseur est exprimée en coordonnées logiques, le client ne peut pas simplement passer ces coordonnées à <xref:System.Windows.Automation.AutomationElement.FromPoint%2A> pour obtenir l’élément situé sous le curseur. En outre, l’application n’est pas en mesure de placer correctement les fenêtres en dehors de sa zone cliente.  
  
 La solution comporte deux parties.  
  
1. Commencez par activer la prise en charge [!INCLUDE[TLA2#tla_dpi](../../../includes/tla2sharptla-dpi-md.md)]de l’application cliente. Pour cela, appelez la fonction [!INCLUDE[TLA#tla_win32](../../../includes/tlasharptla-win32-md.md)] `SetProcessDPIAware` au démarrage. En code managé, la déclaration suivante rend cette fonction disponible.  
  
     [!code-csharp[Highlighter#101](../../../samples/snippets/csharp/VS_Snippets_Wpf/Highlighter/CSharp/NativeMethods.cs#101)]
     [!code-vb[Highlighter#101](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/Highlighter/VisualBasic/NativeMethods.vb#101)]  
  
     Cette fonction effectue l’ensemble du processus PPP prenant en charge, ce qui signifie que toutes les fenêtres qui appartiennent au processus sont non ajustées. Dans le [Highlighter Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Accessibility/Highlighter), par exemple, les quatre fenêtres qui composent le rectangle de sélection sont situés aux coordonnées physiques obtenues à partir d’UI Automation, pas les coordonnées logiques. Si l’exemple ne prenait pas reconnaissant les résolutions, la sélection serait placée aux coordonnées logiques sur le bureau, ce qui entraînerait un positionnement incorrect dans un environnement de 96 PPP.  
  
2. Pour obtenir les coordonnées du curseur, appelez la fonction [!INCLUDE[TLA#tla_win32](../../../includes/tlasharptla-win32-md.md)] `GetPhysicalCursorPos`. L’exemple suivant montre comment déclarer et utiliser cette fonction.  
  
     [!code-csharp[UIAClient_snip#185](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAClient_snip/CSharp/ClientForm.cs#185)]
     [!code-vb[UIAClient_snip#185](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAClient_snip/VisualBasic/ClientForm.vb#185)]  
  
> [!CAUTION]
>  N’utilisez pas <xref:System.Windows.Forms.Cursor.Position%2A?displayProperty=nameWithType>. Le comportement de cette propriété en dehors des fenêtres clientes dans un environnement à l’échelle n’est pas défini.  
  
 Si votre application effectue une communication interprocessus directe avec des applications sans prise en charge [!INCLUDE[TLA2#tla_dpi](../../../includes/tla2sharptla-dpi-md.md)], vous pouvez être tenu d’effectuer des conversions entre les coordonnées logiques et physiques à l’aide des fonctions [!INCLUDE[TLA#tla_win32](../../../includes/tlasharptla-win32-md.md)] `PhysicalToLogicalPoint` et `LogicalToPhysicalPoint`.  
  
## <a name="see-also"></a>Voir aussi

- [Highlighter Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Accessibility/Highlighter)
