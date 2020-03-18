---
ms.openlocfilehash: 6a5cd260a2820e2a81142f6d55e32e91173ca503
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79147449"
---
### <a name="openssl-versions-on-macos"></a><span data-ttu-id="c2cd2-101">Versions OpenSSL sur macOS</span><span class="sxs-lookup"><span data-stu-id="c2cd2-101">OpenSSL versions on macOS</span></span>

<span data-ttu-id="c2cd2-102">Le .NET Core 3.0 et les temps d’exécution plus tard sur macOS préfèrent maintenant OpenSSL 1.1.x <xref:System.Security.Cryptography.AesCcm> <xref:System.Security.Cryptography.AesGcm>versions à OpenSSL 1.0.x versions pour le , , <xref:System.Security.Cryptography.DSAOpenSsl>, <xref:System.Security.Cryptography.ECDiffieHellmanOpenSsl> <xref:System.Security.Cryptography.ECDsaOpenSsl>, , <xref:System.Security.Cryptography.RSAOpenSsl>et <xref:System.Security.Cryptography.SafeEvpPKeyHandle> les types.</span><span class="sxs-lookup"><span data-stu-id="c2cd2-102">The .NET Core 3.0 and later runtimes on macOS now prefer OpenSSL 1.1.x versions to OpenSSL 1.0.x versions for the <xref:System.Security.Cryptography.AesCcm>, <xref:System.Security.Cryptography.AesGcm>, <xref:System.Security.Cryptography.DSAOpenSsl>, <xref:System.Security.Cryptography.ECDiffieHellmanOpenSsl>, <xref:System.Security.Cryptography.ECDsaOpenSsl>, <xref:System.Security.Cryptography.RSAOpenSsl>, and <xref:System.Security.Cryptography.SafeEvpPKeyHandle> types.</span></span>

<span data-ttu-id="c2cd2-103">Le temps d’exécution .NET Core 2.1 prend désormais en charge les versions OpenSSL 1.1.x, mais préfère toujours les versions OpenSSL 1.0.x.</span><span class="sxs-lookup"><span data-stu-id="c2cd2-103">The .NET Core 2.1 runtime now supports OpenSSL 1.1.x versions, but still prefers OpenSSL 1.0.x versions.</span></span>

#### <a name="change-description"></a><span data-ttu-id="c2cd2-104">Description de la modification</span><span class="sxs-lookup"><span data-stu-id="c2cd2-104">Change description</span></span>

<span data-ttu-id="c2cd2-105">Auparavant, le temps d’exécution .NET Core utilisé OpenSSL 1.0.x versions sur macOS pour les types qui interagissent avec OpenSSL.</span><span class="sxs-lookup"><span data-stu-id="c2cd2-105">Previously, the .NET Core runtime used OpenSSL 1.0.x versions on macOS for types that interact with OpenSSL.</span></span> <span data-ttu-id="c2cd2-106">La plus récente version OpenSSL 1.0.x, OpenSSL 1.0.2, est maintenant hors de support.</span><span class="sxs-lookup"><span data-stu-id="c2cd2-106">The most recent OpenSSL 1.0.x version, OpenSSL 1.0.2, is now out of support.</span></span> <span data-ttu-id="c2cd2-107">Pour conserver les types qui utilisent OpenSSL sur les versions prises en charge d’OpenSSL, le .NET Core 3.0 et les temps d’exécution ultérieurs utilisent maintenant de nouvelles versions d’OpenSSL sur macOS.</span><span class="sxs-lookup"><span data-stu-id="c2cd2-107">To keep types that use OpenSSL on supported versions of OpenSSL, the .NET Core 3.0 and later runtimes now use newer versions of OpenSSL on macOS.</span></span>

<span data-ttu-id="c2cd2-108">Avec ce changement, le comportement pour les runtimes .NET Core sur macOS est le suivant:</span><span class="sxs-lookup"><span data-stu-id="c2cd2-108">With this change, the behavior for the .NET Core runtimes on macOS is as follows:</span></span>

- <span data-ttu-id="c2cd2-109">Les temps d’exécution .NET Core 3.0 et plus tard de version utilisent OpenSSL 1.1.x, si disponible, et retomber à OpenSSL 1.0.x seulement s’il n’y a pas de version 1.1.x disponible.</span><span class="sxs-lookup"><span data-stu-id="c2cd2-109">The .NET Core 3.0 and later version runtimes use OpenSSL 1.1.x, if available, and fall back to OpenSSL 1.0.x only if there's no 1.1.x version available.</span></span>

  <span data-ttu-id="c2cd2-110">Pour les appelants qui utilisent les types d’interop OpenSSL <xref:System.Security.Cryptography.SafeEvpPKeyHandle.OpenSslVersion?displayProperty=nameWithType> avec P/Invokes personnalisés, suivez les conseils dans les remarques.</span><span class="sxs-lookup"><span data-stu-id="c2cd2-110">For callers that use the OpenSSL interop types with custom P/Invokes, follow the guidance in the <xref:System.Security.Cryptography.SafeEvpPKeyHandle.OpenSslVersion?displayProperty=nameWithType> remarks.</span></span> <span data-ttu-id="c2cd2-111">Votre application peut se planter si <xref:System.Security.Cryptography.SafeEvpPKeyHandle.OpenSslVersion> vous ne vérifiez pas la valeur.</span><span class="sxs-lookup"><span data-stu-id="c2cd2-111">Your app may crash if you don't check the <xref:System.Security.Cryptography.SafeEvpPKeyHandle.OpenSslVersion> value.</span></span>

