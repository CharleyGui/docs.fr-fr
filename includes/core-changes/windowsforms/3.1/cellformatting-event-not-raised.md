---
ms.openlocfilehash: add3ff8faed2e7fab245e5b6f1b9158b7bdd06f5
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "74567371"
---
### <a name="cellformatting-event-not-raised-if-tooltip-is-shown"></a>CellFormatting événement non soulevé si tooltip est montré

A <xref:System.Windows.Forms.DataGridView> affiche maintenant les outils texte et erreur d’une cellule lorsqu’il est plané par une souris et lorsqu’il est sélectionné via le clavier. Si un tooltip est <xref:System.Windows.Forms.DataGridView.CellFormatting?displayProperty=nameWithType> montré, l’événement n’est pas soulevé.

#### <a name="change-description"></a>Description de la modification

Avant .NET Core 3.1, <xref:System.Windows.Forms.DataGridView> un <xref:System.Windows.Forms.DataGridView.ShowCellToolTips%2A> qui `true` avait la propriété réglée pour montrer une pointe d’outils pour le texte d’une cellule et les erreurs lorsque la cellule a été planée par une souris. Les outils n’ont pas été montrés lorsqu’une cellule a été sélectionnée via le clavier (par exemple, en utilisant la clé Tab, les touches de raccourci ou la navigation fléchée). Si l’utilisateur a édité une <xref:System.Windows.Forms.DataGridView> cellule, puis, alors que le était encore <xref:System.Windows.Forms.DataGridViewCell.ToolTipText> en mode <xref:System.Windows.Forms.DataGridView.CellFormatting> d’édition, planait au-dessus d’une cellule qui n’avait pas l’ensemble de propriété, un événement a été soulevé pour formater le texte de la cellule pour l’affichage dans la cellule.

Pour répondre aux normes d’accessibilité, à partir <xref:System.Windows.Forms.DataGridView> de .NET Core 3.1, un qui a la <xref:System.Windows.Forms.DataGridView.ShowCellToolTips%2A> propriété définie pour `true` afficher les outils pour le texte d’une cellule et les erreurs non seulement lorsque la cellule est planée, mais aussi quand il est sélectionné via le clavier. En conséquence de ce <xref:System.Windows.Forms.DataGridView.CellFormatting> changement, l’événement *n’est* pas <xref:System.Windows.Forms.DataGridViewCell.ToolTipText> soulevé lorsque les <xref:System.Windows.Forms.DataGridView> cellules qui n’ont pas l’ensemble de propriété sont planées pendant que le est en mode d’édition. L’événement n’est pas soulevé parce que le contenu de la cellule planée est montré comme un tooltip au lieu d’être affiché dans la cellule.

#### <a name="version-introduced"></a>Version introduite

3.1

#### <a name="recommended-action"></a>Action recommandée

Refactor tout code qui <xref:System.Windows.Forms.DataGridView.CellFormatting> dépend <xref:System.Windows.Forms.DataGridView> de l’événement pendant que le mode d’édition est en mode d’édition.

#### <a name="category"></a>Category

Windows Forms

#### <a name="affected-apis"></a>API affectées

Non détectable par l’analyse de l’API.

<!-- 

### Affected APIs

- Not detectable via API analysis.

-->
