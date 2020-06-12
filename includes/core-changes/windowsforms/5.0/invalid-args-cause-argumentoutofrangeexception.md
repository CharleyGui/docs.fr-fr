---
ms.openlocfilehash: f42da00487735acdcc60f876c75e1dfd17103008
ms.sourcegitcommit: 1cbd77da54405ea7dba343ac0334fb03237d25d2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/11/2020
ms.locfileid: "84702436"
---
### <a name="winforms-properties-now-throw-argumentoutofrangeexception"></a>Les propriétés WinForms lèvent désormais ArgumentOutOfRangeException

Certaines propriétés de Windows Forms lèvent désormais une exception <xref:System.ArgumentOutOfRangeException> pour les arguments non valides, dans le cas contraire.

#### <a name="change-description"></a>Description de la modification

Auparavant, ces propriétés relevaient d’autres exceptions, telles que <xref:System.NullReferenceException> , <xref:System.IndexOutOfRangeException> ou <xref:System.ArgumentException> , en cas de réussite des arguments hors limites. À compter de .NET 5,0, ces propriétés lèvent désormais une exception <xref:System.ArgumentOutOfRangeException> quand les arguments passés sont en dehors de la plage.

La levée d’une <xref:System.ArgumentOutOfRangeException> conforme au comportement du Runtime .net. Il améliore également l’expérience de débogage en communiquant clairement l’argument qui n’est pas valide.

#### <a name="version-introduced"></a>Version introduite

.NET 5,0

#### <a name="recommended-action"></a>Action recommandée

- Mettez à jour le code pour empêcher le passage d’arguments non valides.
- Si nécessaire, gérez une <xref:System.ArgumentOutOfRangeException> lors de la définition de la propriété.

#### <a name="category"></a>Category

Windows Forms

#### <a name="affected-apis"></a>API affectées

Le tableau suivant répertorie les propriétés et les paramètres affectés :

> [!div class="mx-tdBreakAll"]
> | Propriété | Nom du paramètre | Version ajoutée |
> |-|-|-|
> | <xref:System.Windows.Forms.ListBox.IntegerCollection.Item(System.Int32)?displayProperty=nameWithType> | `index` | 5,0 Preview 5 |
> | <xref:System.Windows.Forms.TreeNode.ImageIndex?displayProperty=nameWithType> | `value` | 5,0 Preview 6 |
> | <xref:System.Windows.Forms.TreeNode.SelectedImageIndex?displayProperty=nameWithType> | `value` | 5,0 Preview 6 |

<!-- 

#### Affected APIs

- `P:System.Windows.Forms.ListBox.IntegerCollection.Item(System.Int32)`
- `P:System.Windows.Forms.TreeNode.ImageIndex`
- `P:System.Windows.Forms.TreeNode.SelectedImageIndex`

-->
