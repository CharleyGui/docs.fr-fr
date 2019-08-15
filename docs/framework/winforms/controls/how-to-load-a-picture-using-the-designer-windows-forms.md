---
title: 'Procédure : Charger une image à l’aide du concepteur (Windows Forms)'
ms.date: 03/30/2017
helpviewer_keywords:
- picture formats
- images [Windows Forms], displaying on Windows Forms
- pictures [Windows Forms], displaying
- forms [Windows Forms], displaying images
- PictureBox control [Windows Forms], adding pictures
ms.assetid: 4dc7b973-afb1-4276-8322-20825af96655
ms.openlocfilehash: 818bc63b5b3bea6c73804f716a72ba3cd1a62b4c
ms.sourcegitcommit: cf9515122fce716bcfb6618ba366e39b5a2eb81e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/15/2019
ms.locfileid: "69039677"
---
# <a name="how-to-load-a-picture-using-the-designer-windows-forms"></a><span data-ttu-id="4faf8-102">Procédure : Charger une image à l’aide du concepteur (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="4faf8-102">How to: Load a Picture Using the Designer (Windows Forms)</span></span>

<span data-ttu-id="4faf8-103">Avec le contrôle <xref:System.Windows.Forms.PictureBox> Windows Forms, vous pouvez charger et afficher une image sur un formulaire au moment du design en affectant à la <xref:System.Windows.Forms.PictureBox.Image%2A> propriété une image valide.</span><span class="sxs-lookup"><span data-stu-id="4faf8-103">With the Windows Forms <xref:System.Windows.Forms.PictureBox> control, you can load and display a picture on a form at design time by setting the <xref:System.Windows.Forms.PictureBox.Image%2A> property to a valid picture.</span></span> <span data-ttu-id="4faf8-104">Le tableau suivant présente les types de fichiers acceptables.</span><span class="sxs-lookup"><span data-stu-id="4faf8-104">The following table shows the acceptable file types.</span></span>

|<span data-ttu-id="4faf8-105">Type</span><span class="sxs-lookup"><span data-stu-id="4faf8-105">Type</span></span>|<span data-ttu-id="4faf8-106">Extension de nom de fichier</span><span class="sxs-lookup"><span data-stu-id="4faf8-106">File name extension</span></span>|
|---|---|
|<span data-ttu-id="4faf8-107">Bitmap</span><span class="sxs-lookup"><span data-stu-id="4faf8-107">Bitmap</span></span>|<span data-ttu-id="4faf8-108">.bmp</span><span class="sxs-lookup"><span data-stu-id="4faf8-108">.bmp</span></span>|
|<span data-ttu-id="4faf8-109">Icône</span><span class="sxs-lookup"><span data-stu-id="4faf8-109">Icon</span></span>|<span data-ttu-id="4faf8-110">.ico</span><span class="sxs-lookup"><span data-stu-id="4faf8-110">.ico</span></span>|
|<span data-ttu-id="4faf8-111">GIF</span><span class="sxs-lookup"><span data-stu-id="4faf8-111">GIF</span></span>|<span data-ttu-id="4faf8-112">.gif</span><span class="sxs-lookup"><span data-stu-id="4faf8-112">.gif</span></span>|
|<span data-ttu-id="4faf8-113">Métafichiers</span><span class="sxs-lookup"><span data-stu-id="4faf8-113">Metafile</span></span>|<span data-ttu-id="4faf8-114">.wmf</span><span class="sxs-lookup"><span data-stu-id="4faf8-114">.wmf</span></span>|
|<span data-ttu-id="4faf8-115">JPEG</span><span class="sxs-lookup"><span data-stu-id="4faf8-115">JPEG</span></span>|<span data-ttu-id="4faf8-116">.jpg</span><span class="sxs-lookup"><span data-stu-id="4faf8-116">.jpg</span></span>|

