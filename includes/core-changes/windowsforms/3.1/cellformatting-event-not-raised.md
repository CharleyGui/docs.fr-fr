---
ms.openlocfilehash: add3ff8faed2e7fab245e5b6f1b9158b7bdd06f5
ms.sourcegitcommit: 79a2d6a07ba4ed08979819666a0ee6927bbf1b01
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2019
ms.locfileid: "74567371"
---
### <a name="cellformatting-event-not-raised-if-tooltip-is-shown"></a>Événement CellFormatting non déclenché si l’info-bulle est affichée

Une <xref:System.Windows.Forms.DataGridView> affiche maintenant le texte et les info-bulles d’erreur d’une cellule lorsque vous survolez par une souris et lorsqu’elle est sélectionnée via le clavier. Si une info-bulle est affichée, l’événement <xref:System.Windows.Forms.DataGridView.CellFormatting?displayProperty=nameWithType> n’est pas déclenché.

#### <a name="change-description"></a>Modifier la description

Avant .NET Core 3,1, un <xref:System.Windows.Forms.DataGridView> dont la propriété <xref:System.Windows.Forms.DataGridView.ShowCellToolTips%2A> a la valeur `true` affichait une info-bulle pour le texte d’une cellule et des erreurs quand la cellule était pointée par une souris. Les info-bulles n’étaient pas affichées lorsqu’une cellule a été sélectionnée à l’aide du clavier (par exemple, en utilisant la touche Tab, les touches de raccourci ou la navigation vers la flèche). Si l’utilisateur a modifié une cellule, puis que le <xref:System.Windows.Forms.DataGridView> était toujours en mode édition, pointé sur une cellule pour laquelle la propriété <xref:System.Windows.Forms.DataGridViewCell.ToolTipText> n’a pas été définie, un événement <xref:System.Windows.Forms.DataGridView.CellFormatting> a été déclenché pour mettre en forme le texte de la cellule en vue de son affichage dans la cellule.

Pour répondre aux normes d’accessibilité, à compter de .NET Core 3,1, un <xref:System.Windows.Forms.DataGridView> dont la propriété <xref:System.Windows.Forms.DataGridView.ShowCellToolTips%2A> a la valeur `true` affiche des info-bulles pour le texte d’une cellule et des erreurs non seulement lorsque la cellule est pointée, mais également quand elle est sélectionnée via le clavier. En raison de cette modification, l’événement <xref:System.Windows.Forms.DataGridView.CellFormatting> n’est *pas* déclenché lorsque les cellules qui n’ont pas la propriété <xref:System.Windows.Forms.DataGridViewCell.ToolTipText> définie sont pointées pendant que le <xref:System.Windows.Forms.DataGridView> est en mode édition. L’événement n’est pas déclenché, car le contenu de la cellule survolée est affiché sous la forme d’une info-bulle au lieu d’être affiché dans la cellule.

#### <a name="version-introduced"></a>Version introduite

3,1

#### <a name="recommended-action"></a>Action recommandée

Refactorisez tout code qui dépend de l’événement <xref:System.Windows.Forms.DataGridView.CellFormatting> lorsque le <xref:System.Windows.Forms.DataGridView> est en mode édition.

#### <a name="category"></a>Category

Windows Forms

#### <a name="affected-apis"></a>API affectées

Non détectable via l’analyse des API.

<!-- 

### Affected APIs

- Not detectable via API analysis.

-->
