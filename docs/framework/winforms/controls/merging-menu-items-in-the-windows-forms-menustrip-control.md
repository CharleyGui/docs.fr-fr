---
title: Fusion d’éléments de menu dans le contrôle MenuStrip
ms.date: 03/30/2017
helpviewer_keywords:
- MenuStrip [Windows Forms], merging
- merging [Windows Forms], general concepts
ms.assetid: 95e113ba-f362-4dda-8a76-6d95ddc45cee
ms.openlocfilehash: 9fc2b40ef23d72db51853c124095b734a7646cda
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76739041"
---
# <a name="merging-menu-items-in-the-windows-forms-menustrip-control"></a>Fusion d'éléments de menu dans le contrôle MenuStrip Windows Forms
Si vous disposez d’une application d’interface multidocument (MDI, multiple document interface), vous pouvez fusionner des éléments de menu ou des menus entiers du formulaire enfant dans les menus du formulaire parent.  
  
 Cette rubrique décrit les concepts de base associés à la fusion d’éléments de menu dans une application MDI.  
  
## <a name="general-concepts"></a>Concepts généraux  
 Les procédures de fusion impliquent à la fois une cible et un contrôle de code source :  
  
- La cible est le contrôle <xref:System.Windows.Forms.MenuStrip> sur le formulaire principal ou parent MDI dans lequel vous fusionnez les éléments de menu.  
  
- La source est le contrôle <xref:System.Windows.Forms.MenuStrip> sur le formulaire enfant MDI qui contient les éléments de menu que vous souhaitez fusionner dans le menu cible.  
  
 La propriété <xref:System.Windows.Forms.MenuStrip.MdiWindowListItem%2A> identifie l’élément de menu dont vous remplissez les listes déroulantes avec les titres des enfants MDI du formulaire MDI parent. Par exemple, vous répertoriez généralement les enfants MDI qui sont actuellement ouverts dans le menu **fenêtre** .  
  
 La propriété <xref:System.Windows.Forms.ToolStripMenuItem.IsMdiWindowListEntry%2A> identifie les éléments de menu provenant d’un <xref:System.Windows.Forms.MenuStrip> sur un formulaire MDI enfant.  
  
 Vous pouvez fusionner les éléments de menu manuellement ou automatiquement. Les éléments de menu sont fusionnés de la même façon pour les deux méthodes, mais la fusion est activée différemment, comme indiqué dans les sections « fusion manuelle » et « fusion automatique » plus loin dans cette rubrique. Dans les fusions manuelle et automatique, chaque action de fusion affecte l’action de fusion suivante.  
  
 <xref:System.Windows.Forms.MenuStrip> la fusion déplace les éléments de menu d’un <xref:System.Windows.Forms.ToolStrip> à un autre au lieu de les cloner, comme c’était le cas avec <xref:System.Windows.Forms.MainMenu>.  
  
## <a name="mergeaction-values"></a>Valeurs MergeAction  
 Vous définissez l’action de fusion sur les éléments de menu du <xref:System.Windows.Forms.MenuStrip> source à l’aide de la propriété <xref:System.Windows.Forms.MergeAction>.  
  
 Le tableau suivant décrit la signification et l’utilisation classique des actions de fusion disponibles.  
  