## <a name="to-display-a-picture-at-design-time"></a><span data-ttu-id="4faf8-117">Pour afficher une image au moment du design</span><span class="sxs-lookup"><span data-stu-id="4faf8-117">To display a picture at design time</span></span>

1. <span data-ttu-id="4faf8-118">Dessinez <xref:System.Windows.Forms.PictureBox> un contrôle sur un formulaire.</span><span class="sxs-lookup"><span data-stu-id="4faf8-118">Draw a <xref:System.Windows.Forms.PictureBox> control on a form.</span></span>

2. <span data-ttu-id="4faf8-119">Dans la fenêtre **Propriétés** , sélectionnez la <xref:System.Windows.Forms.PictureBox.Image%2A> propriété, puis cliquez sur le bouton de sélection pour afficher la boîte de dialogue **ouvrir** .</span><span class="sxs-lookup"><span data-stu-id="4faf8-119">In the **Properties** window, select the <xref:System.Windows.Forms.PictureBox.Image%2A> property, then select the ellipsis button to display the **Open** dialog box.</span></span>

3. <span data-ttu-id="4faf8-120">Si vous recherchez un type de fichier spécifique (par exemple, des fichiers. gif), sélectionnez-le dans la zone **types de fichiers** .</span><span class="sxs-lookup"><span data-stu-id="4faf8-120">If you're looking for a specific file type (for example, .gif files), select it in the **Files of type** box.</span></span>

4. <span data-ttu-id="4faf8-121">Sélectionnez le fichier que vous souhaitez afficher.</span><span class="sxs-lookup"><span data-stu-id="4faf8-121">Select the file you want to display.</span></span>

## <a name="to-clear-the-picture-at-design-time"></a><span data-ttu-id="4faf8-122">Pour effacer l’image au moment du design</span><span class="sxs-lookup"><span data-stu-id="4faf8-122">To clear the picture at design time</span></span>

1. <span data-ttu-id="4faf8-123">Dans la fenêtre **Propriétés** , sélectionnez la <xref:System.Windows.Forms.PictureBox.Image%2A> propriété.</span><span class="sxs-lookup"><span data-stu-id="4faf8-123">In the **Properties** window, select the <xref:System.Windows.Forms.PictureBox.Image%2A> property.</span></span> <span data-ttu-id="4faf8-124">Cliquez avec le bouton droit sur la petite image miniature qui apparaît à gauche du nom de l’objet image, puis choisissez **Réinitialiser**.</span><span class="sxs-lookup"><span data-stu-id="4faf8-124">Right-click the small thumbnail image that appears to the left of the name of the image object, and then choose **Reset**.</span></span>

## <a name="see-also"></a><span data-ttu-id="4faf8-125">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4faf8-125">See also</span></span>

- <xref:System.Windows.Forms.PictureBox>
- [<span data-ttu-id="4faf8-126">Vue d’ensemble du contrôle PictureBox</span><span class="sxs-lookup"><span data-stu-id="4faf8-126">PictureBox Control Overview</span></span>](picturebox-control-overview-windows-forms.md)
- [<span data-ttu-id="4faf8-127">Guide pratique pour Modifier la taille ou l’emplacement d’une image au moment de l’exécution</span><span class="sxs-lookup"><span data-stu-id="4faf8-127">How to: Modify the Size or Placement of a Picture at Run Time</span></span>](how-to-modify-the-size-or-placement-of-a-picture-at-run-time-windows-forms.md)
- [<span data-ttu-id="4faf8-128">Guide pratique pour Définir des images au moment de l’exécution</span><span class="sxs-lookup"><span data-stu-id="4faf8-128">How to: Set Pictures at Run Time</span></span>](how-to-set-pictures-at-run-time-windows-forms.md)
- [<span data-ttu-id="4faf8-129">PictureBox, contrôle</span><span class="sxs-lookup"><span data-stu-id="4faf8-129">PictureBox Control</span></span>](picturebox-control-windows-forms.md)
