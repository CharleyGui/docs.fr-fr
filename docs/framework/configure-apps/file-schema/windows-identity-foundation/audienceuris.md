---
title: <audienceUris>
ms.date: 03/30/2017
ms.assetid: 7a3d8515-d756-4afe-a22d-07cbe2217ee3
author: BrucePerlerMS
ms.openlocfilehash: 003221ed4dc7f4ccf72d2e0d3a91265e13172813
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69941960"
---
# <a name="audienceuris"></a><span data-ttu-id="99705-101">\<audienceUris></span><span class="sxs-lookup"><span data-stu-id="99705-101">\<audienceUris></span></span>
<span data-ttu-id="99705-102">Spécifie l’ensemble d’URI qui sont des identificateurs acceptables de la partie de confiance (RP).</span><span class="sxs-lookup"><span data-stu-id="99705-102">Specifies the set of URIs that are acceptable identifiers of the relying party (RP).</span></span> <span data-ttu-id="99705-103">Les jetons ne sont pas acceptés, sauf s’ils sont étendus à l’un des URI d’audience autorisés.</span><span class="sxs-lookup"><span data-stu-id="99705-103">Tokens will not be accepted unless they are scoped for one of the allowed audience URIs.</span></span>  
  
 <span data-ttu-id="99705-104">\<system.identityModel></span><span class="sxs-lookup"><span data-stu-id="99705-104">\<system.identityModel></span></span>  
<span data-ttu-id="99705-105">\<identityConfiguration></span><span class="sxs-lookup"><span data-stu-id="99705-105">\<identityConfiguration></span></span>  
<span data-ttu-id="99705-106">\<securityTokenHandlers></span><span class="sxs-lookup"><span data-stu-id="99705-106">\<securityTokenHandlers></span></span>  
<span data-ttu-id="99705-107">\<securityTokenHandlerConfiguration></span><span class="sxs-lookup"><span data-stu-id="99705-107">\<securityTokenHandlerConfiguration></span></span>  
<span data-ttu-id="99705-108">\<audienceUris></span><span class="sxs-lookup"><span data-stu-id="99705-108">\<audienceUris></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="99705-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="99705-109">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="99705-110">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="99705-110">Attributes and Elements</span></span>  
 <span data-ttu-id="99705-111">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="99705-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="99705-112">Attributs</span><span class="sxs-lookup"><span data-stu-id="99705-112">Attributes</span></span>  
  
|<span data-ttu-id="99705-113">Attribut</span><span class="sxs-lookup"><span data-stu-id="99705-113">Attribute</span></span>|<span data-ttu-id="99705-114">Description</span><span class="sxs-lookup"><span data-stu-id="99705-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="99705-115">mode</span><span class="sxs-lookup"><span data-stu-id="99705-115">mode</span></span>|<span data-ttu-id="99705-116"><xref:System.IdentityModel.Selectors.AudienceUriMode> Valeur qui spécifie si la restriction de l’audience doit être appliquée à un jeton entrant.</span><span class="sxs-lookup"><span data-stu-id="99705-116">An <xref:System.IdentityModel.Selectors.AudienceUriMode> value that specifies whether the audience restriction should be applied to an incoming token.</span></span> <span data-ttu-id="99705-117">Les valeurs possibles sont «Always», «Never» et «BearerKeyOnly».</span><span class="sxs-lookup"><span data-stu-id="99705-117">The possible values are "Always", "Never", and "BearerKeyOnly".</span></span> <span data-ttu-id="99705-118">La valeur par défaut est «Always».</span><span class="sxs-lookup"><span data-stu-id="99705-118">The default is "Always".</span></span> <span data-ttu-id="99705-119">facultatif.</span><span class="sxs-lookup"><span data-stu-id="99705-119">Optional.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="99705-120">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="99705-120">Child Elements</span></span>  
  
|<span data-ttu-id="99705-121">Élément</span><span class="sxs-lookup"><span data-stu-id="99705-121">Element</span></span>|<span data-ttu-id="99705-122">Description</span><span class="sxs-lookup"><span data-stu-id="99705-122">Description</span></span>|  
|-------------|-----------------|  
|`<add value=xs:string>`|<span data-ttu-id="99705-123">Ajoute l’URI spécifié par l' `value` attribut à la collection audienceUris.</span><span class="sxs-lookup"><span data-stu-id="99705-123">Adds the URI specified by the `value` attribute to the audienceUris collection.</span></span> <span data-ttu-id="99705-124">L'attribut `value` est obligatoire.</span><span class="sxs-lookup"><span data-stu-id="99705-124">The `value` attribute is required.</span></span> <span data-ttu-id="99705-125">L’URI respecte la casse.</span><span class="sxs-lookup"><span data-stu-id="99705-125">The URI is case-sensitive.</span></span>|  
|`<clear>`|<span data-ttu-id="99705-126">Efface la collection audienceUris.</span><span class="sxs-lookup"><span data-stu-id="99705-126">Clears the audienceUris collection.</span></span> <span data-ttu-id="99705-127">Tous les identificateurs sont supprimés de la collection.</span><span class="sxs-lookup"><span data-stu-id="99705-127">All identifiers are removed from the collection.</span></span>|  
|`<remove value=xs:string>`|<span data-ttu-id="99705-128">Supprime l’URI spécifié par l' `value` attribut de la collection audienceUris.</span><span class="sxs-lookup"><span data-stu-id="99705-128">Removes the URI specified by the `value` attribute from the audienceUris collection.</span></span> <span data-ttu-id="99705-129">L'attribut `value` est obligatoire.</span><span class="sxs-lookup"><span data-stu-id="99705-129">The `value` attribute is required.</span></span> <span data-ttu-id="99705-130">L’URI respecte la casse.</span><span class="sxs-lookup"><span data-stu-id="99705-130">The URI is case-sensitive.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="99705-131">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="99705-131">Parent Elements</span></span>  
  
