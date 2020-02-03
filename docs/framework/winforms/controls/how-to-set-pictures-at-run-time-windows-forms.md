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
ms.openlocfilehash: bd0509c05fd9c1cfc0c631fcd613c64d20296f6b
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76746737"
---
# <a name="how-to-set-pictures-at-run-time-windows-forms"></a><span data-ttu-id="c9953-102">Comment : définir des images au moment de l'exécution (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="c9953-102">How to: Set Pictures at Run Time (Windows Forms)</span></span>
<span data-ttu-id="c9953-103">Vous pouvez définir par programmation l’image affichée par un contrôle Windows Forms <xref:System.Windows.Forms.PictureBox>.</span><span class="sxs-lookup"><span data-stu-id="c9953-103">You can programmatically set the image displayed by a Windows Forms <xref:System.Windows.Forms.PictureBox> control.</span></span>  
  
### <a name="to-set-a-picture-programmatically"></a><span data-ttu-id="c9953-104">Pour définir une image par programmation</span><span class="sxs-lookup"><span data-stu-id="c9953-104">To set a picture programmatically</span></span>  
  
- <span data-ttu-id="c9953-105">Définissez la propriété <xref:System.Windows.Forms.PictureBox.Image%2A> à l’aide de la méthode <xref:System.Drawing.Image.FromFile%2A> de la classe <xref:System.Drawing.Image>.</span><span class="sxs-lookup"><span data-stu-id="c9953-105">Set the <xref:System.Windows.Forms.PictureBox.Image%2A> property using the <xref:System.Drawing.Image.FromFile%2A> method of the <xref:System.Drawing.Image> class.</span></span>  
  
     <span data-ttu-id="c9953-106">Dans l’exemple ci-dessous, le chemin d’accès défini pour l’emplacement de l’image est le dossier Mes documents.</span><span class="sxs-lookup"><span data-stu-id="c9953-106">In the example below, the path set for the location of the image is the My Documents folder.</span></span> <span data-ttu-id="c9953-107">En effet, vous pouvez supposer que la plupart des ordinateurs exécutant le système d’exploitation Windows incluent ce répertoire.</span><span class="sxs-lookup"><span data-stu-id="c9953-107">This is done, because you can assume that most computers running the Windows operating system will include this directory.</span></span> <span data-ttu-id="c9953-108">Cela permet également aux utilisateurs avec des niveaux d’accès minimum au système d’exécuter l’application en toute sécurité.</span><span class="sxs-lookup"><span data-stu-id="c9953-108">This also allows users with minimal system access levels to safely run the application.</span></span> <span data-ttu-id="c9953-109">L’exemple ci-dessous suppose un formulaire avec un contrôle de <xref:System.Windows.Forms.PictureBox> déjà ajouté.</span><span class="sxs-lookup"><span data-stu-id="c9953-109">The example below assumes a form with a <xref:System.Windows.Forms.PictureBox> control already added.</span></span>  
  
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
  
### <a name="to-clear-a-graphic"></a><span data-ttu-id="c9953-110">Pour effacer un graphique</span><span class="sxs-lookup"><span data-stu-id="c9953-110">To clear a graphic</span></span>  
  
- <span data-ttu-id="c9953-111">Tout d’abord, libérez la mémoire utilisée par l’image, puis effacez le graphique.</span><span class="sxs-lookup"><span data-stu-id="c9953-111">First, release the memory being used by the image, and then clear the graphic.</span></span> <span data-ttu-id="c9953-112">Le garbage collection libérera de la mémoire plus tard si la gestion de la mémoire devient un problème.</span><span class="sxs-lookup"><span data-stu-id="c9953-112">Garbage collection will free up the memory later if memory management becomes a problem.</span></span>  
  
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
    > <span data-ttu-id="c9953-113">Pour plus d’informations sur les raisons pour lesquelles vous devez utiliser la méthode <xref:System.Drawing.Image.Dispose%2A> de cette manière, consultez [nettoyage des ressources non managées](../../../standard/garbage-collection/unmanaged.md).</span><span class="sxs-lookup"><span data-stu-id="c9953-113">For more information on why you should use the <xref:System.Drawing.Image.Dispose%2A> method in this way, see [Cleaning Up Unmanaged Resources](../../../standard/garbage-collection/unmanaged.md).</span></span>  
  
     <span data-ttu-id="c9953-114">Ce code efface l’image même si un graphique a été chargé dans le contrôle au moment du Design.</span><span class="sxs-lookup"><span data-stu-id="c9953-114">This code will clear the image even if a graphic was loaded into the control at design time.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c9953-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c9953-115">See also</span></span>

- <xref:System.Windows.Forms.PictureBox>
- <xref:System.Drawing.Image.FromFile%2A?displayProperty=nameWithType>
- [<span data-ttu-id="c9953-116">Vue d’ensemble du contrôle PictureBox</span><span class="sxs-lookup"><span data-stu-id="c9953-116">PictureBox Control Overview</span></span>](picturebox-control-overview-windows-forms.md)
- [<span data-ttu-id="c9953-117">Guide pratique pour charger une image à l'aide du concepteur</span><span class="sxs-lookup"><span data-stu-id="c9953-117">How to: Load a Picture Using the Designer</span></span>](how-to-load-a-picture-using-the-designer-windows-forms.md)
- [<span data-ttu-id="c9953-118">Guide pratique pour modifier la taille ou l'emplacement d'une image au moment de l'exécution</span><span class="sxs-lookup"><span data-stu-id="c9953-118">How to: Modify the Size or Placement of a Picture at Run Time</span></span>](how-to-modify-the-size-or-placement-of-a-picture-at-run-time-windows-forms.md)
- [<span data-ttu-id="c9953-119">PictureBox, contrôle</span><span class="sxs-lookup"><span data-stu-id="c9953-119">PictureBox Control</span></span>](picturebox-control-windows-forms.md)
