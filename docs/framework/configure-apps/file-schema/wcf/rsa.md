---
title: <rsa>
ms.date: 03/30/2017
ms.assetid: ae1f2267-e40d-42ff-8abf-06ab7067bdb9
ms.openlocfilehash: 0e1651f563bdb2b2b24eacacf7bfe387e33a82c7
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/10/2019
ms.locfileid: "70855048"
---
# <a name="rsa"></a><span data-ttu-id="06568-101">\<rsa></span><span class="sxs-lookup"><span data-stu-id="06568-101">\<rsa></span></span>
<span data-ttu-id="06568-102">Un client WCF sécurisé qui se connecte à un point de terminaison avec cette identité vérifie que les revendications présentées par le serveur contiennent une revendication intégrant la clé publique RSA utilisée pour construire cette identité.</span><span class="sxs-lookup"><span data-stu-id="06568-102">A secure WCF client that connects to an endpoint with this identity verifies that the claims presented by the server contain a claim that contains the RSA public key used to construct this identity.</span></span>  
  
<span data-ttu-id="06568-103">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="06568-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="06568-104">&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="06568-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="06568-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> client**](client.md)</span><span class="sxs-lookup"><span data-stu-id="06568-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<client>**](client.md)</span></span>\
<span data-ttu-id="06568-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<point de terminaison >** ](endpoint-of-client.md)</span><span class="sxs-lookup"><span data-stu-id="06568-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpoint>**](endpoint-of-client.md)</span></span>\
<span data-ttu-id="06568-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> d’identité**](identity.md)</span><span class="sxs-lookup"><span data-stu-id="06568-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<identity>**](identity.md)</span></span>\
<span data-ttu-id="06568-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> RSA**</span><span class="sxs-lookup"><span data-stu-id="06568-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<rsa>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="06568-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="06568-109">Syntax</span></span>  
  
```xml  
<rsa value="String" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="06568-110">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="06568-110">Attributes and Elements</span></span>  
 <span data-ttu-id="06568-111">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="06568-111">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="06568-112">Attributs</span><span class="sxs-lookup"><span data-stu-id="06568-112">Attributes</span></span>  
  
|<span data-ttu-id="06568-113">Attribut</span><span class="sxs-lookup"><span data-stu-id="06568-113">Attribute</span></span>|<span data-ttu-id="06568-114">Description</span><span class="sxs-lookup"><span data-stu-id="06568-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="06568-115">value</span><span class="sxs-lookup"><span data-stu-id="06568-115">value</span></span>|<span data-ttu-id="06568-116">Chaîne facultative.</span><span class="sxs-lookup"><span data-stu-id="06568-116">Optional String.</span></span> <span data-ttu-id="06568-117">Valeur de clé publique RSA à comparer sur le client.</span><span class="sxs-lookup"><span data-stu-id="06568-117">The RSA public key value to be compared with on the client.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="06568-118">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="06568-118">Child Elements</span></span>  
 <span data-ttu-id="06568-119">Aucun</span><span class="sxs-lookup"><span data-stu-id="06568-119">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="06568-120">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="06568-120">Parent Elements</span></span>  
  
|<span data-ttu-id="06568-121">Élément</span><span class="sxs-lookup"><span data-stu-id="06568-121">Element</span></span>|<span data-ttu-id="06568-122">Description</span><span class="sxs-lookup"><span data-stu-id="06568-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="06568-123">\<identity></span><span class="sxs-lookup"><span data-stu-id="06568-123">\<identity></span></span>](identity.md)|<span data-ttu-id="06568-124">Spécifie l'identité du service à authentifier par le client.</span><span class="sxs-lookup"><span data-stu-id="06568-124">Specifies the identity of the service to be authenticated by the client.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="06568-125">Notes</span><span class="sxs-lookup"><span data-stu-id="06568-125">Remarks</span></span>  
 <span data-ttu-id="06568-126">Un contrôle RSA vous permet de limiter l'authentification à un seul certificat basé sur sa clé RSA ou de générer votre propre valeur de clé RSA.</span><span class="sxs-lookup"><span data-stu-id="06568-126">A RSA check enables you to specifically restrict authentication to a single certificate based upon its RSA key or generated your own RSA key value.</span></span> <span data-ttu-id="06568-127">Cette opération active une authentification plus stricte d'une clé RSA spécifique aux dépens du service, qui n'utilise plus les clients existants lorsque la valeur de clé RSA est modifiée.</span><span class="sxs-lookup"><span data-stu-id="06568-127">This enables stricter authentication of a specific RSA key at the expense of the service no longer working with existing clients if the RSA key value is changed.</span></span>  
  
 <span data-ttu-id="06568-128">Pour plus d’informations sur l’utilisation de l’identité pour valider un service auprès d’un client, consultez [identité du service et authentification](../../../wcf/feature-details/service-identity-and-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="06568-128">For more information about using identity to validate a service to a client, see [Service Identity and Authentication](../../../wcf/feature-details/service-identity-and-authentication.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="06568-129">Exemple</span><span class="sxs-lookup"><span data-stu-id="06568-129">Example</span></span>  
 <span data-ttu-id="06568-130">Le code de configuration suivant spécifie la valeur de clé publique d'un certificat X.509 utilisé pour authentifier un serveur.</span><span class="sxs-lookup"><span data-stu-id="06568-130">The following configuration code specifies the public key value of an X.509 certificate that is used to authenticate a server.</span></span>  
  
```xml  
<identity>
  <rsa value="0000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000" />
</identity>
```  
  
## <a name="see-also"></a><span data-ttu-id="06568-131">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="06568-131">See also</span></span>

- <xref:System.ServiceModel.Configuration.IdentityElement>
- <xref:System.ServiceModel.EndpointAddress>
- <xref:System.ServiceModel.EndpointAddress.Identity%2A>
- <xref:System.ServiceModel.RsaEndpointIdentity>
- [<span data-ttu-id="06568-132">Identité du service et authentification</span><span class="sxs-lookup"><span data-stu-id="06568-132">Service Identity and Authentication</span></span>](../../../wcf/feature-details/service-identity-and-authentication.md)
- [<span data-ttu-id="06568-133">\<identity></span><span class="sxs-lookup"><span data-stu-id="06568-133">\<identity></span></span>](identity.md)
