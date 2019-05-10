---
title: 'Procédure : ajouter ou supprimer des images avec le composant ImageList Windows Forms'
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
ms.openlocfilehash: 31ae91958dbc02a2f64945af896b4a2408224d05
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64624033"
---
# <a name="how-to-add-or-remove-images-with-the-windows-forms-imagelist-component"></a>Procédure : ajouter ou supprimer des images avec le composant ImageList Windows Forms
Les formulaires Windows <xref:System.Windows.Forms.ImageList> composant est généralement rempli d’images avant qu’il soit associé à un contrôle. Toutefois, vous pouvez ajouter et supprimer des images après l’association de la liste d’images avec un contrôle.  
  
> [!NOTE]
>  Lorsque vous supprimez des images, vérifiez que le <xref:System.Windows.Forms.ButtonBase.ImageIndex%2A> propriété de tous les contrôles associés est toujours valide.  
  
### <a name="to-add-images-programmatically"></a>Pour ajouter par programmation des images  
  
- Utilisez le <xref:System.Windows.Forms.ImageList.ImageCollection.Add%2A> méthode de la liste d’images <xref:System.Windows.Forms.ImageList.Images%2A> propriété.  
  
     Dans l’exemple de code suivant, le chemin d’accès défini pour l’emplacement de l’image est la **Mes Documents** dossier. Cet emplacement est utilisé, car vous pouvez supposer que la plupart des ordinateurs qui exécutent le système d’exploitation Windows incluent ce dossier. Choix de cet emplacement permet également aux utilisateurs qui ont système minimal des niveaux d’accès plus exécuter en toute sécurité de l’application. L’exemple de code suivant requiert que vous ayez un formulaire comprenant un <xref:System.Windows.Forms.ImageList> contrôle déjà ajouté.  
  
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
  
- Utilisez une de la <xref:System.Windows.Forms.ImageList.ImageCollection.Add%2A> méthodes de la liste d’images <xref:System.Windows.Forms.ImageList.Images%2A> propriété qui accepte une valeur de clé.  
  
     Dans l’exemple de code suivant, le chemin d’accès défini pour l’emplacement de l’image est la **Mes Documents** dossier. Cet emplacement est utilisé, car vous pouvez supposer que la plupart des ordinateurs qui exécutent le système d’exploitation Windows incluent ce dossier. Choix de cet emplacement permet également aux utilisateurs qui ont système minimal des niveaux d’accès plus exécuter en toute sécurité de l’application. L’exemple de code suivant requiert que vous ayez un formulaire comprenant un <xref:System.Windows.Forms.ImageList> contrôle déjà ajouté.  
  
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
  
### <a name="to-remove-all-images-programmatically"></a>Pour supprimer toutes les images par programme  
  
- Utilisez le <xref:System.Windows.Forms.ImageList.ImageCollection.Remove%2A> méthode pour supprimer une image  
  
     , - ou -  
  
     Utilisez le <xref:System.Windows.Forms.ImageList.ImageCollection.Clear%2A> méthode pour effacer toutes les images dans la liste d’images.  
  
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
  
- Utilisez le <xref:System.Windows.Forms.ImageList.ImageCollection.RemoveByKey%2A> méthode pour supprimer une image par sa clé.  
  
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
