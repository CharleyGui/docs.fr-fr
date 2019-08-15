---
title: 'Procédure : ajouter et supprimer des éléments avec le contrôle ListView Windows Forms à l’aide du concepteur'
ms.date: 03/30/2017
helpviewer_keywords:
- ListView control [Windows Forms], populating
- ListView control [Windows Forms], adding list items
ms.assetid: 217611ee-fd11-4d39-9a54-a37c3e781be1
ms.openlocfilehash: 62665746ea9fcd1553717b02b1f1349dc6415ab2
ms.sourcegitcommit: cf9515122fce716bcfb6618ba366e39b5a2eb81e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/15/2019
ms.locfileid: "69040083"
---
# <a name="how-to-add-and-remove-items-with-the-windows-forms-listview-control-using-the-designer"></a><span data-ttu-id="f7e12-102">Procédure : ajouter et supprimer des éléments avec le contrôle ListView Windows Forms à l’aide du concepteur</span><span class="sxs-lookup"><span data-stu-id="f7e12-102">How to: Add and Remove Items with the Windows Forms ListView Control Using the Designer</span></span>

<span data-ttu-id="f7e12-103">Le processus d’ajout d’un élément à un <xref:System.Windows.Forms.ListView> contrôle Windows Forms consiste principalement à spécifier l’élément et à lui assigner des propriétés.</span><span class="sxs-lookup"><span data-stu-id="f7e12-103">The process of adding an item to a Windows Forms <xref:System.Windows.Forms.ListView> control consists primarily of specifying the item and assigning properties to it.</span></span> <span data-ttu-id="f7e12-104">L’ajout ou la suppression d’éléments de liste peut être effectué à tout moment.</span><span class="sxs-lookup"><span data-stu-id="f7e12-104">Adding or removing list items can be done at any time.</span></span>

<span data-ttu-id="f7e12-105">La procédure suivante requiert un projet d' **application Windows** avec un formulaire contenant <xref:System.Windows.Forms.ListView> un contrôle.</span><span class="sxs-lookup"><span data-stu-id="f7e12-105">The following procedure requires a **Windows Application** project with a form containing a <xref:System.Windows.Forms.ListView> control.</span></span> <span data-ttu-id="f7e12-106">Pour plus d’informations sur la configuration d’un tel [projet, consultez Procédure: Créez un projet](/visualstudio/ide/step-1-create-a-windows-forms-application-project) d’application Windows Forms [et procédez comme suit: Ajoutez des contrôles à](how-to-add-controls-to-windows-forms.md)Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="f7e12-106">For information about setting up such a project, see [How to: Create a Windows Forms application project](/visualstudio/ide/step-1-create-a-windows-forms-application-project) and [How to: Add Controls to Windows Forms](how-to-add-controls-to-windows-forms.md).</span></span>

### <a name="to-add-or-remove-items-using-the-designer"></a><span data-ttu-id="f7e12-107">Pour ajouter ou supprimer des éléments à l’aide du concepteur</span><span class="sxs-lookup"><span data-stu-id="f7e12-107">To add or remove items using the designer</span></span>

1. <span data-ttu-id="f7e12-108">Sélectionnez le contrôle <xref:System.Windows.Forms.ListView>.</span><span class="sxs-lookup"><span data-stu-id="f7e12-108">Select the <xref:System.Windows.Forms.ListView> control.</span></span>

2. <span data-ttu-id="f7e12-109">Dans la fenêtre **Propriétés** , cliquez sur le bouton![de sélection (...) dans le bouton fenêtre Propriétés de Visual Studio.](./media/visual-studio-ellipsis-button.png)) en regard de la <xref:System.Windows.Forms.ListView.Items%2A> propriété.</span><span class="sxs-lookup"><span data-stu-id="f7e12-109">In the **Properties** window, click the **Ellipsis** (![The Ellipsis button (...) in the Properties window of Visual Studio.](./media/visual-studio-ellipsis-button.png)) button next to the <xref:System.Windows.Forms.ListView.Items%2A> property.</span></span>

     <span data-ttu-id="f7e12-110">L' **éditeur de collections ListViewItem** s’affiche.</span><span class="sxs-lookup"><span data-stu-id="f7e12-110">The **ListViewItem Collection Editor** appears.</span></span>

3. <span data-ttu-id="f7e12-111">Pour ajouter un élément, cliquez sur le bouton **Ajouter** .</span><span class="sxs-lookup"><span data-stu-id="f7e12-111">To add an item, click the **Add** button.</span></span> <span data-ttu-id="f7e12-112">Vous pouvez ensuite définir les propriétés du nouvel élément, telles que les <xref:System.Windows.Forms.ListView.Text%2A> propriétés <xref:System.Windows.Forms.ListViewItem.ImageIndex%2A> et.</span><span class="sxs-lookup"><span data-stu-id="f7e12-112">You can then set properties of the new item, such as the <xref:System.Windows.Forms.ListView.Text%2A> and <xref:System.Windows.Forms.ListViewItem.ImageIndex%2A> properties.</span></span>

4. <span data-ttu-id="f7e12-113">Pour supprimer un élément, sélectionnez-le et cliquez sur le bouton **supprimer** .</span><span class="sxs-lookup"><span data-stu-id="f7e12-113">To remove an item, select it and click the **Remove** button.</span></span>

## <a name="see-also"></a><span data-ttu-id="f7e12-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f7e12-114">See also</span></span>

- [<span data-ttu-id="f7e12-115">Vue d’ensemble du contrôle ListView</span><span class="sxs-lookup"><span data-stu-id="f7e12-115">ListView Control Overview</span></span>](listview-control-overview-windows-forms.md)
- [<span data-ttu-id="f7e12-116">Guide pratique : Ajouter des colonnes au contrôle ListView Windows Forms</span><span class="sxs-lookup"><span data-stu-id="f7e12-116">How to: Add Columns to the Windows Forms ListView Control</span></span>](how-to-add-columns-to-the-windows-forms-listview-control.md)
- [<span data-ttu-id="f7e12-117">Guide pratique : Afficher des sous-éléments en colonnes avec le contrôle ListView Windows Forms</span><span class="sxs-lookup"><span data-stu-id="f7e12-117">How to: Display Subitems in Columns with the Windows Forms ListView Control</span></span>](how-to-display-subitems-in-columns-with-the-windows-forms-listview-control.md)
- [<span data-ttu-id="f7e12-118">Guide pratique pour Afficher les icônes pour le contrôle ListView Windows Forms</span><span class="sxs-lookup"><span data-stu-id="f7e12-118">How to: Display Icons for the Windows Forms ListView Control</span></span>](how-to-display-icons-for-the-windows-forms-listview-control.md)
- [<span data-ttu-id="f7e12-119">Guide pratique pour Ajouter des informations personnalisées à un contrôle TreeView ou ListView (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="f7e12-119">How to: Add Custom Information to a TreeView or ListView Control (Windows Forms)</span></span>](add-custom-information-to-a-treeview-or-listview-control-wf.md)
- [<span data-ttu-id="f7e12-120">Guide pratique pour Regrouper des éléments dans un contrôle ListView Windows Forms</span><span class="sxs-lookup"><span data-stu-id="f7e12-120">How to: Group Items in a Windows Forms ListView Control</span></span>](how-to-group-items-in-a-windows-forms-listview-control.md)
