---
title: 'Modification avec rupture : les propriétés WinForms lèvent désormais ArgumentOutOfRangeException'
description: En savoir plus sur la modification avec rupture dans .NET 5,0 où certaines propriétés de Windows Forms lèvent désormais une exception ArgumentOutOfRangeException pour les arguments non valides.
ms.date: 06/18/2020
ms.openlocfilehash: 94593047d16304ce401b23993ad4ca173c10812b
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95761111"
---
# <a name="winforms-properties-now-throw-argumentoutofrangeexception"></a>Les propriétés WinForms lèvent désormais ArgumentOutOfRangeException

Certaines propriétés de Windows Forms lèvent désormais une exception <xref:System.ArgumentOutOfRangeException> pour les arguments non valides, dans le cas contraire.

## <a name="change-description"></a>Description de la modification

Auparavant, ces propriétés relevaient d’autres exceptions, telles que <xref:System.NullReferenceException> , <xref:System.IndexOutOfRangeException> ou <xref:System.ArgumentException> , en cas de réussite des arguments hors limites. À compter de .NET 5,0, ces propriétés lèvent désormais une exception <xref:System.ArgumentOutOfRangeException> quand les arguments passés sont en dehors de la plage.

La levée d’une <xref:System.ArgumentOutOfRangeException> conforme au comportement du Runtime .net. Il améliore également l’expérience de débogage en communiquant clairement l’argument qui n’est pas valide.

## <a name="version-introduced"></a>Version introduite

.NET 5,0

## <a name="recommended-action"></a>Action recommandée

- Mettez à jour le code pour empêcher le passage d’arguments non valides.
- Si nécessaire, gérez une <xref:System.ArgumentOutOfRangeException> lors de la définition de la propriété.

## <a name="affected-apis"></a>API affectées

Le tableau suivant répertorie les propriétés et les paramètres affectés :

> [!div class="mx-tdBreakAll"]
> | Propriété | Nom du paramètre | Version ajoutée |
> |-|-|-|
> | <xref:System.Windows.Forms.ListBox.IntegerCollection.Item(System.Int32)?displayProperty=nameWithType> | `index` | 5,0 Preview 5 |
> | <xref:System.Windows.Forms.TreeNode.ImageIndex?displayProperty=nameWithType> | `value` | 5,0 Preview 6 |
> | <xref:System.Windows.Forms.TreeNode.SelectedImageIndex?displayProperty=nameWithType> | `value` | 5,0 Preview 6 |

<!--

### Affected APIs

- `P:System.Windows.Forms.ListBox.IntegerCollection.Item(System.Int32)`
- `P:System.Windows.Forms.TreeNode.ImageIndex`
- `P:System.Windows.Forms.TreeNode.SelectedImageIndex`

### Category

Windows Forms

-->
