---
title: Définir l’image affichée par un contrôle
ms.date: 08/20/2019
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
ms.openlocfilehash: 5df0068c8462bbaab0cb0135de1dd1b91ababe06
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76746871"
---
# <a name="how-to-set-the-image-displayed-by-a-windows-forms-control"></a>Comment : définir l’image affichée par un contrôle Windows Forms

Plusieurs contrôles de Windows Forms peuvent afficher des images. Ces images peuvent être des icônes qui clarifient l’objectif du contrôle, par exemple une icône de disquette sur un bouton indiquant la commande Enregistrer. Les icônes peuvent également être des images d’arrière-plan pour que le contrôle donne l’apparence et le comportement souhaités.

## <a name="programmatic"></a>Par programme

Définissez la propriété `Image` ou `BackgroundImage` du contrôle sur un objet de type <xref:System.Drawing.Image>. En règle générale, vous chargez l’image à partir d’un fichier à l’aide de la méthode <xref:System.Drawing.Image.FromFile%2A>.

Dans l’exemple de code suivant, le chemin d’accès défini pour l’emplacement de l’image est le dossier **Mes images** . La plupart des ordinateurs exécutant le système d’exploitation Windows incluent ce répertoire. Cela permet également aux utilisateurs disposant de niveaux d’accès système minimaux d’exécuter l’application en toute sécurité. L’exemple de code suivant nécessite que vous disposiez déjà d’un formulaire avec un contrôle <xref:System.Windows.Forms.PictureBox> ajouté.

```vb
' Replace the image named below with your own icon.
PictureBox1.Image = Image.FromFile _
   (System.Environment.GetFolderPath _
   (System.Environment.SpecialFolder.MyPictures) _
   & "\Image.gif")
```

```csharp
// Replace the image named below with your own icon.
// Note the escape character used (@) when specifying the path.
pictureBox1.Image = Image.FromFile
   (System.Environment.GetFolderPath
   (System.Environment.SpecialFolder.MyPictures)
   + @"\Image.gif");
```

```cpp
// Replace the image named below with your own icon.
pictureBox1->Image = Image::FromFile(String::Concat
   (System::Environment::GetFolderPath
   (System::Environment::SpecialFolder::MyPictures),
   "\\Image.gif"));
```

## <a name="designer"></a>Designer

1. Dans la fenêtre **Propriétés** de Visual Studio, sélectionnez la propriété **image** ou **BackgroundImage** du contrôle, puis sélectionnez les points de suspension (![bouton de sélection dans Visual Studio](./media/visual-studio-ellipsis-button.png)) pour afficher la boîte de dialogue **Sélectionner une ressource** .

2. Sélectionnez l’image que vous souhaitez afficher.

## <a name="see-also"></a>Voir aussi

- <xref:System.Drawing.Image.FromFile%2A>
- <xref:System.Drawing.Image>
- <xref:System.Windows.Forms.Control.BackgroundImage%2A>