|<span data-ttu-id="99705-132">Élément</span><span class="sxs-lookup"><span data-stu-id="99705-132">Element</span></span>|<span data-ttu-id="99705-133">Description</span><span class="sxs-lookup"><span data-stu-id="99705-133">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="99705-134">\<securityTokenHandlerConfiguration></span><span class="sxs-lookup"><span data-stu-id="99705-134">\<securityTokenHandlerConfiguration></span></span>](securitytokenhandlerconfiguration.md)|<span data-ttu-id="99705-135">Fournit la configuration pour une collection de gestionnaires de jetons de sécurité.</span><span class="sxs-lookup"><span data-stu-id="99705-135">Provides configuration for a collection of security token handlers.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="99705-136">Notes</span><span class="sxs-lookup"><span data-stu-id="99705-136">Remarks</span></span>  
 <span data-ttu-id="99705-137">Par défaut, la collection est vide; Utilisez `<add>`les `<clear>`éléments, `<remove>` et pour modifier la collection.</span><span class="sxs-lookup"><span data-stu-id="99705-137">By default, the collection is empty; use `<add>`, `<clear>`, and `<remove>` elements to modify the collection.</span></span> <span data-ttu-id="99705-138"><xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler>les <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> objets et utilisent les valeurs de la collection d’URI d’audience pour configurer toutes les restrictions <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement> d’URI d’audience autorisées dans les objets.</span><span class="sxs-lookup"><span data-stu-id="99705-138"><xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> and <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> objects use the values in the audience URI collection to configure any allowed audience URI restrictions in <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement> objects.</span></span>  
  
 <span data-ttu-id="99705-139">L' `<audienceUris>` élément est représenté par la <xref:System.IdentityModel.Configuration.AudienceUriElementCollection> classe.</span><span class="sxs-lookup"><span data-stu-id="99705-139">The `<audienceUris>` element is represented by the <xref:System.IdentityModel.Configuration.AudienceUriElementCollection> class.</span></span> <span data-ttu-id="99705-140">Un URI individuel ajouté à la collection est représenté par la <xref:System.IdentityModel.Configuration.AudienceUriElement> classe.</span><span class="sxs-lookup"><span data-stu-id="99705-140">An individual URI added to the collection is represented by the <xref:System.IdentityModel.Configuration.AudienceUriElement> class.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="99705-141">L’utilisation de l' `<audienceUris>` élément en tant qu’élément enfant de l' [ \<élément identityConfiguration >](identityconfiguration.md) a été dépréciée, mais est toujours prise en charge pour la compatibilité descendante.</span><span class="sxs-lookup"><span data-stu-id="99705-141">The use of the `<audienceUris>` element as a child element of the [\<identityConfiguration>](identityconfiguration.md) element has been deprecated, but is still supported for backward compatibility.</span></span> <span data-ttu-id="99705-142">Les paramètres de `<securityTokenHandlerConfiguration>` l’élément remplacent ceux de `<identityConfiguration>` l’élément.</span><span class="sxs-lookup"><span data-stu-id="99705-142">Settings on the `<securityTokenHandlerConfiguration>` element override those on the `<identityConfiguration>` element.</span></span>  
  
## <a name="example"></a><span data-ttu-id="99705-143">Exemples</span><span class="sxs-lookup"><span data-stu-id="99705-143">Example</span></span>  
 <span data-ttu-id="99705-144">Le code XML suivant montre comment configurer les URI d’audience acceptables pour une application.</span><span class="sxs-lookup"><span data-stu-id="99705-144">The following XML shows how to configure the acceptable audience URIs for an application.</span></span> <span data-ttu-id="99705-145">Cet exemple configure un seul URI.</span><span class="sxs-lookup"><span data-stu-id="99705-145">This example configures a single URI.</span></span> <span data-ttu-id="99705-146">Les jetons dont la portée est limitée à cet URI seront acceptés, tous les autres seront rejetés.</span><span class="sxs-lookup"><span data-stu-id="99705-146">Tokens scoped for this URI will be accepted, all others will be rejected.</span></span>  
  
```xml  
<audienceUris>  
  <add value="http://localhost:19851/"/>  
</audienceUris>  
```
