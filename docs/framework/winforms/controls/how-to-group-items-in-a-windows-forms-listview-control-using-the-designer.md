---
title: 'Procédure : regrouper des éléments dans un contrôle ListView Windows Forms à l’aide du concepteur'
ms.date: 03/30/2017
helpviewer_keywords:
- ListView control [Windows Forms], grouping items
- grouping
- groups [Windows Forms], in Windows Forms controls
ms.assetid: 8b615000-69d9-4c64-acaf-b54fa09b69e3
ms.openlocfilehash: b63bcd9e5e357db350cc2987e09af84eb58bdcff
ms.sourcegitcommit: 56f1d1203d0075a461a10a301459d3aa452f4f47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/25/2019
ms.locfileid: "69039401"
---
# <a name="how-to-group-items-in-a-windows-forms-listview-control-using-the-designer"></a><span data-ttu-id="b596d-102">Procédure : regrouper des éléments dans un contrôle ListView Windows Forms à l’aide du concepteur</span><span class="sxs-lookup"><span data-stu-id="b596d-102">How to: Group Items in a Windows Forms ListView Control Using the Designer</span></span>

<span data-ttu-id="b596d-103">La fonctionnalité de regroupement du <xref:System.Windows.Forms.ListView> contrôle vous permet d’afficher des jeux d’éléments associés dans des groupes.</span><span class="sxs-lookup"><span data-stu-id="b596d-103">The grouping feature of the <xref:System.Windows.Forms.ListView> control enables you to display related sets of items in groups.</span></span> <span data-ttu-id="b596d-104">Ces groupes sont séparés sur l’écran par des en-têtes de groupe horizontaux qui contiennent les titres des groupes.</span><span class="sxs-lookup"><span data-stu-id="b596d-104">These groups are separated on the screen by horizontal group headers that contain the group titles.</span></span> <span data-ttu-id="b596d-105">Vous pouvez utiliser <xref:System.Windows.Forms.ListView> des groupes pour faciliter la navigation dans des listes volumineuses en regroupant les éléments par ordre alphabétique, par date ou par tout autre regroupement logique.</span><span class="sxs-lookup"><span data-stu-id="b596d-105">You can use <xref:System.Windows.Forms.ListView> groups to make navigating large lists easier by grouping items alphabetically, by date, or by any other logical grouping.</span></span> <span data-ttu-id="b596d-106">L’illustration suivante montre des éléments groupés :</span><span class="sxs-lookup"><span data-stu-id="b596d-106">The following image shows some grouped items:</span></span>

![Nombres séparés en groupes pairs et impairs.](./media/how-to-group-items-in-a-windows-forms-listview-control-using-the-designer/odd-even-list-view-groups.gif)

<span data-ttu-id="b596d-108">La procédure suivante requiert un projet d' **application Windows** avec un formulaire contenant <xref:System.Windows.Forms.ListView> un contrôle.</span><span class="sxs-lookup"><span data-stu-id="b596d-108">The following procedure requires a **Windows Application** project with a form containing a <xref:System.Windows.Forms.ListView> control.</span></span> <span data-ttu-id="b596d-109">Pour plus d’informations sur la configuration d’un tel [projet, consultez Procédure : Créez un projet](/visualstudio/ide/step-1-create-a-windows-forms-application-project) d’application Windows Forms [et procédez comme suit : Ajoutez des contrôles à](how-to-add-controls-to-windows-forms.md)Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="b596d-109">For information about setting up such a project, see [How to: Create a Windows Forms application project](/visualstudio/ide/step-1-create-a-windows-forms-application-project) and [How to: Add Controls to Windows Forms](how-to-add-controls-to-windows-forms.md).</span></span>

<span data-ttu-id="b596d-110">Pour activer le regroupement, vous devez d’abord créer un ou <xref:System.Windows.Forms.ListViewGroup> plusieurs objets dans le concepteur ou par programme.</span><span class="sxs-lookup"><span data-stu-id="b596d-110">To enable grouping, you must first create one or more <xref:System.Windows.Forms.ListViewGroup> objects either in the designer or programmatically.</span></span> <span data-ttu-id="b596d-111">Une fois qu’un groupe a été défini, vous pouvez lui affecter des éléments.</span><span class="sxs-lookup"><span data-stu-id="b596d-111">Once a group has been defined, you can assign items to it.</span></span>

> [!NOTE]
> <span data-ttu-id="b596d-112"><xref:System.Windows.Forms.ListView>les groupes sont disponibles uniquement [!INCLUDE[WinXpFamily](../../../../includes/winxpfamily-md.md)] sur lorsque votre application appelle <xref:System.Windows.Forms.Application.EnableVisualStyles%2A?displayProperty=nameWithType> la méthode.</span><span class="sxs-lookup"><span data-stu-id="b596d-112"><xref:System.Windows.Forms.ListView> groups are available only on [!INCLUDE[WinXpFamily](../../../../includes/winxpfamily-md.md)] when your application calls the <xref:System.Windows.Forms.Application.EnableVisualStyles%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="b596d-113">Sur les systèmes d’exploitation antérieurs, tout code relatif aux groupes n’a aucun effet et les groupes n’apparaissent pas.</span><span class="sxs-lookup"><span data-stu-id="b596d-113">On earlier operating systems, any code relating to groups has no effect and the groups will not appear.</span></span> <span data-ttu-id="b596d-114">Pour plus d'informations, consultez <xref:System.Windows.Forms.ListView.Groups%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="b596d-114">For more information, see <xref:System.Windows.Forms.ListView.Groups%2A?displayProperty=nameWithType>.</span></span>

