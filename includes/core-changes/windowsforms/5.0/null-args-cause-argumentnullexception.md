---
ms.openlocfilehash: fc0eec26073c299887b4748d0ad37e21c7294e84
ms.sourcegitcommit: 7980a91f90ae5eca859db7e6bfa03e23e76a1a50
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/13/2020
ms.locfileid: "81274827"
---
### <a name="winforms-apis-now-throw-argumentnullexception"></a>WinForms API maintenant jeter ArgumentNullException

Certaines méthodes de formulaires Windows maintenant jeter <xref:System.ArgumentNullException> un <xref:System.NullReferenceException>pour les arguments nuls, où auparavant ils ont jeté un .

#### <a name="change-description"></a>Description de la modification

Auparavant, certaines méthodes de <xref:System.NullReferenceException> Formulaires Windows ont lancé un argument qui était nul. À partir de .NET 5.0, <xref:System.ArgumentNullException> ces méthodes jettent maintenant un pour les arguments nuls à la place.

Jeter <xref:System.ArgumentNullException> une conformité au comportement de l’exécution .NET. Il améliore également l’expérience de débogage en communiquant clairement qu’un argument est nul et quel argument il est.

#### <a name="version-introduced"></a>Version introduite

.NET 5.0 Aperçu 1
.NET 5.0 Aperçu 2

#### <a name="recommended-action"></a>Action recommandée

Si vous appelez l’une de ces <xref:System.NullReferenceException> méthodes et que <xref:System.ArgumentNullException> votre code attrape actuellement un pour les arguments nuls, attrapez plutôt un. En outre, envisagez de mettre à jour le code pour éviter de transmettre des arguments nuls aux méthodes énumérées.

#### <a name="category"></a>Category

Windows Forms

#### <a name="affected-apis"></a>API affectées

À partir de .NET 5.0 Aperçu 1:

- <xref:System.Windows.Forms.Control.ControlCollection.%23ctor(System.Windows.Forms.Control)>
- <xref:System.Windows.Forms.TabControl.GetToolTipText(System.Object)?displayProperty=nameWithType>
- <xref:System.Windows.Forms.TableLayoutControlCollection.%23ctor(System.Windows.Forms.TableLayoutPanel)>
- <xref:System.Windows.Forms.ToolStripRenderer.OnRenderArrow(System.Windows.Forms.ToolStripArrowRenderEventArgs)?displayProperty=nameWithType>
- <xref:System.Windows.Forms.ToolStripRenderer.OnRenderItemImage(System.Windows.Forms.ToolStripItemImageRenderEventArgs)?displayProperty=nameWithType>
- <xref:System.Windows.Forms.ToolStripRenderer.OnRenderItemCheck(System.Windows.Forms.ToolStripItemImageRenderEventArgs)?displayProperty=nameWithType>
- <xref:System.Windows.Forms.ToolStripRenderer.OnRenderItemText(System.Windows.Forms.ToolStripItemTextRenderEventArgs)?displayProperty=nameWithType>
- <xref:System.Windows.Forms.ToolStripRenderer.OnRenderStatusStripSizingGrip(System.Windows.Forms.ToolStripRenderEventArgs)?displayProperty=nameWithType>

À partir de .NET 5.0 Aperçu 2:

- <xref:System.Windows.Forms.DataGridViewComboBoxEditingControl.ApplyCellStyleToEditingControl(System.Windows.Forms.DataGridViewCellStyle)?displayProperty=nameWithType>
- <xref:System.Windows.Forms.RichTextBox.LoadFile(System.IO.Stream,System.Windows.Forms.RichTextBoxStreamType)?displayProperty=nameWithType>(pour <xref:System.IO.Stream> le paramètre seulement)

<!-- 

### Affected APIs

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
