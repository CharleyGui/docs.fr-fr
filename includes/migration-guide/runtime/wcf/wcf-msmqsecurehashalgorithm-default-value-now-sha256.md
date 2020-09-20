---
ms.openlocfilehash: 7c0227980aa5d90f3788783088bcd7cd9509ed66
ms.sourcegitcommit: 261e0c98a111357692b3b63c596edf0cacf72991
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2020
ms.locfileid: "90770868"
---
### <a name="wcf-msmqsecurehashalgorithm-default-value-is-now-sha256"></a>La valeur par défaut de MsmqSecureHashAlgorithm dans WCF est désormais SHA256

#### <a name="details"></a>Détails

À compter de .NET Framework 4.7.1, l’algorithme de signature des messages par défaut dans WCF pour les messages Msmq est SHA256. Dans .NET Framework 4.7 et versions antérieures, l’algorithme de signature des messages par défaut est SHA1.

#### <a name="suggestion"></a>Suggestion

Si vous rencontrez des problèmes de compatibilité avec cette modification sur le .NET Framework 4.7.1 ou version ultérieure, vous pouvez annuler la modification en ajoutant la ligne suivante à la `<runtime>` section de votre fichier app.config :

```xml
<configuration>
  <runtime>
    <AppContextSwitchOverrides value=&quot;Switch.System.ServiceModel.UseSha1InMsmqEncryptionAlgorithm=true&quot; />
  </runtime>
</configuration>
```

| Nom    | Valeur   |
|:--------|:--------|
| Étendue   | Secondaire   |
| Version | 4.7.1   |
| Type    | Runtime |

#### <a name="affected-apis"></a>API affectées

Non détectable via l’analyse des API.

<!--

#### Affected APIs

Not detectable via API analysis.

-->
