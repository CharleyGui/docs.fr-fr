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
ms.openlocfilehash: 9bb094ce0b7945f23a2e9b8614e56c9492d5f832
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76736025"
---
# <a name="how-to-modify-the-size-or-placement-of-a-picture-at-run-time-windows-forms"></a><span data-ttu-id="275c8-102">Comment : modifier la taille ou l'emplacement d'une image au moment de l'exécution (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="275c8-102">How to: Modify the Size or Placement of a Picture at Run Time (Windows Forms)</span></span>
<span data-ttu-id="275c8-103">Si vous utilisez le contrôle Windows Forms <xref:System.Windows.Forms.PictureBox> sur un formulaire, vous pouvez définir la propriété <xref:System.Windows.Forms.PictureBox.SizeMode%2A> sur ce dernier pour qu’il :</span><span class="sxs-lookup"><span data-stu-id="275c8-103">If you use the Windows Forms <xref:System.Windows.Forms.PictureBox> control on a form, you can set the <xref:System.Windows.Forms.PictureBox.SizeMode%2A> property on it to:</span></span>  
  
- <span data-ttu-id="275c8-104">Aligner le coin supérieur gauche de l’image avec l’angle supérieur gauche du contrôle</span><span class="sxs-lookup"><span data-stu-id="275c8-104">Align the picture's upper left corner with the control's upper left corner</span></span>  
  
- <span data-ttu-id="275c8-105">Centrer l’image dans le contrôle</span><span class="sxs-lookup"><span data-stu-id="275c8-105">Center the picture within the control</span></span>  
  
- <span data-ttu-id="275c8-106">Ajuster la taille du contrôle pour ajuster l’image qu’il affiche</span><span class="sxs-lookup"><span data-stu-id="275c8-106">Adjust the size of the control to fit the picture it displays</span></span>  
  
- <span data-ttu-id="275c8-107">Étirer une image affichée pour l’adapter au contrôle</span><span class="sxs-lookup"><span data-stu-id="275c8-107">Stretch any picture it displays to fit the control</span></span>  
  
 <span data-ttu-id="275c8-108">L’étirement d’une image (en particulier un format bitmap) peut entraîner une perte de qualité d’image.</span><span class="sxs-lookup"><span data-stu-id="275c8-108">Stretching a picture (especially one in bitmap format) can produce a loss in image quality.</span></span> <span data-ttu-id="275c8-109">Les fichiers de données, qui sont des listes d’instructions graphiques pour dessiner des images au moment de l’exécution, sont mieux adaptés à l’étirement que les bitmaps.</span><span class="sxs-lookup"><span data-stu-id="275c8-109">Metafiles, which are lists of graphics instructions for drawing images at run time, are better suited for stretching than bitmaps are.</span></span>  
  
### <a name="to-set-the-sizemode-property-at-run-time"></a><span data-ttu-id="275c8-110">Pour définir la propriété ModeAffichage au moment de l’exécution</span><span class="sxs-lookup"><span data-stu-id="275c8-110">To set the SizeMode property at run time</span></span>  
  
