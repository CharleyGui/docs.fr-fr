---
ms.openlocfilehash: a9b6af31b68c25ab58c52757f48ed23cca3f5a35
ms.sourcegitcommit: 79a2d6a07ba4ed08979819666a0ee6927bbf1b01
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2019
ms.locfileid: "74567988"
---
### <a name="better-argument-validation-in-the-pkcs8privatekeyinfo-constructor"></a>Meilleure validation d’argument dans le constructeur Pkcs8PrivateKeyInfo

À compter de .NET Core 3,0 Preview 9, le constructeur `Pkcs8PrivateKeyInfo` valide le paramètre `algorithmParameters` en tant que valeur codée BER unique.

#### <a name="change-description"></a>Modifier la description

Avant .NET Core 3,0 Preview 9, le [constructeur`Pkcs8PrivateKeyInfo`](xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.%23ctor(System.Security.Cryptography.Oid,System.Nullable%7BSystem.ReadOnlyMemory%7BSystem.Byte%7D%7D,System.ReadOnlyMemory%7BSystem.Byte%7D,System.Boolean)) n’a pas validé l’argument `algorithmParameters`.  Lorsque cet argument représente une valeur non valide, le constructeur réussie, mais un appel à l’une des méthodes <xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.Encode>, <xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.TryEncode%2A>, <xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.Encrypt%2A>ou <xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.TryEncrypt%2A> lèvera une <xref:System.ArgumentException> pour un argument qu’il n’a pas accepté (`preEncodedValue`) ou un <xref:System.Security.Cryptography.CryptographicException>.

Si vous exécutez avec .NET Core 3,0 avant Preview 9, le code suivant lève une exception uniquement lorsque la méthode <xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.Encode> est appelée :

```csharp
byte[] algorithmParameters = { 0x05, 0x00, 0x05, 0x00 };

var info = new Pkcs8PrivateKeyInfo(algorithmId, algorithmParameters, privateKey);
// This line throws an ArgumentException for `preEncodedValue`:
byte[] encoded = info.Encode();
```

À compter de .NET Core 3,0 Preview 9, l’argument est validé dans le constructeur et une valeur non valide entraîne la levée d’une <xref:System.Security.Cryptography.CryptographicException>par la méthode. Cette modification déplace l’exception plus près de la source de l’erreur de données. Par exemple :

```csharp
byte[] algorithmParameters = { 0x05, 0x00, 0x05, 0x00 };

// This line throws a CryptographicException
var info = new Pkcs8PrivateKeyInfo(algorithmId, algorithmParameters, privateKey);
```

#### <a name="version-introduced"></a>Version introduite

3,0 Preview 9

#### <a name="recommended-action"></a>Action recommandée

Assurez-vous que seules les valeurs `algorithmParameters` valides sont fournies, ou que les appels au constructeur `Pkcs8PrivateKeyInfo` testent pour <xref:System.ArgumentException> et <xref:System.Security.Cryptography.CryptographicException> si la gestion des exceptions est souhaitée.

### <a name="category"></a>Category

Chiffrement

### <a name="affected-apis"></a>API affectées

- [Constructeur Pkcs8PrivateKeyInfo](xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.%23ctor(System.Security.Cryptography.Oid,System.Nullable%7BSystem.ReadOnlyMemory%7BSystem.Byte%7D%7D,System.ReadOnlyMemory%7BSystem.Byte%7D,System.Boolean))

<!--

### Affected APIs

- `M:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.#ctor(System.Security.Cryptography.Oid,System.Nullable{System.ReadOnlyMemory{System.Byte}},System.ReadOnlyMemory{System.Byte},System.Boolean))

-->
