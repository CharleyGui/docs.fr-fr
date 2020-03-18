---
ms.openlocfilehash: f9000b19997201c2d3de0643669f9029ff1ca31c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "74567952"
---
### <a name="envelopedcms-defaults-to-aes-256-encryption"></a>EnveloppedCms par défaut au cryptage AES-256

L’algorithme de cryptage `EnvelopedCms` symétrique par défaut utilisé par a changé de TripleDES à AES-256.

#### <a name="change-description"></a>Description de la modification

Dans .NET Core Preview 7 et <xref:System.Security.Cryptography.Pkcs.EnvelopedCms> les versions antérieures, lorsqu’il est utilisé pour chiffrer les données sans spécifier un algorithme de cryptage symétrique via une surcharge constructrice, les données ont été cryptées avec l’algorithme TripleDES/3DES/3DEA/DES3-EDE.

En commençant par .NET Core 3.0 Preview 8 (via la version 4.6.0 du package [System.Security.Cryptography.Pkcs](https://www.nuget.org/packages/System.Security.Cryptography.Pkcs/) NuGet), l’algorithme par défaut a été modifié en AES-256 pour la modernisation de l’algorithme et pour améliorer la sécurité des options par défaut. Si un certificat de destinataire de message a une clé publique (non-EC) <xref:System.Security.Cryptography.CryptographicException> Diffie-Hellman, l’opération de cryptage peut échouer avec un en raison de limitations dans la plate-forme sous-jacente.

Dans le code de l’échantillon suivant, les données sont cryptées avec TripleDES si elles sont en cours d’exécution sur .NET Core 3.0 Aperçu 7 ou plus tôt. Si vous exécutez sur .NET Core 3.0 Aperçu 8 ou plus tard, il est crypté avec AES-256.

```csharp
EnvelopedCms cms = new EnvelopedCms(content);
cms.Encrypt(recipient);
return cms.Encode();
```

#### <a name="version-introduced"></a>Version introduite

3.0 Aperçu 8

#### <a name="recommended-action"></a>Action recommandée

Si vous êtes affecté négativement par la modification, vous pouvez restaurer le cryptage <xref:System.Security.Cryptography.Pkcs.EnvelopedCms> TripleDES en spécifiant explicitement l’identifiant de l’algorithme de cryptage dans un constructeur qui inclut un paramètre de type, <xref:System.Security.Cryptography.Pkcs.AlgorithmIdentifier>tel que :

```csharp
Oid tripleDesOid = new Oid("1.2.840.113549.3.7", null);
AlgorithmIdentifier tripleDesIdentifier = new AlgorithmIdentifier(tripleDesOid);
EnvelopedCms cms = new EnvelopedCms(content, tripleDesIdentifier);

cms.Encrypt(recipient);
return cms.Encode()l
```

#### <a name="category"></a>Category

Chiffrement

#### <a name="affected-apis"></a>API affectées

- <xref:System.Security.Cryptography.Pkcs.EnvelopedCms.%23ctor?displayProperty=nameWithType>
- <xref:System.Security.Cryptography.Pkcs.EnvelopedCms.%23ctor(System.Security.Cryptography.Pkcs.ContentInfo)?displayProperty=nameWithType>
- <xref:System.Security.Cryptography.Pkcs.EnvelopedCms.%23ctor(System.Security.Cryptography.Pkcs.SubjectIdentifierType,System.Security.Cryptography.Pkcs.ContentInfo)?displayProperty=nameWithType>

<!--

### Affected APIs

- `M:System.Security.Cryptography.Pkcs.EnvelopedCms.#ctor`
- `M:System.Security.Cryptography.Pkcs.EnvelopedCms.#ctor(System.Security.Cryptography.Pkcs.ContentInfo)`
- `M:System.Security.Cryptography.Pkcs.EnvelopedCms.%23ctor(System.Security.Cryptography.Pkcs.SubjectIdentifierType,System.Security.Cryptography.Pkcs.ContentInfo)`

-->
