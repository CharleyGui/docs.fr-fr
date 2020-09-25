---
title: <audienceUris>
ms.date: 03/30/2017
ms.assetid: 7a3d8515-d756-4afe-a22d-07cbe2217ee3
author: BrucePerlerMS
ms.openlocfilehash: c9787d8e0d8d66494bbf2dbd0e24ff39178a4cde
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91189901"
---
# \<audienceUris>

<span data-ttu-id="97adc-101">Spécifie l’ensemble d’URI qui sont des identificateurs acceptables de la partie de confiance (RP).</span><span class="sxs-lookup"><span data-stu-id="97adc-101">Specifies the set of URIs that are acceptable identifiers of the relying party (RP).</span></span> <span data-ttu-id="97adc-102">Les jetons ne sont pas acceptés à moins d'avoir pour étendue l'un des URI d'audience autorisés.</span><span class="sxs-lookup"><span data-stu-id="97adc-102">Tokens will not be accepted unless they are scoped for one of the allowed audience URIs.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<securityTokenHandlers>**](securitytokenhandlers.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<securityTokenHandlerConfiguration>**](securitytokenhandlerconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<audienceUris>**  
  
## <a name="syntax"></a><span data-ttu-id="97adc-103">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="97adc-103">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="97adc-104">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="97adc-104">Attributes and Elements</span></span>  

 <span data-ttu-id="97adc-105">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="97adc-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="97adc-106">Attributs</span><span class="sxs-lookup"><span data-stu-id="97adc-106">Attributes</span></span>  
  
|<span data-ttu-id="97adc-107">Attribut</span><span class="sxs-lookup"><span data-stu-id="97adc-107">Attribute</span></span>|<span data-ttu-id="97adc-108">Description</span><span class="sxs-lookup"><span data-stu-id="97adc-108">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="97adc-109">mode</span><span class="sxs-lookup"><span data-stu-id="97adc-109">mode</span></span>|<span data-ttu-id="97adc-110"><xref:System.IdentityModel.Selectors.AudienceUriMode>Valeur qui spécifie si la restriction de l’audience doit être appliquée à un jeton entrant.</span><span class="sxs-lookup"><span data-stu-id="97adc-110">An <xref:System.IdentityModel.Selectors.AudienceUriMode> value that specifies whether the audience restriction should be applied to an incoming token.</span></span> <span data-ttu-id="97adc-111">Les valeurs possibles sont « Always », « Never » et « BearerKeyOnly ».</span><span class="sxs-lookup"><span data-stu-id="97adc-111">The possible values are "Always", "Never", and "BearerKeyOnly".</span></span> <span data-ttu-id="97adc-112">La valeur par défaut est « Always ».</span><span class="sxs-lookup"><span data-stu-id="97adc-112">The default is "Always".</span></span> <span data-ttu-id="97adc-113">Optionnel.</span><span class="sxs-lookup"><span data-stu-id="97adc-113">Optional.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="97adc-114">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="97adc-114">Child Elements</span></span>  
  
|<span data-ttu-id="97adc-115">Élément</span><span class="sxs-lookup"><span data-stu-id="97adc-115">Element</span></span>|<span data-ttu-id="97adc-116">Description</span><span class="sxs-lookup"><span data-stu-id="97adc-116">Description</span></span>|  
|-------------|-----------------|  
|`<add value=xs:string>`|<span data-ttu-id="97adc-117">Ajoute l’URI spécifié par l' `value` attribut à la collection audienceUris.</span><span class="sxs-lookup"><span data-stu-id="97adc-117">Adds the URI specified by the `value` attribute to the audienceUris collection.</span></span> <span data-ttu-id="97adc-118">L'attribut `value` est obligatoire.</span><span class="sxs-lookup"><span data-stu-id="97adc-118">The `value` attribute is required.</span></span> <span data-ttu-id="97adc-119">L’URI respecte la casse.</span><span class="sxs-lookup"><span data-stu-id="97adc-119">The URI is case-sensitive.</span></span>|  
|`<clear>`|<span data-ttu-id="97adc-120">Efface la collection audienceUris.</span><span class="sxs-lookup"><span data-stu-id="97adc-120">Clears the audienceUris collection.</span></span> <span data-ttu-id="97adc-121">Tous les identificateurs sont supprimés de la collection.</span><span class="sxs-lookup"><span data-stu-id="97adc-121">All identifiers are removed from the collection.</span></span>|  
|`<remove value=xs:string>`|<span data-ttu-id="97adc-122">Supprime l’URI spécifié par l' `value` attribut de la collection audienceUris.</span><span class="sxs-lookup"><span data-stu-id="97adc-122">Removes the URI specified by the `value` attribute from the audienceUris collection.</span></span> <span data-ttu-id="97adc-123">L'attribut `value` est obligatoire.</span><span class="sxs-lookup"><span data-stu-id="97adc-123">The `value` attribute is required.</span></span> <span data-ttu-id="97adc-124">L’URI respecte la casse.</span><span class="sxs-lookup"><span data-stu-id="97adc-124">The URI is case-sensitive.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="97adc-125">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="97adc-125">Parent Elements</span></span>  
  
