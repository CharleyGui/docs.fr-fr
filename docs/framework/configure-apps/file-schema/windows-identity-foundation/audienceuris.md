---
title: <audienceUris>
ms.date: 03/30/2017
ms.assetid: 7a3d8515-d756-4afe-a22d-07cbe2217ee3
author: BrucePerlerMS
ms.openlocfilehash: bd04e4ebdf5c58adaeea0ff0ca5993d7d9ce38f1
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70252168"
---
# <a name="audienceuris"></a><span data-ttu-id="06745-101">\<audienceUris></span><span class="sxs-lookup"><span data-stu-id="06745-101">\<audienceUris></span></span>
<span data-ttu-id="06745-102">Spécifie l’ensemble d’URI qui sont des identificateurs acceptables de la partie de confiance (RP).</span><span class="sxs-lookup"><span data-stu-id="06745-102">Specifies the set of URIs that are acceptable identifiers of the relying party (RP).</span></span> <span data-ttu-id="06745-103">Les jetons ne sont pas acceptés, sauf s’ils sont étendus à l’un des URI d’audience autorisés.</span><span class="sxs-lookup"><span data-stu-id="06745-103">Tokens will not be accepted unless they are scoped for one of the allowed audience URIs.</span></span>  
  
<span data-ttu-id="06745-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="06745-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="06745-105">&nbsp;&nbsp;[ **\<System. identityModel >** ](system-identitymodel.md)</span><span class="sxs-lookup"><span data-stu-id="06745-105">&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)</span></span>\
<span data-ttu-id="06745-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<identityConfiguration >** ](identityconfiguration.md)</span><span class="sxs-lookup"><span data-stu-id="06745-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)</span></span>\
<span data-ttu-id="06745-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<securityTokenHandlers >** ](securitytokenhandlers.md)</span><span class="sxs-lookup"><span data-stu-id="06745-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<securityTokenHandlers>**](securitytokenhandlers.md)</span></span>\
<span data-ttu-id="06745-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<securityTokenHandlerConfiguration >** ](securitytokenhandlerconfiguration.md)</span><span class="sxs-lookup"><span data-stu-id="06745-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<securityTokenHandlerConfiguration>**](securitytokenhandlerconfiguration.md)</span></span>\
<span data-ttu-id="06745-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<audienceUris >**</span><span class="sxs-lookup"><span data-stu-id="06745-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<audienceUris>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="06745-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="06745-110">Syntax</span></span>  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <securityTokenHandlers>  
      <securityTokenHandlerConfiguration>  
        <audienceUris mode=xs:string>  
          <add value=xs:string />  
          <clear />  
          <remove value=xs:string />  
        </audienceUris>  
      </securityTokenHandlerConfiguration>  
    </securityTokenHandlers>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="06745-111">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="06745-111">Attributes and Elements</span></span>  
 <span data-ttu-id="06745-112">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="06745-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="06745-113">Attributs</span><span class="sxs-lookup"><span data-stu-id="06745-113">Attributes</span></span>  
  
|<span data-ttu-id="06745-114">Attribut</span><span class="sxs-lookup"><span data-stu-id="06745-114">Attribute</span></span>|<span data-ttu-id="06745-115">Description</span><span class="sxs-lookup"><span data-stu-id="06745-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="06745-116">mode</span><span class="sxs-lookup"><span data-stu-id="06745-116">mode</span></span>|<span data-ttu-id="06745-117"><xref:System.IdentityModel.Selectors.AudienceUriMode> Valeur qui spécifie si la restriction de l’audience doit être appliquée à un jeton entrant.</span><span class="sxs-lookup"><span data-stu-id="06745-117">An <xref:System.IdentityModel.Selectors.AudienceUriMode> value that specifies whether the audience restriction should be applied to an incoming token.</span></span> <span data-ttu-id="06745-118">Les valeurs possibles sont « Always », « Never » et « BearerKeyOnly ».</span><span class="sxs-lookup"><span data-stu-id="06745-118">The possible values are "Always", "Never", and "BearerKeyOnly".</span></span> <span data-ttu-id="06745-119">La valeur par défaut est « Always ».</span><span class="sxs-lookup"><span data-stu-id="06745-119">The default is "Always".</span></span> <span data-ttu-id="06745-120">facultatif.</span><span class="sxs-lookup"><span data-stu-id="06745-120">Optional.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="06745-121">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="06745-121">Child Elements</span></span>  
  
