---
title: 'Procédure : ancrer des contrôles dans des Windows Forms'
ms.date: 03/30/2017
helpviewer_keywords:
- Anchor property [Windows Forms], enabling resizable forms
- Windows Forms controls, screen resolutions
- resizing forms [Windows Forms]
- Windows Forms controls, size
- screen resolution and control display
- controls [Windows Forms], anchoring
- forms [Windows Forms], resizing
- Windows Forms, resizing
- controls [Windows Forms], positioning
ms.assetid: 59ea914f-fbd3-427a-80fe-decd02f7ae6d
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 94fa6fe90e5583a3bfecf376af59d53f6d8528af
ms.sourcegitcommit: 37616676fde89153f563a485fc6159fc57326fc2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/23/2019
ms.locfileid: "69987491"
---
# <a name="how-to-anchor-controls-on-windows-forms"></a><span data-ttu-id="4eaf6-102">Procédure : Contrôles d’ancrage sur Windows Forms</span><span class="sxs-lookup"><span data-stu-id="4eaf6-102">How to: Anchor controls on Windows Forms</span></span>

<span data-ttu-id="4eaf6-103">Si vous concevez un formulaire que l’utilisateur peut redimensionner au moment de l’exécution, les contrôles de votre formulaire doivent être redimensionnés et repositionnés correctement.</span><span class="sxs-lookup"><span data-stu-id="4eaf6-103">If you're designing a form that the user can resize at run time, the controls on your form should resize and reposition properly.</span></span> <span data-ttu-id="4eaf6-104">Pour redimensionner des contrôles de manière dynamique avec le formulaire, vous <xref:System.Windows.Forms.Control.Anchor%2A> pouvez utiliser la propriété de Windows Forms contrôles.</span><span class="sxs-lookup"><span data-stu-id="4eaf6-104">To resize controls dynamically with the form, you can use the <xref:System.Windows.Forms.Control.Anchor%2A> property of Windows Forms controls.</span></span> <span data-ttu-id="4eaf6-105">La <xref:System.Windows.Forms.Control.Anchor%2A> propriété définit une position d’ancrage pour le contrôle.</span><span class="sxs-lookup"><span data-stu-id="4eaf6-105">The <xref:System.Windows.Forms.Control.Anchor%2A> property defines an anchor position for the control.</span></span> <span data-ttu-id="4eaf6-106">Lorsqu’un contrôle est ancré à un formulaire et que le formulaire est redimensionné, le contrôle maintient la distance entre le contrôle et les positions d’ancrage.</span><span class="sxs-lookup"><span data-stu-id="4eaf6-106">When a control is anchored to a form and the form is resized, the control maintains the distance between the control and the anchor positions.</span></span> <span data-ttu-id="4eaf6-107">Par exemple, si vous avez un <xref:System.Windows.Forms.TextBox> contrôle ancré sur les bords gauche, droit et inférieur du formulaire, au fur et à mesure que le formulaire est redimensionné, le <xref:System.Windows.Forms.TextBox> contrôle est redimensionné horizontalement afin qu’il conserve la même distance à partir des côtés droit et gauche du formulaire.</span><span class="sxs-lookup"><span data-stu-id="4eaf6-107">For example, if you have a <xref:System.Windows.Forms.TextBox> control that is anchored to the left, right, and bottom edges of the form, as the form is resized, the <xref:System.Windows.Forms.TextBox> control resizes horizontally so that it maintains the same distance from the right and left sides of the form.</span></span> <span data-ttu-id="4eaf6-108">En outre, le contrôle se positionne verticalement afin que son emplacement soit toujours la même distance que le bord inférieur du formulaire.</span><span class="sxs-lookup"><span data-stu-id="4eaf6-108">In addition, the control positions itself vertically so that its location is always the same distance from the bottom edge of the form.</span></span> <span data-ttu-id="4eaf6-109">Si un contrôle n’est pas ancré et que le formulaire est redimensionné, la position du contrôle par rapport aux bords du formulaire est modifiée.</span><span class="sxs-lookup"><span data-stu-id="4eaf6-109">If a control is not anchored and the form is resized, the position of the control relative to the edges of the form is changed.</span></span>

