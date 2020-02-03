---
title: Vue d'ensemble du contrôle RichTextBox
ms.date: 03/30/2017
f1_keywords:
- RichTextBox
helpviewer_keywords:
- RichTextBox control [Windows Forms], about RichTextBox control
- text boxes [Windows Forms], about text boxes
ms.assetid: 95081194-3dd4-4b84-9545-dd373e491eca
ms.openlocfilehash: 0d40967d97622b23e9dcb07e861f190327e6baba
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76742394"
---
# <a name="richtextbox-control-overview-windows-forms"></a>Vue d'ensemble du contrôle RichTextBox (Windows Forms)
Le contrôle Windows Forms <xref:System.Windows.Forms.RichTextBox> permet d’afficher, d’entrer et de manipuler du texte avec une mise en forme. Le contrôle <xref:System.Windows.Forms.RichTextBox> effectue tout ce que fait le contrôle <xref:System.Windows.Forms.TextBox>, mais il peut également afficher des polices, des couleurs et des liens. charger du texte et des images incorporées à partir d’un fichier ; et recherchent les caractères spécifiés. Le contrôle <xref:System.Windows.Forms.RichTextBox> est généralement utilisé pour fournir des fonctionnalités de manipulation de texte et d’affichage similaires aux applications de traitement de texte telles que Microsoft Word. À l’instar du contrôle <xref:System.Windows.Forms.TextBox>, le contrôle <xref:System.Windows.Forms.RichTextBox> peut afficher des barres de défilement ; mais contrairement au contrôle <xref:System.Windows.Forms.TextBox>, son paramètre par défaut permet d’afficher à la fois les barres de défilement horizontales et verticales en fonction des besoins et des paramètres de barre de défilement supplémentaires.  
  
## <a name="working-with-the-richtextbox-control"></a>Utilisation du contrôle RichTextBox  
 Comme avec le contrôle <xref:System.Windows.Forms.TextBox>, le texte affiché est défini par la propriété <xref:System.Windows.Forms.RichTextBox.Text%2A>. Le contrôle <xref:System.Windows.Forms.RichTextBox> possède de nombreuses propriétés pour mettre en forme le texte. Pour plus d’informations sur ces propriétés, consultez [Guide pratique pour définir les attributs de police du contrôle RichTextBox Windows Forms](how-to-set-font-attributes-for-the-windows-forms-richtextbox-control.md) et [Guide pratique pour définir les retraits, les retraits négatifs de première ligne et les listes à puces avec le contrôle RichTextBox Windows Forms](set-indents-hanging-indents-bulleted-paragraphs-with-wf-richtextbox.md). Pour manipuler des fichiers, les méthodes <xref:System.Windows.Forms.RichTextBox.LoadFile%2A> et <xref:System.Windows.Forms.RichTextBox.SaveFile%2A> peuvent afficher et écrire plusieurs formats de fichiers, notamment du texte brut, du texte brut Unicode et le format RTF (Rich Text Format). Les formats de fichier possibles sont répertoriés dans <xref:System.Windows.Forms.RichTextBoxStreamType>. Vous pouvez utiliser la méthode <xref:System.Windows.Forms.RichTextBox.Find%2A> pour rechercher des chaînes de texte ou des caractères spécifiques.  
  
 Vous pouvez également utiliser un contrôle <xref:System.Windows.Forms.RichTextBox> pour les liens de style Web en affectant à la propriété <xref:System.Windows.Forms.RichTextBox.DetectUrls%2A> la valeur `true` et en écrivant du code pour gérer l’événement <xref:System.Windows.Forms.RichTextBox.LinkClicked>. Pour plus d’informations, consultez [Guide pratique pour afficher des liens de style web avec le contrôle RichTextBox Windows Forms](how-to-display-web-style-links-with-the-windows-forms-richtextbox-control.md). Vous pouvez empêcher l’utilisateur de manipuler tout ou partie du texte du contrôle en affectant à la propriété <xref:System.Windows.Forms.RichTextBox.SelectionProtected%2A> la valeur `true`.  
  
 Vous pouvez annuler et rétablir la plupart des opérations de modification dans un contrôle <xref:System.Windows.Forms.RichTextBox> en appelant les méthodes <xref:System.Windows.Forms.TextBoxBase.Undo%2A> et <xref:System.Windows.Forms.RichTextBox.Redo%2A>. La méthode <xref:System.Windows.Forms.RichTextBox.CanRedo%2A> vous permet de déterminer si la dernière opération annulée par l’utilisateur peut être réappliquée au contrôle.  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Forms.RichTextBox>
- [RichTextBox, contrôle](richtextbox-control-windows-forms.md)
- [Vue d’ensemble du contrôle TextBox](textbox-control-overview-windows-forms.md)