|<span data-ttu-id="97adc-126">Élément</span><span class="sxs-lookup"><span data-stu-id="97adc-126">Element</span></span>|<span data-ttu-id="97adc-127">Description</span><span class="sxs-lookup"><span data-stu-id="97adc-127">Description</span></span>|  
|-------------|-----------------|  
|[\<securityTokenHandlerConfiguration>](securitytokenhandlerconfiguration.md)|<span data-ttu-id="97adc-128">Fournit la configuration pour une collection de gestionnaires de jetons de sécurité.</span><span class="sxs-lookup"><span data-stu-id="97adc-128">Provides configuration for a collection of security token handlers.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="97adc-129">Notes</span><span class="sxs-lookup"><span data-stu-id="97adc-129">Remarks</span></span>  

 <span data-ttu-id="97adc-130">Par défaut, la collection est vide ; Utilisez `<add>` `<clear>` `<remove>` les éléments, et pour modifier la collection.</span><span class="sxs-lookup"><span data-stu-id="97adc-130">By default, the collection is empty; use `<add>`, `<clear>`, and `<remove>` elements to modify the collection.</span></span> <span data-ttu-id="97adc-131"><xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> les <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> objets et utilisent les valeurs de la collection d’URI d’audience pour configurer toutes les restrictions d’URI d’audience autorisées dans les <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement> objets.</span><span class="sxs-lookup"><span data-stu-id="97adc-131"><xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> and <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> objects use the values in the audience URI collection to configure any allowed audience URI restrictions in <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement> objects.</span></span>  
  
 <span data-ttu-id="97adc-132">L' `<audienceUris>` élément est représenté par la <xref:System.IdentityModel.Configuration.AudienceUriElementCollection> classe.</span><span class="sxs-lookup"><span data-stu-id="97adc-132">The `<audienceUris>` element is represented by the <xref:System.IdentityModel.Configuration.AudienceUriElementCollection> class.</span></span> <span data-ttu-id="97adc-133">Un URI individuel ajouté à la collection est représenté par la <xref:System.IdentityModel.Configuration.AudienceUriElement> classe.</span><span class="sxs-lookup"><span data-stu-id="97adc-133">An individual URI added to the collection is represented by the <xref:System.IdentityModel.Configuration.AudienceUriElement> class.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="97adc-134">L’utilisation de l' `<audienceUris>` élément en tant qu’élément enfant de l' [\<identityConfiguration>](identityconfiguration.md) élément a été dépréciée, mais est toujours prise en charge pour la compatibilité descendante.</span><span class="sxs-lookup"><span data-stu-id="97adc-134">The use of the `<audienceUris>` element as a child element of the [\<identityConfiguration>](identityconfiguration.md) element has been deprecated, but is still supported for backward compatibility.</span></span> <span data-ttu-id="97adc-135">Les paramètres de l' `<securityTokenHandlerConfiguration>` élément remplacent ceux de l' `<identityConfiguration>` élément.</span><span class="sxs-lookup"><span data-stu-id="97adc-135">Settings on the `<securityTokenHandlerConfiguration>` element override those on the `<identityConfiguration>` element.</span></span>  
  
## <a name="example"></a><span data-ttu-id="97adc-136">Exemple</span><span class="sxs-lookup"><span data-stu-id="97adc-136">Example</span></span>  

 <span data-ttu-id="97adc-137">Le code XML suivant montre comment configurer les URI d’audience acceptables pour une application.</span><span class="sxs-lookup"><span data-stu-id="97adc-137">The following XML shows how to configure the acceptable audience URIs for an application.</span></span> <span data-ttu-id="97adc-138">Cet exemple configure un seul URI.</span><span class="sxs-lookup"><span data-stu-id="97adc-138">This example configures a single URI.</span></span> <span data-ttu-id="97adc-139">Les jetons dont la portée est limitée à cet URI seront acceptés, tous les autres seront rejetés.</span><span class="sxs-lookup"><span data-stu-id="97adc-139">Tokens scoped for this URI will be accepted, all others will be rejected.</span></span>  
  
```xml  
<audienceUris>  
  <add value="http://localhost:19851/"/>  
</audienceUris>  
```