|<span data-ttu-id="06745-122">Élément</span><span class="sxs-lookup"><span data-stu-id="06745-122">Element</span></span>|<span data-ttu-id="06745-123">Description</span><span class="sxs-lookup"><span data-stu-id="06745-123">Description</span></span>|  
|-------------|-----------------|  
|`<add value=xs:string>`|<span data-ttu-id="06745-124">Ajoute l’URI spécifié par l' `value` attribut à la collection audienceUris.</span><span class="sxs-lookup"><span data-stu-id="06745-124">Adds the URI specified by the `value` attribute to the audienceUris collection.</span></span> <span data-ttu-id="06745-125">L'attribut `value` est obligatoire.</span><span class="sxs-lookup"><span data-stu-id="06745-125">The `value` attribute is required.</span></span> <span data-ttu-id="06745-126">L’URI respecte la casse.</span><span class="sxs-lookup"><span data-stu-id="06745-126">The URI is case-sensitive.</span></span>|  
|`<clear>`|<span data-ttu-id="06745-127">Efface la collection audienceUris.</span><span class="sxs-lookup"><span data-stu-id="06745-127">Clears the audienceUris collection.</span></span> <span data-ttu-id="06745-128">Tous les identificateurs sont supprimés de la collection.</span><span class="sxs-lookup"><span data-stu-id="06745-128">All identifiers are removed from the collection.</span></span>|  
|`<remove value=xs:string>`|<span data-ttu-id="06745-129">Supprime l’URI spécifié par l' `value` attribut de la collection audienceUris.</span><span class="sxs-lookup"><span data-stu-id="06745-129">Removes the URI specified by the `value` attribute from the audienceUris collection.</span></span> <span data-ttu-id="06745-130">L'attribut `value` est obligatoire.</span><span class="sxs-lookup"><span data-stu-id="06745-130">The `value` attribute is required.</span></span> <span data-ttu-id="06745-131">L’URI respecte la casse.</span><span class="sxs-lookup"><span data-stu-id="06745-131">The URI is case-sensitive.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="06745-132">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="06745-132">Parent Elements</span></span>  
  
|<span data-ttu-id="06745-133">Élément</span><span class="sxs-lookup"><span data-stu-id="06745-133">Element</span></span>|<span data-ttu-id="06745-134">Description</span><span class="sxs-lookup"><span data-stu-id="06745-134">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="06745-135">\<securityTokenHandlerConfiguration></span><span class="sxs-lookup"><span data-stu-id="06745-135">\<securityTokenHandlerConfiguration></span></span>](securitytokenhandlerconfiguration.md)|<span data-ttu-id="06745-136">Fournit la configuration pour une collection de gestionnaires de jetons de sécurité.</span><span class="sxs-lookup"><span data-stu-id="06745-136">Provides configuration for a collection of security token handlers.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="06745-137">Notes</span><span class="sxs-lookup"><span data-stu-id="06745-137">Remarks</span></span>  
 <span data-ttu-id="06745-138">Par défaut, la collection est vide ; Utilisez `<add>`les `<clear>`éléments, `<remove>` et pour modifier la collection.</span><span class="sxs-lookup"><span data-stu-id="06745-138">By default, the collection is empty; use `<add>`, `<clear>`, and `<remove>` elements to modify the collection.</span></span> <span data-ttu-id="06745-139"><xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler>les <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> objets et utilisent les valeurs de la collection d’URI d’audience pour configurer toutes les restrictions <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement> d’URI d’audience autorisées dans les objets.</span><span class="sxs-lookup"><span data-stu-id="06745-139"><xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> and <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> objects use the values in the audience URI collection to configure any allowed audience URI restrictions in <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement> objects.</span></span>  
  
 <span data-ttu-id="06745-140">L' `<audienceUris>` élément est représenté par la <xref:System.IdentityModel.Configuration.AudienceUriElementCollection> classe.</span><span class="sxs-lookup"><span data-stu-id="06745-140">The `<audienceUris>` element is represented by the <xref:System.IdentityModel.Configuration.AudienceUriElementCollection> class.</span></span> <span data-ttu-id="06745-141">Un URI individuel ajouté à la collection est représenté par la <xref:System.IdentityModel.Configuration.AudienceUriElement> classe.</span><span class="sxs-lookup"><span data-stu-id="06745-141">An individual URI added to the collection is represented by the <xref:System.IdentityModel.Configuration.AudienceUriElement> class.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="06745-142">L’utilisation de l' `<audienceUris>` élément en tant qu’élément enfant de l' [ \<élément identityConfiguration >](identityconfiguration.md) a été dépréciée, mais est toujours prise en charge pour la compatibilité descendante.</span><span class="sxs-lookup"><span data-stu-id="06745-142">The use of the `<audienceUris>` element as a child element of the [\<identityConfiguration>](identityconfiguration.md) element has been deprecated, but is still supported for backward compatibility.</span></span> <span data-ttu-id="06745-143">Les paramètres de `<securityTokenHandlerConfiguration>` l’élément remplacent ceux de `<identityConfiguration>` l’élément.</span><span class="sxs-lookup"><span data-stu-id="06745-143">Settings on the `<securityTokenHandlerConfiguration>` element override those on the `<identityConfiguration>` element.</span></span>  
  
## <a name="example"></a><span data-ttu-id="06745-144">Exemple</span><span class="sxs-lookup"><span data-stu-id="06745-144">Example</span></span>  
 <span data-ttu-id="06745-145">Le code XML suivant montre comment configurer les URI d’audience acceptables pour une application.</span><span class="sxs-lookup"><span data-stu-id="06745-145">The following XML shows how to configure the acceptable audience URIs for an application.</span></span> <span data-ttu-id="06745-146">Cet exemple configure un seul URI.</span><span class="sxs-lookup"><span data-stu-id="06745-146">This example configures a single URI.</span></span> <span data-ttu-id="06745-147">Les jetons dont la portée est limitée à cet URI seront acceptés, tous les autres seront rejetés.</span><span class="sxs-lookup"><span data-stu-id="06745-147">Tokens scoped for this URI will be accepted, all others will be rejected.</span></span>  
  
```xml  
<audienceUris>  
  <add value="http://localhost:19851/"/>  
</audienceUris>  
```
