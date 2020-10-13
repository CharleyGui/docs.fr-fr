---
ms.openlocfilehash: d312ba2a22797ff6afff6b893f998c965e68e86e
ms.sourcegitcommit: e078b7540a8293ca1b604c9c0da1ff1506f0170b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/13/2020
ms.locfileid: "91997758"
---
### <a name="default-tls-cipher-suites-for-net-on-linux"></a><span data-ttu-id="fd9f1-101">Suites de chiffrement TLS par défaut pour .NET sur Linux</span><span class="sxs-lookup"><span data-stu-id="fd9f1-101">Default TLS cipher suites for .NET on Linux</span></span>

<span data-ttu-id="fd9f1-102">.NET, sur Linux, respecte à présent la configuration OpenSSL pour les suites de chiffrement par défaut lors de l’utilisation de TLS/SSL via la <xref:System.Net.Security.SslStream> classe ou des opérations de niveau supérieur, telles que https via la <xref:System.Net.Http.HttpClient> classe.</span><span class="sxs-lookup"><span data-stu-id="fd9f1-102">.NET, on Linux, now respects the OpenSSL configuration for default cipher suites when doing TLS/SSL via the <xref:System.Net.Security.SslStream> class or higher-level operations, such as HTTPS via the <xref:System.Net.Http.HttpClient> class.</span></span> <span data-ttu-id="fd9f1-103">Lorsque les suites de chiffrement par défaut ne sont pas explicitement configurées, .NET sur Linux utilise une liste restreinte de suites de chiffrement autorisées.</span><span class="sxs-lookup"><span data-stu-id="fd9f1-103">When default cipher suites aren't explicitly configured, .NET on Linux uses a tightly restricted list of permitted cipher suites.</span></span>

#### <a name="change-description"></a><span data-ttu-id="fd9f1-104">Description de la modification</span><span class="sxs-lookup"><span data-stu-id="fd9f1-104">Change description</span></span>

<span data-ttu-id="fd9f1-105">Dans les versions précédentes de .NET, .NET ne respecte pas la configuration du système pour les suites de chiffrement par défaut.</span><span class="sxs-lookup"><span data-stu-id="fd9f1-105">In previous .NET versions, .NET does not respect system configuration for default cipher suites.</span></span> <span data-ttu-id="fd9f1-106">La liste de suites de chiffrement par défaut pour .NET sur Linux est très permissive.</span><span class="sxs-lookup"><span data-stu-id="fd9f1-106">The default cipher suite list for .NET on Linux is very permissive.</span></span>

<span data-ttu-id="fd9f1-107">À compter de .NET 5,0, .NET sur Linux respecte la configuration OpenSSL pour les suites de chiffrement par défaut lorsqu’il est spécifié dans *OpenSSL. cnf*.</span><span class="sxs-lookup"><span data-stu-id="fd9f1-107">Starting in .NET 5.0, .NET on Linux respects the OpenSSL configuration for default cipher suites when it's specified in *openssl.cnf*.</span></span> <span data-ttu-id="fd9f1-108">Lorsque les suites de chiffrement ne sont pas explicitement configurées, les seules suites de chiffrement autorisées sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="fd9f1-108">When cipher suites aren't explicitly configured, the only permitted cipher suites are as follows:</span></span>

