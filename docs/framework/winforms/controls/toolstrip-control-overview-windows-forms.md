---
title: Vue d'ensemble du contrôle ToolStrip
ms.date: 03/30/2017
f1_keywords:
- Toolstrip
helpviewer_keywords:
- ToolStrip control [Windows Forms], about ToolStrip control
- toolbars [Windows Forms], what's new in Windows Forms
- toolbars [Windows Forms]
- what's new [Windows Forms], toolbars
ms.assetid: 81d067ed-297c-4dad-90de-1bcac15336ec
ms.openlocfilehash: 931a6a0ea09f9b684b793c05cb1c3db8ee8fb7c7
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76741080"
---
# <a name="toolstrip-control-overview-windows-forms"></a>Vue d'ensemble du contrôle ToolStrip (Windows Forms)
Le contrôle Windows Forms <xref:System.Windows.Forms.ToolStrip> et ses classes associées fournissent un Framework commun pour combiner des éléments d’interface utilisateur dans des barres d’outils, des barres d’État et des menus. les contrôles <xref:System.Windows.Forms.ToolStrip> offrent une expérience de conception riche qui comprend l’activation et la modification sur place, la disposition personnalisée et le rafting, qui est la capacité des barres d’outils à partager l’espace horizontal ou vertical.  
  
 Bien que <xref:System.Windows.Forms.ToolStrip> remplace et ajoute des fonctionnalités au contrôle dans les versions précédentes, <xref:System.Windows.Forms.ToolBar> est conservé pour la compatibilité descendante et l’utilisation future si vous le souhaitez.  
  
## <a name="features-of-the-toolstrip-controls"></a>Fonctionnalités des contrôles ToolStrip  
 Utilisez le contrôle <xref:System.Windows.Forms.ToolStrip> pour :  
  
- Présenter une interface utilisateur commune à travers les conteneurs.  
  
- Créez facilement des barres d’outils personnalisées et utilisées couramment, qui prennent en charge des fonctionnalités d’interface utilisateur et de disposition avancées, telles que l’ancrage, le rafting, les boutons avec texte et images, les boutons et les contrôles déroulants, les boutons de dépassement de capacité et la réorganisation des éléments de <xref:System.Windows.Forms.ToolStrip> au moment de l’exécution.  
  
- Prendre en charge la réorganisation des éléments de dépassement de capacité et d’exécution. La fonctionnalité de dépassement de capacité déplace les éléments dans un menu déroulant lorsqu’il n’y a pas assez de place pour les afficher dans un <xref:System.Windows.Forms.ToolStrip>.  
  
- Prendre en charge l’apparence et le comportement typiques du système d’exploitation via un modèle de rendu commun.  
  
- Gérez les événements de manière cohérente pour tous les conteneurs et éléments qu’ils contiennent, de la même façon que vous gérez des événements pour d’autres contrôles.  
  
- Faire glisser des éléments d’un <xref:System.Windows.Forms.ToolStrip> vers un autre ou au sein d’un <xref:System.Windows.Forms.ToolStrip>.  
  
- Créer des contrôles déroulants et des éditeurs de type d’interface utilisateur avec des dispositions avancées dans une <xref:System.Windows.Forms.ToolStripDropDown>.  
  
 Utilisez la classe <xref:System.Windows.Forms.ToolStripControlHost> pour utiliser d’autres contrôles sur un <xref:System.Windows.Forms.ToolStrip> et obtenir <xref:System.Windows.Forms.ToolStrip> fonctionnalités correspondantes.  
  
 Vous pouvez étendre les fonctionnalités et modifier l’apparence et le comportement à l’aide de l' <xref:System.Windows.Forms.ToolStripRenderer>, <xref:System.Windows.Forms.ToolStripProfessionalRenderer>et <xref:System.Windows.Forms.ToolStripManager> avec les énumérations <xref:System.Windows.Forms.ToolStripRenderMode> et <xref:System.Windows.Forms.ToolStripManagerRenderMode>.  
  
 Le contrôle <xref:System.Windows.Forms.ToolStrip> est hautement configurable et extensible, et fournit de nombreuses propriétés, méthodes et événements pour personnaliser l’apparence et le comportement. Voici quelques-uns des membres importants :  
  
### <a name="important-toolstrip-members"></a>Membres de ToolStrip importants  
  