1. <span data-ttu-id="275c8-111">Définissez <xref:System.Windows.Forms.PictureBox.SizeMode%2A> sur <xref:System.Windows.Forms.PictureBoxSizeMode.Normal> (valeur par défaut), <xref:System.Windows.Forms.PictureBoxSizeMode.AutoSize>, <xref:System.Windows.Forms.PictureBoxSizeMode.CenterImage>ou <xref:System.Windows.Forms.PictureBoxSizeMode.StretchImage>.</span><span class="sxs-lookup"><span data-stu-id="275c8-111">Set <xref:System.Windows.Forms.PictureBox.SizeMode%2A> to <xref:System.Windows.Forms.PictureBoxSizeMode.Normal> (the default), <xref:System.Windows.Forms.PictureBoxSizeMode.AutoSize>, <xref:System.Windows.Forms.PictureBoxSizeMode.CenterImage>, or <xref:System.Windows.Forms.PictureBoxSizeMode.StretchImage>.</span></span> <span data-ttu-id="275c8-112"><xref:System.Windows.Forms.PictureBoxSizeMode.Normal> signifie que l’image est placée dans le coin supérieur gauche du contrôle ; Si l’image est plus grande que le contrôle, ses bords inférieur et droit sont découpés.</span><span class="sxs-lookup"><span data-stu-id="275c8-112"><xref:System.Windows.Forms.PictureBoxSizeMode.Normal> means that the image is placed in the control's upper-left corner; if the image is larger than the control, its lower and right edges are clipped.</span></span> <span data-ttu-id="275c8-113"><xref:System.Windows.Forms.PictureBoxSizeMode.CenterImage> signifie que l’image est centrée dans le contrôle ; Si l’image est plus grande que le contrôle, les bords extérieurs de l’image sont découpés.</span><span class="sxs-lookup"><span data-stu-id="275c8-113"><xref:System.Windows.Forms.PictureBoxSizeMode.CenterImage> means that the image is centered within the control; if the image is larger than the control, the picture's outside edges are clipped.</span></span> <span data-ttu-id="275c8-114"><xref:System.Windows.Forms.PictureBoxSizeMode.AutoSize> signifie que la taille du contrôle est ajustée à la taille de l’image.</span><span class="sxs-lookup"><span data-stu-id="275c8-114"><xref:System.Windows.Forms.PictureBoxSizeMode.AutoSize> means that the size of the control is adjusted to the size of the image.</span></span> <span data-ttu-id="275c8-115"><xref:System.Windows.Forms.PictureBoxSizeMode.StretchImage> est l’inverse et signifie que la taille de l’image est ajustée à la taille du contrôle.</span><span class="sxs-lookup"><span data-stu-id="275c8-115"><xref:System.Windows.Forms.PictureBoxSizeMode.StretchImage> is the reverse, and means that the size of the image is adjusted to the size of the control.</span></span>  
  
     <span data-ttu-id="275c8-116">Dans l’exemple ci-dessous, le chemin d’accès défini pour l’emplacement de l’image est le dossier Mes documents.</span><span class="sxs-lookup"><span data-stu-id="275c8-116">In the example below, the path set for the location of the image is the My Documents folder.</span></span> <span data-ttu-id="275c8-117">En effet, vous pouvez supposer que la plupart des ordinateurs exécutant le système d’exploitation Windows incluent ce répertoire.</span><span class="sxs-lookup"><span data-stu-id="275c8-117">This is done, because you can assume that most computers running the Windows operating system will include this directory.</span></span> <span data-ttu-id="275c8-118">Cela permet également aux utilisateurs avec des niveaux d’accès minimum au système d’exécuter l’application en toute sécurité.</span><span class="sxs-lookup"><span data-stu-id="275c8-118">This also allows users with minimal system access levels to safely run the application.</span></span> <span data-ttu-id="275c8-119">L’exemple ci-dessous suppose un formulaire avec un contrôle de <xref:System.Windows.Forms.PictureBox> déjà ajouté.</span><span class="sxs-lookup"><span data-stu-id="275c8-119">The example below assumes a form with a <xref:System.Windows.Forms.PictureBox> control already added.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="275c8-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="275c8-120">See also</span></span>

- <xref:System.Windows.Forms.PictureBox>
- [<span data-ttu-id="275c8-121">Guide pratique pour charger une image à l'aide du concepteur</span><span class="sxs-lookup"><span data-stu-id="275c8-121">How to: Load a Picture Using the Designer</span></span>](how-to-load-a-picture-using-the-designer-windows-forms.md)
- [<span data-ttu-id="275c8-122">Vue d’ensemble du contrôle PictureBox</span><span class="sxs-lookup"><span data-stu-id="275c8-122">PictureBox Control Overview</span></span>](picturebox-control-overview-windows-forms.md)
- [<span data-ttu-id="275c8-123">Guide pratique pour définir des images au moment de l'exécution</span><span class="sxs-lookup"><span data-stu-id="275c8-123">How to: Set Pictures at Run Time</span></span>](how-to-set-pictures-at-run-time-windows-forms.md)
- [<span data-ttu-id="275c8-124">PictureBox, contrôle</span><span class="sxs-lookup"><span data-stu-id="275c8-124">PictureBox Control</span></span>](picturebox-control-windows-forms.md)
