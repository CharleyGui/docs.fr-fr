---
ms.openlocfilehash: b736ab743a628fdcbc53c5ee51551e5dad986885
ms.sourcegitcommit: 2b3b2d684259463ddfc76ad680e5e09fdc1984d2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/08/2020
ms.locfileid: "80888115"
---
### <a name="cellformatting-event-not-raised-if-tooltip-is-shown"></a>Événement CellFormatting non déclenché si l’info-bulle est affichée

Un <xref:System.Windows.Forms.DataGridView> affiche maintenant le texte et les info-bulles d’erreur d’une cellule lorsqu’elle est survolée par une souris et lorsqu’elle est sélectionnée via le clavier. Si une info-bulle est affichée <xref:System.Windows.Forms.DataGridView.CellFormatting?displayProperty=nameWithType> , l’événement n’est pas déclenché.

#### <a name="change-description"></a>Description de la modification

Avant .NET Core 3,1, <xref:System.Windows.Forms.DataGridView> dont la <xref:System.Windows.Forms.DataGridView.ShowCellToolTips%2A> propriété a été définie pour `true` montrer une info-bulle pour le texte d’une cellule et des erreurs quand la cellule a été pointée par une souris. Les info-bulles n’étaient pas affichées lorsqu’une cellule a été sélectionnée à l’aide du clavier (par exemple, en utilisant la touche Tab, les touches de raccourci ou la navigation vers la flèche). Si l’utilisateur a modifié une cellule, puis que le <xref:System.Windows.Forms.DataGridView> était toujours en mode édition, pointé sur une cellule pour laquelle la <xref:System.Windows.Forms.DataGridViewCell.ToolTipText> propriété n’a pas été définie, un <xref:System.Windows.Forms.DataGridView.CellFormatting> événement a été déclenché pour mettre en forme le texte de la cellule en vue de son affichage dans la cellule.

Pour répondre aux normes d’accessibilité, à compter de .NET Core <xref:System.Windows.Forms.DataGridView> 3,1, dont <xref:System.Windows.Forms.DataGridView.ShowCellToolTips%2A> la propriété a `true` la valeur affiche des info-bulles pour le texte d’une cellule et des erreurs non seulement lorsque la cellule est survolée, mais également quand elle est sélectionnée via le clavier. En raison de cette <xref:System.Windows.Forms.DataGridView.CellFormatting> modification, l’événement n’est *pas* déclenché lorsque des cellules qui n’ont <xref:System.Windows.Forms.DataGridViewCell.ToolTipText> pas la propriété définie sont pointées <xref:System.Windows.Forms.DataGridView> pendant que le est en mode édition. L’événement n’est pas déclenché, car le contenu de la cellule survolée est affiché sous la forme d’une info-bulle au lieu d’être affiché dans la cellule.

#### <a name="version-introduced"></a>Version introduite

3.1

#### <a name="recommended-action"></a>Action recommandée

Refactorisez tout code qui dépend de l' <xref:System.Windows.Forms.DataGridView.CellFormatting> événement lorsque <xref:System.Windows.Forms.DataGridView> est en mode édition.

#### <a name="category"></a>Category

Windows Forms

#### <a name="affected-apis"></a>API affectées

Aucun

<!-- 

### Affected APIs

Not detectable via API analysis.

-->
