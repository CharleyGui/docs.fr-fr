---
title: <chunkedCookieHandler>
ms.date: 03/30/2017
ms.assetid: 7220de45-1d14-4aec-a29e-4a2ea8ac861f
author: BrucePerlerMS
ms.openlocfilehash: 6aad95033b99f1472284f838f3ede2e74ea8324c
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/06/2020
ms.locfileid: "70252104"
---
# \<chunkedCookieHandler>
<span data-ttu-id="d55c3-101">Configure le <xref:System.IdentityModel.Services.ChunkedCookieHandler> .</span><span class="sxs-lookup"><span data-stu-id="d55c3-101">Configures the <xref:System.IdentityModel.Services.ChunkedCookieHandler>.</span></span> <span data-ttu-id="d55c3-102">Cet élément ne peut être présent que si l' `mode` attribut de l' `<cookieHandler>` élément est « default » ou « chunked ».</span><span class="sxs-lookup"><span data-stu-id="d55c3-102">This element may only be present if the `mode` attribute of the `<cookieHandler>` element is "Default" or "Chunked".</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.identityModel.services>**](system-identitymodel-services.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<federationConfiguration>**](federationconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<cookieHandler>**](cookiehandler.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<chunkedCookieHandler>**  
  
## <a name="syntax"></a><span data-ttu-id="d55c3-103">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d55c3-103">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d55c3-104">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="d55c3-104">Attributes and Elements</span></span>  
 <span data-ttu-id="d55c3-105">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="d55c3-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d55c3-106">Attributs</span><span class="sxs-lookup"><span data-stu-id="d55c3-106">Attributes</span></span>  
  
|<span data-ttu-id="d55c3-107">Attribut</span><span class="sxs-lookup"><span data-stu-id="d55c3-107">Attribute</span></span>|<span data-ttu-id="d55c3-108">Description</span><span class="sxs-lookup"><span data-stu-id="d55c3-108">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="d55c3-109">chunkSize</span><span class="sxs-lookup"><span data-stu-id="d55c3-109">chunkSize</span></span>|<span data-ttu-id="d55c3-110">Taille maximale, en caractères, des données de cookie HTTP pour un cookie HTTP.</span><span class="sxs-lookup"><span data-stu-id="d55c3-110">The maximum size, in characters, of the HTTP cookie data for any one HTTP cookie.</span></span> <span data-ttu-id="d55c3-111">Vous devez être prudent lors de l’ajustement de la taille de segment.</span><span class="sxs-lookup"><span data-stu-id="d55c3-111">You must be careful when adjusting the chunk size.</span></span> <span data-ttu-id="d55c3-112">Les navigateurs Web ont des limites différentes quant à la taille des cookies et au nombre autorisé par domaine.</span><span class="sxs-lookup"><span data-stu-id="d55c3-112">Web browsers have different limits on the size of cookies and number allowed per domain.</span></span> <span data-ttu-id="d55c3-113">Par exemple, la spécification Netscape d’origine a stipulé les limites suivantes : 300 cookies au total, 4096 octets par en-tête de cookie (y compris les métadonnées, pas seulement la valeur du cookie) et 20 cookies par domaine.</span><span class="sxs-lookup"><span data-stu-id="d55c3-113">For example, the original Netscape specification stipulated these limits: 300 cookies total, 4096 bytes per cookie header (including metadata, not just the cookie value), and 20 cookies per domain.</span></span> <span data-ttu-id="d55c3-114">La valeur par défaut est 2000.</span><span class="sxs-lookup"><span data-stu-id="d55c3-114">The default is 2000.</span></span> <span data-ttu-id="d55c3-115">Obligatoire.</span><span class="sxs-lookup"><span data-stu-id="d55c3-115">Required.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="d55c3-116">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="d55c3-116">Child Elements</span></span>  
 <span data-ttu-id="d55c3-117">Aucune</span><span class="sxs-lookup"><span data-stu-id="d55c3-117">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="d55c3-118">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="d55c3-118">Parent Elements</span></span>  
  
|<span data-ttu-id="d55c3-119">Élément</span><span class="sxs-lookup"><span data-stu-id="d55c3-119">Element</span></span>|<span data-ttu-id="d55c3-120">Description</span><span class="sxs-lookup"><span data-stu-id="d55c3-120">Description</span></span>|  
|-------------|-----------------|  
|[\<cookieHandler>](cookiehandler.md)|<span data-ttu-id="d55c3-121">Configure le <xref:System.IdentityModel.Services.CookieHandler> que le <xref:System.IdentityModel.Services.SessionAuthenticationModule> (Sam) utilise pour lire et écrire des cookies.</span><span class="sxs-lookup"><span data-stu-id="d55c3-121">Configures the <xref:System.IdentityModel.Services.CookieHandler> that the <xref:System.IdentityModel.Services.SessionAuthenticationModule> (SAM) uses to read and write cookies.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d55c3-122">Remarques</span><span class="sxs-lookup"><span data-stu-id="d55c3-122">Remarks</span></span>  
 <span data-ttu-id="d55c3-123">Lorsque vous spécifiez un <xref:System.IdentityModel.Services.ChunkedCookieHandler> en affectant `mode` à l’attribut de l’élément la valeur `<cookieHandler>` « default » ou « chunked », vous pouvez spécifier la taille de segment que le gestionnaire de cookies utilise pour lire et écrire des cookies en incluant un `<chunkedCookieHandler>` élément enfant et en définissant son `chunkSize` attribut.</span><span class="sxs-lookup"><span data-stu-id="d55c3-123">When you specify a <xref:System.IdentityModel.Services.ChunkedCookieHandler> by setting the `mode` attribute of the `<cookieHandler>` element to "Default" or "Chunked", you can specify the chunk size that the cookie handler uses to read and write cookies by including a `<chunkedCookieHandler>` child element and setting its `chunkSize` attribute.</span></span> <span data-ttu-id="d55c3-124">Si l' `<chunkedCookieHandler>` élément n’est pas présent, la taille de segment par défaut de 2000 octets est utilisée.</span><span class="sxs-lookup"><span data-stu-id="d55c3-124">If the `<chunkedCookieHandler>` element is not present, the default chunk size of 2000 bytes is used.</span></span> <span data-ttu-id="d55c3-125">Cet élément ne peut pas être spécifié lorsque l' `mode` attribut a la valeur « Custom ».</span><span class="sxs-lookup"><span data-stu-id="d55c3-125">This element cannot be specified when the `mode` attribute is set to "Custom".</span></span>  
  
 <span data-ttu-id="d55c3-126">L' `<chunkedCookieHandler>` élément est représenté par la <xref:System.IdentityModel.Services.ChunkedCookieHandlerElement> classe.</span><span class="sxs-lookup"><span data-stu-id="d55c3-126">The `<chunkedCookieHandler>` element is represented by the <xref:System.IdentityModel.Services.ChunkedCookieHandlerElement> class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d55c3-127">Exemple</span><span class="sxs-lookup"><span data-stu-id="d55c3-127">Example</span></span>  
 <span data-ttu-id="d55c3-128">L’exemple suivant configure un gestionnaire de cookies mémorisé en bloc qui écrit des cookies dans des segments de 3000 octets.</span><span class="sxs-lookup"><span data-stu-id="d55c3-128">The following example configures a chunked cookie handler that writes cookies in chunks of 3000 bytes.</span></span>  
  
```xml  
<cookieHandler mode="Chunked">  
    <chunkedCookieHandler chunkSize=3000/>  
</cookieHandler>  
```  
  
## <a name="see-also"></a><span data-ttu-id="d55c3-129">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d55c3-129">See also</span></span>

- <xref:System.IdentityModel.Services.ChunkedCookieHandler>
