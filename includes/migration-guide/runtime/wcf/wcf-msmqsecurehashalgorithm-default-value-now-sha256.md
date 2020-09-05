---
ms.openlocfilehash: 9baca45de1c8994f610815e84fdee8ba3930eb04
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/05/2020
ms.locfileid: "89496390"
---
### <a name="wcf-msmqsecurehashalgorithm-default-value-is-now-sha256"></a><span data-ttu-id="bb593-101">La valeur par défaut de MsmqSecureHashAlgorithm dans WCF est désormais SHA256</span><span class="sxs-lookup"><span data-stu-id="bb593-101">WCF MsmqSecureHashAlgorithm default value is now SHA256</span></span>

#### <a name="details"></a><span data-ttu-id="bb593-102">Détails</span><span class="sxs-lookup"><span data-stu-id="bb593-102">Details</span></span>

<span data-ttu-id="bb593-103">À compter de .NET Framework 4.7.1, l’algorithme de signature des messages par défaut dans WCF pour les messages Msmq est SHA256.</span><span class="sxs-lookup"><span data-stu-id="bb593-103">Starting with the .NET Framework 4.7.1, the default message signing algorithm in WCF for Msmq messages is SHA256.</span></span> <span data-ttu-id="bb593-104">Dans .NET Framework 4.7 et versions antérieures, l’algorithme de signature des messages par défaut est SHA1.</span><span class="sxs-lookup"><span data-stu-id="bb593-104">In the .NET Framework 4.7 and earlier versions, the default message signing algorithm is SHA1.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="bb593-105">Suggestion</span><span class="sxs-lookup"><span data-stu-id="bb593-105">Suggestion</span></span>

<span data-ttu-id="bb593-106">Si vous rencontrez des problèmes de compatibilité avec cette modification dans .NET Framework 4.7.1 ou version ultérieure, vous pouvez choisir de ne pas adhérer à la modification en ajoutant la ligne suivante à la section <code>&lt;runtime&gt;</code> de votre fichier app.config :</span><span class="sxs-lookup"><span data-stu-id="bb593-106">If you run into compatibility issues with this change on the .NET Framework 4.7.1 or later, you can opt-out the change by adding the following line to the <code>&lt;runtime&gt;</code>section of your app.config file:</span></span><pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.ServiceModel.UseSha1InMsmqEncryptionAlgorithm=true&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>

| <span data-ttu-id="bb593-107">Name</span><span class="sxs-lookup"><span data-stu-id="bb593-107">Name</span></span>    | <span data-ttu-id="bb593-108">Valeur</span><span class="sxs-lookup"><span data-stu-id="bb593-108">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="bb593-109">Étendue</span><span class="sxs-lookup"><span data-stu-id="bb593-109">Scope</span></span>   |<span data-ttu-id="bb593-110">Secondaire</span><span class="sxs-lookup"><span data-stu-id="bb593-110">Minor</span></span>|
|<span data-ttu-id="bb593-111">Version</span><span class="sxs-lookup"><span data-stu-id="bb593-111">Version</span></span>|<span data-ttu-id="bb593-112">4.7.1</span><span class="sxs-lookup"><span data-stu-id="bb593-112">4.7.1</span></span>|
|<span data-ttu-id="bb593-113">Type</span><span class="sxs-lookup"><span data-stu-id="bb593-113">Type</span></span>|<span data-ttu-id="bb593-114">Runtime</span><span class="sxs-lookup"><span data-stu-id="bb593-114">Runtime</span></span>|

#### <a name="affected-apis"></a><span data-ttu-id="bb593-115">API affectées</span><span class="sxs-lookup"><span data-stu-id="bb593-115">Affected APIs</span></span>

<span data-ttu-id="bb593-116">Non détectable via l’analyse des API.</span><span class="sxs-lookup"><span data-stu-id="bb593-116">Not detectable via API analysis.</span></span>

<!--

#### Affected APIs

Not detectable via API analysis.

-->
