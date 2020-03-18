---
ms.openlocfilehash: 6a5cd260a2820e2a81142f6d55e32e91173ca503
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79147449"
---
### <a name="openssl-versions-on-macos"></a>Versions OpenSSL sur macOS

Le .NET Core 3.0 et les temps d’exécution plus tard sur macOS préfèrent maintenant OpenSSL 1.1.x <xref:System.Security.Cryptography.AesCcm> <xref:System.Security.Cryptography.AesGcm>versions à OpenSSL 1.0.x versions pour le , , <xref:System.Security.Cryptography.DSAOpenSsl>, <xref:System.Security.Cryptography.ECDiffieHellmanOpenSsl> <xref:System.Security.Cryptography.ECDsaOpenSsl>, , <xref:System.Security.Cryptography.RSAOpenSsl>et <xref:System.Security.Cryptography.SafeEvpPKeyHandle> les types.

Le temps d’exécution .NET Core 2.1 prend désormais en charge les versions OpenSSL 1.1.x, mais préfère toujours les versions OpenSSL 1.0.x.

#### <a name="change-description"></a>Description de la modification

Auparavant, le temps d’exécution .NET Core utilisé OpenSSL 1.0.x versions sur macOS pour les types qui interagissent avec OpenSSL. La plus récente version OpenSSL 1.0.x, OpenSSL 1.0.2, est maintenant hors de support. Pour conserver les types qui utilisent OpenSSL sur les versions prises en charge d’OpenSSL, le .NET Core 3.0 et les temps d’exécution ultérieurs utilisent maintenant de nouvelles versions d’OpenSSL sur macOS.

Avec ce changement, le comportement pour les runtimes .NET Core sur macOS est le suivant:

- Les temps d’exécution .NET Core 3.0 et plus tard de version utilisent OpenSSL 1.1.x, si disponible, et retomber à OpenSSL 1.0.x seulement s’il n’y a pas de version 1.1.x disponible.

  Pour les appelants qui utilisent les types d’interop OpenSSL <xref:System.Security.Cryptography.SafeEvpPKeyHandle.OpenSslVersion?displayProperty=nameWithType> avec P/Invokes personnalisés, suivez les conseils dans les remarques. Votre application peut se planter si <xref:System.Security.Cryptography.SafeEvpPKeyHandle.OpenSslVersion> vous ne vérifiez pas la valeur.

- Le temps d’exécution .NET Core 2.1 utilise OpenSSL 1.0.x, si disponible, et retombe à OpenSSL 1.1.x s’il n’y a pas de version 1.0.x disponible.

  Le temps d’exécution 2.1 préfère la version <xref:System.Security.Cryptography.SafeEvpPKeyHandle.OpenSslVersion?displayProperty=nameWithType> antérieure d’OpenSSL parce que la propriété n’existe pas en .NET Core 2.1, de sorte que la version OpenSSL ne peut pas être déterminée de façon fiable à l’heure d’exécution.

#### <a name="version-introduced"></a>Version introduite

- .NET Core 2.1.16
- .NET Core 3.0.3
- .NET Core 3.1.2

#### <a name="recommended-action"></a>Action recommandée

- Désinstaller la version OpenSSL 1.0.2 si elle n’est plus nécessaire.

- Installez OpenSSL 1.1.x <xref:System.Security.Cryptography.AesCcm>si <xref:System.Security.Cryptography.AesGcm> <xref:System.Security.Cryptography.DSAOpenSsl>vous <xref:System.Security.Cryptography.ECDiffieHellmanOpenSsl> <xref:System.Security.Cryptography.ECDsaOpenSsl>utilisez <xref:System.Security.Cryptography.RSAOpenSsl>le <xref:System.Security.Cryptography.SafeEvpPKeyHandle> , , , , , ou les types.

- Si vous utilisez les types d’interop OpenSSL avec P/Invokes personnalisés, suivez les conseils dans les <xref:System.Security.Cryptography.SafeEvpPKeyHandle.OpenSslVersion?displayProperty=nameWithType> remarques.

#### <a name="category"></a>Category

CoreFx

#### <a name="affected-apis"></a>API affectées

- <xref:System.Security.Cryptography.AesCcm?displayProperty=fullName>
- <xref:System.Security.Cryptography.AesGcm?displayProperty=fullName>
- <xref:System.Security.Cryptography.DSAOpenSsl?displayProperty=fullName>
- <xref:System.Security.Cryptography.ECDiffieHellmanOpenSsl?displayProperty=fullName>
- <xref:System.Security.Cryptography.ECDsaOpenSsl?displayProperty=fullName>
- <xref:System.Security.Cryptography.RSAOpenSsl?displayProperty=fullName>
- <xref:System.Security.Cryptography.SafeEvpPKeyHandle?displayProperty=fullName>

<!--

### Affected APIs

- `T:System.Security.Cryptography.AesCcm``
- `T:System.Security.Cryptography.AesGcm`
- `T:System.Security.Cryptography.DSAOpenSsl`
- `T:System.Security.Cryptography.ECDiffieHellmanOpenSsl`
- `T:System.Security.Cryptography.ECDsaOpenSsl`
- `T:System.Security.Cryptography.RSAOpenSsl`
- `T:System.Security.Cryptography.SafeEvpPKeyHandle`

-->
