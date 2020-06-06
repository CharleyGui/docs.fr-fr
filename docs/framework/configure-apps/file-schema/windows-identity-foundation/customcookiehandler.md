---
title: <customCookieHandler>
ms.date: 03/30/2017
ms.assetid: a03b153d-5ec6-4915-9031-6f0c3fd348be
author: BrucePerlerMS
ms.openlocfilehash: e1f32e17cf0da5e948d778e8b61aca6053eff4ef
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/06/2020
ms.locfileid: "70252015"
---
# \<customCookieHandler>
<span data-ttu-id="58d89-101">Définit le type de gestionnaire de cookies personnalisé.</span><span class="sxs-lookup"><span data-stu-id="58d89-101">Sets the custom cookie handler type.</span></span> <span data-ttu-id="58d89-102">Cet élément ne peut être présent que si l' `mode` attribut de l' `<cookieHandler>` élément est « Custom ».</span><span class="sxs-lookup"><span data-stu-id="58d89-102">This element may only be present if the `mode` attribute of the `<cookieHandler>` element is "Custom".</span></span> <span data-ttu-id="58d89-103">Le type personnalisé doit être dérivé de la <xref:System.IdentityModel.Services.CookieHandler> classe.</span><span class="sxs-lookup"><span data-stu-id="58d89-103">The custom type must be derived from the <xref:System.IdentityModel.Services.CookieHandler> class.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.identityModel.services>**](system-identitymodel-services.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<federationConfiguration>**](federationconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<cookieHandler>**](cookiehandler.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<customCookieHandler>**  
  
## <a name="syntax"></a><span data-ttu-id="58d89-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="58d89-104">Syntax</span></span>  
  
```xml  
<system.identityModel.services>  
  <federationConfiguration>  
    <cookieHandler mode="Custom">  
      <customCookieHandler type="MyNamespace.MyCustomCookieHandler, MyAssembly" >  
      </customCookieHandler>  
    </cookieHandler>  
  </federationConfiguration>  
</system.identityModel.services>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="58d89-105">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="58d89-105">Attributes and Elements</span></span>  
 <span data-ttu-id="58d89-106">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="58d89-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="58d89-107">Attributs</span><span class="sxs-lookup"><span data-stu-id="58d89-107">Attributes</span></span>  
  
|<span data-ttu-id="58d89-108">Attribut</span><span class="sxs-lookup"><span data-stu-id="58d89-108">Attribute</span></span>|<span data-ttu-id="58d89-109">Description</span><span class="sxs-lookup"><span data-stu-id="58d89-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="58d89-110">type</span><span class="sxs-lookup"><span data-stu-id="58d89-110">type</span></span>|<span data-ttu-id="58d89-111">Spécifie un type personnalisé qui dérive de la <xref:System.IdentityModel.Services.CookieHandler> classe.</span><span class="sxs-lookup"><span data-stu-id="58d89-111">Specifies a custom type that derives from the <xref:System.IdentityModel.Services.CookieHandler> class.</span></span> <span data-ttu-id="58d89-112">Pour plus d’informations sur la spécification de l' `type` attribut, consultez [références de types personnalisés](../windows-workflow-foundation/index.md).</span><span class="sxs-lookup"><span data-stu-id="58d89-112">For more information about how to specify the `type` attribute, see [Custom Type References](../windows-workflow-foundation/index.md).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="58d89-113">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="58d89-113">Child Elements</span></span>  
 <span data-ttu-id="58d89-114">Aucune</span><span class="sxs-lookup"><span data-stu-id="58d89-114">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="58d89-115">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="58d89-115">Parent Elements</span></span>  
  
|<span data-ttu-id="58d89-116">Élément</span><span class="sxs-lookup"><span data-stu-id="58d89-116">Element</span></span>|<span data-ttu-id="58d89-117">Description</span><span class="sxs-lookup"><span data-stu-id="58d89-117">Description</span></span>|  
|-------------|-----------------|  
|[\<cookieHandler>](cookiehandler.md)|<span data-ttu-id="58d89-118">Configure le <xref:System.IdentityModel.Services.CookieHandler> que <xref:System.IdentityModel.Services.SessionAuthenticationModule> utilise pour lire et écrire des cookies.</span><span class="sxs-lookup"><span data-stu-id="58d89-118">Configures the <xref:System.IdentityModel.Services.CookieHandler> that the <xref:System.IdentityModel.Services.SessionAuthenticationModule> uses to read and write cookies.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="58d89-119">Remarques</span><span class="sxs-lookup"><span data-stu-id="58d89-119">Remarks</span></span>  
 <span data-ttu-id="58d89-120">Quand vous spécifiez un gestionnaire de cookies personnalisé en affectant `mode` à l’attribut de l’élément la valeur `<cookieHandler>` « Custom », vous devez spécifier le type du gestionnaire de cookies personnalisé en incluant un `<customCookieHandler>` élément enfant qui référence le type de gestionnaire de cookie.</span><span class="sxs-lookup"><span data-stu-id="58d89-120">When you specify a custom cookie handler by setting the `mode` attribute of the `<cookieHandler>` element to "Custom", you must specify the type of the custom cookie handler by including a `<customCookieHandler>` child element that references the cookie handler type.</span></span> <span data-ttu-id="58d89-121">Cet élément ne peut pas être spécifié lorsque l' `mode` attribut a la valeur « chunked » ou « default ».</span><span class="sxs-lookup"><span data-stu-id="58d89-121">This element cannot be specified when the `mode` attribute is set to "Chunked" or "Default".</span></span> <span data-ttu-id="58d89-122">Les gestionnaires de cookies personnalisés doivent dériver de la <xref:System.IdentityModel.Services.CookieHandler> classe.</span><span class="sxs-lookup"><span data-stu-id="58d89-122">Custom cookie handlers must derive from the <xref:System.IdentityModel.Services.CookieHandler> class.</span></span>  
  
 <span data-ttu-id="58d89-123">L' `<customCookieHandler>` élément est représenté par la <xref:System.IdentityModel.Configuration.CustomTypeElement> classe.</span><span class="sxs-lookup"><span data-stu-id="58d89-123">The `<customCookieHandler>` element is represented by the <xref:System.IdentityModel.Configuration.CustomTypeElement> class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="58d89-124">Exemple</span><span class="sxs-lookup"><span data-stu-id="58d89-124">Example</span></span>  
 <span data-ttu-id="58d89-125">L’exemple suivant configure le SAM pour utiliser un gestionnaire de cookies personnalisé de type `MyNamespace.MyCustomCookieHandler` .</span><span class="sxs-lookup"><span data-stu-id="58d89-125">The following example configures the SAM to use a custom cookie handler of type `MyNamespace.MyCustomCookieHandler`.</span></span>  
  
```xml  
<cookieHandler mode="Custom">  
    <customCookieHandler type="MyNamespace.MyCustomCookieHandler, MyAssembly" />  
</cookieHandler>  
```  
  
## <a name="see-also"></a><span data-ttu-id="58d89-126">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="58d89-126">See also</span></span>

- <xref:System.IdentityModel.Services.CookieHandler>
