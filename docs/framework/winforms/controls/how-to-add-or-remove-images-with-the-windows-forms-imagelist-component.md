---
title: Ajouter ou supprimer des images avec le composant ImageList
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- images [Windows Forms], removing from ImageList component
- images [Windows Forms], storing for controls
- ImageList component [Windows Forms], adding images
- ImageList component [Windows Forms], removing images
- images [Windows Forms], adding to ImageList component
- images [Windows Forms], displaying with controls
ms.assetid: c5eacc56-f769-4e2e-bfb7-f756620913db
ms.openlocfilehash: f531003377395bf219775e5ddb48ceb0822ff0ea
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76741502"
---
# <a name="how-to-add-or-remove-images-with-the-windows-forms-imagelist-component"></a>Comment : ajouter ou supprimer des images avec le composant ImageList Windows Forms
Le composant <xref:System.Windows.Forms.ImageList> Windows Forms est généralement renseigné avec des images avant qu’il ne soit associé à un contrôle. Toutefois, vous pouvez ajouter et supprimer des images après l’Association de la liste d’images avec un contrôle.  
  
> [!NOTE]
> Lorsque vous supprimez des images, vérifiez que la propriété <xref:System.Windows.Forms.ButtonBase.ImageIndex%2A> des contrôles associés est toujours valide.  
  
### <a name="to-add-images-programmatically"></a>Pour ajouter des images par programmation  
  
- Utilisez la méthode <xref:System.Windows.Forms.ImageList.ImageCollection.Add%2A> de la propriété <xref:System.Windows.Forms.ImageList.Images%2A> de la liste d’images.  
  
     Dans l’exemple de code suivant, le chemin d’accès défini pour l’emplacement de l’image est le dossier **Mes documents** . Cet emplacement est utilisé, car vous pouvez supposer que la plupart des ordinateurs qui exécutent le système d’exploitation Windows incluent ce dossier. Le choix de cet emplacement permet également aux utilisateurs qui disposent de niveaux d’accès système minimaux d’exécuter l’application en toute sécurité. L’exemple de code suivant nécessite que vous disposiez d’un formulaire avec un contrôle <xref:System.Windows.Forms.ImageList> déjà ajouté.  
  
    ```vb  
    Public Sub LoadImage()  
       Dim myImage As System.Drawing.Image = _  
         Image.FromFile _  
       (System.Environment.GetFolderPath _  
       (System.Environment.SpecialFolder.Personal) _  
       & "\Image.gif")  
       ImageList1.Images.Add(myImage)  
    End Sub  
    ```  
  
    ```csharp  
    public void addImage()  
    {  
    // Be sure that you use an appropriate escape sequence (such as the   
    // @) when specifying the location of the file.  
       System.Drawing.Image myImage =   
         Image.FromFile  
       (System.Environment.GetFolderPath  
       (System.Environment.SpecialFolder.Personal)  
       + @"\Image.gif");  
       imageList1.Images.Add(myImage);  
    }  
    ```  
  
    ```cpp  
    public:  
       void addImage()  
       {  
       // Replace the bold image in the following sample   
       // with your own icon.  
       // Be sure that you use an appropriate escape sequence (such as   
       // \\) when specifying the location of the file.  
          System::Drawing::Image ^ myImage =   
             Image::FromFile(String::Concat(  
             System::Environment::GetFolderPath(  
             System::Environment::SpecialFolder::Personal),  
             "\\Image.gif"));  
          imageList1->Images->Add(myImage);  
       }  
    ```  
  
### <a name="to-add-images-with-a-key-value"></a>Pour ajouter des images avec une valeur de clé.  
  
- Utilisez l’une des méthodes <xref:System.Windows.Forms.ImageList.ImageCollection.Add%2A> de la propriété <xref:System.Windows.Forms.ImageList.Images%2A> de la liste d’images qui prend une valeur de clé.  
  
     Dans l’exemple de code suivant, le chemin d’accès défini pour l’emplacement de l’image est le dossier **Mes documents** . Cet emplacement est utilisé, car vous pouvez supposer que la plupart des ordinateurs qui exécutent le système d’exploitation Windows incluent ce dossier. Le choix de cet emplacement permet également aux utilisateurs qui disposent de niveaux d’accès système minimaux d’exécuter l’application en toute sécurité. L’exemple de code suivant nécessite que vous disposiez d’un formulaire avec un contrôle <xref:System.Windows.Forms.ImageList> déjà ajouté.  
  
    ```vb  
    Public Sub LoadImage()  
       Dim myImage As System.Drawing.Image = _  
         Image.FromFile _  
       (System.Environment.GetFolderPath _  
       (System.Environment.SpecialFolder.Personal) _  
       & "\Image.gif")  
       ImageList1.Images.Add("myPhoto", myImage)  
    End Sub  
    ```  
  
```csharp  
public void addImage()  
{  
// Be sure that you use an appropriate escape sequence (such as the   
// @) when specifying the location of the file.  
   System.Drawing.Image myImage =   
     Image.FromFile  
   (System.Environment.GetFolderPath  
   (System.Environment.SpecialFolder.Personal)  
   + @"\Image.gif");  
   imageList1.Images.Add("myPhoto", myImage);  
}  
```  
  
### <a name="to-remove-all-images-programmatically"></a>Pour supprimer toutes les images par programmation  
  
- Utilisez la méthode <xref:System.Windows.Forms.ImageList.ImageCollection.Remove%2A> pour supprimer une seule image  
  
     ,-ou-  
  
     Utilisez la méthode <xref:System.Windows.Forms.ImageList.ImageCollection.Clear%2A> pour effacer toutes les images de la liste d’images.  
  
    ```vb  
    ' Removes the first image in the image list  
    ImageList1.Images.Remove(myImage)  
    ' Clears all images in the image list  
    ImageList1.Images.Clear()  
    ```  
  
```csharp  
// Removes the first image in the image list.  
imageList1.Images.Remove(myImage);  
// Clears all images in the image list.  
imageList1.Images.Clear();  
```  
  
### <a name="to-remove-images-by-key"></a>Pour supprimer des images par clé  
  
- Utilisez la méthode <xref:System.Windows.Forms.ImageList.ImageCollection.RemoveByKey%2A> pour supprimer une image unique par sa clé.  
  
    ```vb  
    ' Removes the image named "myPhoto" from the list.  
    ImageList1.Images.RemoveByKey("myPhoto")  
    ```  
  
```csharp  
// Removes the image named "myPhoto" from the list.  
imageList1.Images.RemoveByKey("myPhoto");  
```  
  
## <a name="see-also"></a>Voir aussi

- [ImageList, composant](imagelist-component-windows-forms.md)
- [Vue d'ensemble du composant ImageList](imagelist-component-overview-windows-forms.md)
- [Images, bitmaps et métafichiers](../advanced/images-bitmaps-and-metafiles.md)
