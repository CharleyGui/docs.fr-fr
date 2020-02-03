---
title: Définir les modes de redimensionnement du contrôle DataGridView
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data grids [Windows Forms], setting sizing modes
- DataGridView control [Windows Forms], sizing modes
ms.assetid: e9ad15e6-b4bb-44aa-a767-3738e9db1651
ms.openlocfilehash: 15b084afa4149ac43d40aeae7f35f0eaff5ac0e1
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76738392"
---
# <a name="how-to-set-the-sizing-modes-of-the-windows-forms-datagridview-control"></a><span data-ttu-id="bd0b0-102">Comment : définir les modes de redimensionnement du contrôle DataGridView Windows Forms</span><span class="sxs-lookup"><span data-stu-id="bd0b0-102">How to: Set the Sizing Modes of the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="bd0b0-103">Les procédures suivantes montrent des scénarios courants de personnalisation et de combinaison des options de dimensionnement disponibles pour le contrôle <xref:System.Windows.Forms.DataGridView> et pour certaines colonnes des contrôles.</span><span class="sxs-lookup"><span data-stu-id="bd0b0-103">The following procedures demonstrate some common scenarios that customize or combine the sizing options available for the <xref:System.Windows.Forms.DataGridView> control and for specific columns in a control.</span></span>  
  
### <a name="to-create-a-fixed-width-column"></a><span data-ttu-id="bd0b0-104">Pour créer une colonne de largeur fixe</span><span class="sxs-lookup"><span data-stu-id="bd0b0-104">To create a fixed-width column</span></span>  
  
