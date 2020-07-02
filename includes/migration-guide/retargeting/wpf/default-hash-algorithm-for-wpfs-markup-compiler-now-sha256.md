---
ms.openlocfilehash: 4303b177ffe01328965c909a5a3809414fcead91
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614595"
---
### <a name="the-default-hash-algorithm-for-wpfs-markup-compiler-is-now-sha256"></a>L’algorithme de hachage par défaut pour le compilateur de balisage de WPF est désormais SHA256

#### <a name="details"></a>Détails

Le compilateur de balisage de WPF fournit des services de compilation pour les fichiers de balisage XAML.  Dans .NET Framework 4.7.1 et versions antérieures, l’algorithme de hachage par défaut utilisé pour les sommes de contrôle était SHA1. En raison des récents problèmes de sécurité avec SHA1, cette valeur par défaut est remplacée par SHA256 à compter de .NET Framework 4.7.2.  Ce changement affecte toutes les générations de somme de contrôle pour les fichiers de balisage pendant la compilation.

#### <a name="suggestion"></a>Suggestion

Un développeur qui cible .NET Framework 4.7.2 ou version ultérieure et souhaite restaurer le comportement de hachage SHA1 doit définir l’indicateur AppContext suivant.

<pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Windows.Markup.DoNotUseSha256ForMarkupCompilerChecksumAlgorithm=true&quot;/&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>

Un développeur qui souhaite utiliser le hachage SHA256 tout en ciblant une version du .NET Framework antérieure à la version 4.7.2 doit définir l’indicateur AppContext ci-dessous.  Notez que la version installée du .NET Framework doit être la version 4.7.2 ou une version ultérieure.

<pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Windows.Markup.DoNotUseSha256ForMarkupCompilerChecksumAlgorithm=false&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>

| Nom    | Valeur       |
|:--------|:------------|
| Étendue   | Mode transparent |
| Version | 4.7.2       |
| Type    | Reciblage |
