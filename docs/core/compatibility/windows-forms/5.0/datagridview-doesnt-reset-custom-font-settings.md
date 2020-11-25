---
title: 'Modification avec rupture : DataGridView ne réinitialise plus les polices pour les styles de cellule personnalisés'
description: Découvrez les modifications avec rupture dans .NET 5,0 où DataGridView ne réinitialise plus les polices de style de cellule par défaut de façon à ce qu’elles correspondent à la police ambiante si la police de style de cellule a été personnalisée.
ms.date: 10/18/2020
ms.openlocfilehash: 708b12ba1305681f5c38eb605861d02e3b2c8eb1
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95761307"
---
# <a name="datagridview-no-longer-resets-fonts-for-customized-cell-styles"></a><span data-ttu-id="708d4-103">DataGridView ne réinitialise plus les polices pour les styles de cellule personnalisés</span><span class="sxs-lookup"><span data-stu-id="708d4-103">DataGridView no longer resets fonts for customized cell styles</span></span>

<span data-ttu-id="708d4-104">Lorsque la police ambiante change, <xref:System.Windows.Forms.DataGridViewElement.DataGridView> ne réinitialise plus les polices de style de cellule par défaut pour qu’elles correspondent à la police ambiante si la police de style de cellule a été personnalisée.</span><span class="sxs-lookup"><span data-stu-id="708d4-104">When the ambient font changes, <xref:System.Windows.Forms.DataGridViewElement.DataGridView> no longer resets default cell style fonts to match the ambient font if the cell style font has been customized.</span></span>

## <a name="change-description"></a><span data-ttu-id="708d4-105">Description de la modification</span><span class="sxs-lookup"><span data-stu-id="708d4-105">Change description</span></span>

<span data-ttu-id="708d4-106">Dans les versions précédentes de .NET, si la police ambiante change, <xref:System.Windows.Forms.DataGridViewElement.DataGridView> réinitialise et substitue les polices définies par l’utilisateur dans les <xref:System.Windows.Forms.DataGridView.DefaultCellStyle> <xref:System.Windows.Forms.DataGridView.ColumnHeadersDefaultCellStyle> Propriétés, et <xref:System.Windows.Forms.DataGridView.RowHeadersDefaultCellStyle> .</span><span class="sxs-lookup"><span data-stu-id="708d4-106">In previous .NET versions, if the ambient font changes, <xref:System.Windows.Forms.DataGridViewElement.DataGridView> resets and overrides user-defined fonts in the <xref:System.Windows.Forms.DataGridView.DefaultCellStyle>, <xref:System.Windows.Forms.DataGridView.ColumnHeadersDefaultCellStyle>, and <xref:System.Windows.Forms.DataGridView.RowHeadersDefaultCellStyle> properties.</span></span>

<span data-ttu-id="708d4-107">À compter de .NET 5,0, si vous configurez des paramètres de police dans les <xref:System.Windows.Forms.DataGridView.DefaultCellStyle> <xref:System.Windows.Forms.DataGridView.ColumnHeadersDefaultCellStyle> Propriétés, ou <xref:System.Windows.Forms.DataGridView.RowHeadersDefaultCellStyle> , ces paramètres sont conservés même lorsque la police ambiante change.</span><span class="sxs-lookup"><span data-stu-id="708d4-107">Starting in .NET 5.0, if you configure font settings in the <xref:System.Windows.Forms.DataGridView.DefaultCellStyle>, <xref:System.Windows.Forms.DataGridView.ColumnHeadersDefaultCellStyle>, or <xref:System.Windows.Forms.DataGridView.RowHeadersDefaultCellStyle> properties, those settings are retained even when the ambient font changes.</span></span> <span data-ttu-id="708d4-108">Pour l’une de ces propriétés, vous ne personnalisez pas la police, la police est modifiée pour correspondre aux paramètres de police ambiante.</span><span class="sxs-lookup"><span data-stu-id="708d4-108">For any of these properties that you don't customize the font, the font will change to match the ambient font settings.</span></span>

