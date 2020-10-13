---
ms.openlocfilehash: d312ba2a22797ff6afff6b893f998c965e68e86e
ms.sourcegitcommit: e078b7540a8293ca1b604c9c0da1ff1506f0170b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/13/2020
ms.locfileid: "91997758"
---
### <a name="default-tls-cipher-suites-for-net-on-linux"></a>Suites de chiffrement TLS par défaut pour .NET sur Linux

.NET, sur Linux, respecte à présent la configuration OpenSSL pour les suites de chiffrement par défaut lors de l’utilisation de TLS/SSL via la <xref:System.Net.Security.SslStream> classe ou des opérations de niveau supérieur, telles que https via la <xref:System.Net.Http.HttpClient> classe. Lorsque les suites de chiffrement par défaut ne sont pas explicitement configurées, .NET sur Linux utilise une liste restreinte de suites de chiffrement autorisées.

#### <a name="change-description"></a>Description de la modification

Dans les versions précédentes de .NET, .NET ne respecte pas la configuration du système pour les suites de chiffrement par défaut. La liste de suites de chiffrement par défaut pour .NET sur Linux est très permissive.

À compter de .NET 5,0, .NET sur Linux respecte la configuration OpenSSL pour les suites de chiffrement par défaut lorsqu’il est spécifié dans *OpenSSL. cnf*. Lorsque les suites de chiffrement ne sont pas explicitement configurées, les seules suites de chiffrement autorisées sont les suivantes :

- Suites de chiffrement TLS 1,3
- TLS_ECDHE_ECDSA_WITH_AES_256_GCM_SHA384
- TLS_ECDHE_ECDSA_WITH_AES_128_GCM_SHA256
- TLS_ECDHE_RSA_WITH_AES_256_GCM_SHA384
- TLS_ECDHE_RSA_WITH_AES_128_GCM_SHA256
- TLS_ECDHE_ECDSA_WITH_AES_256_CBC_SHA384
- TLS_ECDHE_ECDSA_WITH_AES_128_CBC_SHA256
- TLS_ECDHE_RSA_WITH_AES_256_CBC_SHA384
- TLS_ECDHE_RSA_WITH_AES_128_CBC_SHA256

Étant donné que cette valeur par défaut de secours n’inclut aucune suite de chiffrement compatible avec TLS 1,0 ou TLS 1,1, ces anciennes versions de protocole sont effectivement désactivées par défaut.

La spécification d’une valeur CipherSuitePolicy à SslStream pour une session spécifique remplacera toujours le contenu du fichier de configuration et/ou la valeur par défaut de secours .NET.

#### <a name="reason-for-change"></a>Motif de modification

Les utilisateurs qui exécutent .NET sur Linux ont demandé que la configuration par défaut <xref:System.Net.Security.SslStream> soit remplacée par une valeur qui fournissait un niveau de sécurité élevé à partir d’outils d’évaluation tiers.

#### <a name="version-introduced"></a>Version introduite

5,0 RC1

#### <a name="recommended-action"></a>Action recommandée

Les nouvelles valeurs par défaut sont susceptibles de fonctionner lors de la communication avec les clients ou serveurs modernes. Si vous devez développer la liste des suites de chiffrement par défaut pour accepter les clients hérités (ou pour contacter les serveurs hérités), spécifiez une `CipherSuitePolicy` valeur ou modifiez le fichier de configuration OpenSSL. Dans de nombreuses distributions Linux, le fichier de configuration OpenSSL se trouve sur */etc/SSL/OpenSSL.cnf*.

Cet exemple de fichier *OpenSSL. cnf* est un fichier minimal équivalent à la stratégie de suites de chiffrement par défaut pour .net 5,0 et versions ultérieures sur Linux. Au lieu de remplacer le fichier système, fusionnez ces concepts avec le fichier présent sur votre système.

```ini
openssl_conf = default_conf

[default_conf]
ssl_conf = ssl_sect

[ssl_sect]
system_default = system_default_sect

[system_default_sect]
CipherString = ECDHE-ECDSA-AES256-GCM-SHA384:ECDHE-ECDSA-AES128-GCM-SHA256:ECDHE-RSA-AES256-GCM-SHA384:ECDHE-RSA-AES128-GCM-SHA256:ECDHE-ECDSA-AES256-SHA384:ECDHE-ECDSA-AES128-SHA256:ECDHE-RSA-AES256-SHA384:ECDHE-RSA-AES128-SHA256
```

Sur les distributions Red Hat Enterprise Linux, CentOS et Fedora, les applications .NET ont par défaut les suites de chiffrement autorisées par les stratégies de chiffrement à l’ensemble du système. Sur ces distributions, utilisez la configuration des stratégies de chiffrement au lieu de *OpenSSL. cnf*.

#### <a name="category"></a>Category

- Chiffrement
- Sécurité

#### <a name="affected-apis"></a>API affectées

Non detectible via l’analyse des API.

<!--

#### Affected APIs

- Not detectible via API analysis.

-->
