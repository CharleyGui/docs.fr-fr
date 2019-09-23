---
ms.openlocfilehash: b965c3a975b0f2cadd906799fef1665261d96d6e
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/23/2019
ms.locfileid: "71181974"
---
### <a name="envelopedcms-defaults-to-aes-256-encryption"></a>La valeur par défaut de EnvelopedCms est le chiffrement AES-256

L’algorithme de chiffrement symétrique `EnvelopedCms` par défaut utilisé par est passé de TripleDES à AES-256.

#### <a name="details"></a>Détails

Dans .net Core Preview 7 et les versions antérieures, <xref:System.Security.Cryptography.Pkcs.EnvelopedCms> quand est utilisé pour chiffrer des données sans spécifier un algorithme de chiffrement symétrique via une surcharge de constructeur, les données ont été chiffrées avec l’algorithme TripleDES/3DES/3DEA/des3-EDE.

À compter de .NET Core 3,0 Preview 8 (via la version 4.6.0 du package NuGet [System. Security. Cryptography. Pkcs](https://www.nuget.org/packages/System.Security.Cryptography.Pkcs/) ), l’algorithme par défaut a été remplacé par AES-256 pour la modernisation des algorithmes et pour améliorer la sécurité des options par défaut. Si un certificat de destinataire de message a une clé publique Diffie-Hellman non-EC, l’opération de chiffrement peut échouer avec un <xref:System.Security.Cryptography.CryptographicException> en raison des limitations de la plateforme sous-jacente.

Dans l’exemple de code suivant, les données sont chiffrées à l’aide de TripleDES si vous exécutez .NET Core 3,0 Preview 7 ou une version antérieure. En cas d’exécution sur .NET Core 3,0 Preview 8 ou version ultérieure, il est chiffré avec AES-256.

```csharp
EnvelopedCms cms = new EnvelopedCms(content);
cms.Encrypt(recipient);
return cms.Encode();
```

#### <a name="version-introduced"></a>Version introduite

3,0 Preview 8

#### <a name="recommended-action"></a>Action recommandée

Si vous avez un impact négatif sur la modification, vous pouvez restaurer le chiffrement TripleDes en spécifiant explicitement l’identificateur d’algorithme <xref:System.Security.Cryptography.Pkcs.EnvelopedCms> de chiffrement dans un constructeur qui <xref:System.Security.Cryptography.Pkcs.AlgorithmIdentifier>comprend un paramètre de type, par exemple :

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
