---
ms.openlocfilehash: 32030698c12de87daef5e1d8851a0f55ec36d688
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/20/2020
ms.locfileid: "83721416"
---
### <a name="better-argument-validation-in-the-pkcs8privatekeyinfo-constructor"></a>Meilleure validation d’argument dans le constructeur Pkcs8PrivateKeyInfo

À compter de .NET Core 3,0 Preview 9, le `Pkcs8PrivateKeyInfo` constructeur valide le `algorithmParameters` paramètre en tant que valeur codée BER unique.

#### <a name="change-description"></a>Description de la modification

Avant .NET Core 3,0 Preview 9, le [ `Pkcs8PrivateKeyInfo` constructeur](xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.%23ctor(System.Security.Cryptography.Oid,System.Nullable%7BSystem.ReadOnlyMemory%7BSystem.Byte%7D%7D,System.ReadOnlyMemory%7BSystem.Byte%7D,System.Boolean)) n’a pas validé l' `algorithmParameters` argument.  Lorsque cet argument représente une valeur non valide, le constructeur aboutissait, mais un appel à l’une <xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.Encode> des <xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.TryEncode%2A> méthodes,, <xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.Encrypt%2A> ou <xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.TryEncrypt%2A> lèverait soit un <xref:System.ArgumentException> pour un argument qu’il n’a pas accepté (), soit `preEncodedValue` un <xref:System.Security.Cryptography.CryptographicException> .

Si vous exécutez avec .NET Core 3,0 avant Preview 9, le code suivant lève une exception uniquement lorsque la <xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.Encode> méthode est appelée :

```csharp
byte[] algorithmParameters = { 0x05, 0x00, 0x05, 0x00 };

var info = new Pkcs8PrivateKeyInfo(algorithmId, algorithmParameters, privateKey);
// This line throws an ArgumentException for `preEncodedValue`:
byte[] encoded = info.Encode();
```

À compter de .NET Core 3,0 Preview 9, l’argument est validé dans le constructeur et une valeur non valide entraîne la levée d’une méthode par la méthode <xref:System.Security.Cryptography.CryptographicException> . Cette modification déplace l’exception plus près de la source de l’erreur de données. Par exemple :

```csharp
byte[] algorithmParameters = { 0x05, 0x00, 0x05, 0x00 };

// This line throws a CryptographicException
var info = new Pkcs8PrivateKeyInfo(algorithmId, algorithmParameters, privateKey);
```

#### <a name="version-introduced"></a>Version introduite

3,0 Preview 9

#### <a name="recommended-action"></a>Action recommandée

Assurez-vous que seules les valeurs valides `algorithmParameters` sont fournies, ou que les appels au `Pkcs8PrivateKeyInfo` constructeur testent pour <xref:System.ArgumentException> et <xref:System.Security.Cryptography.CryptographicException> si la gestion des exceptions est souhaitée.

#### <a name="category"></a>Category

Chiffrement

#### <a name="affected-apis"></a>API affectées

- [Constructeur Pkcs8PrivateKeyInfo](xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.%23ctor(System.Security.Cryptography.Oid,System.Nullable%7BSystem.ReadOnlyMemory%7BSystem.Byte%7D%7D,System.ReadOnlyMemory%7BSystem.Byte%7D,System.Boolean))

<!--

#### Affected APIs

- `M:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.#ctor(System.Security.Cryptography.Oid,System.Nullable{System.ReadOnlyMemory{System.Byte}},System.ReadOnlyMemory{System.Byte},System.Boolean)`

-->
