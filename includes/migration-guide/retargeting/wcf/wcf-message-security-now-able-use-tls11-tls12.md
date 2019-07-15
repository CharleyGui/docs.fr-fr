---
ms.openlocfilehash: 3b7b50700541649a785fa9bbe3ecc56c2697fbfc
ms.sourcegitcommit: d55e14eb63588830c0ba1ea95a24ce6c57ef8c8c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/11/2019
ms.locfileid: "67859079"
---
### <a name="wcf-message-security-now-is-able-to-use-tls11-and-tls12"></a><span data-ttu-id="e2103-101">La sécurité des messages WCF peut désormais utiliser TLS 1.1 et TLS 1.2</span><span class="sxs-lookup"><span data-stu-id="e2103-101">WCF message security now is able to use TLS1.1 and TLS1.2</span></span>

|   |   |
|---|---|
|<span data-ttu-id="e2103-102">Détails</span><span class="sxs-lookup"><span data-stu-id="e2103-102">Details</span></span>|<span data-ttu-id="e2103-103">À compter de .NET Framework 4.7, les clients peuvent configurer TLS 1.1 ou TLS 1.2 dans la sécurité des messages WCF en plus de SSL 3.0 et TLS 1.0 à l’aide des paramètres de configuration d’application.</span><span class="sxs-lookup"><span data-stu-id="e2103-103">Starting in the .NET Framework 4.7, customers can configure either TLS1.1 or TLS1.2 in WCF message security in addition to SSL3.0 and TLS1.0 through application configuration settings.</span></span>|
|<span data-ttu-id="e2103-104">Suggestion</span><span class="sxs-lookup"><span data-stu-id="e2103-104">Suggestion</span></span>|<span data-ttu-id="e2103-105">Dans .NET Framework 4.7, la prise en charge de TLS 1.1 et de TLS 1.2 dans la sécurité des messages WCF est désactivée par défaut.</span><span class="sxs-lookup"><span data-stu-id="e2103-105">In the .NET Framework 4.7, support for TLS1.1 and TLS1.2 in WCF message security is disabled by default.</span></span> <span data-ttu-id="e2103-106">Vous pouvez l’activer en ajoutant la ligne suivante à la section <code>&lt;runtime&gt;</code> du fichier app.config ou du fichier web.config :</span><span class="sxs-lookup"><span data-stu-id="e2103-106">You can enable it by adding the following line to the <code>&lt;runtime&gt;</code> section of the app.config or web.config file:</span></span><pre><code class="lang-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.ServiceModel.DisableUsingServicePointManagerSecurityProtocols=false;Switch.System.Net.DontEnableSchUseStrongCrypto=false&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>|
|<span data-ttu-id="e2103-107">Portée</span><span class="sxs-lookup"><span data-stu-id="e2103-107">Scope</span></span>|<span data-ttu-id="e2103-108">Microsoft Edge</span><span class="sxs-lookup"><span data-stu-id="e2103-108">Edge</span></span>|
|<span data-ttu-id="e2103-109">Version</span><span class="sxs-lookup"><span data-stu-id="e2103-109">Version</span></span>|<span data-ttu-id="e2103-110">4.7</span><span class="sxs-lookup"><span data-stu-id="e2103-110">4.7</span></span>|
|<span data-ttu-id="e2103-111">Type</span><span class="sxs-lookup"><span data-stu-id="e2103-111">Type</span></span>|<span data-ttu-id="e2103-112">Reciblage</span><span class="sxs-lookup"><span data-stu-id="e2103-112">Retargeting</span></span>|

