---
ms.openlocfilehash: 3cf1740565343558a85fdfa68957773468c28231
ms.sourcegitcommit: 261e0c98a111357692b3b63c596edf0cacf72991
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2020
ms.locfileid: "90770809"
---
### <a name="wcf-pipeconnectiongethashalgorithm-now-uses-sha256"></a><span data-ttu-id="b6295-101">PipeConnection.GetHashAlgorithm dans WCF utilise maintenant SHA256</span><span class="sxs-lookup"><span data-stu-id="b6295-101">WCF PipeConnection.GetHashAlgorithm now uses SHA256</span></span>

#### <a name="details"></a><span data-ttu-id="b6295-102">Détails</span><span class="sxs-lookup"><span data-stu-id="b6295-102">Details</span></span>

<span data-ttu-id="b6295-103">À compter de .NET Framework 4.7.1, Windows Communication Foundation utilise un hachage SHA256 pour générer des noms aléatoires pour les canaux nommés.</span><span class="sxs-lookup"><span data-stu-id="b6295-103">Starting with the .NET Framework 4.7.1, Windows Communication Foundation uses a SHA256 hash to generate random names for named pipes.</span></span> <span data-ttu-id="b6295-104">Dans .NET Framework 4.7 et versions antérieures, il utilisait un hachage SHA1.</span><span class="sxs-lookup"><span data-stu-id="b6295-104">In the .NET Framework 4.7 and earlier versions, it used a SHA1 hash.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="b6295-105">Suggestion</span><span class="sxs-lookup"><span data-stu-id="b6295-105">Suggestion</span></span>

<span data-ttu-id="b6295-106">Si vous rencontrez des problèmes de compatibilité avec cette modification dans .NET Framework 4.7.1 ou version ultérieure, vous pouvez choisir de ne pas y adhérer en ajoutant la ligne suivante à la section `<runtime>` de votre fichier app.config :</span><span class="sxs-lookup"><span data-stu-id="b6295-106">If you run into compatibility issue with this change on the .NET Framework 4.7.1 or later, you can opt-out it by adding the following line to the `<runtime>` section of your app.config file:</span></span>

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
