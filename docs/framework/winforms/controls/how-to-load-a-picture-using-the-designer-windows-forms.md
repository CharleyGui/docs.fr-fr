---
title: "Comment : charger une image à l'aide du concepteur"
ms.date: 03/30/2017
helpviewer_keywords:
- picture formats
- images [Windows Forms], displaying on Windows Forms
- pictures [Windows Forms], displaying
- forms [Windows Forms], displaying images
- PictureBox control [Windows Forms], adding pictures
ms.assetid: 4dc7b973-afb1-4276-8322-20825af96655
ms.openlocfilehash: 12b90d561a18fcffaafb9c45b7fa6be6dd060215
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76736331"
---
# <a name="how-to-load-a-picture-using-the-designer-windows-forms"></a><span data-ttu-id="b1936-102">Comment : charger une image à l'aide du concepteur (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="b1936-102">How to: Load a Picture Using the Designer (Windows Forms)</span></span>

<span data-ttu-id="b1936-103">Avec le contrôle Windows Forms <xref:System.Windows.Forms.PictureBox>, vous pouvez charger et afficher une image sur un formulaire au moment du design en affectant une image valide à la propriété <xref:System.Windows.Forms.PictureBox.Image%2A>.</span><span class="sxs-lookup"><span data-stu-id="b1936-103">With the Windows Forms <xref:System.Windows.Forms.PictureBox> control, you can load and display a picture on a form at design time by setting the <xref:System.Windows.Forms.PictureBox.Image%2A> property to a valid picture.</span></span> <span data-ttu-id="b1936-104">Le tableau suivant présente les types de fichiers acceptables.</span><span class="sxs-lookup"><span data-stu-id="b1936-104">The following table shows the acceptable file types.</span></span>

|<span data-ttu-id="b1936-105">Type</span><span class="sxs-lookup"><span data-stu-id="b1936-105">Type</span></span>|<span data-ttu-id="b1936-106">Extension de nom de fichier</span><span class="sxs-lookup"><span data-stu-id="b1936-106">File name extension</span></span>|
|---|---|
|<span data-ttu-id="b1936-107">Bitmap</span><span class="sxs-lookup"><span data-stu-id="b1936-107">Bitmap</span></span>|<span data-ttu-id="b1936-108">.bmp</span><span class="sxs-lookup"><span data-stu-id="b1936-108">.bmp</span></span>|
|<span data-ttu-id="b1936-109">Icône</span><span class="sxs-lookup"><span data-stu-id="b1936-109">Icon</span></span>|<span data-ttu-id="b1936-110">.ico</span><span class="sxs-lookup"><span data-stu-id="b1936-110">.ico</span></span>|
|<span data-ttu-id="b1936-111">GIF</span><span class="sxs-lookup"><span data-stu-id="b1936-111">GIF</span></span>|<span data-ttu-id="b1936-112">.gif</span><span class="sxs-lookup"><span data-stu-id="b1936-112">.gif</span></span>|
|<span data-ttu-id="b1936-113">Métafichiers</span><span class="sxs-lookup"><span data-stu-id="b1936-113">Metafile</span></span>|<span data-ttu-id="b1936-114">.wmf</span><span class="sxs-lookup"><span data-stu-id="b1936-114">.wmf</span></span>|
|<span data-ttu-id="b1936-115">JPEG</span><span class="sxs-lookup"><span data-stu-id="b1936-115">JPEG</span></span>|<span data-ttu-id="b1936-116">.jpg</span><span class="sxs-lookup"><span data-stu-id="b1936-116">.jpg</span></span>|

## <a name="to-display-a-picture-at-design-time"></a><span data-ttu-id="b1936-117">Pour afficher une image au moment du design</span><span class="sxs-lookup"><span data-stu-id="b1936-117">To display a picture at design time</span></span>

1. <span data-ttu-id="b1936-118">Dessinez un contrôle <xref:System.Windows.Forms.PictureBox> sur un formulaire.</span><span class="sxs-lookup"><span data-stu-id="b1936-118">Draw a <xref:System.Windows.Forms.PictureBox> control on a form.</span></span>

2. <span data-ttu-id="b1936-119">Dans la fenêtre **Propriétés** , sélectionnez la propriété <xref:System.Windows.Forms.PictureBox.Image%2A>, puis cliquez sur le bouton de sélection pour afficher la boîte de dialogue **ouvrir** .</span><span class="sxs-lookup"><span data-stu-id="b1936-119">In the **Properties** window, select the <xref:System.Windows.Forms.PictureBox.Image%2A> property, then select the ellipsis button to display the **Open** dialog box.</span></span>

3. <span data-ttu-id="b1936-120">Si vous recherchez un type de fichier spécifique (par exemple, des fichiers. gif), sélectionnez-le dans la zone **types de fichiers** .</span><span class="sxs-lookup"><span data-stu-id="b1936-120">If you're looking for a specific file type (for example, .gif files), select it in the **Files of type** box.</span></span>

4. <span data-ttu-id="b1936-121">Sélectionnez le fichier que vous souhaitez afficher.</span><span class="sxs-lookup"><span data-stu-id="b1936-121">Select the file you want to display.</span></span>

## <a name="to-clear-the-picture-at-design-time"></a><span data-ttu-id="b1936-122">Pour effacer l’image au moment du design</span><span class="sxs-lookup"><span data-stu-id="b1936-122">To clear the picture at design time</span></span>

1. <span data-ttu-id="b1936-123">Dans la fenêtre **Propriétés** , sélectionnez la propriété <xref:System.Windows.Forms.PictureBox.Image%2A>.</span><span class="sxs-lookup"><span data-stu-id="b1936-123">In the **Properties** window, select the <xref:System.Windows.Forms.PictureBox.Image%2A> property.</span></span> <span data-ttu-id="b1936-124">Cliquez avec le bouton droit sur la petite image miniature qui apparaît à gauche du nom de l’objet image, puis choisissez **Réinitialiser**.</span><span class="sxs-lookup"><span data-stu-id="b1936-124">Right-click the small thumbnail image that appears to the left of the name of the image object, and then choose **Reset**.</span></span>

## <a name="see-also"></a><span data-ttu-id="b1936-125">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b1936-125">See also</span></span>

- <xref:System.Windows.Forms.PictureBox>
- [<span data-ttu-id="b1936-126">Vue d’ensemble du contrôle PictureBox</span><span class="sxs-lookup"><span data-stu-id="b1936-126">PictureBox Control Overview</span></span>](picturebox-control-overview-windows-forms.md)
- [<span data-ttu-id="b1936-127">Guide pratique pour modifier la taille ou l'emplacement d'une image au moment de l'exécution</span><span class="sxs-lookup"><span data-stu-id="b1936-127">How to: Modify the Size or Placement of a Picture at Run Time</span></span>](how-to-modify-the-size-or-placement-of-a-picture-at-run-time-windows-forms.md)
- [<span data-ttu-id="b1936-128">Guide pratique pour définir des images au moment de l'exécution</span><span class="sxs-lookup"><span data-stu-id="b1936-128">How to: Set Pictures at Run Time</span></span>](how-to-set-pictures-at-run-time-windows-forms.md)
- [<span data-ttu-id="b1936-129">PictureBox, contrôle</span><span class="sxs-lookup"><span data-stu-id="b1936-129">PictureBox Control</span></span>](picturebox-control-windows-forms.md)
