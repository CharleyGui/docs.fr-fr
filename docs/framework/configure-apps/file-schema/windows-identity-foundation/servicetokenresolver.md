---
title: <serviceTokenResolver>
ms.date: 03/30/2017
ms.assetid: 6e9001e1-e064-4f47-84b2-46225c177746
author: BrucePerlerMS
ms.openlocfilehash: 0983380e553acfe246d6b987784d818b8ae85b17
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79152578"
---
# <a name="servicetokenresolver"></a><span data-ttu-id="3b515-101">\<serviceTokenResolver></span><span class="sxs-lookup"><span data-stu-id="3b515-101">\<serviceTokenResolver></span></span>
<span data-ttu-id="3b515-102">Enregistre le résammateur de jetons de service qui est utilisé par les gestionnaires dans la collection de manutention de jetons.</span><span class="sxs-lookup"><span data-stu-id="3b515-102">Registers the service token resolver that is used by handlers in the token handler collection.</span></span> <span data-ttu-id="3b515-103">Le résolveur de jetons de service est utilisé pour résoudre le jeton de chiffrement sur les jetons et les messages entrants.</span><span class="sxs-lookup"><span data-stu-id="3b515-103">The service token resolver is used to resolve the encryption token on incoming tokens and messages.</span></span>  
  
<span data-ttu-id="3b515-104">[**\<configuration>**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="3b515-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="3b515-105">&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)</span><span class="sxs-lookup"><span data-stu-id="3b515-105">&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)</span></span>\
<span data-ttu-id="3b515-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<identitéConfiguration>**](identityconfiguration.md)</span><span class="sxs-lookup"><span data-stu-id="3b515-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)</span></span>\
<span data-ttu-id="3b515-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<sécuritéTokenHandlers>**](securitytokenhandlers.md)</span><span class="sxs-lookup"><span data-stu-id="3b515-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<securityTokenHandlers>**](securitytokenhandlers.md)</span></span>\
<span data-ttu-id="3b515-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<sécuritéTokenHandlerConfiguration>**](securitytokenhandlerconfiguration.md)</span><span class="sxs-lookup"><span data-stu-id="3b515-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<securityTokenHandlerConfiguration>**](securitytokenhandlerconfiguration.md)</span></span>\
<span data-ttu-id="3b515-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<serviceTokenResolver>**</span><span class="sxs-lookup"><span data-stu-id="3b515-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<serviceTokenResolver>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3b515-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3b515-110">Syntax</span></span>  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <securityTokenHandlers>  
      <securityTokenHandlerConfiguration>  
        <serviceTokenResolver type=xs:string>  
        </serviceTokenResolver>  
      </securityTokenHandlerConfiguration>  
    </securityTokenHandlers>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="3b515-111">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="3b515-111">Attributes and Elements</span></span>  
 <span data-ttu-id="3b515-112">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="3b515-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="3b515-113">Attributs</span><span class="sxs-lookup"><span data-stu-id="3b515-113">Attributes</span></span>  
  
|<span data-ttu-id="3b515-114">Attribut</span><span class="sxs-lookup"><span data-stu-id="3b515-114">Attribute</span></span>|<span data-ttu-id="3b515-115">Description</span><span class="sxs-lookup"><span data-stu-id="3b515-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="3b515-116">type</span><span class="sxs-lookup"><span data-stu-id="3b515-116">type</span></span>|<span data-ttu-id="3b515-117">Spécifie le type de résoutur du jet de service.</span><span class="sxs-lookup"><span data-stu-id="3b515-117">Specifies the type of the service token resolver.</span></span> <span data-ttu-id="3b515-118">Soit <xref:System.IdentityModel.Selectors.SecurityTokenResolver> le type ou un type <xref:System.IdentityModel.Selectors.SecurityTokenResolver> qui dérive de la classe.</span><span class="sxs-lookup"><span data-stu-id="3b515-118">Either the <xref:System.IdentityModel.Selectors.SecurityTokenResolver> type or a type that derives from the <xref:System.IdentityModel.Selectors.SecurityTokenResolver> class.</span></span> <span data-ttu-id="3b515-119">Pour plus d’informations `type` sur la façon de spécifier l’attribut, voir [Références de type personnalisé].</span><span class="sxs-lookup"><span data-stu-id="3b515-119">For more information about how to specify the `type` attribute, see [Custom Type References].</span></span> <span data-ttu-id="3b515-120">Obligatoire.</span><span class="sxs-lookup"><span data-stu-id="3b515-120">Required.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="3b515-121">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="3b515-121">Child Elements</span></span>  
 <span data-ttu-id="3b515-122">None</span><span class="sxs-lookup"><span data-stu-id="3b515-122">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="3b515-123">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="3b515-123">Parent Elements</span></span>  
  
