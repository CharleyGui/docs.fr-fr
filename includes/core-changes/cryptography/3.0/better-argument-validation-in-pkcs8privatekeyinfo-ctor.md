---
ms.openlocfilehash: 8d3a8712528d2d35c706cc26b8c388b65d6ad506
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "77449212"
---
### <a name="better-argument-validation-in-the-pkcs8privatekeyinfo-constructor"></a>Meilleure validation d’argument dans le constructeur Pkcs8PrivateKeyInfo

En commençant par .NET Core 3.0 Aperçu 9, le `Pkcs8PrivateKeyInfo` constructeur valide le `algorithmParameters` paramètre comme une seule valeur codée BER.

#### <a name="change-description"></a>Description de la modification

Avant .NET Core 3.0 Aperçu [ `Pkcs8PrivateKeyInfo` ](xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.%23ctor(System.Security.Cryptography.Oid,System.Nullable%7BSystem.ReadOnlyMemory%7BSystem.Byte%7D%7D,System.ReadOnlyMemory%7BSystem.Byte%7D,System.Boolean)) 9, le `algorithmParameters` constructeur n’a pas validé l’argument.  Lorsque cet argument représentait une valeur invalide, le constructeur réussirait, <xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.Encrypt%2A>mais <xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.TryEncrypt%2A> un appel à <xref:System.ArgumentException> l’un <xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.Encode>des , , <xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.TryEncode%2A> <xref:System.Security.Cryptography.CryptographicException>, ou des méthodes jetterait soit un pour un argument qu’ils n’ont pas accepté (`preEncodedValue`) ou un .

Si vous exécutez avec .NET Core 3.0 avant Aperçu 9, le code suivant jette une exception seulement lorsque la <xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.Encode> méthode est appelée:

```csharp
byte[] algorithmParameters = { 0x05, 0x00, 0x05, 0x00 };

var info = new Pkcs8PrivateKeyInfo(algorithmId, algorithmParameters, privateKey);
// This line throws an ArgumentException for `preEncodedValue`:
byte[] encoded = info.Encode();
```

En commençant par .NET Core 3.0 Aperçu 9, l’argument est validé dans le <xref:System.Security.Cryptography.CryptographicException>constructeur, et une valeur invalide se traduit par la méthode de jeter un . Cette modification rapproche l’exception de la source de l’erreur de données. Par exemple :

```csharp
byte[] algorithmParameters = { 0x05, 0x00, 0x05, 0x00 };

// This line throws a CryptographicException
var info = new Pkcs8PrivateKeyInfo(algorithmId, algorithmParameters, privateKey);
```

#### <a name="version-introduced"></a>Version introduite

3.0 Aperçu 9

#### <a name="recommended-action"></a>Action recommandée

Assurez-vous `algorithmParameters` que seules des valeurs valides sont fournies, ou que les appels au test constructeur pour les `Pkcs8PrivateKeyInfo` deux <xref:System.ArgumentException> et <xref:System.Security.Cryptography.CryptographicException> si la manipulation d’exception est souhaitée.

### <a name="category"></a>Category

Chiffrement

### <a name="affected-apis"></a>API affectées

- [Constructeur Pkcs8PrivateKeyInfo](xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.%23ctor(System.Security.Cryptography.Oid,System.Nullable%7BSystem.ReadOnlyMemory%7BSystem.Byte%7D%7D,System.ReadOnlyMemory%7BSystem.Byte%7D,System.Boolean))

<!--

### Affected APIs

- `M:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.#ctor(System.Security.Cryptography.Oid,System.Nullable{System.ReadOnlyMemory{System.Byte}},System.ReadOnlyMemory{System.Byte},System.Boolean)`

-->
