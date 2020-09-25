---
title: <dns>
ms.date: 03/30/2017
ms.assetid: 81819dae-4825-43b7-bccd-f16d2d3d2f06
ms.openlocfilehash: adfd94365ceb0ddc3164a6baef838c16027b4bc3
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91190136"
---
# \<dns>

<span data-ttu-id="70614-101">Spécifie l'identité attendue du serveur.</span><span class="sxs-lookup"><span data-stu-id="70614-101">Specifies the expected identity of the server.</span></span> <span data-ttu-id="70614-102">Cette identité est valide pour le mode d'authentification du certificat X509 si le certificat du serveur contient un DNS avec la même valeur.</span><span class="sxs-lookup"><span data-stu-id="70614-102">This identity is valid for X509 Certificate authentication mode if the server’s certificate contains a DNS with the same value.</span></span> <span data-ttu-id="70614-103">Elle est également valide pour le mode d'authentification Windows si le SPN a la même valeur.</span><span class="sxs-lookup"><span data-stu-id="70614-103">It is also valid for Windows authentication mode if the SPN has the same value.</span></span>  
  
<span data-ttu-id="70614-104">Pour plus d’informations sur la définition de la valeur de l’élément, consultez [identité du service et authentification](../../../wcf/feature-details/service-identity-and-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="70614-104">For more information about setting the element value, see [Service Identity and Authentication](../../../wcf/feature-details/service-identity-and-authentication.md).</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<client>**](client.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpoint>**](endpoint-of-client.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<identity>**](identity.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<dns>**  
  
## <a name="syntax"></a><span data-ttu-id="70614-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="70614-105">Syntax</span></span>  
  
```xml  
<dns value = "String" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="70614-106">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="70614-106">Attributes and Elements</span></span>  

 <span data-ttu-id="70614-107">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="70614-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="70614-108">Attributs</span><span class="sxs-lookup"><span data-stu-id="70614-108">Attributes</span></span>  
  
|<span data-ttu-id="70614-109">Attribut</span><span class="sxs-lookup"><span data-stu-id="70614-109">Attribute</span></span>|<span data-ttu-id="70614-110">Description</span><span class="sxs-lookup"><span data-stu-id="70614-110">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="70614-111">value</span><span class="sxs-lookup"><span data-stu-id="70614-111">value</span></span>|<span data-ttu-id="70614-112">Système DNS du certificat.</span><span class="sxs-lookup"><span data-stu-id="70614-112">The DNS of the certificate.</span></span> <span data-ttu-id="70614-113">Le système DNS est un protocole standard utilisé pour localiser des ordinateurs sur un réseau IP.</span><span class="sxs-lookup"><span data-stu-id="70614-113">DNS is an industry-standard protocol used to locate computers on an IP-based network.</span></span> <span data-ttu-id="70614-114">Les utilisateurs peuvent mémoriser les noms d’affichage, tels que `https://go.microsoft.com/fwlink/?prd=10929` ou `https://go.microsoft.com/fwlink/?LinkID=96165` , plus faciles que les adresses basées sur les nombres, par exemple composées.</span><span class="sxs-lookup"><span data-stu-id="70614-114">Users can remember display names, such as `https://go.microsoft.com/fwlink/?prd=10929` or `https://go.microsoft.com/fwlink/?LinkID=96165`, easier than number-based addresses, such as 207.46.131.137.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="70614-115">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="70614-115">Child Elements</span></span>  

 <span data-ttu-id="70614-116">Aucun.</span><span class="sxs-lookup"><span data-stu-id="70614-116">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="70614-117">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="70614-117">Parent Elements</span></span>  
  
|<span data-ttu-id="70614-118">Élément</span><span class="sxs-lookup"><span data-stu-id="70614-118">Element</span></span>|<span data-ttu-id="70614-119">Description</span><span class="sxs-lookup"><span data-stu-id="70614-119">Description</span></span>|  
|-------------|-----------------|  
|[\<identity>](identity.md)|<span data-ttu-id="70614-120">Spécifie l'identité du service à authentifier par le client.</span><span class="sxs-lookup"><span data-stu-id="70614-120">Specifies the identity of the service to be authenticated by the client.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="70614-121">Exemple</span><span class="sxs-lookup"><span data-stu-id="70614-121">Example</span></span>  

 <span data-ttu-id="70614-122">Le code de configuration suivant spécifie le système DNS d'un certificat X.509 utilisé pour authentifier un serveur.</span><span class="sxs-lookup"><span data-stu-id="70614-122">The following configuration code specifies the DNS of an X.509 certificate that is used to authenticate a server.</span></span>  
  
```xml  
<identity>
  <dns value = "www.cohowinery.com" />
</identity>
```  
  
## <a name="see-also"></a><span data-ttu-id="70614-123">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="70614-123">See also</span></span>

- <xref:System.ServiceModel.Configuration.IdentityElement>
- <xref:System.ServiceModel.EndpointAddress>
- <xref:System.ServiceModel.EndpointAddress.Identity%2A>
- <xref:System.ServiceModel.DnsEndpointIdentity>
- [<span data-ttu-id="70614-124">Identité du service et authentification</span><span class="sxs-lookup"><span data-stu-id="70614-124">Service Identity and Authentication</span></span>](../../../wcf/feature-details/service-identity-and-authentication.md)
- [\<identity>](identity.md)