|<span data-ttu-id="3b515-124">Élément</span><span class="sxs-lookup"><span data-stu-id="3b515-124">Element</span></span>|<span data-ttu-id="3b515-125">Description</span><span class="sxs-lookup"><span data-stu-id="3b515-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="3b515-126">\<sécuritéTokenHandlerConfiguration></span><span class="sxs-lookup"><span data-stu-id="3b515-126">\<securityTokenHandlerConfiguration></span></span>](securitytokenhandlerconfiguration.md)|<span data-ttu-id="3b515-127">Fournit la configuration pour une collection de gestionnaires de jetons de sécurité.</span><span class="sxs-lookup"><span data-stu-id="3b515-127">Provides configuration for a collection of security token handlers.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3b515-128">Notes </span><span class="sxs-lookup"><span data-stu-id="3b515-128">Remarks</span></span>  
 <span data-ttu-id="3b515-129">Le résolveur de jetons de service peut être utilisé pour résoudre le jeton de chiffrement sur les jetons et les messages entrants.</span><span class="sxs-lookup"><span data-stu-id="3b515-129">The service token resolver can be used to resolve the encryption token on incoming tokens and messages.</span></span> <span data-ttu-id="3b515-130">Il est utilisé pour récupérer la clé qui doit être utilisée pour déchiffrer les jetons entrants.</span><span class="sxs-lookup"><span data-stu-id="3b515-130">It is used to retrieve the key that should be used to decrypt incoming tokens.</span></span> <span data-ttu-id="3b515-131">Vous devez `type` spécifier l’attribut.</span><span class="sxs-lookup"><span data-stu-id="3b515-131">You must specify the `type` attribute.</span></span> <span data-ttu-id="3b515-132">Le type spécifié <xref:System.IdentityModel.Selectors.SecurityTokenResolver> peut être soit ou un <xref:System.IdentityModel.Selectors.SecurityTokenResolver> type personnalisé qui dérive de la classe.</span><span class="sxs-lookup"><span data-stu-id="3b515-132">The type specified can be either <xref:System.IdentityModel.Selectors.SecurityTokenResolver> or a custom type that derives from the <xref:System.IdentityModel.Selectors.SecurityTokenResolver> class.</span></span>  
  
 <span data-ttu-id="3b515-133">Certains gestionnaires de jetons vous permettent de spécifier les paramètres de résolution de jetons de service dans la configuration.</span><span class="sxs-lookup"><span data-stu-id="3b515-133">Some token handlers allow you to specify service token resolver settings in configuration.</span></span> <span data-ttu-id="3b515-134">Les paramètres des manutentionnaires individuels remplacent ceux spécifiés sur la collection de gestionnaires de jetons de sécurité.</span><span class="sxs-lookup"><span data-stu-id="3b515-134">Settings on individual token handlers override those specified on the security token handler collection.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="3b515-135">Spécifier l’élément `<serviceTokenResolver>` comme élément enfant de [ \<l’identitéConfiguration>](identityconfiguration.md) élément a été déprécié, mais est toujours pris en charge pour la compatibilité vers l’arrière.</span><span class="sxs-lookup"><span data-stu-id="3b515-135">Specifying the `<serviceTokenResolver>` element as a child element of the [\<identityConfiguration>](identityconfiguration.md) element has been deprecated, but is still supported for backward compatibility.</span></span> <span data-ttu-id="3b515-136">Les paramètres `<securityTokenHandlerConfiguration>` de l’élément `<identityConfiguration>` l’emportent sur ceux de l’élément.</span><span class="sxs-lookup"><span data-stu-id="3b515-136">Settings on the `<securityTokenHandlerConfiguration>` element override those on the `<identityConfiguration>` element.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3b515-137"> Exemple</span><span class="sxs-lookup"><span data-stu-id="3b515-137">Example</span></span>  
  
```xml  
<serviceTokenResolver type="MyNamespace.CustomTokenResolver, MyAssembly" />  
```
