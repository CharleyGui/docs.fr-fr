---
title: Vue d'ensemble du contrôle MenuStrip (Windows Forms)
ms.date: 03/30/2017
f1_keywords:
- MenuStrip
helpviewer_keywords:
- MenuStrip control [Windows Forms], about MenuStrip control
- menus [Windows Forms], creating
ms.assetid: f45516e5-bf01-4468-b851-d45f4c33c055
ms.openlocfilehash: b72fcf75aeebc297d09cbaa9dbf00bb2370b1222
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64625766"
---
# <a name="menustrip-control-overview-windows-forms"></a>Vue d'ensemble du contrôle MenuStrip (Windows Forms)
Menus exposent des fonctionnalités à vos utilisateurs en maintenant les commandes regroupées par un thème commun.  
  
 Le <xref:System.Windows.Forms.MenuStrip> contrôle est une nouveauté de cette version de Visual Studio et .NET Framework. Avec le contrôle, vous pouvez créer facilement des menus, telles que celles dans Microsoft Office.  
  
 Le <xref:System.Windows.Forms.MenuStrip> contrôle prend en charge l’interface multidocument (MDI) et que la fusion de menus, les info-bulles et le dépassement de capacité. Vous pouvez améliorer la facilité d’utilisation et la lisibilité de vos menus en ajoutant des clés d’accès, des touches de raccourci, des coches, des images et des barres de séparation.  
  
 Le <xref:System.Windows.Forms.MenuStrip> contrôle remplace et ajoute des fonctionnalités à la <xref:System.Windows.Forms.MainMenu> contrôler ; Toutefois, le <xref:System.Windows.Forms.MainMenu> contrôle est conservé pour la compatibilité descendante et l’utilisation future si vous choisissez.  
  
## <a name="ways-to-use-the-menustrip-control"></a>Façons d’utiliser le contrôle MenuStrip  
 Utilisez le <xref:System.Windows.Forms.MenuStrip> le contrôle à :  
  
- Créez facilement personnalisées, employées couramment menus qui prennent en charge utilisateur interface et mise en page fonctionnalités avancées, telles que texte et image classement et alignement, les opérations de glisser-déplacer, MDI, dépassement de capacité et autres modes d’accès aux commandes de menu.  
  
- Prend en charge l’apparence classique et le comportement du système d’exploitation.  
  
- Gérer les événements cohérente pour tous les conteneurs et les éléments de contenu, de la même façon que vous gérez des événements pour d’autres contrôles.  
  
 Le tableau suivant présente certaines propriétés particulièrement importantes de <xref:System.Windows.Forms.MenuStrip> et des classes associées.  
  
|Propriété|Description|  
|--------------|-----------------|  
|<xref:System.Windows.Forms.MenuStrip.MdiWindowListItem%2A>|Obtient ou définit le <xref:System.Windows.Forms.ToolStripMenuItem> qui est utilisé pour afficher une liste des formulaires enfants MDI.|  
|<xref:System.Windows.Forms.ToolStripItem.MergeAction%2A?displayProperty=nameWithType>|Obtient ou définit comment les menus enfants sont fusionnés avec les menus parents dans les applications MDI.|  
|<xref:System.Windows.Forms.ToolStripItem.MergeIndex%2A?displayProperty=nameWithType>|Obtient ou définit la position d’un élément fusionné dans un menu dans les applications MDI.|  
|<xref:System.Windows.Forms.Form.IsMdiContainer%2A?displayProperty=nameWithType>|Obtient ou définit une valeur indiquant si le formulaire est un conteneur de formulaires enfants MDI.|  
|<xref:System.Windows.Forms.MenuStrip.ShowItemToolTips%2A>|Obtient ou définit une valeur indiquant si les info-bulles sont indiquées pour le <xref:System.Windows.Forms.MenuStrip>.|  
|<xref:System.Windows.Forms.MenuStrip.CanOverflow%2A>|Obtient ou définit une valeur indiquant si le <xref:System.Windows.Forms.MenuStrip> prend en charge les fonctionnalités de dépassement de capacité.|  
|<xref:System.Windows.Forms.ToolStripMenuItem.ShortcutKeys%2A>|Obtient ou définit les touches de raccourci associées à <xref:System.Windows.Forms.ToolStripMenuItem>.|  
|<xref:System.Windows.Forms.ToolStripMenuItem.ShowShortcutKeys%2A>|Obtient ou définit une valeur qui indique si les touches de raccourci associées à <xref:System.Windows.Forms.ToolStripMenuItem> sont affichées en regard de <xref:System.Windows.Forms.ToolStripMenuItem>.|  
  
 Le tableau suivant présente les importantes <xref:System.Windows.Forms.MenuStrip> classes auxiliaires.  
  
|Classe|Description|  
|-----------|-----------------|  
|<xref:System.Windows.Forms.ToolStripMenuItem>|Représente une option pouvant être sélectionnée, qui est affichée sur un <xref:System.Windows.Forms.MenuStrip> ou un <xref:System.Windows.Forms.ContextMenuStrip>.|  
|<xref:System.Windows.Forms.ContextMenuStrip>|Représente un menu contextuel.|  
|<xref:System.Windows.Forms.ToolStripDropDown>|Représente un contrôle qui permet à l’utilisateur de sélectionner un élément unique dans une liste qui s’affiche lorsque l’utilisateur clique sur un <xref:System.Windows.Forms.ToolStripDropDownButton> ou un élément de menu de niveau supérieur.|  
|<xref:System.Windows.Forms.ToolStripDropDownItem>|Fournit des fonctionnalités de base pour les contrôles dérivés de <xref:System.Windows.Forms.ToolStripItem> qui affichent des éléments de liste déroulante lorsque vous cliquez sur.|  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Forms.ToolStrip>
- <xref:System.Windows.Forms.MenuStrip>
- <xref:System.Windows.Forms.ContextMenuStrip>
- <xref:System.Windows.Forms.StatusStrip>
- <xref:System.Windows.Forms.ToolStripItem>
- <xref:System.Windows.Forms.ToolStripDropDown>
