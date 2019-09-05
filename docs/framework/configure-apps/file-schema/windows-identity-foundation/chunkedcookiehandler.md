---
title: <chunkedCookieHandler>
ms.date: 03/30/2017
ms.assetid: 7220de45-1d14-4aec-a29e-4a2ea8ac861f
author: BrucePerlerMS
ms.openlocfilehash: 6aad95033b99f1472284f838f3ede2e74ea8324c
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70252104"
---
# <a name="chunkedcookiehandler"></a><span data-ttu-id="f0380-101">\<chunkedCookieHandler></span><span class="sxs-lookup"><span data-stu-id="f0380-101">\<chunkedCookieHandler></span></span>
<span data-ttu-id="f0380-102">Configure le <xref:System.IdentityModel.Services.ChunkedCookieHandler>.</span><span class="sxs-lookup"><span data-stu-id="f0380-102">Configures the <xref:System.IdentityModel.Services.ChunkedCookieHandler>.</span></span> <span data-ttu-id="f0380-103">Cet élément ne peut être présent que si `mode` l’attribut de `<cookieHandler>` l’élément est « default » ou « chunked ».</span><span class="sxs-lookup"><span data-stu-id="f0380-103">This element may only be present if the `mode` attribute of the `<cookieHandler>` element is "Default" or "Chunked".</span></span>  
  
<span data-ttu-id="f0380-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="f0380-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="f0380-105">&nbsp;&nbsp;[ **\<System. identityModel. services >** ](system-identitymodel-services.md)</span><span class="sxs-lookup"><span data-stu-id="f0380-105">&nbsp;&nbsp;[**\<system.identityModel.services>**](system-identitymodel-services.md)</span></span>\
<span data-ttu-id="f0380-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<federationConfiguration >** ](federationconfiguration.md)</span><span class="sxs-lookup"><span data-stu-id="f0380-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<federationConfiguration>**](federationconfiguration.md)</span></span>\
<span data-ttu-id="f0380-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<cookieHandler >** ](cookiehandler.md)</span><span class="sxs-lookup"><span data-stu-id="f0380-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<cookieHandler>**](cookiehandler.md)</span></span>\
<span data-ttu-id="f0380-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<chunkedCookieHandler >**</span><span class="sxs-lookup"><span data-stu-id="f0380-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<chunkedCookieHandler>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f0380-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f0380-109">Syntax</span></span>  
  
