---
title: Vue d'ensemble du contrôle MenuStrip (Windows Forms)
ms.date: 03/30/2017
f1_keywords:
- MenuStrip
helpviewer_keywords:
- MenuStrip control [Windows Forms], about MenuStrip control
- menus [Windows Forms], creating
ms.assetid: f45516e5-bf01-4468-b851-d45f4c33c055
ms.openlocfilehash: 46a3a25415db77ee261f5fb1c3bf114b2275a2d4
ms.sourcegitcommit: 8c6426a3d2adff5fbcbe1fed0f28eda718c15351
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/02/2019
ms.locfileid: "68733458"
---
# <a name="menustrip-control-overview-windows-forms"></a>Vue d'ensemble du contrôle MenuStrip (Windows Forms)
Les menus exposent les fonctionnalités à vos utilisateurs en détenant des commandes qui sont regroupées par un thème commun.  
  
 Le <xref:System.Windows.Forms.MenuStrip> contrôle a été introduit dans la version 2,0 du .NET Framework. Avec le <xref:System.Windows.Forms.MenuStrip> contrôle, vous pouvez facilement créer des menus comme ceux qui se trouvent dans Microsoft Office.  
  
 Le <xref:System.Windows.Forms.MenuStrip> contrôle prend en charge l’interface multidocument (MDI) et la fusion de menus, les info-bulles et le dépassement de capacité. Vous pouvez améliorer l’utilisation et la lisibilité de vos menus en ajoutant des touches d’accès rapide, des touches de raccourci, des coches, des images et des barres de séparation.  
  
 Le <xref:System.Windows.Forms.MenuStrip> contrôle remplace et ajoute des fonctionnalités <xref:System.Windows.Forms.MainMenu> au contrôle; Toutefois, le <xref:System.Windows.Forms.MainMenu> contrôle est conservé pour la compatibilité descendante et l’utilisation future si tel est votre choix.  
  
## <a name="ways-to-use-the-menustrip-control"></a>Méthodes d’utilisation du contrôle MenuStrip  
 Utilisez le <xref:System.Windows.Forms.MenuStrip> contrôle pour:  
  
- Créez facilement des menus personnalisés et couramment employés qui prennent en charge les fonctionnalités avancées de mise en page et d’interface utilisateur, telles que le tri et l’alignement de texte et d’image, les opérations glisser-déplacer, MDI, le dépassement de capacité et d’autres modes d’accès aux commandes de menu.  
  
- Prendre en charge l’apparence et le comportement typiques du système d’exploitation.  
  
- Gérez les événements de manière cohérente pour tous les conteneurs et éléments qu’ils contiennent, de la même façon que vous gérez des événements pour d’autres contrôles.  
  
 Le tableau suivant présente certaines propriétés particulièrement importantes de <xref:System.Windows.Forms.MenuStrip> et des classes associées.  
  
|Propriété|Description|  
|--------------|-----------------|  
|<xref:System.Windows.Forms.MenuStrip.MdiWindowListItem%2A>|Obtient ou définit le <xref:System.Windows.Forms.ToolStripMenuItem> utilisé pour afficher une liste de formulaires enfants MDI.|  
|<xref:System.Windows.Forms.ToolStripItem.MergeAction%2A?displayProperty=nameWithType>|Obtient ou définit la manière dont les menus enfants sont fusionnés avec les menus parents dans les applications MDI.|  
|<xref:System.Windows.Forms.ToolStripItem.MergeIndex%2A?displayProperty=nameWithType>|Obtient ou définit la position d’un élément fusionné dans un menu dans les applications MDI.|  
|<xref:System.Windows.Forms.Form.IsMdiContainer%2A?displayProperty=nameWithType>|Obtient ou définit une valeur indiquant si le formulaire est un conteneur de formulaires enfants MDI.|  
|<xref:System.Windows.Forms.MenuStrip.ShowItemToolTips%2A>|Obtient ou définit une valeur indiquant si les info-bulles sont affichées <xref:System.Windows.Forms.MenuStrip>pour le.|  
|<xref:System.Windows.Forms.MenuStrip.CanOverflow%2A>|Obtient ou définit une valeur indiquant si le <xref:System.Windows.Forms.MenuStrip> prend en charge les fonctionnalités de dépassement de capacité.|  
|<xref:System.Windows.Forms.ToolStripMenuItem.ShortcutKeys%2A>|Obtient ou définit les touches de raccourci associées à <xref:System.Windows.Forms.ToolStripMenuItem>.|  
|<xref:System.Windows.Forms.ToolStripMenuItem.ShowShortcutKeys%2A>|Obtient ou définit une valeur qui indique si les touches de raccourci associées à <xref:System.Windows.Forms.ToolStripMenuItem> sont affichées en regard de <xref:System.Windows.Forms.ToolStripMenuItem>.|  
  
 Le tableau suivant présente les classes <xref:System.Windows.Forms.MenuStrip> auxiliaires importantes.  
  
|Classe|Description|  
|-----------|-----------------|  
|<xref:System.Windows.Forms.ToolStripMenuItem>|Représente une option pouvant être sélectionnée, qui est affichée sur un <xref:System.Windows.Forms.MenuStrip> ou un <xref:System.Windows.Forms.ContextMenuStrip>.|  
|<xref:System.Windows.Forms.ContextMenuStrip>|Représente un menu contextuel.|  
|<xref:System.Windows.Forms.ToolStripDropDown>|Représente un contrôle qui permet à l’utilisateur de sélectionner un élément unique dans une liste qui s’affiche lorsque l’utilisateur clique sur un <xref:System.Windows.Forms.ToolStripDropDownButton> ou un élément de menu de niveau supérieur.|  
|<xref:System.Windows.Forms.ToolStripDropDownItem>|Fournit des fonctionnalités de base pour les <xref:System.Windows.Forms.ToolStripItem> contrôles dérivés de qui affichent des éléments déroulants lorsque l’utilisateur clique dessus.|  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Forms.ToolStrip>
- <xref:System.Windows.Forms.MenuStrip>
- <xref:System.Windows.Forms.ContextMenuStrip>
- <xref:System.Windows.Forms.StatusStrip>
- <xref:System.Windows.Forms.ToolStripItem>
- <xref:System.Windows.Forms.ToolStripDropDown>
