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
# <a name="how-to-add-or-remove-images-with-the-windows-forms-imagelist-component"></a><span data-ttu-id="be8fa-102">Procédure : ajouter ou supprimer des images avec le composant ImageList Windows Forms</span><span class="sxs-lookup"><span data-stu-id="be8fa-102">How to: Add or Remove Images with the Windows Forms ImageList Component</span></span>
<span data-ttu-id="be8fa-103">Les formulaires Windows <xref:System.Windows.Forms.ImageList> composant est généralement rempli d’images avant qu’il soit associé à un contrôle.</span><span class="sxs-lookup"><span data-stu-id="be8fa-103">The Windows Forms <xref:System.Windows.Forms.ImageList> component is typically populated with images before it is associated with a control.</span></span> <span data-ttu-id="be8fa-104">Toutefois, vous pouvez ajouter et supprimer des images après l’association de la liste d’images avec un contrôle.</span><span class="sxs-lookup"><span data-stu-id="be8fa-104">However, you can add and remove images after associating the image list with a control.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="be8fa-105">Lorsque vous supprimez des images, vérifiez que le <xref:System.Windows.Forms.ButtonBase.ImageIndex%2A> propriété de tous les contrôles associés est toujours valide.</span><span class="sxs-lookup"><span data-stu-id="be8fa-105">When you remove images, verify that the <xref:System.Windows.Forms.ButtonBase.ImageIndex%2A> property of any associated controls is still valid.</span></span>  
  
### <a name="to-add-images-programmatically"></a><span data-ttu-id="be8fa-106">Pour ajouter par programmation des images</span><span class="sxs-lookup"><span data-stu-id="be8fa-106">To add images programmatically</span></span>  
  
- <span data-ttu-id="be8fa-107">Utilisez le <xref:System.Windows.Forms.ImageList.ImageCollection.Add%2A> méthode de la liste d’images <xref:System.Windows.Forms.ImageList.Images%2A> propriété.</span><span class="sxs-lookup"><span data-stu-id="be8fa-107">Use the <xref:System.Windows.Forms.ImageList.ImageCollection.Add%2A> method of the image list's <xref:System.Windows.Forms.ImageList.Images%2A> property.</span></span>  
  
     <span data-ttu-id="be8fa-108">Dans l’exemple de code suivant, le chemin d’accès défini pour l’emplacement de l’image est la **Mes Documents** dossier.</span><span class="sxs-lookup"><span data-stu-id="be8fa-108">In the following code example, the path set for the location of the image is the **My Documents** folder.</span></span> <span data-ttu-id="be8fa-109">Cet emplacement est utilisé, car vous pouvez supposer que la plupart des ordinateurs qui exécutent le système d’exploitation Windows incluent ce dossier.</span><span class="sxs-lookup"><span data-stu-id="be8fa-109">This location is used because you can assume that most computers that are running the Windows operating system will include this folder.</span></span> <span data-ttu-id="be8fa-110">Choix de cet emplacement permet également aux utilisateurs qui ont système minimal des niveaux d’accès plus exécuter en toute sécurité de l’application.</span><span class="sxs-lookup"><span data-stu-id="be8fa-110">Choosing this location also lets users who have minimal system access levels more safely run the application.</span></span> <span data-ttu-id="be8fa-111">L’exemple de code suivant requiert que vous ayez un formulaire comprenant un <xref:System.Windows.Forms.ImageList> contrôle déjà ajouté.</span><span class="sxs-lookup"><span data-stu-id="be8fa-111">The following code example requires that you have a form with an <xref:System.Windows.Forms.ImageList> control already added.</span></span>  
  
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
  
### <a name="to-add-images-with-a-key-value"></a><span data-ttu-id="be8fa-112">Pour ajouter des images avec une valeur de clé.</span><span class="sxs-lookup"><span data-stu-id="be8fa-112">To add images with a key value.</span></span>  
  