<span data-ttu-id="4eaf6-110">La <xref:System.Windows.Forms.Control.Anchor%2A> propriété interagit avec la <xref:System.Windows.Forms.Control.AutoSize%2A> propriété.</span><span class="sxs-lookup"><span data-stu-id="4eaf6-110">The <xref:System.Windows.Forms.Control.Anchor%2A> property interacts with the <xref:System.Windows.Forms.Control.AutoSize%2A> property.</span></span> <span data-ttu-id="4eaf6-111">Pour plus d’informations, consultez [vue d’ensemble](autosize-property-overview.md)de la propriété AutoSize.</span><span class="sxs-lookup"><span data-stu-id="4eaf6-111">For more information, see [AutoSize Property Overview](autosize-property-overview.md).</span></span>

## <a name="anchor-a-control-on-a-form"></a><span data-ttu-id="4eaf6-112">Ancrer un contrôle dans un formulaire</span><span class="sxs-lookup"><span data-stu-id="4eaf6-112">Anchor a control on a form</span></span>

1. <span data-ttu-id="4eaf6-113">Dans Visual Studio, sélectionnez le contrôle que vous souhaitez ancrer.</span><span class="sxs-lookup"><span data-stu-id="4eaf6-113">In Visual Studio, select the control you want to anchor.</span></span>

    > [!NOTE]
    > <span data-ttu-id="4eaf6-114">Vous pouvez ancrer plusieurs contrôles simultanément en appuyant sur la touche CTRL, en cliquant sur chaque contrôle pour le sélectionner, puis en suivant le reste de cette procédure.</span><span class="sxs-lookup"><span data-stu-id="4eaf6-114">You can anchor multiple controls simultaneously by pressing the CTRL key, clicking each control to select it, and then following the rest of this procedure.</span></span>

2. <span data-ttu-id="4eaf6-115">Dans la fenêtre **Propriétés** , cliquez sur la flèche à droite de la <xref:System.Windows.Forms.Control.Anchor%2A> propriété.</span><span class="sxs-lookup"><span data-stu-id="4eaf6-115">In the **Properties** window, click the arrow to the right of the <xref:System.Windows.Forms.Control.Anchor%2A> property.</span></span>

     <span data-ttu-id="4eaf6-116">Un éditeur affiche une croix.</span><span class="sxs-lookup"><span data-stu-id="4eaf6-116">An editor is displayed that shows a cross.</span></span>

3. <span data-ttu-id="4eaf6-117">Pour définir une ancre, cliquez sur la section en haut, à gauche, à droite ou en bas de la Croix.</span><span class="sxs-lookup"><span data-stu-id="4eaf6-117">To set an anchor, click the top, left, right, or bottom section of the cross.</span></span>

     <span data-ttu-id="4eaf6-118">Les contrôles sont ancrés par défaut en haut et à gauche.</span><span class="sxs-lookup"><span data-stu-id="4eaf6-118">Controls are anchored to the top and left by default.</span></span>

4. <span data-ttu-id="4eaf6-119">Pour effacer un côté du contrôle qui a été ancré, cliquez sur ce bras de la Croix.</span><span class="sxs-lookup"><span data-stu-id="4eaf6-119">To clear a side of the control that has been anchored, click that arm of the cross.</span></span>

5. <span data-ttu-id="4eaf6-120">Pour fermer l' <xref:System.Windows.Forms.Control.Anchor%2A> éditeur de propriétés, cliquez <xref:System.Windows.Forms.Control.Anchor%2A> à nouveau sur le nom de la propriété.</span><span class="sxs-lookup"><span data-stu-id="4eaf6-120">To close the <xref:System.Windows.Forms.Control.Anchor%2A> property editor, click the <xref:System.Windows.Forms.Control.Anchor%2A> property name again.</span></span>

