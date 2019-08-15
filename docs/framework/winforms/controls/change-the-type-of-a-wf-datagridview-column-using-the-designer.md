---
title: 'Procédure : modifier le type d’une colonne DataGridView Windows Forms à l’aide du concepteur'
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms, columns
- columns [Windows Forms], types
- DataGridView control [Windows Forms], changing column type
- data [Windows Forms], displaying
ms.assetid: 7f994d45-600d-4190-a187-35803214b40c
ms.openlocfilehash: f40ab6fe000f9104b10d5841f52eadf102a91a6b
ms.sourcegitcommit: cf9515122fce716bcfb6618ba366e39b5a2eb81e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/15/2019
ms.locfileid: "69040482"
---
# <a name="how-to-change-the-type-of-a-windows-forms-datagridview-column-using-the-designer"></a><span data-ttu-id="5978f-102">Procédure : modifier le type d’une colonne DataGridView Windows Forms à l’aide du concepteur</span><span class="sxs-lookup"><span data-stu-id="5978f-102">How to: Change the Type of a Windows Forms DataGridView Column Using the Designer</span></span>
<span data-ttu-id="5978f-103">Parfois, vous souhaiterez modifier le type d’une colonne qui a déjà été ajoutée à un contrôle <xref:System.Windows.Forms.DataGridView> de Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="5978f-103">Sometimes you will want to change the type of a column that has already been added to a Windows Forms <xref:System.Windows.Forms.DataGridView> control.</span></span> <span data-ttu-id="5978f-104">Par exemple, vous souhaiterez peut-être modifier les types de certaines colonnes générées automatiquement lorsque vous liez le contrôle à une source de données.</span><span class="sxs-lookup"><span data-stu-id="5978f-104">For example, you may want to modify the types of some of the columns that are generated automatically when you bind the control to a data source.</span></span> <span data-ttu-id="5978f-105">Cela est utile lorsque la table que vous affichez contient des colonnes contenant des clés étrangères sur les lignes d’une table associée.</span><span class="sxs-lookup"><span data-stu-id="5978f-105">This is useful when the table you display has columns containing foreign keys to rows in a related table.</span></span> <span data-ttu-id="5978f-106">Dans ce cas, vous souhaiterez peut-être remplacer les colonnes de zone de texte qui affichent ces clés étrangères par des colonnes de zone de liste déroulante qui affichent des valeurs plus explicites de la table associée.</span><span class="sxs-lookup"><span data-stu-id="5978f-106">In this case, you may want to replace the text box columns that display these foreign keys with combo box columns that display more meaningful values from the related table.</span></span>

 <span data-ttu-id="5978f-107">La procédure suivante requiert un projet d' **application Windows** avec un formulaire contenant <xref:System.Windows.Forms.DataGridView> un contrôle.</span><span class="sxs-lookup"><span data-stu-id="5978f-107">The following procedure requires a **Windows Application** project with a form containing a <xref:System.Windows.Forms.DataGridView> control.</span></span> <span data-ttu-id="5978f-108">Pour plus d’informations sur la configuration d’un tel [projet, consultez Procédure: Créez un projet](/visualstudio/ide/step-1-create-a-windows-forms-application-project) d’application Windows Forms [et procédez comme suit: Ajoutez des contrôles à](how-to-add-controls-to-windows-forms.md)Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="5978f-108">For information about setting up such a project, see [How to: Create a Windows Forms application project](/visualstudio/ide/step-1-create-a-windows-forms-application-project) and [How to: Add Controls to Windows Forms](how-to-add-controls-to-windows-forms.md).</span></span>

### <a name="to-change-the-type-of-a-column-using-the-designer"></a><span data-ttu-id="5978f-109">Pour modifier le type d’une colonne à l’aide du concepteur</span><span class="sxs-lookup"><span data-stu-id="5978f-109">To change the type of a column using the designer</span></span>

1. <span data-ttu-id="5978f-110">Cliquez sur le glyphe de balise active (![glyphe de balise active](./media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")) dans le <xref:System.Windows.Forms.DataGridView> coin supérieur droit du contrôle, puis sélectionnez Modifier les **colonnes**.</span><span class="sxs-lookup"><span data-stu-id="5978f-110">Click the smart tag glyph (![Smart Tag Glyph](./media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")) on the upper-right corner of the <xref:System.Windows.Forms.DataGridView> control, and then select **Edit Columns**.</span></span>

2. <span data-ttu-id="5978f-111">Sélectionnez une colonne dans la liste **colonnes sélectionnées** .</span><span class="sxs-lookup"><span data-stu-id="5978f-111">Select a column from the **Selected Columns** list.</span></span>

3. <span data-ttu-id="5978f-112">Dans la grille Propriétés de la **colonne** , `ColumnType` définissez la propriété sur le nouveau type de colonne.</span><span class="sxs-lookup"><span data-stu-id="5978f-112">In the **Column Properties** grid, set the `ColumnType` property to the new column type.</span></span>

    > [!NOTE]
    >  <span data-ttu-id="5978f-113">La `ColumnType` propriété est une propriété au moment du design qui indique la classe représentant le type de colonne.</span><span class="sxs-lookup"><span data-stu-id="5978f-113">The `ColumnType` property is a design-time-only property that indicates the class representing the column type.</span></span> <span data-ttu-id="5978f-114">Il ne s’agit pas d’une propriété réelle définie dans une classe Column.</span><span class="sxs-lookup"><span data-stu-id="5978f-114">It is not an actual property defined in a column class.</span></span>

## <a name="see-also"></a><span data-ttu-id="5978f-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="5978f-115">See also</span></span>

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridViewColumn>
- [<span data-ttu-id="5978f-116">Guide pratique pour Créer un projet Application Windows Forms</span><span class="sxs-lookup"><span data-stu-id="5978f-116">How to: Create a Windows Forms application project</span></span>](/visualstudio/ide/step-1-create-a-windows-forms-application-project)
- [<span data-ttu-id="5978f-117">Guide pratique pour Ajouter des contrôles à Windows Forms</span><span class="sxs-lookup"><span data-stu-id="5978f-117">How to: Add Controls to Windows Forms</span></span>](how-to-add-controls-to-windows-forms.md)
