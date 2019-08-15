---
title: 'Procédure : définir des styles de ligne alternée pour le contrôle DataGridView Windows Forms à l’aide du concepteur'
ms.date: 03/30/2017
helpviewer_keywords:
- ledger-like formats
- DataGridView control [Windows Forms], row style alternation
- Windows Forms, rows
- rows [Windows Forms], alternating
- data [Windows Forms], displaying
ms.assetid: 02373442-bf94-4470-9f8a-e44c4a9d5b88
ms.openlocfilehash: 1be746d4cce36344e034692a0e2e8e6a9e9320d5
ms.sourcegitcommit: cf9515122fce716bcfb6618ba366e39b5a2eb81e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/15/2019
ms.locfileid: "69040437"
---
# <a name="how-to-set-alternating-row-styles-for-the-windows-forms-datagridview-control-using-the-designer"></a><span data-ttu-id="a639f-102">Procédure : définir des styles de ligne alternée pour le contrôle DataGridView Windows Forms à l’aide du concepteur</span><span class="sxs-lookup"><span data-stu-id="a639f-102">How to: Set Alternating Row Styles for the Windows Forms DataGridView Control Using the Designer</span></span>

<span data-ttu-id="a639f-103">Les données tabulaires sont souvent présentées dans un format de type comptabilité où les lignes alternées ont des couleurs d’arrière-plan différentes.</span><span class="sxs-lookup"><span data-stu-id="a639f-103">Tabular data is often presented in a ledger-like format where alternating rows have different background colors.</span></span> <span data-ttu-id="a639f-104">Avec ce format, il est facile pour les utilisateurs de déterminer quelle cellule appartient à quelle ligne, en particulier dans les tableaux larges qui ont beaucoup de colonnes.</span><span class="sxs-lookup"><span data-stu-id="a639f-104">This format makes it easier for users to tell which cells are in each row, especially with wide tables that have many columns.</span></span>

<span data-ttu-id="a639f-105">Avec le contrôle <xref:System.Windows.Forms.DataGridView>, vous pouvez spécifier des informations de style complètes pour les lignes en alternance.</span><span class="sxs-lookup"><span data-stu-id="a639f-105">With the <xref:System.Windows.Forms.DataGridView> control, you can specify complete style information for alternating rows.</span></span> <span data-ttu-id="a639f-106">Vous pouvez utiliser des caractéristiques de style telles que la couleur de premier plan et la police, en plus de la couleur d’arrière-plan, pour différencier les lignes alternées.</span><span class="sxs-lookup"><span data-stu-id="a639f-106">You can use style characteristics like foreground color and font, in addition to background color, to differentiate alternating rows.</span></span> <span data-ttu-id="a639f-107">Pour plus d’informations, consultez [styles de cellule dans le contrôle DataGridView Windows Forms](cell-styles-in-the-windows-forms-datagridview-control.md).</span><span class="sxs-lookup"><span data-stu-id="a639f-107">For more information, see [Cell Styles in the Windows Forms DataGridView Control](cell-styles-in-the-windows-forms-datagridview-control.md).</span></span>

<span data-ttu-id="a639f-108">La procédure suivante requiert un projet d' **application Windows** avec un formulaire contenant <xref:System.Windows.Forms.DataGridView> un contrôle.</span><span class="sxs-lookup"><span data-stu-id="a639f-108">The following procedure requires a **Windows Application** project with a form containing a <xref:System.Windows.Forms.DataGridView> control.</span></span> <span data-ttu-id="a639f-109">Pour plus d’informations sur la configuration d’un tel [projet, consultez Procédure: Créez un projet](/visualstudio/ide/step-1-create-a-windows-forms-application-project) d’application Windows Forms [et procédez comme suit: Ajoutez des contrôles à](how-to-add-controls-to-windows-forms.md)Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="a639f-109">For information about setting up such a project, see [How to: Create a Windows Forms application project](/visualstudio/ide/step-1-create-a-windows-forms-application-project) and [How to: Add Controls to Windows Forms](how-to-add-controls-to-windows-forms.md).</span></span>


### <a name="define-styles-for-alternating-rows"></a><span data-ttu-id="a639f-110">Définir des styles pour les lignes en alternance</span><span class="sxs-lookup"><span data-stu-id="a639f-110">Define styles for alternating rows</span></span>

1. <span data-ttu-id="a639f-111">Sélectionnez le <xref:System.Windows.Forms.DataGridView> contrôle dans le concepteur.</span><span class="sxs-lookup"><span data-stu-id="a639f-111">Select the <xref:System.Windows.Forms.DataGridView> control in the designer.</span></span>