- <span data-ttu-id="be8fa-113">Utilisez une de la <xref:System.Windows.Forms.ImageList.ImageCollection.Add%2A> méthodes de la liste d’images <xref:System.Windows.Forms.ImageList.Images%2A> propriété qui accepte une valeur de clé.</span><span class="sxs-lookup"><span data-stu-id="be8fa-113">Use one of the <xref:System.Windows.Forms.ImageList.ImageCollection.Add%2A> methods of the image list's <xref:System.Windows.Forms.ImageList.Images%2A> property that takes a key value.</span></span>  
  
     <span data-ttu-id="be8fa-114">Dans l’exemple de code suivant, le chemin d’accès défini pour l’emplacement de l’image est la **Mes Documents** dossier.</span><span class="sxs-lookup"><span data-stu-id="be8fa-114">In the following code example, the path set for the location of the image is the **My Documents** folder.</span></span> <span data-ttu-id="be8fa-115">Cet emplacement est utilisé, car vous pouvez supposer que la plupart des ordinateurs qui exécutent le système d’exploitation Windows incluent ce dossier.</span><span class="sxs-lookup"><span data-stu-id="be8fa-115">This location is used because you can assume that most computers that are running the Windows operating system will include this folder.</span></span> <span data-ttu-id="be8fa-116">Choix de cet emplacement permet également aux utilisateurs qui ont système minimal des niveaux d’accès plus exécuter en toute sécurité de l’application.</span><span class="sxs-lookup"><span data-stu-id="be8fa-116">Choosing this location also lets users who have minimal system access levels more safely run the application.</span></span> <span data-ttu-id="be8fa-117">L’exemple de code suivant requiert que vous ayez un formulaire comprenant un <xref:System.Windows.Forms.ImageList> contrôle déjà ajouté.</span><span class="sxs-lookup"><span data-stu-id="be8fa-117">The following code example requires that you have a form with an <xref:System.Windows.Forms.ImageList> control already added.</span></span>  
  
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
  
### <a name="to-remove-all-images-programmatically"></a><span data-ttu-id="be8fa-118">Pour supprimer toutes les images par programme</span><span class="sxs-lookup"><span data-stu-id="be8fa-118">To remove all images programmatically</span></span>  
  
- <span data-ttu-id="be8fa-119">Utilisez le <xref:System.Windows.Forms.ImageList.ImageCollection.Remove%2A> méthode pour supprimer une image</span><span class="sxs-lookup"><span data-stu-id="be8fa-119">Use the <xref:System.Windows.Forms.ImageList.ImageCollection.Remove%2A> method to remove a single image</span></span>  
  
     <span data-ttu-id="be8fa-120">, - ou -</span><span class="sxs-lookup"><span data-stu-id="be8fa-120">,-or-</span></span>  
  
     <span data-ttu-id="be8fa-121">Utilisez le <xref:System.Windows.Forms.ImageList.ImageCollection.Clear%2A> méthode pour effacer toutes les images dans la liste d’images.</span><span class="sxs-lookup"><span data-stu-id="be8fa-121">Use the <xref:System.Windows.Forms.ImageList.ImageCollection.Clear%2A> method to clear all images in the image list.</span></span>  
  
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
  
### <a name="to-remove-images-by-key"></a><span data-ttu-id="be8fa-122">Pour supprimer des images par clé</span><span class="sxs-lookup"><span data-stu-id="be8fa-122">To remove images by key</span></span>  
  
- <span data-ttu-id="be8fa-123">Utilisez le <xref:System.Windows.Forms.ImageList.ImageCollection.RemoveByKey%2A> méthode pour supprimer une image par sa clé.</span><span class="sxs-lookup"><span data-stu-id="be8fa-123">Use the <xref:System.Windows.Forms.ImageList.ImageCollection.RemoveByKey%2A> method to remove a single image by its key.</span></span>  
  
    ```vb  
    ' Removes the image named "myPhoto" from the list.  
    ImageList1.Images.RemoveByKey("myPhoto")  
    ```  
  
```csharp  
// Removes the image named "myPhoto" from the list.  
imageList1.Images.RemoveByKey("myPhoto");  
```  
  
## <a name="see-also"></a><span data-ttu-id="be8fa-124">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="be8fa-124">See also</span></span>

- [<span data-ttu-id="be8fa-125">ImageList, composant</span><span class="sxs-lookup"><span data-stu-id="be8fa-125">ImageList Component</span></span>](imagelist-component-windows-forms.md)
- [<span data-ttu-id="be8fa-126">Vue d'ensemble du composant ImageList</span><span class="sxs-lookup"><span data-stu-id="be8fa-126">ImageList Component Overview</span></span>](imagelist-component-overview-windows-forms.md)
- [<span data-ttu-id="be8fa-127">Images, bitmaps et métafichiers</span><span class="sxs-lookup"><span data-stu-id="be8fa-127">Images, Bitmaps, and Metafiles</span></span>](../advanced/images-bitmaps-and-metafiles.md)