|Nom|Description|  
|----------|-----------------|  
|<xref:System.Windows.Forms.ToolStrip.Dock%2A>|Obtient ou définit le bord du conteneur parent auquel un <xref:System.Windows.Forms.ToolStrip> est ancré.|  
|<xref:System.Windows.Forms.ToolStrip.AllowItemReorder%2A>|Obtient ou définit une valeur qui indique si des opérations de glisser-déplacer et de réorganisation d'éléments sont traitées en privé par la classe <xref:System.Windows.Forms.ToolStrip>.|  
|<xref:System.Windows.Forms.ToolStrip.LayoutStyle%2A>|Obtient ou définit une valeur indiquant comment le <xref:System.Windows.Forms.ToolStrip> dispose ses éléments.|  
|<xref:System.Windows.Forms.ToolStripItem.Overflow%2A>|Obtient ou définit une valeur indiquant si une <xref:System.Windows.Forms.ToolStripItem> est attachée au <xref:System.Windows.Forms.ToolStrip> ou <xref:System.Windows.Forms.ToolStripOverflowButton> ou peut flotter entre les deux.|  
|<xref:System.Windows.Forms.ToolStrip.IsDropDown%2A>|Obtient une valeur indiquant si un <xref:System.Windows.Forms.ToolStripItem> affiche d’autres éléments dans une liste déroulante lorsque l’utilisateur clique sur le <xref:System.Windows.Forms.ToolStripItem>.|  
|<xref:System.Windows.Forms.ToolStrip.OverflowButton%2A>|Obtient le <xref:System.Windows.Forms.ToolStripItem>, qui correspond au bouton de dépassement de capacité pour un <xref:System.Windows.Forms.ToolStrip> avec dépassement de capacité activé.|  
|<xref:System.Windows.Forms.ToolStrip.Renderer%2A>|Obtient ou définit un <xref:System.Windows.Forms.ToolStripRenderer> utilisé pour personnaliser l’apparence et le comportement (apparence) d’un <xref:System.Windows.Forms.ToolStrip>.|  
|<xref:System.Windows.Forms.ToolStrip.RenderMode%2A>|Obtient ou définit les styles de peinture à appliquer à <xref:System.Windows.Forms.ToolStrip>.|  
|<xref:System.Windows.Forms.ToolStrip.RendererChanged>|Déclenché en cas de modification de la propriété <xref:System.Windows.Forms.ToolStrip.Renderer%2A>.|  
  
 La flexibilité du contrôle de <xref:System.Windows.Forms.ToolStrip> est obtenue à l’aide d’un certain nombre de classes auxiliaires. Voici quelques-unes des plus intéressantes :  
  
### <a name="important-toolstrip-companion-classes"></a>Classes auxiliaires ToolStrip importantes  
  
|Nom|Description|  
|----------|-----------------|  
|<xref:System.Windows.Forms.MenuStrip>|Remplace et ajoute des fonctionnalités à la classe <xref:System.Windows.Forms.MainMenu>.|  
|<xref:System.Windows.Forms.StatusStrip>|Remplace et ajoute des fonctionnalités à la classe <xref:System.Windows.Forms.StatusBar>.|  
|<xref:System.Windows.Forms.ContextMenuStrip>|Remplace et ajoute des fonctionnalités à la classe <xref:System.Windows.Forms.ContextMenu>.|  
|<xref:System.Windows.Forms.ToolStripItem>|Classe de base abstraite qui gère les événements et la disposition pour tous les éléments qu’un <xref:System.Windows.Forms.ToolStrip>, <xref:System.Windows.Forms.ToolStripControlHost>ou <xref:System.Windows.Forms.ToolStripDropDown> peut contenir.|  
|<xref:System.Windows.Forms.ToolStripContainer>|Fournit un conteneur avec un panneau sur chaque côté du formulaire dans lequel les contrôles peuvent être organisés de différentes façons.|  
|<xref:System.Windows.Forms.ToolStripRenderer>|Gère la fonctionnalité de peinture pour les objets <xref:System.Windows.Forms.ToolStrip>.|  
|<xref:System.Windows.Forms.ToolStripProfessionalRenderer>|Fournit une apparence de style Microsoft Office.|  
|<xref:System.Windows.Forms.ToolStripManager>|Contrôle <xref:System.Windows.Forms.ToolStrip> le rendu et le rafting et la fusion des objets <xref:System.Windows.Forms.MenuStrip>, <xref:System.Windows.Forms.ToolStripDropDownMenu> et <xref:System.Windows.Forms.ToolStripMenuItem>.|  
|<xref:System.Windows.Forms.ToolStripManagerRenderMode>|Spécifie le style de peinture (personnalisé, Windows XP ou Microsoft Office Professionnel) appliqué à plusieurs objets <xref:System.Windows.Forms.ToolStrip> contenus dans un formulaire.|  
|<xref:System.Windows.Forms.ToolStripRenderMode>|Spécifie le style de peinture (personnalisé, Windows XP ou Microsoft Office Professionnel) appliqué à un objet <xref:System.Windows.Forms.ToolStrip> contenu dans un formulaire.|  
|<xref:System.Windows.Forms.ToolStripControlHost>|Héberge d’autres contrôles qui ne sont pas spécifiquement <xref:System.Windows.Forms.ToolStrip> contrôles, mais pour lesquels vous souhaitez <xref:System.Windows.Forms.ToolStrip> fonctionnalité.|  
|<xref:System.Windows.Forms.ToolStripItemPlacement>|Spécifie si un <xref:System.Windows.Forms.ToolStripItem> doit être disposé sur le <xref:System.Windows.Forms.ToolStrip>principal, sur le <xref:System.Windows.Forms.ToolStrip>de dépassement de capacité, ou aucun des trois.|  
  
 Pour plus d’informations, consultez Résumé de la [technologie ToolStrip](toolstrip-technology-summary.md) et [architecture du contrôle ToolStrip](toolstrip-control-architecture.md).  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Forms.ToolStrip>
- <xref:System.Windows.Forms.MenuStrip>
- <xref:System.Windows.Forms.ContextMenuStrip>
- <xref:System.Windows.Forms.StatusStrip>
- <xref:System.Windows.Forms.ToolStripItem>
- <xref:System.Windows.Forms.ToolStripDropDown>
