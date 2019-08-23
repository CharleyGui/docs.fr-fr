---
title: <chunkedCookieHandler>
ms.date: 03/30/2017
ms.assetid: 7220de45-1d14-4aec-a29e-4a2ea8ac861f
author: BrucePerlerMS
ms.openlocfilehash: b3b4cf0d7c2748079af7a94534622b1dbadd3ab5
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69941892"
---
# <a name="chunkedcookiehandler"></a><span data-ttu-id="2ea19-101">\<chunkedCookieHandler></span><span class="sxs-lookup"><span data-stu-id="2ea19-101">\<chunkedCookieHandler></span></span>
<span data-ttu-id="2ea19-102">Configure le <xref:System.IdentityModel.Services.ChunkedCookieHandler>.</span><span class="sxs-lookup"><span data-stu-id="2ea19-102">Configures the <xref:System.IdentityModel.Services.ChunkedCookieHandler>.</span></span> <span data-ttu-id="2ea19-103">Cet élément ne peut être présent que si `mode` l’attribut de `<cookieHandler>` l’élément est «default» ou «chunked».</span><span class="sxs-lookup"><span data-stu-id="2ea19-103">This element may only be present if the `mode` attribute of the `<cookieHandler>` element is "Default" or "Chunked".</span></span>  
  
 <span data-ttu-id="2ea19-104">\<system.identityModel.services></span><span class="sxs-lookup"><span data-stu-id="2ea19-104">\<system.identityModel.services></span></span>  
<span data-ttu-id="2ea19-105">\<federationConfiguration></span><span class="sxs-lookup"><span data-stu-id="2ea19-105">\<federationConfiguration></span></span>  
<span data-ttu-id="2ea19-106">\<cookieHandler></span><span class="sxs-lookup"><span data-stu-id="2ea19-106">\<cookieHandler></span></span>  
<span data-ttu-id="2ea19-107">\<chunkedCookieHandler></span><span class="sxs-lookup"><span data-stu-id="2ea19-107">\<chunkedCookieHandler></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2ea19-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2ea19-108">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="2ea19-109">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="2ea19-109">Attributes and Elements</span></span>  
 <span data-ttu-id="2ea19-110">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="2ea19-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="2ea19-111">Attributs</span><span class="sxs-lookup"><span data-stu-id="2ea19-111">Attributes</span></span>  
  
|<span data-ttu-id="2ea19-112">Attribut</span><span class="sxs-lookup"><span data-stu-id="2ea19-112">Attribute</span></span>|<span data-ttu-id="2ea19-113">Description</span><span class="sxs-lookup"><span data-stu-id="2ea19-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="2ea19-114">chunkSize</span><span class="sxs-lookup"><span data-stu-id="2ea19-114">chunkSize</span></span>|<span data-ttu-id="2ea19-115">Taille maximale, en caractères, des données de cookie HTTP pour un cookie HTTP.</span><span class="sxs-lookup"><span data-stu-id="2ea19-115">The maximum size, in characters, of the HTTP cookie data for any one HTTP cookie.</span></span> <span data-ttu-id="2ea19-116">Vous devez être prudent lors de l’ajustement de la taille de segment.</span><span class="sxs-lookup"><span data-stu-id="2ea19-116">You must be careful when adjusting the chunk size.</span></span> <span data-ttu-id="2ea19-117">Les navigateurs Web ont des limites différentes quant à la taille des cookies et au nombre autorisé par domaine.</span><span class="sxs-lookup"><span data-stu-id="2ea19-117">Web browsers have different limits on the size of cookies and number allowed per domain.</span></span> <span data-ttu-id="2ea19-118">Par exemple, la spécification Netscape d’origine a stipulé les limites suivantes: 300 cookies au total, 4096 octets par en-tête de cookie (y compris les métadonnées, pas seulement la valeur du cookie) et 20 cookies par domaine.</span><span class="sxs-lookup"><span data-stu-id="2ea19-118">For example, the original Netscape specification stipulated these limits: 300 cookies total, 4096 bytes per cookie header (including metadata, not just the cookie value), and 20 cookies per domain.</span></span> <span data-ttu-id="2ea19-119">La valeur par défaut est 2000.</span><span class="sxs-lookup"><span data-stu-id="2ea19-119">The default is 2000.</span></span> <span data-ttu-id="2ea19-120">Requis.</span><span class="sxs-lookup"><span data-stu-id="2ea19-120">Required.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="2ea19-121">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="2ea19-121">Child Elements</span></span>  
 <span data-ttu-id="2ea19-122">Aucun</span><span class="sxs-lookup"><span data-stu-id="2ea19-122">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="2ea19-123">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="2ea19-123">Parent Elements</span></span>  
  