## <a name="reason-for-change"></a><span data-ttu-id="708d4-109">Motif de modification</span><span class="sxs-lookup"><span data-stu-id="708d4-109">Reason for change</span></span>

<span data-ttu-id="708d4-110">Avec la [modification de la police par défaut dans .net Core 3,0](../../winforms.md#default-control-font-changed-to-segoe-ui-9-pt), les paramètres de police par défaut pour les divers styles de cellule ont également changé.</span><span class="sxs-lookup"><span data-stu-id="708d4-110">With the [change of the default font in .NET Core 3.0](../../winforms.md#default-control-font-changed-to-segoe-ui-9-pt), the default font settings for the various cell styles also changed.</span></span> <span data-ttu-id="708d4-111">Ce comportement n’est pas souhaitable pour les applications qui reposent sur des styles personnalisés dans leurs <xref:System.Windows.Forms.DataGridViewElement.DataGridView> contrôles et qui empêchent la migration de ces applications de .NET Framework vers .net 5,0.</span><span class="sxs-lookup"><span data-stu-id="708d4-111">This behavior is undesirable for apps that rely on custom styling in their <xref:System.Windows.Forms.DataGridViewElement.DataGridView> controls, and impeded the migration of these apps from .NET Framework to .NET 5.0.</span></span>

## <a name="version-introduced"></a><span data-ttu-id="708d4-112">Version introduite</span><span class="sxs-lookup"><span data-stu-id="708d4-112">Version introduced</span></span>

<span data-ttu-id="708d4-113">.NET 5,0</span><span class="sxs-lookup"><span data-stu-id="708d4-113">.NET 5.0</span></span>

## <a name="recommended-action"></a><span data-ttu-id="708d4-114">Action recommandée</span><span class="sxs-lookup"><span data-stu-id="708d4-114">Recommended action</span></span>

<span data-ttu-id="708d4-115">Aucune action n’est requise de votre part.</span><span class="sxs-lookup"><span data-stu-id="708d4-115">No action is required on your part.</span></span> <span data-ttu-id="708d4-116">Toutefois, si vous avez personnalisé la police dans les <xref:System.Windows.Forms.DataGridView.DefaultCellStyle> <xref:System.Windows.Forms.DataGridView.ColumnHeadersDefaultCellStyle> Propriétés, ou <xref:System.Windows.Forms.DataGridView.RowHeadersDefaultCellStyle> et que vous souhaitez que la police corresponde à la police ambiante, affectez la valeur <xref:System.Windows.Forms.DataGridViewCellStyle.Font?displayProperty=nameWithType> à `null` pour chaque propriété.</span><span class="sxs-lookup"><span data-stu-id="708d4-116">However, if you've customized the font in the <xref:System.Windows.Forms.DataGridView.DefaultCellStyle>, <xref:System.Windows.Forms.DataGridView.ColumnHeadersDefaultCellStyle>, or <xref:System.Windows.Forms.DataGridView.RowHeadersDefaultCellStyle> properties and want the font to match the ambient font, set <xref:System.Windows.Forms.DataGridViewCellStyle.Font?displayProperty=nameWithType> to `null` for each property.</span></span>

## <a name="affected-apis"></a><span data-ttu-id="708d4-117">API affectées</span><span class="sxs-lookup"><span data-stu-id="708d4-117">Affected APIs</span></span>

- <xref:System.Windows.Forms.DataGridView.DefaultCellStyle?displayProperty=fullName>
- <xref:System.Windows.Forms.DataGridView.ColumnHeadersDefaultCellStyle?displayProperty=fullName>
- <xref:System.Windows.Forms.DataGridView.RowHeadersDefaultCellStyle?displayProperty=fullName>

<!--

### Affected APIs

- `P:System.Windows.Forms.DataGridView.DefaultCellStyle`
- `P:System.Windows.Forms.DataGridView.ColumnHeadersDefaultCellStyle`
- `P:System.Windows.Forms.DataGridView.RowHeadersDefaultCellStyle`

### Category

- Windows Forms

-->
