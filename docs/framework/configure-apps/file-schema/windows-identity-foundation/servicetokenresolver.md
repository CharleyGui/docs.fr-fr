---
title: <serviceTokenResolver>
ms.date: 03/30/2017
ms.assetid: 6e9001e1-e064-4f47-84b2-46225c177746
author: BrucePerlerMS
ms.openlocfilehash: 69d34cb54c2236f178ac4291ed24a3f5b45db48e
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69923107"
---
# <a name="servicetokenresolver"></a><span data-ttu-id="1743d-101">\<serviceTokenResolver></span><span class="sxs-lookup"><span data-stu-id="1743d-101">\<serviceTokenResolver></span></span>
<span data-ttu-id="1743d-102">Inscrit le programme de résolution de jetons de service qui est utilisé par les gestionnaires dans la collection de gestionnaires de jetons.</span><span class="sxs-lookup"><span data-stu-id="1743d-102">Registers the service token resolver that is used by handlers in the token handler collection.</span></span> <span data-ttu-id="1743d-103">Le programme de résolution de jetons de service est utilisé pour résoudre le jeton de chiffrement sur les jetons et les messages entrants.</span><span class="sxs-lookup"><span data-stu-id="1743d-103">The service token resolver is used to resolve the encryption token on incoming tokens and messages.</span></span>  
  
 <span data-ttu-id="1743d-104">\<system.identityModel></span><span class="sxs-lookup"><span data-stu-id="1743d-104">\<system.identityModel></span></span>  
<span data-ttu-id="1743d-105">\<identityConfiguration></span><span class="sxs-lookup"><span data-stu-id="1743d-105">\<identityConfiguration></span></span>  
<span data-ttu-id="1743d-106">\<securityTokenHandlers></span><span class="sxs-lookup"><span data-stu-id="1743d-106">\<securityTokenHandlers></span></span>  
<span data-ttu-id="1743d-107">\<securityTokenHandlerConfiguration></span><span class="sxs-lookup"><span data-stu-id="1743d-107">\<securityTokenHandlerConfiguration></span></span>  
<span data-ttu-id="1743d-108">\<serviceTokenResolver></span><span class="sxs-lookup"><span data-stu-id="1743d-108">\<serviceTokenResolver></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1743d-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1743d-109">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="1743d-110">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="1743d-110">Attributes and Elements</span></span>  
 <span data-ttu-id="1743d-111">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="1743d-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="1743d-112">Attributs</span><span class="sxs-lookup"><span data-stu-id="1743d-112">Attributes</span></span>  
  
|<span data-ttu-id="1743d-113">Attribut</span><span class="sxs-lookup"><span data-stu-id="1743d-113">Attribute</span></span>|<span data-ttu-id="1743d-114">Description</span><span class="sxs-lookup"><span data-stu-id="1743d-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="1743d-115">type</span><span class="sxs-lookup"><span data-stu-id="1743d-115">type</span></span>|<span data-ttu-id="1743d-116">Spécifie le type du programme de résolution de jetons de service.</span><span class="sxs-lookup"><span data-stu-id="1743d-116">Specifies the type of the service token resolver.</span></span> <span data-ttu-id="1743d-117">Le <xref:System.IdentityModel.Selectors.SecurityTokenResolver> type ou un type qui dérive de la <xref:System.IdentityModel.Selectors.SecurityTokenResolver> classe.</span><span class="sxs-lookup"><span data-stu-id="1743d-117">Either the <xref:System.IdentityModel.Selectors.SecurityTokenResolver> type or a type that derives from the <xref:System.IdentityModel.Selectors.SecurityTokenResolver> class.</span></span> <span data-ttu-id="1743d-118">Pour plus d’informations sur la spécification de `type` l’attribut, consultez [références de types personnalisés].</span><span class="sxs-lookup"><span data-stu-id="1743d-118">For more information about how to specify the `type` attribute, see [Custom Type References].</span></span> <span data-ttu-id="1743d-119">Requis.</span><span class="sxs-lookup"><span data-stu-id="1743d-119">Required.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="1743d-120">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="1743d-120">Child Elements</span></span>  
 <span data-ttu-id="1743d-121">Aucun</span><span class="sxs-lookup"><span data-stu-id="1743d-121">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="1743d-122">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="1743d-122">Parent Elements</span></span>  
  
