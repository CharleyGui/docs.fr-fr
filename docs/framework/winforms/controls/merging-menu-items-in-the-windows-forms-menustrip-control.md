---
title: Fusion d'éléments de menu dans le contrôle MenuStrip Windows Forms
ms.date: 03/30/2017
helpviewer_keywords:
- MenuStrip [Windows Forms], merging
- merging [Windows Forms], general concepts
ms.assetid: 95e113ba-f362-4dda-8a76-6d95ddc45cee
ms.openlocfilehash: 9a1f59a065faaa3a08a9d8a68973adb1faa5ed09
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64582931"
---
# <a name="merging-menu-items-in-the-windows-forms-menustrip-control"></a>Fusion d'éléments de menu dans le contrôle MenuStrip Windows Forms
Si vous avez une application d’interface multidocument (MDI), vous pouvez fusionner des éléments de menu ou des menus entiers à partir du formulaire enfant dans les menus du formulaire parent.  
  
 Cette rubrique décrit les concepts de base associés à la fusion d’éléments de menu dans une application MDI.  
  
## <a name="general-concepts"></a>Concepts généraux  
 Procédures de fusion impliquent une cible et un contrôle de code source :  
  
- La cible est le <xref:System.Windows.Forms.MenuStrip> contrôle sur le principal ou le formulaire MDI parent dans lequel vous fusionnez des éléments de menu.  
  
- La source est le <xref:System.Windows.Forms.MenuStrip> contrôle sur le formulaire enfant MDI qui contient les éléments de menu à fusionner dans le menu cible.  
  
 Le <xref:System.Windows.Forms.MenuStrip.MdiWindowListItem%2A> propriété identifie l’élément de menu dont vous remplissez avec les titres de l’interface MDI en cours de la liste déroulante parente enfants MDI du formulaire. Par exemple, vous répertoriez en général les enfants MDI qui sont actuellement ouverts sur le **fenêtre** menu.  
  
 Le <xref:System.Windows.Forms.ToolStripMenuItem.IsMdiWindowListEntry%2A> propriété identifie les éléments de menu proviennent d’un <xref:System.Windows.Forms.MenuStrip> sur un formulaire enfant MDI.  
  
 Vous pouvez fusionner des éléments de menu manuellement ou automatiquement. Les éléments de menu de fusion de la même façon pour les deux méthodes, mais la fusion est activée différemment, comme indiqué dans les sections « Fusion manuelle » et « Fusion automatique » plus loin dans cette rubrique. Manuel et automatique de fusion, de chaque action de fusion affecte l’action de fusion suivante.  
  
 <xref:System.Windows.Forms.MenuStrip> fusion déplace des éléments de menu à partir d’un <xref:System.Windows.Forms.ToolStrip> à l’autre plutôt que de les cloner, comme c’était le cas avec <xref:System.Windows.Forms.MainMenu>.  
  
## <a name="mergeaction-values"></a>Valeurs MergeAction  
 Vous définissez l’action de fusion sur les éléments de menu dans la source <xref:System.Windows.Forms.MenuStrip> à l’aide de la <xref:System.Windows.Forms.MergeAction> propriété.  
  
 Le tableau suivant décrit l’utilisation classique et ce qui signifie que des actions de fusion disponibles.  
  
