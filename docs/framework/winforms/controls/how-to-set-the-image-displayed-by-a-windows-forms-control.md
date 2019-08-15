---
title: 'Procédure : définir l’image affichée par un contrôle Windows Forms'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- Button control [Windows Forms], images
- Windows Forms controls, images
- controls [Windows Forms], images
- images [Windows Forms], Windows Forms controls
- examples [Windows Forms], controls
ms.assetid: 9445af8f-4f62-48b0-a3f6-068058964b9f
ms.openlocfilehash: 99bde4fac7b3057358c7e6a8550efdb4cc351eb0
ms.sourcegitcommit: cf9515122fce716bcfb6618ba366e39b5a2eb81e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/15/2019
ms.locfileid: "69037878"
---
# <a name="how-to-set-the-image-displayed-by-a-windows-forms-control"></a>Procédure : Définir l’image affichée par un contrôle Windows Forms

Plusieurs contrôles de Windows Forms peuvent afficher des images. Ces images peuvent être des icônes qui clarifient l’objectif du contrôle, par exemple une icône de disquette sur un bouton indiquant la commande **Enregistrer** . Les icônes peuvent également être des images d’arrière-plan pour que le contrôle donne l’apparence et le comportement souhaités.

## <a name="to-set-the-image-displayed-by-a-control"></a>Pour définir l’image affichée par un contrôle

1. Affectez à la `Image` propriété `BackgroundImage` ou au contrôle la valeur d' <xref:System.Drawing.Image>un objet de type. En général, vous allez charger l’image à partir d’un fichier à <xref:System.Drawing.Image.FromFile%2A> l’aide de la méthode.

     Dans l’exemple de code suivant, le chemin d’accès défini pour l’emplacement de l’image est le dossier **Mes images** . La plupart des ordinateurs exécutant le système d’exploitation Windows comporteront ce répertoire. Cela permet également aux utilisateurs disposant de niveaux d’accès système minimaux d’exécuter l’application en toute sécurité. L’exemple de code suivant nécessite que vous disposiez déjà d’un <xref:System.Windows.Forms.PictureBox> formulaire avec un contrôle ajouté.

    ```vb
    ' Replace the image named below
    ' with an icon of your own choosing.
    PictureBox1.Image = Image.FromFile _
       (System.Environment.GetFolderPath _
       (System.Environment.SpecialFolder.MyPictures) _
       & "\Image.gif")
    ```

    ```csharp
    // Replace the image named below
    // with an icon of your own choosing.
    // Note the escape character used (@) when specifying the path.
    pictureBox1.Image = Image.FromFile
       (System.Environment.GetFolderPath
       (System.Environment.SpecialFolder.MyPictures)
       + @"\Image.gif");
    ```

    ```cpp
    // Replace the image named below
    // with an icon of your own choosing.
    pictureBox1->Image = Image::FromFile(String::Concat
       (System::Environment::GetFolderPath
       (System::Environment::SpecialFolder::MyPictures),
       "\\Image.gif"));
    ```

## <a name="see-also"></a>Voir aussi

- <xref:System.Drawing.Image.FromFile%2A>
- <xref:System.Drawing.Image>
- <xref:System.Windows.Forms.Control.BackgroundImage%2A>
