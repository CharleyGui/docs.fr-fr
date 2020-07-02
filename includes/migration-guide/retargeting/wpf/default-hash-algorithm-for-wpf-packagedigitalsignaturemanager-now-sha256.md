---
ms.openlocfilehash: d3e0a61601f60a389b662f6f74934b6e6dc6e663
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614587"
---
### <a name="the-default-hash-algorithm-for-wpf-packagedigitalsignaturemanager-is-now-sha256"></a>L’algorithme de hachage par défaut pour WPF PackageDigitalSignatureManager est désormais SHA256

#### <a name="details"></a>Détails

`System.IO.Packaging.PackageDigitalSignatureManager` fournit des fonctionnalités pour les signatures numériques en relation avec les packages WPF.  Dans le .NET Framework 4.7 et versions antérieures, l’algorithme par défaut (<xref:System.IO.Packaging.PackageDigitalSignatureManager.DefaultHashAlgorithm?displayProperty=nameWithType>) utilisé pour la signature des parties d’un package était SHA1.  En raison des récents problèmes de sécurité avec SHA1, cette valeur par défaut est remplacée par SHA256 à compter du .NET Framework 4.7.1.  Ce changement affecte toutes les signatures de package, notamment les documents XPS.

#### <a name="suggestion"></a>Suggestion

Un développeur qui souhaite utiliser ce changement tout en ciblant une version antérieure à .NET Framework 4.7.1 ou un développeur qui nécessite les fonctionnalités précédentes tout en ciblant .NET Framework 4.7.1 ou ultérieur peut définir l’indicateur AppContext en conséquence.  La valeur true signifie que SHA1 est utilisé comme algorithme par défaut ; false entraîne l’utilisation de SHA256.<pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.MS.Internal.UseSha1AsDefaultHashAlgorithmForDigitalSignatures=true&quot;/&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>

| Nom    | Valeur       |
|:--------|:------------|
| Étendue   | Edge        |
| Version | 4.7.1       |
| Type    | Reciblage |

#### <a name="affected-apis"></a>API affectées

- <xref:System.IO.Packaging.PackageDigitalSignatureManager.DefaultHashAlgorithm?displayProperty=nameWithType>
