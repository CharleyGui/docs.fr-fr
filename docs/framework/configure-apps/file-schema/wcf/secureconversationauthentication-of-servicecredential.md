---
title: <secureConversationAuthentication> de <serviceCredential>
ms.date: 03/30/2017
ms.assetid: 0bd3fac7-befd-4a45-ba51-c200b33be0fd
ms.openlocfilehash: 336969c654f332ae3d838d8fd6d1c4243838539c
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/06/2020
ms.locfileid: "70399940"
---
# <a name="secureconversationauthentication-of-servicecredential"></a><span data-ttu-id="efe3f-102">\<secureConversationAuthentication> de \<serviceCredential></span><span class="sxs-lookup"><span data-stu-id="efe3f-102">\<secureConversationAuthentication> of \<serviceCredential></span></span>
<span data-ttu-id="efe3f-103">Spécifie les paramètres pour un service de conversation sécurisé.</span><span class="sxs-lookup"><span data-stu-id="efe3f-103">Specifies the settings for a secure conversation service.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceCredentials>**](servicecredentials.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<secureConversationAuthentication>**  
  
## <a name="syntax"></a><span data-ttu-id="efe3f-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="efe3f-104">Syntax</span></span>  
  
```xml  
<secureConversationAuthentication securityStateEncoderType="String" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="efe3f-105">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="efe3f-105">Attributes and Elements</span></span>  
 <span data-ttu-id="efe3f-106">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="efe3f-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="efe3f-107">Attributs</span><span class="sxs-lookup"><span data-stu-id="efe3f-107">Attributes</span></span>  
  
|<span data-ttu-id="efe3f-108">Attribut</span><span class="sxs-lookup"><span data-stu-id="efe3f-108">Attribute</span></span>|<span data-ttu-id="efe3f-109">Description</span><span class="sxs-lookup"><span data-stu-id="efe3f-109">Description</span></span>|  
|---------------|-----------------|  
|`securityStateEncoderType`|<span data-ttu-id="efe3f-110">Chaîne qui spécifie le type de <xref:System.ServiceModel.Security.SecurityStateEncoder> à utiliser.</span><span class="sxs-lookup"><span data-stu-id="efe3f-110">A string that specifies the type of <xref:System.ServiceModel.Security.SecurityStateEncoder> to be used.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="efe3f-111">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="efe3f-111">Child Elements</span></span>  
 <span data-ttu-id="efe3f-112">Aucun.</span><span class="sxs-lookup"><span data-stu-id="efe3f-112">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="efe3f-113">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="efe3f-113">Parent Elements</span></span>  
  
|<span data-ttu-id="efe3f-114">Élément</span><span class="sxs-lookup"><span data-stu-id="efe3f-114">Element</span></span>|<span data-ttu-id="efe3f-115">Description</span><span class="sxs-lookup"><span data-stu-id="efe3f-115">Description</span></span>|  
|-------------|-----------------|  
|[\<serviceCredentials>](servicecredentials.md)|<span data-ttu-id="efe3f-116">Spécifie les informations d’identification à utiliser pour authentifier le service, ainsi que les paramètres liés à la validation des informations d’identification du client.</span><span class="sxs-lookup"><span data-stu-id="efe3f-116">Specifies the credential to be used in authenticating the service, and the client credential validation-related settings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="efe3f-117">Remarques</span><span class="sxs-lookup"><span data-stu-id="efe3f-117">Remarks</span></span>  
 <span data-ttu-id="efe3f-118">Utilisez cet élément de configuration pour spécifier la liste des types de revendication connus pour la sérialisation des cookies SCT (Security Context Token), ainsi qu'un encodeur pour encoder et sécuriser les informations de cookies.</span><span class="sxs-lookup"><span data-stu-id="efe3f-118">Use this configuration element to specify a list of known claim types for the Security Context Token (SCT) cookies serialization, as well as an encoder to encode and secure cookies information.</span></span> <span data-ttu-id="efe3f-119">Pour plus d'informations sur SCT, consultez <xref:System.ServiceModel.Security.SecureConversationServiceCredential>.</span><span class="sxs-lookup"><span data-stu-id="efe3f-119">For more information on SCT, see <xref:System.ServiceModel.Security.SecureConversationServiceCredential>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="efe3f-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="efe3f-120">See also</span></span>

- <xref:System.ServiceModel.Configuration.SecureConversationServiceElement>
- <xref:System.ServiceModel.Configuration.ServiceCredentialsElement.SecureConversationAuthentication%2A>
- <xref:System.ServiceModel.Description.ServiceCredentials.SecureConversationAuthentication%2A>
- <xref:System.ServiceModel.Security.SecureConversationServiceCredential>
