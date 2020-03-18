---
ms.openlocfilehash: 2fb980c8b75e25ba347c56ccc1c90f2959e83e21
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "74567961"
---
### <a name="minimum-size-for-rsaopenssl-key-generation-has-increased"></a><span data-ttu-id="8f49e-101">La taille minimale de la génération clé RSAOpenSsl a augmenté</span><span class="sxs-lookup"><span data-stu-id="8f49e-101">Minimum size for RSAOpenSsl key generation has increased</span></span>

<span data-ttu-id="8f49e-102">La taille minimale pour générer de nouvelles touches RSA sur Linux est passée de 384 bits à 512 bits.</span><span class="sxs-lookup"><span data-stu-id="8f49e-102">The minimum size for generating new RSA keys on Linux has increased from 384-bit to 512-bit.</span></span>

#### <a name="change-description"></a><span data-ttu-id="8f49e-103">Description de la modification</span><span class="sxs-lookup"><span data-stu-id="8f49e-103">Change description</span></span>

<span data-ttu-id="8f49e-104">À partir de .NET Core 3.0, la `LegalKeySizes` taille minimale <xref:System.Security.Cryptography.RSA.Create%2A?displayProperty=nameWithType>de <xref:System.Security.Cryptography.RSAOpenSsl.%23ctor%2A?displayProperty=nameWithType>clé <xref:System.Security.Cryptography.RSACryptoServiceProvider.%23ctor%2A?displayProperty=nameWithType> légale déclarée par la propriété sur les instances RSA de , , et sur Linux a augmenté de 384 à 512.</span><span class="sxs-lookup"><span data-stu-id="8f49e-104">Starting with .NET Core 3.0, the minimum legal key size reported by the `LegalKeySizes` property on RSA instances from <xref:System.Security.Cryptography.RSA.Create%2A?displayProperty=nameWithType>, <xref:System.Security.Cryptography.RSAOpenSsl.%23ctor%2A?displayProperty=nameWithType>, and <xref:System.Security.Cryptography.RSACryptoServiceProvider.%23ctor%2A?displayProperty=nameWithType> on Linux has increased from 384 to 512.</span></span>

<span data-ttu-id="8f49e-105">En conséquence, dans .NET Core 2.2 et les versions antérieures, un appel de méthode tel que `RSA.Create(384)` réussit.</span><span class="sxs-lookup"><span data-stu-id="8f49e-105">As a result, in .NET Core 2.2 and earlier versions, a method call such as `RSA.Create(384)` succeeds.</span></span> <span data-ttu-id="8f49e-106">Dans .NET Core 3.0 et les `RSA.Create(384)` versions ultérieures, l’appel de méthode jette une exception indiquant que la taille est trop petite.</span><span class="sxs-lookup"><span data-stu-id="8f49e-106">In .NET Core 3.0 and later versions, the method call `RSA.Create(384)` throws an exception indicating the size is too small.</span></span>

<span data-ttu-id="8f49e-107">Ce changement a été apporté parce qu’OpenSSL, qui effectue les opérations cryptographiques sur Linux, a augmenté son minimum entre les versions 1.0.2 et 1.1.0.</span><span class="sxs-lookup"><span data-stu-id="8f49e-107">This change was made because OpenSSL, which performs the cryptographic operations on Linux, raised its minimum between versions 1.0.2 and 1.1.0.</span></span> <span data-ttu-id="8f49e-108">.NET Core 3.0 préfère OpenSSL 1.1.x à 1.0.x, et la version minimale déclarée a été soulevée pour refléter cette nouvelle limitation de dépendance plus élevée.</span><span class="sxs-lookup"><span data-stu-id="8f49e-108">.NET Core 3.0 prefers OpenSSL 1.1.x to 1.0.x, and the minimum reported version was raised to reflect this new higher dependency limitation.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="8f49e-109">Version introduite</span><span class="sxs-lookup"><span data-stu-id="8f49e-109">Version introduced</span></span>

<span data-ttu-id="8f49e-110">3.0</span><span class="sxs-lookup"><span data-stu-id="8f49e-110">3.0</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="8f49e-111">Action recommandée</span><span class="sxs-lookup"><span data-stu-id="8f49e-111">Recommended action</span></span>

<span data-ttu-id="8f49e-112">Si vous appelez l’une des API affectées, assurez-vous que la taille des clés générées n’est pas inférieure au minimum du fournisseur.</span><span class="sxs-lookup"><span data-stu-id="8f49e-112">If you call any of the affected APIs, ensure that the size of any generated keys is not less than the provider minimum.</span></span>

> [!NOTE]
> <span data-ttu-id="8f49e-113">Le RSA 384 bits est déjà considéré comme peu sûr (tout comme le RSA 512 bits).</span><span class="sxs-lookup"><span data-stu-id="8f49e-113">384-bit RSA is already considered insecure (as is 512-bit RSA).</span></span> <span data-ttu-id="8f49e-114">Les recommandations modernes, telles que [NIST Special Publication 800-57 Partie 1 Révision 4](https://nvlpubs.nist.gov/nistpubs/SpecialPublications/NIST.SP.800-57pt1r4.pdf), suggèrent 2048-bit comme la taille minimale pour les clés nouvellement générées.</span><span class="sxs-lookup"><span data-stu-id="8f49e-114">Modern recommendations, such as [NIST Special Publication 800-57 Part 1 Revision 4](https://nvlpubs.nist.gov/nistpubs/SpecialPublications/NIST.SP.800-57pt1r4.pdf), suggest 2048-bit as the minimum size for newly generated keys.</span></span>

#### <a name="category"></a><span data-ttu-id="8f49e-115">Category</span><span class="sxs-lookup"><span data-stu-id="8f49e-115">Category</span></span>

<span data-ttu-id="8f49e-116">Chiffrement</span><span class="sxs-lookup"><span data-stu-id="8f49e-116">Cryptography</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="8f49e-117">API affectées</span><span class="sxs-lookup"><span data-stu-id="8f49e-117">Affected APIs</span></span>

- <xref:System.Security.Cryptography.AsymmetricAlgorithm.LegalKeySizes?displayProperty=nameWithType>
- <xref:System.Security.Cryptography.RSA.Create%2A?displayProperty=nameWithType>
- <xref:System.Security.Cryptography.RSAOpenSsl.%23ctor%2A?displayProperty=nameWithType>
- <xref:System.Security.Cryptography.RSACryptoServiceProvider.%23ctor%2A?displayProperty=nameWithType>

<!--
### Affected APIs

- `P:System.Security.Cryptography.AsymmetricAlgorithm.LegalKeySizes`
- `Overload:System.Security.Cryptography.RSA.Create`
- `Overload:System.Security.Cryptography.RSAOpenSsl.#ctor`
- `Overload:System.Security.Cryptography.RSACryptoServiceProvider.#ctor`

-->
