---
title: <claimsAuthorizationManager>
ms.date: 03/30/2017
ms.assetid: 9354eee3-f692-4ad6-8427-3169686b8bcc
author: BrucePerlerMS
ms.openlocfilehash: 74ca031f7017d51adaa7a71593f537b64abbeae6
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69942888"
---
# <a name="claimsauthorizationmanager"></a><span data-ttu-id="2d7fe-101">\<claimsAuthorizationManager></span><span class="sxs-lookup"><span data-stu-id="2d7fe-101">\<claimsAuthorizationManager></span></span>
<span data-ttu-id="2d7fe-102">Inscrit un gestionnaire d’autorisations des revendications pour les revendications entrantes.</span><span class="sxs-lookup"><span data-stu-id="2d7fe-102">Registers a claims authorization manager for the incoming claims.</span></span>  
  
 <span data-ttu-id="2d7fe-103">\<system.identityModel></span><span class="sxs-lookup"><span data-stu-id="2d7fe-103">\<system.identityModel></span></span>  
<span data-ttu-id="2d7fe-104">\<identityConfiguration></span><span class="sxs-lookup"><span data-stu-id="2d7fe-104">\<identityConfiguration></span></span>  
<span data-ttu-id="2d7fe-105">\<claimsAuthorizationManager></span><span class="sxs-lookup"><span data-stu-id="2d7fe-105">\<claimsAuthorizationManager></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2d7fe-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2d7fe-106">Syntax</span></span>  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <claimsAuthorizationManager type = xs:string>  
      <optionalConfigurationElements />  
    </claimsAuthorizationManager>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="2d7fe-107">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="2d7fe-107">Attributes and Elements</span></span>  
 <span data-ttu-id="2d7fe-108">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="2d7fe-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="2d7fe-109">Attributs</span><span class="sxs-lookup"><span data-stu-id="2d7fe-109">Attributes</span></span>  
  
|<span data-ttu-id="2d7fe-110">Attribut</span><span class="sxs-lookup"><span data-stu-id="2d7fe-110">Attribute</span></span>|<span data-ttu-id="2d7fe-111">Description</span><span class="sxs-lookup"><span data-stu-id="2d7fe-111">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="2d7fe-112">type</span><span class="sxs-lookup"><span data-stu-id="2d7fe-112">type</span></span>|<span data-ttu-id="2d7fe-113">Type personnalisé qui dérive de la <xref:System.Security.Claims.ClaimsAuthorizationManager> classe.</span><span class="sxs-lookup"><span data-stu-id="2d7fe-113">A custom type that derives from the <xref:System.Security.Claims.ClaimsAuthorizationManager> class.</span></span> <span data-ttu-id="2d7fe-114">Pour plus d’informations sur la spécification de `type` l’attribut, consultez [références de types personnalisés](../windows-workflow-foundation/index.md).</span><span class="sxs-lookup"><span data-stu-id="2d7fe-114">For more information about how to specify the `type` attribute, see [Custom Type References](../windows-workflow-foundation/index.md).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="2d7fe-115">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="2d7fe-115">Child Elements</span></span>  
 <span data-ttu-id="2d7fe-116">S’il n’y `type` a aucun attribut, ou `type` si l’attribut <xref:System.Security.Claims.ClaimsAuthenticationManager> fait référence à `<claimsAuthorizationManager>` la classe, l’élément ne prend pas d’éléments enfants; <xref:System.Security.Claims.ClaimsAuthorizationManager> Toutefois, les classes dérivées de peuvent définir des éléments de configuration enfants.</span><span class="sxs-lookup"><span data-stu-id="2d7fe-116">If there is no `type` attribute, or if the `type` attribute references the <xref:System.Security.Claims.ClaimsAuthenticationManager> class, the `<claimsAuthorizationManager>` element does not take child elements; however, classes derived from <xref:System.Security.Claims.ClaimsAuthorizationManager> can define child configuration elements.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="2d7fe-117">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="2d7fe-117">Parent Elements</span></span>  
  
