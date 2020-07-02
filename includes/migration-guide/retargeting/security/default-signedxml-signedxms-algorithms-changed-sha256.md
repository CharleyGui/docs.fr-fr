---
ms.openlocfilehash: e2ae329d027d605e6331afe422e550990fab1042
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614539"
---
### <a name="default-signedxml-and-signedxms-algorithms-changed-to-sha256"></a>Valeur par défaut des algorithmes SignedXML et SignedXMS remplacée par SHA256

#### <a name="details"></a>Détails

Dans .NET Framework 4.7 et les versions antérieures, SignedXML et SignedCMS utilisent par défaut SHA1 pour certaines opérations. À compter de .NET Framework 4.7.1, SHA256 est activé par défaut pour ces opérations. Ce changement est nécessaire car SHA1 n’est plus considérée comme sécurisé.

#### <a name="suggestion"></a>Suggestion

Deux nouvelles valeurs de commutateur de contexte permettent de contrôler si SHA1 (non sécurisé) ou SHA256 est utilisé par défaut :

- Switch.System.Security.Cryptography.Xml.UseInsecureHashAlgorithms
- Switch.SysTEM. Security. Cryptography. Pkcs. UseInsecureHashAlgorithms pour les applications qui ciblent le .NET Framework 4.7.1 et versions ultérieures. si l’utilisation de SHA256 n’est pas souhaitable, vous pouvez restaurer la valeur par défaut SHA1 en ajoutant le commutateur de configuration suivant à la section [Runtime](~/docs/framework/configure-apps/file-schema/runtime/runtime-element.md) de votre fichier de configuration d’application :

```xml
<AppContextSwitchOverrides value="Switch.System.Security.Cryptography.Xml.UseInsecureHashAlgorithms=true;Switch.System.Security.Cryptography.Pkcs.UseInsecureHashAlgorithms=true" />
```

Pour les applications que ciblent .NET Framework 4.7 et les versions antérieures, vous pouvez accepter ce changement en ajoutant le commutateur de configuration suivant à la section [runtime](~/docs/framework/configure-apps/file-schema/runtime/runtime-element.md) de votre fichier de configuration d’application :

```xml
<AppContextSwitchOverrides value="Switch.System.Security.Cryptography.Xml.UseInsecureHashAlgorithms=false;Switch.System.Security.Cryptography.Pkcs.UseInsecureHashAlgorithms=false" />
```

| Nom    | Valeur       |
|:--------|:------------|
| Étendue   | Secondaire       |
| Version | 4.7.1       |
| Type    | Reciblage |

#### <a name="affected-apis"></a>API affectées

- <xref:System.Security.Cryptography.Pkcs.CmsSigner?displayProperty=nameWithType>
- <xref:System.Security.Cryptography.Xml.SignedXml?displayProperty=nameWithType>
- <xref:System.Security.Cryptography.Xml.Reference?displayProperty=nameWithType>
