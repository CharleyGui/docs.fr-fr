---
title: "Comment : modifier la taille ou l'emplacement d'une image au moment de l'exécution"
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- images [Windows Forms], controlling placement in PictureBox control [Windows Forms]
- examples [Windows Forms], PictureBox control
- PictureBox control [Windows Forms], picture size and alignment
- pictures [Windows Forms], controlling placement in PictureBox control [Windows Forms]
ms.assetid: d0b332a3-fae2-4891-957c-dc3e17743326
ms.openlocfilehash: fea813d7b9fe585e35b729b8b64e3a5f414ef76d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79141964"
---
# <a name="how-to-modify-the-size-or-placement-of-a-picture-at-run-time-windows-forms"></a>Comment : modifier la taille ou l'emplacement d'une image au moment de l'exécution (Windows Forms)
Si vous utilisez <xref:System.Windows.Forms.PictureBox> le contrôle des formulaires <xref:System.Windows.Forms.PictureBox.SizeMode%2A> Windows sur un formulaire, vous pouvez y définir la propriété :  
  
- Alignez le coin supérieur gauche de l’image avec le coin supérieur gauche du contrôle  
  
- Centrez l’image dans le contrôle  
  
- Ajuster la taille du contrôle pour s’adapter à l’image qu’il affiche  
  
- Étirez n’importe quelle image qu’il affiche pour adapter le contrôle  
  
 L’étirement d’une image (en particulier un en format bitmap) peut produire une perte de qualité d’image. Les métafiles, qui sont des listes d’instructions graphiques pour dessiner des images au moment de l’exécution, sont mieux adaptés pour l’étirement que les bitmaps.  
  
### <a name="to-set-the-sizemode-property-at-run-time"></a>Pour définir la propriété SizeMode au moment de l’exécution  
  
1. Configuré <xref:System.Windows.Forms.PictureBox.SizeMode%2A> <xref:System.Windows.Forms.PictureBoxSizeMode.Normal> à <xref:System.Windows.Forms.PictureBoxSizeMode.AutoSize>(la valeur par défaut), , <xref:System.Windows.Forms.PictureBoxSizeMode.CenterImage>, ou <xref:System.Windows.Forms.PictureBoxSizeMode.StretchImage>. <xref:System.Windows.Forms.PictureBoxSizeMode.Normal>signifie que l’image est placée dans le coin supérieur gauche du contrôle; si l’image est plus grande que le contrôle, ses bords inférieurs et droits sont coupés. <xref:System.Windows.Forms.PictureBoxSizeMode.CenterImage>signifie que l’image est centrée dans le contrôle; si l’image est plus grande que le contrôle, les bords extérieurs de l’image sont coupés. <xref:System.Windows.Forms.PictureBoxSizeMode.AutoSize>signifie que la taille du contrôle est ajustée à la taille de l’image. <xref:System.Windows.Forms.PictureBoxSizeMode.StretchImage>est l’inverse, et signifie que la taille de l’image est ajustée à la taille du contrôle.  
  
     Dans l’exemple ci-dessous, le chemin défini pour l’emplacement de l’image est le dossier Mes Documents. Cela est fait, parce que vous pouvez supposer que la plupart des ordinateurs exécutant le système d’exploitation Windows inclura ce répertoire. Cela permet également aux utilisateurs avec des niveaux d’accès minimum au système d’exécuter l’application en toute sécurité. L’exemple ci-dessous suppose <xref:System.Windows.Forms.PictureBox> un formulaire avec un contrôle déjà ajouté.  
  
    ```vb  
    Private Sub StretchPic()  
       ' Stretch the picture to fit the control.  
       PictureBox1.SizeMode = PictureBoxSizeMode.StretchImage  
       ' Load the picture into the control.  
       ' You should replace the bold image
       ' in the sample below with an icon of your own choosing.  
       PictureBox1.Image = Image.FromFile _  
       (System.Environment.GetFolderPath _  
       (System.Environment.SpecialFolder.Personal) _  
       & "\Image.gif")  
    End Sub  
    ```  
  
    ```csharp  
    private void StretchPic(){  
       // Stretch the picture to fit the control.  
       PictureBox1.SizeMode = PictureBoxSizeMode.StretchImage;  
       // Load the picture into the control.  
       // You should replace the bold image
       // in the sample below with an icon of your own choosing.  
       // Note the escape character used (@) when specifying the path.  
       PictureBox1.Image = Image.FromFile _  
       (System.Environment.GetFolderPath _  
       (System.Environment.SpecialFolder.Personal) _  
       + @"\Image.gif")  
    }  
    ```  
  
    ```cpp  
    private:  
       void StretchPic()  
       {  
          // Stretch the picture to fit the control.  
          pictureBox1->SizeMode = PictureBoxSizeMode::StretchImage;  
          // Load the picture into the control.  
          // You should replace the bold image
          // in the sample below with an icon of your own choosing.  
          pictureBox1->Image = Image::FromFile(String::Concat(  
             System::Environment::GetFolderPath(  
             System::Environment::SpecialFolder::Personal),  
             "\\Image.gif"));  
       }  
    ```  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Forms.PictureBox>
- [Comment : charger une image à l'aide du concepteur](how-to-load-a-picture-using-the-designer-windows-forms.md)
- [Vue d'ensemble du contrôle PictureBox](picturebox-control-overview-windows-forms.md)
- [Comment : définir des images au moment de l'exécution](how-to-set-pictures-at-run-time-windows-forms.md)
- [PictureBox, contrôle](picturebox-control-windows-forms.md)
