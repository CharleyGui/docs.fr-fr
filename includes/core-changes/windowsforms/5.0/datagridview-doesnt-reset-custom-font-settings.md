---
ms.openlocfilehash: 9c84c9f844a2a7efb9633c11634b069ef6b6033b
ms.sourcegitcommit: 636af37170ae75a11c4f7d1ecd770820e7dfe7bd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/07/2020
ms.locfileid: "91804858"
---
### <a name="datagridview-no-longer-resets-fonts-for-customized-cell-styles"></a><span data-ttu-id="def4b-101">DataGridView ne réinitialise plus les polices pour les styles de cellule personnalisés</span><span class="sxs-lookup"><span data-stu-id="def4b-101">DataGridView no longer resets fonts for customized cell styles</span></span>

<span data-ttu-id="def4b-102">Lorsque la police ambiante change, <xref:System.Windows.Forms.DataGridViewElement.DataGridView> ne réinitialise plus les polices de style de cellule par défaut pour qu’elles correspondent à la police ambiante si la police de style de cellule a été personnalisée.</span><span class="sxs-lookup"><span data-stu-id="def4b-102">When the ambient font changes, <xref:System.Windows.Forms.DataGridViewElement.DataGridView> no longer resets default cell style fonts to match the ambient font if the cell style font has been customized.</span></span>

#### <a name="change-description"></a><span data-ttu-id="def4b-103">Description de la modification</span><span class="sxs-lookup"><span data-stu-id="def4b-103">Change description</span></span>

<span data-ttu-id="def4b-104">Dans les versions précédentes de .NET, si la police ambiante change, <xref:System.Windows.Forms.DataGridViewElement.DataGridView> réinitialise et substitue les polices définies par l’utilisateur dans les <xref:System.Windows.Forms.DataGridView.DefaultCellStyle> <xref:System.Windows.Forms.DataGridView.ColumnHeadersDefaultCellStyle> Propriétés, et <xref:System.Windows.Forms.DataGridView.RowHeadersDefaultCellStyle> .</span><span class="sxs-lookup"><span data-stu-id="def4b-104">In previous .NET versions, if the ambient font changes, <xref:System.Windows.Forms.DataGridViewElement.DataGridView> resets and overrides user-defined fonts in the <xref:System.Windows.Forms.DataGridView.DefaultCellStyle>, <xref:System.Windows.Forms.DataGridView.ColumnHeadersDefaultCellStyle>, and <xref:System.Windows.Forms.DataGridView.RowHeadersDefaultCellStyle> properties.</span></span>

<span data-ttu-id="def4b-105">À compter de .NET 5,0, si vous configurez des paramètres de police dans les <xref:System.Windows.Forms.DataGridView.DefaultCellStyle> <xref:System.Windows.Forms.DataGridView.ColumnHeadersDefaultCellStyle> Propriétés, ou <xref:System.Windows.Forms.DataGridView.RowHeadersDefaultCellStyle> , ces paramètres sont conservés même lorsque la police ambiante change.</span><span class="sxs-lookup"><span data-stu-id="def4b-105">Starting in .NET 5.0, if you configure font settings in the <xref:System.Windows.Forms.DataGridView.DefaultCellStyle>, <xref:System.Windows.Forms.DataGridView.ColumnHeadersDefaultCellStyle>, or <xref:System.Windows.Forms.DataGridView.RowHeadersDefaultCellStyle> properties, those settings are retained even when the ambient font changes.</span></span> <span data-ttu-id="def4b-106">Pour l’une de ces propriétés, vous ne personnalisez pas la police, la police est modifiée pour correspondre aux paramètres de police ambiante.</span><span class="sxs-lookup"><span data-stu-id="def4b-106">For any of these properties that you don't customize the font, the font will change to match the ambient font settings.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="def4b-107">Motif de modification</span><span class="sxs-lookup"><span data-stu-id="def4b-107">Reason for change</span></span>

