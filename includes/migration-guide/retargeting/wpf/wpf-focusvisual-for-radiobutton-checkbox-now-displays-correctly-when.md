---
ms.openlocfilehash: 9e70bcd95393a7ff24de43577d26869ce674067b
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614614"
---
### <a name="wpf-focusvisual-for-radiobutton-and-checkbox-now-displays-correctly-when-the-controls-have-no-content"></a>Le visuel de focus WPF pour RadioButton et CheckBox s’affiche désormais correctement quand les contrôles n’ont pas de contenu

#### <a name="details"></a>Détails

Dans .NET Framework 4.7.1 et versions antérieures, les contrôles WPF <xref:System.Windows.Controls.CheckBox?displayProperty=nameWithType> et <xref:System.Windows.Controls.RadioButton?displayProperty=nameWithType> ont des visuels de focus incohérents et, dans les thèmes standard et à contraste élevé, incorrects.  Ces problèmes se produisent dans les cas où les contrôles n’ont pas de contenu défini.  Cela peut rendre la transition entre les thèmes confuse et le visuel de focus difficile à voir. Dans .NET Framework 4.7.2, ces visuels sont désormais plus cohérents entre les thèmes et plus facilement visibles dans les thèmes classique et à contraste élevé.

#### <a name="suggestion"></a>Suggestion

Un développeur ciblant .NET Framework 4.7.2 qui souhaite restaurer le comportement de .NET 4.7.1 doit définir l’indicateur AppContext suivant.

<pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.UseLegacyAccessibilityFeatures.2=true;&quot;/&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>

Un développeur qui souhaite utiliser cette modification tout en ciblant une version de .NET Framework antérieure à la version 4.7.2 doit définir les indicateurs AppContext suivants. Notez que tous les indicateurs doivent être définis correctement et que la version installée de .NET Framework doit être la version 4.7.2 ou ultérieure. Les applications WPF doivent accepter toutes les améliorations d’accessibilité antérieures pour obtenir les dernières améliorations. Pour ce faire, vérifiez que les deux commutateurs AppContext Switch.UseLegacyAccessibilityFeatures et Switch.UseLegacyAccessibilityFeatures.2 sont définis sur false.

<pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.UseLegacyAccessibilityFeatures=false;Switch.UseLegacyAccessibilityFeatures.2=false;&quot;/&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>

| Nom    | Valeur       |
|:--------|:------------|
| Étendue   | Edge        |
| Version | 4.7.2       |
| Type    | Reciblage |
