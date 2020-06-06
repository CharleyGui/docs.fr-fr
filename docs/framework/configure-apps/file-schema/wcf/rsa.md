---
title: <rsa>
ms.date: 03/30/2017
ms.assetid: ae1f2267-e40d-42ff-8abf-06ab7067bdb9
ms.openlocfilehash: 0e1651f563bdb2b2b24eacacf7bfe387e33a82c7
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/06/2020
ms.locfileid: "70855048"
---
# \<rsa>
<span data-ttu-id="d2b43-101">Un client WCF sécurisé qui se connecte à un point de terminaison avec cette identité vérifie que les revendications présentées par le serveur contiennent une revendication intégrant la clé publique RSA utilisée pour construire cette identité.</span><span class="sxs-lookup"><span data-stu-id="d2b43-101">A secure WCF client that connects to an endpoint with this identity verifies that the claims presented by the server contain a claim that contains the RSA public key used to construct this identity.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<client>**](client.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpoint>**](endpoint-of-client.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<identity>**](identity.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<rsa>**  
  
## <a name="syntax"></a><span data-ttu-id="d2b43-102">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d2b43-102">Syntax</span></span>  
  
```xml  
<rsa value="String" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d2b43-103">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="d2b43-103">Attributes and Elements</span></span>  
 <span data-ttu-id="d2b43-104">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="d2b43-104">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d2b43-105">Attributs</span><span class="sxs-lookup"><span data-stu-id="d2b43-105">Attributes</span></span>  
  
|<span data-ttu-id="d2b43-106">Attribut</span><span class="sxs-lookup"><span data-stu-id="d2b43-106">Attribute</span></span>|<span data-ttu-id="d2b43-107">Description</span><span class="sxs-lookup"><span data-stu-id="d2b43-107">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="d2b43-108">value</span><span class="sxs-lookup"><span data-stu-id="d2b43-108">value</span></span>|<span data-ttu-id="d2b43-109">Chaîne facultative.</span><span class="sxs-lookup"><span data-stu-id="d2b43-109">Optional String.</span></span> <span data-ttu-id="d2b43-110">Valeur de clé publique RSA à comparer sur le client.</span><span class="sxs-lookup"><span data-stu-id="d2b43-110">The RSA public key value to be compared with on the client.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="d2b43-111">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="d2b43-111">Child Elements</span></span>  
 <span data-ttu-id="d2b43-112">Aucune</span><span class="sxs-lookup"><span data-stu-id="d2b43-112">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="d2b43-113">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="d2b43-113">Parent Elements</span></span>  
  
|<span data-ttu-id="d2b43-114">Élément</span><span class="sxs-lookup"><span data-stu-id="d2b43-114">Element</span></span>|<span data-ttu-id="d2b43-115">Description</span><span class="sxs-lookup"><span data-stu-id="d2b43-115">Description</span></span>|  
|-------------|-----------------|  
|[\<identity>](identity.md)|<span data-ttu-id="d2b43-116">Spécifie l'identité du service à authentifier par le client.</span><span class="sxs-lookup"><span data-stu-id="d2b43-116">Specifies the identity of the service to be authenticated by the client.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d2b43-117">Remarques</span><span class="sxs-lookup"><span data-stu-id="d2b43-117">Remarks</span></span>  
 <span data-ttu-id="d2b43-118">Un contrôle RSA vous permet de limiter l'authentification à un seul certificat basé sur sa clé RSA ou de générer votre propre valeur de clé RSA.</span><span class="sxs-lookup"><span data-stu-id="d2b43-118">A RSA check enables you to specifically restrict authentication to a single certificate based upon its RSA key or generated your own RSA key value.</span></span> <span data-ttu-id="d2b43-119">Cette opération active une authentification plus stricte d'une clé RSA spécifique aux dépens du service, qui n'utilise plus les clients existants lorsque la valeur de clé RSA est modifiée.</span><span class="sxs-lookup"><span data-stu-id="d2b43-119">This enables stricter authentication of a specific RSA key at the expense of the service no longer working with existing clients if the RSA key value is changed.</span></span>  
  
 <span data-ttu-id="d2b43-120">Pour plus d’informations sur l’utilisation de l’identité pour valider un service auprès d’un client, consultez [identité du service et authentification](../../../wcf/feature-details/service-identity-and-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="d2b43-120">For more information about using identity to validate a service to a client, see [Service Identity and Authentication](../../../wcf/feature-details/service-identity-and-authentication.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="d2b43-121">Exemple</span><span class="sxs-lookup"><span data-stu-id="d2b43-121">Example</span></span>  
 <span data-ttu-id="d2b43-122">Le code de configuration suivant spécifie la valeur de clé publique d'un certificat X.509 utilisé pour authentifier un serveur.</span><span class="sxs-lookup"><span data-stu-id="d2b43-122">The following configuration code specifies the public key value of an X.509 certificate that is used to authenticate a server.</span></span>  
  
```xml  
<identity>
  <rsa value="0000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000" />
</identity>
```  
  
## <a name="see-also"></a><span data-ttu-id="d2b43-123">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d2b43-123">See also</span></span>

- <xref:System.ServiceModel.Configuration.IdentityElement>
- <xref:System.ServiceModel.EndpointAddress>
- <xref:System.ServiceModel.EndpointAddress.Identity%2A>
- <xref:System.ServiceModel.RsaEndpointIdentity>
- [<span data-ttu-id="d2b43-124">Identité du service et authentification</span><span class="sxs-lookup"><span data-stu-id="d2b43-124">Service Identity and Authentication</span></span>](../../../wcf/feature-details/service-identity-and-authentication.md)
- [\<identity>](identity.md)
