---
ms.openlocfilehash: 65d8ca480d41a3807473583355fe8be41e0e9701
ms.sourcegitcommit: 7980a91f90ae5eca859db7e6bfa03e23e76a1a50
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/13/2020
ms.locfileid: "81274732"
---
### <a name="net-core-30-prefers-openssl-11x-to-openssl-10x"></a>.NET Core 3,0 préfère OpenSSL 1.1. x à OpenSSL 1.0. x

.NET Core pour Linux, qui fonctionne sur plusieurs distributions Linux, peut prendre en charge à la fois OpenSSL 1.0. x et OpenSSL 1.1. x.  .NET Core 2,1 et .NET Core 2,2 recherchent 1.0. x en premier, puis reviennent à 1.1. x ; .NET Core 3,0 recherche 1.1. x en premier. Cette modification a été apportée pour ajouter la prise en charge de nouvelles normes de chiffrement.

Cette modification peut avoir un impact sur les bibliothèques ou les applications qui effectuent une interopérabilité de la plateforme avec les types d’interopérabilité spécifiques à OpenSSL dans .NET Core.

#### <a name="change-description"></a>Description de la modification

Dans .NET Core 2,2 et versions antérieures, le runtime préfère charger OpenSSL 1.0. x sur 1.1. x. Cela signifie que les <xref:System.IntPtr> types <xref:System.Runtime.InteropServices.SafeHandle> et pour l’interopérabilité avec OpenSSL sont utilisés avec libénigmatique. so. 1.0.0/libénigmatique. so. 1,0/libénigmatique. so. 10 par préférence.

À compter de .NET Core 3,0, le runtime préfère le chargement d’OpenSSL 1.1. x sur OpenSSL 1.0. x. <xref:System.IntPtr> par <xref:System.Runtime.InteropServices.SafeHandle> conséquent, les types et pour l’interopérabilité avec OpenSSL sont utilisés avec libénigmatique. so. 1.1/libénigmatique. so. 11/libénigmatique. so. 1.1.0/libénigmatique. so. 1.1.1 par préférence. Par conséquent, les bibliothèques et les applications qui interagissent directement avec OpenSSL peuvent avoir des pointeurs incompatibles avec les valeurs .NET Core exposées lors de la mise à niveau à partir de .NET Core 2,1 ou .NET Core 2,2.

#### <a name="version-introduced"></a>Version introduite

3.0

#### <a name="recommended-action"></a>Action recommandée

Les bibliothèques et les applications qui effectuent des opérations directes avec OpenSSL doivent veiller à ce qu’elles utilisent la même version d’OpenSSL que le Runtime .NET Core.

Toutes les bibliothèques ou applications qui <xref:System.IntPtr> utilisent <xref:System.Runtime.InteropServices.SafeHandle> ou les valeurs des types de chiffrement .net Core directement avec OpenSSL doivent comparer la version de la bibliothèque qu’ils <xref:System.Security.Cryptography.SafeEvpPKeyHandle.OpenSslVersion?displayProperty=nameWithType> utilisent avec la nouvelle propriété pour garantir la compatibilité des pointeurs.

#### <a name="category"></a>Category

Chiffrement

#### <a name="affected-apis"></a>API affectées

- <xref:System.Security.Cryptography.SafeEvpPKeyHandle.%23ctor%2A>
- <xref:System.Security.Cryptography.RSAOpenSsl.%23ctor(System.IntPtr)>
- <xref:System.Security.Cryptography.RSAOpenSsl.%23ctor(System.Security.Cryptography.SafeEvpPKeyHandle)>
- <xref:System.Security.Cryptography.RSAOpenSsl.DuplicateKeyHandle?displayProperty=nameWithType>
- <xref:System.Security.Cryptography.DSAOpenSsl.%23ctor(System.IntPtr)>
- <xref:System.Security.Cryptography.DSAOpenSsl.%23ctor(System.Security.Cryptography.SafeEvpPKeyHandle)>
- <xref:System.Security.Cryptography.DSAOpenSsl.DuplicateKeyHandle?displayProperty=nameWithType>
- <xref:System.Security.Cryptography.ECDsaOpenSsl.%23ctor(System.IntPtr)>
- <xref:System.Security.Cryptography.ECDsaOpenSsl.%23ctor(System.Security.Cryptography.SafeEvpPKeyHandle)>
- <xref:System.Security.Cryptography.ECDsaOpenSsl.DuplicateKeyHandle?displayProperty=nameWithType>
- <xref:System.Security.Cryptography.ECDiffieHellmanOpenSsl.%23ctor(System.IntPtr)>
- <xref:System.Security.Cryptography.ECDiffieHellmanOpenSsl.%23ctor(System.Security.Cryptography.SafeEvpPKeyHandle)>
- <xref:System.Security.Cryptography.ECDiffieHellmanOpenSsl.DuplicateKeyHandle?displayProperty=nameWithType>
- <xref:System.Security.Cryptography.X509Certificates.X509Certificate.Handle?displayProperty=nameWithType>

<!--

### Affected APIs

- `Overload:System.Security.Cryptography.SafeEvpPKeyHandle.#ctor`
- `M:System.Security.Cryptography.RSAOpenSsl.#ctor(System.IntPtr)`
- `M:System.Security.Cryptography.RSAOpenSsl.#ctor(System.Security.Cryptography.SafeEvpPKeyHandle)`
- `M:System.Security.Cryptography.RSAOpenSsl.DuplicateKeyHandle`
- `M:System.Security.Cryptography.DSAOpenSsl.#ctor(System.IntPtr)`
- `M:System.Security.Cryptography.DSAOpenSsl.#ctor(System.Security.Cryptography.SafeEvpPKeyHandle)`
- `M:System.Security.Cryptography.DSAOpenSsl.DuplicateKeyHandle`
- `M:System.Security.Cryptography.ECDsaOpenSsl.#ctor(System.IntPtr)`
- `M:System.Security.Cryptography.ECDsaOpenSsl.#ctor(System.Security.CryptographySafeEvpPKeyHandle)`
- `M:System.Security.Cryptography.ECDsaOpenSsl.DuplicateKeyHandle`
- `M:System.Security.Cryptography.ECDiffieHellmanOpenSsl.#ctor(System.IntPtr)`
- `M:System.Security.Cryptography.ECDiffieHellmanOpenSsl.#ctor(System.Security.Cryptography.SafeEvpPKeyHandle)`
- `M:System.Security.Cryptography.ECDiffieHellmanOpenSsl.DuplicateKeyHandle`
- `P:System.Security.Cryptography.X509Certificates.X509Certificate.Handle`

-->
