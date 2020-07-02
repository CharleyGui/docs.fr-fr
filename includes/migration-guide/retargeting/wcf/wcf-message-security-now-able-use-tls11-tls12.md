---
ms.openlocfilehash: c646372104457e8bc5d418744847f3ee771c8d8b
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614536"
---
### <a name="wcf-message-security-now-is-able-to-use-tls11-and-tls12"></a><span data-ttu-id="490fa-101">La sécurité des messages WCF peut désormais utiliser TLS 1.1 et TLS 1.2</span><span class="sxs-lookup"><span data-stu-id="490fa-101">WCF message security now is able to use TLS1.1 and TLS1.2</span></span>

#### <a name="details"></a><span data-ttu-id="490fa-102">Détails</span><span class="sxs-lookup"><span data-stu-id="490fa-102">Details</span></span>

<span data-ttu-id="490fa-103">À compter de .NET Framework 4.7, les clients peuvent configurer TLS 1.1 ou TLS 1.2 dans la sécurité des messages WCF en plus de SSL 3.0 et TLS 1.0 à l’aide des paramètres de configuration d’application.</span><span class="sxs-lookup"><span data-stu-id="490fa-103">Starting in the .NET Framework 4.7, customers can configure either TLS1.1 or TLS1.2 in WCF message security in addition to SSL3.0 and TLS1.0 through application configuration settings.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="490fa-104">Suggestion</span><span class="sxs-lookup"><span data-stu-id="490fa-104">Suggestion</span></span>

<span data-ttu-id="490fa-105">Dans .NET Framework 4.7, la prise en charge de TLS 1.1 et de TLS 1.2 dans la sécurité des messages WCF est désactivée par défaut.</span><span class="sxs-lookup"><span data-stu-id="490fa-105">In the .NET Framework 4.7, support for TLS1.1 and TLS1.2 in WCF message security is disabled by default.</span></span> <span data-ttu-id="490fa-106">Vous pouvez l’activer en ajoutant la ligne suivante à la section `<runtime>` du fichier app.config ou du fichier web.config :</span><span class="sxs-lookup"><span data-stu-id="490fa-106">You can enable it by adding the following line to the `<runtime>` section of the app.config or web.config file:</span></span>

```xml
<runtime>
<AppContextSwitchOverrides value="Switch.System.ServiceModel.DisableUsingServicePointManagerSecurityProtocols=false;Switch.System.Net.DontEnableSchUseStrongCrypto=false" />
</runtime>
```

| <span data-ttu-id="490fa-107">Nom</span><span class="sxs-lookup"><span data-stu-id="490fa-107">Name</span></span>    | <span data-ttu-id="490fa-108">Valeur</span><span class="sxs-lookup"><span data-stu-id="490fa-108">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="490fa-109">Étendue</span><span class="sxs-lookup"><span data-stu-id="490fa-109">Scope</span></span>   | <span data-ttu-id="490fa-110">Edge</span><span class="sxs-lookup"><span data-stu-id="490fa-110">Edge</span></span>        |
| <span data-ttu-id="490fa-111">Version</span><span class="sxs-lookup"><span data-stu-id="490fa-111">Version</span></span> | <span data-ttu-id="490fa-112">4,7</span><span class="sxs-lookup"><span data-stu-id="490fa-112">4.7</span></span>         |
| <span data-ttu-id="490fa-113">Type</span><span class="sxs-lookup"><span data-stu-id="490fa-113">Type</span></span>    | <span data-ttu-id="490fa-114">Reciblage</span><span class="sxs-lookup"><span data-stu-id="490fa-114">Retargeting</span></span> |
