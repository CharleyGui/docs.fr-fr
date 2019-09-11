---
title: <certificate> pour <identity>
ms.date: 03/30/2017
ms.assetid: 4aeccaf7-8f23-495c-aa5f-5bd8b5d4a10c
ms.openlocfilehash: 1cfd207afc72cc71359d9d262e30b0696ba63d2b
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/10/2019
ms.locfileid: "70850017"
---
# <a name="certificate-for-identity"></a><span data-ttu-id="ce31d-102">\<> de certificat \<pour l’identité ></span><span class="sxs-lookup"><span data-stu-id="ce31d-102">\<certificate> for \<identity></span></span>
<span data-ttu-id="ce31d-103">Spécifie un certificat X.509 utilisé pour valider un serveur auprès d'un client.</span><span class="sxs-lookup"><span data-stu-id="ce31d-103">Specifies an X.509 certificate used to validate a server to a client.</span></span>  
  
<span data-ttu-id="ce31d-104">Pour plus d’informations sur la définition de la valeur de l’élément, consultez [identité du service et authentification](../../../wcf/feature-details/service-identity-and-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="ce31d-104">For more information about setting the element value, see [Service Identity and Authentication](../../../wcf/feature-details/service-identity-and-authentication.md).</span></span>  
  
<span data-ttu-id="ce31d-105">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="ce31d-105">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="ce31d-106">&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="ce31d-106">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="ce31d-107">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> client**](client.md)</span><span class="sxs-lookup"><span data-stu-id="ce31d-107">&nbsp;&nbsp;&nbsp;&nbsp;[**\<client>**](client.md)</span></span>\
<span data-ttu-id="ce31d-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<point de terminaison >** ](endpoint-of-client.md)</span><span class="sxs-lookup"><span data-stu-id="ce31d-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpoint>**](endpoint-of-client.md)</span></span>\
<span data-ttu-id="ce31d-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> d’identité**](identity.md)</span><span class="sxs-lookup"><span data-stu-id="ce31d-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<identity>**](identity.md)</span></span>\
<span data-ttu-id="ce31d-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> de certificat**</span><span class="sxs-lookup"><span data-stu-id="ce31d-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<certificate>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ce31d-111">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ce31d-111">Syntax</span></span>  
  
```xml  
<certificate encodedValue = "String" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ce31d-112">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="ce31d-112">Attributes and Elements</span></span>  
 <span data-ttu-id="ce31d-113">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="ce31d-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ce31d-114">Attributs</span><span class="sxs-lookup"><span data-stu-id="ce31d-114">Attributes</span></span>  
  
|<span data-ttu-id="ce31d-115">Attribut</span><span class="sxs-lookup"><span data-stu-id="ce31d-115">Attribute</span></span>|<span data-ttu-id="ce31d-116">Description</span><span class="sxs-lookup"><span data-stu-id="ce31d-116">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="ce31d-117">encodedValue</span><span class="sxs-lookup"><span data-stu-id="ce31d-117">encodedValue</span></span>|<span data-ttu-id="ce31d-118">Encodage Base64 du certificat.</span><span class="sxs-lookup"><span data-stu-id="ce31d-118">A Base64 encoding of the certificate.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="ce31d-119">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="ce31d-119">Child Elements</span></span>  
 <span data-ttu-id="ce31d-120">Aucun.</span><span class="sxs-lookup"><span data-stu-id="ce31d-120">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="ce31d-121">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="ce31d-121">Parent Elements</span></span>  
  
|<span data-ttu-id="ce31d-122">Élément</span><span class="sxs-lookup"><span data-stu-id="ce31d-122">Element</span></span>|<span data-ttu-id="ce31d-123">Description</span><span class="sxs-lookup"><span data-stu-id="ce31d-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ce31d-124">\<identity></span><span class="sxs-lookup"><span data-stu-id="ce31d-124">\<identity></span></span>](identity.md)|<span data-ttu-id="ce31d-125">Spécifie l'identité du service à authentifier par le client.</span><span class="sxs-lookup"><span data-stu-id="ce31d-125">Specifies the identity of the service to be authenticated by the client.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="ce31d-126">Exemple</span><span class="sxs-lookup"><span data-stu-id="ce31d-126">Example</span></span>  
 <span data-ttu-id="ce31d-127">Le code suivant spécifie la représentation encodée d'un certificat qui est utilisée pour valider un serveur auprès d'un client.</span><span class="sxs-lookup"><span data-stu-id="ce31d-127">The following code specifies the encoded representation of a certificate used to validate a server to a client.</span></span>  
  
```xml  
<identity>
  <certificate encodedValue="MIIBxjCCAXSgAwIBAgIQmXJgyu9tro1M98GifjtuoDAJBgUrDgMCHQUAMBYxFDASBgNVBAMTC1Jvb3QgQWdlbmN5MB4XDTA2MDUxNzIxNDQyNVoXDTM5MTIzMTIzNTk1OVowKTEQMA4GA1UEChMHQ29udG9zbzEVMBMGA1UEAxMMaWRlbnRpdHkuY29tMIGfMA0GCSqGSIb3DQEBAQUAA4GNADCBiQKBgQDBmivcb8hYbh11hqVoDuB7zmJ2y230f" />
</identity>
```  
  
## <a name="see-also"></a><span data-ttu-id="ce31d-128">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ce31d-128">See also</span></span>

- <xref:System.ServiceModel.Configuration.IdentityElement>
- <xref:System.ServiceModel.EndpointAddress>
- <xref:System.ServiceModel.EndpointAddress.Identity%2A>
- <xref:System.ServiceModel.EndpointIdentity>
- [<span data-ttu-id="ce31d-129">Identité du service et authentification</span><span class="sxs-lookup"><span data-stu-id="ce31d-129">Service Identity and Authentication</span></span>](../../../wcf/feature-details/service-identity-and-authentication.md)
- [<span data-ttu-id="ce31d-130">\<identity></span><span class="sxs-lookup"><span data-stu-id="ce31d-130">\<identity></span></span>](identity.md)
