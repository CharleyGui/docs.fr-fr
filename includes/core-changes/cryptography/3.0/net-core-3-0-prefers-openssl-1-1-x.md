---
ms.openlocfilehash: 877f9d99b660c4af843e4d8d525219c1df6c99a9
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/20/2020
ms.locfileid: "83721456"
---
### <a name="net-core-30-prefers-openssl-11x-to-openssl-10x"></a><span data-ttu-id="24b87-101">.NET Core 3,0 préfère OpenSSL 1.1. x à OpenSSL 1.0. x</span><span class="sxs-lookup"><span data-stu-id="24b87-101">.NET Core 3.0 prefers OpenSSL 1.1.x to OpenSSL 1.0.x</span></span>

<span data-ttu-id="24b87-102">.NET Core pour Linux, qui fonctionne sur plusieurs distributions Linux, peut prendre en charge à la fois OpenSSL 1.0. x et OpenSSL 1.1. x.</span><span class="sxs-lookup"><span data-stu-id="24b87-102">.NET Core for Linux, which works across multiple Linux distributions, can support both OpenSSL 1.0.x and OpenSSL 1.1.x.</span></span>  <span data-ttu-id="24b87-103">.NET Core 2,1 et .NET Core 2,2 recherchent 1.0. x en premier, puis reviennent à 1.1. x ; .NET Core 3,0 recherche 1.1. x en premier.</span><span class="sxs-lookup"><span data-stu-id="24b87-103">.NET Core 2.1 and .NET Core 2.2 look for 1.0.x first, then fall back to 1.1.x; .NET Core 3.0 looks for 1.1.x first.</span></span> <span data-ttu-id="24b87-104">Cette modification a été apportée pour ajouter la prise en charge de nouvelles normes de chiffrement.</span><span class="sxs-lookup"><span data-stu-id="24b87-104">This change was made to add support for new cryptographic standards.</span></span>

<span data-ttu-id="24b87-105">Cette modification peut avoir un impact sur les bibliothèques ou les applications qui effectuent une interopérabilité de la plateforme avec les types d’interopérabilité spécifiques à OpenSSL dans .NET Core.</span><span class="sxs-lookup"><span data-stu-id="24b87-105">This change may impact libraries or applications that do platform interop with the OpenSSL-specific interop types in .NET Core.</span></span>

#### <a name="change-description"></a><span data-ttu-id="24b87-106">Description de la modification</span><span class="sxs-lookup"><span data-stu-id="24b87-106">Change description</span></span>

<span data-ttu-id="24b87-107">Dans .NET Core 2,2 et versions antérieures, le runtime préfère charger OpenSSL 1.0. x sur 1.1. x.</span><span class="sxs-lookup"><span data-stu-id="24b87-107">In .NET Core 2.2 and earlier versions, the runtime prefers loading OpenSSL 1.0.x over 1.1.x.</span></span> <span data-ttu-id="24b87-108">Cela signifie que les <xref:System.IntPtr> <xref:System.Runtime.InteropServices.SafeHandle> types et pour l’interopérabilité avec OpenSSL sont utilisés avec libénigmatique. so. 1.0.0/libénigmatique. so. 1,0/libénigmatique. so. 10 par préférence.</span><span class="sxs-lookup"><span data-stu-id="24b87-108">This means that the <xref:System.IntPtr> and <xref:System.Runtime.InteropServices.SafeHandle> types for interop with OpenSSL are used with libcrypto.so.1.0.0 / libcrypto.so.1.0 / libcrypto.so.10 by preference.</span></span>

<span data-ttu-id="24b87-109">À compter de .NET Core 3,0, le runtime préfère le chargement d’OpenSSL 1.1. x sur OpenSSL 1.0. x. par conséquent, les <xref:System.IntPtr> <xref:System.Runtime.InteropServices.SafeHandle> types et pour l’interopérabilité avec OpenSSL sont utilisés avec libénigmatique. so. 1.1/libénigmatique. so. 11/libénigmatique. so. 1.1.0/libénigmatique. so. 1.1.1 par préférence.</span><span class="sxs-lookup"><span data-stu-id="24b87-109">Starting with .NET Core 3.0, the runtime prefers loading OpenSSL 1.1.x over OpenSSL 1.0.x, so the <xref:System.IntPtr> and <xref:System.Runtime.InteropServices.SafeHandle> types for interop with OpenSSL are used with libcrypto.so.1.1 / libcrypto.so.11 / libcrypto.so.1.1.0 / libcrypto.so.1.1.1 by preference.</span></span> <span data-ttu-id="24b87-110">Par conséquent, les bibliothèques et les applications qui interagissent directement avec OpenSSL peuvent avoir des pointeurs incompatibles avec les valeurs .NET Core exposées lors de la mise à niveau à partir de .NET Core 2,1 ou .NET Core 2,2.</span><span class="sxs-lookup"><span data-stu-id="24b87-110">As a result, libraries and applications that interoperate with OpenSSL directly may have incompatible pointers with the .NET Core-exposed values when upgrading from .NET Core 2.1 or .NET Core 2.2.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="24b87-111">Version introduite</span><span class="sxs-lookup"><span data-stu-id="24b87-111">Version introduced</span></span>

