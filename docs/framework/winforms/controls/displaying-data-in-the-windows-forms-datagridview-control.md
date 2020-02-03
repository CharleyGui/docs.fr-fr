---
title: Affichage des données dans le contrôle DataGridView
ms.date: 03/30/2017
helpviewer_keywords:
- data [Windows Forms], displaying in tabular format
- data grids [Windows Forms], displaying data
- displaying data [Windows Forms], data grids
- DataGridView control [Windows Forms], displaying data
ms.assetid: b170b52a-2ebd-4948-ac2f-e52d494cebb2
ms.openlocfilehash: d02362895d75df3735d19554bd44bb8ac443c6c2
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76745869"
---
# <a name="displaying-data-in-the-windows-forms-datagridview-control"></a><span data-ttu-id="b0f24-102">Affichage des données dans le contrôle DataGridView Windows Forms</span><span class="sxs-lookup"><span data-stu-id="b0f24-102">Displaying Data in the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="b0f24-103">Le contrôle `DataGridView` permet d’afficher des données provenant de diverses sources de données externes.</span><span class="sxs-lookup"><span data-stu-id="b0f24-103">The `DataGridView` control is used to display data from a variety of external data sources.</span></span> <span data-ttu-id="b0f24-104">Vous pouvez également ajouter des lignes et des colonnes au contrôle et les remplir manuellement avec des données.</span><span class="sxs-lookup"><span data-stu-id="b0f24-104">Alternatively, you can add rows and columns to the control and manually populate it with data.</span></span>  
  
 <span data-ttu-id="b0f24-105">Lorsque vous liez le contrôle à une source de données, vous pouvez générer des colonnes automatiquement en fonction du schéma de la source de données.</span><span class="sxs-lookup"><span data-stu-id="b0f24-105">When you bind the control to a data source, you can generate columns automatically based on the schema of the data source.</span></span> <span data-ttu-id="b0f24-106">Si ces colonnes n’apparaissent pas exactement comme vous le souhaitez, vous pouvez les masquer, les supprimer ou les réorganiser.</span><span class="sxs-lookup"><span data-stu-id="b0f24-106">If these columns do not appear just as you want them to, you can hide, remove, or rearrange them.</span></span> <span data-ttu-id="b0f24-107">Vous pouvez également ajouter des colonnes indépendantes pour afficher des données supplémentaires qui ne proviennent pas de la source de données.</span><span class="sxs-lookup"><span data-stu-id="b0f24-107">You can also add unbound columns to display supplemental data that does not come from the data source.</span></span>  
  
 <span data-ttu-id="b0f24-108">En outre, vous pouvez afficher vos données à l’aide de formats standard (tels que le format monétaire), ou vous pouvez personnaliser la mise en forme d’affichage pour présenter vos données, mais vous devez (par exemple, modifier la couleur d’arrière-plan pour les nombres négatifs ou remplacer des valeurs de chaîne). avec les images correspondantes).</span><span class="sxs-lookup"><span data-stu-id="b0f24-108">Additionally, you can display your data using standard formats (such as currency format), or you can customize the display formatting to present your data however you need to (such as changing the background color for negative numbers, or replacing string values with corresponding images).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="b0f24-109">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="b0f24-109">In This Section</span></span>  
 [<span data-ttu-id="b0f24-110">Modes d’affichage des données dans le contrôle DataGridView Windows Forms</span><span class="sxs-lookup"><span data-stu-id="b0f24-110">Data Display Modes in the Windows Forms DataGridView Control</span></span>](data-display-modes-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="b0f24-111">Décrit les options permettant de remplir le contrôle avec des données.</span><span class="sxs-lookup"><span data-stu-id="b0f24-111">Describes the options for populating the control with data.</span></span>  
  
 [<span data-ttu-id="b0f24-112">Mise en forme de données dans le contrôle DataGridView Windows Forms</span><span class="sxs-lookup"><span data-stu-id="b0f24-112">Data Formatting in the Windows Forms DataGridView Control</span></span>](data-formatting-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="b0f24-113">Décrit les options de mise en forme des valeurs d’affichage des cellules.</span><span class="sxs-lookup"><span data-stu-id="b0f24-113">Describes the options for formatting cell display values.</span></span>  
  
 [<span data-ttu-id="b0f24-114">Procédure pas à pas : création d’un contrôle DataGridView Windows Forms non lié</span><span class="sxs-lookup"><span data-stu-id="b0f24-114">Walkthrough: Creating an Unbound Windows Forms DataGridView Control</span></span>](walkthrough-creating-an-unbound-windows-forms-datagridview-control.md)  
 <span data-ttu-id="b0f24-115">Décrit comment remplir manuellement le contrôle avec des données.</span><span class="sxs-lookup"><span data-stu-id="b0f24-115">Describes how to manually populate the control with data.</span></span>  
  
 [<span data-ttu-id="b0f24-116">Guide pratique pour lier des données au contrôle DataGridView Windows Forms</span><span class="sxs-lookup"><span data-stu-id="b0f24-116">How to: Bind Data to the Windows Forms DataGridView Control</span></span>](how-to-bind-data-to-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="b0f24-117">Décrit comment remplir le contrôle avec des données en le liant à un `BindingSource` qui contient des informations extraites d’une base de données.</span><span class="sxs-lookup"><span data-stu-id="b0f24-117">Describes how to populate the control with data by binding it to a `BindingSource` that contains information pulled from a database.</span></span>  
  
 [<span data-ttu-id="b0f24-118">Guide pratique pour générer automatiquement des colonnes dans un contrôle DataGridView Windows Forms lié aux données</span><span class="sxs-lookup"><span data-stu-id="b0f24-118">How to: Autogenerate Columns in a Data-Bound Windows Forms DataGridView Control</span></span>](autogenerate-columns-in-a-data-bound-wf-datagridview-control.md)  
 <span data-ttu-id="b0f24-119">Décrit comment générer automatiquement des colonnes en fonction d’une source de données liée.</span><span class="sxs-lookup"><span data-stu-id="b0f24-119">Describes how to automatically generate columns based on a bound data source.</span></span>  
  
 [<span data-ttu-id="b0f24-120">Guide pratique pour supprimer les colonnes générées automatiquement d'un contrôle DataGridView Windows Forms</span><span class="sxs-lookup"><span data-stu-id="b0f24-120">How to: Remove Autogenerated Columns from a Windows Forms DataGridView Control</span></span>](remove-autogenerated-columns-from-a-wf-datagridview-control.md)  
 <span data-ttu-id="b0f24-121">Décrit comment masquer ou supprimer des colonnes générées automatiquement à partir d’une source de données liée.</span><span class="sxs-lookup"><span data-stu-id="b0f24-121">Describes how to hide or delete columns generated automatically from a bound data source.</span></span>  
  
 [<span data-ttu-id="b0f24-122">Guide pratique pour modifier l'ordre des colonnes dans le contrôle DataGridView Windows Forms</span><span class="sxs-lookup"><span data-stu-id="b0f24-122">How to: Change the Order of Columns in the Windows Forms DataGridView Control</span></span>](how-to-change-the-order-of-columns-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="b0f24-123">Explique comment réorganiser les colonnes générées automatiquement à partir d’une source de données liée.</span><span class="sxs-lookup"><span data-stu-id="b0f24-123">Describes how to rearrange columns generated automatically from a bound data source.</span></span>  
  
 [<span data-ttu-id="b0f24-124">Guide pratique pour ajouter une colonne indépendante à un contrôle DataGridView Windows Forms lié aux données</span><span class="sxs-lookup"><span data-stu-id="b0f24-124">How to: Add an Unbound Column to a Data-Bound Windows Forms DataGridView Control</span></span>](unbound-column-to-a-data-bound-datagridview.md)  
 <span data-ttu-id="b0f24-125">Décrit comment ajouter des données à partir d’une source de données liée en affichant des colonnes supplémentaires non liées.</span><span class="sxs-lookup"><span data-stu-id="b0f24-125">Describes how to supplement data from a bound data source by displaying additional, unbound columns.</span></span>  
  
 [<span data-ttu-id="b0f24-126">Comment : lier des objets aux contrôles DataGridView Windows Forms</span><span class="sxs-lookup"><span data-stu-id="b0f24-126">How to: Bind Objects to Windows Forms DataGridView Controls</span></span>](how-to-bind-objects-to-windows-forms-datagridview-controls.md)  
 <span data-ttu-id="b0f24-127">Décrit comment lier le contrôle à une collection d’objets arbitraires afin que chaque objet soit affiché sur sa propre ligne.</span><span class="sxs-lookup"><span data-stu-id="b0f24-127">Describes how to bind the control to a collection of arbitrary objects so that each object is displayed in its own row.</span></span>  
  
 [<span data-ttu-id="b0f24-128">Comment : accéder à des objets liés à des lignes DataGridView Windows Forms</span><span class="sxs-lookup"><span data-stu-id="b0f24-128">How to: Access Objects Bound to Windows Forms DataGridView Rows</span></span>](how-to-access-objects-bound-to-windows-forms-datagridview-rows.md)  
 <span data-ttu-id="b0f24-129">Décrit comment récupérer un objet lié à une ligne particulière du contrôle.</span><span class="sxs-lookup"><span data-stu-id="b0f24-129">Describes how to retrieve an object bound to a particular row of the control.</span></span>  
  
 [<span data-ttu-id="b0f24-130">Procédure pas à pas : création d'un formulaire maître/détail qui utilise deux contrôles DataGridView Windows Forms</span><span class="sxs-lookup"><span data-stu-id="b0f24-130">Walkthrough: Creating a Master/Detail Form Using Two Windows Forms DataGridView Controls</span></span>](creating-a-master-detail-form-using-two-datagridviews.md)  
 <span data-ttu-id="b0f24-131">Décrit comment afficher des données de deux tables de base de données associées afin que les valeurs affichées dans un contrôle `DataGridView` dépendent de la ligne actuellement sélectionnée dans un autre contrôle.</span><span class="sxs-lookup"><span data-stu-id="b0f24-131">Describes how to display data from two related database tables so that the values shown in one `DataGridView` control depend on the currently selected row in another control.</span></span>  
  
 [<span data-ttu-id="b0f24-132">Guide pratique pour personnaliser la mise en forme des données dans le contrôle DataGridView Windows Forms</span><span class="sxs-lookup"><span data-stu-id="b0f24-132">How to: Customize Data Formatting in the Windows Forms DataGridView Control</span></span>](how-to-customize-data-formatting-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="b0f24-133">Décrit comment gérer l’événement <xref:System.Windows.Forms.DataGridView.CellFormatting?displayProperty=nameWithType> pour modifier l’apparence des cellules en fonction de leurs valeurs.</span><span class="sxs-lookup"><span data-stu-id="b0f24-133">Describes how to handle the <xref:System.Windows.Forms.DataGridView.CellFormatting?displayProperty=nameWithType> event to change the appearance of cells depending on their values.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="b0f24-134">Référence</span><span class="sxs-lookup"><span data-stu-id="b0f24-134">Reference</span></span>  
 <xref:System.Windows.Forms.DataGridView>  
 <span data-ttu-id="b0f24-135">Fournit une documentation de référence pour le contrôle <xref:System.Windows.Forms.DataGridView>.</span><span class="sxs-lookup"><span data-stu-id="b0f24-135">Provides reference documentation for the <xref:System.Windows.Forms.DataGridView> control.</span></span>  
  
 <xref:System.Windows.Forms.DataGridView.DataSource%2A?displayProperty=nameWithType>  
 <span data-ttu-id="b0f24-136">Fournit une documentation de référence pour la propriété <xref:System.Windows.Forms.DataGridView.DataSource%2A>.</span><span class="sxs-lookup"><span data-stu-id="b0f24-136">Provides reference documentation for the <xref:System.Windows.Forms.DataGridView.DataSource%2A> property.</span></span>  
  
 <xref:System.Windows.Forms.BindingSource>  
 <span data-ttu-id="b0f24-137">Fournit la documentation de référence pour le composant <xref:System.Windows.Forms.BindingSource>.</span><span class="sxs-lookup"><span data-stu-id="b0f24-137">Provides reference documentation for the <xref:System.Windows.Forms.BindingSource> component.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="b0f24-138">Sections connexes</span><span class="sxs-lookup"><span data-stu-id="b0f24-138">Related Sections</span></span>  
 [<span data-ttu-id="b0f24-139">Saisie de données dans le contrôle DataGridView Windows Forms</span><span class="sxs-lookup"><span data-stu-id="b0f24-139">Data Entry in the Windows Forms DataGridView Control</span></span>](data-entry-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="b0f24-140">Fournit des rubriques qui décrivent comment modifier la façon dont les utilisateurs ajoutent et modifient des données dans le contrôle.</span><span class="sxs-lookup"><span data-stu-id="b0f24-140">Provides topics that describe how to change the way users add and modify data in the control.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b0f24-141">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b0f24-141">See also</span></span>

- [<span data-ttu-id="b0f24-142">DataGridView, contrôle</span><span class="sxs-lookup"><span data-stu-id="b0f24-142">DataGridView Control</span></span>](datagridview-control-windows-forms.md)
- [<span data-ttu-id="b0f24-143">Types de colonnes dans le contrôle DataGridView Windows Forms</span><span class="sxs-lookup"><span data-stu-id="b0f24-143">Column Types in the Windows Forms DataGridView Control</span></span>](column-types-in-the-windows-forms-datagridview-control.md)
