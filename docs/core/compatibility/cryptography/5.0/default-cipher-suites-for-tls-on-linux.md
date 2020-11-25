---
title: 'Modification avec rupture : suites de chiffrement TLS par défaut pour .NET sur Linux'
description: Découvrez la modification avec rupture dans .NET 5,0 où .NET, sur Linux, respecte à présent la configuration OpenSSL pour les suites de chiffrement par défaut lors de l’installation de TLS/SSL.
ms.date: 10/16/2020
ms.openlocfilehash: f1c23517161ac213a9cd7cf6e7da8eebeb91583b
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95760808"
---
# <a name="default-tls-cipher-suites-for-net-on-linux"></a><span data-ttu-id="a63d4-103">Suites de chiffrement TLS par défaut pour .NET sur Linux</span><span class="sxs-lookup"><span data-stu-id="a63d4-103">Default TLS cipher suites for .NET on Linux</span></span>

<span data-ttu-id="a63d4-104">.NET, sur Linux, respecte à présent la configuration OpenSSL pour les suites de chiffrement par défaut lors de l’utilisation de TLS/SSL via la <xref:System.Net.Security.SslStream> classe ou des opérations de niveau supérieur, telles que https via la <xref:System.Net.Http.HttpClient> classe.</span><span class="sxs-lookup"><span data-stu-id="a63d4-104">.NET, on Linux, now respects the OpenSSL configuration for default cipher suites when doing TLS/SSL via the <xref:System.Net.Security.SslStream> class or higher-level operations, such as HTTPS via the <xref:System.Net.Http.HttpClient> class.</span></span> <span data-ttu-id="a63d4-105">Lorsque les suites de chiffrement par défaut ne sont pas explicitement configurées, .NET sur Linux utilise une liste restreinte de suites de chiffrement autorisées.</span><span class="sxs-lookup"><span data-stu-id="a63d4-105">When default cipher suites aren't explicitly configured, .NET on Linux uses a tightly restricted list of permitted cipher suites.</span></span>

## <a name="change-description"></a><span data-ttu-id="a63d4-106">Description de la modification</span><span class="sxs-lookup"><span data-stu-id="a63d4-106">Change description</span></span>

<span data-ttu-id="a63d4-107">Dans les versions précédentes de .NET, .NET ne respecte pas la configuration du système pour les suites de chiffrement par défaut.</span><span class="sxs-lookup"><span data-stu-id="a63d4-107">In previous .NET versions, .NET does not respect system configuration for default cipher suites.</span></span> <span data-ttu-id="a63d4-108">La liste de suites de chiffrement par défaut pour .NET sur Linux est très permissive.</span><span class="sxs-lookup"><span data-stu-id="a63d4-108">The default cipher suite list for .NET on Linux is very permissive.</span></span>

<span data-ttu-id="a63d4-109">À compter de .NET 5,0, .NET sur Linux respecte la configuration OpenSSL pour les suites de chiffrement par défaut lorsqu’il est spécifié dans *OpenSSL. cnf*.</span><span class="sxs-lookup"><span data-stu-id="a63d4-109">Starting in .NET 5.0, .NET on Linux respects the OpenSSL configuration for default cipher suites when it's specified in *openssl.cnf*.</span></span> <span data-ttu-id="a63d4-110">Lorsque les suites de chiffrement ne sont pas explicitement configurées, les seules suites de chiffrement autorisées sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="a63d4-110">When cipher suites aren't explicitly configured, the only permitted cipher suites are as follows:</span></span>

