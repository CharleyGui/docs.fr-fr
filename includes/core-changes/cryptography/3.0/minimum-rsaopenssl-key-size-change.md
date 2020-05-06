---
ms.openlocfilehash: b5b724afefcce69df706f2bea0b1612db653af03
ms.sourcegitcommit: 7980a91f90ae5eca859db7e6bfa03e23e76a1a50
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/13/2020
ms.locfileid: "81275358"
---
### <a name="minimum-size-for-rsaopenssl-key-generation-has-increased"></a><span data-ttu-id="3a5df-101">La taille minimale de la génération de la clé de RSAOpenSsl a augmenté</span><span class="sxs-lookup"><span data-stu-id="3a5df-101">Minimum size for RSAOpenSsl key generation has increased</span></span>

<span data-ttu-id="3a5df-102">La taille minimale de la génération de nouvelles clés RSA sur Linux est passée de 384 bits à 512 bits.</span><span class="sxs-lookup"><span data-stu-id="3a5df-102">The minimum size for generating new RSA keys on Linux has increased from 384-bit to 512-bit.</span></span>

#### <a name="change-description"></a><span data-ttu-id="3a5df-103">Description de la modification</span><span class="sxs-lookup"><span data-stu-id="3a5df-103">Change description</span></span>

<span data-ttu-id="3a5df-104">À compter de .net Core 3,0, la taille de clé légale minimale indiquée `LegalKeySizes` par la propriété sur les <xref:System.Security.Cryptography.RSA.Create%2A?displayProperty=nameWithType>instances <xref:System.Security.Cryptography.RSAOpenSsl.%23ctor%2A>RSA de <xref:System.Security.Cryptography.RSACryptoServiceProvider.%23ctor%2A> , et sur Linux est passée de 384 à 512.</span><span class="sxs-lookup"><span data-stu-id="3a5df-104">Starting with .NET Core 3.0, the minimum legal key size reported by the `LegalKeySizes` property on RSA instances from <xref:System.Security.Cryptography.RSA.Create%2A?displayProperty=nameWithType>, <xref:System.Security.Cryptography.RSAOpenSsl.%23ctor%2A>, and <xref:System.Security.Cryptography.RSACryptoServiceProvider.%23ctor%2A> on Linux has increased from 384 to 512.</span></span>

<span data-ttu-id="3a5df-105">Par conséquent, dans .NET Core 2,2 et les versions antérieures, un appel de méthode tel `RSA.Create(384)` que aboutit.</span><span class="sxs-lookup"><span data-stu-id="3a5df-105">As a result, in .NET Core 2.2 and earlier versions, a method call such as `RSA.Create(384)` succeeds.</span></span> <span data-ttu-id="3a5df-106">Dans .NET Core 3,0 et versions ultérieures, l’appel `RSA.Create(384)` de méthode lève une exception indiquant que la taille est trop petite.</span><span class="sxs-lookup"><span data-stu-id="3a5df-106">In .NET Core 3.0 and later versions, the method call `RSA.Create(384)` throws an exception indicating the size is too small.</span></span>

<span data-ttu-id="3a5df-107">Cette modification a été apportée car OpenSSL, qui effectue les opérations de chiffrement sur Linux, a augmenté son minimum entre les versions 1.0.2 et 1.1.0.</span><span class="sxs-lookup"><span data-stu-id="3a5df-107">This change was made because OpenSSL, which performs the cryptographic operations on Linux, raised its minimum between versions 1.0.2 and 1.1.0.</span></span> <span data-ttu-id="3a5df-108">.NET Core 3,0 préfère OpenSSL 1.1. x à 1.0. x, et la version signalée minimale a été augmentée pour refléter cette nouvelle limite de dépendance supérieure.</span><span class="sxs-lookup"><span data-stu-id="3a5df-108">.NET Core 3.0 prefers OpenSSL 1.1.x to 1.0.x, and the minimum reported version was raised to reflect this new higher dependency limitation.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="3a5df-109">Version introduite</span><span class="sxs-lookup"><span data-stu-id="3a5df-109">Version introduced</span></span>

<span data-ttu-id="3a5df-110">3.0</span><span class="sxs-lookup"><span data-stu-id="3a5df-110">3.0</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="3a5df-111">Action recommandée</span><span class="sxs-lookup"><span data-stu-id="3a5df-111">Recommended action</span></span>

<span data-ttu-id="3a5df-112">Si vous appelez l’une des API affectées, assurez-vous que la taille de toutes les clés générées n’est pas inférieure à la valeur minimale du fournisseur.</span><span class="sxs-lookup"><span data-stu-id="3a5df-112">If you call any of the affected APIs, ensure that the size of any generated keys is not less than the provider minimum.</span></span>

> [!NOTE]
> <span data-ttu-id="3a5df-113">RSA 384 bits est déjà considéré comme non sécurisé (comme c’est le cas de la RSA 512 bits).</span><span class="sxs-lookup"><span data-stu-id="3a5df-113">384-bit RSA is already considered insecure (as is 512-bit RSA).</span></span> <span data-ttu-id="3a5df-114">Des recommandations modernes, telles que la [publication spéciale NIST 800-57 partie 1 révision 4](https://nvlpubs.nist.gov/nistpubs/SpecialPublications/NIST.SP.800-57pt1r4.pdf), suggèrent 2048 bits comme taille minimale pour les clés nouvellement générées.</span><span class="sxs-lookup"><span data-stu-id="3a5df-114">Modern recommendations, such as [NIST Special Publication 800-57 Part 1 Revision 4](https://nvlpubs.nist.gov/nistpubs/SpecialPublications/NIST.SP.800-57pt1r4.pdf), suggest 2048-bit as the minimum size for newly generated keys.</span></span>

#### <a name="category"></a><span data-ttu-id="3a5df-115">Category</span><span class="sxs-lookup"><span data-stu-id="3a5df-115">Category</span></span>

<span data-ttu-id="3a5df-116">Chiffrement</span><span class="sxs-lookup"><span data-stu-id="3a5df-116">Cryptography</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="3a5df-117">API affectées</span><span class="sxs-lookup"><span data-stu-id="3a5df-117">Affected APIs</span></span>

- <xref:System.Security.Cryptography.AsymmetricAlgorithm.LegalKeySizes?displayProperty=nameWithType>
- <xref:System.Security.Cryptography.RSA.Create%2A?displayProperty=nameWithType>
- <xref:System.Security.Cryptography.RSAOpenSsl.%23ctor%2A>
- <xref:System.Security.Cryptography.RSACryptoServiceProvider.%23ctor%2A>

<!--
### Affected APIs

- `P:System.Security.Cryptography.AsymmetricAlgorithm.LegalKeySizes`
- `Overload:System.Security.Cryptography.RSA.Create`
- `Overload:System.Security.Cryptography.RSAOpenSsl.#ctor`
- `Overload:System.Security.Cryptography.RSACryptoServiceProvider.#ctor`

-->
