---
title: <remove>
ms.date: 03/30/2017
ms.assetid: 4058e2f1-7db4-4d1a-84dd-1b52836f2ae6
author: BrucePerlerMS
ms.openlocfilehash: cfdfbb3aabde253ad17b221801b20c1ac9a45c2d
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70251926"
---
# <a name="remove"></a><span data-ttu-id="d77c6-101">\<remove></span><span class="sxs-lookup"><span data-stu-id="d77c6-101">\<remove></span></span>
<span data-ttu-id="d77c6-102">Supprime le gestionnaire de jetons de sécurité spécifié de la collection de gestionnaires de jetons.</span><span class="sxs-lookup"><span data-stu-id="d77c6-102">Removes the specified security token handler from the token handler collection.</span></span>  
  
<span data-ttu-id="d77c6-103">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="d77c6-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="d77c6-104">&nbsp;&nbsp;[ **\<System. identityModel >** ](system-identitymodel.md)</span><span class="sxs-lookup"><span data-stu-id="d77c6-104">&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)</span></span>\
<span data-ttu-id="d77c6-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<identityConfiguration >** ](identityconfiguration.md)</span><span class="sxs-lookup"><span data-stu-id="d77c6-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)</span></span>\
<span data-ttu-id="d77c6-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<securityTokenHandlers >** ](securitytokenhandlers.md)</span><span class="sxs-lookup"><span data-stu-id="d77c6-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<securityTokenHandlers>**](securitytokenhandlers.md)</span></span>\
<span data-ttu-id="d77c6-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<supprimer >**</span><span class="sxs-lookup"><span data-stu-id="d77c6-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<remove>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d77c6-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d77c6-108">Syntax</span></span>  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <securityTokenHandlers>  
      <remove type=xs:string >  
      </remove>  
    </securityTokenHandlers>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d77c6-109">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="d77c6-109">Attributes and Elements</span></span>  
 <span data-ttu-id="d77c6-110">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="d77c6-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d77c6-111">Attributs</span><span class="sxs-lookup"><span data-stu-id="d77c6-111">Attributes</span></span>  
  
|<span data-ttu-id="d77c6-112">Attribut</span><span class="sxs-lookup"><span data-stu-id="d77c6-112">Attribute</span></span>|<span data-ttu-id="d77c6-113">Description</span><span class="sxs-lookup"><span data-stu-id="d77c6-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="d77c6-114">type</span><span class="sxs-lookup"><span data-stu-id="d77c6-114">type</span></span>|<span data-ttu-id="d77c6-115">Nom de type CLR du gestionnaire de jetons à supprimer.</span><span class="sxs-lookup"><span data-stu-id="d77c6-115">The CLR type name of the token handler to be removed.</span></span> <span data-ttu-id="d77c6-116">Pour plus d’informations sur la spécification de `type` l’attribut, consultez [références de types personnalisés](https://docs.microsoft.com/previous-versions/windows-identity-foundation/gg638728(v=msdn.10)#custom-type-references).</span><span class="sxs-lookup"><span data-stu-id="d77c6-116">For more information about how to specify the `type` attribute, see [Custom Type References](https://docs.microsoft.com/previous-versions/windows-identity-foundation/gg638728(v=msdn.10)#custom-type-references).</span></span> <span data-ttu-id="d77c6-117">Requis.</span><span class="sxs-lookup"><span data-stu-id="d77c6-117">Required.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="d77c6-118">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="d77c6-118">Child Elements</span></span>  
 <span data-ttu-id="d77c6-119">Aucun</span><span class="sxs-lookup"><span data-stu-id="d77c6-119">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="d77c6-120">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="d77c6-120">Parent Elements</span></span>  
  
|<span data-ttu-id="d77c6-121">Élément</span><span class="sxs-lookup"><span data-stu-id="d77c6-121">Element</span></span>|<span data-ttu-id="d77c6-122">Description</span><span class="sxs-lookup"><span data-stu-id="d77c6-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d77c6-123">\<securityTokenHandlers></span><span class="sxs-lookup"><span data-stu-id="d77c6-123">\<securityTokenHandlers></span></span>](securitytokenhandlers.md)|<span data-ttu-id="d77c6-124">Spécifie une collection de gestionnaires de jetons de sécurité inscrits auprès du point de terminaison.</span><span class="sxs-lookup"><span data-stu-id="d77c6-124">Specifies a collection of security token handlers that are registered with the endpoint.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="d77c6-125">Exemple</span><span class="sxs-lookup"><span data-stu-id="d77c6-125">Example</span></span>  
 <span data-ttu-id="d77c6-126">Le code XML suivant montre l’utilisation des `<add>` éléments `<remove>` et pour remplacer le gestionnaire de jetons de session par défaut par un gestionnaire de jetons de session personnalisé.</span><span class="sxs-lookup"><span data-stu-id="d77c6-126">The following XML shows the use of the `<add>` and `<remove>` elements to replace the default session token handler with a custom session token handler.</span></span> <span data-ttu-id="d77c6-127">Le code XML est extrait de `ClaimsAwareWebFarm` l’exemple.</span><span class="sxs-lookup"><span data-stu-id="d77c6-127">The XML is taken from the `ClaimsAwareWebFarm` sample.</span></span>  
  
```xml  
<securityTokenHandlers>  
  <remove type="System.IdentityModel.Tokens.SessionSecurityTokenHandler, System.IdentityModel, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
  <add type="System.IdentityModel.Services.Tokens.MachineKeySessionSecurityTokenHandler, System.IdentityModel.Services, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
</securityTokenHandlers>  
```