- <span data-ttu-id="c2cd2-112">Le temps d’exécution .NET Core 2.1 utilise OpenSSL 1.0.x, si disponible, et retombe à OpenSSL 1.1.x s’il n’y a pas de version 1.0.x disponible.</span><span class="sxs-lookup"><span data-stu-id="c2cd2-112">The .NET Core 2.1 runtime uses OpenSSL 1.0.x, if available, and falls back to OpenSSL 1.1.x if there's no 1.0.x version available.</span></span>

  <span data-ttu-id="c2cd2-113">Le temps d’exécution 2.1 préfère la version <xref:System.Security.Cryptography.SafeEvpPKeyHandle.OpenSslVersion?displayProperty=nameWithType> antérieure d’OpenSSL parce que la propriété n’existe pas en .NET Core 2.1, de sorte que la version OpenSSL ne peut pas être déterminée de façon fiable à l’heure d’exécution.</span><span class="sxs-lookup"><span data-stu-id="c2cd2-113">The 2.1 runtime prefers the earlier version of OpenSSL because the <xref:System.Security.Cryptography.SafeEvpPKeyHandle.OpenSslVersion?displayProperty=nameWithType> property does not exist in .NET Core 2.1, so the OpenSSL version cannot be reliably determined at run time.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="c2cd2-114">Version introduite</span><span class="sxs-lookup"><span data-stu-id="c2cd2-114">Version introduced</span></span>

- <span data-ttu-id="c2cd2-115">.NET Core 2.1.16</span><span class="sxs-lookup"><span data-stu-id="c2cd2-115">.NET Core 2.1.16</span></span>
- <span data-ttu-id="c2cd2-116">.NET Core 3.0.3</span><span class="sxs-lookup"><span data-stu-id="c2cd2-116">.NET Core 3.0.3</span></span>
- <span data-ttu-id="c2cd2-117">.NET Core 3.1.2</span><span class="sxs-lookup"><span data-stu-id="c2cd2-117">.NET Core 3.1.2</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="c2cd2-118">Action recommandée</span><span class="sxs-lookup"><span data-stu-id="c2cd2-118">Recommended action</span></span>

- <span data-ttu-id="c2cd2-119">Désinstaller la version OpenSSL 1.0.2 si elle n’est plus nécessaire.</span><span class="sxs-lookup"><span data-stu-id="c2cd2-119">Uninstall OpenSSL version 1.0.2 if it's no longer needed.</span></span>

- <span data-ttu-id="c2cd2-120">Installez OpenSSL 1.1.x <xref:System.Security.Cryptography.AesCcm>si <xref:System.Security.Cryptography.AesGcm> <xref:System.Security.Cryptography.DSAOpenSsl>vous <xref:System.Security.Cryptography.ECDiffieHellmanOpenSsl> <xref:System.Security.Cryptography.ECDsaOpenSsl>utilisez <xref:System.Security.Cryptography.RSAOpenSsl>le <xref:System.Security.Cryptography.SafeEvpPKeyHandle> , , , , , ou les types.</span><span class="sxs-lookup"><span data-stu-id="c2cd2-120">Install OpenSSL 1.1.x if you use the <xref:System.Security.Cryptography.AesCcm>, <xref:System.Security.Cryptography.AesGcm>, <xref:System.Security.Cryptography.DSAOpenSsl>, <xref:System.Security.Cryptography.ECDiffieHellmanOpenSsl>, <xref:System.Security.Cryptography.ECDsaOpenSsl>, <xref:System.Security.Cryptography.RSAOpenSsl>, or <xref:System.Security.Cryptography.SafeEvpPKeyHandle> types.</span></span>

- <span data-ttu-id="c2cd2-121">Si vous utilisez les types d’interop OpenSSL avec P/Invokes personnalisés, suivez les conseils dans les <xref:System.Security.Cryptography.SafeEvpPKeyHandle.OpenSslVersion?displayProperty=nameWithType> remarques.</span><span class="sxs-lookup"><span data-stu-id="c2cd2-121">If you use the OpenSSL interop types with custom P/Invokes, follow the guidance in the <xref:System.Security.Cryptography.SafeEvpPKeyHandle.OpenSslVersion?displayProperty=nameWithType> remarks.</span></span>

#### <a name="category"></a><span data-ttu-id="c2cd2-122">Category</span><span class="sxs-lookup"><span data-stu-id="c2cd2-122">Category</span></span>

<span data-ttu-id="c2cd2-123">CoreFx</span><span class="sxs-lookup"><span data-stu-id="c2cd2-123">CoreFx</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="c2cd2-124">API affectées</span><span class="sxs-lookup"><span data-stu-id="c2cd2-124">Affected APIs</span></span>

- <xref:System.Security.Cryptography.AesCcm?displayProperty=fullName>
- <xref:System.Security.Cryptography.AesGcm?displayProperty=fullName>
- <xref:System.Security.Cryptography.DSAOpenSsl?displayProperty=fullName>
- <xref:System.Security.Cryptography.ECDiffieHellmanOpenSsl?displayProperty=fullName>
- <xref:System.Security.Cryptography.ECDsaOpenSsl?displayProperty=fullName>
- <xref:System.Security.Cryptography.RSAOpenSsl?displayProperty=fullName>
- <xref:System.Security.Cryptography.SafeEvpPKeyHandle?displayProperty=fullName>

<!--

### Affected APIs

- `T:System.Security.Cryptography.AesCcm``
- `T:System.Security.Cryptography.AesGcm`
- `T:System.Security.Cryptography.DSAOpenSsl`
- `T:System.Security.Cryptography.ECDiffieHellmanOpenSsl`
- `T:System.Security.Cryptography.ECDsaOpenSsl`
- `T:System.Security.Cryptography.RSAOpenSsl`
- `T:System.Security.Cryptography.SafeEvpPKeyHandle`

-->
