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
ms.openlocfilehash: e045be7ea9407bc379b0c22282fcd2184ff5db51
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79182302"
---
# <a name="how-to-add-or-remove-images-with-the-windows-forms-imagelist-component"></a><span data-ttu-id="1363e-102">Comment : ajouter ou supprimer des images avec le composant ImageList Windows Forms</span><span class="sxs-lookup"><span data-stu-id="1363e-102">How to: Add or Remove Images with the Windows Forms ImageList Component</span></span>
<span data-ttu-id="1363e-103">Le composant <xref:System.Windows.Forms.ImageList> Windows Forms est généralement peuplé d’images avant d’être associé à un contrôle.</span><span class="sxs-lookup"><span data-stu-id="1363e-103">The Windows Forms <xref:System.Windows.Forms.ImageList> component is typically populated with images before it is associated with a control.</span></span> <span data-ttu-id="1363e-104">Cependant, vous pouvez ajouter et supprimer des images après avoir associé la liste d’images avec un contrôle.</span><span class="sxs-lookup"><span data-stu-id="1363e-104">However, you can add and remove images after associating the image list with a control.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="1363e-105">Lorsque vous supprimez des <xref:System.Windows.Forms.ButtonBase.ImageIndex%2A> images, vérifiez que la propriété de tous les contrôles associés est toujours valide.</span><span class="sxs-lookup"><span data-stu-id="1363e-105">When you remove images, verify that the <xref:System.Windows.Forms.ButtonBase.ImageIndex%2A> property of any associated controls is still valid.</span></span>  
  
### <a name="to-add-images-programmatically"></a><span data-ttu-id="1363e-106">Pour ajouter des images programmatiquement</span><span class="sxs-lookup"><span data-stu-id="1363e-106">To add images programmatically</span></span>  
  
- <span data-ttu-id="1363e-107">Utilisez <xref:System.Windows.Forms.ImageList.ImageCollection.Add%2A> la méthode de la <xref:System.Windows.Forms.ImageList.Images%2A> propriété de la liste d’images.</span><span class="sxs-lookup"><span data-stu-id="1363e-107">Use the <xref:System.Windows.Forms.ImageList.ImageCollection.Add%2A> method of the image list's <xref:System.Windows.Forms.ImageList.Images%2A> property.</span></span>  
  
     <span data-ttu-id="1363e-108">Dans l’exemple de code suivant, le chemin défini pour l’emplacement de l’image est le dossier **Mes Documents.**</span><span class="sxs-lookup"><span data-stu-id="1363e-108">In the following code example, the path set for the location of the image is the **My Documents** folder.</span></span> <span data-ttu-id="1363e-109">Cet emplacement est utilisé parce que vous pouvez supposer que la plupart des ordinateurs qui exécutent le système d’exploitation Windows inclura ce dossier.</span><span class="sxs-lookup"><span data-stu-id="1363e-109">This location is used because you can assume that most computers that are running the Windows operating system will include this folder.</span></span> <span data-ttu-id="1363e-110">Le choix de cet emplacement permet également aux utilisateurs qui ont des niveaux d’accès au système minimal d’exécuter l’application en toute sécurité.</span><span class="sxs-lookup"><span data-stu-id="1363e-110">Choosing this location also lets users who have minimal system access levels more safely run the application.</span></span> <span data-ttu-id="1363e-111">L’exemple de code suivant exige <xref:System.Windows.Forms.ImageList> que vous ayez un formulaire avec un contrôle déjà ajouté.</span><span class="sxs-lookup"><span data-stu-id="1363e-111">The following code example requires that you have a form with an <xref:System.Windows.Forms.ImageList> control already added.</span></span>  
  
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
  
### <a name="to-add-images-with-a-key-value"></a><span data-ttu-id="1363e-112">Pour ajouter des images avec une valeur clé.</span><span class="sxs-lookup"><span data-stu-id="1363e-112">To add images with a key value.</span></span>  
  
