---
ms.openlocfilehash: b49b2f88b130bb952b77964d5bf38374dc606385
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "74567980"
---
### <a name="net-core-30-prefers-openssl-11x-to-openssl-10x"></a><span data-ttu-id="0a390-101">.NET Core 3.0 préfère OpenSSL 1.1.x à OpenSSL 1.0.x</span><span class="sxs-lookup"><span data-stu-id="0a390-101">.NET Core 3.0 prefers OpenSSL 1.1.x to OpenSSL 1.0.x</span></span>

<span data-ttu-id="0a390-102">.NET Core pour Linux, qui fonctionne à travers plusieurs distributions Linux, peut prendre en charge à la fois OpenSSL 1.0.x et OpenSSL 1.1.x.</span><span class="sxs-lookup"><span data-stu-id="0a390-102">.NET Core for Linux, which works across multiple Linux distributions, can support both OpenSSL 1.0.x and OpenSSL 1.1.x.</span></span>  <span data-ttu-id="0a390-103">.NET Core 2.1 et .NET Core 2.2 look for 1.0.x first, then fall back to 1.1.x; .NET Core 3.0 looks for 1.1.x first.</span><span class="sxs-lookup"><span data-stu-id="0a390-103">.NET Core 2.1 and .NET Core 2.2 look for 1.0.x first, then fall back to 1.1.x; .NET Core 3.0 looks for 1.1.x first.</span></span> <span data-ttu-id="0a390-104">Ce changement a été apporté pour renforcer les nouvelles normes cryptographiques.</span><span class="sxs-lookup"><span data-stu-id="0a390-104">This change was made to add support for new cryptographic standards.</span></span>

<span data-ttu-id="0a390-105">Ce changement peut avoir un impact sur les bibliothèques ou les applications qui ne plate-forme interop avec les types d’interops OpenSSL spécifiques dans .NET Core.</span><span class="sxs-lookup"><span data-stu-id="0a390-105">This change may impact libraries or applications that do platform interop with the OpenSSL-specific interop types in .NET Core.</span></span>

#### <a name="change-description"></a><span data-ttu-id="0a390-106">Description de la modification</span><span class="sxs-lookup"><span data-stu-id="0a390-106">Change description</span></span>

<span data-ttu-id="0a390-107">Dans .NET Core 2.2 et les versions antérieures, le temps d’exécution préfère charger OpenSSL 1.0.x sur 1.1.x.</span><span class="sxs-lookup"><span data-stu-id="0a390-107">In .NET Core 2.2 and earlier versions, the runtime prefers loading OpenSSL 1.0.x over 1.1.x.</span></span> <span data-ttu-id="0a390-108">Cela signifie <xref:System.IntPtr> que <xref:System.Runtime.InteropServices.SafeHandle> le et les types pour interop avec OpenSSL sont utilisés avec libcrypto.so.1.0.0 / libcrypto.so.1.0 / libcrypto.so.10 par préférence.</span><span class="sxs-lookup"><span data-stu-id="0a390-108">This means that the <xref:System.IntPtr> and <xref:System.Runtime.InteropServices.SafeHandle> types for interop with OpenSSL are used with libcrypto.so.1.0.0 / libcrypto.so.1.0 / libcrypto.so.10 by preference.</span></span>

<span data-ttu-id="0a390-109">À partir de .NET Core 3.0, l’heure d’exécution préfère charger OpenSSL 1.1.x <xref:System.IntPtr> sur <xref:System.Runtime.InteropServices.SafeHandle> OpenSSL 1.0.x, de sorte que le et les types pour interop avec OpenSSL sont utilisés avec libcrypto.so.1.1 / libcrypto.so.11 / libcrypto.so.1.1 / libcrypto.so.1.0 / libcrypto.so.1.1 par préférence.</span><span class="sxs-lookup"><span data-stu-id="0a390-109">Starting with .NET Core 3.0, the runtime prefers loading OpenSSL 1.1.x over OpenSSL 1.0.x, so the <xref:System.IntPtr> and <xref:System.Runtime.InteropServices.SafeHandle> types for interop with OpenSSL are used with libcrypto.so.1.1 / libcrypto.so.11 / libcrypto.so.1.1.0 / libcrypto.so.1.1.1 by preference.</span></span> <span data-ttu-id="0a390-110">Par conséquent, les bibliothèques et les applications qui interopément avec OpenSSL directement peuvent avoir des indications incompatibles avec les valeurs .NET Core-exposed lors de la mise à niveau de .NET Core 2.1 ou .NET Core 2.2.</span><span class="sxs-lookup"><span data-stu-id="0a390-110">As a result, libraries and applications that interoperate with OpenSSL directly may have incompatible pointers with the .NET Core-exposed values when upgrading from .NET Core 2.1 or .NET Core 2.2.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="0a390-111">Version introduite</span><span class="sxs-lookup"><span data-stu-id="0a390-111">Version introduced</span></span>

<span data-ttu-id="0a390-112">3.0</span><span class="sxs-lookup"><span data-stu-id="0a390-112">3.0</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="0a390-113">Action recommandée</span><span class="sxs-lookup"><span data-stu-id="0a390-113">Recommended action</span></span>

<span data-ttu-id="0a390-114">Les bibliothèques et les applications qui font des opérations directes avec OpenSSL doivent être prudents pour s’assurer qu’ils utilisent la même version d’OpenSSL que le temps d’exécution .NET Core.</span><span class="sxs-lookup"><span data-stu-id="0a390-114">Libraries and applications that do direct operations with OpenSSL need to be careful to ensure they are using the same version of OpenSSL as the .NET Core runtime.</span></span>

<span data-ttu-id="0a390-115">Toutes les bibliothèques <xref:System.IntPtr> ou <xref:System.Runtime.InteropServices.SafeHandle> applications qui utilisent ou les valeurs des types cryptographiques .NET Core directement <xref:System.Security.Cryptography.SafeEvpPKeyHandle.OpenSslVersion?displayProperty=nameWithType> avec OpenSSL doivent comparer la version de la bibliothèque qu’ils utilisent avec la nouvelle propriété pour s’assurer que les pointeurs sont compatibles.</span><span class="sxs-lookup"><span data-stu-id="0a390-115">All libraries or applications that use <xref:System.IntPtr> or <xref:System.Runtime.InteropServices.SafeHandle> values from the .NET Core cryptographic types directly with OpenSSL should compare the version of the library they use with the new <xref:System.Security.Cryptography.SafeEvpPKeyHandle.OpenSslVersion?displayProperty=nameWithType> property to ensure the pointers are compatible.</span></span>

#### <a name="category"></a><span data-ttu-id="0a390-116">Category</span><span class="sxs-lookup"><span data-stu-id="0a390-116">Category</span></span>

<span data-ttu-id="0a390-117">Chiffrement</span><span class="sxs-lookup"><span data-stu-id="0a390-117">Cryptography</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="0a390-118">API affectées</span><span class="sxs-lookup"><span data-stu-id="0a390-118">Affected APIs</span></span>

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
