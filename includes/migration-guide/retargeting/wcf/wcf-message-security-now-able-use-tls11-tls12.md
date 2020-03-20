---
ms.openlocfilehash: 0a3dc43ebdc58d54675f2264a8ee56d9f4358cd8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/15/2020
ms.locfileid: "67859079"
---
### <a name="wcf-message-security-now-is-able-to-use-tls11-and-tls12"></a><span data-ttu-id="9dca4-101">La sécurité des messages WCF peut désormais utiliser TLS 1.1 et TLS 1.2</span><span class="sxs-lookup"><span data-stu-id="9dca4-101">WCF message security now is able to use TLS1.1 and TLS1.2</span></span>

|   |   |
|---|---|
|<span data-ttu-id="9dca4-102">Détails</span><span class="sxs-lookup"><span data-stu-id="9dca4-102">Details</span></span>|<span data-ttu-id="9dca4-103">À compter de .NET Framework 4.7, les clients peuvent configurer TLS 1.1 ou TLS 1.2 dans la sécurité des messages WCF en plus de SSL 3.0 et TLS 1.0 à l’aide des paramètres de configuration d’application.</span><span class="sxs-lookup"><span data-stu-id="9dca4-103">Starting in the .NET Framework 4.7, customers can configure either TLS1.1 or TLS1.2 in WCF message security in addition to SSL3.0 and TLS1.0 through application configuration settings.</span></span>|
|<span data-ttu-id="9dca4-104">Suggestion</span><span class="sxs-lookup"><span data-stu-id="9dca4-104">Suggestion</span></span>|<span data-ttu-id="9dca4-105">Dans .NET Framework 4.7, la prise en charge de TLS 1.1 et de TLS 1.2 dans la sécurité des messages WCF est désactivée par défaut.</span><span class="sxs-lookup"><span data-stu-id="9dca4-105">In the .NET Framework 4.7, support for TLS1.1 and TLS1.2 in WCF message security is disabled by default.</span></span> <span data-ttu-id="9dca4-106">Vous pouvez l’activer en ajoutant la ligne suivante à la section <code>&lt;runtime&gt;</code> du fichier app.config ou du fichier web.config :</span><span class="sxs-lookup"><span data-stu-id="9dca4-106">You can enable it by adding the following line to the <code>&lt;runtime&gt;</code> section of the app.config or web.config file:</span></span><pre><code class="lang-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.ServiceModel.DisableUsingServicePointManagerSecurityProtocols=false;Switch.System.Net.DontEnableSchUseStrongCrypto=false&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>|
|<span data-ttu-id="9dca4-107">Étendue</span><span class="sxs-lookup"><span data-stu-id="9dca4-107">Scope</span></span>|<span data-ttu-id="9dca4-108">Edge</span><span class="sxs-lookup"><span data-stu-id="9dca4-108">Edge</span></span>|
|<span data-ttu-id="9dca4-109">Version</span><span class="sxs-lookup"><span data-stu-id="9dca4-109">Version</span></span>|<span data-ttu-id="9dca4-110">4,7</span><span class="sxs-lookup"><span data-stu-id="9dca4-110">4.7</span></span>|
|<span data-ttu-id="9dca4-111">Type</span><span class="sxs-lookup"><span data-stu-id="9dca4-111">Type</span></span>|<span data-ttu-id="9dca4-112">Reciblage</span><span class="sxs-lookup"><span data-stu-id="9dca4-112">Retargeting</span></span>|
