---
ms.openlocfilehash: bd656478a55856e676853e57f3e7386ea0aa0211
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614545"
---
### <a name="currentculture-is-not-preserved-across-wpf-dispatcher-operations"></a>CurrentCulture n’est pas conservé d’une opération de répartiteur WPF à l’autre

#### <a name="details"></a>Détails

À compter du .NET Framework 4.6, les changements apportés à <xref:System.Globalization.CultureInfo.CurrentCulture?displayProperty=fullName> ou <xref:System.Globalization.CultureInfo.CurrentUICulture?displayProperty=fullName> dans un <xref:System.Windows.Threading.Dispatcher?displayProperty=fullName> sont perdus à la fin de l’opération de ce répartiteur. De même, les changements apportés à <xref:System.Globalization.CultureInfo.CurrentCulture?displayProperty=fullName> ou <xref:System.Globalization.CultureInfo.CurrentUICulture?displayProperty=fullName> en dehors d’une opération de répartiteur peuvent ne pas être reflétés quand cette opération s’exécute. Concrètement, cela signifie que les changements <xref:System.Globalization.CultureInfo.CurrentCulture?displayProperty=fullName> et <xref:System.Globalization.CultureInfo.CurrentUICulture?displayProperty=fullName> peuvent ne pas circuler entre les rappels d’IU WPF et tout autre code dans une application WPF. Cela est dû à un changement dans <xref:System.Threading.ExecutionContext?displayProperty=fullName> qui provoque le stockage de <xref:System.Globalization.CultureInfo.CurrentCulture?displayProperty=fullName> et de <xref:System.Globalization.CultureInfo.CurrentUICulture?displayProperty=fullName> dans le contexte d’exécution à compter des applications ciblant le .NET Framework 4.6. Les opérations de répartiteur WPF stockent le contexte d’exécution utilisé pour commencer l’opération et restaurer le contexte précédent lorsque l’opération est terminée. Étant donné que <xref:System.Globalization.CultureInfo.CurrentCulture?displayProperty=fullName> et <xref:System.Globalization.CultureInfo.CurrentUICulture?displayProperty=fullName> font désormais partie de ce contexte, les modifications qui leur sont apportées dans une opération de répartiteur ne sont pas conservées en dehors de cette opération.

#### <a name="suggestion"></a>Suggestion

Si vos applications sont affectées par ce changement, vous pouvez le contourner en stockant la valeur <xref:System.Globalization.CultureInfo.CurrentCulture?displayProperty=fullName> ou <xref:System.Globalization.CultureInfo.CurrentUICulture?displayProperty=fullName> souhaitée dans un champ, puis en vérifiant dans tous les corps d’opérations de répartiteur (notamment les gestionnaires de rappels d’événements de l’interface utilisateur) que les bons <xref:System.Globalization.CultureInfo.CurrentCulture?displayProperty=fullName> et <xref:System.Globalization.CultureInfo.CurrentUICulture?displayProperty=fullName> sont définis. Étant donné que le changement d’ExecutionContext sous-jacent à ce changement WPF affecte uniquement les applications qui ciblent le .NET Framework 4.6 ou ultérieur, vous pouvez éviter le problème en ciblant le .NET Framework 4.5.2. Pour les applications qui ciblent le .NET Framework 4.6 ou ultérieur, vous pouvez également contourner ce changement en définissant le commutateur de compatibilité suivant :

<pre><code class="lang-csharp">AppContext.SetSwitch(&quot;Switch.System.Globalization.NoAsyncCurrentCulture&quot;, true);&#13;&#10;</code></pre>

Ce problème a été résolu par WPF dans le .NET Framework 4.6.2. Il a également été résolu dans .NET Framework versions 4.6 et 4.6.1 par le biais du correctif décrit dans [l’article 3139549 de la Base de connaissances](https://support.microsoft.com/kb/3139549). Les applications qui ciblent .NET Framework 4.6 ou ultérieur obtiennent automatiquement le comportement approprié dans les applications WPF. <xref:System.Globalization.CultureInfo.CurrentCulture?displayProperty=fullName>/<xref:System.Globalization.CultureInfo.CurrentUICulture?displayProperty=fullName> est conservé d’une opération de répartiteur à l’autre.

| Nom    | Valeur       |
|:--------|:------------|
| Étendue   | Secondaire       |
| Version | 4.6         |
| Type    | Reciblage |
