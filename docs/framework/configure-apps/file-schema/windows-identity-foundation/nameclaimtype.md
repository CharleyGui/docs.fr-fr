---
title: <nameClaimType>
ms.date: 03/30/2017
ms.assetid: 17514d95-f0f5-4789-8e28-346640dc227c
author: BrucePerlerMS
ms.openlocfilehash: 47366c5bb2bd9228268fce3ae6e1fb5ad457dab1
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69942623"
---
# <a name="nameclaimtype"></a><span data-ttu-id="12318-101">\<nameClaimType></span><span class="sxs-lookup"><span data-stu-id="12318-101">\<nameClaimType></span></span>
<span data-ttu-id="12318-102">Définit le type de revendication qui spécifie la <xref:System.Security.Principal.IIdentity.Name%2A> propriété.</span><span class="sxs-lookup"><span data-stu-id="12318-102">Sets the claim type that specifies the <xref:System.Security.Principal.IIdentity.Name%2A> property.</span></span> <span data-ttu-id="12318-103">Le type de revendication est utilisé pour rechercher un <xref:System.Security.Claims.Claim> objet dans la collection <xref:System.Security.Claims.ClaimsIdentity> d’objets retournés par la <xref:System.IdentityModel.Tokens.SecurityTokenHandler.ValidateToken%2A> méthode de ce gestionnaire de jetons.</span><span class="sxs-lookup"><span data-stu-id="12318-103">The claim type is used to search for a <xref:System.Security.Claims.Claim> in the collection of <xref:System.Security.Claims.ClaimsIdentity> objects returned by the <xref:System.IdentityModel.Tokens.SecurityTokenHandler.ValidateToken%2A> method of this token handler.</span></span> <span data-ttu-id="12318-104">La valeur de la revendication correspondante est ensuite définie en tant que nom du <xref:System.Security.Principal.IIdentity> généré à partir de ce gestionnaire de jetons.</span><span class="sxs-lookup"><span data-stu-id="12318-104">The value of the matching claim is then set as the name of the <xref:System.Security.Principal.IIdentity> generated from this token handler.</span></span>  
  
 <span data-ttu-id="12318-105">\<system.identityModel></span><span class="sxs-lookup"><span data-stu-id="12318-105">\<system.identityModel></span></span>  
<span data-ttu-id="12318-106">\<identityConfiguration></span><span class="sxs-lookup"><span data-stu-id="12318-106">\<identityConfiguration></span></span>  
<span data-ttu-id="12318-107">\<securityTokenHandlers></span><span class="sxs-lookup"><span data-stu-id="12318-107">\<securityTokenHandlers></span></span>  
<span data-ttu-id="12318-108">\<add></span><span class="sxs-lookup"><span data-stu-id="12318-108">\<add></span></span>  
<span data-ttu-id="12318-109">\<samlSecurityTokenRequirement></span><span class="sxs-lookup"><span data-stu-id="12318-109">\<samlSecurityTokenRequirement></span></span>  
<span data-ttu-id="12318-110">\<nameClaimType></span><span class="sxs-lookup"><span data-stu-id="12318-110">\<nameClaimType></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="12318-111">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="12318-111">Syntax</span></span>  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <securityTokenHandlers>  
      <add>  
        <samlSecurityTokenRequirement>  
          <nameClaimType value=xs:string>  
          </nameClaimType>  
        </samlSecurityTokenRequirement>  
      </add>  
    </securityTokenHandlers>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="12318-112">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="12318-112">Attributes and Elements</span></span>  
 <span data-ttu-id="12318-113">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="12318-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="12318-114">Attributs</span><span class="sxs-lookup"><span data-stu-id="12318-114">Attributes</span></span>  
  
|<span data-ttu-id="12318-115">Attribut</span><span class="sxs-lookup"><span data-stu-id="12318-115">Attribute</span></span>|<span data-ttu-id="12318-116">Description</span><span class="sxs-lookup"><span data-stu-id="12318-116">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="12318-117">value</span><span class="sxs-lookup"><span data-stu-id="12318-117">value</span></span>|<span data-ttu-id="12318-118">Chaîne qui spécifie l’URI qui représente le type de revendication de la revendication à utiliser pour <xref:System.Security.Principal.IIdentity.Name%2A> la propriété.</span><span class="sxs-lookup"><span data-stu-id="12318-118">A string that specifies the URI that represents the claim type of the claim to use for the <xref:System.Security.Principal.IIdentity.Name%2A> property.</span></span> <span data-ttu-id="12318-119">Requis.</span><span class="sxs-lookup"><span data-stu-id="12318-119">Required.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="12318-120">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="12318-120">Child Elements</span></span>  
 <span data-ttu-id="12318-121">Aucun</span><span class="sxs-lookup"><span data-stu-id="12318-121">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="12318-122">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="12318-122">Parent Elements</span></span>  
  
|<span data-ttu-id="12318-123">Élément</span><span class="sxs-lookup"><span data-stu-id="12318-123">Element</span></span>|<span data-ttu-id="12318-124">Description</span><span class="sxs-lookup"><span data-stu-id="12318-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="12318-125">\<samlSecurityTokenRequirement></span><span class="sxs-lookup"><span data-stu-id="12318-125">\<samlSecurityTokenRequirement></span></span>](samlsecuritytokenrequirement.md)|<span data-ttu-id="12318-126">Fournit la configuration pour <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> la classe, <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> la classe ou une classe dérivée de l’une de ces classes.</span><span class="sxs-lookup"><span data-stu-id="12318-126">Provides configuration for the <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> class, the <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> class, or a derived class of either of these classes.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="12318-127">Notes</span><span class="sxs-lookup"><span data-stu-id="12318-127">Remarks</span></span>  
 <span data-ttu-id="12318-128">L' `<nameClaimType>` élément définit la <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement.NameClaimType%2A> propriété lorsqu’un <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement> objet est initialisé à partir de la configuration.</span><span class="sxs-lookup"><span data-stu-id="12318-128">The `<nameClaimType>` element sets the <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement.NameClaimType%2A> property when a <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement> object is initialized from configuration.</span></span>  
  
## <a name="example"></a><span data-ttu-id="12318-129">Exemples</span><span class="sxs-lookup"><span data-stu-id="12318-129">Example</span></span>  
  
```xml  
<add type="System.IdentityModel.Tokens.SamlSecurityTokenHandler, System.IdentityModel">  
    <samlSecurityTokenRequirement>  
        <nameClaimType value="http://schemas.xmlsoap.org/ws/2005/05/identity/claims/name" />  
    </samlSecurityTokenRequirement>  
</add>  
```  
  
## <a name="see-also"></a><span data-ttu-id="12318-130">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="12318-130">See also</span></span>

- <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement.NameClaimType%2A>
