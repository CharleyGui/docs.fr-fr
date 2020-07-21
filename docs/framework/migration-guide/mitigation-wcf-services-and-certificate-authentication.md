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
# <a name="mitigation-wcf-services-and-certificate-authentication"></a><span data-ttu-id="6ee3b-103">Atténuation : Services WCF et authentification par certificat</span><span class="sxs-lookup"><span data-stu-id="6ee3b-103">Mitigation: WCF Services and Certificate Authentication</span></span>

<span data-ttu-id="6ee3b-104">Le .NET Framework 4.6 ajoute TLS 1.1 et TLS 1.2 à la liste des protocoles WCF SSL par défaut.</span><span class="sxs-lookup"><span data-stu-id="6ee3b-104">The .NET Framework 4.6 adds TLS 1.1 and TLS 1.2 to the WCF SSL protocol default list.</span></span> <span data-ttu-id="6ee3b-105">Lorsque le .NET Framework 4.6 ou ultérieur est installé sur les ordinateurs clients et serveurs, TLS 1.2 est utilisé à des fins de négociation.</span><span class="sxs-lookup"><span data-stu-id="6ee3b-105">When both client and server machines have  the .NET Framework 4.6 or later installed, TLS 1.2 is used for negotiation.</span></span>

## <a name="impact"></a><span data-ttu-id="6ee3b-106">Impact</span><span class="sxs-lookup"><span data-stu-id="6ee3b-106">Impact</span></span>

<span data-ttu-id="6ee3b-107">TLS 1.2 ne prend pas en charge l’authentification par certificat MD5.</span><span class="sxs-lookup"><span data-stu-id="6ee3b-107">TLS 1.2 does not support MD5 certificate authentication.</span></span> <span data-ttu-id="6ee3b-108">Par conséquent, si un client utilise un certificat SSL qui utilise MD5 pour l’algorithme de hachage, le client WCF ne parvient pas à se connecter au service WCF.</span><span class="sxs-lookup"><span data-stu-id="6ee3b-108">As a result, if a customer uses an SSL certificate which uses MD5 for the hash algorithm, the WCF client fails to connect to the WCF service.</span></span> <span data-ttu-id="6ee3b-109">Pour plus d’informations, consultez [Atténuation : Services WCF et authentification par certificat](mitigation-wcf-services-and-certificate-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="6ee3b-109">For more information, see [Mitigation: WCF Services and Certificate Authentication](mitigation-wcf-services-and-certificate-authentication.md).</span></span>

## <a name="mitigation"></a><span data-ttu-id="6ee3b-110">Limitation des risques</span><span class="sxs-lookup"><span data-stu-id="6ee3b-110">Mitigation</span></span>

<span data-ttu-id="6ee3b-111">Vous pouvez contourner ce problème afin qu’un client WCF puisse se connecter à un serveur WCF en effectuant une des opérations suivantes :</span><span class="sxs-lookup"><span data-stu-id="6ee3b-111">You can work around this issue so that a WCF client can connect to a WCF server by doing any of the following:</span></span>

- <span data-ttu-id="6ee3b-112">Mettez à jour le certificat pour ne pas utiliser l’algorithme MD5.</span><span class="sxs-lookup"><span data-stu-id="6ee3b-112">Update the certificate to not use the MD5 algorithm.</span></span> <span data-ttu-id="6ee3b-113">Il s'agit de la solution recommandée.</span><span class="sxs-lookup"><span data-stu-id="6ee3b-113">This is the recommended solution.</span></span>

- <span data-ttu-id="6ee3b-114">Si la liaison n’est pas configurée dynamiquement dans le code source, mettez à jour le fichier de configuration de l’application pour utiliser TLS 1.1 ou une version antérieure du protocole.</span><span class="sxs-lookup"><span data-stu-id="6ee3b-114">If the binding is not dynamically configured in source code, update the application's configuration file to use TLS 1.1 or an earlier version of the protocol.</span></span> <span data-ttu-id="6ee3b-115">Cela vous permet de continuer à utiliser un certificat avec l’algorithme de hachage MD5.</span><span class="sxs-lookup"><span data-stu-id="6ee3b-115">This allows you to continue to use a certificate with the MD5 hash algorithm.</span></span>

  > [!CAUTION]
  > <span data-ttu-id="6ee3b-116">Cette solution de contournement n’est pas recommandée, car un certificat avec l’algorithme de hachage MD5 est considéré comme non sécurisé.</span><span class="sxs-lookup"><span data-stu-id="6ee3b-116">This workaround is not recommended, since a certificate with the MD5 hash algorithm is considered insecure.</span></span>

  <span data-ttu-id="6ee3b-117">Le fichier de configuration suivant effectue ceci :</span><span class="sxs-lookup"><span data-stu-id="6ee3b-117">The following configuration file does this:</span></span>

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

- <span data-ttu-id="6ee3b-118">Si la liaison est configurée dynamiquement dans le code source, mettez à jour la propriété <xref:System.ServiceModel.TcpTransportSecurity.SslProtocols%2A?displayProperty=nameWithType> pour utiliser TLS 1.1 (<xref:System.Security.Authentication.SslProtocols.Tls11?displayProperty=nameWithType>) ou une version antérieure du protocole dans le code source.</span><span class="sxs-lookup"><span data-stu-id="6ee3b-118">If the binding is dynamically configured in source code, update the <xref:System.ServiceModel.TcpTransportSecurity.SslProtocols%2A?displayProperty=nameWithType> property to use TLS 1.1 (<xref:System.Security.Authentication.SslProtocols.Tls11?displayProperty=nameWithType>) or an  earlier version of the protocol in the source code.</span></span>

  > [!CAUTION]
  > <span data-ttu-id="6ee3b-119">Cette solution de contournement n’est pas recommandée, car un certificat avec l’algorithme de hachage MD5 est considéré comme non sécurisé.</span><span class="sxs-lookup"><span data-stu-id="6ee3b-119">This workaround is not recommended, since a certificate with the MD5 hash algorithm is considered insecure.</span></span>

## <a name="see-also"></a><span data-ttu-id="6ee3b-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="6ee3b-120">See also</span></span>

- [<span data-ttu-id="6ee3b-121">Compatibilité des applications</span><span class="sxs-lookup"><span data-stu-id="6ee3b-121">Application compatibility</span></span>](application-compatibility.md)