|<span data-ttu-id="2ea19-124">Élément</span><span class="sxs-lookup"><span data-stu-id="2ea19-124">Element</span></span>|<span data-ttu-id="2ea19-125">Description</span><span class="sxs-lookup"><span data-stu-id="2ea19-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="2ea19-126">\<cookieHandler></span><span class="sxs-lookup"><span data-stu-id="2ea19-126">\<cookieHandler></span></span>](cookiehandler.md)|<span data-ttu-id="2ea19-127">Configure le <xref:System.IdentityModel.Services.CookieHandler> que le <xref:System.IdentityModel.Services.SessionAuthenticationModule> (Sam) utilise pour lire et écrire des cookies.</span><span class="sxs-lookup"><span data-stu-id="2ea19-127">Configures the <xref:System.IdentityModel.Services.CookieHandler> that the <xref:System.IdentityModel.Services.SessionAuthenticationModule> (SAM) uses to read and write cookies.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2ea19-128">Notes</span><span class="sxs-lookup"><span data-stu-id="2ea19-128">Remarks</span></span>  
 <span data-ttu-id="2ea19-129">Lorsque vous spécifiez <xref:System.IdentityModel.Services.ChunkedCookieHandler> un en affectant à l' `<cookieHandler>` `mode` attribut de l’élément la valeur «default» ou «chunked», vous pouvez spécifier la taille de segment que le gestionnaire de cookies utilise pour lire `<chunkedCookieHandler>` et écrire des cookies en incluant un élément enfant et définition de `chunkSize` son attribut.</span><span class="sxs-lookup"><span data-stu-id="2ea19-129">When you specify a <xref:System.IdentityModel.Services.ChunkedCookieHandler> by setting the `mode` attribute of the `<cookieHandler>` element to "Default" or "Chunked", you can specify the chunk size that the cookie handler uses to read and write cookies by including a `<chunkedCookieHandler>` child element and setting its `chunkSize` attribute.</span></span> <span data-ttu-id="2ea19-130">Si l' `<chunkedCookieHandler>` élément n’est pas présent, la taille de segment par défaut de 2000 octets est utilisée.</span><span class="sxs-lookup"><span data-stu-id="2ea19-130">If the `<chunkedCookieHandler>` element is not present, the default chunk size of 2000 bytes is used.</span></span> <span data-ttu-id="2ea19-131">Cet élément ne peut pas être spécifié `mode` lorsque l’attribut a la valeur «Custom».</span><span class="sxs-lookup"><span data-stu-id="2ea19-131">This element cannot be specified when the `mode` attribute is set to "Custom".</span></span>  
  
 <span data-ttu-id="2ea19-132">L' `<chunkedCookieHandler>` élément est représenté par la <xref:System.IdentityModel.Services.ChunkedCookieHandlerElement> classe.</span><span class="sxs-lookup"><span data-stu-id="2ea19-132">The `<chunkedCookieHandler>` element is represented by the <xref:System.IdentityModel.Services.ChunkedCookieHandlerElement> class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2ea19-133">Exemple</span><span class="sxs-lookup"><span data-stu-id="2ea19-133">Example</span></span>  
 <span data-ttu-id="2ea19-134">L’exemple suivant configure un gestionnaire de cookies mémorisé en bloc qui écrit des cookies dans des segments de 3000 octets.</span><span class="sxs-lookup"><span data-stu-id="2ea19-134">The following example configures a chunked cookie handler that writes cookies in chunks of 3000 bytes.</span></span>  
  
```xml  
<cookieHandler mode="Chunked">  
    <chunkedCookieHandler chunkSize=3000/>  
</cookieHandler>  
```  
  
## <a name="see-also"></a><span data-ttu-id="2ea19-135">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2ea19-135">See also</span></span>

- <xref:System.IdentityModel.Services.ChunkedCookieHandler>