<span data-ttu-id="def4b-108">Avec la [modification de la police par défaut dans .net Core 3,0](../../../../docs/core/compatibility/winforms.md#default-control-font-changed-to-segoe-ui-9-pt), les paramètres de police par défaut pour les divers styles de cellule ont également changé.</span><span class="sxs-lookup"><span data-stu-id="def4b-108">With the [change of the default font in .NET Core 3.0](../../../../docs/core/compatibility/winforms.md#default-control-font-changed-to-segoe-ui-9-pt), the default font settings for the various cell styles also changed.</span></span> <span data-ttu-id="def4b-109">Ce comportement n’est pas souhaitable pour les applications qui reposent sur des styles personnalisés dans leurs <xref:System.Windows.Forms.DataGridViewElement.DataGridView> contrôles et qui empêchent la migration de ces applications de .NET Framework vers .net 5,0.</span><span class="sxs-lookup"><span data-stu-id="def4b-109">This behavior is undesirable for apps that rely on custom styling in their <xref:System.Windows.Forms.DataGridViewElement.DataGridView> controls, and impeded the migration of these apps from .NET Framework to .NET 5.0.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="def4b-110">Version introduite</span><span class="sxs-lookup"><span data-stu-id="def4b-110">Version introduced</span></span>

<span data-ttu-id="def4b-111">.NET 5,0 RC2</span><span class="sxs-lookup"><span data-stu-id="def4b-111">.NET 5.0 RC2</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="def4b-112">Action recommandée</span><span class="sxs-lookup"><span data-stu-id="def4b-112">Recommended action</span></span>

<span data-ttu-id="def4b-113">Aucune action n’est requise de votre part.</span><span class="sxs-lookup"><span data-stu-id="def4b-113">No action is required on your part.</span></span> <span data-ttu-id="def4b-114">Toutefois, si vous avez personnalisé la police dans les <xref:System.Windows.Forms.DataGridView.DefaultCellStyle> <xref:System.Windows.Forms.DataGridView.ColumnHeadersDefaultCellStyle> Propriétés, ou <xref:System.Windows.Forms.DataGridView.RowHeadersDefaultCellStyle> et que vous souhaitez que la police corresponde à la police ambiante, affectez la valeur <xref:System.Windows.Forms.DataGridViewCellStyle.Font?displayProperty=nameWithType> à `null` pour chaque propriété.</span><span class="sxs-lookup"><span data-stu-id="def4b-114">However, if you've customized the font in the <xref:System.Windows.Forms.DataGridView.DefaultCellStyle>, <xref:System.Windows.Forms.DataGridView.ColumnHeadersDefaultCellStyle>, or <xref:System.Windows.Forms.DataGridView.RowHeadersDefaultCellStyle> properties and want the font to match the ambient font, set <xref:System.Windows.Forms.DataGridViewCellStyle.Font?displayProperty=nameWithType> to `null` for each property.</span></span>

#### <a name="category"></a><span data-ttu-id="def4b-115">Category</span><span class="sxs-lookup"><span data-stu-id="def4b-115">Category</span></span>

- <span data-ttu-id="def4b-116">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="def4b-116">Windows Forms</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="def4b-117">API affectées</span><span class="sxs-lookup"><span data-stu-id="def4b-117">Affected APIs</span></span>

- <xref:System.Windows.Forms.DataGridView.DefaultCellStyle?displayProperty=fullName>
- <xref:System.Windows.Forms.DataGridView.ColumnHeadersDefaultCellStyle?displayProperty=fullName>
- <xref:System.Windows.Forms.DataGridView.RowHeadersDefaultCellStyle?displayProperty=fullName>

<!--

#### Affected APIs

- `P:System.Windows.Forms.DataGridView.DefaultCellStyle`
- `P:System.Windows.Forms.DataGridView.ColumnHeadersDefaultCellStyle`
- `P:System.Windows.Forms.DataGridView.RowHeadersDefaultCellStyle`

-->