```xml  
<system.identityModel.services>  
  <federationConfiguration>  
    <cookieHandler mode="Chunked||Default" >  
      <chunkedCookieHandler size=xs:int >  
      </chunkedCookieHandler>  
    </cookieHandler>  
  </federationConfiguration>  
</system.identityModel.services>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f0380-110">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="f0380-110">Attributes and Elements</span></span>  
 <span data-ttu-id="f0380-111">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="f0380-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f0380-112">Attributs</span><span class="sxs-lookup"><span data-stu-id="f0380-112">Attributes</span></span>  
  
|<span data-ttu-id="f0380-113">Attribut</span><span class="sxs-lookup"><span data-stu-id="f0380-113">Attribute</span></span>|<span data-ttu-id="f0380-114">Description</span><span class="sxs-lookup"><span data-stu-id="f0380-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="f0380-115">chunkSize</span><span class="sxs-lookup"><span data-stu-id="f0380-115">chunkSize</span></span>|<span data-ttu-id="f0380-116">Taille maximale, en caractères, des données de cookie HTTP pour un cookie HTTP.</span><span class="sxs-lookup"><span data-stu-id="f0380-116">The maximum size, in characters, of the HTTP cookie data for any one HTTP cookie.</span></span> <span data-ttu-id="f0380-117">Vous devez être prudent lors de l’ajustement de la taille de segment.</span><span class="sxs-lookup"><span data-stu-id="f0380-117">You must be careful when adjusting the chunk size.</span></span> <span data-ttu-id="f0380-118">Les navigateurs Web ont des limites différentes quant à la taille des cookies et au nombre autorisé par domaine.</span><span class="sxs-lookup"><span data-stu-id="f0380-118">Web browsers have different limits on the size of cookies and number allowed per domain.</span></span> <span data-ttu-id="f0380-119">Par exemple, la spécification Netscape d’origine a stipulé les limites suivantes : 300 cookies au total, 4096 octets par en-tête de cookie (y compris les métadonnées, pas seulement la valeur du cookie) et 20 cookies par domaine.</span><span class="sxs-lookup"><span data-stu-id="f0380-119">For example, the original Netscape specification stipulated these limits: 300 cookies total, 4096 bytes per cookie header (including metadata, not just the cookie value), and 20 cookies per domain.</span></span> <span data-ttu-id="f0380-120">La valeur par défaut est 2000.</span><span class="sxs-lookup"><span data-stu-id="f0380-120">The default is 2000.</span></span> <span data-ttu-id="f0380-121">Requis.</span><span class="sxs-lookup"><span data-stu-id="f0380-121">Required.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="f0380-122">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="f0380-122">Child Elements</span></span>  
 <span data-ttu-id="f0380-123">Aucun</span><span class="sxs-lookup"><span data-stu-id="f0380-123">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="f0380-124">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="f0380-124">Parent Elements</span></span>  
  
|<span data-ttu-id="f0380-125">Élément</span><span class="sxs-lookup"><span data-stu-id="f0380-125">Element</span></span>|<span data-ttu-id="f0380-126">Description</span><span class="sxs-lookup"><span data-stu-id="f0380-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f0380-127">\<cookieHandler></span><span class="sxs-lookup"><span data-stu-id="f0380-127">\<cookieHandler></span></span>](cookiehandler.md)|<span data-ttu-id="f0380-128">Configure le <xref:System.IdentityModel.Services.CookieHandler> que le <xref:System.IdentityModel.Services.SessionAuthenticationModule> (Sam) utilise pour lire et écrire des cookies.</span><span class="sxs-lookup"><span data-stu-id="f0380-128">Configures the <xref:System.IdentityModel.Services.CookieHandler> that the <xref:System.IdentityModel.Services.SessionAuthenticationModule> (SAM) uses to read and write cookies.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f0380-129">Notes</span><span class="sxs-lookup"><span data-stu-id="f0380-129">Remarks</span></span>  
 <span data-ttu-id="f0380-130">Lorsque vous spécifiez <xref:System.IdentityModel.Services.ChunkedCookieHandler> un en affectant à l' `<cookieHandler>` `mode` attribut de l’élément la valeur « default » ou « chunked », vous pouvez spécifier la taille de segment que le gestionnaire de cookies utilise pour lire `<chunkedCookieHandler>` et écrire des cookies en incluant un élément enfant et définition de `chunkSize` son attribut.</span><span class="sxs-lookup"><span data-stu-id="f0380-130">When you specify a <xref:System.IdentityModel.Services.ChunkedCookieHandler> by setting the `mode` attribute of the `<cookieHandler>` element to "Default" or "Chunked", you can specify the chunk size that the cookie handler uses to read and write cookies by including a `<chunkedCookieHandler>` child element and setting its `chunkSize` attribute.</span></span> <span data-ttu-id="f0380-131">Si l' `<chunkedCookieHandler>` élément n’est pas présent, la taille de segment par défaut de 2000 octets est utilisée.</span><span class="sxs-lookup"><span data-stu-id="f0380-131">If the `<chunkedCookieHandler>` element is not present, the default chunk size of 2000 bytes is used.</span></span> <span data-ttu-id="f0380-132">Cet élément ne peut pas être spécifié `mode` lorsque l’attribut a la valeur « Custom ».</span><span class="sxs-lookup"><span data-stu-id="f0380-132">This element cannot be specified when the `mode` attribute is set to "Custom".</span></span>  
  
 <span data-ttu-id="f0380-133">L' `<chunkedCookieHandler>` élément est représenté par la <xref:System.IdentityModel.Services.ChunkedCookieHandlerElement> classe.</span><span class="sxs-lookup"><span data-stu-id="f0380-133">The `<chunkedCookieHandler>` element is represented by the <xref:System.IdentityModel.Services.ChunkedCookieHandlerElement> class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f0380-134">Exemple</span><span class="sxs-lookup"><span data-stu-id="f0380-134">Example</span></span>  
 <span data-ttu-id="f0380-135">L’exemple suivant configure un gestionnaire de cookies mémorisé en bloc qui écrit des cookies dans des segments de 3000 octets.</span><span class="sxs-lookup"><span data-stu-id="f0380-135">The following example configures a chunked cookie handler that writes cookies in chunks of 3000 bytes.</span></span>  
  
```xml  
<cookieHandler mode="Chunked">  
    <chunkedCookieHandler chunkSize=3000/>  
</cookieHandler>  
```  
  
## <a name="see-also"></a><span data-ttu-id="f0380-136">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f0380-136">See also</span></span>

- <xref:System.IdentityModel.Services.ChunkedCookieHandler>
