---
title: 'Atténuation : Services WCF et authentification par certificat'
description: Découvrez comment atténuer les problèmes d’authentification de certificat à partir des modifications apportées à la liste par défaut du protocole SSL WCF dans .NET Framework 4,6.
ms.date: 03/30/2017
ms.assetid: ef19c91a-b9df-4bf0-a28e-eb1e99c4bc95
ms.openlocfilehash: b6460e58bb32151003430d6573c4bcf1b514081b
ms.sourcegitcommit: cf5a800a33de64d0aad6d115ffcc935f32375164
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/20/2020
ms.locfileid: "86475370"
---
# <a name="mitigation-wcf-services-and-certificate-authentication"></a>Atténuation : Services WCF et authentification par certificat

Le .NET Framework 4.6 ajoute TLS 1.1 et TLS 1.2 à la liste des protocoles WCF SSL par défaut. Lorsque le .NET Framework 4.6 ou ultérieur est installé sur les ordinateurs clients et serveurs, TLS 1.2 est utilisé à des fins de négociation.

## <a name="impact"></a>Impact

TLS 1.2 ne prend pas en charge l’authentification par certificat MD5. Par conséquent, si un client utilise un certificat SSL qui utilise MD5 pour l’algorithme de hachage, le client WCF ne parvient pas à se connecter au service WCF. Pour plus d’informations, consultez [Atténuation : Services WCF et authentification par certificat](mitigation-wcf-services-and-certificate-authentication.md).

## <a name="mitigation"></a>Limitation des risques

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

- [Compatibilité des applications](application-compatibility.md)
