---
title: 'Atténuation : Services WCF et authentification par certificat'
ms.date: 03/30/2017
ms.assetid: ef19c91a-b9df-4bf0-a28e-eb1e99c4bc95
ms.openlocfilehash: cc8afaf0592a26f7bab15ab94b04ba4a9bfac930
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73126118"
---
# <a name="mitigation-wcf-services-and-certificate-authentication"></a>Atténuation : Services WCF et authentification par certificat

Le .NET Framework 4.6 ajoute TLS 1.1 et TLS 1.2 à la liste des protocoles WCF SSL par défaut. Lorsque le .NET Framework 4.6 ou ultérieur est installé sur les ordinateurs clients et serveurs, TLS 1.2 est utilisé à des fins de négociation.

## <a name="impact"></a>Impact

TLS 1.2 ne prend pas en charge l’authentification par certificat MD5. Par conséquent, si un client utilise un certificat SSL employant MD5 comme algorithme de hachage, le client WCF ne parvient pas à se connecter au service WCF. Pour plus d’informations, consultez [Atténuation : Services WCF et authentification par certificat](mitigation-wcf-services-and-certificate-authentication.md).

## <a name="mitigation"></a>Atténuation

Vous pouvez contourner ce problème afin qu’un client WCF puisse se connecter à un serveur WCF en effectuant une des opérations suivantes :

- Mettez à jour le certificat pour ne pas utiliser l’algorithme MD5. Il s'agit de la solution recommandée.

- Si la liaison n’est pas configurée dynamiquement dans le code source, mettez à jour le fichier de configuration de l’application pour utiliser TLS 1.1 ou une version antérieure du protocole. Cela vous permet de continuer à utiliser un certificat avec l’algorithme de hachage MD5.

  > [!CAUTION]
  > Cette solution de contournement n’est pas recommandée, car un certificat avec l’algorithme de hachage MD5 est considéré comme non sécurisé.

  Le fichier de configuration suivant effectue ceci :

  ```xml
  <configuration>
      <system.serviceModel>
          <bindings>
              <netTcpBinding>
                  <binding>
                      <security mode= "None|Transport|Message|TransportWithMessageCredential" >
                          <transport clientCredentialType="None|Windows|Certificate"
                                              protectionLevel="None|Sign|EncryptAndSign"
                                              sslProtocols="Ssl3|Tls1|Tls11">
                          </transport>
                      </security>
                  </binding>
              </netTcpBinding>
          </bindings>
      </system.serviceModel>
  </configuration>
  ```

- Si la liaison est configurée dynamiquement dans le code source, mettez à jour la propriété <xref:System.ServiceModel.TcpTransportSecurity.SslProtocols%2A?displayProperty=nameWithType> pour utiliser TLS 1.1 (<xref:System.Security.Authentication.SslProtocols.Tls11?displayProperty=nameWithType>) ou une version antérieure du protocole dans le code source.

  > [!CAUTION]
  > Cette solution de contournement n’est pas recommandée, car un certificat avec l’algorithme de hachage MD5 est considéré comme non sécurisé.

## <a name="see-also"></a>Voir aussi

- [Modifications du runtime](runtime-changes-in-the-net-framework-4-6.md)
