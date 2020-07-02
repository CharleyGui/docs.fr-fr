---
ms.openlocfilehash: 7c2e80669d9ef27f87cde9442d8eeab0ee31a524
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614622"
---
### <a name="wpf-textboxpasswordbox-text-selection-does-not-follow-system-colors"></a>La sélection de texte WPF TextBox/PasswordBox ne suit pas les couleurs système

#### <a name="details"></a>Détails

Dans .NET Framework 4.7.1 et versions antérieures, WPF `System.Windows.Controls.TextBox` et `System.Windows.Controls.PasswordBox` pouvaient afficher une sélection de texte uniquement dans la couche Ornement. Dans certains thèmes système, cela occultait le texte, au point de le rendre difficile à lire.  Dans .NET Framework 4.7.2 et ultérieur, les développeurs ont la possibilité d’activer un schéma de rendu de sélection non basée sur la couche Ornement qui atténue ce problème.

#### <a name="suggestion"></a>Suggestion

Un développeur qui souhaite utiliser cette modification doit définir l’indicateur AppContext suivant de façon appropriée.  Vous ne pouvez utiliser cette fonctionnalité que si vous avez installé .NET Framework version 4.7.2 ou ultérieure. Pour activer la sélection non basée sur un ornement, utilisez l’indicateur AppContext suivant.<pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Windows.Controls.Text.UseAdornerForTextboxSelectionRendering=false&quot;/&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>

| Nom    | Valeur       |
|:--------|:------------|
| Étendue   | Edge        |
| Version | 4.7.2       |
| Type    | Reciblage |
