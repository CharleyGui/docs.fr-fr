---
ms.openlocfilehash: 3cf1740565343558a85fdfa68957773468c28231
ms.sourcegitcommit: 261e0c98a111357692b3b63c596edf0cacf72991
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2020
ms.locfileid: "90770809"
---
### <a name="wcf-pipeconnectiongethashalgorithm-now-uses-sha256"></a>PipeConnection.GetHashAlgorithm dans WCF utilise maintenant SHA256

#### <a name="details"></a>Détails

À compter de .NET Framework 4.7.1, Windows Communication Foundation utilise un hachage SHA256 pour générer des noms aléatoires pour les canaux nommés. Dans .NET Framework 4.7 et versions antérieures, il utilisait un hachage SHA1.

#### <a name="suggestion"></a>Suggestion

Si vous rencontrez des problèmes de compatibilité avec cette modification dans .NET Framework 4.7.1 ou version ultérieure, vous pouvez choisir de ne pas y adhérer en ajoutant la ligne suivante à la section `<runtime>` de votre fichier app.config :

```xml
<configuration>
  <runtime>
    <AppContextSwitchOverrides value="Switch.System.ServiceModel.UseSha1InPipeConnectionGetHashAlgorithm=true" />
  </runtime>
</configuration>

| Name    | Value   |
|:--------|:--------|
| Scope   | Minor   |
| Version | 4.7.1   |
| Type    | Runtime |

#### Affected APIs

Not detectable via API analysis.

<!--

#### Affected APIs

Not detectable via API analysis.

-->
