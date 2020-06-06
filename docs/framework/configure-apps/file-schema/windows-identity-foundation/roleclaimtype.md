---
title: <roleClaimType>
ms.date: 03/30/2017
ms.assetid: 69a49deb-6369-41ba-806b-ae8d21fac64b
author: BrucePerlerMS
ms.openlocfilehash: 0f651377346b1f14a4226128cd5cf7059543adca
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/06/2020
ms.locfileid: "70251909"
---
# \<roleClaimType>
<span data-ttu-id="697e2-101">Spécifie le type de revendication qui définit les revendications de type de rôle dans la collection d' <xref:System.Security.Claims.ClaimsIdentity> objets retournée par la <xref:System.IdentityModel.Tokens.SecurityTokenHandler.ValidateToken%2A> méthode du gestionnaire de jetons.</span><span class="sxs-lookup"><span data-stu-id="697e2-101">Specifies the claim type that defines the role type claims in the collection of <xref:System.Security.Claims.ClaimsIdentity> objects returned by the <xref:System.IdentityModel.Tokens.SecurityTokenHandler.ValidateToken%2A> method of the token handler.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<securityTokenHandlers>**](securitytokenhandlers.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<add>**](add.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<samlSecurityTokenRequirement>**](samlsecuritytokenrequirement.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<roleClaimType>**  
  
## <a name="syntax"></a><span data-ttu-id="697e2-102">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="697e2-102">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="697e2-103">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="697e2-103">Attributes and Elements</span></span>  
 <span data-ttu-id="697e2-104">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="697e2-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="697e2-105">Attributs</span><span class="sxs-lookup"><span data-stu-id="697e2-105">Attributes</span></span>  
  
|<span data-ttu-id="697e2-106">Attribut</span><span class="sxs-lookup"><span data-stu-id="697e2-106">Attribute</span></span>|<span data-ttu-id="697e2-107">Description</span><span class="sxs-lookup"><span data-stu-id="697e2-107">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="697e2-108">value</span><span class="sxs-lookup"><span data-stu-id="697e2-108">value</span></span>|<span data-ttu-id="697e2-109">Chaîne qui spécifie l’URI qui représente le type de revendication de la revendication à utiliser pour le type de revendication de rôle.</span><span class="sxs-lookup"><span data-stu-id="697e2-109">A string that specifies the URI that represents the claim type of the claim to use for the role claim type.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="697e2-110">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="697e2-110">Child Elements</span></span>  
 <span data-ttu-id="697e2-111">Aucune</span><span class="sxs-lookup"><span data-stu-id="697e2-111">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="697e2-112">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="697e2-112">Parent Elements</span></span>  
  
|<span data-ttu-id="697e2-113">Élément</span><span class="sxs-lookup"><span data-stu-id="697e2-113">Element</span></span>|<span data-ttu-id="697e2-114">Description</span><span class="sxs-lookup"><span data-stu-id="697e2-114">Description</span></span>|  
|-------------|-----------------|  
|[\<samlSecurityTokenRequirement>](samlsecuritytokenrequirement.md)|<span data-ttu-id="697e2-115">Fournit la configuration pour la <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> classe, la <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> classe ou une classe dérivée de l’une de ces classes.</span><span class="sxs-lookup"><span data-stu-id="697e2-115">Provides configuration for the <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> class, the <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> class, or a derived class of either of these classes.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="697e2-116">Remarques</span><span class="sxs-lookup"><span data-stu-id="697e2-116">Remarks</span></span>  
 <span data-ttu-id="697e2-117">L' `<roleClaimType>` élément définit la <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement.RoleClaimType%2A> propriété lorsqu’un <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement> objet est initialisé à partir de la configuration.</span><span class="sxs-lookup"><span data-stu-id="697e2-117">The `<roleClaimType>` element sets the <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement.RoleClaimType%2A> property when a <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement> object is initialized from configuration.</span></span>  
  
## <a name="example"></a><span data-ttu-id="697e2-118">Exemple</span><span class="sxs-lookup"><span data-stu-id="697e2-118">Example</span></span>  
  
```xml  
<add type="System.IdentityModel.Tokens.SamlSecurityTokenHandler, System.IdentityModel">  
    <samlSecurityTokenRequirement>  
        <roleClaimType value="schemas.microsoft.com/ws/2006/04/identity/claims/role" />  
    </samlSecurityTokenRequirement>  
</add>  
```  
  
## <a name="see-also"></a><span data-ttu-id="697e2-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="697e2-119">See also</span></span>

- <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement.RoleClaimType%2A>