|<span data-ttu-id="2d7fe-118">Élément</span><span class="sxs-lookup"><span data-stu-id="2d7fe-118">Element</span></span>|<span data-ttu-id="2d7fe-119">Description</span><span class="sxs-lookup"><span data-stu-id="2d7fe-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="2d7fe-120">\<identityConfiguration></span><span class="sxs-lookup"><span data-stu-id="2d7fe-120">\<identityConfiguration></span></span>](identityconfiguration.md)|<span data-ttu-id="2d7fe-121">Spécifie les paramètres d’identité au niveau du service.</span><span class="sxs-lookup"><span data-stu-id="2d7fe-121">Specifies service-level identity settings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2d7fe-122">Notes</span><span class="sxs-lookup"><span data-stu-id="2d7fe-122">Remarks</span></span>  
 <span data-ttu-id="2d7fe-123">Le comportement par défaut fourni par <xref:System.Security.Claims.ClaimsAuthorizationManager> la classe autorise toujours les revendications entrantes.</span><span class="sxs-lookup"><span data-stu-id="2d7fe-123">The default behavior provided through the <xref:System.Security.Claims.ClaimsAuthorizationManager> class always authorizes the incoming claims.</span></span> <span data-ttu-id="2d7fe-124">Si aucun `type` attribut n’est spécifié ou si `type` l’attribut spécifie la <xref:System.Security.Claims.ClaimsAuthorizationManager> classe `<claimsAuthorizationManager>` , l’élément ne prend pas d’éléments enfants.</span><span class="sxs-lookup"><span data-stu-id="2d7fe-124">If no `type` attribute is specified or if the `type` attribute specifies the <xref:System.Security.Claims.ClaimsAuthorizationManager> class, the `<claimsAuthorizationManager>` element does not take child elements.</span></span> <span data-ttu-id="2d7fe-125">Vous pouvez spécifier l' `type` attribut pour inscrire un type dérivé de la <xref:System.Security.Claims.ClaimsAuthorizationManager> classe afin d’implémenter un comportement personnalisé.</span><span class="sxs-lookup"><span data-stu-id="2d7fe-125">You can specify the `type` attribute to register a type derived from the <xref:System.Security.Claims.ClaimsAuthorizationManager> class to implement custom behavior.</span></span> <span data-ttu-id="2d7fe-126">Les classes dérivées peuvent prendre en charge la configuration `<claimsAuthorizationManager>` par le biais d’éléments <xref:System.Security.Claims.ClaimsAuthorizationManager.LoadCustomConfiguration%2A> enfants de l’élément en substituant la méthode pour gérer ces éléments.</span><span class="sxs-lookup"><span data-stu-id="2d7fe-126">Derived classes can support configuration through child elements of the `<claimsAuthorizationManager>` element by overriding the <xref:System.Security.Claims.ClaimsAuthorizationManager.LoadCustomConfiguration%2A> method to handle these elements.</span></span> <span data-ttu-id="2d7fe-127">Le schéma défini pour les éléments enfants est jusqu’au concepteur de la classe.</span><span class="sxs-lookup"><span data-stu-id="2d7fe-127">The schema defined for the child elements is up to the designer of the class.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="2d7fe-128">Lors de l' <xref:System.IdentityModel.Services.ClaimsPrincipalPermission> utilisation de <xref:System.IdentityModel.Services.ClaimsPrincipalPermissionAttribute> la classe ou pour fournir un contrôle d’accès basé sur les revendications dans votre code, la configuration d’identité `<federationConfiguration>` référencée par l’élément configure le gestionnaire d’autorisation des revendications et la stratégie utilisée pour effectuer décisions d’autorisation.</span><span class="sxs-lookup"><span data-stu-id="2d7fe-128">When using the <xref:System.IdentityModel.Services.ClaimsPrincipalPermission> or the <xref:System.IdentityModel.Services.ClaimsPrincipalPermissionAttribute> class to provide claims-based access control in your code, the identity configuration that is referenced by the `<federationConfiguration>` element configures the claims authorization manager and policy that is used to make authorization decisions.</span></span> <span data-ttu-id="2d7fe-129">Cela est vrai, même dans les scénarios qui ne sont pas des scénarios Web passifs, par exemple des applications Windows Communication Foundation (WCF) ou une application qui n’est pas basée sur le Web.</span><span class="sxs-lookup"><span data-stu-id="2d7fe-129">This is true, even in scenarios that are not passive Web scenarios, for example Windows Communication Foundation (WCF) applications or an application that is not Web-based.</span></span> <span data-ttu-id="2d7fe-130">Si l’application n’est pas une application Web passive `<claimsAuthorizationManager>` , l’élément (et ses éléments de stratégie enfants, le cas échéant) de la configuration d’identité référencée sont les seuls paramètres appliqués.</span><span class="sxs-lookup"><span data-stu-id="2d7fe-130">If the application is not a passive Web application, the `<claimsAuthorizationManager>` element (and its child policy elements, if present) of the referenced identity configuration are the only settings applied.</span></span> <span data-ttu-id="2d7fe-131">Tous les autres paramètres sont ignorés.</span><span class="sxs-lookup"><span data-stu-id="2d7fe-131">All other settings are ignored.</span></span> <span data-ttu-id="2d7fe-132">Pour plus d’informations, consultez l' [ \<élément federationConfiguration >](federationconfiguration.md) .</span><span class="sxs-lookup"><span data-stu-id="2d7fe-132">For more information, see the [\<federationConfiguration>](federationconfiguration.md) element.</span></span>  
  
 <span data-ttu-id="2d7fe-133">Cet élément définit la <xref:System.IdentityModel.Configuration.IdentityConfiguration.ClaimsAuthorizationManager%2A?displayProperty=nameWithType> propriété.</span><span class="sxs-lookup"><span data-stu-id="2d7fe-133">This element sets the <xref:System.IdentityModel.Configuration.IdentityConfiguration.ClaimsAuthorizationManager%2A?displayProperty=nameWithType> property.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2d7fe-134">Exemples</span><span class="sxs-lookup"><span data-stu-id="2d7fe-134">Example</span></span>  
 <span data-ttu-id="2d7fe-135">Le code XML suivant montre la configuration d’un gestionnaire d’autorisations pour les revendications qui implémente une stratégie composée de paires ressource-action chacune spécifiant des combinaisons booléennes des revendications qu’un demandeur doit posséder pour exécuter l’action sur la ressource.</span><span class="sxs-lookup"><span data-stu-id="2d7fe-135">The following XML shows the configuration for a claims authorization manager that implements policy composed of resource-action pairs each of which specifies boolean combinations of the claims that a requestor must possess to perform the action on the resource.</span></span> <span data-ttu-id="2d7fe-136">Le code qui implémente le gestionnaire d’autorisations des revendications capable d’utiliser cette stratégie est disponible dans `ClaimsBasedAuthorization` l’exemple.</span><span class="sxs-lookup"><span data-stu-id="2d7fe-136">The code that implements the claims authorization manager capable of using this policy can be found in the `ClaimsBasedAuthorization` sample.</span></span>  
  
