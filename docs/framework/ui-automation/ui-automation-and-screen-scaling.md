---
title: Mise à l'échelle de l'écran et UI Automation
description: Découvrez comment Windows et UI Automation gèrent la mise à l’échelle de l’écran. DWM effectue une mise à l’échelle par défaut pour toutes les applications, que les applications clientes UI Automation doivent prendre en compte.
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
ms.openlocfilehash: 99239d7bac2e556d4da0d74f36c68916da7c688a
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/24/2020
ms.locfileid: "87164013"
---
# <a name="ui-automation-and-screen-scaling"></a>Mise à l'échelle de l'écran et UI Automation
> [!NOTE]
> Cette documentation s'adresse aux développeurs .NET Framework qui souhaitent utiliser les classes [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] managées définies dans l'espace de noms <xref:System.Windows.Automation>. Pour obtenir les dernières informations sur [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], consultez [API Windows Automation : UI Automation](/windows/win32/winauto/entry-uiauto-win32).  
  
À compter de Windows Vista, Windows permet aux utilisateurs de modifier le paramètre points par pouce (dpi) afin que la plupart des éléments de l’interface utilisateur de l’écran apparaissent plus grands. Bien que cette fonctionnalité soit disponible dans Windows, dans les versions précédentes, la mise à l’échelle devait être implémentée par les applications. À compter de Windows Vista, la Gestionnaire de fenêtrage effectue une mise à l’échelle par défaut pour toutes les applications qui ne gèrent pas leur propre mise à l’échelle. Les applications clientes UI Automation doivent prendre en compte cette fonctionnalité.  
  
<a name="Scaling_in_Windows_Vista"></a>
## <a name="scaling-in-windows-vista"></a>Mise à l’échelle dans Windows Vista  
 Le paramètre PPP par défaut est 96, ce qui signifie que 96 pixels occupent la largeur ou la hauteur d’un pouce notionnel. La mesure exacte d’un « pouce » dépend de la taille et de la résolution physique du moniteur. Par exemple, sur un moniteur d’une largeur de 12 pouces, pour une résolution horizontale de 1 280 pixels, une ligne horizontale de 96 pixels s’étend sur 9/10e de pouce.  
  
 La modification du paramètre PPP n’est pas la même que la modification de la résolution de l’écran. Avec la mise à l’échelle PPP, le nombre de pixels physiques sur l’écran reste le même. Toutefois, la mise à l’échelle est appliquée à la taille et à l’emplacement des éléments [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] . Cette mise à l’échelle peut être effectuée automatiquement par le Gestionnaire de fenêtrage (DWM, Desktop Window Manager) pour le bureau et pour les applications qui ne demandent pas explicitement à ne pas être mises à l’échelle.  
  
 En effet, lorsque l’utilisateur définit le facteur d’échelle sur 120 ppp, un pouce vertical ou horizontal sur l’écran augmente de 25%. Toutes les dimensions sont ajustées en conséquence. Le décalage d’une fenêtre d’application par rapport aux bords supérieur et gauche de l’écran augmente de 25 %. Si la mise à l’échelle de l’application est activée et que l’application n’a pas de prise en charge dpi, la taille de la fenêtre augmente dans la même proportion, avec les décalages et les tailles de tous les [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] éléments qu’elle contient.  
  
> [!NOTE]
> Par défaut, le DWM n’effectue pas de mise à l’échelle pour les applications qui ne prennent pas en charge DPI lorsque l’utilisateur définit la valeur PPP sur 120, mais l’exécute lorsque la valeur PPP est définie sur une valeur personnalisée 144 ou supérieure. Toutefois, l’utilisateur peut remplacer le comportement par défaut.  
  
 La mise à l’échelle de l’écran pose de nouveaux défis pour les applications qui sont concernées d’une manière ou d’une autre par les coordonnées d’écran. L’écran contient maintenant deux systèmes de coordonnées : l’un physique et l’autre logique. Les coordonnées physiques d’un point correspondent au décalage réel en pixels par rapport au point d’origine en haut à gauche. Les coordonnées logiques correspondent aux décalages tels qu’ils seraient si les pixels eux-mêmes étaient mis à l’échelle.  
  
 Supposons que vous concevez une boîte de dialogue avec un bouton aux coordonnées (100, 48). Lorsque cette boîte de dialogue est affichée avec la valeur par défaut de 96 dpi, le bouton se trouve aux coordonnées physiques de (100, 48). À 120 ppp, il se trouve aux coordonnées physiques de (125, 60). Toutefois, les coordonnées logiques sont les mêmes à n’importe quel paramètre PPP : (100, 48).  
  
 Les coordonnées logiques sont importantes, car elles rendent cohérent le comportement du système d’exploitation et des applications quel que soit le paramètre PPP. Par exemple, <xref:System.Windows.Forms.Cursor.Position%2A?displayProperty=nameWithType> retourne normalement les coordonnées logiques. Si vous déplacez le curseur sur un élément dans une boîte de dialogue, les mêmes coordonnées sont retournées quel que soit le paramètre PPP. Si vous dessinez un contrôle à l’emplacement (100, 100), il est dessiné à ces coordonnées logiques et occupera la même position relative à n’importe quel paramètre PPP.  
  
