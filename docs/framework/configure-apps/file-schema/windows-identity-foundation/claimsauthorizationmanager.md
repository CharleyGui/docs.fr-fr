---
title: <claimsAuthorizationManager>
ms.date: 03/30/2017
ms.assetid: 9354eee3-f692-4ad6-8427-3169686b8bcc
author: BrucePerlerMS
ms.openlocfilehash: ddbe8a862940272e4192a3f4c0abdc1f9e8b5d48
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/06/2020
ms.locfileid: "70252085"
---
# \<claimsAuthorizationManager>
<span data-ttu-id="0863a-101">Inscrit un gestionnaire d’autorisations des revendications pour les revendications entrantes.</span><span class="sxs-lookup"><span data-stu-id="0863a-101">Registers a claims authorization manager for the incoming claims.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<claimsAuthorizationManager>**  
  
## <a name="syntax"></a><span data-ttu-id="0863a-102">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0863a-102">Syntax</span></span>  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <claimsAuthorizationManager type = xs:string>  
      <optionalConfigurationElements />  
    </claimsAuthorizationManager>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="0863a-103">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="0863a-103">Attributes and Elements</span></span>  
 <span data-ttu-id="0863a-104">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="0863a-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="0863a-105">Attributs</span><span class="sxs-lookup"><span data-stu-id="0863a-105">Attributes</span></span>  
  
|<span data-ttu-id="0863a-106">Attribut</span><span class="sxs-lookup"><span data-stu-id="0863a-106">Attribute</span></span>|<span data-ttu-id="0863a-107">Description</span><span class="sxs-lookup"><span data-stu-id="0863a-107">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="0863a-108">type</span><span class="sxs-lookup"><span data-stu-id="0863a-108">type</span></span>|<span data-ttu-id="0863a-109">Type personnalisé qui dérive de la <xref:System.Security.Claims.ClaimsAuthorizationManager> classe.</span><span class="sxs-lookup"><span data-stu-id="0863a-109">A custom type that derives from the <xref:System.Security.Claims.ClaimsAuthorizationManager> class.</span></span> <span data-ttu-id="0863a-110">Pour plus d’informations sur la spécification de l' `type` attribut, consultez [références de types personnalisés](../windows-workflow-foundation/index.md).</span><span class="sxs-lookup"><span data-stu-id="0863a-110">For more information about how to specify the `type` attribute, see [Custom Type References](../windows-workflow-foundation/index.md).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="0863a-111">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="0863a-111">Child Elements</span></span>  
 <span data-ttu-id="0863a-112">S’il n’y a aucun `type` attribut, ou si l' `type` attribut fait référence <xref:System.Security.Claims.ClaimsAuthenticationManager> à la classe, l' `<claimsAuthorizationManager>` élément ne prend pas d’éléments enfants ; Toutefois, les classes dérivées de <xref:System.Security.Claims.ClaimsAuthorizationManager> peuvent définir des éléments de configuration enfants.</span><span class="sxs-lookup"><span data-stu-id="0863a-112">If there is no `type` attribute, or if the `type` attribute references the <xref:System.Security.Claims.ClaimsAuthenticationManager> class, the `<claimsAuthorizationManager>` element does not take child elements; however, classes derived from <xref:System.Security.Claims.ClaimsAuthorizationManager> can define child configuration elements.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="0863a-113">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="0863a-113">Parent Elements</span></span>  
  
