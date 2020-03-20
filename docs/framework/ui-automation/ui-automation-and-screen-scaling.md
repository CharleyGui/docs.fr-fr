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
ms.openlocfilehash: 2a68a74fa6aadcaba21f142d394a1f8a3d8af371
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79179969"
---
# <a name="ui-automation-and-screen-scaling"></a>Mise à l'échelle de l'écran et UI Automation
> [!NOTE]
> Cette documentation s'adresse aux développeurs .NET Framework qui souhaitent utiliser les classes [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] managées définies dans l'espace de noms <xref:System.Windows.Automation>. Pour obtenir les dernières informations sur [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], consultez [API Windows Automation : UI Automation](/windows/win32/winauto/entry-uiauto-win32).  
  
En commençant par Windows Vista, Windows permet aux utilisateurs de modifier les points par pouce (dpi) réglage de sorte que la plupart des interfaces utilisateur (interface utilisateur) éléments sur l’écran apparaissent plus grands. Bien que cette fonctionnalité a longtemps été disponible dans Windows, dans les versions précédentes de la mise à l’échelle a dû être implémentée par les applications. En commençant par Windows Vista, le gestionnaire de fenêtre de bureau effectue la mise à l’échelle par défaut pour toutes les applications qui ne gèrent pas leur propre mise à l’échelle. Les applications clientes UI Automation doivent prendre en compte cette fonctionnalité.  
  
<a name="Scaling_in_Windows_Vista"></a>
## <a name="scaling-in-windows-vista"></a>Mise à l’échelle dans Windows Vista  
 Le réglage par défaut de dpi est 96, ce qui signifie que 96 pixels occupent une largeur ou une hauteur d’un pouce théorique. La mesure exacte d’un « pouce » dépend de la taille et de la résolution physique du moniteur. Par exemple, sur un moniteur d’une largeur de 12 pouces, pour une résolution horizontale de 1 280 pixels, une ligne horizontale de 96 pixels s’étend sur 9/10e de pouce.  
  
 Changer le paramètre dpi n’est pas la même chose que de changer la résolution de l’écran. Avec l’échelle de dpi, le nombre de pixels physiques sur l’écran reste le même. Toutefois, la mise à l’échelle est appliquée à la taille et à l’emplacement des éléments [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] . Cette mise à l’échelle peut être effectuée automatiquement par le Gestionnaire de fenêtrage (DWM, Desktop Window Manager) pour le bureau et pour les applications qui ne demandent pas explicitement à ne pas être mises à l’échelle.  
  
 En effet, lorsque l’utilisateur définit le facteur d’échelle à 120 dpi, un pouce vertical ou horizontal sur l’écran devient plus grand de 25 pour cent. Toutes les dimensions sont ajustées en conséquence. Le décalage d’une fenêtre d’application par rapport aux bords supérieur et gauche de l’écran augmente de 25 %. Si la mise à l’échelle de l’application est activée et que l’application n’est pas consciente [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] des pi,, la taille de la fenêtre augmente dans la même proportion, ainsi que les décalages et les tailles de tous les éléments qu’elle contient.  
  
> [!NOTE]
> Par défaut, le DWM n’effectue pas de mise à l’échelle pour les applications non-dpi-aware lorsque l’utilisateur définit le dpi à 120, mais ne l’effectuer lorsque le dpi est réglé à une valeur personnalisée de 144 ou plus. Toutefois, l’utilisateur peut remplacer le comportement par défaut.  
  
 La mise à l’échelle de l’écran pose de nouveaux défis pour les applications qui sont concernées d’une manière ou d’une autre par les coordonnées d’écran. L’écran contient maintenant deux systèmes de coordonnées : l’un physique et l’autre logique. Les coordonnées physiques d’un point correspondent au décalage réel en pixels par rapport au point d’origine en haut à gauche. Les coordonnées logiques correspondent aux décalages tels qu’ils seraient si les pixels eux-mêmes étaient mis à l’échelle.  
  
 Supposons que vous concevez une boîte de dialogue avec un bouton aux coordonnées (100, 48). Lorsque cette boîte de dialogue est affichée à la dpi par défaut 96, le bouton est situé aux coordonnées physiques de (100, 48). A 120 dpi, il est situé aux coordonnées physiques de (125, 60). Mais les coordonnées logiques sont les mêmes dans n’importe quel réglage dpi: (100, 48).  
  
 Les coordonnées logiques sont importantes, car elles rendent le comportement du système d’exploitation et des applications cohérent quel que soit le réglage dpi. Par exemple, <xref:System.Windows.Forms.Cursor.Position%2A?displayProperty=nameWithType> retourne normalement les coordonnées logiques. Si vous déplacez le curseur sur un élément dans une boîte de dialogue, les mêmes coordonnées sont retournées quel que soit le réglage dpi. Si vous tracez un contrôle à (100, 100), il est attiré par ces coordonnées logiques, et occupera la même position relative à n’importe quel réglage dpi.  
  