- <span data-ttu-id="bd0b0-105">Définissez la propriété <xref:System.Windows.Forms.DataGridViewColumn.AutoSizeMode%2A> sur <xref:System.Windows.Forms.DataGridViewAutoSizeColumnMode.None>, la propriété <xref:System.Windows.Forms.DataGridViewColumn.Resizable%2A> sur <xref:System.Windows.Forms.DataGridViewTriState.False>, la propriété <xref:System.Windows.Forms.DataGridViewColumn.ReadOnly%2A> sur `true`, et la propriété <xref:System.Windows.Forms.DataGridViewColumn.Width%2A> sur une valeur appropriée.</span><span class="sxs-lookup"><span data-stu-id="bd0b0-105">Set the <xref:System.Windows.Forms.DataGridViewColumn.AutoSizeMode%2A> property to <xref:System.Windows.Forms.DataGridViewAutoSizeColumnMode.None>, the <xref:System.Windows.Forms.DataGridViewColumn.Resizable%2A> property to <xref:System.Windows.Forms.DataGridViewTriState.False>, the <xref:System.Windows.Forms.DataGridViewColumn.ReadOnly%2A> property to `true`, and the <xref:System.Windows.Forms.DataGridViewColumn.Width%2A> property to an appropriate value.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewSizingScenarios#10](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSizingScenarios/CS/sizingscenarios.cs#10)]
     [!code-vb[System.Windows.Forms.DataGridViewSizingScenarios#10](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSizingScenarios/vb/sizingscenarios.vb#10)]  
  
### <a name="to-create-a-column-that-adjusts-its-size-to-fit-its-content"></a><span data-ttu-id="bd0b0-106">Pour créer une colonne dont la taille s'ajuste au contenu</span><span class="sxs-lookup"><span data-stu-id="bd0b0-106">To create a column that adjusts its size to fit its content</span></span>  
  
- <span data-ttu-id="bd0b0-107">Définissez la propriété <xref:System.Windows.Forms.DataGridViewColumn.AutoSizeMode%2A> sur un mode de dimensionnement basé sur le contenu.</span><span class="sxs-lookup"><span data-stu-id="bd0b0-107">Set the <xref:System.Windows.Forms.DataGridViewColumn.AutoSizeMode%2A> property to a content-based sizing mode.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewSizingScenarios#20](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSizingScenarios/CS/sizingscenarios.cs#20)]
     [!code-vb[System.Windows.Forms.DataGridViewSizingScenarios#20](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSizingScenarios/vb/sizingscenarios.vb#20)]  
  
### <a name="to-create-fill-mode-columns-for-values-of-varying-size-and-importance"></a><span data-ttu-id="bd0b0-108">Pour créer des colonnes avec mode de remplissage pour les valeurs de taille et d'importance variables</span><span class="sxs-lookup"><span data-stu-id="bd0b0-108">To create fill-mode columns for values of varying size and importance</span></span>  
  
- <span data-ttu-id="bd0b0-109">Définissez la propriété <xref:System.Windows.Forms.DataGridView.AutoSizeColumnsMode%2A?displayProperty=nameWithType> sur <xref:System.Windows.Forms.DataGridViewAutoSizeColumnsMode.Fill> pour définir le mode de dimensionnement de toutes les colonnes qui ne substituent pas cette valeur.</span><span class="sxs-lookup"><span data-stu-id="bd0b0-109">Set the <xref:System.Windows.Forms.DataGridView.AutoSizeColumnsMode%2A?displayProperty=nameWithType> property to <xref:System.Windows.Forms.DataGridViewAutoSizeColumnsMode.Fill> to set the sizing mode for all columns that do not override this value.</span></span> <span data-ttu-id="bd0b0-110">Définissez la propriété <xref:System.Windows.Forms.DataGridViewColumn.FillWeight%2A> des colonnes sur des valeurs qui soient proportionnelles à leur largeur moyenne de contenu.</span><span class="sxs-lookup"><span data-stu-id="bd0b0-110">Set the <xref:System.Windows.Forms.DataGridViewColumn.FillWeight%2A> properties of the columns to values that are proportional to their average content widths.</span></span> <span data-ttu-id="bd0b0-111">Définissez la propriété <xref:System.Windows.Forms.DataGridViewColumn.MinimumWidth%2A> des colonnes importantes pour garantir un affichage partiel du contenu.</span><span class="sxs-lookup"><span data-stu-id="bd0b0-111">Set the <xref:System.Windows.Forms.DataGridViewColumn.MinimumWidth%2A> properties of important columns to ensure partial content display.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewSizingScenarios#30](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSizingScenarios/CS/sizingscenarios.cs#30)]
     [!code-vb[System.Windows.Forms.DataGridViewSizingScenarios#30](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSizingScenarios/vb/sizingscenarios.vb#30)]  
  
## <a name="example"></a><span data-ttu-id="bd0b0-112">Exemple</span><span class="sxs-lookup"><span data-stu-id="bd0b0-112">Example</span></span>  
 <span data-ttu-id="bd0b0-113">L'exemple de code complet suivant est une démonstration d'application qui peut vous aider à comprendre les options de dimensionnement décrites dans cette rubrique.</span><span class="sxs-lookup"><span data-stu-id="bd0b0-113">The following complete code example provides a demonstration application that can help you understand the sizing options described in this topic.</span></span>  
  
 [!code-csharp[System.Windows.Forms.DataGridViewSizingScenarios#00](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSizingScenarios/CS/sizingscenarios.cs#00)]
 [!code-vb[System.Windows.Forms.DataGridViewSizingScenarios#00](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSizingScenarios/vb/sizingscenarios.vb#00)]  
  
 <span data-ttu-id="bd0b0-114">Pour utiliser cette démonstration d'application :</span><span class="sxs-lookup"><span data-stu-id="bd0b0-114">To use this demonstration application:</span></span>  
  
- <span data-ttu-id="bd0b0-115">Modifiez la taille du formulaire.</span><span class="sxs-lookup"><span data-stu-id="bd0b0-115">Change the size of the form.</span></span> <span data-ttu-id="bd0b0-116">Observez comment les colonnes avec mode de remplissage changent tout en conservant les proportions indiquées par les valeurs de propriétés <xref:System.Windows.Forms.DataGridViewColumn.FillWeight%2A>.</span><span class="sxs-lookup"><span data-stu-id="bd0b0-116">Observe how the fill-mode columns change their widths while retaining the proportions indicated by the <xref:System.Windows.Forms.DataGridViewColumn.FillWeight%2A> property values.</span></span> <span data-ttu-id="bd0b0-117">Observez comment la <xref:System.Windows.Forms.DataGridViewColumn.MinimumWidth%2A> d'une colonne empêche celle-ci de changer quand le formulaire est trop petit.</span><span class="sxs-lookup"><span data-stu-id="bd0b0-117">Observe how a column's <xref:System.Windows.Forms.DataGridViewColumn.MinimumWidth%2A> prevents it from changing when the form is too small.</span></span>  
  
- <span data-ttu-id="bd0b0-118">Modifiez les tailles des colonnes en faisant glisser les séparateurs de colonnes avec la souris.</span><span class="sxs-lookup"><span data-stu-id="bd0b0-118">Change the column sizes by dragging the column dividers with the mouse.</span></span> <span data-ttu-id="bd0b0-119">Observez comment certaines colonnes ne peuvent pas être redimensionnées et comment les colonnes redimensionnables ne peuvent pas devenir plus étroites que leur largeur minimale.</span><span class="sxs-lookup"><span data-stu-id="bd0b0-119">Observe how some columns cannot be resized, and how resizable columns cannot be made narrower than their minimum widths.</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="bd0b0-120">Compilation du code</span><span class="sxs-lookup"><span data-stu-id="bd0b0-120">Compiling the Code</span></span>  
 <span data-ttu-id="bd0b0-121">Cet exemple nécessite :</span><span class="sxs-lookup"><span data-stu-id="bd0b0-121">This example requires:</span></span>  
  
- <span data-ttu-id="bd0b0-122">des références aux assemblys System et System.Windows.Forms.</span><span class="sxs-lookup"><span data-stu-id="bd0b0-122">References to the System and System.Windows.Forms assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bd0b0-123">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="bd0b0-123">See also</span></span>

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridViewColumn.AutoSizeMode%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewAutoSizeColumnMode>
- <xref:System.Windows.Forms.DataGridViewColumn.Resizable%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewColumn.ReadOnly%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewColumn.Width%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewColumn.FillWeight%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewColumn.MinimumWidth%2A?displayProperty=nameWithType>
