---
ms.openlocfilehash: a4476fbff572c004632153e5a98812c241efca57
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/20/2020
ms.locfileid: "83721435"
---
### <a name="openssl-versions-on-macos"></a>Versions OpenSSL sur macOS

Les runtimes .net Core 3,0 et versions ultérieures sur MacOS préfèrent désormais les versions d’OpenSSL 1.1. x aux versions d’OpenSSL 1.0. x pour les <xref:System.Security.Cryptography.AesCcm> <xref:System.Security.Cryptography.AesGcm> types,, <xref:System.Security.Cryptography.DSAOpenSsl> , <xref:System.Security.Cryptography.ECDiffieHellmanOpenSsl> ,, <xref:System.Security.Cryptography.ECDsaOpenSsl> <xref:System.Security.Cryptography.RSAOpenSsl> et <xref:System.Security.Cryptography.SafeEvpPKeyHandle> .

Le Runtime .NET Core 2,1 prend désormais en charge les versions d’OpenSSL 1.1. x, mais il préfère toujours les versions d’OpenSSL 1.0. x.

#### <a name="change-description"></a>Description de la modification

Auparavant, le Runtime .NET Core utilisait des versions d’OpenSSL 1.0. x sur macOS pour les types qui interagissent avec OpenSSL. La version la plus récente d’OpenSSL 1.0. x, OpenSSL 1.0.2, n’est plus prise en charge. Pour conserver les types qui utilisent OpenSSL sur les versions prises en charge d’OpenSSL, les runtimes .NET Core 3,0 et versions ultérieures utilisent désormais des versions plus récentes de OpenSSL sur macOS.

Avec cette modification, le comportement des runtimes .NET Core sur macOS est le suivant :

- Les runtimes .NET Core 3,0 et versions ultérieures utilisent OpenSSL 1.1. x, s’ils sont disponibles, et reviennent à OpenSSL 1.0. x uniquement si aucune version 1.1. x n’est disponible.

  Pour les appelants qui utilisent les types d’interopérabilité OpenSSL avec des P/Invoke personnalisés, suivez les instructions des <xref:System.Security.Cryptography.SafeEvpPKeyHandle.OpenSslVersion?displayProperty=nameWithType> Notes. Votre application peut se bloquer si vous ne vérifiez pas la <xref:System.Security.Cryptography.SafeEvpPKeyHandle.OpenSslVersion> valeur.

- Le Runtime .NET Core 2,1 utilise OpenSSL 1.0. x, s’il est disponible, et revient à OpenSSL 1.1. x si aucune version 1.0. x n’est disponible.

  Le Runtime 2,1 préfère la version antérieure d’OpenSSL, car la <xref:System.Security.Cryptography.SafeEvpPKeyHandle.OpenSslVersion?displayProperty=nameWithType> propriété n’existe pas dans .net Core 2,1, donc la version d’OpenSSL ne peut pas être déterminée de manière fiable au moment de l’exécution.

#### <a name="version-introduced"></a>Version introduite

- 2.1.16 .NET Core
- 3.0.3 .NET Core
- .NET Core 3.1.2

#### <a name="recommended-action"></a>Action recommandée

- Désinstallez OpenSSL version 1.0.2 Si vous n’en avez plus besoin.

- Installez OpenSSL 1.1. x si vous utilisez les <xref:System.Security.Cryptography.AesCcm> types,, <xref:System.Security.Cryptography.AesGcm> <xref:System.Security.Cryptography.DSAOpenSsl> , <xref:System.Security.Cryptography.ECDiffieHellmanOpenSsl> ,, <xref:System.Security.Cryptography.ECDsaOpenSsl> <xref:System.Security.Cryptography.RSAOpenSsl> ou <xref:System.Security.Cryptography.SafeEvpPKeyHandle> .

- Si vous utilisez les types d’interopérabilité OpenSSL avec des P/Invoke personnalisés, suivez les instructions des <xref:System.Security.Cryptography.SafeEvpPKeyHandle.OpenSslVersion?displayProperty=nameWithType> Notes.

#### <a name="category"></a>Category

Bibliothèques .NET Core

#### <a name="affected-apis"></a>API affectées

- <xref:System.Security.Cryptography.AesCcm?displayProperty=fullName>
- <xref:System.Security.Cryptography.AesGcm?displayProperty=fullName>
- <xref:System.Security.Cryptography.DSAOpenSsl?displayProperty=fullName>
- <xref:System.Security.Cryptography.ECDiffieHellmanOpenSsl?displayProperty=fullName>
- <xref:System.Security.Cryptography.ECDsaOpenSsl?displayProperty=fullName>
- <xref:System.Security.Cryptography.RSAOpenSsl?displayProperty=fullName>
- <xref:System.Security.Cryptography.SafeEvpPKeyHandle?displayProperty=fullName>

<!--

#### Affected APIs

- `T:System.Security.Cryptography.AesCcm``
- `T:System.Security.Cryptography.AesGcm`
- `T:System.Security.Cryptography.DSAOpenSsl`
- `T:System.Security.Cryptography.ECDiffieHellmanOpenSsl`
- `T:System.Security.Cryptography.ECDsaOpenSsl`
- `T:System.Security.Cryptography.RSAOpenSsl`
- `T:System.Security.Cryptography.SafeEvpPKeyHandle`

-->
