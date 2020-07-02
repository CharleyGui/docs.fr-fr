---
ms.openlocfilehash: 0e949cbdeda99dd7b94e919b903a21171a57f527
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614491"
---
### <a name="wcf-binding-with-the-transportwithmessagecredential-security-mode"></a><span data-ttu-id="faa8a-101">Liaison WCF avec le mode de sécurité TransportWithMessageCredential</span><span class="sxs-lookup"><span data-stu-id="faa8a-101">WCF binding with the TransportWithMessageCredential security mode</span></span>

#### <a name="details"></a><span data-ttu-id="faa8a-102">Détails</span><span class="sxs-lookup"><span data-stu-id="faa8a-102">Details</span></span>

<span data-ttu-id="faa8a-103">À compter de .NET Framework 4.6.1, il est possible de configurer une liaison WCF qui utilise le mode de sécurité TransportWithMessageCredential pour recevoir des messages avec des en-têtes &quot;to&quot; non signés pour les clés de sécurité asymétriques. Par défaut, les en-têtes &quot;to&quot; non signés continueront à être rejetés dans .NET Framework 4.6.1.</span><span class="sxs-lookup"><span data-stu-id="faa8a-103">Beginning in the .NET Framework 4.6.1, WCF binding that uses the TransportWithMessageCredential security mode can be set up to receive messages with unsigned &quot;to&quot; headers for asymmetric security keys.By default, unsigned &quot;to&quot; headers will continue to be rejected in .NET Framework 4.6.1.</span></span> <span data-ttu-id="faa8a-104">Ils seront acceptés uniquement si une application accepte ce nouveau mode de fonctionnement en utilisant le commutateur de configuration Switch.System.ServiceModel.AllowUnsignedToHeader.</span><span class="sxs-lookup"><span data-stu-id="faa8a-104">They will only be accepted if an application opts into this new mode of operation using the Switch.System.ServiceModel.AllowUnsignedToHeader configuration switch.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="faa8a-105">Suggestion</span><span class="sxs-lookup"><span data-stu-id="faa8a-105">Suggestion</span></span>

<span data-ttu-id="faa8a-106">Parce qu’il s’agit d’une fonctionnalité d’abonnement, le comportement des applications existantes ne devrait pas être affecté.</span><span class="sxs-lookup"><span data-stu-id="faa8a-106">Because this is an opt-in feature, it should not affect the behavior of existing apps.</span></span><br/><span data-ttu-id="faa8a-107">Pour contrôler si le nouveau comportement est utilisé ou non, utilisez le paramètre de configuration suivant :</span><span class="sxs-lookup"><span data-stu-id="faa8a-107">To control whether the new behavior is used or not, use the following configuration setting:</span></span>

```xml
<runtime>
  <AppContextSwitchOverrides value="Switch.System.ServiceModel.AllowUnsignedToHeader=true" />
</runtime>
```

| <span data-ttu-id="faa8a-108">Nom</span><span class="sxs-lookup"><span data-stu-id="faa8a-108">Name</span></span>    | <span data-ttu-id="faa8a-109">Valeur</span><span class="sxs-lookup"><span data-stu-id="faa8a-109">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="faa8a-110">Étendue</span><span class="sxs-lookup"><span data-stu-id="faa8a-110">Scope</span></span>   | <span data-ttu-id="faa8a-111">Mode transparent</span><span class="sxs-lookup"><span data-stu-id="faa8a-111">Transparent</span></span> |
| <span data-ttu-id="faa8a-112">Version</span><span class="sxs-lookup"><span data-stu-id="faa8a-112">Version</span></span> | <span data-ttu-id="faa8a-113">4.6.1</span><span class="sxs-lookup"><span data-stu-id="faa8a-113">4.6.1</span></span>       |
| <span data-ttu-id="faa8a-114">Type</span><span class="sxs-lookup"><span data-stu-id="faa8a-114">Type</span></span>    | <span data-ttu-id="faa8a-115">Reciblage</span><span class="sxs-lookup"><span data-stu-id="faa8a-115">Retargeting</span></span> |

#### <a name="affected-apis"></a><span data-ttu-id="faa8a-116">API affectées</span><span class="sxs-lookup"><span data-stu-id="faa8a-116">Affected APIs</span></span>

- <xref:System.ServiceModel.BasicHttpSecurityMode.TransportWithMessageCredential?displayProperty=nameWithType>
- <xref:System.ServiceModel.BasicHttpsSecurityMode.TransportWithMessageCredential?displayProperty=nameWithType>
- <xref:System.ServiceModel.SecurityMode.TransportWithMessageCredential?displayProperty=nameWithType>
- <xref:System.ServiceModel.WSFederationHttpSecurityMode.TransportWithMessageCredential?displayProperty=nameWithType>
