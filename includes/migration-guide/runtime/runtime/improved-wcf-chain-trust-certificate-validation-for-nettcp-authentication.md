---
ms.openlocfilehash: c8f017084fc1ec1eca636ef0178a40559e15b2c5
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/05/2020
ms.locfileid: "89497183"
---
### <a name="improved-wcf-chain-trust-certificate-validation-for-nettcp-certificate-authentication"></a><span data-ttu-id="6d1ea-101">Amélioration de la validation des certificats de confiance des chaînes WCF pour l’authentification de certificat Net.Tcp</span><span class="sxs-lookup"><span data-stu-id="6d1ea-101">Improved WCF chain trust certificate validation for Net.Tcp certificate authentication</span></span>

#### <a name="details"></a><span data-ttu-id="6d1ea-102">Détails</span><span class="sxs-lookup"><span data-stu-id="6d1ea-102">Details</span></span>

<span data-ttu-id="6d1ea-103">.NET Framework 4.7.2 améliore la validation des certificats de confiance des chaînes lors de l’utilisation de l’authentification de certificat avec la sécurité de transport avec WCF.</span><span class="sxs-lookup"><span data-stu-id="6d1ea-103">.NET Framework 4.7.2 improves chain trust certificate validation when using certificate authentication with transport security with WCF.</span></span> <span data-ttu-id="6d1ea-104">Avec cette amélioration, les certificats clients utilisés pour s’authentifier auprès d’un serveur doivent être configurés pour l’authentification client.</span><span class="sxs-lookup"><span data-stu-id="6d1ea-104">With this improvement, client certificates that are used to authenticate to a server must be configured for client authentication.</span></span>  <span data-ttu-id="6d1ea-105">De même, les certificats de serveur pour l’authentification d’un serveur doivent être configurés pour l’authentification serveur.</span><span class="sxs-lookup"><span data-stu-id="6d1ea-105">Similarly server certificates that are for the authenticating a server must be configured for server authentication.</span></span> <span data-ttu-id="6d1ea-106">Avec ce changement, si le certificat racine est désactivé, la validation de chaîne de certificat échoue.</span><span class="sxs-lookup"><span data-stu-id="6d1ea-106">With this change, if the root certificate is disabled, the certificate chain validation fails.</span></span> <span data-ttu-id="6d1ea-107">Le même changement a également été effectué pour .NET Framework 3.5 et versions ultérieures par le biais du déploiement de sécurité Windows.</span><span class="sxs-lookup"><span data-stu-id="6d1ea-107">The same change was also made to .NET Framework 3.5 and later versions via Windows security roll-up.</span></span> <span data-ttu-id="6d1ea-108">Vous trouverez plus d’informations [ici](https://support.microsoft.com/help/4055269/security-only-update-for-net-framework-3-5-1-4-5-2-4-6-4-6-1-4-6-2-4-7). Ce changement est activé par défaut et peut être désactivé par un paramètre de configuration.</span><span class="sxs-lookup"><span data-stu-id="6d1ea-108">You can find more information [here](https://support.microsoft.com/help/4055269/security-only-update-for-net-framework-3-5-1-4-5-2-4-6-4-6-1-4-6-2-4-7).This change is on by default and can be turned off by a configuration setting.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="6d1ea-109">Suggestion</span><span class="sxs-lookup"><span data-stu-id="6d1ea-109">Suggestion</span></span>

<ul><li><span data-ttu-id="6d1ea-110">Vérifiez si votre certification serveur et client a l’OID EKU nécessaire.</span><span class="sxs-lookup"><span data-stu-id="6d1ea-110">Validate if your server and client certification has the required EKU OID.</span></span> <span data-ttu-id="6d1ea-111">Si ce n’est pas le cas, mettez à jour votre certification.</span><span class="sxs-lookup"><span data-stu-id="6d1ea-111">If not, update your certification.</span></span></li><li><span data-ttu-id="6d1ea-112">Vérifiez si votre certificat racine est valide.</span><span class="sxs-lookup"><span data-stu-id="6d1ea-112">Validate if your root certificate is invalid.</span></span> <span data-ttu-id="6d1ea-113">Si ce n’est pas le cas, mettez-le à jour.</span><span class="sxs-lookup"><span data-stu-id="6d1ea-113">If so, update the root certificate.</span></span></li><li><span data-ttu-id="6d1ea-114">Comment ignorer ce changement : Si vous ne pouvez pas mettre à jour le certificat, vous pouvez contourner temporairement ce changement cassant avec le paramètre de configuration suivant. Toutefois, si vous choisissez d’ignorer ce changement, vous exposez votre système au problème de sécurité.</span><span class="sxs-lookup"><span data-stu-id="6d1ea-114">How to opt out of the change: If you can't update the certificate, you can work around the breaking change temporarily with the following configration setting,  However, opting out of the change will leave your system vulnerable to the security issue.</span></span></li></ul><pre><code class="lang-xml">&lt;appSettings&gt;&#13;&#10;&lt;add key=&quot;wcf:useLegacyCertificateUsagePolicy&quot; value=&quot;true&quot; /&gt;&#13;&#10;&lt;/appSettings&gt;&#13;&#10;</code></pre>

| <span data-ttu-id="6d1ea-115">Name</span><span class="sxs-lookup"><span data-stu-id="6d1ea-115">Name</span></span>    | <span data-ttu-id="6d1ea-116">Valeur</span><span class="sxs-lookup"><span data-stu-id="6d1ea-116">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="6d1ea-117">Étendue</span><span class="sxs-lookup"><span data-stu-id="6d1ea-117">Scope</span></span>   |<span data-ttu-id="6d1ea-118">Secondaire</span><span class="sxs-lookup"><span data-stu-id="6d1ea-118">Minor</span></span>|
|<span data-ttu-id="6d1ea-119">Version</span><span class="sxs-lookup"><span data-stu-id="6d1ea-119">Version</span></span>|<span data-ttu-id="6d1ea-120">4.7.2</span><span class="sxs-lookup"><span data-stu-id="6d1ea-120">4.7.2</span></span>|
|<span data-ttu-id="6d1ea-121">Type</span><span class="sxs-lookup"><span data-stu-id="6d1ea-121">Type</span></span>|<span data-ttu-id="6d1ea-122">Runtime</span><span class="sxs-lookup"><span data-stu-id="6d1ea-122">Runtime</span></span>|

#### <a name="affected-apis"></a><span data-ttu-id="6d1ea-123">API affectées</span><span class="sxs-lookup"><span data-stu-id="6d1ea-123">Affected APIs</span></span>

<span data-ttu-id="6d1ea-124">Non détectable via l’analyse des API.</span><span class="sxs-lookup"><span data-stu-id="6d1ea-124">Not detectable via API analysis.</span></span>

<!--

#### Affected APIs

Not detectable via API analysis.

-->