<a name="Scaling_in_UI_Automation_Clients"></a>
## <a name="scaling-in-ui-automation-clients"></a>Mise à l’échelle dans les clients UI Automation  
 L’API [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] n’utilise pas de coordonnées logiques. Les méthodes et propriétés suivantes retournent des coordonnées physiques ou les utilisent comme paramètres.  
  
- <xref:System.Windows.Automation.AutomationElement.GetClickablePoint%2A>  
  
- <xref:System.Windows.Automation.AutomationElement.TryGetClickablePoint%2A>  
  
- <xref:System.Windows.Automation.AutomationElement.ClickablePointProperty>  
  
- <xref:System.Windows.Automation.AutomationElement.FromPoint%2A>  
  
- <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.BoundingRectangle%2A>  
  
 Par défaut, une application client UI Automation fonctionnant dans un environnement non-96- dpi ne sera pas en mesure d’obtenir les résultats corrects de ces méthodes et propriétés. Par exemple, comme la position du curseur est exprimée en coordonnées logiques, le client ne peut pas simplement passer ces coordonnées à <xref:System.Windows.Automation.AutomationElement.FromPoint%2A> pour obtenir l’élément situé sous le curseur. En outre, l’application n’est pas en mesure de placer correctement les fenêtres en dehors de sa zone cliente.  
  
 La solution comporte deux parties.  
  
1. Tout d’abord, rendre l’application client dpi-aware. Pour ce faire, appelez la `SetProcessDPIAware` fonction Win32 au démarrage. En code managé, la déclaration suivante rend cette fonction disponible.  
  
     [!code-csharp[Highlighter#101](../../../samples/snippets/csharp/VS_Snippets_Wpf/Highlighter/CSharp/NativeMethods.cs#101)]
     [!code-vb[Highlighter#101](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/Highlighter/VisualBasic/NativeMethods.vb#101)]  
  
     Cette fonction rend l’ensemble du processus dpi-conscient, ce qui signifie que toutes les fenêtres qui appartiennent au processus ne sont pas échelle. Dans [l’échantillon de surligneur](https://github.com/Microsoft/WPF-Samples/tree/master/Accessibility/Highlighter), par exemple, les quatre fenêtres qui composent le rectangle de surbrillance sont situées aux coordonnées physiques obtenues à partir de l’automatisation de l’interface utilisateur, et non les coordonnées logiques. Si l’échantillon n’était pas conscient de l’ipi, le point culminant serait tiré aux coordonnées logiques sur le bureau, ce qui entraînerait un mauvais placement dans un environnement non-96-dpi.  
  
2. Pour obtenir des coordonnées curseurs, appelez `GetPhysicalCursorPos`la fonction Win32 . L’exemple suivant montre comment déclarer et utiliser cette fonction.  
  
     [!code-csharp[UIAClient_snip#185](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAClient_snip/CSharp/ClientForm.cs#185)]
     [!code-vb[UIAClient_snip#185](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAClient_snip/VisualBasic/ClientForm.vb#185)]  
  
> [!CAUTION]
> N’utilisez pas <xref:System.Windows.Forms.Cursor.Position%2A?displayProperty=nameWithType>. Le comportement de cette propriété en dehors des fenêtres clientes dans un environnement à l’échelle n’est pas défini.  
  
 Si votre application effectue une communication transversale directe avec des applications non conscientes de la topi, vous `PhysicalToLogicalPoint` pouvez `LogicalToPhysicalPoint`avoir converti entre les coordonnées logiques et physiques en utilisant les fonctions Win32 et .  
  
## <a name="see-also"></a>Voir aussi

- [Highlighter Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Accessibility/Highlighter)
