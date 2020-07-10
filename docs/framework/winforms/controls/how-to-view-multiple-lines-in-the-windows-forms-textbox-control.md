---
title: Afficher plusieurs lignes dans le contrôle TextBox
description: Découvrez comment afficher plusieurs lignes dans le contrôle Windows Forms zone de texte en définissant les propriétés Multiline, WordWrap et ScrollBars.
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
ms.openlocfilehash: e40d720bcd56366f4f06bfe2e2d347aaf9aa9d6c
ms.sourcegitcommit: cb27c01a8b0b4630148374638aff4e2221f90b22
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/09/2020
ms.locfileid: "86174469"
---
# <a name="how-to-view-multiple-lines-in-the-windows-forms-textbox-control"></a>Comment : afficher des lignes multiples dans le contrôle TextBox Windows Forms
Par défaut, le <xref:System.Windows.Forms.TextBox> contrôle Windows Forms affiche une seule ligne de texte et n’affiche pas de barres de défilement. Si le texte est plus long que l’espace disponible, seule une partie du texte est visible. Vous pouvez modifier ce comportement par défaut en définissant les <xref:System.Windows.Forms.TextBox.Multiline%2A> <xref:System.Windows.Forms.TextBoxBase.WordWrap%2A> Propriétés, et <xref:System.Windows.Forms.TextBox.ScrollBars%2A> sur les valeurs appropriées.  
  
### <a name="to-display-a-carriage-return-in-the-textbox-control"></a>Pour afficher un retour chariot dans le contrôle TextBox  
  
- Pour afficher un retour chariot dans une ligne multiligne <xref:System.Windows.Forms.TextBox> , utilisez la <xref:System.Environment.NewLine%2A> propriété.  
  
     N’oubliez pas que l’interprétation des caractères d’échappement ( \\ ) est spécifique au langage. Visual Basic utilise `Chr$(13) & Chr$(10)` pour la combinaison de retour chariot et de saut de ligne.  
  
### <a name="to-view-multiple-lines-in-the-textbox-control"></a>Pour afficher plusieurs lignes dans le contrôle TextBox  
  
1. Attribuez à la propriété <xref:System.Windows.Forms.TextBox.Multiline%2A> la valeur `true`. Si <xref:System.Windows.Forms.TextBoxBase.WordWrap%2A> est `true` (valeur par défaut), le texte du contrôle apparaîtra sous la forme d’un ou de plusieurs paragraphes ; sinon, il apparaîtra sous la forme d’une liste, dans laquelle des lignes peuvent être découpées à la périphérie du contrôle.  
  
2. Affectez à la propriété <xref:System.Windows.Forms.TextBox.ScrollBars%2A> une valeur appropriée.  
  
    |Valeur|Description|  
    |-----------|-----------------|  
    |<xref:System.Windows.Forms.ScrollBars.None>|Utilisez cette valeur si le texte est un paragraphe qui correspond presque toujours au contrôle. L’utilisateur peut utiliser le pointeur de la souris pour se déplacer dans le contrôle si le texte est trop long pour être affiché en une seule fois.|  
    |<xref:System.Windows.Forms.ScrollBars.Horizontal>|Utilisez cette valeur si vous souhaitez afficher une liste de lignes, dont certaines peuvent être plus longues que la largeur du <xref:System.Windows.Forms.TextBox> contrôle.|  
    |<xref:System.Windows.Forms.ScrollBars.Both>|Utilisez cette valeur si la liste peut être plus longue que la hauteur du contrôle.|  
  
3. Affectez à la propriété <xref:System.Windows.Forms.TextBoxBase.WordWrap%2A> une valeur appropriée.  
  
    |Valeur|Description|  
    |-----------|-----------------|  
    |`false`|Le texte dans le contrôle ne sera pas automatiquement renvoyé à la ligne. il défilera vers la droite jusqu’à ce qu’un saut de ligne soit atteint. Utilisez cette valeur si vous avez choisi <xref:System.Windows.Forms.ScrollBars.Horizontal> barres de défilement ou <xref:System.Windows.Forms.ScrollBars.Both> , ci-dessus.|  
    |`true` (valeur par défaut)|La barre de défilement horizontale n’apparaît pas. Utilisez cette valeur si vous avez choisi des <xref:System.Windows.Forms.ScrollBars.Vertical> barres <xref:System.Windows.Forms.ScrollBars.None> de défilement ou, ci-dessus, pour afficher un ou plusieurs paragraphes.|  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Forms.TextBox>
- [Vue d'ensemble du contrôle TextBox](textbox-control-overview-windows-forms.md)
- [Guide pratique pour contrôler le point d’insertion dans un contrôle TextBox Windows Forms](how-to-control-the-insertion-point-in-a-windows-forms-textbox-control.md)
- [Comment : créer une zone de texte pour mot de passe avec le contrôle TextBox Windows Forms](how-to-create-a-password-text-box-with-the-windows-forms-textbox-control.md)
- [Comment : créer une zone de texte en lecture seule](how-to-create-a-read-only-text-box-windows-forms.md)
- [Comment : insérer des guillemets dans une chaîne](how-to-put-quotation-marks-in-a-string-windows-forms.md)
- [Comment : sélectionner du texte dans le contrôle TextBox Windows Forms](how-to-select-text-in-the-windows-forms-textbox-control.md)
- [TextBox, contrôle](textbox-control-windows-forms.md)
