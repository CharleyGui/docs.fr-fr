---
title: Regrouper des éléments dans un contrôle ListView à l’aide du concepteur
ms.date: 03/30/2017
helpviewer_keywords:
- ListView control [Windows Forms], grouping items
- grouping
- groups [Windows Forms], in Windows Forms controls
ms.assetid: 8b615000-69d9-4c64-acaf-b54fa09b69e3
ms.openlocfilehash: 935d8d75517e1028e686ca229f6ada656f58b01e
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76736686"
---
# <a name="how-to-group-items-in-a-windows-forms-listview-control-using-the-designer"></a><span data-ttu-id="5d0de-102">Comment : regrouper des éléments dans un contrôle ListView Windows Forms à l'aide du concepteur</span><span class="sxs-lookup"><span data-stu-id="5d0de-102">How to: Group Items in a Windows Forms ListView Control Using the Designer</span></span>

<span data-ttu-id="5d0de-103">La fonctionnalité de regroupement du contrôle <xref:System.Windows.Forms.ListView> vous permet d’afficher des jeux d’éléments associés dans des groupes.</span><span class="sxs-lookup"><span data-stu-id="5d0de-103">The grouping feature of the <xref:System.Windows.Forms.ListView> control enables you to display related sets of items in groups.</span></span> <span data-ttu-id="5d0de-104">Ces groupes sont séparés sur l’écran par des en-têtes de groupe horizontaux qui contiennent les titres des groupes.</span><span class="sxs-lookup"><span data-stu-id="5d0de-104">These groups are separated on the screen by horizontal group headers that contain the group titles.</span></span> <span data-ttu-id="5d0de-105">Vous pouvez utiliser des groupes de <xref:System.Windows.Forms.ListView> pour faciliter la navigation dans des listes volumineuses en regroupant les éléments par ordre alphabétique, par date ou par tout autre regroupement logique.</span><span class="sxs-lookup"><span data-stu-id="5d0de-105">You can use <xref:System.Windows.Forms.ListView> groups to make navigating large lists easier by grouping items alphabetically, by date, or by any other logical grouping.</span></span> <span data-ttu-id="5d0de-106">L’illustration suivante montre des éléments groupés :</span><span class="sxs-lookup"><span data-stu-id="5d0de-106">The following image shows some grouped items:</span></span>

![Nombres séparés en groupes pairs et impairs.](./media/how-to-group-items-in-a-windows-forms-listview-control-using-the-designer/odd-even-list-view-groups.gif)

<span data-ttu-id="5d0de-108">La procédure suivante requiert un projet d' **application Windows** avec un formulaire contenant un contrôle de <xref:System.Windows.Forms.ListView>.</span><span class="sxs-lookup"><span data-stu-id="5d0de-108">The following procedure requires a **Windows Application** project with a form containing a <xref:System.Windows.Forms.ListView> control.</span></span> <span data-ttu-id="5d0de-109">Pour plus d’informations sur la configuration d’un tel projet, consultez [Comment : créer un projet d’application Windows Forms](/visualstudio/ide/step-1-create-a-windows-forms-application-project) et [Comment : ajouter des contrôles à des Windows Forms](how-to-add-controls-to-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="5d0de-109">For information about setting up such a project, see [How to: Create a Windows Forms application project](/visualstudio/ide/step-1-create-a-windows-forms-application-project) and [How to: Add Controls to Windows Forms](how-to-add-controls-to-windows-forms.md).</span></span>

<span data-ttu-id="5d0de-110">Pour activer le regroupement, vous devez d’abord créer un ou plusieurs objets <xref:System.Windows.Forms.ListViewGroup> dans le concepteur ou par programme.</span><span class="sxs-lookup"><span data-stu-id="5d0de-110">To enable grouping, you must first create one or more <xref:System.Windows.Forms.ListViewGroup> objects either in the designer or programmatically.</span></span> <span data-ttu-id="5d0de-111">Une fois qu’un groupe a été défini, vous pouvez lui affecter des éléments.</span><span class="sxs-lookup"><span data-stu-id="5d0de-111">Once a group has been defined, you can assign items to it.</span></span>

## <a name="to-add-or-remove-groups-in-the-designer"></a><span data-ttu-id="5d0de-112">Pour ajouter ou supprimer des groupes dans le concepteur</span><span class="sxs-lookup"><span data-stu-id="5d0de-112">To add or remove groups in the designer</span></span>

1. <span data-ttu-id="5d0de-113">Dans la fenêtre **Propriétés** , cliquez sur les **points de suspension** (![le bouton de sélection (...) du bouton fenêtre Propriétés de Visual Studio.](./media/visual-studio-ellipsis-button.png)) en regard de la propriété <xref:System.Windows.Forms.ListView.Groups%2A>.</span><span class="sxs-lookup"><span data-stu-id="5d0de-113">In the **Properties** window, click the **Ellipsis** (![The Ellipsis button (...) in the Properties window of Visual Studio.](./media/visual-studio-ellipsis-button.png)) button next to the <xref:System.Windows.Forms.ListView.Groups%2A> property.</span></span>

     <span data-ttu-id="5d0de-114">L **'éditeur de collections ListViewGroup** s’affiche.</span><span class="sxs-lookup"><span data-stu-id="5d0de-114">The **ListViewGroup Collection Editor** appears.</span></span>

