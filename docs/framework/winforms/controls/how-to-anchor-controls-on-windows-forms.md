---
title: ancrer des contrôles
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
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 7c307d8c5b3bc32e15e6de048c434854ef1bbc65
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76747184"
---
# <a name="how-to-anchor-controls-on-windows-forms"></a><span data-ttu-id="a681c-102">Comment : ancrer des contrôles sur Windows Forms</span><span class="sxs-lookup"><span data-stu-id="a681c-102">How to: Anchor controls on Windows Forms</span></span>

<span data-ttu-id="a681c-103">Si vous concevez un formulaire que l’utilisateur peut redimensionner au moment de l’exécution, les contrôles de votre formulaire doivent être redimensionnés et repositionnés correctement.</span><span class="sxs-lookup"><span data-stu-id="a681c-103">If you're designing a form that the user can resize at run time, the controls on your form should resize and reposition properly.</span></span> <span data-ttu-id="a681c-104">Pour redimensionner des contrôles de manière dynamique avec le formulaire, vous pouvez utiliser la propriété <xref:System.Windows.Forms.Control.Anchor%2A> de Windows Forms contrôles.</span><span class="sxs-lookup"><span data-stu-id="a681c-104">To resize controls dynamically with the form, you can use the <xref:System.Windows.Forms.Control.Anchor%2A> property of Windows Forms controls.</span></span> <span data-ttu-id="a681c-105">La propriété <xref:System.Windows.Forms.Control.Anchor%2A> définit une position d’ancrage pour le contrôle.</span><span class="sxs-lookup"><span data-stu-id="a681c-105">The <xref:System.Windows.Forms.Control.Anchor%2A> property defines an anchor position for the control.</span></span> <span data-ttu-id="a681c-106">Lorsqu’un contrôle est ancré à un formulaire et que le formulaire est redimensionné, le contrôle maintient la distance entre le contrôle et les positions d’ancrage.</span><span class="sxs-lookup"><span data-stu-id="a681c-106">When a control is anchored to a form and the form is resized, the control maintains the distance between the control and the anchor positions.</span></span> <span data-ttu-id="a681c-107">Par exemple, si vous avez un contrôle <xref:System.Windows.Forms.TextBox> qui est ancré aux bords gauche, droit et inférieur du formulaire, au fur et à mesure que le formulaire est redimensionné, le contrôle <xref:System.Windows.Forms.TextBox> se redimensionne horizontalement afin qu’il conserve la même distance à partir des côtés droit et gauche du formulaire.</span><span class="sxs-lookup"><span data-stu-id="a681c-107">For example, if you have a <xref:System.Windows.Forms.TextBox> control that is anchored to the left, right, and bottom edges of the form, as the form is resized, the <xref:System.Windows.Forms.TextBox> control resizes horizontally so that it maintains the same distance from the right and left sides of the form.</span></span> <span data-ttu-id="a681c-108">En outre, le contrôle se positionne verticalement afin que son emplacement soit toujours la même distance que le bord inférieur du formulaire.</span><span class="sxs-lookup"><span data-stu-id="a681c-108">In addition, the control positions itself vertically so that its location is always the same distance from the bottom edge of the form.</span></span> <span data-ttu-id="a681c-109">Si un contrôle n’est pas ancré et que le formulaire est redimensionné, la position du contrôle par rapport aux bords du formulaire est modifiée.</span><span class="sxs-lookup"><span data-stu-id="a681c-109">If a control is not anchored and the form is resized, the position of the control relative to the edges of the form is changed.</span></span>

<span data-ttu-id="a681c-110">La propriété <xref:System.Windows.Forms.Control.Anchor%2A> interagit avec la propriété <xref:System.Windows.Forms.Control.AutoSize%2A>.</span><span class="sxs-lookup"><span data-stu-id="a681c-110">The <xref:System.Windows.Forms.Control.Anchor%2A> property interacts with the <xref:System.Windows.Forms.Control.AutoSize%2A> property.</span></span> <span data-ttu-id="a681c-111">Pour plus d’informations, consultez [vue d’ensemble de la propriété AutoSize](autosize-property-overview.md).</span><span class="sxs-lookup"><span data-stu-id="a681c-111">For more information, see [AutoSize Property Overview](autosize-property-overview.md).</span></span>

## <a name="anchor-a-control-on-a-form"></a><span data-ttu-id="a681c-112">Ancrer un contrôle dans un formulaire</span><span class="sxs-lookup"><span data-stu-id="a681c-112">Anchor a control on a form</span></span>

1. <span data-ttu-id="a681c-113">Dans Visual Studio, sélectionnez le contrôle que vous souhaitez ancrer.</span><span class="sxs-lookup"><span data-stu-id="a681c-113">In Visual Studio, select the control you want to anchor.</span></span>

    > [!NOTE]
    > <span data-ttu-id="a681c-114">Vous pouvez ancrer plusieurs contrôles simultanément en appuyant sur la touche CTRL, en cliquant sur chaque contrôle pour le sélectionner, puis en suivant le reste de cette procédure.</span><span class="sxs-lookup"><span data-stu-id="a681c-114">You can anchor multiple controls simultaneously by pressing the CTRL key, clicking each control to select it, and then following the rest of this procedure.</span></span>

