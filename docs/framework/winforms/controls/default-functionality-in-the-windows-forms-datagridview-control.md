---
title: Fonctionnalités par défaut du contrôle DataGridView
ms.date: 03/30/2017
helpviewer_keywords:
- data grids [Windows Forms], default functionality in DataGridView control
- DataGridView control [Windows Forms], default functionality
ms.assetid: 4405f697-cad1-4839-9bcd-8ddb09d9f00e
ms.openlocfilehash: b695883ac7ec3fb0c459adb66214b0eceab3a128
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76746132"
---
# <a name="default-functionality-in-the-windows-forms-datagridview-control"></a><span data-ttu-id="22680-102">Fonctionnalités par défaut du contrôle DataGridView Windows Forms</span><span class="sxs-lookup"><span data-stu-id="22680-102">Default Functionality in the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="22680-103">Le contrôle Windows Forms <xref:System.Windows.Forms.DataGridView> fournit aux utilisateurs une quantité significative de fonctionnalités par défaut.</span><span class="sxs-lookup"><span data-stu-id="22680-103">The Windows Forms <xref:System.Windows.Forms.DataGridView> control provides users with a significant amount of default functionality.</span></span>  
  
## <a name="default-functionality"></a><span data-ttu-id="22680-104">Fonctionnalité par défaut</span><span class="sxs-lookup"><span data-stu-id="22680-104">Default Functionality</span></span>  
 <span data-ttu-id="22680-105">Par défaut, un contrôle de <xref:System.Windows.Forms.DataGridView> :</span><span class="sxs-lookup"><span data-stu-id="22680-105">By default, a <xref:System.Windows.Forms.DataGridView> control:</span></span>  
  
- <span data-ttu-id="22680-106">Affiche automatiquement les en-têtes de colonnes et les en-têtes de lignes qui restent visibles lorsque la table défile verticalement.</span><span class="sxs-lookup"><span data-stu-id="22680-106">Automatically displays column headers and row headers that remain visible as the table scrolls vertically.</span></span>  
  
- <span data-ttu-id="22680-107">Possède un en-tête de ligne qui contient un indicateur de sélection pour la ligne actuelle.</span><span class="sxs-lookup"><span data-stu-id="22680-107">Has a row header that contains a selection indicator for the current row.</span></span>  
  
- <span data-ttu-id="22680-108">Possède un rectangle de sélection dans la première cellule.</span><span class="sxs-lookup"><span data-stu-id="22680-108">Has a selection rectangle in the first cell.</span></span>  
  
- <span data-ttu-id="22680-109">Contient des colonnes qui peuvent être redimensionnées automatiquement lorsque l’utilisateur double-clique sur les séparateurs de colonnes.</span><span class="sxs-lookup"><span data-stu-id="22680-109">Has columns that can be automatically resized when the user double-clicks the column dividers.</span></span>  
  
- <span data-ttu-id="22680-110">Prend automatiquement en charge les styles visuels sur Windows XP et la famille Windows Server 2003 quand la méthode <xref:System.Windows.Forms.Application.EnableVisualStyles%2A> est appelée à partir de la méthode `Main` de l’application.</span><span class="sxs-lookup"><span data-stu-id="22680-110">Automatically supports visual styles on Windows XP and the Windows Server 2003 family when the <xref:System.Windows.Forms.Application.EnableVisualStyles%2A> method is called from the application's `Main` method.</span></span>  
  
 <span data-ttu-id="22680-111">En outre, le contenu d’un contrôle de <xref:System.Windows.Forms.DataGridView> peut être modifié par défaut :</span><span class="sxs-lookup"><span data-stu-id="22680-111">Additionally, the contents of a <xref:System.Windows.Forms.DataGridView> control can be edited by default:</span></span>  
  
- <span data-ttu-id="22680-112">Si l’utilisateur double-clique ou appuie sur F2 dans une cellule, le contrôle met automatiquement la cellule en mode édition et met à jour le contenu de la cellule au fur et à mesure que l’utilisateur tape.</span><span class="sxs-lookup"><span data-stu-id="22680-112">If the user double-clicks or presses F2 in a cell, the control automatically puts the cell into edit mode and updates the contents of the cell as the user types.</span></span>  
  
- <span data-ttu-id="22680-113">Si l’utilisateur fait défiler jusqu’à la fin de la grille, l’utilisateur verra qu’une ligne pour l’ajout de nouveaux enregistrements est présente.</span><span class="sxs-lookup"><span data-stu-id="22680-113">If the user scrolls to the end of the grid, the user will see that a row for adding new records is present.</span></span> <span data-ttu-id="22680-114">Quand l’utilisateur clique sur cette ligne, une nouvelle ligne est ajoutée au contrôle <xref:System.Windows.Forms.DataGridView>, avec les valeurs par défaut.</span><span class="sxs-lookup"><span data-stu-id="22680-114">When the user clicks this row, a new row is added to the <xref:System.Windows.Forms.DataGridView> control, with default values.</span></span> <span data-ttu-id="22680-115">Quand l’utilisateur appuie sur ÉCHAP, cette nouvelle ligne disparaît.</span><span class="sxs-lookup"><span data-stu-id="22680-115">When the user presses ESC, this new row disappears.</span></span>  
  
- <span data-ttu-id="22680-116">Si l’utilisateur clique sur un en-tête de ligne, la ligne entière est sélectionnée.</span><span class="sxs-lookup"><span data-stu-id="22680-116">If the user clicks a row header, the whole row is selected.</span></span>  
  
 <span data-ttu-id="22680-117">Quand vous liez un contrôle <xref:System.Windows.Forms.DataGridView> à une source de données en définissant sa propriété <xref:System.Windows.Forms.DataGridView.DataSource%2A>, le contrôle :</span><span class="sxs-lookup"><span data-stu-id="22680-117">When you bind a <xref:System.Windows.Forms.DataGridView> control to a data source by setting its <xref:System.Windows.Forms.DataGridView.DataSource%2A> property, the control:</span></span>  
  
- <span data-ttu-id="22680-118">Utilise automatiquement les noms des colonnes de la source de données comme texte d’en-tête de colonne.</span><span class="sxs-lookup"><span data-stu-id="22680-118">Automatically uses the names of the data source's columns as the column header text.</span></span>  
  
- <span data-ttu-id="22680-119">Est rempli avec le contenu de la source de données.</span><span class="sxs-lookup"><span data-stu-id="22680-119">Is populated with the contents of the data source.</span></span> <span data-ttu-id="22680-120"><xref:System.Windows.Forms.DataGridView> colonnes sont automatiquement créées pour chaque colonne de la source de données.</span><span class="sxs-lookup"><span data-stu-id="22680-120"><xref:System.Windows.Forms.DataGridView> columns are automatically created for each column in the data source.</span></span>  
  
- <span data-ttu-id="22680-121">Crée une ligne pour chaque ligne visible dans la table.</span><span class="sxs-lookup"><span data-stu-id="22680-121">Creates a row for each visible row in the table.</span></span>  
  
- <span data-ttu-id="22680-122">Trie automatiquement les lignes en fonction des données sous-jacentes lorsque l’utilisateur clique sur un en-tête de colonne.</span><span class="sxs-lookup"><span data-stu-id="22680-122">Automatically sorts the rows based on the underlying data when the user clicks a column header.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="22680-123">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="22680-123">See also</span></span>

- <xref:System.Windows.Forms.DataGridView>
- [<span data-ttu-id="22680-124">DataGridView, contrôle</span><span class="sxs-lookup"><span data-stu-id="22680-124">DataGridView Control</span></span>](datagridview-control-windows-forms.md)