<span data-ttu-id="24b87-112">3.0</span><span class="sxs-lookup"><span data-stu-id="24b87-112">3.0</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="24b87-113">Action recommandée</span><span class="sxs-lookup"><span data-stu-id="24b87-113">Recommended action</span></span>

<span data-ttu-id="24b87-114">Les bibliothèques et les applications qui effectuent des opérations directes avec OpenSSL doivent veiller à ce qu’elles utilisent la même version d’OpenSSL que le Runtime .NET Core.</span><span class="sxs-lookup"><span data-stu-id="24b87-114">Libraries and applications that do direct operations with OpenSSL need to be careful to ensure they are using the same version of OpenSSL as the .NET Core runtime.</span></span>

<span data-ttu-id="24b87-115">Toutes les bibliothèques ou applications qui utilisent <xref:System.IntPtr> ou <xref:System.Runtime.InteropServices.SafeHandle> les valeurs des types de chiffrement .net Core directement avec OpenSSL doivent comparer la version de la bibliothèque qu’ils utilisent avec la nouvelle <xref:System.Security.Cryptography.SafeEvpPKeyHandle.OpenSslVersion?displayProperty=nameWithType> propriété pour garantir la compatibilité des pointeurs.</span><span class="sxs-lookup"><span data-stu-id="24b87-115">All libraries or applications that use <xref:System.IntPtr> or <xref:System.Runtime.InteropServices.SafeHandle> values from the .NET Core cryptographic types directly with OpenSSL should compare the version of the library they use with the new <xref:System.Security.Cryptography.SafeEvpPKeyHandle.OpenSslVersion?displayProperty=nameWithType> property to ensure the pointers are compatible.</span></span>

#### <a name="category"></a><span data-ttu-id="24b87-116">Category</span><span class="sxs-lookup"><span data-stu-id="24b87-116">Category</span></span>

<span data-ttu-id="24b87-117">Chiffrement</span><span class="sxs-lookup"><span data-stu-id="24b87-117">Cryptography</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="24b87-118">API affectées</span><span class="sxs-lookup"><span data-stu-id="24b87-118">Affected APIs</span></span>

- <xref:System.Security.Cryptography.SafeEvpPKeyHandle.%23ctor%2A>
- <xref:System.Security.Cryptography.RSAOpenSsl.%23ctor(System.IntPtr)>
- <xref:System.Security.Cryptography.RSAOpenSsl.%23ctor(System.Security.Cryptography.SafeEvpPKeyHandle)>
- <xref:System.Security.Cryptography.RSAOpenSsl.DuplicateKeyHandle?displayProperty=nameWithType>
- <xref:System.Security.Cryptography.DSAOpenSsl.%23ctor(System.IntPtr)>
- <xref:System.Security.Cryptography.DSAOpenSsl.%23ctor(System.Security.Cryptography.SafeEvpPKeyHandle)>
- <xref:System.Security.Cryptography.DSAOpenSsl.DuplicateKeyHandle?displayProperty=nameWithType>
- <xref:System.Security.Cryptography.ECDsaOpenSsl.%23ctor(System.IntPtr)>
- <xref:System.Security.Cryptography.ECDsaOpenSsl.%23ctor(System.Security.Cryptography.SafeEvpPKeyHandle)>
- <xref:System.Security.Cryptography.ECDsaOpenSsl.DuplicateKeyHandle?displayProperty=nameWithType>
- <xref:System.Security.Cryptography.ECDiffieHellmanOpenSsl.%23ctor(System.IntPtr)>
- <xref:System.Security.Cryptography.ECDiffieHellmanOpenSsl.%23ctor(System.Security.Cryptography.SafeEvpPKeyHandle)>
- <xref:System.Security.Cryptography.ECDiffieHellmanOpenSsl.DuplicateKeyHandle?displayProperty=nameWithType>
- <xref:System.Security.Cryptography.X509Certificates.X509Certificate.Handle?displayProperty=nameWithType>

<!--

#### Affected APIs

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