|Valeur MergeAction|Description|Utilisation courante|  
|-----------------------|-----------------|-----------------|  
|<xref:System.Windows.Forms.MergeAction.Append>|(Valeur par défaut) Ajoute l’élément source à la fin de la collection de l’élément cible.|Ajout d’éléments de menu à la fin du menu lorsqu’une partie du programme est activée.|  
|<xref:System.Windows.Forms.MergeAction.Insert>|Ajoute l’élément source à la collection de l’élément cible, à l’emplacement spécifié par le <xref:System.Windows.Forms.ToolStripItem.MergeIndex%2A> propriété définie sur l’élément source.|Ajout d’éléments de menu au milieu ou le début du menu lorsqu’une partie du programme est activée.<br /><br /> Si la valeur de <xref:System.Windows.Forms.ToolStripItem.MergeIndex%2A> est le même pour les deux éléments de menu, ils sont ajoutés dans l’ordre inverse. Définissez <xref:System.Windows.Forms.ToolStripItem.MergeIndex%2A> en conséquence pour conserver l’ordre d’origine.|  
|<xref:System.Windows.Forms.MergeAction.Replace>|Recherche une correspondance de texte, ou utilise le <xref:System.Windows.Forms.ToolStripItem.MergeIndex%2A> valeur si aucune correspondance de texte est trouvé, puis remplace l’élément de menu cible correspondant par l’élément de menu source.|Remplacement d’un élément de menu cible avec un élément de menu source du même nom qui fait quelque chose de différent.|  
|<xref:System.Windows.Forms.MergeAction.MatchOnly>|Recherche une correspondance de texte, ou utilise le <xref:System.Windows.Forms.ToolStripItem.MergeIndex%2A> valeur si aucune correspondance de texte est trouvé, puis ajoute tous les éléments de liste déroulante à partir de la source à la cible.|Création d’une structure de menu qui insère ou ajoute des éléments de menu dans un sous-menu ou supprime des éléments de menu à partir d’un sous-menu. Par exemple, vous pouvez ajouter un élément de menu à partir d’un enfant MDI à un principal <xref:System.Windows.Forms.MenuStrip> **Enregistrer sous** menu.<br /><br /> <xref:System.Windows.Forms.MergeAction.MatchOnly> vous permet de naviguer dans la structure de menu sans effectuer aucune action. Il fournit un moyen d’évaluer les éléments suivants.|  
|<xref:System.Windows.Forms.MergeAction.Remove>|Recherche une correspondance de texte, ou utilise le <xref:System.Windows.Forms.ToolStripItem.MergeIndex%2A> valeur si aucune correspondance de texte est trouvé, puis supprime l’élément de la cible.|Suppression d’un élément de menu à partir de la cible <xref:System.Windows.Forms.MenuStrip>.|  
  
## <a name="manual-merging"></a>Fusion manuelle  
 Uniquement <xref:System.Windows.Forms.MenuStrip> contrôles participent à la fusion automatique. Pour combiner les éléments d’autres contrôles, tels que <xref:System.Windows.Forms.ToolStrip> et <xref:System.Windows.Forms.StatusStrip> contrôles, vous devez les fusionner manuellement, en appelant le <xref:System.Windows.Forms.ToolStripManager.Merge%2A> et <xref:System.Windows.Forms.ToolStripManager.RevertMerge%2A> méthodes dans votre code en fonction des besoins.  
  
## <a name="automatic-merging"></a>Fusion automatique  
 Vous pouvez utiliser la fusion automatique pour les applications MDI en activant le formulaire source. Pour utiliser un <xref:System.Windows.Forms.MenuStrip> dans une application MDI, définissez la <xref:System.Windows.Forms.Form.MainMenuStrip%2A> propriété à la cible <xref:System.Windows.Forms.MenuStrip> afin que les actions de fusion exécutées sur la source de <xref:System.Windows.Forms.MenuStrip> sont répercutées dans la cible <xref:System.Windows.Forms.MenuStrip>.  
  
 Vous pouvez déclencher la fusion automatique en activant le <xref:System.Windows.Forms.MenuStrip> sur la source MDI. Lors de son activation, la source <xref:System.Windows.Forms.MenuStrip> est fusionné dans la cible MDI. Lorsqu’un nouveau formulaire devient actif, la fusion est rétablie sur le dernier formulaire et déclenchée sur le nouveau formulaire. Vous pouvez contrôler ce comportement en définissant le <xref:System.Windows.Forms.ToolStripItem.MergeAction%2A> propriété en fonction des besoins sur chaque <xref:System.Windows.Forms.ToolStripItem>et en définissant le <xref:System.Windows.Forms.ToolStrip.AllowMerge%2A> propriété sur chaque <xref:System.Windows.Forms.MenuStrip>.  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Forms.ToolStripManager>
- <xref:System.Windows.Forms.MenuStrip>
- [MenuStrip, contrôle](menustrip-control-windows-forms.md)
- [Guide pratique pour Créer une liste des fenêtres MDI avec MenuStrip](how-to-create-an-mdi-window-list-with-menustrip-windows-forms.md)
- [Guide pratique pour Configurer la fusion de menus automatique pour les Applications MDI](how-to-set-up-automatic-menu-merging-for-mdi-applications.md)
