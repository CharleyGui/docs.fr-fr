---
title: "Comment : charger une image à l'aide du concepteur"
description: Découvrez comment utiliser le contrôle Windows Forms PictureBox pour charger et afficher une image sur un formulaire au moment du Design.
ms.date: 03/30/2017
helpviewer_keywords:
- picture formats
- images [Windows Forms], displaying on Windows Forms
- pictures [Windows Forms], displaying
- forms [Windows Forms], displaying images
- PictureBox control [Windows Forms], adding pictures
ms.assetid: 4dc7b973-afb1-4276-8322-20825af96655
ms.openlocfilehash: a05ffe19412fc7a4e3e02f01336d89cce39fac8a
ms.sourcegitcommit: dc2feef0794cf41dbac1451a13b8183258566c0e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/24/2020
ms.locfileid: "85325596"
---
# <a name="how-to-load-a-picture-using-the-designer-windows-forms"></a>Comment : charger une image à l'aide du concepteur (Windows Forms)

Avec le <xref:System.Windows.Forms.PictureBox> contrôle Windows Forms, vous pouvez charger et afficher une image sur un formulaire au moment du design en affectant <xref:System.Windows.Forms.PictureBox.Image%2A> à la propriété une image valide. Le tableau suivant présente les types de fichiers acceptables.

|Type|Extension de nom de fichier|
|---|---|
|Bitmap|.bmp|
|Icône|.ico|
|GIF|.gif|
|Métafichiers|. wmf|
|JPEG|.jpg|

## <a name="to-display-a-picture-at-design-time"></a>Pour afficher une image au moment du design

1. Dessinez un <xref:System.Windows.Forms.PictureBox> contrôle sur un formulaire.

2. Dans la fenêtre **Propriétés** , sélectionnez la <xref:System.Windows.Forms.PictureBox.Image%2A> propriété, puis cliquez sur le bouton de sélection pour afficher la boîte de dialogue **ouvrir** .

3. Si vous recherchez un type de fichier spécifique (par exemple, des fichiers. gif), sélectionnez-le dans la zone **types de fichiers** .

4. Sélectionnez le fichier que vous souhaitez afficher.

## <a name="to-clear-the-picture-at-design-time"></a>Pour effacer l’image au moment du design

1. Dans la fenêtre **Propriétés** , sélectionnez la <xref:System.Windows.Forms.PictureBox.Image%2A> propriété. Cliquez avec le bouton droit sur la petite image miniature qui apparaît à gauche du nom de l’objet image, puis choisissez **Réinitialiser**.

## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Forms.PictureBox>
- [Vue d'ensemble du contrôle PictureBox](picturebox-control-overview-windows-forms.md)
- [Comment : modifier la taille ou l'emplacement d'une image au moment de l'exécution](how-to-modify-the-size-or-placement-of-a-picture-at-run-time-windows-forms.md)
- [Comment : définir des images au moment de l'exécution](how-to-set-pictures-at-run-time-windows-forms.md)
- [PictureBox, contrôle](picturebox-control-windows-forms.md)
