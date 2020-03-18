---
ms.openlocfilehash: f9000b19997201c2d3de0643669f9029ff1ca31c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "74567952"
---
### <a name="envelopedcms-defaults-to-aes-256-encryption"></a><span data-ttu-id="53608-101">EnveloppedCms par défaut au cryptage AES-256</span><span class="sxs-lookup"><span data-stu-id="53608-101">EnvelopedCms defaults to AES-256 encryption</span></span>

<span data-ttu-id="53608-102">L’algorithme de cryptage `EnvelopedCms` symétrique par défaut utilisé par a changé de TripleDES à AES-256.</span><span class="sxs-lookup"><span data-stu-id="53608-102">The default symmetric encryption algorithm used by `EnvelopedCms` has changed from TripleDES to AES-256.</span></span>

#### <a name="change-description"></a><span data-ttu-id="53608-103">Description de la modification</span><span class="sxs-lookup"><span data-stu-id="53608-103">Change description</span></span>

<span data-ttu-id="53608-104">Dans .NET Core Preview 7 et <xref:System.Security.Cryptography.Pkcs.EnvelopedCms> les versions antérieures, lorsqu’il est utilisé pour chiffrer les données sans spécifier un algorithme de cryptage symétrique via une surcharge constructrice, les données ont été cryptées avec l’algorithme TripleDES/3DES/3DEA/DES3-EDE.</span><span class="sxs-lookup"><span data-stu-id="53608-104">In .NET Core Preview 7 and earlier versions, when <xref:System.Security.Cryptography.Pkcs.EnvelopedCms> is used to encrypt data without specifying a symmetric encryption algorithm via a constructor overload, the data was encrypted with the TripleDES/3DES/3DEA/DES3-EDE algorithm.</span></span>

<span data-ttu-id="53608-105">En commençant par .NET Core 3.0 Preview 8 (via la version 4.6.0 du package [System.Security.Cryptography.Pkcs](https://www.nuget.org/packages/System.Security.Cryptography.Pkcs/) NuGet), l’algorithme par défaut a été modifié en AES-256 pour la modernisation de l’algorithme et pour améliorer la sécurité des options par défaut.</span><span class="sxs-lookup"><span data-stu-id="53608-105">Starting with .NET Core 3.0 Preview 8 (via version 4.6.0 of the [System.Security.Cryptography.Pkcs](https://www.nuget.org/packages/System.Security.Cryptography.Pkcs/) NuGet package), the default algorithm has been changed to AES-256 for algorithm modernization and to improve the security of default options.</span></span> <span data-ttu-id="53608-106">Si un certificat de destinataire de message a une clé publique (non-EC) <xref:System.Security.Cryptography.CryptographicException> Diffie-Hellman, l’opération de cryptage peut échouer avec un en raison de limitations dans la plate-forme sous-jacente.</span><span class="sxs-lookup"><span data-stu-id="53608-106">If a message recipient certificate has a (non-EC) Diffie-Hellman public key, the encryption operation may fail with a <xref:System.Security.Cryptography.CryptographicException> due to limitations in the underlying platform.</span></span>

<span data-ttu-id="53608-107">Dans le code de l’échantillon suivant, les données sont cryptées avec TripleDES si elles sont en cours d’exécution sur .NET Core 3.0 Aperçu 7 ou plus tôt.</span><span class="sxs-lookup"><span data-stu-id="53608-107">In the following sample code, the data is encrypted with TripleDES if running on .NET Core 3.0 Preview 7 or earlier.</span></span> <span data-ttu-id="53608-108">Si vous exécutez sur .NET Core 3.0 Aperçu 8 ou plus tard, il est crypté avec AES-256.</span><span class="sxs-lookup"><span data-stu-id="53608-108">If running on .NET Core 3.0 Preview 8 or later, it is encrypted with AES-256.</span></span>

```csharp
EnvelopedCms cms = new EnvelopedCms(content);
cms.Encrypt(recipient);
return cms.Encode();
```

#### <a name="version-introduced"></a><span data-ttu-id="53608-109">Version introduite</span><span class="sxs-lookup"><span data-stu-id="53608-109">Version introduced</span></span>

<span data-ttu-id="53608-110">3.0 Aperçu 8</span><span class="sxs-lookup"><span data-stu-id="53608-110">3.0 Preview 8</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="53608-111">Action recommandée</span><span class="sxs-lookup"><span data-stu-id="53608-111">Recommended action</span></span>

<span data-ttu-id="53608-112">Si vous êtes affecté négativement par la modification, vous pouvez restaurer le cryptage <xref:System.Security.Cryptography.Pkcs.EnvelopedCms> TripleDES en spécifiant explicitement l’identifiant de l’algorithme de cryptage dans un constructeur qui inclut un paramètre de type, <xref:System.Security.Cryptography.Pkcs.AlgorithmIdentifier>tel que :</span><span class="sxs-lookup"><span data-stu-id="53608-112">If you are negatively impacted by the change, you can restore TripleDES encryption by explicitly specifying the encryption algorithm identifier in an <xref:System.Security.Cryptography.Pkcs.EnvelopedCms> constructor that includes a parameter of type <xref:System.Security.Cryptography.Pkcs.AlgorithmIdentifier>, such as:</span></span>

```csharp
Oid tripleDesOid = new Oid("1.2.840.113549.3.7", null);
AlgorithmIdentifier tripleDesIdentifier = new AlgorithmIdentifier(tripleDesOid);
EnvelopedCms cms = new EnvelopedCms(content, tripleDesIdentifier);

cms.Encrypt(recipient);
return cms.Encode()l
```

#### <a name="category"></a><span data-ttu-id="53608-113">Category</span><span class="sxs-lookup"><span data-stu-id="53608-113">Category</span></span>

<span data-ttu-id="53608-114">Chiffrement</span><span class="sxs-lookup"><span data-stu-id="53608-114">Cryptography</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="53608-115">API affectées</span><span class="sxs-lookup"><span data-stu-id="53608-115">Affected APIs</span></span>

- <xref:System.Security.Cryptography.Pkcs.EnvelopedCms.%23ctor?displayProperty=nameWithType>
- <xref:System.Security.Cryptography.Pkcs.EnvelopedCms.%23ctor(System.Security.Cryptography.Pkcs.ContentInfo)?displayProperty=nameWithType>
- <xref:System.Security.Cryptography.Pkcs.EnvelopedCms.%23ctor(System.Security.Cryptography.Pkcs.SubjectIdentifierType,System.Security.Cryptography.Pkcs.ContentInfo)?displayProperty=nameWithType>

<!--

### Affected APIs

- `M:System.Security.Cryptography.Pkcs.EnvelopedCms.#ctor`
- `M:System.Security.Cryptography.Pkcs.EnvelopedCms.#ctor(System.Security.Cryptography.Pkcs.ContentInfo)`
- `M:System.Security.Cryptography.Pkcs.EnvelopedCms.%23ctor(System.Security.Cryptography.Pkcs.SubjectIdentifierType,System.Security.Cryptography.Pkcs.ContentInfo)`

-->
