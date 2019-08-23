---
title: <rsa>
ms.date: 03/30/2017
ms.assetid: ae1f2267-e40d-42ff-8abf-06ab7067bdb9
ms.openlocfilehash: dd8e5ab11a7c019a8fe967f1c14b88a922a16c33
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69934734"
---
# <a name="rsa"></a><span data-ttu-id="972a2-101">\<rsa></span><span class="sxs-lookup"><span data-stu-id="972a2-101">\<rsa></span></span>
<span data-ttu-id="972a2-102">Un client WCF sécurisé qui se connecte à un point de terminaison avec cette identité vérifie que les revendications présentées par le serveur contiennent une revendication intégrant la clé publique RSA utilisée pour construire cette identité.</span><span class="sxs-lookup"><span data-stu-id="972a2-102">A secure WCF client that connects to an endpoint with this identity verifies that the claims presented by the server contain a claim that contains the RSA public key used to construct this identity.</span></span>  
  
 <span data-ttu-id="972a2-103">\<identity></span><span class="sxs-lookup"><span data-stu-id="972a2-103">\<identity></span></span>  
<span data-ttu-id="972a2-104">\<rsa></span><span class="sxs-lookup"><span data-stu-id="972a2-104">\<rsa></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="972a2-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="972a2-105">Syntax</span></span>  
  
```xml  
<rsa value="String" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="972a2-106">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="972a2-106">Attributes and Elements</span></span>  
 <span data-ttu-id="972a2-107">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="972a2-107">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="972a2-108">Attributs</span><span class="sxs-lookup"><span data-stu-id="972a2-108">Attributes</span></span>  
  
|<span data-ttu-id="972a2-109">Attribut</span><span class="sxs-lookup"><span data-stu-id="972a2-109">Attribute</span></span>|<span data-ttu-id="972a2-110">Description</span><span class="sxs-lookup"><span data-stu-id="972a2-110">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="972a2-111">value</span><span class="sxs-lookup"><span data-stu-id="972a2-111">value</span></span>|<span data-ttu-id="972a2-112">Chaîne facultative.</span><span class="sxs-lookup"><span data-stu-id="972a2-112">Optional String.</span></span> <span data-ttu-id="972a2-113">Valeur de clé publique RSA à comparer sur le client.</span><span class="sxs-lookup"><span data-stu-id="972a2-113">The RSA public key value to be compared with on the client.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="972a2-114">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="972a2-114">Child Elements</span></span>  
 <span data-ttu-id="972a2-115">Aucun</span><span class="sxs-lookup"><span data-stu-id="972a2-115">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="972a2-116">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="972a2-116">Parent Elements</span></span>  
  
|<span data-ttu-id="972a2-117">Élément</span><span class="sxs-lookup"><span data-stu-id="972a2-117">Element</span></span>|<span data-ttu-id="972a2-118">Description</span><span class="sxs-lookup"><span data-stu-id="972a2-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="972a2-119">\<identity></span><span class="sxs-lookup"><span data-stu-id="972a2-119">\<identity></span></span>](identity.md)|<span data-ttu-id="972a2-120">Spécifie l'identité du service à authentifier par le client.</span><span class="sxs-lookup"><span data-stu-id="972a2-120">Specifies the identity of the service to be authenticated by the client.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="972a2-121">Notes</span><span class="sxs-lookup"><span data-stu-id="972a2-121">Remarks</span></span>  
 <span data-ttu-id="972a2-122">Un contrôle RSA vous permet de limiter l'authentification à un seul certificat basé sur sa clé RSA ou de générer votre propre valeur de clé RSA.</span><span class="sxs-lookup"><span data-stu-id="972a2-122">A RSA check enables you to specifically restrict authentication to a single certificate based upon its RSA key or generated your own RSA key value.</span></span> <span data-ttu-id="972a2-123">Cette opération active une authentification plus stricte d'une clé RSA spécifique aux dépens du service, qui n'utilise plus les clients existants lorsque la valeur de clé RSA est modifiée.</span><span class="sxs-lookup"><span data-stu-id="972a2-123">This enables stricter authentication of a specific RSA key at the expense of the service no longer working with existing clients if the RSA key value is changed.</span></span>  
  
 <span data-ttu-id="972a2-124">Pour plus d’informations sur l’utilisation de l’identité pour valider un service auprès d’un client, consultez [identité du service et authentification](../../../wcf/feature-details/service-identity-and-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="972a2-124">For more information about using identity to validate a service to a client, see [Service Identity and Authentication](../../../wcf/feature-details/service-identity-and-authentication.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="972a2-125">Exemples</span><span class="sxs-lookup"><span data-stu-id="972a2-125">Example</span></span>  
 <span data-ttu-id="972a2-126">Le code de configuration suivant spécifie la valeur de clé publique d'un certificat X.509 utilisé pour authentifier un serveur.</span><span class="sxs-lookup"><span data-stu-id="972a2-126">The following configuration code specifies the public key value of an X.509 certificate that is used to authenticate a server.</span></span>  
  
```xml  
<identity>
  <rsa value="0000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000" />
</identity>
```  
  
## <a name="see-also"></a><span data-ttu-id="972a2-127">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="972a2-127">See also</span></span>

- <xref:System.ServiceModel.Configuration.IdentityElement>
- <xref:System.ServiceModel.EndpointAddress>
- <xref:System.ServiceModel.EndpointAddress.Identity%2A>
- <xref:System.ServiceModel.RsaEndpointIdentity>
- [<span data-ttu-id="972a2-128">Identité du service et authentification</span><span class="sxs-lookup"><span data-stu-id="972a2-128">Service Identity and Authentication</span></span>](../../../wcf/feature-details/service-identity-and-authentication.md)
- [<span data-ttu-id="972a2-129">\<identity></span><span class="sxs-lookup"><span data-stu-id="972a2-129">\<identity></span></span>](identity.md)