2. <span data-ttu-id="5d0de-115">Pour ajouter un groupe, cliquez sur le bouton **Ajouter** .</span><span class="sxs-lookup"><span data-stu-id="5d0de-115">To add a group, click the **Add** button.</span></span> <span data-ttu-id="5d0de-116">Vous pouvez ensuite définir les propriétés du nouveau groupe, telles que les propriétés <xref:System.Windows.Forms.ListViewGroup.Header%2A> et <xref:System.Windows.Forms.ListViewGroup.HeaderAlignment%2A>.</span><span class="sxs-lookup"><span data-stu-id="5d0de-116">You can then set properties of the new group, such as the <xref:System.Windows.Forms.ListViewGroup.Header%2A> and <xref:System.Windows.Forms.ListViewGroup.HeaderAlignment%2A> properties.</span></span> <span data-ttu-id="5d0de-117">Pour supprimer un groupe, sélectionnez-le et cliquez sur le bouton **supprimer** .</span><span class="sxs-lookup"><span data-stu-id="5d0de-117">To remove a group, select it and click the **Remove** button.</span></span>

## <a name="to-assign-items-to-groups-in-the-designer"></a><span data-ttu-id="5d0de-118">Pour assigner des éléments à des groupes dans le concepteur</span><span class="sxs-lookup"><span data-stu-id="5d0de-118">To assign items to groups in the designer</span></span>

1. <span data-ttu-id="5d0de-119">Dans la fenêtre **Propriétés** , cliquez sur les **points de suspension** (![le bouton de sélection (...) du bouton fenêtre Propriétés de Visual Studio.](./media/visual-studio-ellipsis-button.png)) en regard de la propriété <xref:System.Windows.Forms.ListView.Items%2A>.</span><span class="sxs-lookup"><span data-stu-id="5d0de-119">In the **Properties** window, click the **Ellipsis** (![The Ellipsis button (...) in the Properties window of Visual Studio.](./media/visual-studio-ellipsis-button.png)) button next to the <xref:System.Windows.Forms.ListView.Items%2A> property.</span></span>

     <span data-ttu-id="5d0de-120">L' **éditeur de collections ListViewItem** s’affiche.</span><span class="sxs-lookup"><span data-stu-id="5d0de-120">The **ListViewItem Collection Editor** appears.</span></span>

2. <span data-ttu-id="5d0de-121">Pour ajouter un nouvel élément, cliquez sur le bouton **Ajouter** .</span><span class="sxs-lookup"><span data-stu-id="5d0de-121">To add a new item, click the **Add** button.</span></span> <span data-ttu-id="5d0de-122">Vous pouvez ensuite définir les propriétés du nouvel élément, telles que les propriétés <xref:System.Windows.Forms.ListViewItem.Text%2A> et <xref:System.Windows.Forms.ListViewItem.ImageIndex%2A>.</span><span class="sxs-lookup"><span data-stu-id="5d0de-122">You can then set properties of the new item, such as the <xref:System.Windows.Forms.ListViewItem.Text%2A> and <xref:System.Windows.Forms.ListViewItem.ImageIndex%2A> properties.</span></span>

3. <span data-ttu-id="5d0de-123">Sélectionnez la propriété <xref:System.Windows.Forms.ListViewItem.Group%2A> et choisissez un groupe dans la liste déroulante.</span><span class="sxs-lookup"><span data-stu-id="5d0de-123">Select the <xref:System.Windows.Forms.ListViewItem.Group%2A> property and choose a group from the drop-down list.</span></span>

## <a name="see-also"></a><span data-ttu-id="5d0de-124">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="5d0de-124">See also</span></span>

- <xref:System.Windows.Forms.ListView>
- <xref:System.Windows.Forms.ListView.Groups%2A>
- <xref:System.Windows.Forms.ListViewGroup>
- [<span data-ttu-id="5d0de-125">ListView, contrôle</span><span class="sxs-lookup"><span data-stu-id="5d0de-125">ListView Control</span></span>](listview-control-windows-forms.md)
- [<span data-ttu-id="5d0de-126">Vue d’ensemble du contrôle ListView</span><span class="sxs-lookup"><span data-stu-id="5d0de-126">ListView Control Overview</span></span>](listview-control-overview-windows-forms.md)
- [<span data-ttu-id="5d0de-127">Guide pratique pour ajouter et supprimer des éléments avec le contrôle ListView Windows Forms</span><span class="sxs-lookup"><span data-stu-id="5d0de-127">How to: Add and Remove Items with the Windows Forms ListView Control</span></span>](how-to-add-and-remove-items-with-the-windows-forms-listview-control.md)