```xml  
<system.identityModel>  
    <identityConfiguration>  
      <claimsAuthorizationManager type="ClaimsAuthorizationLibrary.MyClaimsAuthorizationManager, ClaimsAuthorizationLibrary">  
        <policy resource="http://localhost:28491/Developers.aspx" action="GET">  
          <or>  
            <claim claimType="http://schemas.microsoft.com/ws/2008/06/identity/claims/role" claimValue="developer" />  
            <claim claimType="http://schemas.xmlsoap.org/claims/Group" claimValue="Administrator" />  
          </or>  
        </policy>  
        <policy resource="http://localhost:28491/Administrators.aspx" action="GET">  
          <and>  
            <claim claimType="http://schemas.xmlsoap.org/claims/Group" claimValue="Administrator" />  
            <claim claimType="http://schemas.xmlsoap.org/ws/2005/05/identity/claims/country" claimValue="USA" />  
          </and>  
        </policy>  
        <policy resource="http://localhost:28491/Default.aspx" action="GET">  
        </policy>  
        <policy resource="http://localhost:28491/" action="GET">  
        </policy>  
        <policy resource="http://localhost:28491/Claims.aspx" action="GET">  
        </policy>  
      </claimsAuthorizationManager>  
    <identityConfiguration>  
<system.identityModel>  
```