- <span data-ttu-id="1363e-113">Utilisez l’une des <xref:System.Windows.Forms.ImageList.ImageCollection.Add%2A> méthodes de <xref:System.Windows.Forms.ImageList.Images%2A> la propriété de la liste d’images qui prend une valeur clé.</span><span class="sxs-lookup"><span data-stu-id="1363e-113">Use one of the <xref:System.Windows.Forms.ImageList.ImageCollection.Add%2A> methods of the image list's <xref:System.Windows.Forms.ImageList.Images%2A> property that takes a key value.</span></span>  
  
     <span data-ttu-id="1363e-114">Dans l’exemple de code suivant, le chemin défini pour l’emplacement de l’image est le dossier **Mes Documents.**</span><span class="sxs-lookup"><span data-stu-id="1363e-114">In the following code example, the path set for the location of the image is the **My Documents** folder.</span></span> <span data-ttu-id="1363e-115">Cet emplacement est utilisé parce que vous pouvez supposer que la plupart des ordinateurs qui exécutent le système d’exploitation Windows inclura ce dossier.</span><span class="sxs-lookup"><span data-stu-id="1363e-115">This location is used because you can assume that most computers that are running the Windows operating system will include this folder.</span></span> <span data-ttu-id="1363e-116">Le choix de cet emplacement permet également aux utilisateurs qui ont des niveaux d’accès au système minimal d’exécuter l’application en toute sécurité.</span><span class="sxs-lookup"><span data-stu-id="1363e-116">Choosing this location also lets users who have minimal system access levels more safely run the application.</span></span> <span data-ttu-id="1363e-117">L’exemple de code suivant exige <xref:System.Windows.Forms.ImageList> que vous ayez un formulaire avec un contrôle déjà ajouté.</span><span class="sxs-lookup"><span data-stu-id="1363e-117">The following code example requires that you have a form with an <xref:System.Windows.Forms.ImageList> control already added.</span></span>  
  
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
  
### <a name="to-remove-all-images-programmatically"></a><span data-ttu-id="1363e-118">Supprimer toutes les images programmatiquement</span><span class="sxs-lookup"><span data-stu-id="1363e-118">To remove all images programmatically</span></span>  
  
- <span data-ttu-id="1363e-119">Utilisez <xref:System.Windows.Forms.ImageList.ImageCollection.Remove%2A> la méthode pour supprimer une seule image</span><span class="sxs-lookup"><span data-stu-id="1363e-119">Use the <xref:System.Windows.Forms.ImageList.ImageCollection.Remove%2A> method to remove a single image</span></span>  
  
     <span data-ttu-id="1363e-120">,-ou-</span><span class="sxs-lookup"><span data-stu-id="1363e-120">,-or-</span></span>  
  
     <span data-ttu-id="1363e-121">Utilisez <xref:System.Windows.Forms.ImageList.ImageCollection.Clear%2A> la méthode pour effacer toutes les images de la liste d’images.</span><span class="sxs-lookup"><span data-stu-id="1363e-121">Use the <xref:System.Windows.Forms.ImageList.ImageCollection.Clear%2A> method to clear all images in the image list.</span></span>  
  
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
  
### <a name="to-remove-images-by-key"></a><span data-ttu-id="1363e-122">Supprimer les images par clé</span><span class="sxs-lookup"><span data-stu-id="1363e-122">To remove images by key</span></span>  
  
- <span data-ttu-id="1363e-123">Utilisez <xref:System.Windows.Forms.ImageList.ImageCollection.RemoveByKey%2A> la méthode pour supprimer une seule image par sa clé.</span><span class="sxs-lookup"><span data-stu-id="1363e-123">Use the <xref:System.Windows.Forms.ImageList.ImageCollection.RemoveByKey%2A> method to remove a single image by its key.</span></span>  
  
    ```vb  
    ' Removes the image named "myPhoto" from the list.  
    ImageList1.Images.RemoveByKey("myPhoto")  
    ```  
  
```csharp  
// Removes the image named "myPhoto" from the list.  
imageList1.Images.RemoveByKey("myPhoto");  
```  
  
## <a name="see-also"></a><span data-ttu-id="1363e-124">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="1363e-124">See also</span></span>

- [<span data-ttu-id="1363e-125">ImageList, composant</span><span class="sxs-lookup"><span data-stu-id="1363e-125">ImageList Component</span></span>](imagelist-component-windows-forms.md)
- [<span data-ttu-id="1363e-126">Vue d’ensemble du composant ImageList</span><span class="sxs-lookup"><span data-stu-id="1363e-126">ImageList Component Overview</span></span>](imagelist-component-overview-windows-forms.md)
- [<span data-ttu-id="1363e-127">Images, bitmaps et métafichiers</span><span class="sxs-lookup"><span data-stu-id="1363e-127">Images, Bitmaps, and Metafiles</span></span>](../advanced/images-bitmaps-and-metafiles.md)
