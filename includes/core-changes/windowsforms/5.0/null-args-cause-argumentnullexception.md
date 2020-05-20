---
ms.openlocfilehash: ab8d801f3cdcfbeb6de20146754b26e3713d7dd6
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/20/2020
ms.locfileid: "83702455"
---
### <a name="winforms-methods-now-throw-argumentnullexception"></a>Les méthodes WinForms lèvent désormais ArgumentNullException

Certaines méthodes Windows Forms lèvent désormais un <xref:System.ArgumentNullException> pour les arguments null, où ils ont précédemment levé un <xref:System.NullReferenceException> .

#### <a name="change-description"></a>Description de la modification

Jusqu’à présent, certaines méthodes Windows Forms <xref:System.NullReferenceException> ont levé une si passé un argument qui avait la valeur null. À compter de .NET 5,0, ces méthodes lèvent désormais une exception <xref:System.ArgumentNullException> pour les arguments null.

La levée d’une <xref:System.ArgumentNullException> conforme au comportement du Runtime .net. Il améliore également l’expérience de débogage en communiquant clairement qu’un argument est null et son argument.

#### <a name="version-introduced"></a>Version introduite

.NET 5,0 Preview 1 \
.NET 5,0 Preview 2

#### <a name="recommended-action"></a>Action recommandée

Si vous appelez l’une de ces méthodes et que votre code intercepte actuellement un <xref:System.NullReferenceException> pour les arguments null, interceptez à la <xref:System.ArgumentNullException> place. En outre, envisagez de mettre à jour le code afin d’éviter de passer des arguments null aux méthodes listées.

#### <a name="category"></a>Category

Windows Forms

#### <a name="affected-apis"></a>API affectées

À compter de .NET 5,0 Preview 1 :

- <xref:System.Windows.Forms.Control.ControlCollection.%23ctor(System.Windows.Forms.Control)>
- <xref:System.Windows.Forms.TabControl.GetToolTipText(System.Object)?displayProperty=nameWithType>
- <xref:System.Windows.Forms.TableLayoutControlCollection.%23ctor(System.Windows.Forms.TableLayoutPanel)>
- <xref:System.Windows.Forms.ToolStripRenderer.OnRenderArrow(System.Windows.Forms.ToolStripArrowRenderEventArgs)?displayProperty=nameWithType>
- <xref:System.Windows.Forms.ToolStripRenderer.OnRenderItemImage(System.Windows.Forms.ToolStripItemImageRenderEventArgs)?displayProperty=nameWithType>
- <xref:System.Windows.Forms.ToolStripRenderer.OnRenderItemCheck(System.Windows.Forms.ToolStripItemImageRenderEventArgs)?displayProperty=nameWithType>
- <xref:System.Windows.Forms.ToolStripRenderer.OnRenderItemText(System.Windows.Forms.ToolStripItemTextRenderEventArgs)?displayProperty=nameWithType>
- <xref:System.Windows.Forms.ToolStripRenderer.OnRenderStatusStripSizingGrip(System.Windows.Forms.ToolStripRenderEventArgs)?displayProperty=nameWithType>

À compter de .NET 5,0 Preview 2 :

- <xref:System.Windows.Forms.DataGridViewComboBoxEditingControl.ApplyCellStyleToEditingControl(System.Windows.Forms.DataGridViewCellStyle)?displayProperty=nameWithType>
- <xref:System.Windows.Forms.RichTextBox.LoadFile(System.IO.Stream,System.Windows.Forms.RichTextBoxStreamType)?displayProperty=nameWithType>(pour le <xref:System.IO.Stream> paramètre uniquement)

<!-- 

#### Affected APIs

- `M:System.Windows.Forms.Control.ControlCollection.#ctor(System.Windows.Forms.Control)`
- `M:System.Windows.Forms.TabControl.GetToolTipText(System.Object)`
- `M:System.Windows.Forms.TableLayoutControlCollection.#ctor(System.Windows.Forms.TableLayoutPanel)`
- `M:System.Windows.Forms.ToolStripRenderer.OnRenderArrow(System.Windows.Forms.ToolStripArrowRenderEventArgs)`
- `M:System.Windows.Forms.ToolStripRenderer.OnRenderItemImage(System.Windows.Forms.ToolStripItemImageRenderEventArgs)`
- `M:System.Windows.Forms.ToolStripRenderer.OnRenderItemCheck(System.Windows.Forms.ToolStripItemImageRenderEventArgs)`
- `M:System.Windows.Forms.ToolStripRenderer.OnRenderItemText(System.Windows.Forms.ToolStripItemTextRenderEventArgs)`
- `M:System.Windows.Forms.ToolStripRenderer.OnRenderStatusStripSizingGrip(System.Windows.Forms.ToolStripRenderEventArgs)`
- `M:System.Windows.Forms.DataGridViewComboBoxEditingControl.ApplyCellStyleToEditingControl(System.Windows.Forms.DataGridViewCellStyle)`
- `M:System.Windows.Forms.RichTextBox.LoadFile(System.IO.Stream,System.Windows.Forms.RichTextBoxStreamType)`

-->
