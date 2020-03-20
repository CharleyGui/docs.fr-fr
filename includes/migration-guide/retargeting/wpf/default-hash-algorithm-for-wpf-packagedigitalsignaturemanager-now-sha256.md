---
ms.openlocfilehash: 141e906077748795e0360cec450a54a9fd170dc9
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/15/2020
ms.locfileid: "67858986"
---
### <a name="the-default-hash-algorithm-for-wpf-packagedigitalsignaturemanager-is-now-sha256"></a>L’algorithme de hachage par défaut pour WPF PackageDigitalSignatureManager est désormais SHA256

|   |   |
|---|---|
|Détails|<code>System.IO.Packaging.PackageDigitalSignatureManager</code> fournit des fonctionnalités pour les signatures numériques en relation avec les packages WPF.  Dans le .NET Framework 4.7 et versions antérieures, l’algorithme par défaut (<xref:System.IO.Packaging.PackageDigitalSignatureManager.DefaultHashAlgorithm?displayProperty=nameWithType>) utilisé pour la signature des parties d’un package était SHA1.  En raison des récents problèmes de sécurité avec SHA1, cette valeur par défaut est remplacée par SHA256 à compter du .NET Framework 4.7.1.  Ce changement affecte toutes les signatures de package, notamment les documents XPS.|
|Suggestion|Un développeur qui souhaite utiliser ce changement tout en ciblant une version antérieure à .NET Framework 4.7.1 ou un développeur qui nécessite les fonctionnalités précédentes tout en ciblant .NET Framework 4.7.1 ou ultérieur peut définir l’indicateur AppContext en conséquence.  La valeur true signifie que SHA1 est utilisé comme algorithme par défaut ; false entraîne l’utilisation de SHA256.<pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.MS.Internal.UseSha1AsDefaultHashAlgorithmForDigitalSignatures=true&quot;/&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>|
|Étendue|Edge|
|Version|4.7.1|
|Type|Reciblage|
|API affectées|<ul><li><xref:System.IO.Packaging.PackageDigitalSignatureManager.DefaultHashAlgorithm?displayProperty=nameWithType></li></ul>|
