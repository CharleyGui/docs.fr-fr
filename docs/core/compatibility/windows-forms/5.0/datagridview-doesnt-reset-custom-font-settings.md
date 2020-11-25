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
# <a name="datagridview-no-longer-resets-fonts-for-customized-cell-styles"></a>DataGridView ne réinitialise plus les polices pour les styles de cellule personnalisés

Lorsque la police ambiante change, <xref:System.Windows.Forms.DataGridViewElement.DataGridView> ne réinitialise plus les polices de style de cellule par défaut pour qu’elles correspondent à la police ambiante si la police de style de cellule a été personnalisée.

## <a name="change-description"></a>Description de la modification

Dans les versions précédentes de .NET, si la police ambiante change, <xref:System.Windows.Forms.DataGridViewElement.DataGridView> réinitialise et substitue les polices définies par l’utilisateur dans les <xref:System.Windows.Forms.DataGridView.DefaultCellStyle> <xref:System.Windows.Forms.DataGridView.ColumnHeadersDefaultCellStyle> Propriétés, et <xref:System.Windows.Forms.DataGridView.RowHeadersDefaultCellStyle> .

À compter de .NET 5,0, si vous configurez des paramètres de police dans les <xref:System.Windows.Forms.DataGridView.DefaultCellStyle> <xref:System.Windows.Forms.DataGridView.ColumnHeadersDefaultCellStyle> Propriétés, ou <xref:System.Windows.Forms.DataGridView.RowHeadersDefaultCellStyle> , ces paramètres sont conservés même lorsque la police ambiante change. Pour l’une de ces propriétés, vous ne personnalisez pas la police, la police est modifiée pour correspondre aux paramètres de police ambiante.

## <a name="reason-for-change"></a>Motif de modification

Avec la [modification de la police par défaut dans .net Core 3,0](../../winforms.md#default-control-font-changed-to-segoe-ui-9-pt), les paramètres de police par défaut pour les divers styles de cellule ont également changé. Ce comportement n’est pas souhaitable pour les applications qui reposent sur des styles personnalisés dans leurs <xref:System.Windows.Forms.DataGridViewElement.DataGridView> contrôles et qui empêchent la migration de ces applications de .NET Framework vers .net 5,0.

## <a name="version-introduced"></a>Version introduite

.NET 5,0

## <a name="recommended-action"></a>Action recommandée

Aucune action n’est requise de votre part. Toutefois, si vous avez personnalisé la police dans les <xref:System.Windows.Forms.DataGridView.DefaultCellStyle> <xref:System.Windows.Forms.DataGridView.ColumnHeadersDefaultCellStyle> Propriétés, ou <xref:System.Windows.Forms.DataGridView.RowHeadersDefaultCellStyle> et que vous souhaitez que la police corresponde à la police ambiante, affectez la valeur <xref:System.Windows.Forms.DataGridViewCellStyle.Font?displayProperty=nameWithType> à `null` pour chaque propriété.

## <a name="affected-apis"></a>API affectées

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
