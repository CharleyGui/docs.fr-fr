---
title: <dns>
ms.date: 03/30/2017
ms.assetid: 81819dae-4825-43b7-bccd-f16d2d3d2f06
ms.openlocfilehash: 35d33fd4d174c8e4ccdaaf1ac33884663340e16a
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69919122"
---
# <a name="dns"></a><span data-ttu-id="0b47b-101">\<dns></span><span class="sxs-lookup"><span data-stu-id="0b47b-101">\<dns></span></span>
<span data-ttu-id="0b47b-102">Spécifie l'identité attendue du serveur.</span><span class="sxs-lookup"><span data-stu-id="0b47b-102">Specifies the expected identity of the server.</span></span> <span data-ttu-id="0b47b-103">Cette identité est valide pour le mode d'authentification du certificat X509 si le certificat du serveur contient un DNS avec la même valeur.</span><span class="sxs-lookup"><span data-stu-id="0b47b-103">This identity is valid for X509 Certificate authentication mode if the server’s certificate contains a DNS with the same value.</span></span> <span data-ttu-id="0b47b-104">Elle est également valide pour le mode d'authentification Windows si le SPN a la même valeur.</span><span class="sxs-lookup"><span data-stu-id="0b47b-104">It is also valid for Windows authentication mode if the SPN has the same value.</span></span>  
  
 <span data-ttu-id="0b47b-105">Pour plus d’informations sur la définition de la valeur de l’élément, consultez [identité du service et authentification](../../../wcf/feature-details/service-identity-and-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="0b47b-105">For more information about setting the element value, see [Service Identity and Authentication](../../../wcf/feature-details/service-identity-and-authentication.md).</span></span>  
  
 <span data-ttu-id="0b47b-106">\<identity></span><span class="sxs-lookup"><span data-stu-id="0b47b-106">\<identity></span></span>  
<span data-ttu-id="0b47b-107">\<dns></span><span class="sxs-lookup"><span data-stu-id="0b47b-107">\<dns></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0b47b-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0b47b-108">Syntax</span></span>  
  
```xml  
<dns value = "String" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="0b47b-109">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="0b47b-109">Attributes and Elements</span></span>  
 <span data-ttu-id="0b47b-110">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="0b47b-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="0b47b-111">Attributs</span><span class="sxs-lookup"><span data-stu-id="0b47b-111">Attributes</span></span>  
  
|<span data-ttu-id="0b47b-112">Attribut</span><span class="sxs-lookup"><span data-stu-id="0b47b-112">Attribute</span></span>|<span data-ttu-id="0b47b-113">Description</span><span class="sxs-lookup"><span data-stu-id="0b47b-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="0b47b-114">value</span><span class="sxs-lookup"><span data-stu-id="0b47b-114">value</span></span>|<span data-ttu-id="0b47b-115">Système DNS du certificat.</span><span class="sxs-lookup"><span data-stu-id="0b47b-115">The DNS of the certificate.</span></span> <span data-ttu-id="0b47b-116">Le système DNS est un protocole standard utilisé pour localiser des ordinateurs sur un réseau IP.</span><span class="sxs-lookup"><span data-stu-id="0b47b-116">DNS is an industry-standard protocol used to locate computers on an IP-based network.</span></span> <span data-ttu-id="0b47b-117">Les utilisateurs peuvent mémoriser les noms d' <https://go.microsoft.com/fwlink/?prd=10929> affichage [https://go.microsoft.com/fwlink/?LinkID=96165](https://go.microsoft.com/fwlink/?LinkID=96165), tels que ou, plus faciles que les adresses basées sur les nombres, par exemple composées.</span><span class="sxs-lookup"><span data-stu-id="0b47b-117">Users can remember display names, such as <https://go.microsoft.com/fwlink/?prd=10929> or [https://go.microsoft.com/fwlink/?LinkID=96165](https://go.microsoft.com/fwlink/?LinkID=96165), easier than number-based addresses, such as 207.46.131.137.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="0b47b-118">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="0b47b-118">Child Elements</span></span>  
 <span data-ttu-id="0b47b-119">Aucun.</span><span class="sxs-lookup"><span data-stu-id="0b47b-119">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="0b47b-120">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="0b47b-120">Parent Elements</span></span>  
  
|<span data-ttu-id="0b47b-121">Élément</span><span class="sxs-lookup"><span data-stu-id="0b47b-121">Element</span></span>|<span data-ttu-id="0b47b-122">Description</span><span class="sxs-lookup"><span data-stu-id="0b47b-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="0b47b-123">\<identity></span><span class="sxs-lookup"><span data-stu-id="0b47b-123">\<identity></span></span>](identity.md)|<span data-ttu-id="0b47b-124">Spécifie l'identité du service à authentifier par le client.</span><span class="sxs-lookup"><span data-stu-id="0b47b-124">Specifies the identity of the service to be authenticated by the client.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="0b47b-125">Exemple</span><span class="sxs-lookup"><span data-stu-id="0b47b-125">Example</span></span>  
 <span data-ttu-id="0b47b-126">Le code de configuration suivant spécifie le système DNS d'un certificat X.509 utilisé pour authentifier un serveur.</span><span class="sxs-lookup"><span data-stu-id="0b47b-126">The following configuration code specifies the DNS of an X.509 certificate that is used to authenticate a server.</span></span>  
  
```xml  
<identity>
  <dns value = "www.cohowinery.com" />
</identity>
```  
  
## <a name="see-also"></a><span data-ttu-id="0b47b-127">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="0b47b-127">See also</span></span>

- <xref:System.ServiceModel.Configuration.IdentityElement>
- <xref:System.ServiceModel.EndpointAddress>
- <xref:System.ServiceModel.EndpointAddress.Identity%2A>
- <xref:System.ServiceModel.DnsEndpointIdentity>
- [<span data-ttu-id="0b47b-128">Identité du service et authentification</span><span class="sxs-lookup"><span data-stu-id="0b47b-128">Service Identity and Authentication</span></span>](../../../wcf/feature-details/service-identity-and-authentication.md)
- [<span data-ttu-id="0b47b-129">\<identity></span><span class="sxs-lookup"><span data-stu-id="0b47b-129">\<identity></span></span>](identity.md)
