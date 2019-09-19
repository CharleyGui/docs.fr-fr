---
ms.openlocfilehash: f72a9f60d0adcace2df6f1761940f8d8cd33d3af
ms.sourcegitcommit: a4b10e1f2a8bb4e8ff902630855474a0c4f1b37a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2019
ms.locfileid: "71119288"
---
### <a name="better-argument-validation-in-the-pkcs8privatekeyinfo-constructor"></a><span data-ttu-id="5603f-101">Meilleure validation d’argument dans le constructeur Pkcs8PrivateKeyInfo</span><span class="sxs-lookup"><span data-stu-id="5603f-101">Better argument validation in the Pkcs8PrivateKeyInfo constructor</span></span>

<span data-ttu-id="5603f-102">À compter de .net Core 3,0 Preview 9, `Pkcs8PrivateKeyInfo` le constructeur valide le `algorithmParameters` paramètre en tant que valeur codée BER unique.</span><span class="sxs-lookup"><span data-stu-id="5603f-102">Starting with .NET Core 3.0 Preview 9, the `Pkcs8PrivateKeyInfo` constructor validates the `algorithmParameters` parameter as a single BER-encoded value.</span></span> 

#### <a name="change-description"></a><span data-ttu-id="5603f-103">Modifier la description</span><span class="sxs-lookup"><span data-stu-id="5603f-103">Change description</span></span>

<span data-ttu-id="5603f-104">Avant .net Core 3,0 Preview 9, le [ `Pkcs8PrivateKeyInfo` constructeur](xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.%23ctor(System.Security.Cryptography.Oid,System.Nullable%7BSystem.ReadOnlyMemory%7BSystem.Byte%7D%7D,System.ReadOnlyMemory%7BSystem.Byte%7D,System.Boolean)) n’a pas validé `algorithmParameters` l’argument.</span><span class="sxs-lookup"><span data-stu-id="5603f-104">Before .NET Core 3.0 Preview 9, the [`Pkcs8PrivateKeyInfo` constructor](xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.%23ctor(System.Security.Cryptography.Oid,System.Nullable%7BSystem.ReadOnlyMemory%7BSystem.Byte%7D%7D,System.ReadOnlyMemory%7BSystem.Byte%7D,System.Boolean)) did not validate the `algorithmParameters` argument.</span></span>  <span data-ttu-id="5603f-105">Lorsque cet argument représente une valeur non valide, le constructeur aboutissait, mais <xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.Encode>un appel à l’une des méthodes <xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.Encrypt%2A>, <xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.TryEncode%2A>, <xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.TryEncrypt%2A> ou lèverait soit un <xref:System.ArgumentException> pour un argument qu’il n’a pas accepté (`preEncodedValue`) <xref:System.Security.Cryptography.CryptographicException>ou.</span><span class="sxs-lookup"><span data-stu-id="5603f-105">When this argument represented an invalid value, the constructor would succeed, but a call to any of the <xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.Encode>, <xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.TryEncode%2A>, <xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.Encrypt%2A>, or <xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.TryEncrypt%2A> methods would throw either an <xref:System.ArgumentException> for an argument they did not accept (`preEncodedValue`) or a <xref:System.Security.Cryptography.CryptographicException>.</span></span>

<span data-ttu-id="5603f-106">Si vous exécutez avec .net Core 3,0 avant Preview 9, le code suivant lève une exception uniquement lorsque la <xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.Encode> méthode est appelée :</span><span class="sxs-lookup"><span data-stu-id="5603f-106">If run with .NET Core 3.0 before Preview 9, the following code throws an exception only when the <xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.Encode> method is called:</span></span>

```csharp
byte[] algorithmParameters = { 0x05, 0x00, 0x05, 0x00 };

var info = new Pkcs8PrivateKeyInfo(algorithmId, algorithmParameters, privateKey);
// This line throws an ArgumentException for `preEncodedValue`:
byte[] encoded = info.Encode();
```

<span data-ttu-id="5603f-107">À compter de .NET Core 3,0 Preview 9, l’argument est validé dans le constructeur et une valeur non valide entraîne la levée d’une <xref:System.Security.Cryptography.CryptographicException>méthode par la méthode.</span><span class="sxs-lookup"><span data-stu-id="5603f-107">Starting with .NET Core 3.0 Preview 9, the argument is validated in the constructor, and an invalid value results in the method throwing a <xref:System.Security.Cryptography.CryptographicException>.</span></span> <span data-ttu-id="5603f-108">Cette modification déplace l’exception plus près de la source de l’erreur de données.</span><span class="sxs-lookup"><span data-stu-id="5603f-108">This change moves the exception closer to the source of the data error.</span></span> <span data-ttu-id="5603f-109">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="5603f-109">For example:</span></span>

```csharp
byte[] algorithmParameters = { 0x05, 0x00, 0x05, 0x00 };

// This line throws a CryptographicException
var info = new Pkcs8PrivateKeyInfo(algorithmId, algorithmParameters, privateKey);
```

#### <a name="version-introduced"></a><span data-ttu-id="5603f-110">Version introduite</span><span class="sxs-lookup"><span data-stu-id="5603f-110">Version introduced</span></span>

<span data-ttu-id="5603f-111">3,0 Preview 9</span><span class="sxs-lookup"><span data-stu-id="5603f-111">3.0 Preview 9</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="5603f-112">Action recommandée</span><span class="sxs-lookup"><span data-stu-id="5603f-112">Recommended action</span></span>

<span data-ttu-id="5603f-113">Assurez-vous `algorithmParameters` que seules les valeurs valides sont fournies, ou que les appels <xref:System.ArgumentException> au <xref:System.Security.Cryptography.CryptographicException> constructeur testent pour et si la `Pkcs8PrivateKeyInfo` gestion des exceptions est souhaitée.</span><span class="sxs-lookup"><span data-stu-id="5603f-113">Ensure that only valid `algorithmParameters` values are provided, or that calls to the `Pkcs8PrivateKeyInfo` constructor test for both <xref:System.ArgumentException> and <xref:System.Security.Cryptography.CryptographicException> if exception handling is desired.</span></span>

### <a name="category"></a><span data-ttu-id="5603f-114">Category</span><span class="sxs-lookup"><span data-stu-id="5603f-114">Category</span></span>

<span data-ttu-id="5603f-115">Chiffrement</span><span class="sxs-lookup"><span data-stu-id="5603f-115">Cryptography</span></span>

### <a name="affected-apis"></a><span data-ttu-id="5603f-116">API affectées</span><span class="sxs-lookup"><span data-stu-id="5603f-116">Affected APIs</span></span>

- <span data-ttu-id="5603f-117">[Constructeur Pkcs8PrivateKeyInfo](xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.%23ctor(System.Security.Cryptography.Oid,System.Nullable%7BSystem.ReadOnlyMemory%7BSystem.Byte%7D%7D,System.ReadOnlyMemory%7BSystem.Byte%7D,System.Boolean))</span><span class="sxs-lookup"><span data-stu-id="5603f-117">[Pkcs8PrivateKeyInfo constructor](xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.%23ctor(System.Security.Cryptography.Oid,System.Nullable%7BSystem.ReadOnlyMemory%7BSystem.Byte%7D%7D,System.ReadOnlyMemory%7BSystem.Byte%7D,System.Boolean))</span></span>

<!--

### Affected APIs

- `M:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.#ctor(System.Security.Cryptography.Oid,System.Nullable{System.ReadOnlyMemory{System.Byte}},System.ReadOnlyMemory{System.Byte},System.Boolean))

-->