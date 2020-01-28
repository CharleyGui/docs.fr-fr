---
title: Vue d’ensemble du contrôle NumericUpDown
ms.date: 03/30/2017
f1_keywords:
- NumericUpDown
helpviewer_keywords:
- numeric spin button control [Windows Forms], Windows Forms
- NumericUpDown control [Windows Forms], about NumericUpDown control
- spin button control [Windows Forms], Windows Forms
ms.assetid: cff3cf30-4d46-4381-87df-37bfe83c71c5
ms.openlocfilehash: 3e24fa543df9028e9866d91ec60c3cf88578ac56
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76740800"
---
# <a name="numericupdown-control-overview-windows-forms"></a>Vue d'ensemble du contrôle NumericUpDown (Windows Forms)
Le contrôle <xref:System.Windows.Forms.NumericUpDown> ressemble à une combinaison d’une zone de texte et d’une paire de flèches sur lesquelles l’utilisateur peut cliquer pour ajuster une valeur. Le contrôle affiche et définit une valeur numérique unique à partir d’une liste de choix de valeurs numériques fixes. L’utilisateur peut augmenter et diminuer le nombre en cliquant sur les flèches vers le haut et vers le bas, en appuyant sur les touches de direction haut et bas, ou en tapant un nombre dans la partie zone de texte du contrôle. Si vous cliquez sur la touche haut, le nombre est déplacé vers la valeur maximale ; Si vous cliquez sur la touche de direction bas, le nombre est déplacé vers la valeur minimale.  
  
 En raison de ses fonctionnalités polyvalentes, ce contrôle est un choix évident, par exemple, si vous souhaitez créer un contrôle de volume pour une application de lecteur de musique. Le contrôle <xref:System.Windows.Forms.NumericUpDown> est utilisé dans de nombreuses applications du panneau de configuration Windows.  
  
## <a name="key-properties-and-methods"></a>Propriétés et méthodes de clé  
 Les nombres affichés dans la zone de texte du contrôle peuvent être dans différents formats, y compris le format hexadécimal. Pour plus d’informations, consultez [Comment : définir le format du contrôle NumericUpDown Windows Forms](how-to-set-the-format-for-the-windows-forms-numericupdown-control.md). Les propriétés de clé du contrôle sont <xref:System.Windows.Forms.NumericUpDown.Value%2A>, <xref:System.Windows.Forms.NumericUpDown.Maximum%2A> (valeur par défaut 100), <xref:System.Windows.Forms.NumericUpDown.Minimum%2A> (valeur par défaut 0) et <xref:System.Windows.Forms.NumericUpDown.Increment%2A> (valeur par défaut 1). La propriété <xref:System.Windows.Forms.NumericUpDown.Value%2A> définit le nombre actuel sélectionné dans le contrôle. La propriété <xref:System.Windows.Forms.NumericUpDown.Increment%2A> définit la valeur d’ajustement du nombre lorsque l’utilisateur clique sur une flèche haut ou bas. Lorsque le focus se déplace hors du contrôle, toute entrée typée est validée par rapport aux valeurs numériques minimale et maximale. Vous pouvez augmenter la vitesse de déplacement du contrôle à travers les nombres, lorsque l’utilisateur appuie continuellement sur la flèche haut ou bas, avec la propriété <xref:System.Windows.Forms.NumericUpDown.Accelerations%2A>. Les principales méthodes du contrôle sont <xref:System.Windows.Forms.NumericUpDown.UpButton%2A> et <xref:System.Windows.Forms.NumericUpDown.DownButton%2A>.  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Forms.NumericUpDown>
- [NumericUpDown, contrôle](numericupdown-control-windows-forms.md)
- [Guide pratique pour définir le format du contrôle NumericUpDown Windows Forms](how-to-set-the-format-for-the-windows-forms-numericupdown-control.md)
- [TextBox, contrôle](textbox-control-windows-forms.md)
