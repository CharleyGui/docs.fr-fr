---
ms.openlocfilehash: 9b734fe960165b6d4b97b861cb3e8f31979f25c5
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85621086"
---
### <a name="remove-ssl3-from-the-wcf-transportdefaults"></a>Suppression de Ssl3 de TransportDefaults dans WCF

#### <a name="details"></a>Détails

Quand vous utilisez NetTcp avec la sécurité du transport et un type d’informations d’identification de certificat, le protocole SSL 3 n’est plus celui utilisé par défaut quand il s’agit de négocier une connexion sécurisée. Dans la majorité des cas, cela ne devrait pas avoir de conséquences sur les applications existantes, car TLS 1.0 a toujours figuré dans la liste de protocoles pour NetTcp. Tous les clients existants doivent pouvoir négocier une connexion en utilisant au moins TLS 1.0.

#### <a name="suggestion"></a>Suggestion

Si Ssl3 est exigé, utilisez l’un des mécanismes de configuration suivants pour l’ajouter à la liste des protocoles négociés.<ul><li><xref:System.ServiceModel.Channels.SslStreamSecurityBindingElement.SslProtocols></li><li><xref:System.ServiceModel.TcpTransportSecurity.SslProtocols></li><li>[<](~/docs/framework/configure-apps/file-schema/wcf/transport-of-nettcpbinding.md)</li><li>[section &lt;sslStreamSecurity&gt; de &lt;customBinding&gt;]~/docs/framework/configure-apps/file-schema/wcf/sslstreamsecurity.md)</li></ul>

| Nom    | Valeur       |
|:--------|:------------|
| Étendue   |Edge|
|Version|4.6.2|
|Type|Runtime

#### <a name="affected-apis"></a>API affectées

-<xref:System.ServiceModel.Channels.SslStreamSecurityBindingElement.SslProtocols?displayProperty=nameWithType></li><li><xref:System.ServiceModel.TcpTransportSecurity.SslProtocols?displayProperty=nameWithType></li></ul>|
