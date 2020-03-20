---
ms.openlocfilehash: 923105114c9e8da02c61c842cc02bed1ead3eddc
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/15/2020
ms.locfileid: "67858975"
---
### <a name="tabcontrol-selectionchanged-event-and-selectedcontent-property"></a>Événement TabControl SelectionChanged et propriété SelectedContent

|   |   |
|---|---|
|Détails|À compter de .NET Framework 4.7.1, un <xref:System.Windows.Controls.TabControl> met à jour la valeur de sa propriété <xref:System.Windows.Controls.TabControl.SelectedContent> avant de déclencher l’événement <xref:System.Windows.Controls.Primitives.Selector.SelectionChanged> quand sa sélection change. Dans .NET Framework 4.7 et antérieur, la mise à jour de SelectedContent se produisait après l’événement.|
|Suggestion|Les applications qui ciblent .NET Framework 4.7.1 ou ultérieur peuvent refuser ce changement et utiliser le comportement hérité en ajoutant le code suivant à la section <code>&lt;runtime&gt;</code> du fichier de configuration d’application :<pre><code class="lang-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Windows.Controls.TabControl.SelectionPropertiesCanLagBehindSelectionChangedEvent=true&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>Les applications qui ciblent .NET Framework 4.7 ou antérieur mais qui s’exécutent sur .NET Framework 4.7.1 ou ultérieur peuvent activer le nouveau comportement en ajoutant la ligne suivante à la section <code>&lt;runtime&gt;</code> du fichier .configuration de l’application :<pre><code class="lang-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Windows.Controls.TabControl.SelectionPropertiesCanLagBehindSelectionChangedEvent=false&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>|
|Étendue|Secondaire|
|Version|4.7.1|
|Type|Reciblage|
|API affectées|<ul><li><xref:System.Windows.Controls.TabControl.SelectedContent?displayProperty=nameWithType></li><li><xref:System.Windows.Controls.Primitives.Selector.SelectionChanged?displayProperty=nameWithType></li></ul>|
