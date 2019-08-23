---
title: <customCookieHandler>
ms.date: 03/30/2017
ms.assetid: a03b153d-5ec6-4915-9031-6f0c3fd348be
author: BrucePerlerMS
ms.openlocfilehash: ebf1f7f3de1b44dba63977bf524dea9af2690fb1
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69942784"
---
# <a name="customcookiehandler"></a><span data-ttu-id="c052d-101">\<customCookieHandler></span><span class="sxs-lookup"><span data-stu-id="c052d-101">\<customCookieHandler></span></span>
<span data-ttu-id="c052d-102">Définit le type de gestionnaire de cookies personnalisé.</span><span class="sxs-lookup"><span data-stu-id="c052d-102">Sets the custom cookie handler type.</span></span> <span data-ttu-id="c052d-103">Cet élément ne peut être présent que si `mode` l’attribut de `<cookieHandler>` l’élément est «Custom».</span><span class="sxs-lookup"><span data-stu-id="c052d-103">This element may only be present if the `mode` attribute of the `<cookieHandler>` element is "Custom".</span></span> <span data-ttu-id="c052d-104">Le type personnalisé doit être dérivé de la <xref:System.IdentityModel.Services.CookieHandler> classe.</span><span class="sxs-lookup"><span data-stu-id="c052d-104">The custom type must be derived from the <xref:System.IdentityModel.Services.CookieHandler> class.</span></span>  
  
 <span data-ttu-id="c052d-105">\<system.identityModel.services></span><span class="sxs-lookup"><span data-stu-id="c052d-105">\<system.identityModel.services></span></span>  
<span data-ttu-id="c052d-106">\<federationConfiguration></span><span class="sxs-lookup"><span data-stu-id="c052d-106">\<federationConfiguration></span></span>  
<span data-ttu-id="c052d-107">\<cookieHandler></span><span class="sxs-lookup"><span data-stu-id="c052d-107">\<cookieHandler></span></span>  
<span data-ttu-id="c052d-108">\<customCookieHandler></span><span class="sxs-lookup"><span data-stu-id="c052d-108">\<customCookieHandler></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c052d-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c052d-109">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c052d-110">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="c052d-110">Attributes and Elements</span></span>  
 <span data-ttu-id="c052d-111">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="c052d-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c052d-112">Attributs</span><span class="sxs-lookup"><span data-stu-id="c052d-112">Attributes</span></span>  
  
|<span data-ttu-id="c052d-113">Attribut</span><span class="sxs-lookup"><span data-stu-id="c052d-113">Attribute</span></span>|<span data-ttu-id="c052d-114">Description</span><span class="sxs-lookup"><span data-stu-id="c052d-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="c052d-115">type</span><span class="sxs-lookup"><span data-stu-id="c052d-115">type</span></span>|<span data-ttu-id="c052d-116">Spécifie un type personnalisé qui dérive de <xref:System.IdentityModel.Services.CookieHandler> la classe.</span><span class="sxs-lookup"><span data-stu-id="c052d-116">Specifies a custom type that derives from the <xref:System.IdentityModel.Services.CookieHandler> class.</span></span> <span data-ttu-id="c052d-117">Pour plus d’informations sur la spécification de `type` l’attribut, consultez [références de types personnalisés](../windows-workflow-foundation/index.md).</span><span class="sxs-lookup"><span data-stu-id="c052d-117">For more information about how to specify the `type` attribute, see [Custom Type References](../windows-workflow-foundation/index.md).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="c052d-118">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="c052d-118">Child Elements</span></span>  
 <span data-ttu-id="c052d-119">Aucun</span><span class="sxs-lookup"><span data-stu-id="c052d-119">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="c052d-120">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="c052d-120">Parent Elements</span></span>  
  
|<span data-ttu-id="c052d-121">Élément</span><span class="sxs-lookup"><span data-stu-id="c052d-121">Element</span></span>|<span data-ttu-id="c052d-122">Description</span><span class="sxs-lookup"><span data-stu-id="c052d-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c052d-123">\<cookieHandler></span><span class="sxs-lookup"><span data-stu-id="c052d-123">\<cookieHandler></span></span>](cookiehandler.md)|<span data-ttu-id="c052d-124">Configure le <xref:System.IdentityModel.Services.CookieHandler> <xref:System.IdentityModel.Services.SessionAuthenticationModule> que utilise pour lire et écrire des cookies.</span><span class="sxs-lookup"><span data-stu-id="c052d-124">Configures the <xref:System.IdentityModel.Services.CookieHandler> that the <xref:System.IdentityModel.Services.SessionAuthenticationModule> uses to read and write cookies.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c052d-125">Notes</span><span class="sxs-lookup"><span data-stu-id="c052d-125">Remarks</span></span>  
 <span data-ttu-id="c052d-126">Quand vous spécifiez un gestionnaire de cookies personnalisé en `mode` affectant à `<cookieHandler>` l’attribut de l’élément la valeur «Custom», vous devez spécifier le type du gestionnaire de `<customCookieHandler>` cookies personnalisé en incluant un élément enfant qui référence le type de gestionnaire de cookie.</span><span class="sxs-lookup"><span data-stu-id="c052d-126">When you specify a custom cookie handler by setting the `mode` attribute of the `<cookieHandler>` element to "Custom", you must specify the type of the custom cookie handler by including a `<customCookieHandler>` child element that references the cookie handler type.</span></span> <span data-ttu-id="c052d-127">Cet élément ne peut pas être spécifié `mode` lorsque l’attribut a la valeur «chunked» ou «default».</span><span class="sxs-lookup"><span data-stu-id="c052d-127">This element cannot be specified when the `mode` attribute is set to "Chunked" or "Default".</span></span> <span data-ttu-id="c052d-128">Les gestionnaires de cookies personnalisés doivent dériver <xref:System.IdentityModel.Services.CookieHandler> de la classe.</span><span class="sxs-lookup"><span data-stu-id="c052d-128">Custom cookie handlers must derive from the <xref:System.IdentityModel.Services.CookieHandler> class.</span></span>  
  
 <span data-ttu-id="c052d-129">L' `<customCookieHandler>` élément est représenté par la <xref:System.IdentityModel.Configuration.CustomTypeElement> classe.</span><span class="sxs-lookup"><span data-stu-id="c052d-129">The `<customCookieHandler>` element is represented by the <xref:System.IdentityModel.Configuration.CustomTypeElement> class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c052d-130">Exemple</span><span class="sxs-lookup"><span data-stu-id="c052d-130">Example</span></span>  
 <span data-ttu-id="c052d-131">L’exemple suivant configure le SAM pour utiliser un gestionnaire de cookies personnalisé de type `MyNamespace.MyCustomCookieHandler`.</span><span class="sxs-lookup"><span data-stu-id="c052d-131">The following example configures the SAM to use a custom cookie handler of type `MyNamespace.MyCustomCookieHandler`.</span></span>  
  
```xml  
<cookieHandler mode="Custom">  
    <customCookieHandler type="MyNamespace.MyCustomCookieHandler, MyAssembly" />  
</cookieHandler>  
```  
  
## <a name="see-also"></a><span data-ttu-id="c052d-132">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c052d-132">See also</span></span>

- <xref:System.IdentityModel.Services.CookieHandler>
