---
ms.openlocfilehash: a4476fbff572c004632153e5a98812c241efca57
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/20/2020
ms.locfileid: "83721435"
---
### <a name="openssl-versions-on-macos"></a><span data-ttu-id="44401-101">Versions OpenSSL sur macOS</span><span class="sxs-lookup"><span data-stu-id="44401-101">OpenSSL versions on macOS</span></span>

<span data-ttu-id="44401-102">Les runtimes .net Core 3,0 et versions ultérieures sur MacOS préfèrent désormais les versions d’OpenSSL 1.1. x aux versions d’OpenSSL 1.0. x pour les <xref:System.Security.Cryptography.AesCcm> <xref:System.Security.Cryptography.AesGcm> types,, <xref:System.Security.Cryptography.DSAOpenSsl> , <xref:System.Security.Cryptography.ECDiffieHellmanOpenSsl> ,, <xref:System.Security.Cryptography.ECDsaOpenSsl> <xref:System.Security.Cryptography.RSAOpenSsl> et <xref:System.Security.Cryptography.SafeEvpPKeyHandle> .</span><span class="sxs-lookup"><span data-stu-id="44401-102">The .NET Core 3.0 and later runtimes on macOS now prefer OpenSSL 1.1.x versions to OpenSSL 1.0.x versions for the <xref:System.Security.Cryptography.AesCcm>, <xref:System.Security.Cryptography.AesGcm>, <xref:System.Security.Cryptography.DSAOpenSsl>, <xref:System.Security.Cryptography.ECDiffieHellmanOpenSsl>, <xref:System.Security.Cryptography.ECDsaOpenSsl>, <xref:System.Security.Cryptography.RSAOpenSsl>, and <xref:System.Security.Cryptography.SafeEvpPKeyHandle> types.</span></span>

<span data-ttu-id="44401-103">Le Runtime .NET Core 2,1 prend désormais en charge les versions d’OpenSSL 1.1. x, mais il préfère toujours les versions d’OpenSSL 1.0. x.</span><span class="sxs-lookup"><span data-stu-id="44401-103">The .NET Core 2.1 runtime now supports OpenSSL 1.1.x versions, but still prefers OpenSSL 1.0.x versions.</span></span>

#### <a name="change-description"></a><span data-ttu-id="44401-104">Description de la modification</span><span class="sxs-lookup"><span data-stu-id="44401-104">Change description</span></span>

<span data-ttu-id="44401-105">Auparavant, le Runtime .NET Core utilisait des versions d’OpenSSL 1.0. x sur macOS pour les types qui interagissent avec OpenSSL.</span><span class="sxs-lookup"><span data-stu-id="44401-105">Previously, the .NET Core runtime used OpenSSL 1.0.x versions on macOS for types that interact with OpenSSL.</span></span> <span data-ttu-id="44401-106">La version la plus récente d’OpenSSL 1.0. x, OpenSSL 1.0.2, n’est plus prise en charge.</span><span class="sxs-lookup"><span data-stu-id="44401-106">The most recent OpenSSL 1.0.x version, OpenSSL 1.0.2, is now out of support.</span></span> <span data-ttu-id="44401-107">Pour conserver les types qui utilisent OpenSSL sur les versions prises en charge d’OpenSSL, les runtimes .NET Core 3,0 et versions ultérieures utilisent désormais des versions plus récentes de OpenSSL sur macOS.</span><span class="sxs-lookup"><span data-stu-id="44401-107">To keep types that use OpenSSL on supported versions of OpenSSL, the .NET Core 3.0 and later runtimes now use newer versions of OpenSSL on macOS.</span></span>

<span data-ttu-id="44401-108">Avec cette modification, le comportement des runtimes .NET Core sur macOS est le suivant :</span><span class="sxs-lookup"><span data-stu-id="44401-108">With this change, the behavior for the .NET Core runtimes on macOS is as follows:</span></span>

- <span data-ttu-id="44401-109">Les runtimes .NET Core 3,0 et versions ultérieures utilisent OpenSSL 1.1. x, s’ils sont disponibles, et reviennent à OpenSSL 1.0. x uniquement si aucune version 1.1. x n’est disponible.</span><span class="sxs-lookup"><span data-stu-id="44401-109">The .NET Core 3.0 and later version runtimes use OpenSSL 1.1.x, if available, and fall back to OpenSSL 1.0.x only if there's no 1.1.x version available.</span></span>

  <span data-ttu-id="44401-110">Pour les appelants qui utilisent les types d’interopérabilité OpenSSL avec des P/Invoke personnalisés, suivez les instructions des <xref:System.Security.Cryptography.SafeEvpPKeyHandle.OpenSslVersion?displayProperty=nameWithType> Notes.</span><span class="sxs-lookup"><span data-stu-id="44401-110">For callers that use the OpenSSL interop types with custom P/Invokes, follow the guidance in the <xref:System.Security.Cryptography.SafeEvpPKeyHandle.OpenSslVersion?displayProperty=nameWithType> remarks.</span></span> <span data-ttu-id="44401-111">Votre application peut se bloquer si vous ne vérifiez pas la <xref:System.Security.Cryptography.SafeEvpPKeyHandle.OpenSslVersion> valeur.</span><span class="sxs-lookup"><span data-stu-id="44401-111">Your app may crash if you don't check the <xref:System.Security.Cryptography.SafeEvpPKeyHandle.OpenSslVersion> value.</span></span>