|<span data-ttu-id="1743d-123">Élément</span><span class="sxs-lookup"><span data-stu-id="1743d-123">Element</span></span>|<span data-ttu-id="1743d-124">Description</span><span class="sxs-lookup"><span data-stu-id="1743d-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="1743d-125">\<securityTokenHandlerConfiguration></span><span class="sxs-lookup"><span data-stu-id="1743d-125">\<securityTokenHandlerConfiguration></span></span>](securitytokenhandlerconfiguration.md)|<span data-ttu-id="1743d-126">Fournit la configuration pour une collection de gestionnaires de jetons de sécurité.</span><span class="sxs-lookup"><span data-stu-id="1743d-126">Provides configuration for a collection of security token handlers.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1743d-127">Notes</span><span class="sxs-lookup"><span data-stu-id="1743d-127">Remarks</span></span>  
 <span data-ttu-id="1743d-128">Le programme de résolution de jetons de service peut être utilisé pour résoudre le jeton de chiffrement sur les jetons et les messages entrants.</span><span class="sxs-lookup"><span data-stu-id="1743d-128">The service token resolver can be used to resolve the encryption token on incoming tokens and messages.</span></span> <span data-ttu-id="1743d-129">Il est utilisé pour récupérer la clé qui doit être utilisée pour déchiffrer les jetons entrants.</span><span class="sxs-lookup"><span data-stu-id="1743d-129">It is used to retrieve the key that should be used to decrypt incoming tokens.</span></span> <span data-ttu-id="1743d-130">Vous devez spécifier l' `type` attribut.</span><span class="sxs-lookup"><span data-stu-id="1743d-130">You must specify the `type` attribute.</span></span> <span data-ttu-id="1743d-131">Le type spécifié peut être <xref:System.IdentityModel.Selectors.SecurityTokenResolver> ou un type personnalisé qui dérive de la <xref:System.IdentityModel.Selectors.SecurityTokenResolver> classe.</span><span class="sxs-lookup"><span data-stu-id="1743d-131">The type specified can be either <xref:System.IdentityModel.Selectors.SecurityTokenResolver> or a custom type that derives from the <xref:System.IdentityModel.Selectors.SecurityTokenResolver> class.</span></span>  
  
 <span data-ttu-id="1743d-132">Certains gestionnaires de jetons vous permettent de spécifier des paramètres de résolution de jetons de service dans la configuration.</span><span class="sxs-lookup"><span data-stu-id="1743d-132">Some token handlers allow you to specify service token resolver settings in configuration.</span></span> <span data-ttu-id="1743d-133">Les paramètres sur des gestionnaires de jetons individuels remplacent ceux spécifiés dans la collection de gestionnaires de jetons de sécurité.</span><span class="sxs-lookup"><span data-stu-id="1743d-133">Settings on individual token handlers override those specified on the security token handler collection.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="1743d-134">La spécification `<serviceTokenResolver>` de l’élément en tant qu’élément enfant de l' [ \<élément identityConfiguration >](identityconfiguration.md) a été dépréciée, mais est toujours prise en charge pour la compatibilité descendante.</span><span class="sxs-lookup"><span data-stu-id="1743d-134">Specifying the `<serviceTokenResolver>` element as a child element of the [\<identityConfiguration>](identityconfiguration.md) element has been deprecated, but is still supported for backward compatibility.</span></span> <span data-ttu-id="1743d-135">Les paramètres de `<securityTokenHandlerConfiguration>` l’élément remplacent ceux de `<identityConfiguration>` l’élément.</span><span class="sxs-lookup"><span data-stu-id="1743d-135">Settings on the `<securityTokenHandlerConfiguration>` element override those on the `<identityConfiguration>` element.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1743d-136">Exemples</span><span class="sxs-lookup"><span data-stu-id="1743d-136">Example</span></span>  
  
```xml  
<serviceTokenResolver type="MyNamespace.CustomTokenResolver, MyAssembly" />  
```
