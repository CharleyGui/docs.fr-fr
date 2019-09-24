---
ms.openlocfilehash: b49b2f88b130bb952b77964d5bf38374dc606385
ms.sourcegitcommit: 56f1d1203d0075a461a10a301459d3aa452f4f47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2019
ms.locfileid: "71216397"
---
### <a name="net-core-30-prefers-openssl-11x-to-openssl-10x"></a><span data-ttu-id="aeaa1-101">.NET Core 3,0 préfère OpenSSL 1.1. x à OpenSSL 1.0. x</span><span class="sxs-lookup"><span data-stu-id="aeaa1-101">.NET Core 3.0 prefers OpenSSL 1.1.x to OpenSSL 1.0.x</span></span>

<span data-ttu-id="aeaa1-102">.NET Core pour Linux, qui fonctionne sur plusieurs distributions Linux, peut prendre en charge à la fois OpenSSL 1.0. x et OpenSSL 1.1. x.</span><span class="sxs-lookup"><span data-stu-id="aeaa1-102">.NET Core for Linux, which works across multiple Linux distributions, can support both OpenSSL 1.0.x and OpenSSL 1.1.x.</span></span>  <span data-ttu-id="aeaa1-103">.NET Core 2,1 et .NET Core 2,2 recherchent 1.0. x en premier, puis reviennent à 1.1. x ; .NET Core 3,0 recherche 1.1. x en premier.</span><span class="sxs-lookup"><span data-stu-id="aeaa1-103">.NET Core 2.1 and .NET Core 2.2 look for 1.0.x first, then fall back to 1.1.x; .NET Core 3.0 looks for 1.1.x first.</span></span> <span data-ttu-id="aeaa1-104">Cette modification a été apportée pour ajouter la prise en charge de nouvelles normes de chiffrement.</span><span class="sxs-lookup"><span data-stu-id="aeaa1-104">This change was made to add support for new cryptographic standards.</span></span>

<span data-ttu-id="aeaa1-105">Cette modification peut avoir un impact sur les bibliothèques ou les applications qui effectuent une interopérabilité de la plateforme avec les types d’interopérabilité spécifiques à OpenSSL dans .NET Core.</span><span class="sxs-lookup"><span data-stu-id="aeaa1-105">This change may impact libraries or applications that do platform interop with the OpenSSL-specific interop types in .NET Core.</span></span>

#### <a name="change-description"></a><span data-ttu-id="aeaa1-106">Modifier la description</span><span class="sxs-lookup"><span data-stu-id="aeaa1-106">Change description</span></span>

<span data-ttu-id="aeaa1-107">Dans .NET Core 2,2 et versions antérieures, le runtime préfère charger OpenSSL 1.0. x sur 1.1. x.</span><span class="sxs-lookup"><span data-stu-id="aeaa1-107">In .NET Core 2.2 and earlier versions, the runtime prefers loading OpenSSL 1.0.x over 1.1.x.</span></span> <span data-ttu-id="aeaa1-108">Cela signifie que les <xref:System.IntPtr> types <xref:System.Runtime.InteropServices.SafeHandle> et pour l’interopérabilité avec OpenSSL sont utilisés avec libénigmatique. so. 1.0.0/libénigmatique. so. 1,0/libénigmatique. so. 10 par préférence.</span><span class="sxs-lookup"><span data-stu-id="aeaa1-108">This means that the <xref:System.IntPtr> and <xref:System.Runtime.InteropServices.SafeHandle> types for interop with OpenSSL are used with libcrypto.so.1.0.0 / libcrypto.so.1.0 / libcrypto.so.10 by preference.</span></span>

<span data-ttu-id="aeaa1-109">À compter de .net Core 3,0, le runtime préfère le chargement d’OpenSSL 1.1. x sur OpenSSL 1.0. x. <xref:System.IntPtr> par <xref:System.Runtime.InteropServices.SafeHandle> conséquent, les types et pour l’interopérabilité avec OpenSSL sont utilisés avec libénigmatique. so. 1.1/libénigmatique. so. 11/libénigmatique. so. relatives.</span><span class="sxs-lookup"><span data-stu-id="aeaa1-109">Starting with .NET Core 3.0, the runtime prefers loading OpenSSL 1.1.x over OpenSSL 1.0.x, so the <xref:System.IntPtr> and <xref:System.Runtime.InteropServices.SafeHandle> types for interop with OpenSSL are used with libcrypto.so.1.1 / libcrypto.so.11 / libcrypto.so.1.1.0 / libcrypto.so.1.1.1 by preference.</span></span> <span data-ttu-id="aeaa1-110">Par conséquent, les bibliothèques et les applications qui interagissent directement avec OpenSSL peuvent avoir des pointeurs incompatibles avec les valeurs .NET Core exposées lors de la mise à niveau à partir de .NET Core 2,1 ou .NET Core 2,2.</span><span class="sxs-lookup"><span data-stu-id="aeaa1-110">As a result, libraries and applications that interoperate with OpenSSL directly may have incompatible pointers with the .NET Core-exposed values when upgrading from .NET Core 2.1 or .NET Core 2.2.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="aeaa1-111">Version introduite</span><span class="sxs-lookup"><span data-stu-id="aeaa1-111">Version introduced</span></span>

<span data-ttu-id="aeaa1-112">3.0</span><span class="sxs-lookup"><span data-stu-id="aeaa1-112">3.0</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="aeaa1-113">Action recommandée</span><span class="sxs-lookup"><span data-stu-id="aeaa1-113">Recommended action</span></span>

