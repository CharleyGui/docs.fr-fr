---
ms.openlocfilehash: a5f4047d70276a90c9d72918a2559fd795feb26e
ms.sourcegitcommit: 261e0c98a111357692b3b63c596edf0cacf72991
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2020
ms.locfileid: "90770777"
---
### <a name="remove-ssl3-from-the-wcf-transportdefaults"></a><span data-ttu-id="1d0db-101">Suppression de Ssl3 de TransportDefaults dans WCF</span><span class="sxs-lookup"><span data-stu-id="1d0db-101">Remove Ssl3 from the WCF TransportDefaults</span></span>

#### <a name="details"></a><span data-ttu-id="1d0db-102">Détails</span><span class="sxs-lookup"><span data-stu-id="1d0db-102">Details</span></span>

<span data-ttu-id="1d0db-103">Quand vous utilisez NetTcp avec la sécurité du transport et un type d’informations d’identification de certificat, le protocole SSL 3 n’est plus celui utilisé par défaut quand il s’agit de négocier une connexion sécurisée.</span><span class="sxs-lookup"><span data-stu-id="1d0db-103">When using NetTcp with transport security and a credential type of certificate, the SSL 3 protocol is no longer a default protocol used for negotiating a secure connection.</span></span> <span data-ttu-id="1d0db-104">Dans la majorité des cas, cela ne devrait pas avoir de conséquences sur les applications existantes, car TLS 1.0 a toujours figuré dans la liste de protocoles pour NetTcp.</span><span class="sxs-lookup"><span data-stu-id="1d0db-104">In most cases there should be no impact to existing apps as TLS 1.0 has always been included in the protocol list for NetTcp.</span></span> <span data-ttu-id="1d0db-105">Tous les clients existants doivent pouvoir négocier une connexion en utilisant au moins TLS 1.0.</span><span class="sxs-lookup"><span data-stu-id="1d0db-105">All existing clients should be able to negotiate a connection using at least TLS1.0.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="1d0db-106">Suggestion</span><span class="sxs-lookup"><span data-stu-id="1d0db-106">Suggestion</span></span>

<span data-ttu-id="1d0db-107">Si Ssl3 est exigé, utilisez l’un des mécanismes de configuration suivants pour l’ajouter à la liste des protocoles négociés.</span><span class="sxs-lookup"><span data-stu-id="1d0db-107">If Ssl3 is required, use one of the following configuration mechanisms to add Ssl3 to the list of negotiated protocols.</span></span>

- <xref:System.ServiceModel.Channels.SslStreamSecurityBindingElement.SslProtocols>
- <xref:System.ServiceModel.TcpTransportSecurity.SslProtocols>
- [<span data-ttu-id="1d0db-108">\<transport> of \<netTcpBinding></span><span class="sxs-lookup"><span data-stu-id="1d0db-108">\<transport> of \<netTcpBinding></span></span>](../../../../docs/framework/configure-apps/file-schema/wcf/transport-of-nettcpbinding.md)
- [\<sslStreamSecurity>](../../../../docs/framework/configure-apps/file-schema/wcf/sslstreamsecurity.md)

| <span data-ttu-id="1d0db-109">Nom</span><span class="sxs-lookup"><span data-stu-id="1d0db-109">Name</span></span>    | <span data-ttu-id="1d0db-110">Valeur</span><span class="sxs-lookup"><span data-stu-id="1d0db-110">Value</span></span>   |
|:--------|:--------|
| <span data-ttu-id="1d0db-111">Étendue</span><span class="sxs-lookup"><span data-stu-id="1d0db-111">Scope</span></span>   | <span data-ttu-id="1d0db-112">Edge</span><span class="sxs-lookup"><span data-stu-id="1d0db-112">Edge</span></span>    |
| <span data-ttu-id="1d0db-113">Version</span><span class="sxs-lookup"><span data-stu-id="1d0db-113">Version</span></span> | <span data-ttu-id="1d0db-114">4.6.2</span><span class="sxs-lookup"><span data-stu-id="1d0db-114">4.6.2</span></span>   |
| <span data-ttu-id="1d0db-115">Type</span><span class="sxs-lookup"><span data-stu-id="1d0db-115">Type</span></span>    | <span data-ttu-id="1d0db-116">Runtime</span><span class="sxs-lookup"><span data-stu-id="1d0db-116">Runtime</span></span> |

#### <a name="affected-apis"></a><span data-ttu-id="1d0db-117">API affectées</span><span class="sxs-lookup"><span data-stu-id="1d0db-117">Affected APIs</span></span>

- <xref:System.ServiceModel.Channels.SslStreamSecurityBindingElement.SslProtocols?displayProperty=nameWithType>
- <xref:System.ServiceModel.TcpTransportSecurity.SslProtocols?displayProperty=nameWithType>

<!--

#### Affected APIs

- `P:System.ServiceModel.Channels.SslStreamSecurityBindingElement.SslProtocols`
- `P:System.ServiceModel.TcpTransportSecurity.SslProtocols`

-->
