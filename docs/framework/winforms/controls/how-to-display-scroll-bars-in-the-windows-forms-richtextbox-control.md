---
title: Afficher les barres de défilement dans le contrôle RichTextBox
ms.date: 03/30/2017
helpviewer_keywords:
- text boxes [Windows Forms], displaying scroll bars
- scroll bars [Windows Forms], displaying in controls
- RichTextBox control [Windows Forms], displaying scroll bars
ms.assetid: cdeb42e1-86e8-410c-ba46-18aec264ef5f
ms.openlocfilehash: 2185b572ef20765043d3df3dbfd8bf5b21cfac28
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76745564"
---
# <a name="how-to-display-scroll-bars-in-the-windows-forms-richtextbox-control"></a>Comment : afficher les barres de défilement dans le contrôle RichTextBox Windows Forms
Par défaut, le contrôle Windows Forms <xref:System.Windows.Forms.RichTextBox> affiche des barres de défilement horizontales et verticales si nécessaire. Il existe sept valeurs possibles pour la propriété <xref:System.Windows.Forms.RichTextBox.ScrollBars%2A> du contrôle <xref:System.Windows.Forms.RichTextBox>, qui sont décrites dans le tableau ci-dessous.  
  
### <a name="to-display-scroll-bars-in-a-richtextbox-control"></a>Pour afficher les barres de défilement dans un contrôle RichTextBox  
  
1. Affectez à la propriété <xref:System.Windows.Forms.RichTextBox.Multiline%2A> la valeur `true`. Aucun type de barre de défilement, y compris horizontal, ne s’affiche si la propriété <xref:System.Windows.Forms.RichTextBox.Multiline%2A> est définie sur `false`.  
  
2. Affectez à la propriété <xref:System.Windows.Forms.RichTextBox.ScrollBars%2A> la valeur appropriée de l’énumération <xref:System.Windows.Forms.RichTextBoxScrollBars>.  
  
    |Valeur|Description|  
    |-----------|-----------------|  
    |<xref:System.Windows.Forms.RichTextBoxScrollBars.Both> (valeur par défaut)|Affiche des barres de défilement horizontales ou verticales, ou les deux, uniquement lorsque le texte dépasse la largeur ou la longueur du contrôle.|  
    |<xref:System.Windows.Forms.RichTextBoxScrollBars.None>|N’affiche jamais aucun type de barre de défilement.|  
    |<xref:System.Windows.Forms.RichTextBoxScrollBars.Horizontal>|Affiche une barre de défilement horizontale uniquement lorsque le texte dépasse la largeur du contrôle. (Pour que cela se produise, la propriété <xref:System.Windows.Forms.TextBoxBase.WordWrap%2A> doit être définie sur `false`.)|  
    |<xref:System.Windows.Forms.RichTextBoxScrollBars.Vertical>|Affiche une barre de défilement verticale uniquement lorsque le texte dépasse la hauteur du contrôle.|  
    |<xref:System.Windows.Forms.RichTextBoxScrollBars.ForcedHorizontal>|Affiche une barre de défilement horizontale lorsque la propriété <xref:System.Windows.Forms.TextBoxBase.WordWrap%2A> est définie sur `false`. La barre de défilement apparaît grisée lorsque le texte ne dépasse pas la largeur du contrôle.|  
    |<xref:System.Windows.Forms.RichTextBoxScrollBars.ForcedVertical>|Affiche toujours une barre de défilement verticale. La barre de défilement apparaît grisée lorsque le texte ne dépasse pas la longueur du contrôle.|  
    |<xref:System.Windows.Forms.RichTextBoxScrollBars.ForcedBoth>|Affiche toujours une barre de défilement verticale. Affiche une barre de défilement horizontale lorsque la propriété <xref:System.Windows.Forms.TextBoxBase.WordWrap%2A> est définie sur `false`. Les barres de défilement apparaissent grisées lorsque le texte ne dépasse pas la largeur ou la longueur du contrôle.|  
  
3. Affectez à la propriété <xref:System.Windows.Forms.TextBoxBase.WordWrap%2A> une valeur appropriée.  
  
    |Valeur|Description|  
    |-----------|-----------------|  
    |`false`|Le texte dans le contrôle n’est pas automatiquement ajusté pour s’ajuster à la largeur du contrôle, de sorte qu’il fait défiler vers la droite jusqu’à ce qu’un saut de ligne soit atteint. Utilisez cette valeur si vous avez choisi des barres de défilement horizontales ou les deux, ci-dessus.|  
    |`true` (valeur par défaut)|Le texte dans le contrôle est automatiquement ajusté pour s’ajuster à la largeur du contrôle. La barre de défilement horizontale n’apparaît pas. Utilisez cette valeur si vous avez choisi des barres de défilement verticales ou aucune, ci-dessus, pour afficher un ou plusieurs paragraphes.|  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Forms.RichTextBoxScrollBars>
- <xref:System.Windows.Forms.RichTextBox>
- [RichTextBox, contrôle](richtextbox-control-windows-forms.md)
- [Contrôles à utiliser dans les Windows Forms](controls-to-use-on-windows-forms.md)
