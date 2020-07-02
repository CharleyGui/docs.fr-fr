---
ms.openlocfilehash: 0ef39d67cd4335658658f5772b5bce49d827cad0
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614598"
---
### <a name="selector-selectionchanged-event-and-selectedvalue-property"></a>Événement SelectionChanged et propriété SelectedValue de Selector

#### <a name="details"></a>Détails

À compter de .NET Framework 4.7.1, un <xref:System.Windows.Controls.Primitives.Selector> met toujours à jour la valeur de sa propriété <xref:System.Windows.Controls.Primitives.Selector.SelectedValue%2A> avant de déclencher l’événement <xref:System.Windows.Controls.Primitives.Selector.SelectionChanged> quand sa sélection change. La propriété SelectedValue est ainsi cohérente avec les autres propriétés de sélection (<xref:System.Windows.Controls.Primitives.Selector.SelectedItem%2A> et <xref:System.Windows.Controls.Primitives.Selector.SelectedIndex%2A>), qui sont mises à jour avant le déclenchement de l’événement.<p/>Dans .NET Framework 4.7 et antérieur, la mise à jour de SelectedValue avait lieu avant l’événement dans la plupart des cas, mais elle se produisait après l’événement si le changement de sélection résultait du changement de la propriété <xref:System.Windows.Controls.Primitives.Selector.SelectedValue%2A>.

#### <a name="suggestion"></a>Suggestion

Les applications qui ciblent .NET Framework 4.7.1 ou ultérieur peuvent refuser ce changement et utiliser le comportement hérité en ajoutant le code suivant à la section `<runtime>` du fichier de configuration d’application :

<pre><code class="lang-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides&#13;&#10;value=&quot;Switch.System.Windows.Controls.TabControl.SelectionPropertiesCanLagBehindSelectionChangedEvent=true&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>

Les applications qui ciblent .NET Framework 4.7 ou antérieur mais qui s’exécutent sur .NET Framework 4.7.1 ou ultérieur peuvent activer le nouveau comportement en ajoutant la ligne suivante à la section `<runtime>` du fichier .configuration de l’application :

<pre><code class="lang-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Windows.Controls.TabControl.SelectionPropertiesCanLagBehindSelectionChangedEvent=false&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>

| Nom    | Valeur       |
|:--------|:------------|
| Étendue   | Secondaire       |
| Version | 4.7.1       |
| Type    | Reciblage |

#### <a name="affected-apis"></a>API affectées

- <xref:System.Windows.Controls.TabControl.SelectedContent?displayProperty=nameWithType>
- <xref:System.Windows.Controls.Primitives.Selector.SelectionChanged?displayProperty=nameWithType>
