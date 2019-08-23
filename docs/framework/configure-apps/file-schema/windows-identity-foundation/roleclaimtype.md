---
title: <roleClaimType>
ms.date: 03/30/2017
ms.assetid: 69a49deb-6369-41ba-806b-ae8d21fac64b
author: BrucePerlerMS
ms.openlocfilehash: 0ce2e06ee895d09de193bac1fe7038e71794dda4
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69942539"
---
# <a name="roleclaimtype"></a><span data-ttu-id="f648c-101">\<roleClaimType></span><span class="sxs-lookup"><span data-stu-id="f648c-101">\<roleClaimType></span></span>
<span data-ttu-id="f648c-102">Spécifie le type de revendication qui définit les revendications de type de rôle <xref:System.Security.Claims.ClaimsIdentity> dans la collection d' <xref:System.IdentityModel.Tokens.SecurityTokenHandler.ValidateToken%2A> objets retournée par la méthode du gestionnaire de jetons.</span><span class="sxs-lookup"><span data-stu-id="f648c-102">Specifies the claim type that defines the role type claims in the collection of <xref:System.Security.Claims.ClaimsIdentity> objects returned by the <xref:System.IdentityModel.Tokens.SecurityTokenHandler.ValidateToken%2A> method of the token handler.</span></span>  
  
 <span data-ttu-id="f648c-103">\<system.identityModel></span><span class="sxs-lookup"><span data-stu-id="f648c-103">\<system.identityModel></span></span>  
<span data-ttu-id="f648c-104">\<identityConfiguration></span><span class="sxs-lookup"><span data-stu-id="f648c-104">\<identityConfiguration></span></span>  
<span data-ttu-id="f648c-105">\<securityTokenHandlers></span><span class="sxs-lookup"><span data-stu-id="f648c-105">\<securityTokenHandlers></span></span>  
<span data-ttu-id="f648c-106">\<add></span><span class="sxs-lookup"><span data-stu-id="f648c-106">\<add></span></span>  
<span data-ttu-id="f648c-107">\<samlSecurityTokenRequirement></span><span class="sxs-lookup"><span data-stu-id="f648c-107">\<samlSecurityTokenRequirement></span></span>  
<span data-ttu-id="f648c-108">\<roleClaimType></span><span class="sxs-lookup"><span data-stu-id="f648c-108">\<roleClaimType></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f648c-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f648c-109">Syntax</span></span>  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <securityTokenHandlers>  
      <add>  
        <samlSecurityTokenRequirement>  
          <roleClaimType value=xs:string>  
          </roleClaimType>  
        </samlSecurityTokenRequirement>  
      </add>  
    </securityTokenHandlers>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f648c-110">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="f648c-110">Attributes and Elements</span></span>  
 <span data-ttu-id="f648c-111">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="f648c-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f648c-112">Attributs</span><span class="sxs-lookup"><span data-stu-id="f648c-112">Attributes</span></span>  
  
|<span data-ttu-id="f648c-113">Attribut</span><span class="sxs-lookup"><span data-stu-id="f648c-113">Attribute</span></span>|<span data-ttu-id="f648c-114">Description</span><span class="sxs-lookup"><span data-stu-id="f648c-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="f648c-115">value</span><span class="sxs-lookup"><span data-stu-id="f648c-115">value</span></span>|<span data-ttu-id="f648c-116">Chaîne qui spécifie l’URI qui représente le type de revendication de la revendication à utiliser pour le type de revendication de rôle.</span><span class="sxs-lookup"><span data-stu-id="f648c-116">A string that specifies the URI that represents the claim type of the claim to use for the role claim type.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="f648c-117">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="f648c-117">Child Elements</span></span>  
 <span data-ttu-id="f648c-118">Aucun</span><span class="sxs-lookup"><span data-stu-id="f648c-118">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="f648c-119">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="f648c-119">Parent Elements</span></span>  
  
|<span data-ttu-id="f648c-120">Élément</span><span class="sxs-lookup"><span data-stu-id="f648c-120">Element</span></span>|<span data-ttu-id="f648c-121">Description</span><span class="sxs-lookup"><span data-stu-id="f648c-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f648c-122">\<samlSecurityTokenRequirement></span><span class="sxs-lookup"><span data-stu-id="f648c-122">\<samlSecurityTokenRequirement></span></span>](samlsecuritytokenrequirement.md)|<span data-ttu-id="f648c-123">Fournit la configuration pour <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> la classe, <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> la classe ou une classe dérivée de l’une de ces classes.</span><span class="sxs-lookup"><span data-stu-id="f648c-123">Provides configuration for the <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> class, the <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> class, or a derived class of either of these classes.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f648c-124">Notes</span><span class="sxs-lookup"><span data-stu-id="f648c-124">Remarks</span></span>  
 <span data-ttu-id="f648c-125">L' `<roleClaimType>` élément définit la <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement.RoleClaimType%2A> propriété lorsqu’un <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement> objet est initialisé à partir de la configuration.</span><span class="sxs-lookup"><span data-stu-id="f648c-125">The `<roleClaimType>` element sets the <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement.RoleClaimType%2A> property when a <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement> object is initialized from configuration.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f648c-126">Exemple</span><span class="sxs-lookup"><span data-stu-id="f648c-126">Example</span></span>  
  
```xml  
<add type="System.IdentityModel.Tokens.SamlSecurityTokenHandler, System.IdentityModel">  
    <samlSecurityTokenRequirement>  
        <roleClaimType value="schemas.microsoft.com/ws/2006/04/identity/claims/role" />  
    </samlSecurityTokenRequirement>  
</add>  
```  
  
## <a name="see-also"></a><span data-ttu-id="f648c-127">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f648c-127">See also</span></span>

- <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement.RoleClaimType%2A>
