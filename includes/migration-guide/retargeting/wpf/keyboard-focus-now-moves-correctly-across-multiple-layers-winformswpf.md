---
ms.openlocfilehash: a82b720fd4e771481ea1142a88a095443afa0d5b
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614603"
---
### <a name="keyboard-focus-now-moves-correctly-across-multiple-layers-of-winformswpf-hosting"></a>Le focus clavier se déplace désormais correctement entre plusieurs couches d’hébergement WinForms/WPF

#### <a name="details"></a>Détails

Imaginez une application WPF qui héberge un contrôle WinForms hébergeant à son tour des contrôles WPF. Les utilisateurs peuvent être dans l’impossibilité de quitter la couche WinForms au moyen de la touche Tab si le premier ou dernier contrôle dans cette couche est le contrôle WPF `System.Windows.Forms.Integration.ElementHost`. Ce changement résout ce problème, et les utilisateurs peuvent désormais quitter la couche WinForms au moyen de la touche Tab. Les applications automatisées pour lesquelles il est indispensable que le focus ne quitte jamais la couche WinForms pourraient ne plus fonctionner comme prévu.

#### <a name="suggestion"></a>Suggestion

Un développeur qui souhaite utiliser ce changement tout en ciblant une version du .NET Framework antérieure à la version 4.7.2 peut définir l’ensemble suivant d’indicateurs AppContext sur false pour activer la modification.

<pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.UseLegacyAccessibilityFeatures=false;Switch.UseLegacyAccessibilityFeatures.2=false&quot;/&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>

Les applications WPF doivent accepter toutes les améliorations d’accessibilité antérieures pour obtenir les dernières améliorations. En d’autres termes, les deux commutateurs `Switch.UseLegacyAccessibilityFeatures` et `Switch.UseLegacyAccessibilityFeatures.2` doivent être définis. Un développeur qui a besoin des fonctionnalités antérieures tout en ciblant .NET 4.7.2 ou version ultérieure peut définir l’indicateur AppContext suivant sur la valeur true pour activer la modification.

<pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.UseLegacyAccessibilityFeatures.2=true&quot;/&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>

| Nom    | Valeur       |
|:--------|:------------|
| Étendue   | Edge        |
| Version | 4.7.2       |
| Type    | Reciblage |
