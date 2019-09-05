---
title: <roleClaimType>
ms.date: 03/30/2017
ms.assetid: 69a49deb-6369-41ba-806b-ae8d21fac64b
author: BrucePerlerMS
ms.openlocfilehash: 0f651377346b1f14a4226128cd5cf7059543adca
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70251909"
---
# <a name="roleclaimtype"></a><span data-ttu-id="a5ee8-101">\<roleClaimType></span><span class="sxs-lookup"><span data-stu-id="a5ee8-101">\<roleClaimType></span></span>
<span data-ttu-id="a5ee8-102">Spécifie le type de revendication qui définit les revendications de type de rôle <xref:System.Security.Claims.ClaimsIdentity> dans la collection d' <xref:System.IdentityModel.Tokens.SecurityTokenHandler.ValidateToken%2A> objets retournée par la méthode du gestionnaire de jetons.</span><span class="sxs-lookup"><span data-stu-id="a5ee8-102">Specifies the claim type that defines the role type claims in the collection of <xref:System.Security.Claims.ClaimsIdentity> objects returned by the <xref:System.IdentityModel.Tokens.SecurityTokenHandler.ValidateToken%2A> method of the token handler.</span></span>  
  
<span data-ttu-id="a5ee8-103">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="a5ee8-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="a5ee8-104">&nbsp;&nbsp;[ **\<System. identityModel >** ](system-identitymodel.md)</span><span class="sxs-lookup"><span data-stu-id="a5ee8-104">&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)</span></span>\
<span data-ttu-id="a5ee8-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<identityConfiguration >** ](identityconfiguration.md)</span><span class="sxs-lookup"><span data-stu-id="a5ee8-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)</span></span>\
<span data-ttu-id="a5ee8-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<securityTokenHandlers >** ](securitytokenhandlers.md)</span><span class="sxs-lookup"><span data-stu-id="a5ee8-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<securityTokenHandlers>**](securitytokenhandlers.md)</span></span>\
<span data-ttu-id="a5ee8-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<Ajouter >** ](add.md)</span><span class="sxs-lookup"><span data-stu-id="a5ee8-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<add>**](add.md)</span></span>\
<span data-ttu-id="a5ee8-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<samlSecurityTokenRequirement >** ](samlsecuritytokenrequirement.md)</span><span class="sxs-lookup"><span data-stu-id="a5ee8-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<samlSecurityTokenRequirement>**](samlsecuritytokenrequirement.md)</span></span>\
<span data-ttu-id="a5ee8-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<roleClaimType >**</span><span class="sxs-lookup"><span data-stu-id="a5ee8-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<roleClaimType>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a5ee8-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a5ee8-110">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a5ee8-111">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="a5ee8-111">Attributes and Elements</span></span>  
 <span data-ttu-id="a5ee8-112">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="a5ee8-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a5ee8-113">Attributs</span><span class="sxs-lookup"><span data-stu-id="a5ee8-113">Attributes</span></span>  
  
|<span data-ttu-id="a5ee8-114">Attribut</span><span class="sxs-lookup"><span data-stu-id="a5ee8-114">Attribute</span></span>|<span data-ttu-id="a5ee8-115">Description</span><span class="sxs-lookup"><span data-stu-id="a5ee8-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="a5ee8-116">value</span><span class="sxs-lookup"><span data-stu-id="a5ee8-116">value</span></span>|<span data-ttu-id="a5ee8-117">Chaîne qui spécifie l’URI qui représente le type de revendication de la revendication à utiliser pour le type de revendication de rôle.</span><span class="sxs-lookup"><span data-stu-id="a5ee8-117">A string that specifies the URI that represents the claim type of the claim to use for the role claim type.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="a5ee8-118">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="a5ee8-118">Child Elements</span></span>  
 <span data-ttu-id="a5ee8-119">Aucun</span><span class="sxs-lookup"><span data-stu-id="a5ee8-119">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="a5ee8-120">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="a5ee8-120">Parent Elements</span></span>  
  
|<span data-ttu-id="a5ee8-121">Élément</span><span class="sxs-lookup"><span data-stu-id="a5ee8-121">Element</span></span>|<span data-ttu-id="a5ee8-122">Description</span><span class="sxs-lookup"><span data-stu-id="a5ee8-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a5ee8-123">\<samlSecurityTokenRequirement></span><span class="sxs-lookup"><span data-stu-id="a5ee8-123">\<samlSecurityTokenRequirement></span></span>](samlsecuritytokenrequirement.md)|<span data-ttu-id="a5ee8-124">Fournit la configuration pour <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> la classe, <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> la classe ou une classe dérivée de l’une de ces classes.</span><span class="sxs-lookup"><span data-stu-id="a5ee8-124">Provides configuration for the <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> class, the <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> class, or a derived class of either of these classes.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a5ee8-125">Notes</span><span class="sxs-lookup"><span data-stu-id="a5ee8-125">Remarks</span></span>  
 <span data-ttu-id="a5ee8-126">L' `<roleClaimType>` élément définit la <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement.RoleClaimType%2A> propriété lorsqu’un <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement> objet est initialisé à partir de la configuration.</span><span class="sxs-lookup"><span data-stu-id="a5ee8-126">The `<roleClaimType>` element sets the <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement.RoleClaimType%2A> property when a <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement> object is initialized from configuration.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a5ee8-127">Exemple</span><span class="sxs-lookup"><span data-stu-id="a5ee8-127">Example</span></span>  
  
```xml  
<add type="System.IdentityModel.Tokens.SamlSecurityTokenHandler, System.IdentityModel">  
    <samlSecurityTokenRequirement>  
        <roleClaimType value="schemas.microsoft.com/ws/2006/04/identity/claims/role" />  
    </samlSecurityTokenRequirement>  
</add>  
```  
  
## <a name="see-also"></a><span data-ttu-id="a5ee8-128">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a5ee8-128">See also</span></span>

- <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement.RoleClaimType%2A>
