---
title: Vue d'ensemble du contrôle MenuStrip
ms.date: 03/30/2017
f1_keywords:
- MenuStrip
helpviewer_keywords:
- MenuStrip control [Windows Forms], about MenuStrip control
- menus [Windows Forms], creating
ms.assetid: f45516e5-bf01-4468-b851-d45f4c33c055
ms.openlocfilehash: a536d13cb7be3f4e4e4a085e1a4da1b0899b3a0c
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76734471"
---
# <a name="menustrip-control-overview-windows-forms"></a>Vue d'ensemble du contrôle MenuStrip (Windows Forms)
Les menus exposent les fonctionnalités à vos utilisateurs en détenant des commandes qui sont regroupées par un thème commun.  
  
 Le contrôle de <xref:System.Windows.Forms.MenuStrip> a été introduit dans la version 2,0 du .NET Framework. Avec le contrôle <xref:System.Windows.Forms.MenuStrip>, vous pouvez facilement créer des menus comme ceux qui se trouvent dans Microsoft Office.  
  
 Le contrôle <xref:System.Windows.Forms.MenuStrip> prend en charge l’interface multidocument (MDI) et la fusion de menus, les info-bulles et le dépassement de capacité. Vous pouvez améliorer l’utilisation et la lisibilité de vos menus en ajoutant des touches d’accès rapide, des touches de raccourci, des coches, des images et des barres de séparation.  
  
 Le contrôle <xref:System.Windows.Forms.MenuStrip> remplace et ajoute des fonctionnalités au contrôle <xref:System.Windows.Forms.MainMenu> ; Toutefois, le contrôle de <xref:System.Windows.Forms.MainMenu> est conservé pour la compatibilité descendante et l’utilisation future si vous le souhaitez.  
  
## <a name="ways-to-use-the-menustrip-control"></a>Méthodes d’utilisation du contrôle MenuStrip  
 Utilisez le contrôle <xref:System.Windows.Forms.MenuStrip> pour :  
  
- Créez facilement des menus personnalisés et couramment employés qui prennent en charge les fonctionnalités avancées de mise en page et d’interface utilisateur, telles que le tri et l’alignement de texte et d’image, les opérations glisser-déplacer, MDI, le dépassement de capacité et d’autres modes d’accès aux commandes de menu.  
  
- Prendre en charge l’apparence et le comportement typiques du système d’exploitation.  
  
- Gérez les événements de manière cohérente pour tous les conteneurs et éléments qu’ils contiennent, de la même façon que vous gérez des événements pour d’autres contrôles.  
  
 Le tableau suivant présente certaines propriétés particulièrement importantes des <xref:System.Windows.Forms.MenuStrip> et des classes associées.  
  
|Propriété|Description|  
|--------------|-----------------|  
|<xref:System.Windows.Forms.MenuStrip.MdiWindowListItem%2A>|Obtient ou définit le <xref:System.Windows.Forms.ToolStripMenuItem> utilisé pour afficher une liste de formulaires enfants MDI.|  
|<xref:System.Windows.Forms.ToolStripItem.MergeAction%2A?displayProperty=nameWithType>|Obtient ou définit la manière dont les menus enfants sont fusionnés avec les menus parents dans les applications MDI.|  
|<xref:System.Windows.Forms.ToolStripItem.MergeIndex%2A?displayProperty=nameWithType>|Obtient ou définit la position d’un élément fusionné dans un menu dans les applications MDI.|  
|<xref:System.Windows.Forms.Form.IsMdiContainer%2A?displayProperty=nameWithType>|Obtient ou définit une valeur indiquant si le formulaire est un conteneur de formulaires enfants MDI.|  
|<xref:System.Windows.Forms.MenuStrip.ShowItemToolTips%2A>|Obtient ou définit une valeur indiquant si les info-bulles sont affichées pour le <xref:System.Windows.Forms.MenuStrip>.|  
|<xref:System.Windows.Forms.MenuStrip.CanOverflow%2A>|Obtient ou définit une valeur indiquant si le <xref:System.Windows.Forms.MenuStrip> prend en charge les fonctionnalités de dépassement de capacité.|  
|<xref:System.Windows.Forms.ToolStripMenuItem.ShortcutKeys%2A>|Obtient ou définit les touches de raccourci associées à <xref:System.Windows.Forms.ToolStripMenuItem>.|  
|<xref:System.Windows.Forms.ToolStripMenuItem.ShowShortcutKeys%2A>|Obtient ou définit une valeur qui indique si les touches de raccourci associées à <xref:System.Windows.Forms.ToolStripMenuItem> sont affichées en regard de <xref:System.Windows.Forms.ToolStripMenuItem>.|  
  
 Le tableau suivant présente les principales classes auxiliaires <xref:System.Windows.Forms.MenuStrip>.  
  
|Class|Description|  
|-----------|-----------------|  
|<xref:System.Windows.Forms.ToolStripMenuItem>|Représente une option pouvant être sélectionnée, qui est affichée sur un <xref:System.Windows.Forms.MenuStrip> ou un <xref:System.Windows.Forms.ContextMenuStrip>.|  
|<xref:System.Windows.Forms.ContextMenuStrip>|Représente un menu contextuel.|  
|<xref:System.Windows.Forms.ToolStripDropDown>|Représente un contrôle qui permet à l’utilisateur de sélectionner un élément unique dans une liste qui s’affiche lorsque l’utilisateur clique sur un <xref:System.Windows.Forms.ToolStripDropDownButton> ou sur un élément de menu de niveau supérieur.|  
|<xref:System.Windows.Forms.ToolStripDropDownItem>|Fournit des fonctionnalités de base pour les contrôles dérivés de <xref:System.Windows.Forms.ToolStripItem> qui affichent des éléments déroulants lorsque l’utilisateur clique dessus.|  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Forms.ToolStrip>
- <xref:System.Windows.Forms.MenuStrip>
- <xref:System.Windows.Forms.ContextMenuStrip>
- <xref:System.Windows.Forms.StatusStrip>
- <xref:System.Windows.Forms.ToolStripItem>
- <xref:System.Windows.Forms.ToolStripDropDown>
