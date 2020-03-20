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
# <a name="how-to-set-pictures-at-run-time-windows-forms"></a><span data-ttu-id="2ac02-102">Comment : définir des images au moment de l'exécution (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="2ac02-102">How to: Set Pictures at Run Time (Windows Forms)</span></span>
<span data-ttu-id="2ac02-103">Vous pouvez configurer l’image affichée <xref:System.Windows.Forms.PictureBox> par un contrôle Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="2ac02-103">You can programmatically set the image displayed by a Windows Forms <xref:System.Windows.Forms.PictureBox> control.</span></span>  
  
### <a name="to-set-a-picture-programmatically"></a><span data-ttu-id="2ac02-104">Pour définir une image programmatique</span><span class="sxs-lookup"><span data-stu-id="2ac02-104">To set a picture programmatically</span></span>  
  
- <span data-ttu-id="2ac02-105">Réglez <xref:System.Windows.Forms.PictureBox.Image%2A> la <xref:System.Drawing.Image.FromFile%2A> propriété <xref:System.Drawing.Image> en utilisant la méthode de la classe.</span><span class="sxs-lookup"><span data-stu-id="2ac02-105">Set the <xref:System.Windows.Forms.PictureBox.Image%2A> property using the <xref:System.Drawing.Image.FromFile%2A> method of the <xref:System.Drawing.Image> class.</span></span>  
  
     <span data-ttu-id="2ac02-106">Dans l’exemple ci-dessous, le chemin défini pour l’emplacement de l’image est le dossier Mes Documents.</span><span class="sxs-lookup"><span data-stu-id="2ac02-106">In the example below, the path set for the location of the image is the My Documents folder.</span></span> <span data-ttu-id="2ac02-107">Cela est fait, parce que vous pouvez supposer que la plupart des ordinateurs exécutant le système d’exploitation Windows inclura ce répertoire.</span><span class="sxs-lookup"><span data-stu-id="2ac02-107">This is done, because you can assume that most computers running the Windows operating system will include this directory.</span></span> <span data-ttu-id="2ac02-108">Cela permet également aux utilisateurs avec des niveaux d’accès minimum au système d’exécuter l’application en toute sécurité.</span><span class="sxs-lookup"><span data-stu-id="2ac02-108">This also allows users with minimal system access levels to safely run the application.</span></span> <span data-ttu-id="2ac02-109">L’exemple ci-dessous suppose <xref:System.Windows.Forms.PictureBox> un formulaire avec un contrôle déjà ajouté.</span><span class="sxs-lookup"><span data-stu-id="2ac02-109">The example below assumes a form with a <xref:System.Windows.Forms.PictureBox> control already added.</span></span>  
  
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
  
### <a name="to-clear-a-graphic"></a><span data-ttu-id="2ac02-110">Pour effacer un graphique</span><span class="sxs-lookup"><span data-stu-id="2ac02-110">To clear a graphic</span></span>  
  
- <span data-ttu-id="2ac02-111">Tout d’abord, relâchez la mémoire utilisée par l’image, puis effacez le graphique.</span><span class="sxs-lookup"><span data-stu-id="2ac02-111">First, release the memory being used by the image, and then clear the graphic.</span></span> <span data-ttu-id="2ac02-112">La collecte des ordures libérera la mémoire plus tard si la gestion de la mémoire devient un problème.</span><span class="sxs-lookup"><span data-stu-id="2ac02-112">Garbage collection will free up the memory later if memory management becomes a problem.</span></span>  
  
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
    > <span data-ttu-id="2ac02-113">Pour plus d’informations sur <xref:System.Drawing.Image.Dispose%2A> les raisons pour lesquelles vous devriez utiliser la méthode de cette façon, voir [Cleaning Up Unmanaged Resources](../../../standard/garbage-collection/unmanaged.md).</span><span class="sxs-lookup"><span data-stu-id="2ac02-113">For more information on why you should use the <xref:System.Drawing.Image.Dispose%2A> method in this way, see [Cleaning Up Unmanaged Resources](../../../standard/garbage-collection/unmanaged.md).</span></span>  
  
     <span data-ttu-id="2ac02-114">Ce code effacera l’image même si un graphique a été chargé dans le contrôle au moment de la conception.</span><span class="sxs-lookup"><span data-stu-id="2ac02-114">This code will clear the image even if a graphic was loaded into the control at design time.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2ac02-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2ac02-115">See also</span></span>

- <xref:System.Windows.Forms.PictureBox>
- <xref:System.Drawing.Image.FromFile%2A?displayProperty=nameWithType>
- [<span data-ttu-id="2ac02-116">Vue d'ensemble du contrôle PictureBox</span><span class="sxs-lookup"><span data-stu-id="2ac02-116">PictureBox Control Overview</span></span>](picturebox-control-overview-windows-forms.md)
- [<span data-ttu-id="2ac02-117">Comment : charger une image à l'aide du concepteur</span><span class="sxs-lookup"><span data-stu-id="2ac02-117">How to: Load a Picture Using the Designer</span></span>](how-to-load-a-picture-using-the-designer-windows-forms.md)
- [<span data-ttu-id="2ac02-118">Comment : modifier la taille ou l'emplacement d'une image au moment de l'exécution</span><span class="sxs-lookup"><span data-stu-id="2ac02-118">How to: Modify the Size or Placement of a Picture at Run Time</span></span>](how-to-modify-the-size-or-placement-of-a-picture-at-run-time-windows-forms.md)
- [<span data-ttu-id="2ac02-119">PictureBox, contrôle</span><span class="sxs-lookup"><span data-stu-id="2ac02-119">PictureBox Control</span></span>](picturebox-control-windows-forms.md)
