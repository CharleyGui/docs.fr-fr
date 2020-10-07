---
ms.openlocfilehash: 9c84c9f844a2a7efb9633c11634b069ef6b6033b
ms.sourcegitcommit: 636af37170ae75a11c4f7d1ecd770820e7dfe7bd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/07/2020
ms.locfileid: "91804858"
---
### <a name="datagridview-no-longer-resets-fonts-for-customized-cell-styles"></a>DataGridView ne réinitialise plus les polices pour les styles de cellule personnalisés

Lorsque la police ambiante change, <xref:System.Windows.Forms.DataGridViewElement.DataGridView> ne réinitialise plus les polices de style de cellule par défaut pour qu’elles correspondent à la police ambiante si la police de style de cellule a été personnalisée.

#### <a name="change-description"></a>Description de la modification

Dans les versions précédentes de .NET, si la police ambiante change, <xref:System.Windows.Forms.DataGridViewElement.DataGridView> réinitialise et substitue les polices définies par l’utilisateur dans les <xref:System.Windows.Forms.DataGridView.DefaultCellStyle> <xref:System.Windows.Forms.DataGridView.ColumnHeadersDefaultCellStyle> Propriétés, et <xref:System.Windows.Forms.DataGridView.RowHeadersDefaultCellStyle> .

À compter de .NET 5,0, si vous configurez des paramètres de police dans les <xref:System.Windows.Forms.DataGridView.DefaultCellStyle> <xref:System.Windows.Forms.DataGridView.ColumnHeadersDefaultCellStyle> Propriétés, ou <xref:System.Windows.Forms.DataGridView.RowHeadersDefaultCellStyle> , ces paramètres sont conservés même lorsque la police ambiante change. Pour l’une de ces propriétés, vous ne personnalisez pas la police, la police est modifiée pour correspondre aux paramètres de police ambiante.

#### <a name="reason-for-change"></a>Motif de modification

Avec la [modification de la police par défaut dans .net Core 3,0](../../../../docs/core/compatibility/winforms.md#default-control-font-changed-to-segoe-ui-9-pt), les paramètres de police par défaut pour les divers styles de cellule ont également changé. Ce comportement n’est pas souhaitable pour les applications qui reposent sur des styles personnalisés dans leurs <xref:System.Windows.Forms.DataGridViewElement.DataGridView> contrôles et qui empêchent la migration de ces applications de .NET Framework vers .net 5,0.

#### <a name="version-introduced"></a>Version introduite

.NET 5,0 RC2

#### <a name="recommended-action"></a>Action recommandée

Aucune action n’est requise de votre part. Toutefois, si vous avez personnalisé la police dans les <xref:System.Windows.Forms.DataGridView.DefaultCellStyle> <xref:System.Windows.Forms.DataGridView.ColumnHeadersDefaultCellStyle> Propriétés, ou <xref:System.Windows.Forms.DataGridView.RowHeadersDefaultCellStyle> et que vous souhaitez que la police corresponde à la police ambiante, affectez la valeur <xref:System.Windows.Forms.DataGridViewCellStyle.Font?displayProperty=nameWithType> à `null` pour chaque propriété.

#### <a name="category"></a>Category

- Windows Forms

#### <a name="affected-apis"></a>API affectées

- <xref:System.Windows.Forms.DataGridView.DefaultCellStyle?displayProperty=fullName>
- <xref:System.Windows.Forms.DataGridView.ColumnHeadersDefaultCellStyle?displayProperty=fullName>
- <xref:System.Windows.Forms.DataGridView.RowHeadersDefaultCellStyle?displayProperty=fullName>

<!--

#### Affected APIs

- `P:System.Windows.Forms.DataGridView.DefaultCellStyle`
- `P:System.Windows.Forms.DataGridView.ColumnHeadersDefaultCellStyle`
- `P:System.Windows.Forms.DataGridView.RowHeadersDefaultCellStyle`

-->
