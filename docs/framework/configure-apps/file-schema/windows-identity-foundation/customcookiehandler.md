---
title: <customCookieHandler>
ms.date: 03/30/2017
ms.assetid: a03b153d-5ec6-4915-9031-6f0c3fd348be
author: BrucePerlerMS
ms.openlocfilehash: e1f32e17cf0da5e948d778e8b61aca6053eff4ef
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70252015"
---
# <a name="customcookiehandler"></a><span data-ttu-id="53dc1-101">\<customCookieHandler></span><span class="sxs-lookup"><span data-stu-id="53dc1-101">\<customCookieHandler></span></span>
<span data-ttu-id="53dc1-102">Définit le type de gestionnaire de cookies personnalisé.</span><span class="sxs-lookup"><span data-stu-id="53dc1-102">Sets the custom cookie handler type.</span></span> <span data-ttu-id="53dc1-103">Cet élément ne peut être présent que si `mode` l’attribut de `<cookieHandler>` l’élément est « Custom ».</span><span class="sxs-lookup"><span data-stu-id="53dc1-103">This element may only be present if the `mode` attribute of the `<cookieHandler>` element is "Custom".</span></span> <span data-ttu-id="53dc1-104">Le type personnalisé doit être dérivé de la <xref:System.IdentityModel.Services.CookieHandler> classe.</span><span class="sxs-lookup"><span data-stu-id="53dc1-104">The custom type must be derived from the <xref:System.IdentityModel.Services.CookieHandler> class.</span></span>  
  
<span data-ttu-id="53dc1-105">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="53dc1-105">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="53dc1-106">&nbsp;&nbsp;[ **\<System. identityModel. services >** ](system-identitymodel-services.md)</span><span class="sxs-lookup"><span data-stu-id="53dc1-106">&nbsp;&nbsp;[**\<system.identityModel.services>**](system-identitymodel-services.md)</span></span>\
<span data-ttu-id="53dc1-107">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<federationConfiguration >** ](federationconfiguration.md)</span><span class="sxs-lookup"><span data-stu-id="53dc1-107">&nbsp;&nbsp;&nbsp;&nbsp;[**\<federationConfiguration>**](federationconfiguration.md)</span></span>\
<span data-ttu-id="53dc1-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<cookieHandler >** ](cookiehandler.md)</span><span class="sxs-lookup"><span data-stu-id="53dc1-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<cookieHandler>**](cookiehandler.md)</span></span>\
<span data-ttu-id="53dc1-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<customCookieHandler >**</span><span class="sxs-lookup"><span data-stu-id="53dc1-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<customCookieHandler>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="53dc1-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="53dc1-110">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="53dc1-111">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="53dc1-111">Attributes and Elements</span></span>  
 <span data-ttu-id="53dc1-112">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="53dc1-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="53dc1-113">Attributs</span><span class="sxs-lookup"><span data-stu-id="53dc1-113">Attributes</span></span>  
  
|<span data-ttu-id="53dc1-114">Attribut</span><span class="sxs-lookup"><span data-stu-id="53dc1-114">Attribute</span></span>|<span data-ttu-id="53dc1-115">Description</span><span class="sxs-lookup"><span data-stu-id="53dc1-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="53dc1-116">type</span><span class="sxs-lookup"><span data-stu-id="53dc1-116">type</span></span>|<span data-ttu-id="53dc1-117">Spécifie un type personnalisé qui dérive de <xref:System.IdentityModel.Services.CookieHandler> la classe.</span><span class="sxs-lookup"><span data-stu-id="53dc1-117">Specifies a custom type that derives from the <xref:System.IdentityModel.Services.CookieHandler> class.</span></span> <span data-ttu-id="53dc1-118">Pour plus d’informations sur la spécification de `type` l’attribut, consultez [références de types personnalisés](../windows-workflow-foundation/index.md).</span><span class="sxs-lookup"><span data-stu-id="53dc1-118">For more information about how to specify the `type` attribute, see [Custom Type References](../windows-workflow-foundation/index.md).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="53dc1-119">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="53dc1-119">Child Elements</span></span>  
 <span data-ttu-id="53dc1-120">Aucun</span><span class="sxs-lookup"><span data-stu-id="53dc1-120">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="53dc1-121">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="53dc1-121">Parent Elements</span></span>  
  
