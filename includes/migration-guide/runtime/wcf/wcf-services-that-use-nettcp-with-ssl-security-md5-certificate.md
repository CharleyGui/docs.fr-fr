---
ms.openlocfilehash: afcb9b950d4c47b4251dcc8ab0cf9cfc702005c8
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/05/2020
ms.locfileid: "89496092"
---
### <a name="wcf-services-that-use-nettcp-with-ssl-security-and-md5-certificate-authentication"></a><span data-ttu-id="51fc2-101">Services WCF qui utilisent NETTCP avec la sécurité SSL et l’authentification par certificat MD5</span><span class="sxs-lookup"><span data-stu-id="51fc2-101">WCF services that use NETTCP with SSL security and MD5 certificate authentication</span></span>

#### <a name="details"></a><span data-ttu-id="51fc2-102">Détails</span><span class="sxs-lookup"><span data-stu-id="51fc2-102">Details</span></span>

<span data-ttu-id="51fc2-103">Le .NET Framework 4.6 ajoute TLS 1.1 et TLS 1.2 à la liste des protocoles WCF SSL par défaut.</span><span class="sxs-lookup"><span data-stu-id="51fc2-103">The .NET Framework 4.6 adds TLS 1.1 and TLS 1.2 to the WCF SSL default protocol list.</span></span> <span data-ttu-id="51fc2-104">Quand .NET Framework 4.6 ou ultérieur est installé sur les ordinateurs client et serveur, TLS 1.2 est utilisé à des fins de négociation. TLS 1.2 ne prend pas en charge l’authentification par certificat MD5.</span><span class="sxs-lookup"><span data-stu-id="51fc2-104">When both client and server machines have the .NET Framework 4.6 or later installed, TLS 1.2 is used for negotiation.TLS 1.2 does not support MD5 certificate authentication.</span></span> <span data-ttu-id="51fc2-105">Par conséquent, si un client utilise un certificat MD5, le client WCF ne parviendra pas à se connecter au service WCF.</span><span class="sxs-lookup"><span data-stu-id="51fc2-105">As a result, if a customer uses an MD5 certificate, the WCF client will fail to connect to the WCF service.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="51fc2-106">Suggestion</span><span class="sxs-lookup"><span data-stu-id="51fc2-106">Suggestion</span></span>

<span data-ttu-id="51fc2-107">Vous pouvez contourner ce problème afin qu’un client WCF puisse se connecter à un serveur WCF en effectuant une des opérations suivantes :</span><span class="sxs-lookup"><span data-stu-id="51fc2-107">You can work around this issue so that a WCF client can connect to a WCF server by doing any of the following:</span></span>

- <span data-ttu-id="51fc2-108">Mettez à jour le certificat pour ne pas utiliser l’algorithme MD5.</span><span class="sxs-lookup"><span data-stu-id="51fc2-108">Update the certificate to not use the MD5 algorithm.</span></span> <span data-ttu-id="51fc2-109">Il s'agit de la solution recommandée.</span><span class="sxs-lookup"><span data-stu-id="51fc2-109">This is the recommended solution.</span></span>
- <span data-ttu-id="51fc2-110">Si la liaison n’est pas configurée dynamiquement dans le code source, mettez à jour le fichier de configuration de l’application pour utiliser TLS 1.1 ou une version antérieure du protocole.</span><span class="sxs-lookup"><span data-stu-id="51fc2-110">If the binding is not dynamically configured in source code, update the application's configuration file to use TLS 1.1 or an earlier version of the protocol.</span></span> <span data-ttu-id="51fc2-111">Cela vous permet de continuer à utiliser un certificat avec l’algorithme de hachage MD5.</span><span class="sxs-lookup"><span data-stu-id="51fc2-111">This allows you to continue to use a certificate with the MD5 hash algorithm.</span></span>

> [!WARNING]
> <span data-ttu-id="51fc2-112">Cette solution de contournement n’est pas recommandée, car un certificat avec l’algorithme de hachage MD5 est considéré comme non sécurisé.</span><span class="sxs-lookup"><span data-stu-id="51fc2-112">This workaround is not recommended, since a certificate with the MD5 hash algorithm is considered insecure.</span></span>

<span data-ttu-id="51fc2-113">Le fichier de configuration suivant effectue ceci :</span><span class="sxs-lookup"><span data-stu-id="51fc2-113">The following configuration file does this:</span></span>

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

- <span data-ttu-id="51fc2-114">Si la liaison est configurée dynamiquement dans le code source, mettez à jour la propriété <xref:System.ServiceModel.TcpTransportSecurity.SslProtocols?displayProperty=nameWithType> pour utiliser TLS 1.1 (<xref:System.Security.Authentication.SslProtocols.Tls11?displayProperty=nameWithType> ou une version antérieure du protocole dans le code source.</span><span class="sxs-lookup"><span data-stu-id="51fc2-114">If the binding is dynamically configured in source code, update the <xref:System.ServiceModel.TcpTransportSecurity.SslProtocols?displayProperty=nameWithType> property to use TLS 1.1 (<xref:System.Security.Authentication.SslProtocols.Tls11?displayProperty=nameWithType> or an earlier version of the protocol in the source code.</span></span>

> [!WARNING]
> <span data-ttu-id="51fc2-115">Cette solution de contournement n’est pas recommandée, car un certificat avec l’algorithme de hachage MD5 est considéré comme non sécurisé.</span><span class="sxs-lookup"><span data-stu-id="51fc2-115">This workaround is not recommended, since a certificate with the MD5 hash algorithm is considered insecure.</span></span>

| <span data-ttu-id="51fc2-116">Name</span><span class="sxs-lookup"><span data-stu-id="51fc2-116">Name</span></span>    | <span data-ttu-id="51fc2-117">Valeur</span><span class="sxs-lookup"><span data-stu-id="51fc2-117">Value</span></span>   |
|:--------|:--------|
| <span data-ttu-id="51fc2-118">Étendue</span><span class="sxs-lookup"><span data-stu-id="51fc2-118">Scope</span></span>   | <span data-ttu-id="51fc2-119">Secondaire</span><span class="sxs-lookup"><span data-stu-id="51fc2-119">Minor</span></span>   |
| <span data-ttu-id="51fc2-120">Version</span><span class="sxs-lookup"><span data-stu-id="51fc2-120">Version</span></span> | <span data-ttu-id="51fc2-121">4,6</span><span class="sxs-lookup"><span data-stu-id="51fc2-121">4.6</span></span>     |
| <span data-ttu-id="51fc2-122">Type</span><span class="sxs-lookup"><span data-stu-id="51fc2-122">Type</span></span>    | <span data-ttu-id="51fc2-123">Runtime</span><span class="sxs-lookup"><span data-stu-id="51fc2-123">Runtime</span></span> |

#### <a name="affected-apis"></a><span data-ttu-id="51fc2-124">API affectées</span><span class="sxs-lookup"><span data-stu-id="51fc2-124">Affected APIs</span></span>

<span data-ttu-id="51fc2-125">Non détectable via l’analyse des API.</span><span class="sxs-lookup"><span data-stu-id="51fc2-125">Not detectable via API analysis.</span></span>

<!--

#### Affected APIs

Not detectable via API analysis.

-->
