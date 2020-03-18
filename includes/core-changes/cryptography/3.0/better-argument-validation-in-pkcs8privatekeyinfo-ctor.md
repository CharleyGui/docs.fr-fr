---
ms.openlocfilehash: 8d3a8712528d2d35c706cc26b8c388b65d6ad506
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "77449212"
---
### <a name="better-argument-validation-in-the-pkcs8privatekeyinfo-constructor"></a><span data-ttu-id="0e076-101">Meilleure validation d’argument dans le constructeur Pkcs8PrivateKeyInfo</span><span class="sxs-lookup"><span data-stu-id="0e076-101">Better argument validation in the Pkcs8PrivateKeyInfo constructor</span></span>

<span data-ttu-id="0e076-102">En commençant par .NET Core 3.0 Aperçu 9, le `Pkcs8PrivateKeyInfo` constructeur valide le `algorithmParameters` paramètre comme une seule valeur codée BER.</span><span class="sxs-lookup"><span data-stu-id="0e076-102">Starting with .NET Core 3.0 Preview 9, the `Pkcs8PrivateKeyInfo` constructor validates the `algorithmParameters` parameter as a single BER-encoded value.</span></span>

#### <a name="change-description"></a><span data-ttu-id="0e076-103">Description de la modification</span><span class="sxs-lookup"><span data-stu-id="0e076-103">Change description</span></span>

<span data-ttu-id="0e076-104">Avant .NET Core 3.0 Aperçu [ `Pkcs8PrivateKeyInfo` ](xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.%23ctor(System.Security.Cryptography.Oid,System.Nullable%7BSystem.ReadOnlyMemory%7BSystem.Byte%7D%7D,System.ReadOnlyMemory%7BSystem.Byte%7D,System.Boolean)) 9, le `algorithmParameters` constructeur n’a pas validé l’argument.</span><span class="sxs-lookup"><span data-stu-id="0e076-104">Before .NET Core 3.0 Preview 9, the [`Pkcs8PrivateKeyInfo` constructor](xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.%23ctor(System.Security.Cryptography.Oid,System.Nullable%7BSystem.ReadOnlyMemory%7BSystem.Byte%7D%7D,System.ReadOnlyMemory%7BSystem.Byte%7D,System.Boolean)) did not validate the `algorithmParameters` argument.</span></span>  <span data-ttu-id="0e076-105">Lorsque cet argument représentait une valeur invalide, le constructeur réussirait, <xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.Encrypt%2A>mais <xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.TryEncrypt%2A> un appel à <xref:System.ArgumentException> l’un <xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.Encode>des , , <xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.TryEncode%2A> <xref:System.Security.Cryptography.CryptographicException>, ou des méthodes jetterait soit un pour un argument qu’ils n’ont pas accepté (`preEncodedValue`) ou un .</span><span class="sxs-lookup"><span data-stu-id="0e076-105">When this argument represented an invalid value, the constructor would succeed, but a call to any of the <xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.Encode>, <xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.TryEncode%2A>, <xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.Encrypt%2A>, or <xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.TryEncrypt%2A> methods would throw either an <xref:System.ArgumentException> for an argument they did not accept (`preEncodedValue`) or a <xref:System.Security.Cryptography.CryptographicException>.</span></span>

<span data-ttu-id="0e076-106">Si vous exécutez avec .NET Core 3.0 avant Aperçu 9, le code suivant jette une exception seulement lorsque la <xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.Encode> méthode est appelée:</span><span class="sxs-lookup"><span data-stu-id="0e076-106">If run with .NET Core 3.0 before Preview 9, the following code throws an exception only when the <xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.Encode> method is called:</span></span>

```csharp
byte[] algorithmParameters = { 0x05, 0x00, 0x05, 0x00 };

var info = new Pkcs8PrivateKeyInfo(algorithmId, algorithmParameters, privateKey);
// This line throws an ArgumentException for `preEncodedValue`:
byte[] encoded = info.Encode();
```

<span data-ttu-id="0e076-107">En commençant par .NET Core 3.0 Aperçu 9, l’argument est validé dans le <xref:System.Security.Cryptography.CryptographicException>constructeur, et une valeur invalide se traduit par la méthode de jeter un .</span><span class="sxs-lookup"><span data-stu-id="0e076-107">Starting with .NET Core 3.0 Preview 9, the argument is validated in the constructor, and an invalid value results in the method throwing a <xref:System.Security.Cryptography.CryptographicException>.</span></span> <span data-ttu-id="0e076-108">Cette modification rapproche l’exception de la source de l’erreur de données.</span><span class="sxs-lookup"><span data-stu-id="0e076-108">This change moves the exception closer to the source of the data error.</span></span> <span data-ttu-id="0e076-109">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="0e076-109">For example:</span></span>

```csharp
byte[] algorithmParameters = { 0x05, 0x00, 0x05, 0x00 };

// This line throws a CryptographicException
var info = new Pkcs8PrivateKeyInfo(algorithmId, algorithmParameters, privateKey);
```

#### <a name="version-introduced"></a><span data-ttu-id="0e076-110">Version introduite</span><span class="sxs-lookup"><span data-stu-id="0e076-110">Version introduced</span></span>

<span data-ttu-id="0e076-111">3.0 Aperçu 9</span><span class="sxs-lookup"><span data-stu-id="0e076-111">3.0 Preview 9</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="0e076-112">Action recommandée</span><span class="sxs-lookup"><span data-stu-id="0e076-112">Recommended action</span></span>

<span data-ttu-id="0e076-113">Assurez-vous `algorithmParameters` que seules des valeurs valides sont fournies, ou que les appels au test constructeur pour les `Pkcs8PrivateKeyInfo` deux <xref:System.ArgumentException> et <xref:System.Security.Cryptography.CryptographicException> si la manipulation d’exception est souhaitée.</span><span class="sxs-lookup"><span data-stu-id="0e076-113">Ensure that only valid `algorithmParameters` values are provided, or that calls to the `Pkcs8PrivateKeyInfo` constructor test for both <xref:System.ArgumentException> and <xref:System.Security.Cryptography.CryptographicException> if exception handling is desired.</span></span>

### <a name="category"></a><span data-ttu-id="0e076-114">Category</span><span class="sxs-lookup"><span data-stu-id="0e076-114">Category</span></span>

<span data-ttu-id="0e076-115">Chiffrement</span><span class="sxs-lookup"><span data-stu-id="0e076-115">Cryptography</span></span>

### <a name="affected-apis"></a><span data-ttu-id="0e076-116">API affectées</span><span class="sxs-lookup"><span data-stu-id="0e076-116">Affected APIs</span></span>

- <span data-ttu-id="0e076-117">[Constructeur Pkcs8PrivateKeyInfo](xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.%23ctor(System.Security.Cryptography.Oid,System.Nullable%7BSystem.ReadOnlyMemory%7BSystem.Byte%7D%7D,System.ReadOnlyMemory%7BSystem.Byte%7D,System.Boolean))</span><span class="sxs-lookup"><span data-stu-id="0e076-117">[Pkcs8PrivateKeyInfo constructor](xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.%23ctor(System.Security.Cryptography.Oid,System.Nullable%7BSystem.ReadOnlyMemory%7BSystem.Byte%7D%7D,System.ReadOnlyMemory%7BSystem.Byte%7D,System.Boolean))</span></span>

<!--

### Affected APIs

- `M:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.#ctor(System.Security.Cryptography.Oid,System.Nullable{System.ReadOnlyMemory{System.Byte}},System.ReadOnlyMemory{System.Byte},System.Boolean)`

-->