|<span data-ttu-id="53dc1-122">Élément</span><span class="sxs-lookup"><span data-stu-id="53dc1-122">Element</span></span>|<span data-ttu-id="53dc1-123">Description</span><span class="sxs-lookup"><span data-stu-id="53dc1-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="53dc1-124">\<cookieHandler></span><span class="sxs-lookup"><span data-stu-id="53dc1-124">\<cookieHandler></span></span>](cookiehandler.md)|<span data-ttu-id="53dc1-125">Configure le <xref:System.IdentityModel.Services.CookieHandler> <xref:System.IdentityModel.Services.SessionAuthenticationModule> que utilise pour lire et écrire des cookies.</span><span class="sxs-lookup"><span data-stu-id="53dc1-125">Configures the <xref:System.IdentityModel.Services.CookieHandler> that the <xref:System.IdentityModel.Services.SessionAuthenticationModule> uses to read and write cookies.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="53dc1-126">Notes</span><span class="sxs-lookup"><span data-stu-id="53dc1-126">Remarks</span></span>  
 <span data-ttu-id="53dc1-127">Quand vous spécifiez un gestionnaire de cookies personnalisé en `mode` affectant à `<cookieHandler>` l’attribut de l’élément la valeur « Custom », vous devez spécifier le type du gestionnaire de `<customCookieHandler>` cookies personnalisé en incluant un élément enfant qui référence le type de gestionnaire de cookie.</span><span class="sxs-lookup"><span data-stu-id="53dc1-127">When you specify a custom cookie handler by setting the `mode` attribute of the `<cookieHandler>` element to "Custom", you must specify the type of the custom cookie handler by including a `<customCookieHandler>` child element that references the cookie handler type.</span></span> <span data-ttu-id="53dc1-128">Cet élément ne peut pas être spécifié `mode` lorsque l’attribut a la valeur « chunked » ou « default ».</span><span class="sxs-lookup"><span data-stu-id="53dc1-128">This element cannot be specified when the `mode` attribute is set to "Chunked" or "Default".</span></span> <span data-ttu-id="53dc1-129">Les gestionnaires de cookies personnalisés doivent dériver <xref:System.IdentityModel.Services.CookieHandler> de la classe.</span><span class="sxs-lookup"><span data-stu-id="53dc1-129">Custom cookie handlers must derive from the <xref:System.IdentityModel.Services.CookieHandler> class.</span></span>  
  
 <span data-ttu-id="53dc1-130">L' `<customCookieHandler>` élément est représenté par la <xref:System.IdentityModel.Configuration.CustomTypeElement> classe.</span><span class="sxs-lookup"><span data-stu-id="53dc1-130">The `<customCookieHandler>` element is represented by the <xref:System.IdentityModel.Configuration.CustomTypeElement> class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="53dc1-131">Exemples</span><span class="sxs-lookup"><span data-stu-id="53dc1-131">Example</span></span>  
 <span data-ttu-id="53dc1-132">L’exemple suivant configure le SAM pour utiliser un gestionnaire de cookies personnalisé de type `MyNamespace.MyCustomCookieHandler`.</span><span class="sxs-lookup"><span data-stu-id="53dc1-132">The following example configures the SAM to use a custom cookie handler of type `MyNamespace.MyCustomCookieHandler`.</span></span>  
  
```xml  
<cookieHandler mode="Custom">  
    <customCookieHandler type="MyNamespace.MyCustomCookieHandler, MyAssembly" />  
</cookieHandler>  
```  
  
## <a name="see-also"></a><span data-ttu-id="53dc1-133">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="53dc1-133">See also</span></span>

- <xref:System.IdentityModel.Services.CookieHandler>
