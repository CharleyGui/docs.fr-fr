---
title: Redimensionner des colonnes et des lignes dans le contrôle DataGridView
ms.date: 03/30/2017
helpviewer_keywords:
- DataGridView control [Windows Forms], sizing rows and columns
- columns [Windows Forms], resizing in grids
- data grids [Windows Forms], resizing columns and rows
ms.assetid: 7532764d-e5c1-4943-a08b-6377a722d3b6
ms.openlocfilehash: 8f8394a837ccc11c469f9ad4feeb60464d0014fe
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76742412"
---
# <a name="resizing-columns-and-rows-in-the-windows-forms-datagridview-control"></a><span data-ttu-id="0fd5e-102">Redimensionnement des colonnes et des lignes dans le contrôle DataGridView Windows Forms</span><span class="sxs-lookup"><span data-stu-id="0fd5e-102">Resizing Columns and Rows in the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="0fd5e-103">Le contrôle `DataGridView` fournit de nombreuses options permettant de personnaliser le comportement de dimensionnement de ses colonnes et de ses lignes.</span><span class="sxs-lookup"><span data-stu-id="0fd5e-103">The `DataGridView` control provides numerous options for customizing the sizing behavior of its columns and rows.</span></span> <span data-ttu-id="0fd5e-104">En règle générale, les cellules `DataGridView` ne sont pas redimensionnées en fonction de leur contenu.</span><span class="sxs-lookup"><span data-stu-id="0fd5e-104">Typically, `DataGridView` cells do not resize based on their contents.</span></span> <span data-ttu-id="0fd5e-105">Au lieu de cela, ils détourent toute valeur d’affichage supérieure à la cellule.</span><span class="sxs-lookup"><span data-stu-id="0fd5e-105">Instead, they clip any display value that is larger than the cell.</span></span> <span data-ttu-id="0fd5e-106">Si le contenu peut être affiché sous forme de chaîne, la cellule l’affiche dans une info-bulle.</span><span class="sxs-lookup"><span data-stu-id="0fd5e-106">If the content can be displayed as a string, the cell displays it in a ToolTip.</span></span>  
  
 <span data-ttu-id="0fd5e-107">Par défaut, les utilisateurs peuvent faire glisser les séparateurs de ligne, de colonne et d’en-tête avec la souris pour afficher plus d’informations.</span><span class="sxs-lookup"><span data-stu-id="0fd5e-107">By default, users can drag row, column, and header dividers with the mouse to show more information.</span></span> <span data-ttu-id="0fd5e-108">Les utilisateurs peuvent également double-cliquer sur un séparateur pour redimensionner automatiquement la ligne, la colonne ou la bande d’en-tête associée en fonction de son contenu.</span><span class="sxs-lookup"><span data-stu-id="0fd5e-108">Users can also double-click a divider to automatically resize the associated row, column, or header band based on its contents.</span></span>  
  
 <span data-ttu-id="0fd5e-109">Le contrôle `DataGridView` fournit des propriétés, des méthodes et des événements qui vous permettent de personnaliser ou de désactiver tous ces comportements dirigés par l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="0fd5e-109">The `DataGridView` control provides properties, methods, and events that enable you to customize or disable all of these user-directed behaviors.</span></span> <span data-ttu-id="0fd5e-110">En outre, vous pouvez redimensionner des lignes, des colonnes et des en-têtes par programmation en fonction de leur contenu, ou vous pouvez les configurer pour qu’ils se redimensionnent automatiquement chaque fois que leur contenu change.</span><span class="sxs-lookup"><span data-stu-id="0fd5e-110">Additionally, you can programmatically resize rows, columns, and headers to fit their contents, or you can configure them to automatically resize themselves whenever their contents change.</span></span> <span data-ttu-id="0fd5e-111">Vous pouvez également configurer des colonnes pour diviser automatiquement la largeur disponible du contrôle dans les proportions que vous spécifiez.</span><span class="sxs-lookup"><span data-stu-id="0fd5e-111">You can also configure columns to automatically divide the available width of the control in proportions that you specify.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="0fd5e-112">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="0fd5e-112">In This Section</span></span>  
 [<span data-ttu-id="0fd5e-113">Options de dimensionnement dans le contrôle DataGridView Windows Forms</span><span class="sxs-lookup"><span data-stu-id="0fd5e-113">Sizing Options in the Windows Forms DataGridView Control</span></span>](sizing-options-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="0fd5e-114">Décrit les options de dimensionnement des lignes, des colonnes et des en-têtes.</span><span class="sxs-lookup"><span data-stu-id="0fd5e-114">Describes the options for sizing rows, columns, and headers.</span></span> <span data-ttu-id="0fd5e-115">Fournit également des détails sur les propriétés et les méthodes liées au dimensionnement, et décrit les scénarios d’utilisation courants.</span><span class="sxs-lookup"><span data-stu-id="0fd5e-115">Also provides details on sizing-related properties and methods, and describes common usage scenarios.</span></span>  
  
 [<span data-ttu-id="0fd5e-116">Mode Remplissage des colonnes dans le contrôle DataGridView Windows Forms</span><span class="sxs-lookup"><span data-stu-id="0fd5e-116">Column Fill Mode in the Windows Forms DataGridView Control</span></span>](column-fill-mode-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="0fd5e-117">Décrit le mode de remplissage de colonne en détail et fournit un code de démonstration que vous pouvez utiliser pour expérimenter le mode de remplissage de colonne et d’autres modes.</span><span class="sxs-lookup"><span data-stu-id="0fd5e-117">Describes column fill mode in detail, and provides demonstration code that you can use to experiment with column fill mode and other modes.</span></span>  
  
 [<span data-ttu-id="0fd5e-118">Guide pratique pour définir les modes de redimensionnement du contrôle DataGridView Windows Forms</span><span class="sxs-lookup"><span data-stu-id="0fd5e-118">How to: Set the Sizing Modes of the Windows Forms DataGridView Control</span></span>](how-to-set-the-sizing-modes-of-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="0fd5e-119">Décrit comment configurer les modes de dimensionnement à des fins courantes.</span><span class="sxs-lookup"><span data-stu-id="0fd5e-119">Describes how to configure the sizing modes for common purposes.</span></span>  
  
 [<span data-ttu-id="0fd5e-120">Guide pratique pour redimensionner des cellules par programme pour les adapter au contenu du contrôle DataGridView Windows Forms</span><span class="sxs-lookup"><span data-stu-id="0fd5e-120">How to: Programmatically Resize Cells to Fit Content in the Windows Forms DataGridView Control</span></span>](programmatically-resize-cells-to-fit-content-in-the-datagrid.md)  
 <span data-ttu-id="0fd5e-121">Fournit un code de démonstration que vous pouvez utiliser pour expérimenter le redimensionnement par programmation.</span><span class="sxs-lookup"><span data-stu-id="0fd5e-121">Provides demonstration code that you can use to experiment with programmatic resizing.</span></span>  
  
 [<span data-ttu-id="0fd5e-122">Guide pratique pour redimensionner automatiquement des cellules lorsque leur contenu change dans le contrôle DataGridView Windows Forms</span><span class="sxs-lookup"><span data-stu-id="0fd5e-122">How to: Automatically Resize Cells When Content Changes in the Windows Forms DataGridView Control</span></span>](automatically-resize-cells-when-content-changes-in-the-datagrid.md)  
 <span data-ttu-id="0fd5e-123">Fournit un code de démonstration que vous pouvez utiliser pour expérimenter les modes de dimensionnement automatique.</span><span class="sxs-lookup"><span data-stu-id="0fd5e-123">Provides demonstration code that you can use to experiment with automatic sizing modes.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="0fd5e-124">Reference</span><span class="sxs-lookup"><span data-stu-id="0fd5e-124">Reference</span></span>  
 <xref:System.Windows.Forms.DataGridView>  
 <span data-ttu-id="0fd5e-125">Fournit une documentation de référence pour le contrôle <xref:System.Windows.Forms.DataGridView>.</span><span class="sxs-lookup"><span data-stu-id="0fd5e-125">Provides reference documentation for the <xref:System.Windows.Forms.DataGridView> control.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0fd5e-126">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="0fd5e-126">See also</span></span>

- [<span data-ttu-id="0fd5e-127">DataGridView, contrôle</span><span class="sxs-lookup"><span data-stu-id="0fd5e-127">DataGridView Control</span></span>](datagridview-control-windows-forms.md)
