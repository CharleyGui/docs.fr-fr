---
ms.openlocfilehash: 2aa6603e2ed77ffa94fbc6325cd5db50985bda6a
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85620081"
---
### <a name="previewlostkeyboardfocus-is-called-repeatedly-if-its-handler-shows-a-windows-forms-message-box"></a>PreviewLostKeyboardFocus est appelé de façon répétée si son gestionnaire affiche une boîte de message Windows Forms

#### <a name="details"></a>Détails

À compter de la version 4.5 du .NET Framework, quand vous appelez <xref:System.Windows.Forms.MessageBox.Show%2A?displayProperty=nameWithType> à partir d’un gestionnaire <xref:System.Windows.UIElement.PreviewLostKeyboardFocus>, le gestionnaire est redéclenché quand la boîte de message est fermée, ce qui peut aboutir à une boucle infinie de boîtes de message.

#### <a name="suggestion"></a>Suggestion

Il existe deux options pour contourner ce problème :<ol><li>Vous pouvez appeler <xref:System.Windows.MessageBox.Show%2A?displayProperty=nameWithType> au lieu de <xref:System.Windows.Forms.MessageBox.Show%2A?displayProperty=nameWithType>.</li><li>Vous pouvez afficher la boîte de message à partir d’un gestionnaire d’événements <xref:System.Windows.UIElement.LostKeyboardFocus> (au lieu du gestionnaire d’événements <xref:System.Windows.UIElement.PreviewLostKeyboardFocus?displayProperty=fullName>).</li></ol>

| Nom    | Valeur       |
|:--------|:------------|
| Étendue   |Edge|
|Version|4,5|
|Type|Runtime

#### <a name="affected-apis"></a>API affectées

-<xref:System.Windows.ContentElement.PreviewLostKeyboardFocus?displayProperty=nameWithType></li><li><xref:System.Windows.IInputElement.PreviewLostKeyboardFocus?displayProperty=nameWithType></li><li><xref:System.Windows.UIElement.PreviewLostKeyboardFocus?displayProperty=nameWithType></li><li><xref:System.Windows.UIElement3D.PreviewLostKeyboardFocus?displayProperty=nameWithType></li></ul>|