- <span data-ttu-id="fd9f1-109">Suites de chiffrement TLS 1,3</span><span class="sxs-lookup"><span data-stu-id="fd9f1-109">TLS 1.3 cipher suites</span></span>
- <span data-ttu-id="fd9f1-110">TLS_ECDHE_ECDSA_WITH_AES_256_GCM_SHA384</span><span class="sxs-lookup"><span data-stu-id="fd9f1-110">TLS_ECDHE_ECDSA_WITH_AES_256_GCM_SHA384</span></span>
- <span data-ttu-id="fd9f1-111">TLS_ECDHE_ECDSA_WITH_AES_128_GCM_SHA256</span><span class="sxs-lookup"><span data-stu-id="fd9f1-111">TLS_ECDHE_ECDSA_WITH_AES_128_GCM_SHA256</span></span>
- <span data-ttu-id="fd9f1-112">TLS_ECDHE_RSA_WITH_AES_256_GCM_SHA384</span><span class="sxs-lookup"><span data-stu-id="fd9f1-112">TLS_ECDHE_RSA_WITH_AES_256_GCM_SHA384</span></span>
- <span data-ttu-id="fd9f1-113">TLS_ECDHE_RSA_WITH_AES_128_GCM_SHA256</span><span class="sxs-lookup"><span data-stu-id="fd9f1-113">TLS_ECDHE_RSA_WITH_AES_128_GCM_SHA256</span></span>
- <span data-ttu-id="fd9f1-114">TLS_ECDHE_ECDSA_WITH_AES_256_CBC_SHA384</span><span class="sxs-lookup"><span data-stu-id="fd9f1-114">TLS_ECDHE_ECDSA_WITH_AES_256_CBC_SHA384</span></span>
- <span data-ttu-id="fd9f1-115">TLS_ECDHE_ECDSA_WITH_AES_128_CBC_SHA256</span><span class="sxs-lookup"><span data-stu-id="fd9f1-115">TLS_ECDHE_ECDSA_WITH_AES_128_CBC_SHA256</span></span>
- <span data-ttu-id="fd9f1-116">TLS_ECDHE_RSA_WITH_AES_256_CBC_SHA384</span><span class="sxs-lookup"><span data-stu-id="fd9f1-116">TLS_ECDHE_RSA_WITH_AES_256_CBC_SHA384</span></span>
- <span data-ttu-id="fd9f1-117">TLS_ECDHE_RSA_WITH_AES_128_CBC_SHA256</span><span class="sxs-lookup"><span data-stu-id="fd9f1-117">TLS_ECDHE_RSA_WITH_AES_128_CBC_SHA256</span></span>

<span data-ttu-id="fd9f1-118">Étant donné que cette valeur par défaut de secours n’inclut aucune suite de chiffrement compatible avec TLS 1,0 ou TLS 1,1, ces anciennes versions de protocole sont effectivement désactivées par défaut.</span><span class="sxs-lookup"><span data-stu-id="fd9f1-118">Since this fallback default doesn't include any cipher suites that are compatible with TLS 1.0 or TLS 1.1, these older protocol versions are effectively disabled by default.</span></span>

<span data-ttu-id="fd9f1-119">La spécification d’une valeur CipherSuitePolicy à SslStream pour une session spécifique remplacera toujours le contenu du fichier de configuration et/ou la valeur par défaut de secours .NET.</span><span class="sxs-lookup"><span data-stu-id="fd9f1-119">Supplying a CipherSuitePolicy value to SslStream for a specific session will still replace the configuration file content and/or .NET fallback default.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="fd9f1-120">Motif de modification</span><span class="sxs-lookup"><span data-stu-id="fd9f1-120">Reason for change</span></span>

<span data-ttu-id="fd9f1-121">Les utilisateurs qui exécutent .NET sur Linux ont demandé que la configuration par défaut <xref:System.Net.Security.SslStream> soit remplacée par une valeur qui fournissait un niveau de sécurité élevé à partir d’outils d’évaluation tiers.</span><span class="sxs-lookup"><span data-stu-id="fd9f1-121">Users running .NET on Linux requested that the default configuration for <xref:System.Net.Security.SslStream> be changed to one that provided a high security rating from third-party assessment tools.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="fd9f1-122">Version introduite</span><span class="sxs-lookup"><span data-stu-id="fd9f1-122">Version introduced</span></span>

<span data-ttu-id="fd9f1-123">5,0 RC1</span><span class="sxs-lookup"><span data-stu-id="fd9f1-123">5.0 RC1</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="fd9f1-124">Action recommandée</span><span class="sxs-lookup"><span data-stu-id="fd9f1-124">Recommended action</span></span>

