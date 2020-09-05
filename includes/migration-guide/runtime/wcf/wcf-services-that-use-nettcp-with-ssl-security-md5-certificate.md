---
ms.openlocfilehash: afcb9b950d4c47b4251dcc8ab0cf9cfc702005c8
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/05/2020
ms.locfileid: "89496092"
---
### <a name="wcf-services-that-use-nettcp-with-ssl-security-and-md5-certificate-authentication"></a>Services WCF qui utilisent NETTCP avec la sécurité SSL et l’authentification par certificat MD5

#### <a name="details"></a>Détails

Le .NET Framework 4.6 ajoute TLS 1.1 et TLS 1.2 à la liste des protocoles WCF SSL par défaut. Quand .NET Framework 4.6 ou ultérieur est installé sur les ordinateurs client et serveur, TLS 1.2 est utilisé à des fins de négociation. TLS 1.2 ne prend pas en charge l’authentification par certificat MD5. Par conséquent, si un client utilise un certificat MD5, le client WCF ne parviendra pas à se connecter au service WCF.

#### <a name="suggestion"></a>Suggestion

Vous pouvez contourner ce problème afin qu’un client WCF puisse se connecter à un serveur WCF en effectuant une des opérations suivantes :

- Mettez à jour le certificat pour ne pas utiliser l’algorithme MD5. Il s'agit de la solution recommandée.
- Si la liaison n’est pas configurée dynamiquement dans le code source, mettez à jour le fichier de configuration de l’application pour utiliser TLS 1.1 ou une version antérieure du protocole. Cela vous permet de continuer à utiliser un certificat avec l’algorithme de hachage MD5.

> [!WARNING]
> Cette solution de contournement n’est pas recommandée, car un certificat avec l’algorithme de hachage MD5 est considéré comme non sécurisé.

Le fichier de configuration suivant effectue ceci :

```xml
<configuration>
  <system.serviceModel>
    <bindings>
      <netTcpBinding>
        <binding>
          <security mode= "None/Transport/Message/TransportWithMessageCredential" >
            <transport clientCredentialType="None/Windows/Certificate"
                       protectionLevel="None/Sign/EncryptAndSign"
                       sslProtocols="Ssl3/Tls1/Tls11">
            </transport>
          </security>
        </binding>
      </netTcpBinding>
    </bindings>
  </system.ServiceModel>
</configuration>
```

- Si la liaison est configurée dynamiquement dans le code source, mettez à jour la propriété <xref:System.ServiceModel.TcpTransportSecurity.SslProtocols?displayProperty=nameWithType> pour utiliser TLS 1.1 (<xref:System.Security.Authentication.SslProtocols.Tls11?displayProperty=nameWithType> ou une version antérieure du protocole dans le code source.

> [!WARNING]
> Cette solution de contournement n’est pas recommandée, car un certificat avec l’algorithme de hachage MD5 est considéré comme non sécurisé.

| Name    | Valeur   |
|:--------|:--------|
| Étendue   | Secondaire   |
| Version | 4,6     |
| Type    | Runtime |

#### <a name="affected-apis"></a>API affectées

Non détectable via l’analyse des API.

<!--

#### Affected APIs

Not detectable via API analysis.

-->