- <span data-ttu-id="a63d4-111">Suites de chiffrement TLS 1,3</span><span class="sxs-lookup"><span data-stu-id="a63d4-111">TLS 1.3 cipher suites</span></span>
- <span data-ttu-id="a63d4-112">TLS_ECDHE_ECDSA_WITH_AES_256_GCM_SHA384</span><span class="sxs-lookup"><span data-stu-id="a63d4-112">TLS_ECDHE_ECDSA_WITH_AES_256_GCM_SHA384</span></span>
- <span data-ttu-id="a63d4-113">TLS_ECDHE_ECDSA_WITH_AES_128_GCM_SHA256</span><span class="sxs-lookup"><span data-stu-id="a63d4-113">TLS_ECDHE_ECDSA_WITH_AES_128_GCM_SHA256</span></span>
- <span data-ttu-id="a63d4-114">TLS_ECDHE_RSA_WITH_AES_256_GCM_SHA384</span><span class="sxs-lookup"><span data-stu-id="a63d4-114">TLS_ECDHE_RSA_WITH_AES_256_GCM_SHA384</span></span>
- <span data-ttu-id="a63d4-115">TLS_ECDHE_RSA_WITH_AES_128_GCM_SHA256</span><span class="sxs-lookup"><span data-stu-id="a63d4-115">TLS_ECDHE_RSA_WITH_AES_128_GCM_SHA256</span></span>
- <span data-ttu-id="a63d4-116">TLS_ECDHE_ECDSA_WITH_AES_256_CBC_SHA384</span><span class="sxs-lookup"><span data-stu-id="a63d4-116">TLS_ECDHE_ECDSA_WITH_AES_256_CBC_SHA384</span></span>
- <span data-ttu-id="a63d4-117">TLS_ECDHE_ECDSA_WITH_AES_128_CBC_SHA256</span><span class="sxs-lookup"><span data-stu-id="a63d4-117">TLS_ECDHE_ECDSA_WITH_AES_128_CBC_SHA256</span></span>
- <span data-ttu-id="a63d4-118">TLS_ECDHE_RSA_WITH_AES_256_CBC_SHA384</span><span class="sxs-lookup"><span data-stu-id="a63d4-118">TLS_ECDHE_RSA_WITH_AES_256_CBC_SHA384</span></span>
- <span data-ttu-id="a63d4-119">TLS_ECDHE_RSA_WITH_AES_128_CBC_SHA256</span><span class="sxs-lookup"><span data-stu-id="a63d4-119">TLS_ECDHE_RSA_WITH_AES_128_CBC_SHA256</span></span>

<span data-ttu-id="a63d4-120">Étant donné que cette valeur par défaut de secours n’inclut aucune suite de chiffrement compatible avec TLS 1,0 ou TLS 1,1, ces anciennes versions de protocole sont effectivement désactivées par défaut.</span><span class="sxs-lookup"><span data-stu-id="a63d4-120">Since this fallback default doesn't include any cipher suites that are compatible with TLS 1.0 or TLS 1.1, these older protocol versions are effectively disabled by default.</span></span>

<span data-ttu-id="a63d4-121">La spécification d’une valeur CipherSuitePolicy à SslStream pour une session spécifique remplacera toujours le contenu du fichier de configuration et/ou la valeur par défaut de secours .NET.</span><span class="sxs-lookup"><span data-stu-id="a63d4-121">Supplying a CipherSuitePolicy value to SslStream for a specific session will still replace the configuration file content and/or .NET fallback default.</span></span>

## <a name="reason-for-change"></a><span data-ttu-id="a63d4-122">Motif de modification</span><span class="sxs-lookup"><span data-stu-id="a63d4-122">Reason for change</span></span>

<span data-ttu-id="a63d4-123">Les utilisateurs qui exécutent .NET sur Linux ont demandé que la configuration par défaut <xref:System.Net.Security.SslStream> soit remplacée par une valeur qui fournissait un niveau de sécurité élevé à partir d’outils d’évaluation tiers.</span><span class="sxs-lookup"><span data-stu-id="a63d4-123">Users running .NET on Linux requested that the default configuration for <xref:System.Net.Security.SslStream> be changed to one that provided a high security rating from third-party assessment tools.</span></span>

## <a name="version-introduced"></a><span data-ttu-id="a63d4-124">Version introduite</span><span class="sxs-lookup"><span data-stu-id="a63d4-124">Version introduced</span></span>

<span data-ttu-id="a63d4-125">5.0</span><span class="sxs-lookup"><span data-stu-id="a63d4-125">5.0</span></span>

