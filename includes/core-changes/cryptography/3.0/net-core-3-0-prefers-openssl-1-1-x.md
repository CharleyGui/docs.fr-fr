---
ms.openlocfilehash: b49b2f88b130bb952b77964d5bf38374dc606385
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "74567980"
---
### <a name="net-core-30-prefers-openssl-11x-to-openssl-10x"></a>.NET Core 3.0 préfère OpenSSL 1.1.x à OpenSSL 1.0.x

.NET Core pour Linux, qui fonctionne à travers plusieurs distributions Linux, peut prendre en charge à la fois OpenSSL 1.0.x et OpenSSL 1.1.x.  .NET Core 2.1 et .NET Core 2.2 look for 1.0.x first, then fall back to 1.1.x; .NET Core 3.0 looks for 1.1.x first. Ce changement a été apporté pour renforcer les nouvelles normes cryptographiques.

Ce changement peut avoir un impact sur les bibliothèques ou les applications qui ne plate-forme interop avec les types d’interops OpenSSL spécifiques dans .NET Core.

#### <a name="change-description"></a>Description de la modification

Dans .NET Core 2.2 et les versions antérieures, le temps d’exécution préfère charger OpenSSL 1.0.x sur 1.1.x. Cela signifie <xref:System.IntPtr> que <xref:System.Runtime.InteropServices.SafeHandle> le et les types pour interop avec OpenSSL sont utilisés avec libcrypto.so.1.0.0 / libcrypto.so.1.0 / libcrypto.so.10 par préférence.

À partir de .NET Core 3.0, l’heure d’exécution préfère charger OpenSSL 1.1.x <xref:System.IntPtr> sur <xref:System.Runtime.InteropServices.SafeHandle> OpenSSL 1.0.x, de sorte que le et les types pour interop avec OpenSSL sont utilisés avec libcrypto.so.1.1 / libcrypto.so.11 / libcrypto.so.1.1 / libcrypto.so.1.0 / libcrypto.so.1.1 par préférence. Par conséquent, les bibliothèques et les applications qui interopément avec OpenSSL directement peuvent avoir des indications incompatibles avec les valeurs .NET Core-exposed lors de la mise à niveau de .NET Core 2.1 ou .NET Core 2.2.

#### <a name="version-introduced"></a>Version introduite

3.0

#### <a name="recommended-action"></a>Action recommandée

Les bibliothèques et les applications qui font des opérations directes avec OpenSSL doivent être prudents pour s’assurer qu’ils utilisent la même version d’OpenSSL que le temps d’exécution .NET Core.

Toutes les bibliothèques <xref:System.IntPtr> ou <xref:System.Runtime.InteropServices.SafeHandle> applications qui utilisent ou les valeurs des types cryptographiques .NET Core directement <xref:System.Security.Cryptography.SafeEvpPKeyHandle.OpenSslVersion?displayProperty=nameWithType> avec OpenSSL doivent comparer la version de la bibliothèque qu’ils utilisent avec la nouvelle propriété pour s’assurer que les pointeurs sont compatibles.

#### <a name="category"></a>Category

Chiffrement

#### <a name="affected-apis"></a>API affectées

- <xref:System.Security.Cryptography.SafeEvpPKeyHandle.%23ctor%2A?displayProperty=nameWithType>
- <xref:System.Security.Cryptography.RSAOpenSsl.%23ctor(System.IntPtr)?displayProperty=nameWithType>
- <xref:System.Security.Cryptography.RSAOpenSsl.%23ctor(System.Security.Cryptography.SafeEvpPKeyHandle)?displayProperty=nameWithType>
- <xref:System.Security.Cryptography.RSAOpenSsl.DuplicateKeyHandle?displayProperty=nameWithType>
- <xref:System.Security.Cryptography.DSAOpenSsl.%23ctor(System.IntPtr)?displayProperty=nameWithType>
- <xref:System.Security.Cryptography.DSAOpenSsl.%23ctor(System.Security.Cryptography.SafeEvpPKeyHandle)?displayProperty=nameWithType>
- <xref:System.Security.Cryptography.DSAOpenSsl.DuplicateKeyHandle?displayProperty=nameWithType>
- <xref:System.Security.Cryptography.ECDsaOpenSsl.%23ctor(System.IntPtr)?displayProperty=nameWithType>
- <xref:System.Security.Cryptography.ECDsaOpenSsl.%23ctor(System.Security.Cryptography.SafeEvpPKeyHandle)?displayProperty=nameWithType>
- <xref:System.Security.Cryptography.ECDsaOpenSsl.DuplicateKeyHandle?displayProperty=nameWithType>
- <xref:System.Security.Cryptography.ECDiffieHellmanOpenSsl.%23ctor(System.IntPtr)?displayProperty=nameWithType>
- <xref:System.Security.Cryptography.ECDiffieHellmanOpenSsl.%23ctor(System.Security.Cryptography.SafeEvpPKeyHandle)?displayProperty=nameWithType>
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
