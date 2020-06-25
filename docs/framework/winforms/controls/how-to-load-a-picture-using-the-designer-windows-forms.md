---
title: "Comment : charger une image à l'aide du concepteur"
description: Découvrez comment utiliser le contrôle Windows Forms PictureBox pour charger et afficher une image sur un formulaire au moment du Design.
ms.date: 03/30/2017
helpviewer_keywords:
- picture formats
- images [Windows Forms], displaying on Windows Forms
- pictures [Windows Forms], displaying
- forms [Windows Forms], displaying images
- PictureBox control [Windows Forms], adding pictures
ms.assetid: 4dc7b973-afb1-4276-8322-20825af96655
ms.openlocfilehash: a05ffe19412fc7a4e3e02f01336d89cce39fac8a
ms.sourcegitcommit: dc2feef0794cf41dbac1451a13b8183258566c0e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/24/2020
ms.locfileid: "85325596"
---
# <a name="how-to-load-a-picture-using-the-designer-windows-forms"></a><span data-ttu-id="d43d9-103">Comment : charger une image à l'aide du concepteur (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="d43d9-103">How to: Load a Picture Using the Designer (Windows Forms)</span></span>

<span data-ttu-id="d43d9-104">Avec le <xref:System.Windows.Forms.PictureBox> contrôle Windows Forms, vous pouvez charger et afficher une image sur un formulaire au moment du design en affectant <xref:System.Windows.Forms.PictureBox.Image%2A> à la propriété une image valide.</span><span class="sxs-lookup"><span data-stu-id="d43d9-104">With the Windows Forms <xref:System.Windows.Forms.PictureBox> control, you can load and display a picture on a form at design time by setting the <xref:System.Windows.Forms.PictureBox.Image%2A> property to a valid picture.</span></span> <span data-ttu-id="d43d9-105">Le tableau suivant présente les types de fichiers acceptables.</span><span class="sxs-lookup"><span data-stu-id="d43d9-105">The following table shows the acceptable file types.</span></span>

|<span data-ttu-id="d43d9-106">Type</span><span class="sxs-lookup"><span data-stu-id="d43d9-106">Type</span></span>|<span data-ttu-id="d43d9-107">Extension de nom de fichier</span><span class="sxs-lookup"><span data-stu-id="d43d9-107">File name extension</span></span>|
|---|---|
|<span data-ttu-id="d43d9-108">Bitmap</span><span class="sxs-lookup"><span data-stu-id="d43d9-108">Bitmap</span></span>|<span data-ttu-id="d43d9-109">.bmp</span><span class="sxs-lookup"><span data-stu-id="d43d9-109">.bmp</span></span>|
|<span data-ttu-id="d43d9-110">Icône</span><span class="sxs-lookup"><span data-stu-id="d43d9-110">Icon</span></span>|<span data-ttu-id="d43d9-111">.ico</span><span class="sxs-lookup"><span data-stu-id="d43d9-111">.ico</span></span>|
|<span data-ttu-id="d43d9-112">GIF</span><span class="sxs-lookup"><span data-stu-id="d43d9-112">GIF</span></span>|<span data-ttu-id="d43d9-113">.gif</span><span class="sxs-lookup"><span data-stu-id="d43d9-113">.gif</span></span>|
|<span data-ttu-id="d43d9-114">Métafichiers</span><span class="sxs-lookup"><span data-stu-id="d43d9-114">Metafile</span></span>|<span data-ttu-id="d43d9-115">. wmf</span><span class="sxs-lookup"><span data-stu-id="d43d9-115">.wmf</span></span>|
|<span data-ttu-id="d43d9-116">JPEG</span><span class="sxs-lookup"><span data-stu-id="d43d9-116">JPEG</span></span>|<span data-ttu-id="d43d9-117">.jpg</span><span class="sxs-lookup"><span data-stu-id="d43d9-117">.jpg</span></span>|

