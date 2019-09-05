---
title: <serviceTokenResolver>
ms.date: 03/30/2017
ms.assetid: 6e9001e1-e064-4f47-84b2-46225c177746
author: BrucePerlerMS
ms.openlocfilehash: 30a53c11b551623311f7ca3f957143fc702568a1
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70251853"
---
# <a name="servicetokenresolver"></a><span data-ttu-id="478c3-101">\<serviceTokenResolver></span><span class="sxs-lookup"><span data-stu-id="478c3-101">\<serviceTokenResolver></span></span>
<span data-ttu-id="478c3-102">Inscrit le programme de résolution de jetons de service qui est utilisé par les gestionnaires dans la collection de gestionnaires de jetons.</span><span class="sxs-lookup"><span data-stu-id="478c3-102">Registers the service token resolver that is used by handlers in the token handler collection.</span></span> <span data-ttu-id="478c3-103">Le programme de résolution de jetons de service est utilisé pour résoudre le jeton de chiffrement sur les jetons et les messages entrants.</span><span class="sxs-lookup"><span data-stu-id="478c3-103">The service token resolver is used to resolve the encryption token on incoming tokens and messages.</span></span>  
  
<span data-ttu-id="478c3-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="478c3-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="478c3-105">&nbsp;&nbsp;[ **\<System. identityModel >** ](system-identitymodel.md)</span><span class="sxs-lookup"><span data-stu-id="478c3-105">&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)</span></span>\
<span data-ttu-id="478c3-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<identityConfiguration >** ](identityconfiguration.md)</span><span class="sxs-lookup"><span data-stu-id="478c3-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)</span></span>\
<span data-ttu-id="478c3-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<securityTokenHandlers >** ](securitytokenhandlers.md)</span><span class="sxs-lookup"><span data-stu-id="478c3-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<securityTokenHandlers>**](securitytokenhandlers.md)</span></span>\
<span data-ttu-id="478c3-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<securityTokenHandlerConfiguration >** ](securitytokenhandlerconfiguration.md)</span><span class="sxs-lookup"><span data-stu-id="478c3-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<securityTokenHandlerConfiguration>**](securitytokenhandlerconfiguration.md)</span></span>\
<span data-ttu-id="478c3-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<serviceTokenResolver >**</span><span class="sxs-lookup"><span data-stu-id="478c3-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<serviceTokenResolver>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="478c3-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="478c3-110">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="478c3-111">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="478c3-111">Attributes and Elements</span></span>  
 <span data-ttu-id="478c3-112">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="478c3-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="478c3-113">Attributs</span><span class="sxs-lookup"><span data-stu-id="478c3-113">Attributes</span></span>  
  
|<span data-ttu-id="478c3-114">Attribut</span><span class="sxs-lookup"><span data-stu-id="478c3-114">Attribute</span></span>|<span data-ttu-id="478c3-115">Description</span><span class="sxs-lookup"><span data-stu-id="478c3-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="478c3-116">type</span><span class="sxs-lookup"><span data-stu-id="478c3-116">type</span></span>|<span data-ttu-id="478c3-117">Spécifie le type du programme de résolution de jetons de service.</span><span class="sxs-lookup"><span data-stu-id="478c3-117">Specifies the type of the service token resolver.</span></span> <span data-ttu-id="478c3-118">Le <xref:System.IdentityModel.Selectors.SecurityTokenResolver> type ou un type qui dérive de la <xref:System.IdentityModel.Selectors.SecurityTokenResolver> classe.</span><span class="sxs-lookup"><span data-stu-id="478c3-118">Either the <xref:System.IdentityModel.Selectors.SecurityTokenResolver> type or a type that derives from the <xref:System.IdentityModel.Selectors.SecurityTokenResolver> class.</span></span> <span data-ttu-id="478c3-119">Pour plus d’informations sur la spécification de `type` l’attribut, consultez [références de types personnalisés].</span><span class="sxs-lookup"><span data-stu-id="478c3-119">For more information about how to specify the `type` attribute, see [Custom Type References].</span></span> <span data-ttu-id="478c3-120">Requis.</span><span class="sxs-lookup"><span data-stu-id="478c3-120">Required.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="478c3-121">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="478c3-121">Child Elements</span></span>  
 <span data-ttu-id="478c3-122">Aucun</span><span class="sxs-lookup"><span data-stu-id="478c3-122">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="478c3-123">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="478c3-123">Parent Elements</span></span>  
  
