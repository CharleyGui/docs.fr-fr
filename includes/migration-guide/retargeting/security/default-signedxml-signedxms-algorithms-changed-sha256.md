---
ms.openlocfilehash: db076d6799e4de5b8610cf9c1aac79b5386a7229
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/15/2020
ms.locfileid: "67859050"
---
### <a name="default-signedxml-and-signedxms-algorithms-changed-to-sha256"></a>Valeur par défaut des algorithmes SignedXML et SignedXMS remplacée par SHA256

|   |   |
|---|---|
|Détails|Dans .NET Framework 4.7 et les versions antérieures, SignedXML et SignedCMS utilisent par défaut SHA1 pour certaines opérations. À compter de .NET Framework 4.7.1, SHA256 est activé par défaut pour ces opérations. Ce changement est nécessaire car SHA1 n’est plus considérée comme sécurisé.|
|Suggestion|Deux nouvelles valeurs de commutateur de contexte permettent de contrôler si SHA1 (non sécurisé) ou SHA256 est utilisé par défaut :<ul><li>Switch.System.Security.Cryptography.Xml.UseInsecureHashAlgorithms</li><li>Switch.System.Security.Cryptography.Pkcs.UseInsecureHashAlgorithms</li></ul>Pour les applications que ciblent .NET Framework 4.7.1 et les versions ultérieures, si l’utilisation de SHA256 n’est pas souhaitable, vous pouvez restaurer SHA1 comme valeur par défaut en ajoutant le commutateur de configuration suivant à la section [runtime](~/docs/framework/configure-apps/file-schema/runtime/runtime-element.md) de votre fichier de configuration d’application :<pre><code class="lang-xml">&lt;AppContextSwitchOverrides value=&quot;Switch.System.Security.Cryptography.Xml.UseInsecureHashAlgorithms=true;Switch.System.Security.Cryptography.Pkcs.UseInsecureHashAlgorithms=true&quot; /&gt;&#13;&#10;</code></pre>Pour les applications que ciblent .NET Framework 4.7 et les versions antérieures, vous pouvez accepter ce changement en ajoutant le commutateur de configuration suivant à la section [runtime](~/docs/framework/configure-apps/file-schema/runtime/runtime-element.md) de votre fichier de configuration d’application :<pre><code class="lang-xml">&lt;AppContextSwitchOverrides value=&quot;Switch.System.Security.Cryptography.Xml.UseInsecureHashAlgorithms=false;Switch.System.Security.Cryptography.Pkcs.UseInsecureHashAlgorithms=false&quot; /&gt;&#13;&#10;</code></pre>|
|Étendue|Secondaire|
|Version|4.7.1|
|Type|Reciblage|
|API affectées|<ul><li><xref:System.Security.Cryptography.Pkcs.CmsSigner?displayProperty=nameWithType></li><li><xref:System.Security.Cryptography.Xml.SignedXml?displayProperty=nameWithType></li><li><xref:System.Security.Cryptography.Xml.Reference?displayProperty=nameWithType></li></ul>|