## <a name="to-display-a-picture-at-design-time"></a><span data-ttu-id="d43d9-118">Pour afficher une image au moment du design</span><span class="sxs-lookup"><span data-stu-id="d43d9-118">To display a picture at design time</span></span>

1. <span data-ttu-id="d43d9-119">Dessinez un <xref:System.Windows.Forms.PictureBox> contrôle sur un formulaire.</span><span class="sxs-lookup"><span data-stu-id="d43d9-119">Draw a <xref:System.Windows.Forms.PictureBox> control on a form.</span></span>

2. <span data-ttu-id="d43d9-120">Dans la fenêtre **Propriétés** , sélectionnez la <xref:System.Windows.Forms.PictureBox.Image%2A> propriété, puis cliquez sur le bouton de sélection pour afficher la boîte de dialogue **ouvrir** .</span><span class="sxs-lookup"><span data-stu-id="d43d9-120">In the **Properties** window, select the <xref:System.Windows.Forms.PictureBox.Image%2A> property, then select the ellipsis button to display the **Open** dialog box.</span></span>

3. <span data-ttu-id="d43d9-121">Si vous recherchez un type de fichier spécifique (par exemple, des fichiers. gif), sélectionnez-le dans la zone **types de fichiers** .</span><span class="sxs-lookup"><span data-stu-id="d43d9-121">If you're looking for a specific file type (for example, .gif files), select it in the **Files of type** box.</span></span>

4. <span data-ttu-id="d43d9-122">Sélectionnez le fichier que vous souhaitez afficher.</span><span class="sxs-lookup"><span data-stu-id="d43d9-122">Select the file you want to display.</span></span>

## <a name="to-clear-the-picture-at-design-time"></a><span data-ttu-id="d43d9-123">Pour effacer l’image au moment du design</span><span class="sxs-lookup"><span data-stu-id="d43d9-123">To clear the picture at design time</span></span>

1. <span data-ttu-id="d43d9-124">Dans la fenêtre **Propriétés** , sélectionnez la <xref:System.Windows.Forms.PictureBox.Image%2A> propriété.</span><span class="sxs-lookup"><span data-stu-id="d43d9-124">In the **Properties** window, select the <xref:System.Windows.Forms.PictureBox.Image%2A> property.</span></span> <span data-ttu-id="d43d9-125">Cliquez avec le bouton droit sur la petite image miniature qui apparaît à gauche du nom de l’objet image, puis choisissez **Réinitialiser**.</span><span class="sxs-lookup"><span data-stu-id="d43d9-125">Right-click the small thumbnail image that appears to the left of the name of the image object, and then choose **Reset**.</span></span>

## <a name="see-also"></a><span data-ttu-id="d43d9-126">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d43d9-126">See also</span></span>

- <xref:System.Windows.Forms.PictureBox>
- [<span data-ttu-id="d43d9-127">Vue d'ensemble du contrôle PictureBox</span><span class="sxs-lookup"><span data-stu-id="d43d9-127">PictureBox Control Overview</span></span>](picturebox-control-overview-windows-forms.md)
- [<span data-ttu-id="d43d9-128">Comment : modifier la taille ou l'emplacement d'une image au moment de l'exécution</span><span class="sxs-lookup"><span data-stu-id="d43d9-128">How to: Modify the Size or Placement of a Picture at Run Time</span></span>](how-to-modify-the-size-or-placement-of-a-picture-at-run-time-windows-forms.md)
- [<span data-ttu-id="d43d9-129">Comment : définir des images au moment de l'exécution</span><span class="sxs-lookup"><span data-stu-id="d43d9-129">How to: Set Pictures at Run Time</span></span>](how-to-set-pictures-at-run-time-windows-forms.md)
- [<span data-ttu-id="d43d9-130">PictureBox, contrôle</span><span class="sxs-lookup"><span data-stu-id="d43d9-130">PictureBox Control</span></span>](picturebox-control-windows-forms.md)
