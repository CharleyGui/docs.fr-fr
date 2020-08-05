---
ms.openlocfilehash: e0cdcce9b8c7d591925b08635e3354dadaf22b7b
ms.sourcegitcommit: b7a8b09828bab4e90f66af8d495ecd7024c45042
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87556023"
---
### <a name="envelopedcms-defaults-to-aes-256-encryption"></a>La valeur par défaut de EnvelopedCms est le chiffrement AES-256

L’algorithme de chiffrement symétrique par défaut utilisé par `EnvelopedCms` est passé de TripleDES à AES-256.

#### <a name="change-description"></a>Description de la modification

Dans les versions précédentes, lorsque <xref:System.Security.Cryptography.Pkcs.EnvelopedCms> est utilisé pour chiffrer des données sans spécifier un algorithme de chiffrement symétrique via une surcharge de constructeur, les données sont chiffrées avec l’algorithme TripleDES/3DES/3DEA/des3-EDE.

À compter de .NET Core 3,0 (via la version 4.6.0 du package NuGet [System. Security. Cryptography. Pkcs](https://www.nuget.org/packages/System.Security.Cryptography.Pkcs/) ), l’algorithme par défaut a été remplacé par AES-256 pour la modernisation des algorithmes et pour améliorer la sécurité des options par défaut. Si un certificat de destinataire de message a une clé publique Diffie-Hellman non-EC, l’opération de chiffrement peut échouer avec un <xref:System.Security.Cryptography.CryptographicException> en raison des limitations de la plateforme sous-jacente.

Dans l’exemple de code suivant, les données sont chiffrées avec TripleDES si elles s’exécutent sur .NET Core 2,2 ou une version antérieure. S’il est exécuté sur .NET Core 3,0 ou une version ultérieure, il est chiffré avec AES-256.

```csharp
EnvelopedCms cms = new EnvelopedCms(content);
cms.Encrypt(recipient);
return cms.Encode();
```

#### <a name="version-introduced"></a>Version introduite

3.0

#### <a name="recommended-action"></a>Action recommandée

Si vous avez un impact négatif sur la modification, vous pouvez restaurer le chiffrement TripleDES en spécifiant explicitement l’identificateur d’algorithme de chiffrement dans un <xref:System.Security.Cryptography.Pkcs.EnvelopedCms> constructeur qui comprend un paramètre de type <xref:System.Security.Cryptography.Pkcs.AlgorithmIdentifier> , par exemple :

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

- <xref:System.Security.Cryptography.Pkcs.EnvelopedCms.%23ctor>
- <xref:System.Security.Cryptography.Pkcs.EnvelopedCms.%23ctor(System.Security.Cryptography.Pkcs.ContentInfo)>
- <xref:System.Security.Cryptography.Pkcs.EnvelopedCms.%23ctor(System.Security.Cryptography.Pkcs.SubjectIdentifierType,System.Security.Cryptography.Pkcs.ContentInfo)>

<!--

#### Affected APIs

- `M:System.Security.Cryptography.Pkcs.EnvelopedCms.#ctor`
- `M:System.Security.Cryptography.Pkcs.EnvelopedCms.#ctor(System.Security.Cryptography.Pkcs.ContentInfo)`
- `M:System.Security.Cryptography.Pkcs.EnvelopedCms.%23ctor(System.Security.Cryptography.Pkcs.SubjectIdentifierType,System.Security.Cryptography.Pkcs.ContentInfo)`

-->
