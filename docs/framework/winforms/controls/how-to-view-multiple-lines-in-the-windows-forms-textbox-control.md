---
title: Afficher plusieurs lignes dans le contrôle TextBox
ms.date: 03/30/2017
helpviewer_keywords:
- newline
- end of line
- ScrollBars property [Windows Forms], in TextBox control
- CRLF
- MultiLine property in TextBox control
- line-feed
- TextBox control [Windows Forms], viewing multiple lines
- carriage return
ms.assetid: 43173201-0b74-4067-a472-605029ca5f35
ms.openlocfilehash: 61ea671c1e86fa8254bfc1b043a46f3b7aa6af1d
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76728285"
---
# <a name="how-to-view-multiple-lines-in-the-windows-forms-textbox-control"></a>Comment : afficher des lignes multiples dans le contrôle TextBox Windows Forms
Par défaut, le contrôle de <xref:System.Windows.Forms.TextBox> Windows Forms affiche une seule ligne de texte et n’affiche pas de barres de défilement. Si le texte est plus long que l’espace disponible, seule une partie du texte est visible. Vous pouvez modifier ce comportement par défaut en définissant les propriétés <xref:System.Windows.Forms.TextBox.Multiline%2A>, <xref:System.Windows.Forms.TextBoxBase.WordWrap%2A>et <xref:System.Windows.Forms.TextBox.ScrollBars%2A> sur les valeurs appropriées.  
  
### <a name="to-display-a-carriage-return-in-the-textbox-control"></a>Pour afficher un retour chariot dans le contrôle TextBox  
  
- Pour afficher un retour chariot dans un <xref:System.Windows.Forms.TextBox>multiligne, utilisez la propriété <xref:System.Environment.NewLine%2A>.  
  
     N’oubliez pas que l’interprétation des caractères d’échappement (\\) est spécifique au langage. Visual Basic utilise `Chr$(13) & Chr$(10)` pour la combinaison de caractères retour chariot et saut de ligne.  
  
### <a name="to-view-multiple-lines-in-the-textbox-control"></a>Pour afficher plusieurs lignes dans le contrôle TextBox  
  
1. Affectez à la propriété <xref:System.Windows.Forms.TextBox.Multiline%2A> la valeur `true`. Si <xref:System.Windows.Forms.TextBoxBase.WordWrap%2A> est `true` (valeur par défaut), le texte dans le contrôle s’affiche sous la forme d’un ou de plusieurs paragraphes ; dans le cas contraire, elle apparaît sous la forme d’une liste, dans laquelle certaines lignes peuvent être découpées à la périphérie du contrôle.  
  
2. Affectez à la propriété <xref:System.Windows.Forms.TextBox.ScrollBars%2A> une valeur appropriée.  
  
    |Valeur|Description|  
    |-----------|-----------------|  
    |<xref:System.Windows.Forms.ScrollBars.None>|Utilisez cette valeur si le texte est un paragraphe qui correspond presque toujours au contrôle. L’utilisateur peut utiliser le pointeur de la souris pour se déplacer dans le contrôle si le texte est trop long pour être affiché en une seule fois.|  
    |<xref:System.Windows.Forms.ScrollBars.Horizontal>|Utilisez cette valeur si vous souhaitez afficher une liste de lignes, dont certaines peuvent être plus longues que la largeur du contrôle <xref:System.Windows.Forms.TextBox>.|  
    |<xref:System.Windows.Forms.ScrollBars.Both>|Utilisez cette valeur si la liste peut être plus longue que la hauteur du contrôle.|  
  
3. Affectez à la propriété <xref:System.Windows.Forms.TextBoxBase.WordWrap%2A> une valeur appropriée.  
  
    |Valeur|Description|  
    |-----------|-----------------|  
    |`false`|Le texte dans le contrôle ne sera pas automatiquement renvoyé à la ligne. il défilera vers la droite jusqu’à ce qu’un saut de ligne soit atteint. Utilisez cette valeur si vous avez choisi <xref:System.Windows.Forms.ScrollBars.Horizontal> barres de défilement ou <xref:System.Windows.Forms.ScrollBars.Both>ci-dessus.|  
    |`true` (valeur par défaut)|La barre de défilement horizontale n’apparaît pas. Utilisez cette valeur si vous avez choisi <xref:System.Windows.Forms.ScrollBars.Vertical> barres de défilement ou <xref:System.Windows.Forms.ScrollBars.None>ci-dessus pour afficher un ou plusieurs paragraphes.|  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Forms.TextBox>
- [Vue d’ensemble du contrôle TextBox](textbox-control-overview-windows-forms.md)
- [Guide pratique pour contrôler le point d’insertion dans un contrôle TextBox Windows Forms](how-to-control-the-insertion-point-in-a-windows-forms-textbox-control.md)
- [Guide pratique pour créer une zone de texte pour mot de passe avec le contrôle TextBox Windows Forms](how-to-create-a-password-text-box-with-the-windows-forms-textbox-control.md)
- [Guide pratique pour créer une zone de texte en lecture seule](how-to-create-a-read-only-text-box-windows-forms.md)
- [Guide pratique pour insérer des guillemets dans une chaîne](how-to-put-quotation-marks-in-a-string-windows-forms.md)
- [Guide pratique pour sélectionner du texte dans le contrôle TextBox Windows Forms](how-to-select-text-in-the-windows-forms-textbox-control.md)
- [TextBox, contrôle](textbox-control-windows-forms.md)
