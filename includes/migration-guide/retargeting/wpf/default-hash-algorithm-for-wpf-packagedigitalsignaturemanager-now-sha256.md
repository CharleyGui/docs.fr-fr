---
ms.openlocfilehash: 745e880db08c5fa7e5514a71758f7fbb042e7ef4
ms.sourcegitcommit: d55e14eb63588830c0ba1ea95a24ce6c57ef8c8c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/11/2019
ms.locfileid: "67858986"
---
### <a name="the-default-hash-algorithm-for-wpf-packagedigitalsignaturemanager-is-now-sha256"></a>L’algorithme de hachage par défaut pour WPF PackageDigitalSignatureManager est désormais SHA256

|   |   |
|---|---|
|Détails|<code>System.IO.Packaging.PackageDigitalSignatureManager</code> fournit des fonctionnalités pour les signatures numériques en relation avec les packages WPF.  Dans le .NET Framework 4.7 et versions antérieures, l’algorithme par défaut (<xref:System.IO.Packaging.PackageDigitalSignatureManager.DefaultHashAlgorithm?displayProperty=nameWithType>) utilisé pour la signature des parties d’un package était SHA1.  En raison des récents problèmes de sécurité avec SHA1, cette valeur par défaut est remplacée par SHA256 à compter du .NET Framework 4.7.1.  Ce changement affecte toutes les signatures de package, notamment les documents XPS.|
|Suggestion|Un développeur qui souhaite utiliser ce changement tout en ciblant une version antérieure à .NET Framework 4.7.1 ou un développeur qui nécessite les fonctionnalités précédentes tout en ciblant .NET Framework 4.7.1 ou ultérieur peut définir l’indicateur AppContext en conséquence.  La valeur true signifie que SHA1 est utilisé comme algorithme par défaut ; false entraîne l’utilisation de SHA256.<pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.MS.Internal.UseSha1AsDefaultHashAlgorithmForDigitalSignatures=true&quot;/&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>|
|Portée|Microsoft Edge|
|Version|4.7.1|
|Type|Reciblage|
|API affectées|<ul><li><xref:System.IO.Packaging.PackageDigitalSignatureManager.DefaultHashAlgorithm?displayProperty=nameWithType></li></ul>|

