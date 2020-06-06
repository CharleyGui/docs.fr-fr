---
title: <certificate> pour <identity>
ms.date: 03/30/2017
ms.assetid: 4aeccaf7-8f23-495c-aa5f-5bd8b5d4a10c
ms.openlocfilehash: 1cfd207afc72cc71359d9d262e30b0696ba63d2b
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/06/2020
ms.locfileid: "70850017"
---
# <a name="certificate-for-identity"></a><span data-ttu-id="b7087-102">\<certificate> pour \<identity></span><span class="sxs-lookup"><span data-stu-id="b7087-102">\<certificate> for \<identity></span></span>
<span data-ttu-id="b7087-103">Spécifie un certificat X.509 utilisé pour valider un serveur auprès d'un client.</span><span class="sxs-lookup"><span data-stu-id="b7087-103">Specifies an X.509 certificate used to validate a server to a client.</span></span>  
  
<span data-ttu-id="b7087-104">Pour plus d’informations sur la définition de la valeur de l’élément, consultez [identité du service et authentification](../../../wcf/feature-details/service-identity-and-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="b7087-104">For more information about setting the element value, see [Service Identity and Authentication](../../../wcf/feature-details/service-identity-and-authentication.md).</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<client>**](client.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpoint>**](endpoint-of-client.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<identity>**](identity.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<certificate>**  
  
## <a name="syntax"></a><span data-ttu-id="b7087-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b7087-105">Syntax</span></span>  
  
```xml  
<certificate encodedValue = "String" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b7087-106">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="b7087-106">Attributes and Elements</span></span>  
 <span data-ttu-id="b7087-107">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="b7087-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b7087-108">Attributs</span><span class="sxs-lookup"><span data-stu-id="b7087-108">Attributes</span></span>  
  
|<span data-ttu-id="b7087-109">Attribut</span><span class="sxs-lookup"><span data-stu-id="b7087-109">Attribute</span></span>|<span data-ttu-id="b7087-110">Description</span><span class="sxs-lookup"><span data-stu-id="b7087-110">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="b7087-111">encodedValue</span><span class="sxs-lookup"><span data-stu-id="b7087-111">encodedValue</span></span>|<span data-ttu-id="b7087-112">Encodage Base64 du certificat.</span><span class="sxs-lookup"><span data-stu-id="b7087-112">A Base64 encoding of the certificate.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="b7087-113">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="b7087-113">Child Elements</span></span>  
 <span data-ttu-id="b7087-114">Aucun.</span><span class="sxs-lookup"><span data-stu-id="b7087-114">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="b7087-115">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="b7087-115">Parent Elements</span></span>  
  
|<span data-ttu-id="b7087-116">Élément</span><span class="sxs-lookup"><span data-stu-id="b7087-116">Element</span></span>|<span data-ttu-id="b7087-117">Description</span><span class="sxs-lookup"><span data-stu-id="b7087-117">Description</span></span>|  
|-------------|-----------------|  
|[\<identity>](identity.md)|<span data-ttu-id="b7087-118">Spécifie l'identité du service à authentifier par le client.</span><span class="sxs-lookup"><span data-stu-id="b7087-118">Specifies the identity of the service to be authenticated by the client.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="b7087-119">Exemple</span><span class="sxs-lookup"><span data-stu-id="b7087-119">Example</span></span>  
 <span data-ttu-id="b7087-120">Le code suivant spécifie la représentation encodée d'un certificat qui est utilisée pour valider un serveur auprès d'un client.</span><span class="sxs-lookup"><span data-stu-id="b7087-120">The following code specifies the encoded representation of a certificate used to validate a server to a client.</span></span>  
  
```xml  
<identity>
  <certificate encodedValue="MIIBxjCCAXSgAwIBAgIQmXJgyu9tro1M98GifjtuoDAJBgUrDgMCHQUAMBYxFDASBgNVBAMTC1Jvb3QgQWdlbmN5MB4XDTA2MDUxNzIxNDQyNVoXDTM5MTIzMTIzNTk1OVowKTEQMA4GA1UEChMHQ29udG9zbzEVMBMGA1UEAxMMaWRlbnRpdHkuY29tMIGfMA0GCSqGSIb3DQEBAQUAA4GNADCBiQKBgQDBmivcb8hYbh11hqVoDuB7zmJ2y230f" />
</identity>
```  
  
## <a name="see-also"></a><span data-ttu-id="b7087-121">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b7087-121">See also</span></span>

- <xref:System.ServiceModel.Configuration.IdentityElement>
- <xref:System.ServiceModel.EndpointAddress>
- <xref:System.ServiceModel.EndpointAddress.Identity%2A>
- <xref:System.ServiceModel.EndpointIdentity>
- [<span data-ttu-id="b7087-122">Identité du service et authentification</span><span class="sxs-lookup"><span data-stu-id="b7087-122">Service Identity and Authentication</span></span>](../../../wcf/feature-details/service-identity-and-authentication.md)
- [\<identity>](identity.md)
