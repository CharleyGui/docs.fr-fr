---
ms.openlocfilehash: 4788f5b80306116e63ee56584d65b862ce0606ee
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/05/2020
ms.locfileid: "89496369"
---
### <a name="rsacng-and-dsacng-are-once-again-usable-in-partial-trust-scenarios"></a><span data-ttu-id="73104-101">RSACng et DSACng sont à nouveau utilisables dans les scénarios de confiance partielle</span><span class="sxs-lookup"><span data-stu-id="73104-101">RSACng and DSACng are once again usable in Partial Trust scenarios</span></span>

#### <a name="details"></a><span data-ttu-id="73104-102">Détails</span><span class="sxs-lookup"><span data-stu-id="73104-102">Details</span></span>

<span data-ttu-id="73104-103">CngLightup (utilisé dans plusieurs API de chiffrement de niveau supérieur, telles que <xref:System.Security.Cryptography.Xml.EncryptedXml?displayProperty=nameWithType>) et <xref:System.Security.Cryptography.RSACng?displayProperty=nameWithType> dans certains cas s’appuient sur la confiance totale.</span><span class="sxs-lookup"><span data-stu-id="73104-103">CngLightup (used in several higher-level crypto apis, such as <xref:System.Security.Cryptography.Xml.EncryptedXml?displayProperty=nameWithType>) and <xref:System.Security.Cryptography.RSACng?displayProperty=nameWithType> in some cases rely on full trust.</span></span> <span data-ttu-id="73104-104">Ces éléments comprennent P/Invokes sans l’assertion d’autorisations <xref:System.Security.Permissions.SecurityPermissionFlag.UnmanagedCode?displayProperty=nameWithType> et des chemins de code où <xref:System.Security.Cryptography.CngKey?displayProperty=nameWithType> a des demandes d’autorisation pour <xref:System.Security.Permissions.SecurityPermissionFlag.UnmanagedCode?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="73104-104">These include P/Invokes without asserting <xref:System.Security.Permissions.SecurityPermissionFlag.UnmanagedCode?displayProperty=nameWithType> permissions, and code paths where <xref:System.Security.Cryptography.CngKey?displayProperty=nameWithType> has permission demands for <xref:System.Security.Permissions.SecurityPermissionFlag.UnmanagedCode?displayProperty=nameWithType>.</span></span> <span data-ttu-id="73104-105">À compter de .NET Framework 4.6.2, CngLightup a été utilisé pour basculer vers <xref:System.Security.Cryptography.RSACng?displayProperty=nameWithType> autant que possible.</span><span class="sxs-lookup"><span data-stu-id="73104-105">Starting with the .NET Framework 4.6.2, CngLightup was used to switch to <xref:System.Security.Cryptography.RSACng?displayProperty=nameWithType> wherever possible.</span></span> <span data-ttu-id="73104-106">Par conséquent, les applications de confiance partielle qui utilisaient correctement <xref:System.Security.Cryptography.Xml.EncryptedXml?displayProperty=nameWithType> ont commencé à échouer et à lever des exceptions <xref:System.Security.SecurityException>. Cette modification ajoute les assertions nécessaires afin que toutes les fonctions utilisant CngLightup disposent des autorisations requises.</span><span class="sxs-lookup"><span data-stu-id="73104-106">As a result, partial trust apps that successfully used <xref:System.Security.Cryptography.Xml.EncryptedXml?displayProperty=nameWithType> began to fail and throw <xref:System.Security.SecurityException> exceptions.This change adds the required asserts so that all functions using CngLightup have the required permissions.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="73104-107">Suggestion</span><span class="sxs-lookup"><span data-stu-id="73104-107">Suggestion</span></span>

<span data-ttu-id="73104-108">Si cette modification dans .NET Framework 4.6.2 a eu un impact négatif sur vos applications de confiance partielle, effectuez la mise à niveau vers .NET Framework 4.7.1.</span><span class="sxs-lookup"><span data-stu-id="73104-108">If this change in the .NET Framework 4.6.2 has negatively impacted your partial trust apps, upgrade to the .NET Framework 4.7.1.</span></span>

| <span data-ttu-id="73104-109">Name</span><span class="sxs-lookup"><span data-stu-id="73104-109">Name</span></span>    | <span data-ttu-id="73104-110">Valeur</span><span class="sxs-lookup"><span data-stu-id="73104-110">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="73104-111">Étendue</span><span class="sxs-lookup"><span data-stu-id="73104-111">Scope</span></span>   |<span data-ttu-id="73104-112">Edge</span><span class="sxs-lookup"><span data-stu-id="73104-112">Edge</span></span>|
|<span data-ttu-id="73104-113">Version</span><span class="sxs-lookup"><span data-stu-id="73104-113">Version</span></span>|<span data-ttu-id="73104-114">4.6.2</span><span class="sxs-lookup"><span data-stu-id="73104-114">4.6.2</span></span>|
|<span data-ttu-id="73104-115">Type</span><span class="sxs-lookup"><span data-stu-id="73104-115">Type</span></span>|<span data-ttu-id="73104-116">Runtime</span><span class="sxs-lookup"><span data-stu-id="73104-116">Runtime</span></span>|

#### <a name="affected-apis"></a><span data-ttu-id="73104-117">API affectées</span><span class="sxs-lookup"><span data-stu-id="73104-117">Affected APIs</span></span>

- <xref:System.Security.Cryptography.DSACng.%23ctor(System.Security.Cryptography.CngKey)>
- <xref:System.Security.Cryptography.DSACng.Key?displayProperty=nameWithType>
- <xref:System.Security.Cryptography.DSACng.LegalKeySizes?displayProperty=nameWithType>
- <xref:System.Security.Cryptography.DSACng.CreateSignature(System.Byte[])?displayProperty=nameWithType>
- <xref:System.Security.Cryptography.DSACng.VerifySignature(System.Byte[],System.Byte[])?displayProperty=nameWithType>
- <xref:System.Security.Cryptography.RSACng.%23ctor(System.Security.Cryptography.CngKey)>
- <xref:System.Security.Cryptography.RSACng.Key?displayProperty=nameWithType>
- <xref:System.Security.Cryptography.RSACng.Decrypt(System.Byte[],System.Security.Cryptography.RSAEncryptionPadding)?displayProperty=nameWithType>
- <xref:System.Security.Cryptography.RSACng.SignHash(System.Byte[],System.Security.Cryptography.HashAlgorithmName,System.Security.Cryptography.RSASignaturePadding)?displayProperty=nameWithType>

<!--

#### Affected APIs

- `M:System.Security.Cryptography.DSACng.#ctor(System.Security.Cryptography.CngKey)`
- `P:System.Security.Cryptography.DSACng.Key`
- `P:System.Security.Cryptography.DSACng.LegalKeySizes`
- `M:System.Security.Cryptography.DSACng.CreateSignature(System.Byte[])`
- `M:System.Security.Cryptography.DSACng.VerifySignature(System.Byte[],System.Byte[])`
- `M:System.Security.Cryptography.RSACng.#ctor(System.Security.Cryptography.CngKey)`
- `P:System.Security.Cryptography.RSACng.Key`
- `M:System.Security.Cryptography.RSACng.Decrypt(System.Byte[],System.Security.Cryptography.RSAEncryptionPadding)`
- `M:System.Security.Cryptography.RSACng.SignHash(System.Byte[],System.Security.Cryptography.HashAlgorithmName,System.Security.Cryptography.RSASignaturePadding)`

-->
