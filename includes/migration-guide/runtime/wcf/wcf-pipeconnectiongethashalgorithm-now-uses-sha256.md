---
ms.openlocfilehash: 9f5f238e3d4222af1da3a1713e1b3e65de6e6f49
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/22/2020
ms.locfileid: "91025019"
---
### <a name="wcf-pipeconnectiongethashalgorithm-now-uses-sha256"></a><span data-ttu-id="ab6f9-101">PipeConnection.GetHashAlgorithm dans WCF utilise maintenant SHA256</span><span class="sxs-lookup"><span data-stu-id="ab6f9-101">WCF PipeConnection.GetHashAlgorithm now uses SHA256</span></span>

#### <a name="details"></a><span data-ttu-id="ab6f9-102">Détails</span><span class="sxs-lookup"><span data-stu-id="ab6f9-102">Details</span></span>

<span data-ttu-id="ab6f9-103">À compter de .NET Framework 4.7.1, Windows Communication Foundation utilise un hachage SHA256 pour générer des noms aléatoires pour les canaux nommés.</span><span class="sxs-lookup"><span data-stu-id="ab6f9-103">Starting with the .NET Framework 4.7.1, Windows Communication Foundation uses a SHA256 hash to generate random names for named pipes.</span></span> <span data-ttu-id="ab6f9-104">Dans .NET Framework 4.7 et versions antérieures, il utilisait un hachage SHA1.</span><span class="sxs-lookup"><span data-stu-id="ab6f9-104">In the .NET Framework 4.7 and earlier versions, it used a SHA1 hash.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="ab6f9-105">Suggestion</span><span class="sxs-lookup"><span data-stu-id="ab6f9-105">Suggestion</span></span>

<span data-ttu-id="ab6f9-106">Si vous rencontrez des problèmes de compatibilité avec cette modification dans .NET Framework 4.7.1 ou version ultérieure, vous pouvez choisir de ne pas y adhérer en ajoutant la ligne suivante à la section `<runtime>` de votre fichier app.config :</span><span class="sxs-lookup"><span data-stu-id="ab6f9-106">If you run into compatibility issue with this change on the .NET Framework 4.7.1 or later, you can opt-out it by adding the following line to the `<runtime>` section of your app.config file:</span></span>

```xml
<configuration>
  <runtime>
    <AppContextSwitchOverrides value="Switch.System.ServiceModel.UseSha1InPipeConnectionGetHashAlgorithm=true" />
  </runtime>
</configuration>
```

| <span data-ttu-id="ab6f9-107">Nom</span><span class="sxs-lookup"><span data-stu-id="ab6f9-107">Name</span></span>    | <span data-ttu-id="ab6f9-108">Valeur</span><span class="sxs-lookup"><span data-stu-id="ab6f9-108">Value</span></span>   |
|:--------|:--------|
| <span data-ttu-id="ab6f9-109">Étendue</span><span class="sxs-lookup"><span data-stu-id="ab6f9-109">Scope</span></span>   | <span data-ttu-id="ab6f9-110">Secondaire</span><span class="sxs-lookup"><span data-stu-id="ab6f9-110">Minor</span></span>   |
| <span data-ttu-id="ab6f9-111">Version</span><span class="sxs-lookup"><span data-stu-id="ab6f9-111">Version</span></span> | <span data-ttu-id="ab6f9-112">4.7.1</span><span class="sxs-lookup"><span data-stu-id="ab6f9-112">4.7.1</span></span>   |
| <span data-ttu-id="ab6f9-113">Type</span><span class="sxs-lookup"><span data-stu-id="ab6f9-113">Type</span></span>    | <span data-ttu-id="ab6f9-114">Runtime</span><span class="sxs-lookup"><span data-stu-id="ab6f9-114">Runtime</span></span> |

#### <a name="affected-apis"></a><span data-ttu-id="ab6f9-115">API affectées</span><span class="sxs-lookup"><span data-stu-id="ab6f9-115">Affected APIs</span></span>

<span data-ttu-id="ab6f9-116">Non détectable via l’analyse des API.</span><span class="sxs-lookup"><span data-stu-id="ab6f9-116">Not detectable via API analysis.</span></span>

<!--

#### Affected APIs

Not detectable via API analysis.

-->
