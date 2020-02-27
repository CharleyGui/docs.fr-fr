---
title: Ajouter et supprimer des colonnes dans le contrôle DataGridView à l’aide du concepteur
ms.date: 03/30/2017
f1_keywords:
- vs.DataGridViewAddColumnDialog
helpviewer_keywords:
- DataGridView control [Windows Forms], adding columns
- DataGridView control [Windows Forms], removing columns
ms.assetid: 9e709f35-0a8c-4e7e-b4c4-bacb7a834077
ms.openlocfilehash: 8843b1d30f3e5f31a060e27b41b0105e6584f155
ms.sourcegitcommit: 44a7cd8687f227fc6db3211ccf4783dc20235e51
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/26/2020
ms.locfileid: "77628603"
---
# <a name="how-to-add-and-remove-columns-in-the-windows-forms-datagridview-control-using-the-designer"></a><span data-ttu-id="a5379-102">Comment : ajouter et supprimer des colonnes dans le contrôle DataGridView Windows Forms à l'aide du concepteur</span><span class="sxs-lookup"><span data-stu-id="a5379-102">How to: Add and Remove Columns in the Windows Forms DataGridView Control Using the Designer</span></span>
<span data-ttu-id="a5379-103">Le contrôle de <xref:System.Windows.Forms.DataGridView> Windows Forms doit contenir des colonnes pour afficher les données.</span><span class="sxs-lookup"><span data-stu-id="a5379-103">The Windows Forms <xref:System.Windows.Forms.DataGridView> control must contain columns in order to display data.</span></span> <span data-ttu-id="a5379-104">Si vous envisagez de remplir le contrôle manuellement, vous devez ajouter les colonnes vous-même.</span><span class="sxs-lookup"><span data-stu-id="a5379-104">If you plan to populate the control manually, you must add the columns yourself.</span></span> <span data-ttu-id="a5379-105">Vous pouvez également lier le contrôle à une source de données, qui génère et remplit automatiquement les colonnes.</span><span class="sxs-lookup"><span data-stu-id="a5379-105">Alternately, you can bind the control to a data source, which generates and populates the columns automatically.</span></span> <span data-ttu-id="a5379-106">Si la source de données contient plus de colonnes que vous ne souhaitez afficher, vous pouvez supprimer les colonnes indésirables.</span><span class="sxs-lookup"><span data-stu-id="a5379-106">If the data source contains more columns than you want to display, you can remove the unwanted columns.</span></span>

 <span data-ttu-id="a5379-107">Les procédures suivantes requièrent un projet d' **application Windows** avec un formulaire contenant un contrôle de <xref:System.Windows.Forms.DataGridView>.</span><span class="sxs-lookup"><span data-stu-id="a5379-107">The following procedures require a **Windows Application** project with a form containing a <xref:System.Windows.Forms.DataGridView> control.</span></span> <span data-ttu-id="a5379-108">Pour plus d’informations sur la configuration d’un tel projet, consultez [Comment : créer un projet d’application Windows Forms](/visualstudio/ide/step-1-create-a-windows-forms-application-project) et [Comment : ajouter des contrôles à des Windows Forms](how-to-add-controls-to-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="a5379-108">For information about setting up such a project, see [How to: Create a Windows Forms application project](/visualstudio/ide/step-1-create-a-windows-forms-application-project) and [How to: Add Controls to Windows Forms](how-to-add-controls-to-windows-forms.md).</span></span>

## <a name="to-add-a-column-using-the-designer"></a><span data-ttu-id="a5379-109">Pour ajouter une colonne à l’aide du concepteur</span><span class="sxs-lookup"><span data-stu-id="a5379-109">To add a column using the designer</span></span>

1. <span data-ttu-id="a5379-110">Cliquez sur le glyphe actions du concepteur (![petite flèche noire](./media/designer-actions-glyph.gif)) dans le coin supérieur droit du contrôle <xref:System.Windows.Forms.DataGridView>, puis sélectionnez **Ajouter une colonne**.</span><span class="sxs-lookup"><span data-stu-id="a5379-110">Click the designer actions glyph (![Small black arrow](./media/designer-actions-glyph.gif)) on the upper-right corner of the <xref:System.Windows.Forms.DataGridView> control, and then select **Add Column**.</span></span>

2. <span data-ttu-id="a5379-111">Dans la boîte de dialogue **Ajouter une colonne** , choisissez l’option de **colonne DataBound** et sélectionnez une colonne dans la source de données, ou choisissez l’option **colonne indépendante** et définissez la colonne à l’aide des champs fournis.</span><span class="sxs-lookup"><span data-stu-id="a5379-111">In the **Add Column** dialog box, choose the **Databound Column** option and select a column from the data source, or choose the **Unbound Column** option and define the column using the fields provided.</span></span>

3. <span data-ttu-id="a5379-112">Cliquez sur le bouton **Ajouter** pour ajouter la colonne, provoquant son affichage dans le concepteur si les colonnes existantes ne remplissent pas encore la zone d’affichage du contrôle.</span><span class="sxs-lookup"><span data-stu-id="a5379-112">Click the **Add** button to add the column, causing it to appear in the designer if the existing columns do not already fill the control display area.</span></span>

    > [!NOTE]
    > <span data-ttu-id="a5379-113">Vous pouvez modifier les propriétés des colonnes dans la boîte de dialogue **modifier les colonnes** , à laquelle vous pouvez accéder à partir de la balise active du contrôle.</span><span class="sxs-lookup"><span data-stu-id="a5379-113">You can modify column properties in the **Edit Columns** dialog box, which you can access from the control's smart tag.</span></span>

## <a name="to-remove-a-column-using-the-designer"></a><span data-ttu-id="a5379-114">Pour supprimer une colonne à l’aide du concepteur</span><span class="sxs-lookup"><span data-stu-id="a5379-114">To remove a column using the designer</span></span>

1. <span data-ttu-id="a5379-115">Choisissez **modifier les colonnes** à partir de la balise active du contrôle.</span><span class="sxs-lookup"><span data-stu-id="a5379-115">Choose **Edit Columns** from the control's smart tag.</span></span>

2. <span data-ttu-id="a5379-116">Sélectionnez une colonne dans la liste **colonnes sélectionnées** .</span><span class="sxs-lookup"><span data-stu-id="a5379-116">Select a column from the **Selected Columns** list.</span></span>

3. <span data-ttu-id="a5379-117">Cliquez sur le bouton **supprimer** pour supprimer la colonne, provoquant sa disparition du concepteur.</span><span class="sxs-lookup"><span data-stu-id="a5379-117">Click the **Remove** button to delete the column, causing it to disappear from the designer.</span></span>

## <a name="see-also"></a><span data-ttu-id="a5379-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a5379-118">See also</span></span>

- <xref:System.Windows.Forms.DataGridView>
- [<span data-ttu-id="a5379-119">Comment : créer un projet d’application Windows Forms</span><span class="sxs-lookup"><span data-stu-id="a5379-119">How to: Create a Windows Forms application project</span></span>](/visualstudio/ide/step-1-create-a-windows-forms-application-project)
- [<span data-ttu-id="a5379-120">Comment : ajouter des contrôles à des Windows Forms</span><span class="sxs-lookup"><span data-stu-id="a5379-120">How to: Add Controls to Windows Forms</span></span>](how-to-add-controls-to-windows-forms.md)
