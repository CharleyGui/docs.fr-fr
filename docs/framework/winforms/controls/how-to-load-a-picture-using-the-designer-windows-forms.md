---
title: 'Procédure : Charger une image à l’aide du concepteur (Windows Forms)'
ms.date: 03/30/2017
helpviewer_keywords:
- picture formats
- images [Windows Forms], displaying on Windows Forms
- pictures [Windows Forms], displaying
- forms [Windows Forms], displaying images
- PictureBox control [Windows Forms], adding pictures
ms.assetid: 4dc7b973-afb1-4276-8322-20825af96655
ms.openlocfilehash: 1d95d5baafa42c7dea40933ba837b684d90b7b2b
ms.sourcegitcommit: a97ecb94437362b21fffc5eb3c38b6c0b4368999
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/13/2019
ms.locfileid: "68972370"
---
# <a name="how-to-load-a-picture-using-the-designer-windows-forms"></a>Procédure : Charger une image à l’aide du concepteur (Windows Forms)

Avec le contrôle <xref:System.Windows.Forms.PictureBox> Windows Forms, vous pouvez charger et afficher une image sur un formulaire au moment du design en affectant à la <xref:System.Windows.Forms.PictureBox.Image%2A> propriété une image valide. Le tableau suivant présente les types de fichiers acceptables.

|Type|Extension de nom de fichier|
|----------|-------------------------|
|Bitmap|.bmp|
|Icône|.ico|
|GIF|.gif|
|Métafichiers|.wmf|
|JPEG|.jpg|

> [!NOTE]
>  Les boîtes de dialogue et les commandes de menu qui s'affichent peuvent être différentes de celles qui sont décrites dans l'aide, en fonction de vos paramètres actifs ou de l'édition utilisée. Pour modifier vos paramètres, choisissez **Importation et exportation de paramètres** dans le menu **Outils** . Pour plus d’informations, consultez [Personnaliser l’IDE Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).

## <a name="to-display-a-picture-at-design-time"></a>Pour afficher une image au moment du design

1. Dessinez <xref:System.Windows.Forms.PictureBox> un contrôle sur un formulaire.

2. Dans la fenêtre Propriétés, sélectionnez la <xref:System.Windows.Forms.PictureBox.Image%2A> propriété, puis cliquez sur le bouton de sélection pour afficher la boîte de dialogue **ouvrir** .

3. Si vous recherchez un type de fichier spécifique (par exemple, des fichiers. gif), sélectionnez-le dans la zone **types de fichiers** .

4. Sélectionnez le fichier que vous souhaitez afficher.

## <a name="to-clear-the-picture-at-design-time"></a>Pour effacer l’image au moment du design

1. Dans la fenêtre **Propriétés** , sélectionnez la <xref:System.Windows.Forms.PictureBox.Image%2A> propriété et cliquez avec le bouton droit sur la petite image miniature qui apparaît à gauche du nom de l’objet image. Choisissez **Réinitialiser**.

## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Forms.PictureBox>
- [Vue d’ensemble du contrôle PictureBox](picturebox-control-overview-windows-forms.md)
- [Guide pratique : Modifier la taille ou l’emplacement d’une image au moment de l’exécution](how-to-modify-the-size-or-placement-of-a-picture-at-run-time-windows-forms.md)
- [Guide pratique : Définir des images au moment de l’exécution](how-to-set-pictures-at-run-time-windows-forms.md)
- [PictureBox, contrôle](picturebox-control-windows-forms.md)
