---
title: <dns>
ms.date: 03/30/2017
ms.assetid: 81819dae-4825-43b7-bccd-f16d2d3d2f06
ms.openlocfilehash: e49a564c9793b371425b2b787586bb9d3cbed58b
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/19/2020
ms.locfileid: "77452225"
---
# <a name="dns"></a><span data-ttu-id="0be41-101">> DNS \<</span><span class="sxs-lookup"><span data-stu-id="0be41-101">\<dns></span></span>
<span data-ttu-id="0be41-102">Spécifie l'identité attendue du serveur.</span><span class="sxs-lookup"><span data-stu-id="0be41-102">Specifies the expected identity of the server.</span></span> <span data-ttu-id="0be41-103">Cette identité est valide pour le mode d'authentification du certificat X509 si le certificat du serveur contient un DNS avec la même valeur.</span><span class="sxs-lookup"><span data-stu-id="0be41-103">This identity is valid for X509 Certificate authentication mode if the server’s certificate contains a DNS with the same value.</span></span> <span data-ttu-id="0be41-104">Elle est également valide pour le mode d'authentification Windows si le SPN a la même valeur.</span><span class="sxs-lookup"><span data-stu-id="0be41-104">It is also valid for Windows authentication mode if the SPN has the same value.</span></span>  
  
<span data-ttu-id="0be41-105">Pour plus d’informations sur la définition de la valeur de l’élément, consultez [identité du service et authentification](../../../wcf/feature-details/service-identity-and-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="0be41-105">For more information about setting the element value, see [Service Identity and Authentication](../../../wcf/feature-details/service-identity-and-authentication.md).</span></span>  
  
<span data-ttu-id="0be41-106">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="0be41-106">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="0be41-107">&nbsp;&nbsp;[ **\<> System. serviceModel**](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="0be41-107">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="0be41-108">&nbsp;&nbsp;&nbsp;&nbsp;\<> [**client**](client.md)</span><span class="sxs-lookup"><span data-stu-id="0be41-108">&nbsp;&nbsp;&nbsp;&nbsp;[**\<client>**](client.md)</span></span>\
<span data-ttu-id="0be41-109">&nbsp;&nbsp;&nbsp;&nbsp;[ **&nbsp;&nbsp;\<** ](endpoint-of-client.md) ></span><span class="sxs-lookup"><span data-stu-id="0be41-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpoint>**](endpoint-of-client.md)</span></span>\
<span data-ttu-id="0be41-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;\<> d' [**identité**](identity.md)</span><span class="sxs-lookup"><span data-stu-id="0be41-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<identity>**](identity.md)</span></span>\
<span data-ttu-id="0be41-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;\<**DNS** ></span><span class="sxs-lookup"><span data-stu-id="0be41-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<dns>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0be41-112">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0be41-112">Syntax</span></span>  
  
```xml  
<dns value = "String" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="0be41-113">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="0be41-113">Attributes and Elements</span></span>  
 <span data-ttu-id="0be41-114">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="0be41-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="0be41-115">Attributs</span><span class="sxs-lookup"><span data-stu-id="0be41-115">Attributes</span></span>  
  
|<span data-ttu-id="0be41-116">Attribut</span><span class="sxs-lookup"><span data-stu-id="0be41-116">Attribute</span></span>|<span data-ttu-id="0be41-117">Description</span><span class="sxs-lookup"><span data-stu-id="0be41-117">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="0be41-118">valeur</span><span class="sxs-lookup"><span data-stu-id="0be41-118">value</span></span>|<span data-ttu-id="0be41-119">Système DNS du certificat.</span><span class="sxs-lookup"><span data-stu-id="0be41-119">The DNS of the certificate.</span></span> <span data-ttu-id="0be41-120">Le système DNS est un protocole standard utilisé pour localiser des ordinateurs sur un réseau IP.</span><span class="sxs-lookup"><span data-stu-id="0be41-120">DNS is an industry-standard protocol used to locate computers on an IP-based network.</span></span> <span data-ttu-id="0be41-121">Les utilisateurs peuvent mémoriser les noms d’affichage, tels que `https://go.microsoft.com/fwlink/?prd=10929` ou `https://go.microsoft.com/fwlink/?LinkID=96165`, plus faciles que les adresses basées sur les nombres, par exemple composées.</span><span class="sxs-lookup"><span data-stu-id="0be41-121">Users can remember display names, such as `https://go.microsoft.com/fwlink/?prd=10929` or `https://go.microsoft.com/fwlink/?LinkID=96165`, easier than number-based addresses, such as 207.46.131.137.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="0be41-122">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="0be41-122">Child Elements</span></span>  
 <span data-ttu-id="0be41-123">None.</span><span class="sxs-lookup"><span data-stu-id="0be41-123">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="0be41-124">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="0be41-124">Parent Elements</span></span>  
  
|<span data-ttu-id="0be41-125">Élément</span><span class="sxs-lookup"><span data-stu-id="0be41-125">Element</span></span>|<span data-ttu-id="0be41-126">Description</span><span class="sxs-lookup"><span data-stu-id="0be41-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="0be41-127">\<d’identité ></span><span class="sxs-lookup"><span data-stu-id="0be41-127">\<identity></span></span>](identity.md)|<span data-ttu-id="0be41-128">Spécifie l'identité du service à authentifier par le client.</span><span class="sxs-lookup"><span data-stu-id="0be41-128">Specifies the identity of the service to be authenticated by the client.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="0be41-129">Exemple</span><span class="sxs-lookup"><span data-stu-id="0be41-129">Example</span></span>  
 <span data-ttu-id="0be41-130">Le code de configuration suivant spécifie le système DNS d'un certificat X.509 utilisé pour authentifier un serveur.</span><span class="sxs-lookup"><span data-stu-id="0be41-130">The following configuration code specifies the DNS of an X.509 certificate that is used to authenticate a server.</span></span>  
  
```xml  
<identity>
  <dns value = "www.cohowinery.com" />
</identity>
```  
  
## <a name="see-also"></a><span data-ttu-id="0be41-131">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="0be41-131">See also</span></span>

- <xref:System.ServiceModel.Configuration.IdentityElement>
- <xref:System.ServiceModel.EndpointAddress>
- <xref:System.ServiceModel.EndpointAddress.Identity%2A>
- <xref:System.ServiceModel.DnsEndpointIdentity>
- [<span data-ttu-id="0be41-132">Identité du service et authentification</span><span class="sxs-lookup"><span data-stu-id="0be41-132">Service Identity and Authentication</span></span>](../../../wcf/feature-details/service-identity-and-authentication.md)
- [<span data-ttu-id="0be41-133">\<d’identité ></span><span class="sxs-lookup"><span data-stu-id="0be41-133">\<identity></span></span>](identity.md)