|Valeur MergeAction|Description|Utilisation courante|  
|-----------------------|-----------------|-----------------|  
|<xref:System.Windows.Forms.MergeAction.Append>|Valeurs Ajoute l’élément source à la fin de la collection de l’élément cible.|Ajout d’éléments de menu à la fin du menu quand une partie du programme est activée.|  
|<xref:System.Windows.Forms.MergeAction.Insert>|Ajoute l’élément source à la collection de l’élément cible, à l’emplacement spécifié par la propriété <xref:System.Windows.Forms.ToolStripItem.MergeIndex%2A> définie sur l’élément source.|Ajout d’éléments de menu au milieu ou au début du menu quand une partie du programme est activée.<br /><br /> Si la valeur de <xref:System.Windows.Forms.ToolStripItem.MergeIndex%2A> est la même pour les deux éléments de menu, ceux-ci sont ajoutés dans l’ordre inverse. Définissez <xref:System.Windows.Forms.ToolStripItem.MergeIndex%2A> de manière appropriée pour conserver l’ordre d’origine.|  
|<xref:System.Windows.Forms.MergeAction.Replace>|Recherche une correspondance de texte ou utilise la valeur <xref:System.Windows.Forms.ToolStripItem.MergeIndex%2A> si aucune correspondance de texte n’est trouvée, puis remplace l’élément de menu cible correspondant par l’élément de menu source.|Remplacement d’un élément de menu cible par un élément de menu source portant le même nom, ce qui diffère.|  
|<xref:System.Windows.Forms.MergeAction.MatchOnly>|Recherche une correspondance de texte ou utilise la valeur <xref:System.Windows.Forms.ToolStripItem.MergeIndex%2A> si aucune correspondance de texte n’est trouvée, puis ajoute tous les éléments déroulants de la source à la cible.|Création d’une structure de menu qui insère ou ajoute des éléments de menu dans un sous-menu, ou supprime des éléments de menu d’un sous-menu. Par exemple, vous pouvez ajouter un élément de menu d’un enfant MDI à un menu principal <xref:System.Windows.Forms.MenuStrip>**Enregistrer sous** .<br /><br /> <xref:System.Windows.Forms.MergeAction.MatchOnly> vous permet de parcourir la structure de menus sans entreprendre aucune action. Il offre un moyen d’évaluer les éléments suivants.|  
|<xref:System.Windows.Forms.MergeAction.Remove>|Recherche une correspondance de texte ou utilise la valeur <xref:System.Windows.Forms.ToolStripItem.MergeIndex%2A> si aucune correspondance de texte n’est trouvée, puis supprime l’élément de la cible.|Suppression d’un élément de menu du <xref:System.Windows.Forms.MenuStrip>cible.|  
  
## <a name="manual-merging"></a>Fusion manuelle  
 Seuls les contrôles <xref:System.Windows.Forms.MenuStrip> participent à la fusion automatique. Pour combiner les éléments d’autres contrôles, tels que les contrôles <xref:System.Windows.Forms.ToolStrip> et <xref:System.Windows.Forms.StatusStrip>, vous devez les fusionner manuellement, en appelant les méthodes <xref:System.Windows.Forms.ToolStripManager.Merge%2A> et <xref:System.Windows.Forms.ToolStripManager.RevertMerge%2A> dans votre code, selon les besoins.  
  
## <a name="automatic-merging"></a>Fusion automatique  
 Vous pouvez utiliser la fusion automatique pour les applications MDI en activant le formulaire source. Pour utiliser un <xref:System.Windows.Forms.MenuStrip> dans une application MDI, affectez à la propriété <xref:System.Windows.Forms.Form.MainMenuStrip%2A> la <xref:System.Windows.Forms.MenuStrip> cible afin que les actions de fusion effectuées sur le <xref:System.Windows.Forms.MenuStrip> source soient reflétées dans le <xref:System.Windows.Forms.MenuStrip>cible.  
  
 Vous pouvez déclencher la fusion automatique en activant la <xref:System.Windows.Forms.MenuStrip> sur la source MDI. Lors de l’activation, la <xref:System.Windows.Forms.MenuStrip> source est fusionnée dans la cible MDI. Lorsqu’un nouveau formulaire devient actif, la fusion est restaurée sur le dernier formulaire et déclenchée sur le nouveau formulaire. Vous pouvez contrôler ce comportement en définissant la propriété <xref:System.Windows.Forms.ToolStripItem.MergeAction%2A> selon les besoins sur chaque <xref:System.Windows.Forms.ToolStripItem>, et en définissant la propriété <xref:System.Windows.Forms.ToolStrip.AllowMerge%2A> sur chaque <xref:System.Windows.Forms.MenuStrip>.  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Forms.ToolStripManager>
- <xref:System.Windows.Forms.MenuStrip>
- [MenuStrip, contrôle](menustrip-control-windows-forms.md)
- [Guide pratique pour créer une liste des fenêtres MDI avec MenuStrip](how-to-create-an-mdi-window-list-with-menustrip-windows-forms.md)
- [Guide pratique pour configurer la fusion de menus automatique pour les applications MDI](how-to-set-up-automatic-menu-merging-for-mdi-applications.md)