|<span data-ttu-id="478c3-124">Élément</span><span class="sxs-lookup"><span data-stu-id="478c3-124">Element</span></span>|<span data-ttu-id="478c3-125">Description</span><span class="sxs-lookup"><span data-stu-id="478c3-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="478c3-126">\<securityTokenHandlerConfiguration></span><span class="sxs-lookup"><span data-stu-id="478c3-126">\<securityTokenHandlerConfiguration></span></span>](securitytokenhandlerconfiguration.md)|<span data-ttu-id="478c3-127">Fournit la configuration pour une collection de gestionnaires de jetons de sécurité.</span><span class="sxs-lookup"><span data-stu-id="478c3-127">Provides configuration for a collection of security token handlers.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="478c3-128">Notes</span><span class="sxs-lookup"><span data-stu-id="478c3-128">Remarks</span></span>  
 <span data-ttu-id="478c3-129">Le programme de résolution de jetons de service peut être utilisé pour résoudre le jeton de chiffrement sur les jetons et les messages entrants.</span><span class="sxs-lookup"><span data-stu-id="478c3-129">The service token resolver can be used to resolve the encryption token on incoming tokens and messages.</span></span> <span data-ttu-id="478c3-130">Il est utilisé pour récupérer la clé qui doit être utilisée pour déchiffrer les jetons entrants.</span><span class="sxs-lookup"><span data-stu-id="478c3-130">It is used to retrieve the key that should be used to decrypt incoming tokens.</span></span> <span data-ttu-id="478c3-131">Vous devez spécifier l' `type` attribut.</span><span class="sxs-lookup"><span data-stu-id="478c3-131">You must specify the `type` attribute.</span></span> <span data-ttu-id="478c3-132">Le type spécifié peut être <xref:System.IdentityModel.Selectors.SecurityTokenResolver> ou un type personnalisé qui dérive de la <xref:System.IdentityModel.Selectors.SecurityTokenResolver> classe.</span><span class="sxs-lookup"><span data-stu-id="478c3-132">The type specified can be either <xref:System.IdentityModel.Selectors.SecurityTokenResolver> or a custom type that derives from the <xref:System.IdentityModel.Selectors.SecurityTokenResolver> class.</span></span>  
  
 <span data-ttu-id="478c3-133">Certains gestionnaires de jetons vous permettent de spécifier des paramètres de résolution de jetons de service dans la configuration.</span><span class="sxs-lookup"><span data-stu-id="478c3-133">Some token handlers allow you to specify service token resolver settings in configuration.</span></span> <span data-ttu-id="478c3-134">Les paramètres sur des gestionnaires de jetons individuels remplacent ceux spécifiés dans la collection de gestionnaires de jetons de sécurité.</span><span class="sxs-lookup"><span data-stu-id="478c3-134">Settings on individual token handlers override those specified on the security token handler collection.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="478c3-135">La spécification `<serviceTokenResolver>` de l’élément en tant qu’élément enfant de l' [ \<élément identityConfiguration >](identityconfiguration.md) a été dépréciée, mais est toujours prise en charge pour la compatibilité descendante.</span><span class="sxs-lookup"><span data-stu-id="478c3-135">Specifying the `<serviceTokenResolver>` element as a child element of the [\<identityConfiguration>](identityconfiguration.md) element has been deprecated, but is still supported for backward compatibility.</span></span> <span data-ttu-id="478c3-136">Les paramètres de `<securityTokenHandlerConfiguration>` l’élément remplacent ceux de `<identityConfiguration>` l’élément.</span><span class="sxs-lookup"><span data-stu-id="478c3-136">Settings on the `<securityTokenHandlerConfiguration>` element override those on the `<identityConfiguration>` element.</span></span>  
  
## <a name="example"></a><span data-ttu-id="478c3-137">Exemple</span><span class="sxs-lookup"><span data-stu-id="478c3-137">Example</span></span>  
  
```xml  
<serviceTokenResolver type="MyNamespace.CustomTokenResolver, MyAssembly" />  
```
 