## <a name="recommended-action"></a><span data-ttu-id="a63d4-126">Action recommandée</span><span class="sxs-lookup"><span data-stu-id="a63d4-126">Recommended action</span></span>

<span data-ttu-id="a63d4-127">Les nouvelles valeurs par défaut sont susceptibles de fonctionner lors de la communication avec les clients ou serveurs modernes.</span><span class="sxs-lookup"><span data-stu-id="a63d4-127">The new defaults are likely to work when communicating with modern clients or servers.</span></span> <span data-ttu-id="a63d4-128">Si vous devez développer la liste des suites de chiffrement par défaut pour accepter les clients hérités (ou pour contacter les serveurs hérités), spécifiez une `CipherSuitePolicy` valeur ou modifiez le fichier de configuration OpenSSL.</span><span class="sxs-lookup"><span data-stu-id="a63d4-128">If you need to expand the default cipher suite list to accept legacy clients (or to contact legacy servers), either specify a `CipherSuitePolicy` value or change the OpenSSL configuration file.</span></span> <span data-ttu-id="a63d4-129">Dans de nombreuses distributions Linux, le fichier de configuration OpenSSL se trouve sur */etc/SSL/OpenSSL.cnf*.</span><span class="sxs-lookup"><span data-stu-id="a63d4-129">On many Linux distributions, the OpenSSL configuration file is at */etc/ssl/openssl.cnf*.</span></span>

<span data-ttu-id="a63d4-130">Cet exemple de fichier *OpenSSL. cnf* est un fichier minimal équivalent à la stratégie de suites de chiffrement par défaut pour .net 5,0 et versions ultérieures sur Linux.</span><span class="sxs-lookup"><span data-stu-id="a63d4-130">This sample *openssl.cnf* file is a minimal file that's equivalent to the default cipher suites policy for .NET 5.0 and later on Linux.</span></span> <span data-ttu-id="a63d4-131">Au lieu de remplacer le fichier système, fusionnez ces concepts avec le fichier présent sur votre système.</span><span class="sxs-lookup"><span data-stu-id="a63d4-131">Instead of replacing the system file, merge these concepts with the file that's present on your system.</span></span>

```ini
openssl_conf = default_conf

[default_conf]
ssl_conf = ssl_sect

[ssl_sect]
system_default = system_default_sect

[system_default_sect]
CipherString = ECDHE-ECDSA-AES256-GCM-SHA384:ECDHE-ECDSA-AES128-GCM-SHA256:ECDHE-RSA-AES256-GCM-SHA384:ECDHE-RSA-AES128-GCM-SHA256:ECDHE-ECDSA-AES256-SHA384:ECDHE-ECDSA-AES128-SHA256:ECDHE-RSA-AES256-SHA384:ECDHE-RSA-AES128-SHA256
```

<span data-ttu-id="a63d4-132">Sur les distributions Red Hat Enterprise Linux, CentOS et Fedora, les applications .NET ont par défaut les suites de chiffrement autorisées par les stratégies de chiffrement à l’ensemble du système.</span><span class="sxs-lookup"><span data-stu-id="a63d4-132">On the Red Hat Enterprise Linux, CentOS, and Fedora distributions, .NET applications default to the cipher suites permitted by the system-wide cryptographic policies.</span></span> <span data-ttu-id="a63d4-133">Sur ces distributions, utilisez la configuration des stratégies de chiffrement au lieu de *OpenSSL. cnf*.</span><span class="sxs-lookup"><span data-stu-id="a63d4-133">On these distributions, use the crypto-policies configuration instead of *openssl.cnf*.</span></span>

## <a name="affected-apis"></a><span data-ttu-id="a63d4-134">API affectées</span><span class="sxs-lookup"><span data-stu-id="a63d4-134">Affected APIs</span></span>

<span data-ttu-id="a63d4-135">Non detectible via l’analyse des API.</span><span class="sxs-lookup"><span data-stu-id="a63d4-135">Not detectible via API analysis.</span></span>

<!--

### Affected APIs

- Not detectible via API analysis.

### Category

- Cryptography
- Security

-->