<span data-ttu-id="fd9f1-125">Les nouvelles valeurs par défaut sont susceptibles de fonctionner lors de la communication avec les clients ou serveurs modernes.</span><span class="sxs-lookup"><span data-stu-id="fd9f1-125">The new defaults are likely to work when communicating with modern clients or servers.</span></span> <span data-ttu-id="fd9f1-126">Si vous devez développer la liste des suites de chiffrement par défaut pour accepter les clients hérités (ou pour contacter les serveurs hérités), spécifiez une `CipherSuitePolicy` valeur ou modifiez le fichier de configuration OpenSSL.</span><span class="sxs-lookup"><span data-stu-id="fd9f1-126">If you need to expand the default cipher suite list to accept legacy clients (or to contact legacy servers), either specify a `CipherSuitePolicy` value or change the OpenSSL configuration file.</span></span> <span data-ttu-id="fd9f1-127">Dans de nombreuses distributions Linux, le fichier de configuration OpenSSL se trouve sur */etc/SSL/OpenSSL.cnf*.</span><span class="sxs-lookup"><span data-stu-id="fd9f1-127">On many Linux distributions, the OpenSSL configuration file is at */etc/ssl/openssl.cnf*.</span></span>

<span data-ttu-id="fd9f1-128">Cet exemple de fichier *OpenSSL. cnf* est un fichier minimal équivalent à la stratégie de suites de chiffrement par défaut pour .net 5,0 et versions ultérieures sur Linux.</span><span class="sxs-lookup"><span data-stu-id="fd9f1-128">This sample *openssl.cnf* file is a minimal file that's equivalent to the default cipher suites policy for .NET 5.0 and later on Linux.</span></span> <span data-ttu-id="fd9f1-129">Au lieu de remplacer le fichier système, fusionnez ces concepts avec le fichier présent sur votre système.</span><span class="sxs-lookup"><span data-stu-id="fd9f1-129">Instead of replacing the system file, merge these concepts with the file that's present on your system.</span></span>

```ini
openssl_conf = default_conf

[default_conf]
ssl_conf = ssl_sect

[ssl_sect]
system_default = system_default_sect

[system_default_sect]
CipherString = ECDHE-ECDSA-AES256-GCM-SHA384:ECDHE-ECDSA-AES128-GCM-SHA256:ECDHE-RSA-AES256-GCM-SHA384:ECDHE-RSA-AES128-GCM-SHA256:ECDHE-ECDSA-AES256-SHA384:ECDHE-ECDSA-AES128-SHA256:ECDHE-RSA-AES256-SHA384:ECDHE-RSA-AES128-SHA256
```

<span data-ttu-id="fd9f1-130">Sur les distributions Red Hat Enterprise Linux, CentOS et Fedora, les applications .NET ont par défaut les suites de chiffrement autorisées par les stratégies de chiffrement à l’ensemble du système.</span><span class="sxs-lookup"><span data-stu-id="fd9f1-130">On the Red Hat Enterprise Linux, CentOS, and Fedora distributions, .NET applications default to the cipher suites permitted by the system-wide cryptographic policies.</span></span> <span data-ttu-id="fd9f1-131">Sur ces distributions, utilisez la configuration des stratégies de chiffrement au lieu de *OpenSSL. cnf*.</span><span class="sxs-lookup"><span data-stu-id="fd9f1-131">On these distributions, use the crypto-policies configuration instead of *openssl.cnf*.</span></span>

#### <a name="category"></a><span data-ttu-id="fd9f1-132">Category</span><span class="sxs-lookup"><span data-stu-id="fd9f1-132">Category</span></span>

- <span data-ttu-id="fd9f1-133">Chiffrement</span><span class="sxs-lookup"><span data-stu-id="fd9f1-133">Cryptography</span></span>
- <span data-ttu-id="fd9f1-134">Sécurité</span><span class="sxs-lookup"><span data-stu-id="fd9f1-134">Security</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="fd9f1-135">API affectées</span><span class="sxs-lookup"><span data-stu-id="fd9f1-135">Affected APIs</span></span>

<span data-ttu-id="fd9f1-136">Non detectible via l’analyse des API.</span><span class="sxs-lookup"><span data-stu-id="fd9f1-136">Not detectible via API analysis.</span></span>

<!--

#### Affected APIs

- Not detectible via API analysis.

-->