## <a name="to-add-or-remove-groups-in-the-designer"></a><span data-ttu-id="b596d-115">Pour ajouter ou supprimer des groupes dans le concepteur</span><span class="sxs-lookup"><span data-stu-id="b596d-115">To add or remove groups in the designer</span></span>

1. <span data-ttu-id="b596d-116">Dans la fenêtre **Propriétés** , cliquez sur **le bouton de sélection (** ![...) dans le bouton fenêtre Propriétés de Visual Studio.](./media/visual-studio-ellipsis-button.png)) en regard de la <xref:System.Windows.Forms.ListView.Groups%2A> propriété.</span><span class="sxs-lookup"><span data-stu-id="b596d-116">In the **Properties** window, click the **Ellipsis** (![The Ellipsis button (...) in the Properties window of Visual Studio.](./media/visual-studio-ellipsis-button.png)) button next to the <xref:System.Windows.Forms.ListView.Groups%2A> property.</span></span>

     <span data-ttu-id="b596d-117">L **'éditeur de collections ListViewGroup** s’affiche.</span><span class="sxs-lookup"><span data-stu-id="b596d-117">The **ListViewGroup Collection Editor** appears.</span></span>

2. <span data-ttu-id="b596d-118">Pour ajouter un groupe, cliquez sur le bouton **Ajouter** .</span><span class="sxs-lookup"><span data-stu-id="b596d-118">To add a group, click the **Add** button.</span></span> <span data-ttu-id="b596d-119">Vous pouvez ensuite définir les propriétés du nouveau groupe, telles que les <xref:System.Windows.Forms.ListViewGroup.Header%2A> propriétés <xref:System.Windows.Forms.ListViewGroup.HeaderAlignment%2A> et.</span><span class="sxs-lookup"><span data-stu-id="b596d-119">You can then set properties of the new group, such as the <xref:System.Windows.Forms.ListViewGroup.Header%2A> and <xref:System.Windows.Forms.ListViewGroup.HeaderAlignment%2A> properties.</span></span> <span data-ttu-id="b596d-120">Pour supprimer un groupe, sélectionnez-le et cliquez sur le bouton **supprimer** .</span><span class="sxs-lookup"><span data-stu-id="b596d-120">To remove a group, select it and click the **Remove** button.</span></span>

## <a name="to-assign-items-to-groups-in-the-designer"></a><span data-ttu-id="b596d-121">Pour assigner des éléments à des groupes dans le concepteur</span><span class="sxs-lookup"><span data-stu-id="b596d-121">To assign items to groups in the designer</span></span>

1. <span data-ttu-id="b596d-122">Dans la fenêtre **Propriétés** , cliquez sur **le bouton de sélection (** ![...) dans le bouton fenêtre Propriétés de Visual Studio.](./media/visual-studio-ellipsis-button.png)) en regard de la <xref:System.Windows.Forms.ListView.Items%2A> propriété.</span><span class="sxs-lookup"><span data-stu-id="b596d-122">In the **Properties** window, click the **Ellipsis** (![The Ellipsis button (...) in the Properties window of Visual Studio.](./media/visual-studio-ellipsis-button.png)) button next to the <xref:System.Windows.Forms.ListView.Items%2A> property.</span></span>

     <span data-ttu-id="b596d-123">L' **éditeur de collections ListViewItem** s’affiche.</span><span class="sxs-lookup"><span data-stu-id="b596d-123">The **ListViewItem Collection Editor** appears.</span></span>

2. <span data-ttu-id="b596d-124">Pour ajouter un nouvel élément, cliquez sur le bouton **Ajouter** .</span><span class="sxs-lookup"><span data-stu-id="b596d-124">To add a new item, click the **Add** button.</span></span> <span data-ttu-id="b596d-125">Vous pouvez ensuite définir les propriétés du nouvel élément, telles que les <xref:System.Windows.Forms.ListViewItem.Text%2A> propriétés <xref:System.Windows.Forms.ListViewItem.ImageIndex%2A> et.</span><span class="sxs-lookup"><span data-stu-id="b596d-125">You can then set properties of the new item, such as the <xref:System.Windows.Forms.ListViewItem.Text%2A> and <xref:System.Windows.Forms.ListViewItem.ImageIndex%2A> properties.</span></span>

3. <span data-ttu-id="b596d-126">Sélectionnez la <xref:System.Windows.Forms.ListViewItem.Group%2A> propriété et choisissez un groupe dans la liste déroulante.</span><span class="sxs-lookup"><span data-stu-id="b596d-126">Select the <xref:System.Windows.Forms.ListViewItem.Group%2A> property and choose a group from the drop-down list.</span></span>

## <a name="see-also"></a><span data-ttu-id="b596d-127">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b596d-127">See also</span></span>

- <xref:System.Windows.Forms.ListView>
- <xref:System.Windows.Forms.ListView.Groups%2A>
- <xref:System.Windows.Forms.ListViewGroup>
- [<span data-ttu-id="b596d-128">Contrôle ListView</span><span class="sxs-lookup"><span data-stu-id="b596d-128">ListView Control</span></span>](listview-control-windows-forms.md)
- [<span data-ttu-id="b596d-129">Vue d’ensemble du contrôle ListView</span><span class="sxs-lookup"><span data-stu-id="b596d-129">ListView Control Overview</span></span>](listview-control-overview-windows-forms.md)
- [<span data-ttu-id="b596d-130">Guide pratique pour Ajouter et supprimer des éléments avec le contrôle ListView Windows Forms</span><span class="sxs-lookup"><span data-stu-id="b596d-130">How to: Add and Remove Items with the Windows Forms ListView Control</span></span>](how-to-add-and-remove-items-with-the-windows-forms-listview-control.md)