- <span data-ttu-id="44401-112">Le Runtime .NET Core 2,1 utilise OpenSSL 1.0. x, s’il est disponible, et revient à OpenSSL 1.1. x si aucune version 1.0. x n’est disponible.</span><span class="sxs-lookup"><span data-stu-id="44401-112">The .NET Core 2.1 runtime uses OpenSSL 1.0.x, if available, and falls back to OpenSSL 1.1.x if there's no 1.0.x version available.</span></span>

  <span data-ttu-id="44401-113">Le Runtime 2,1 préfère la version antérieure d’OpenSSL, car la <xref:System.Security.Cryptography.SafeEvpPKeyHandle.OpenSslVersion?displayProperty=nameWithType> propriété n’existe pas dans .net Core 2,1, donc la version d’OpenSSL ne peut pas être déterminée de manière fiable au moment de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="44401-113">The 2.1 runtime prefers the earlier version of OpenSSL because the <xref:System.Security.Cryptography.SafeEvpPKeyHandle.OpenSslVersion?displayProperty=nameWithType> property does not exist in .NET Core 2.1, so the OpenSSL version cannot be reliably determined at run time.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="44401-114">Version introduite</span><span class="sxs-lookup"><span data-stu-id="44401-114">Version introduced</span></span>

- <span data-ttu-id="44401-115">2.1.16 .NET Core</span><span class="sxs-lookup"><span data-stu-id="44401-115">.NET Core 2.1.16</span></span>
- <span data-ttu-id="44401-116">3.0.3 .NET Core</span><span class="sxs-lookup"><span data-stu-id="44401-116">.NET Core 3.0.3</span></span>
- <span data-ttu-id="44401-117">.NET Core 3.1.2</span><span class="sxs-lookup"><span data-stu-id="44401-117">.NET Core 3.1.2</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="44401-118">Action recommandée</span><span class="sxs-lookup"><span data-stu-id="44401-118">Recommended action</span></span>

- <span data-ttu-id="44401-119">Désinstallez OpenSSL version 1.0.2 Si vous n’en avez plus besoin.</span><span class="sxs-lookup"><span data-stu-id="44401-119">Uninstall OpenSSL version 1.0.2 if it's no longer needed.</span></span>

- <span data-ttu-id="44401-120">Installez OpenSSL 1.1. x si vous utilisez les <xref:System.Security.Cryptography.AesCcm> types,, <xref:System.Security.Cryptography.AesGcm> <xref:System.Security.Cryptography.DSAOpenSsl> , <xref:System.Security.Cryptography.ECDiffieHellmanOpenSsl> ,, <xref:System.Security.Cryptography.ECDsaOpenSsl> <xref:System.Security.Cryptography.RSAOpenSsl> ou <xref:System.Security.Cryptography.SafeEvpPKeyHandle> .</span><span class="sxs-lookup"><span data-stu-id="44401-120">Install OpenSSL 1.1.x if you use the <xref:System.Security.Cryptography.AesCcm>, <xref:System.Security.Cryptography.AesGcm>, <xref:System.Security.Cryptography.DSAOpenSsl>, <xref:System.Security.Cryptography.ECDiffieHellmanOpenSsl>, <xref:System.Security.Cryptography.ECDsaOpenSsl>, <xref:System.Security.Cryptography.RSAOpenSsl>, or <xref:System.Security.Cryptography.SafeEvpPKeyHandle> types.</span></span>

- <span data-ttu-id="44401-121">Si vous utilisez les types d’interopérabilité OpenSSL avec des P/Invoke personnalisés, suivez les instructions des <xref:System.Security.Cryptography.SafeEvpPKeyHandle.OpenSslVersion?displayProperty=nameWithType> Notes.</span><span class="sxs-lookup"><span data-stu-id="44401-121">If you use the OpenSSL interop types with custom P/Invokes, follow the guidance in the <xref:System.Security.Cryptography.SafeEvpPKeyHandle.OpenSslVersion?displayProperty=nameWithType> remarks.</span></span>

#### <a name="category"></a><span data-ttu-id="44401-122">Category</span><span class="sxs-lookup"><span data-stu-id="44401-122">Category</span></span>

<span data-ttu-id="44401-123">Bibliothèques .NET Core</span><span class="sxs-lookup"><span data-stu-id="44401-123">Core .NET libraries</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="44401-124">API affectées</span><span class="sxs-lookup"><span data-stu-id="44401-124">Affected APIs</span></span>

- <xref:System.Security.Cryptography.AesCcm?displayProperty=fullName>
- <xref:System.Security.Cryptography.AesGcm?displayProperty=fullName>
- <xref:System.Security.Cryptography.DSAOpenSsl?displayProperty=fullName>
- <xref:System.Security.Cryptography.ECDiffieHellmanOpenSsl?displayProperty=fullName>
- <xref:System.Security.Cryptography.ECDsaOpenSsl?displayProperty=fullName>
- <xref:System.Security.Cryptography.RSAOpenSsl?displayProperty=fullName>
- <xref:System.Security.Cryptography.SafeEvpPKeyHandle?displayProperty=fullName>

<!--

#### Affected APIs

- `T:System.Security.Cryptography.AesCcm``
- `T:System.Security.Cryptography.AesGcm`
- `T:System.Security.Cryptography.DSAOpenSsl`
- `T:System.Security.Cryptography.ECDiffieHellmanOpenSsl`
- `T:System.Security.Cryptography.ECDsaOpenSsl`
- `T:System.Security.Cryptography.RSAOpenSsl`
- `T:System.Security.Cryptography.SafeEvpPKeyHandle`

-->
