---
ms.openlocfilehash: 9b734fe960165b6d4b97b861cb3e8f31979f25c5
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85621086"
---
### <a name="remove-ssl3-from-the-wcf-transportdefaults"></a><span data-ttu-id="0bed6-101">Suppression de Ssl3 de TransportDefaults dans WCF</span><span class="sxs-lookup"><span data-stu-id="0bed6-101">Remove Ssl3 from the WCF TransportDefaults</span></span>

#### <a name="details"></a><span data-ttu-id="0bed6-102">Détails</span><span class="sxs-lookup"><span data-stu-id="0bed6-102">Details</span></span>

<span data-ttu-id="0bed6-103">Quand vous utilisez NetTcp avec la sécurité du transport et un type d’informations d’identification de certificat, le protocole SSL 3 n’est plus celui utilisé par défaut quand il s’agit de négocier une connexion sécurisée.</span><span class="sxs-lookup"><span data-stu-id="0bed6-103">When using NetTcp with transport security and a credential type of certificate, the SSL 3 protocol is no longer a default protocol used for negotiating a secure connection.</span></span> <span data-ttu-id="0bed6-104">Dans la majorité des cas, cela ne devrait pas avoir de conséquences sur les applications existantes, car TLS 1.0 a toujours figuré dans la liste de protocoles pour NetTcp.</span><span class="sxs-lookup"><span data-stu-id="0bed6-104">In most cases there should be no impact to existing apps as TLS 1.0 has always been included in the protocol list for NetTcp.</span></span> <span data-ttu-id="0bed6-105">Tous les clients existants doivent pouvoir négocier une connexion en utilisant au moins TLS 1.0.</span><span class="sxs-lookup"><span data-stu-id="0bed6-105">All existing clients should be able to negotiate a connection using at least TLS1.0.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="0bed6-106">Suggestion</span><span class="sxs-lookup"><span data-stu-id="0bed6-106">Suggestion</span></span>

<span data-ttu-id="0bed6-107">Si Ssl3 est exigé, utilisez l’un des mécanismes de configuration suivants pour l’ajouter à la liste des protocoles négociés.</span><span class="sxs-lookup"><span data-stu-id="0bed6-107">If Ssl3 is required, use one of the following configuration mechanisms to add Ssl3 to the list of negotiated protocols.</span></span><ul><li><xref:System.ServiceModel.Channels.SslStreamSecurityBindingElement.SslProtocols></li><li><xref:System.ServiceModel.TcpTransportSecurity.SslProtocols></li><li>[<](~/docs/framework/configure-apps/file-schema/wcf/transport-of-nettcpbinding.md)</li><li><span data-ttu-id="0bed6-108">[section &lt;sslStreamSecurity&gt; de &lt;customBinding&gt;]~/docs/framework/configure-apps/file-schema/wcf/sslstreamsecurity.md)</span><span class="sxs-lookup"><span data-stu-id="0bed6-108">[&lt;sslStreamSecurity&gt; section of &lt;customBinding&gt;]~/docs/framework/configure-apps/file-schema/wcf/sslstreamsecurity.md)</span></span></li></ul>

| <span data-ttu-id="0bed6-109">Nom</span><span class="sxs-lookup"><span data-stu-id="0bed6-109">Name</span></span>    | <span data-ttu-id="0bed6-110">Valeur</span><span class="sxs-lookup"><span data-stu-id="0bed6-110">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="0bed6-111">Étendue</span><span class="sxs-lookup"><span data-stu-id="0bed6-111">Scope</span></span>   |<span data-ttu-id="0bed6-112">Edge</span><span class="sxs-lookup"><span data-stu-id="0bed6-112">Edge</span></span>|
|<span data-ttu-id="0bed6-113">Version</span><span class="sxs-lookup"><span data-stu-id="0bed6-113">Version</span></span>|<span data-ttu-id="0bed6-114">4.6.2</span><span class="sxs-lookup"><span data-stu-id="0bed6-114">4.6.2</span></span>|
|<span data-ttu-id="0bed6-115">Type</span><span class="sxs-lookup"><span data-stu-id="0bed6-115">Type</span></span>|<span data-ttu-id="0bed6-116">Runtime</span><span class="sxs-lookup"><span data-stu-id="0bed6-116">Runtime</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="0bed6-117">API affectées</span><span class="sxs-lookup"><span data-stu-id="0bed6-117">Affected APIs</span></span>

-<xref:System.ServiceModel.Channels.SslStreamSecurityBindingElement.SslProtocols?displayProperty=nameWithType></li><li><xref:System.ServiceModel.TcpTransportSecurity.SslProtocols?displayProperty=nameWithType></li></ul>|
