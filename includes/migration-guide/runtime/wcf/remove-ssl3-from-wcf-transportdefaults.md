---
ms.openlocfilehash: a5f4047d70276a90c9d72918a2559fd795feb26e
ms.sourcegitcommit: 261e0c98a111357692b3b63c596edf0cacf72991
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2020
ms.locfileid: "90770777"
---
### <a name="remove-ssl3-from-the-wcf-transportdefaults"></a>Suppression de Ssl3 de TransportDefaults dans WCF

#### <a name="details"></a>Détails

Quand vous utilisez NetTcp avec la sécurité du transport et un type d’informations d’identification de certificat, le protocole SSL 3 n’est plus celui utilisé par défaut quand il s’agit de négocier une connexion sécurisée. Dans la majorité des cas, cela ne devrait pas avoir de conséquences sur les applications existantes, car TLS 1.0 a toujours figuré dans la liste de protocoles pour NetTcp. Tous les clients existants doivent pouvoir négocier une connexion en utilisant au moins TLS 1.0.

#### <a name="suggestion"></a>Suggestion

Si Ssl3 est exigé, utilisez l’un des mécanismes de configuration suivants pour l’ajouter à la liste des protocoles négociés.

- <xref:System.ServiceModel.Channels.SslStreamSecurityBindingElement.SslProtocols>
- <xref:System.ServiceModel.TcpTransportSecurity.SslProtocols>
- [\<transport> of \<netTcpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/transport-of-nettcpbinding.md)
- [\<sslStreamSecurity>](../../../../docs/framework/configure-apps/file-schema/wcf/sslstreamsecurity.md)

| Nom    | Valeur   |
|:--------|:--------|
| Étendue   | Edge    |
| Version | 4.6.2   |
| Type    | Runtime |

#### <a name="affected-apis"></a>API affectées

- <xref:System.ServiceModel.Channels.SslStreamSecurityBindingElement.SslProtocols?displayProperty=nameWithType>
- <xref:System.ServiceModel.TcpTransportSecurity.SslProtocols?displayProperty=nameWithType>

<!--

#### Affected APIs

- `P:System.ServiceModel.Channels.SslStreamSecurityBindingElement.SslProtocols`
- `P:System.ServiceModel.TcpTransportSecurity.SslProtocols`

-->
