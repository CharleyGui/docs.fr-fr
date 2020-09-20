---
ms.openlocfilehash: 7c0227980aa5d90f3788783088bcd7cd9509ed66
ms.sourcegitcommit: 261e0c98a111357692b3b63c596edf0cacf72991
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2020
ms.locfileid: "90770868"
---
### <a name="wcf-msmqsecurehashalgorithm-default-value-is-now-sha256"></a><span data-ttu-id="8af55-101">La valeur par défaut de MsmqSecureHashAlgorithm dans WCF est désormais SHA256</span><span class="sxs-lookup"><span data-stu-id="8af55-101">WCF MsmqSecureHashAlgorithm default value is now SHA256</span></span>

#### <a name="details"></a><span data-ttu-id="8af55-102">Détails</span><span class="sxs-lookup"><span data-stu-id="8af55-102">Details</span></span>

<span data-ttu-id="8af55-103">À compter de .NET Framework 4.7.1, l’algorithme de signature des messages par défaut dans WCF pour les messages Msmq est SHA256.</span><span class="sxs-lookup"><span data-stu-id="8af55-103">Starting with the .NET Framework 4.7.1, the default message signing algorithm in WCF for Msmq messages is SHA256.</span></span> <span data-ttu-id="8af55-104">Dans .NET Framework 4.7 et versions antérieures, l’algorithme de signature des messages par défaut est SHA1.</span><span class="sxs-lookup"><span data-stu-id="8af55-104">In the .NET Framework 4.7 and earlier versions, the default message signing algorithm is SHA1.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="8af55-105">Suggestion</span><span class="sxs-lookup"><span data-stu-id="8af55-105">Suggestion</span></span>

<span data-ttu-id="8af55-106">Si vous rencontrez des problèmes de compatibilité avec cette modification sur le .NET Framework 4.7.1 ou version ultérieure, vous pouvez annuler la modification en ajoutant la ligne suivante à la `<runtime>` section de votre fichier app.config :</span><span class="sxs-lookup"><span data-stu-id="8af55-106">If you run into compatibility issues with this change on the .NET Framework 4.7.1 or later, you can opt-out the change by adding the following line to the `<runtime>` section of your app.config file:</span></span>

```xml
<configuration>
  <runtime>
    <AppContextSwitchOverrides value=&quot;Switch.System.ServiceModel.UseSha1InMsmqEncryptionAlgorithm=true&quot; />
  </runtime>
</configuration>
```

| <span data-ttu-id="8af55-107">Nom</span><span class="sxs-lookup"><span data-stu-id="8af55-107">Name</span></span>    | <span data-ttu-id="8af55-108">Valeur</span><span class="sxs-lookup"><span data-stu-id="8af55-108">Value</span></span>   |
|:--------|:--------|
| <span data-ttu-id="8af55-109">Étendue</span><span class="sxs-lookup"><span data-stu-id="8af55-109">Scope</span></span>   | <span data-ttu-id="8af55-110">Secondaire</span><span class="sxs-lookup"><span data-stu-id="8af55-110">Minor</span></span>   |
| <span data-ttu-id="8af55-111">Version</span><span class="sxs-lookup"><span data-stu-id="8af55-111">Version</span></span> | <span data-ttu-id="8af55-112">4.7.1</span><span class="sxs-lookup"><span data-stu-id="8af55-112">4.7.1</span></span>   |
| <span data-ttu-id="8af55-113">Type</span><span class="sxs-lookup"><span data-stu-id="8af55-113">Type</span></span>    | <span data-ttu-id="8af55-114">Runtime</span><span class="sxs-lookup"><span data-stu-id="8af55-114">Runtime</span></span> |

#### <a name="affected-apis"></a><span data-ttu-id="8af55-115">API affectées</span><span class="sxs-lookup"><span data-stu-id="8af55-115">Affected APIs</span></span>

<span data-ttu-id="8af55-116">Non détectable via l’analyse des API.</span><span class="sxs-lookup"><span data-stu-id="8af55-116">Not detectable via API analysis.</span></span>

<!--

#### Affected APIs

Not detectable via API analysis.

-->