2. <span data-ttu-id="a639f-112">Dans la fenêtre **Propriétés** , cliquez sur le bouton de![sélection (le bouton de sélection (...) dans le fenêtre Propriétés de](./media/visual-studio-ellipsis-button.png)Visual Studio.) <xref:System.Windows.Forms.DataGridView.AlternatingRowsDefaultCellStyle%2A> en regard de la propriété.</span><span class="sxs-lookup"><span data-stu-id="a639f-112">In the **Properties** window, click the ellipsis button (![The Ellipsis button (...) in the Properties window of Visual Studio.](./media/visual-studio-ellipsis-button.png)) next to the <xref:System.Windows.Forms.DataGridView.AlternatingRowsDefaultCellStyle%2A> property.</span></span>

3. <span data-ttu-id="a639f-113">Dans la boîte de dialogue **Générateur CellStyle** , définissez le style en définissant les propriétés et utilisez le volet de **visualisation** pour confirmer vos choix.</span><span class="sxs-lookup"><span data-stu-id="a639f-113">In the **CellStyle Builder** dialog box, define the style by setting the properties, and use the **Preview** pane to confirm your choices.</span></span> <span data-ttu-id="a639f-114">Les styles que vous spécifiez sont utilisés pour toutes les autres lignes affichées dans le contrôle, en commençant par le deuxième.</span><span class="sxs-lookup"><span data-stu-id="a639f-114">The styles you specify are used for every other row displayed in the control, starting with the second one.</span></span>

4. <span data-ttu-id="a639f-115">Pour définir des styles pour les lignes restantes, répétez les étapes <xref:System.Windows.Forms.DataGridView.RowsDefaultCellStyle%2A> 2 et 3 à l’aide de la propriété.</span><span class="sxs-lookup"><span data-stu-id="a639f-115">To define styles for the remaining rows, repeat steps 2 and 3 using the <xref:System.Windows.Forms.DataGridView.RowsDefaultCellStyle%2A> property.</span></span>

    > [!NOTE]
    > <span data-ttu-id="a639f-116">Les cellules sont affichées à l’aide de styles hérités de plusieurs propriétés.</span><span class="sxs-lookup"><span data-stu-id="a639f-116">Cells are displayed using styles inherited from multiple properties.</span></span> <span data-ttu-id="a639f-117">Pour plus d’informations sur l’héritage de style, consultez [styles de cellule dans le contrôle DataGridView Windows Forms](cell-styles-in-the-windows-forms-datagridview-control.md).</span><span class="sxs-lookup"><span data-stu-id="a639f-117">For more information about style inheritance, see [Cell Styles in the Windows Forms DataGridView Control](cell-styles-in-the-windows-forms-datagridview-control.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="a639f-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a639f-118">See also</span></span>

- <xref:System.Windows.Forms.DataGridView>
- [<span data-ttu-id="a639f-119">Styles de cellules dans le contrôle DataGridView Windows Forms</span><span class="sxs-lookup"><span data-stu-id="a639f-119">Cell Styles in the Windows Forms DataGridView Control</span></span>](cell-styles-in-the-windows-forms-datagridview-control.md)
- [<span data-ttu-id="a639f-120">Mises en forme et styles de base dans le contrôle DataGridView Windows Forms</span><span class="sxs-lookup"><span data-stu-id="a639f-120">Basic Formatting and Styling in the Windows Forms DataGridView Control</span></span>](basic-formatting-and-styling-in-the-windows-forms-datagridview-control.md)
- [<span data-ttu-id="a639f-121">Utilisation du concepteur avec le contrôle DataGridView Windows Forms</span><span class="sxs-lookup"><span data-stu-id="a639f-121">Using the Designer with the Windows Forms DataGridView Control</span></span>](using-the-designer-with-the-windows-forms-datagridview-control.md)
- [<span data-ttu-id="a639f-122">Guide pratique : Créer un projet Application Windows Forms</span><span class="sxs-lookup"><span data-stu-id="a639f-122">How to: Create a Windows Forms application project</span></span>](/visualstudio/ide/step-1-create-a-windows-forms-application-project)
- [<span data-ttu-id="a639f-123">Guide pratique pour Ajouter des contrôles à Windows Forms</span><span class="sxs-lookup"><span data-stu-id="a639f-123">How to: Add Controls to Windows Forms</span></span>](how-to-add-controls-to-windows-forms.md)
