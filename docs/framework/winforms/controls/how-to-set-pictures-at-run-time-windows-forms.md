---
title: "Comment : définir des images au moment de l'exécution"
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- pictures [Windows Forms], setting display
- examples [Windows Forms], PictureBox control
- bitmaps [Windows Forms], displaying in PictureBox control [Windows Forms]
- PictureBox control [Windows Forms], adding images
- images [Windows Forms], adding with PictureBox control [Windows Forms]
- PictureBox control [Windows Forms], adding pictures
ms.assetid: 18ca41d0-68a5-4660-985e-a6c1fbc01d76
ms.openlocfilehash: cd599ac7e07b5210f8bcff1ffbc76b3d9ee563d7
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79182114"
---
# <a name="how-to-set-pictures-at-run-time-windows-forms"></a>Comment : définir des images au moment de l'exécution (Windows Forms)
Vous pouvez configurer l’image affichée <xref:System.Windows.Forms.PictureBox> par un contrôle Windows Forms.  
  
### <a name="to-set-a-picture-programmatically"></a>Pour définir une image programmatique  
  
- Réglez <xref:System.Windows.Forms.PictureBox.Image%2A> la <xref:System.Drawing.Image.FromFile%2A> propriété <xref:System.Drawing.Image> en utilisant la méthode de la classe.  
  
     Dans l’exemple ci-dessous, le chemin défini pour l’emplacement de l’image est le dossier Mes Documents. Cela est fait, parce que vous pouvez supposer que la plupart des ordinateurs exécutant le système d’exploitation Windows inclura ce répertoire. Cela permet également aux utilisateurs avec des niveaux d’accès minimum au système d’exécuter l’application en toute sécurité. L’exemple ci-dessous suppose <xref:System.Windows.Forms.PictureBox> un formulaire avec un contrôle déjà ajouté.  
  
    ```vb  
    Private Sub LoadNewPict()  
       ' You should replace the bold image
       ' in the sample below with an icon of your own choosing.  
       PictureBox1.Image = Image.FromFile _  
       (System.Environment.GetFolderPath _  
       (System.Environment.SpecialFolder.Personal) _  
       & "\Image.gif")  
    End Sub  
    ```  
  
    ```csharp  
    private void LoadNewPict(){  
       // You should replace the bold image
       // in the sample below with an icon of your own choosing.  
       // Note the escape character used (@) when specifying the path.  
       pictureBox1.Image = Image.FromFile  
       (System.Environment.GetFolderPath  
       (System.Environment.SpecialFolder.Personal)  
       + @"\Image.gif");  
    }  
    ```  
  
    ```cpp  
    private:  
       void LoadNewPict()  
       {  
          // You should replace the bold image
          // in the sample below with an icon of your own choosing.  
          pictureBox1->Image = Image::FromFile(String::Concat(  
             System::Environment::GetFolderPath(  
             System::Environment::SpecialFolder::Personal),  
             "\\Image.gif"));  
       }  
    ```  
  
### <a name="to-clear-a-graphic"></a>Pour effacer un graphique  
  
- Tout d’abord, relâchez la mémoire utilisée par l’image, puis effacez le graphique. La collecte des ordures libérera la mémoire plus tard si la gestion de la mémoire devient un problème.  
  
    ```vb  
    If Not (PictureBox1.Image Is Nothing) Then  
       PictureBox1.Image.Dispose()  
       PictureBox1.Image = Nothing  
    End If  
    ```  
  
    ```csharp  
    if (pictureBox1.Image != null)
    {  
       pictureBox1.Image.Dispose();  
       pictureBox1.Image = null;  
    }  
    ```  
  
    ```cpp  
    if (pictureBox1->Image != nullptr)  
    {  
       pictureBox1->Image->Dispose();  
       pictureBox1->Image = nullptr;  
    }  
    ```  
  
    > [!NOTE]
    > Pour plus d’informations sur <xref:System.Drawing.Image.Dispose%2A> les raisons pour lesquelles vous devriez utiliser la méthode de cette façon, voir [Cleaning Up Unmanaged Resources](../../../standard/garbage-collection/unmanaged.md).  
  
     Ce code effacera l’image même si un graphique a été chargé dans le contrôle au moment de la conception.  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Forms.PictureBox>
- <xref:System.Drawing.Image.FromFile%2A?displayProperty=nameWithType>
- [Vue d'ensemble du contrôle PictureBox](picturebox-control-overview-windows-forms.md)
- [Comment : charger une image à l'aide du concepteur](how-to-load-a-picture-using-the-designer-windows-forms.md)
- [Comment : modifier la taille ou l'emplacement d'une image au moment de l'exécution](how-to-modify-the-size-or-placement-of-a-picture-at-run-time-windows-forms.md)
- [PictureBox, contrôle](picturebox-control-windows-forms.md)
