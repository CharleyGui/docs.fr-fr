---
title: 'Procédure : Définir des images au moment de l’exécution (Windows Forms)'
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
ms.openlocfilehash: 99d78a275c8ad8f55d9b0832a794545b65da7e20
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69917525"
---
# <a name="how-to-set-pictures-at-run-time-windows-forms"></a><span data-ttu-id="d9fcb-102">Procédure : Définir des images au moment de l’exécution (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="d9fcb-102">How to: Set Pictures at Run Time (Windows Forms)</span></span>
<span data-ttu-id="d9fcb-103">Vous pouvez définir par programmation l’image affichée par un contrôle Windows Forms <xref:System.Windows.Forms.PictureBox> .</span><span class="sxs-lookup"><span data-stu-id="d9fcb-103">You can programmatically set the image displayed by a Windows Forms <xref:System.Windows.Forms.PictureBox> control.</span></span>  
  
### <a name="to-set-a-picture-programmatically"></a><span data-ttu-id="d9fcb-104">Pour définir une image par programmation</span><span class="sxs-lookup"><span data-stu-id="d9fcb-104">To set a picture programmatically</span></span>  
  
- <span data-ttu-id="d9fcb-105">Définissez la <xref:System.Windows.Forms.PictureBox.Image%2A> propriété à l' <xref:System.Drawing.Image.FromFile%2A> aide de la <xref:System.Drawing.Image> méthode de la classe.</span><span class="sxs-lookup"><span data-stu-id="d9fcb-105">Set the <xref:System.Windows.Forms.PictureBox.Image%2A> property using the <xref:System.Drawing.Image.FromFile%2A> method of the <xref:System.Drawing.Image> class.</span></span>  
  
     <span data-ttu-id="d9fcb-106">Dans l’exemple ci-dessous, le chemin d’accès défini pour l’emplacement de l’image est le dossier Mes documents.</span><span class="sxs-lookup"><span data-stu-id="d9fcb-106">In the example below, the path set for the location of the image is the My Documents folder.</span></span> <span data-ttu-id="d9fcb-107">En effet, vous pouvez supposer que la plupart des ordinateurs exécutant le système d’exploitation Windows incluent ce répertoire.</span><span class="sxs-lookup"><span data-stu-id="d9fcb-107">This is done, because you can assume that most computers running the Windows operating system will include this directory.</span></span> <span data-ttu-id="d9fcb-108">Cela permet également aux utilisateurs avec des niveaux d’accès minimum au système d’exécuter l’application en toute sécurité.</span><span class="sxs-lookup"><span data-stu-id="d9fcb-108">This also allows users with minimal system access levels to safely run the application.</span></span> <span data-ttu-id="d9fcb-109">L’exemple ci-dessous suppose qu’un formulaire <xref:System.Windows.Forms.PictureBox> avec un contrôle a déjà été ajouté.</span><span class="sxs-lookup"><span data-stu-id="d9fcb-109">The example below assumes a form with a <xref:System.Windows.Forms.PictureBox> control already added.</span></span>  
  
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
  
### <a name="to-clear-a-graphic"></a><span data-ttu-id="d9fcb-110">Pour effacer un graphique</span><span class="sxs-lookup"><span data-stu-id="d9fcb-110">To clear a graphic</span></span>  
  
- <span data-ttu-id="d9fcb-111">Tout d’abord, libérez la mémoire utilisée par l’image, puis effacez le graphique.</span><span class="sxs-lookup"><span data-stu-id="d9fcb-111">First, release the memory being used by the image, and then clear the graphic.</span></span> <span data-ttu-id="d9fcb-112">Le garbage collection libérera de la mémoire plus tard si la gestion de la mémoire devient un problème.</span><span class="sxs-lookup"><span data-stu-id="d9fcb-112">Garbage collection will free up the memory later if memory management becomes a problem.</span></span>  
  
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
    > <span data-ttu-id="d9fcb-113">Pour plus d’informations sur les raisons pour lesquelles <xref:System.Drawing.Image.Dispose%2A> vous devez utiliser la méthode de cette manière, consultez [nettoyage des ressources non managées](../../../standard/garbage-collection/unmanaged.md).</span><span class="sxs-lookup"><span data-stu-id="d9fcb-113">For more information on why you should use the <xref:System.Drawing.Image.Dispose%2A> method in this way, see [Cleaning Up Unmanaged Resources](../../../standard/garbage-collection/unmanaged.md).</span></span>  
  
     <span data-ttu-id="d9fcb-114">Ce code efface l’image même si un graphique a été chargé dans le contrôle au moment du Design.</span><span class="sxs-lookup"><span data-stu-id="d9fcb-114">This code will clear the image even if a graphic was loaded into the control at design time.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d9fcb-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d9fcb-115">See also</span></span>

- <xref:System.Windows.Forms.PictureBox>
- <xref:System.Drawing.Image.FromFile%2A?displayProperty=nameWithType>
- [<span data-ttu-id="d9fcb-116">Vue d’ensemble du contrôle PictureBox</span><span class="sxs-lookup"><span data-stu-id="d9fcb-116">PictureBox Control Overview</span></span>](picturebox-control-overview-windows-forms.md)
- [<span data-ttu-id="d9fcb-117">Guide pratique pour Charger une image à l’aide du concepteur</span><span class="sxs-lookup"><span data-stu-id="d9fcb-117">How to: Load a Picture Using the Designer</span></span>](how-to-load-a-picture-using-the-designer-windows-forms.md)
- [<span data-ttu-id="d9fcb-118">Guide pratique : Modifier la taille ou l’emplacement d’une image au moment de l’exécution</span><span class="sxs-lookup"><span data-stu-id="d9fcb-118">How to: Modify the Size or Placement of a Picture at Run Time</span></span>](how-to-modify-the-size-or-placement-of-a-picture-at-run-time-windows-forms.md)
- [<span data-ttu-id="d9fcb-119">PictureBox, contrôle</span><span class="sxs-lookup"><span data-stu-id="d9fcb-119">PictureBox Control</span></span>](picturebox-control-windows-forms.md)
