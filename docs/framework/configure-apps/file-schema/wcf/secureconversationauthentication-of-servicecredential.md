---
title: <secureConversationAuthentication> de <serviceCredential>
ms.date: 03/30/2017
ms.assetid: 0bd3fac7-befd-4a45-ba51-c200b33be0fd
ms.openlocfilehash: 336969c654f332ae3d838d8fd6d1c4243838539c
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70399940"
---
# <a name="secureconversationauthentication-of-servicecredential"></a><span data-ttu-id="f7a00-102">\<SecureConversationAuthentication > de \<serviceCredential ></span><span class="sxs-lookup"><span data-stu-id="f7a00-102">\<secureConversationAuthentication> of \<serviceCredential></span></span>
<span data-ttu-id="f7a00-103">Spécifie les paramètres pour un service de conversation sécurisé.</span><span class="sxs-lookup"><span data-stu-id="f7a00-103">Specifies the settings for a secure conversation service.</span></span>  
  
<span data-ttu-id="f7a00-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="f7a00-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="f7a00-105">&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="f7a00-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="f7a00-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<comportements >** ](behaviors.md)</span><span class="sxs-lookup"><span data-stu-id="f7a00-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)</span></span>\
<span data-ttu-id="f7a00-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<serviceBehaviors >** ](servicebehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="f7a00-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)</span></span>\
<span data-ttu-id="f7a00-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> de comportement**](behavior-of-servicebehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="f7a00-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)</span></span>\
<span data-ttu-id="f7a00-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<serviceCredentials >** ](servicecredentials.md)</span><span class="sxs-lookup"><span data-stu-id="f7a00-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceCredentials>**](servicecredentials.md)</span></span>\
<span data-ttu-id="f7a00-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<secureConversationAuthentication >**</span><span class="sxs-lookup"><span data-stu-id="f7a00-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<secureConversationAuthentication>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f7a00-111">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f7a00-111">Syntax</span></span>  
  
```xml  
<secureConversationAuthentication securityStateEncoderType="String" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f7a00-112">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="f7a00-112">Attributes and Elements</span></span>  
 <span data-ttu-id="f7a00-113">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="f7a00-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f7a00-114">Attributs</span><span class="sxs-lookup"><span data-stu-id="f7a00-114">Attributes</span></span>  
  
|<span data-ttu-id="f7a00-115">Attribut</span><span class="sxs-lookup"><span data-stu-id="f7a00-115">Attribute</span></span>|<span data-ttu-id="f7a00-116">Description</span><span class="sxs-lookup"><span data-stu-id="f7a00-116">Description</span></span>|  
|---------------|-----------------|  
|`securityStateEncoderType`|<span data-ttu-id="f7a00-117">Chaîne qui spécifie le type de <xref:System.ServiceModel.Security.SecurityStateEncoder> à utiliser.</span><span class="sxs-lookup"><span data-stu-id="f7a00-117">A string that specifies the type of <xref:System.ServiceModel.Security.SecurityStateEncoder> to be used.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="f7a00-118">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="f7a00-118">Child Elements</span></span>  
 <span data-ttu-id="f7a00-119">Aucun.</span><span class="sxs-lookup"><span data-stu-id="f7a00-119">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="f7a00-120">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="f7a00-120">Parent Elements</span></span>  
  
|<span data-ttu-id="f7a00-121">Élément</span><span class="sxs-lookup"><span data-stu-id="f7a00-121">Element</span></span>|<span data-ttu-id="f7a00-122">Description</span><span class="sxs-lookup"><span data-stu-id="f7a00-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f7a00-123">\<serviceCredentials></span><span class="sxs-lookup"><span data-stu-id="f7a00-123">\<serviceCredentials></span></span>](servicecredentials.md)|<span data-ttu-id="f7a00-124">Spécifie les informations d’identification à utiliser pour authentifier le service, ainsi que les paramètres liés à la validation des informations d’identification du client.</span><span class="sxs-lookup"><span data-stu-id="f7a00-124">Specifies the credential to be used in authenticating the service, and the client credential validation-related settings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f7a00-125">Notes</span><span class="sxs-lookup"><span data-stu-id="f7a00-125">Remarks</span></span>  
 <span data-ttu-id="f7a00-126">Utilisez cet élément de configuration pour spécifier la liste des types de revendication connus pour la sérialisation des cookies SCT (Security Context Token), ainsi qu'un encodeur pour encoder et sécuriser les informations de cookies.</span><span class="sxs-lookup"><span data-stu-id="f7a00-126">Use this configuration element to specify a list of known claim types for the Security Context Token (SCT) cookies serialization, as well as an encoder to encode and secure cookies information.</span></span> <span data-ttu-id="f7a00-127">Pour plus d'informations sur SCT, consultez <xref:System.ServiceModel.Security.SecureConversationServiceCredential>.</span><span class="sxs-lookup"><span data-stu-id="f7a00-127">For more information on SCT, see <xref:System.ServiceModel.Security.SecureConversationServiceCredential>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f7a00-128">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f7a00-128">See also</span></span>

- <xref:System.ServiceModel.Configuration.SecureConversationServiceElement>
- <xref:System.ServiceModel.Configuration.ServiceCredentialsElement.SecureConversationAuthentication%2A>
- <xref:System.ServiceModel.Description.ServiceCredentials.SecureConversationAuthentication%2A>
- <xref:System.ServiceModel.Security.SecureConversationServiceCredential>