<span data-ttu-id="4eaf6-121">Lorsque votre formulaire s’affiche au moment de l’exécution, le contrôle est redimensionné pour rester positionné à la même distance que le bord du formulaire.</span><span class="sxs-lookup"><span data-stu-id="4eaf6-121">When your form is displayed at run time, the control resizes to remain positioned at the same distance from the edge of the form.</span></span> <span data-ttu-id="4eaf6-122">La distance à partir du bord ancré reste toujours la même que la distance définie lorsque le contrôle est positionné dans le Concepteur Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="4eaf6-122">The distance from the anchored edge always remains the same as the distance defined when the control is positioned in the Windows Forms Designer.</span></span>

> [!NOTE]
> <span data-ttu-id="4eaf6-123">Certains contrôles, tels que le <xref:System.Windows.Forms.ComboBox> contrôle, ont une limite à leur hauteur.</span><span class="sxs-lookup"><span data-stu-id="4eaf6-123">Certain controls, such as the <xref:System.Windows.Forms.ComboBox> control, have a limit to their height.</span></span> <span data-ttu-id="4eaf6-124">L’ancrage du contrôle au bas de son formulaire ou conteneur ne peut pas forcer le contrôle à dépasser sa limite de hauteur.</span><span class="sxs-lookup"><span data-stu-id="4eaf6-124">Anchoring the control to the bottom of its form or container cannot force the control to exceed its height limit.</span></span>

<span data-ttu-id="4eaf6-125">Les contrôles hérités `Protected` doivent être en mesure d’être ancrés.</span><span class="sxs-lookup"><span data-stu-id="4eaf6-125">Inherited controls must be `Protected` to be able to be anchored.</span></span> <span data-ttu-id="4eaf6-126">Pour modifier le niveau d’accès d’un contrôle, définissez `Modifiers` sa propriété dans la fenêtre **Propriétés** .</span><span class="sxs-lookup"><span data-stu-id="4eaf6-126">To change the access level of a control, set its `Modifiers` property in the **Properties** window.</span></span>

## <a name="see-also"></a><span data-ttu-id="4eaf6-127">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4eaf6-127">See also</span></span>

- [<span data-ttu-id="4eaf6-128">Contrôles Windows Forms</span><span class="sxs-lookup"><span data-stu-id="4eaf6-128">Windows Forms Controls</span></span>](index.md)
- [<span data-ttu-id="4eaf6-129">Vue d’ensemble de la propriété AutoSize</span><span class="sxs-lookup"><span data-stu-id="4eaf6-129">AutoSize Property Overview</span></span>](autosize-property-overview.md)
- [<span data-ttu-id="4eaf6-130">Guide pratique pour Ancrer les contrôles sur Windows Forms</span><span class="sxs-lookup"><span data-stu-id="4eaf6-130">How to: Dock Controls on Windows Forms</span></span>](how-to-dock-controls-on-windows-forms.md)
- [<span data-ttu-id="4eaf6-131">Procédure pas à pas : Réorganisation des contrôles sur Windows Forms à l’aide d’un FlowLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="4eaf6-131">Walkthrough: Arranging Controls on Windows Forms Using a FlowLayoutPanel</span></span>](walkthrough-arranging-controls-on-windows-forms-using-a-flowlayoutpanel.md)
- [<span data-ttu-id="4eaf6-132">Procédure pas à pas : Réorganisation des contrôles sur Windows Forms à l’aide d’un TableLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="4eaf6-132">Walkthrough: Arranging Controls on Windows Forms Using a TableLayoutPanel</span></span>](walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md)
- [<span data-ttu-id="4eaf6-133">Procédure pas à pas : Disposition des contrôles Windows Forms avec le remplissage, les marges et la propriété AutoSize</span><span class="sxs-lookup"><span data-stu-id="4eaf6-133">Walkthrough: Laying Out Windows Forms Controls with Padding, Margins, and the AutoSize Property</span></span>](windows-forms-controls-padding-autosize.md)