<span data-ttu-id="aeaa1-114">Les bibliothèques et les applications qui effectuent des opérations directes avec OpenSSL doivent veiller à ce qu’elles utilisent la même version d’OpenSSL que le Runtime .NET Core.</span><span class="sxs-lookup"><span data-stu-id="aeaa1-114">Libraries and applications that do direct operations with OpenSSL need to be careful to ensure they are using the same version of OpenSSL as the .NET Core runtime.</span></span>

<span data-ttu-id="aeaa1-115">Toutes les bibliothèques ou applications qui <xref:System.IntPtr> utilisent <xref:System.Runtime.InteropServices.SafeHandle> ou les valeurs des types de chiffrement .net Core directement avec OpenSSL doivent comparer la version de la bibliothèque qu’ils <xref:System.Security.Cryptography.SafeEvpPKeyHandle.OpenSslVersion?displayProperty=nameWithType> utilisent avec la nouvelle propriété pour s’assurer que les pointeurs sont conforme.</span><span class="sxs-lookup"><span data-stu-id="aeaa1-115">All libraries or applications that use <xref:System.IntPtr> or <xref:System.Runtime.InteropServices.SafeHandle> values from the .NET Core cryptographic types directly with OpenSSL should compare the version of the library they use with the new <xref:System.Security.Cryptography.SafeEvpPKeyHandle.OpenSslVersion?displayProperty=nameWithType> property to ensure the pointers are compatible.</span></span>

#### <a name="category"></a><span data-ttu-id="aeaa1-116">Category</span><span class="sxs-lookup"><span data-stu-id="aeaa1-116">Category</span></span>

<span data-ttu-id="aeaa1-117">Chiffrement</span><span class="sxs-lookup"><span data-stu-id="aeaa1-117">Cryptography</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="aeaa1-118">API affectées</span><span class="sxs-lookup"><span data-stu-id="aeaa1-118">Affected APIs</span></span>

- <xref:System.Security.Cryptography.SafeEvpPKeyHandle.%23ctor%2A?displayProperty=nameWithType>
- <xref:System.Security.Cryptography.RSAOpenSsl.%23ctor(System.IntPtr)?displayProperty=nameWithType>
- <xref:System.Security.Cryptography.RSAOpenSsl.%23ctor(System.Security.Cryptography.SafeEvpPKeyHandle)?displayProperty=nameWithType>
- <xref:System.Security.Cryptography.RSAOpenSsl.DuplicateKeyHandle?displayProperty=nameWithType>
- <xref:System.Security.Cryptography.DSAOpenSsl.%23ctor(System.IntPtr)?displayProperty=nameWithType>
- <xref:System.Security.Cryptography.DSAOpenSsl.%23ctor(System.Security.Cryptography.SafeEvpPKeyHandle)?displayProperty=nameWithType>
- <xref:System.Security.Cryptography.DSAOpenSsl.DuplicateKeyHandle?displayProperty=nameWithType>
- <xref:System.Security.Cryptography.ECDsaOpenSsl.%23ctor(System.IntPtr)?displayProperty=nameWithType>
- <xref:System.Security.Cryptography.ECDsaOpenSsl.%23ctor(System.Security.Cryptography.SafeEvpPKeyHandle)?displayProperty=nameWithType>
- <xref:System.Security.Cryptography.ECDsaOpenSsl.DuplicateKeyHandle?displayProperty=nameWithType>
- <xref:System.Security.Cryptography.ECDiffieHellmanOpenSsl.%23ctor(System.IntPtr)?displayProperty=nameWithType>
- <xref:System.Security.Cryptography.ECDiffieHellmanOpenSsl.%23ctor(System.Security.Cryptography.SafeEvpPKeyHandle)?displayProperty=nameWithType>
- <xref:System.Security.Cryptography.ECDiffieHellmanOpenSsl.DuplicateKeyHandle?displayProperty=nameWithType>
- <xref:System.Security.Cryptography.X509Certificates.X509Certificate.Handle?displayProperty=nameWithType>

<!--

### Affected APIs

- `Overload:System.Security.Cryptography.SafeEvpPKeyHandle.#ctor`
- `M:System.Security.Cryptography.RSAOpenSsl.#ctor(System.IntPtr)`
- `M:System.Security.Cryptography.RSAOpenSsl.#ctor(System.Security.Cryptography.SafeEvpPKeyHandle)`
- `M:System.Security.Cryptography.RSAOpenSsl.DuplicateKeyHandle`
- `M:System.Security.Cryptography.DSAOpenSsl.#ctor(System.IntPtr)`
- `M:System.Security.Cryptography.DSAOpenSsl.#ctor(System.Security.Cryptography.SafeEvpPKeyHandle)`
- `M:System.Security.Cryptography.DSAOpenSsl.DuplicateKeyHandle`
- `M:System.Security.Cryptography.ECDsaOpenSsl.#ctor(System.IntPtr)`
- `M:System.Security.Cryptography.ECDsaOpenSsl.#ctor(System.Security.CryptographySafeEvpPKeyHandle)`
- `M:System.Security.Cryptography.ECDsaOpenSsl.DuplicateKeyHandle`
- `M:System.Security.Cryptography.ECDiffieHellmanOpenSsl.#ctor(System.IntPtr)`
- `M:System.Security.Cryptography.ECDiffieHellmanOpenSsl.#ctor(System.Security.Cryptography.SafeEvpPKeyHandle)`
- `M:System.Security.Cryptography.ECDiffieHellmanOpenSsl.DuplicateKeyHandle`
- `P:System.Security.Cryptography.X509Certificates.X509Certificate.Handle`

-->