<a name="Scaling_in_UI_Automation_Clients"></a>
## <a name="scaling-in-ui-automation-clients"></a>Mise à l’échelle dans les clients UI Automation  
 L' [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] API n’utilise pas de coordonnées logiques. Les méthodes et propriétés suivantes retournent des coordonnées physiques ou les utilisent comme paramètres.  
  
- <xref:System.Windows.Automation.AutomationElement.GetClickablePoint%2A>  
  
- <xref:System.Windows.Automation.AutomationElement.TryGetClickablePoint%2A>  
  
- <xref:System.Windows.Automation.AutomationElement.ClickablePointProperty>  
  
- <xref:System.Windows.Automation.AutomationElement.FromPoint%2A>  
  
- <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.BoundingRectangle%2A>  
  
 Par défaut, une application cliente UI Automation en cours d’exécution dans un environnement autre que 96 ppp ne peut pas obtenir les résultats corrects à partir de ces méthodes et propriétés. Par exemple, comme la position du curseur est exprimée en coordonnées logiques, le client ne peut pas simplement passer ces coordonnées à <xref:System.Windows.Automation.AutomationElement.FromPoint%2A> pour obtenir l’élément situé sous le curseur. En outre, l’application n’est pas en mesure de placer correctement les fenêtres en dehors de sa zone cliente.  
  
 La solution comporte deux parties.  
  
1. Tout d’abord, assurez-vous que l’application cliente prend en charge dpi. Pour ce faire, appelez la fonction Win32 `SetProcessDPIAware` au démarrage. En code managé, la déclaration suivante rend cette fonction disponible.  
  
     [!code-csharp[Highlighter#101](../../../samples/snippets/csharp/VS_Snippets_Wpf/Highlighter/CSharp/NativeMethods.cs#101)]
     [!code-vb[Highlighter#101](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/Highlighter/VisualBasic/NativeMethods.vb#101)]  
  
     Cette fonction rend la prise en charge DPI du processus entier, ce qui signifie que toutes les fenêtres qui appartiennent au processus ne sont pas mises à l’échelle. Dans l' [exemple de surligneur](https://github.com/Microsoft/WPF-Samples/tree/master/Accessibility/Highlighter), par exemple, les quatre fenêtres qui composent le rectangle de surbrillance sont situées aux coordonnées physiques obtenues à partir d’UI Automation, et non aux coordonnées logiques. Si l’exemple n’a pas de prise en charge dpi, la mise en surbrillance serait dessinée aux coordonnées logiques sur le bureau, ce qui entraînerait un positionnement incorrect dans un environnement non-96 ppp.  
  
2. Pour connaître les coordonnées du curseur, appelez la fonction Win32 `GetPhysicalCursorPos` . L’exemple suivant montre comment déclarer et utiliser cette fonction.  
  
     [!code-csharp[UIAClient_snip#185](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAClient_snip/CSharp/ClientForm.cs#185)]
     [!code-vb[UIAClient_snip#185](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAClient_snip/VisualBasic/ClientForm.vb#185)]  
  
> [!CAUTION]
> N’utilisez pas <xref:System.Windows.Forms.Cursor.Position%2A?displayProperty=nameWithType>. Le comportement de cette propriété en dehors des fenêtres clientes dans un environnement à l’échelle n’est pas défini.  
  
 Si votre application effectue une communication interprocessus directe avec des applications qui ne prennent pas en charge dpi, vous pouvez effectuer une conversion entre les coordonnées logiques et physiques à l’aide des fonctions Win32 `PhysicalToLogicalPoint` et `LogicalToPhysicalPoint` .  
  
## <a name="see-also"></a>Voir aussi

- [Highlighter Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Accessibility/Highlighter)