2. <span data-ttu-id="a681c-115">Dans la fenêtre **Propriétés** , cliquez sur la flèche à droite de la propriété <xref:System.Windows.Forms.Control.Anchor%2A>.</span><span class="sxs-lookup"><span data-stu-id="a681c-115">In the **Properties** window, click the arrow to the right of the <xref:System.Windows.Forms.Control.Anchor%2A> property.</span></span>

     <span data-ttu-id="a681c-116">Un éditeur affiche une croix.</span><span class="sxs-lookup"><span data-stu-id="a681c-116">An editor is displayed that shows a cross.</span></span>

3. <span data-ttu-id="a681c-117">Pour définir une ancre, cliquez sur la section en haut, à gauche, à droite ou en bas de la Croix.</span><span class="sxs-lookup"><span data-stu-id="a681c-117">To set an anchor, click the top, left, right, or bottom section of the cross.</span></span>

     <span data-ttu-id="a681c-118">Les contrôles sont ancrés par défaut en haut et à gauche.</span><span class="sxs-lookup"><span data-stu-id="a681c-118">Controls are anchored to the top and left by default.</span></span>

4. <span data-ttu-id="a681c-119">Pour effacer un côté du contrôle qui a été ancré, cliquez sur ce bras de la Croix.</span><span class="sxs-lookup"><span data-stu-id="a681c-119">To clear a side of the control that has been anchored, click that arm of the cross.</span></span>

5. <span data-ttu-id="a681c-120">Pour fermer l’éditeur de propriétés <xref:System.Windows.Forms.Control.Anchor%2A>, cliquez à nouveau sur le nom de la propriété <xref:System.Windows.Forms.Control.Anchor%2A>.</span><span class="sxs-lookup"><span data-stu-id="a681c-120">To close the <xref:System.Windows.Forms.Control.Anchor%2A> property editor, click the <xref:System.Windows.Forms.Control.Anchor%2A> property name again.</span></span>

<span data-ttu-id="a681c-121">Lorsque votre formulaire s’affiche au moment de l’exécution, le contrôle est redimensionné pour rester positionné à la même distance que le bord du formulaire.</span><span class="sxs-lookup"><span data-stu-id="a681c-121">When your form is displayed at run time, the control resizes to remain positioned at the same distance from the edge of the form.</span></span> <span data-ttu-id="a681c-122">La distance à partir du bord ancré reste toujours la même que la distance définie lorsque le contrôle est positionné dans le Concepteur Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="a681c-122">The distance from the anchored edge always remains the same as the distance defined when the control is positioned in the Windows Forms Designer.</span></span>

> [!NOTE]
> <span data-ttu-id="a681c-123">Certains contrôles, tels que le contrôle <xref:System.Windows.Forms.ComboBox>, ont une limite à leur hauteur.</span><span class="sxs-lookup"><span data-stu-id="a681c-123">Certain controls, such as the <xref:System.Windows.Forms.ComboBox> control, have a limit to their height.</span></span> <span data-ttu-id="a681c-124">L’ancrage du contrôle au bas de son formulaire ou conteneur ne peut pas forcer le contrôle à dépasser sa limite de hauteur.</span><span class="sxs-lookup"><span data-stu-id="a681c-124">Anchoring the control to the bottom of its form or container cannot force the control to exceed its height limit.</span></span>

<span data-ttu-id="a681c-125">Les contrôles hérités doivent être `Protected` pour pouvoir être ancrés.</span><span class="sxs-lookup"><span data-stu-id="a681c-125">Inherited controls must be `Protected` to be able to be anchored.</span></span> <span data-ttu-id="a681c-126">Pour modifier le niveau d’accès d’un contrôle, définissez sa propriété `Modifiers` dans la fenêtre **Propriétés** .</span><span class="sxs-lookup"><span data-stu-id="a681c-126">To change the access level of a control, set its `Modifiers` property in the **Properties** window.</span></span>

## <a name="see-also"></a><span data-ttu-id="a681c-127">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a681c-127">See also</span></span>

- [<span data-ttu-id="a681c-128">Contrôles Windows Forms</span><span class="sxs-lookup"><span data-stu-id="a681c-128">Windows Forms Controls</span></span>](index.md)
- [<span data-ttu-id="a681c-129">Vue d’ensemble de la propriété AutoSize</span><span class="sxs-lookup"><span data-stu-id="a681c-129">AutoSize Property Overview</span></span>](autosize-property-overview.md)
- [<span data-ttu-id="a681c-130">Guide pratique pour fixer des contrôles sur des Windows Forms</span><span class="sxs-lookup"><span data-stu-id="a681c-130">How to: Dock Controls on Windows Forms</span></span>](how-to-dock-controls-on-windows-forms.md)
- [<span data-ttu-id="a681c-131">Procédure pas à pas : organisation des contrôles dans les Windows Forms à l’aide d’un FlowLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="a681c-131">Walkthrough: Arranging Controls on Windows Forms Using a FlowLayoutPanel</span></span>](walkthrough-arranging-controls-on-windows-forms-using-a-flowlayoutpanel.md)
- [<span data-ttu-id="a681c-132">Procédure pas à pas : organisation des contrôles dans les Windows Forms à l’aide d’un TableLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="a681c-132">Walkthrough: Arranging Controls on Windows Forms Using a TableLayoutPanel</span></span>](walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md)
- [<span data-ttu-id="a681c-133">Procédure pas à pas : disposition des contrôles Windows Forms avec les propriétés Padding, Margins et AutoSize</span><span class="sxs-lookup"><span data-stu-id="a681c-133">Walkthrough: Laying Out Windows Forms Controls with Padding, Margins, and the AutoSize Property</span></span>](windows-forms-controls-padding-autosize.md)