|<span data-ttu-id="0863a-114">Élément</span><span class="sxs-lookup"><span data-stu-id="0863a-114">Element</span></span>|<span data-ttu-id="0863a-115">Description</span><span class="sxs-lookup"><span data-stu-id="0863a-115">Description</span></span>|  
|-------------|-----------------|  
|[\<identityConfiguration>](identityconfiguration.md)|<span data-ttu-id="0863a-116">Spécifie les paramètres d’identité au niveau du service.</span><span class="sxs-lookup"><span data-stu-id="0863a-116">Specifies service-level identity settings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0863a-117">Remarques</span><span class="sxs-lookup"><span data-stu-id="0863a-117">Remarks</span></span>  
 <span data-ttu-id="0863a-118">Le comportement par défaut fourni par la <xref:System.Security.Claims.ClaimsAuthorizationManager> classe autorise toujours les revendications entrantes.</span><span class="sxs-lookup"><span data-stu-id="0863a-118">The default behavior provided through the <xref:System.Security.Claims.ClaimsAuthorizationManager> class always authorizes the incoming claims.</span></span> <span data-ttu-id="0863a-119">Si aucun `type` attribut n’est spécifié ou si l' `type` attribut spécifie la <xref:System.Security.Claims.ClaimsAuthorizationManager> classe, l' `<claimsAuthorizationManager>` élément ne prend pas d’éléments enfants.</span><span class="sxs-lookup"><span data-stu-id="0863a-119">If no `type` attribute is specified or if the `type` attribute specifies the <xref:System.Security.Claims.ClaimsAuthorizationManager> class, the `<claimsAuthorizationManager>` element does not take child elements.</span></span> <span data-ttu-id="0863a-120">Vous pouvez spécifier l' `type` attribut pour inscrire un type dérivé de la <xref:System.Security.Claims.ClaimsAuthorizationManager> classe afin d’implémenter un comportement personnalisé.</span><span class="sxs-lookup"><span data-stu-id="0863a-120">You can specify the `type` attribute to register a type derived from the <xref:System.Security.Claims.ClaimsAuthorizationManager> class to implement custom behavior.</span></span> <span data-ttu-id="0863a-121">Les classes dérivées peuvent prendre en charge la configuration par le biais d’éléments enfants de l' `<claimsAuthorizationManager>` élément en substituant la <xref:System.Security.Claims.ClaimsAuthorizationManager.LoadCustomConfiguration%2A> méthode pour gérer ces éléments.</span><span class="sxs-lookup"><span data-stu-id="0863a-121">Derived classes can support configuration through child elements of the `<claimsAuthorizationManager>` element by overriding the <xref:System.Security.Claims.ClaimsAuthorizationManager.LoadCustomConfiguration%2A> method to handle these elements.</span></span> <span data-ttu-id="0863a-122">Le schéma défini pour les éléments enfants est jusqu’au concepteur de la classe.</span><span class="sxs-lookup"><span data-stu-id="0863a-122">The schema defined for the child elements is up to the designer of the class.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="0863a-123">Lors de l’utilisation de la <xref:System.IdentityModel.Services.ClaimsPrincipalPermission> <xref:System.IdentityModel.Services.ClaimsPrincipalPermissionAttribute> classe ou pour fournir un contrôle d’accès basé sur les revendications dans votre code, la configuration d’identité référencée par l' `<federationConfiguration>` élément configure le gestionnaire d’autorisation des revendications et la stratégie utilisée pour prendre des décisions d’autorisation.</span><span class="sxs-lookup"><span data-stu-id="0863a-123">When using the <xref:System.IdentityModel.Services.ClaimsPrincipalPermission> or the <xref:System.IdentityModel.Services.ClaimsPrincipalPermissionAttribute> class to provide claims-based access control in your code, the identity configuration that is referenced by the `<federationConfiguration>` element configures the claims authorization manager and policy that is used to make authorization decisions.</span></span> <span data-ttu-id="0863a-124">Cela est vrai, même dans les scénarios qui ne sont pas des scénarios Web passifs, par exemple des applications Windows Communication Foundation (WCF) ou une application qui n’est pas basée sur le Web.</span><span class="sxs-lookup"><span data-stu-id="0863a-124">This is true, even in scenarios that are not passive Web scenarios, for example Windows Communication Foundation (WCF) applications or an application that is not Web-based.</span></span> <span data-ttu-id="0863a-125">Si l’application n’est pas une application Web passive, l' `<claimsAuthorizationManager>` élément (et ses éléments de stratégie enfants, le cas échéant) de la configuration d’identité référencée sont les seuls paramètres appliqués.</span><span class="sxs-lookup"><span data-stu-id="0863a-125">If the application is not a passive Web application, the `<claimsAuthorizationManager>` element (and its child policy elements, if present) of the referenced identity configuration are the only settings applied.</span></span> <span data-ttu-id="0863a-126">Tous les autres paramètres sont ignorés.</span><span class="sxs-lookup"><span data-stu-id="0863a-126">All other settings are ignored.</span></span> <span data-ttu-id="0863a-127">Pour plus d’informations, consultez l' [\<federationConfiguration>](federationconfiguration.md) élément.</span><span class="sxs-lookup"><span data-stu-id="0863a-127">For more information, see the [\<federationConfiguration>](federationconfiguration.md) element.</span></span>  
  
 <span data-ttu-id="0863a-128">Cet élément définit la <xref:System.IdentityModel.Configuration.IdentityConfiguration.ClaimsAuthorizationManager%2A?displayProperty=nameWithType> propriété.</span><span class="sxs-lookup"><span data-stu-id="0863a-128">This element sets the <xref:System.IdentityModel.Configuration.IdentityConfiguration.ClaimsAuthorizationManager%2A?displayProperty=nameWithType> property.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0863a-129">Exemple</span><span class="sxs-lookup"><span data-stu-id="0863a-129">Example</span></span>  
 <span data-ttu-id="0863a-130">Le code XML suivant montre la configuration d’un gestionnaire d’autorisations pour les revendications qui implémente une stratégie composée de paires ressource-action chacune spécifiant des combinaisons booléennes des revendications qu’un demandeur doit posséder pour exécuter l’action sur la ressource.</span><span class="sxs-lookup"><span data-stu-id="0863a-130">The following XML shows the configuration for a claims authorization manager that implements policy composed of resource-action pairs each of which specifies boolean combinations of the claims that a requestor must possess to perform the action on the resource.</span></span> <span data-ttu-id="0863a-131">Le code qui implémente le gestionnaire d’autorisations des revendications capable d’utiliser cette stratégie est disponible dans l' `ClaimsBasedAuthorization` exemple.</span><span class="sxs-lookup"><span data-stu-id="0863a-131">The code that implements the claims authorization manager capable of using this policy can be found in the `ClaimsBasedAuthorization` sample.</span></span>  
  
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
