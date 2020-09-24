---
title: <nameClaimType>
ms.date: 03/30/2017
ms.assetid: 17514d95-f0f5-4789-8e28-346640dc227c
author: BrucePerlerMS
ms.openlocfilehash: 4ffc19366d91e4a14ee0f931d7009ede390cc097
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91165024"
---
# \<nameClaimType>

<span data-ttu-id="c0e31-101">Définit le type de revendication qui spécifie la <xref:System.Security.Principal.IIdentity.Name%2A> propriété.</span><span class="sxs-lookup"><span data-stu-id="c0e31-101">Sets the claim type that specifies the <xref:System.Security.Principal.IIdentity.Name%2A> property.</span></span> <span data-ttu-id="c0e31-102">Le type de revendication est utilisé pour rechercher un <xref:System.Security.Claims.Claim> objet dans la collection d' <xref:System.Security.Claims.ClaimsIdentity> objets retournés par la <xref:System.IdentityModel.Tokens.SecurityTokenHandler.ValidateToken%2A> méthode de ce gestionnaire de jetons.</span><span class="sxs-lookup"><span data-stu-id="c0e31-102">The claim type is used to search for a <xref:System.Security.Claims.Claim> in the collection of <xref:System.Security.Claims.ClaimsIdentity> objects returned by the <xref:System.IdentityModel.Tokens.SecurityTokenHandler.ValidateToken%2A> method of this token handler.</span></span> <span data-ttu-id="c0e31-103">La valeur de la revendication correspondante est ensuite définie en tant que nom du <xref:System.Security.Principal.IIdentity> généré à partir de ce gestionnaire de jetons.</span><span class="sxs-lookup"><span data-stu-id="c0e31-103">The value of the matching claim is then set as the name of the <xref:System.Security.Principal.IIdentity> generated from this token handler.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<securityTokenHandlers>**](securitytokenhandlers.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<add>**](add.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<samlSecurityTokenRequirement>**](samlsecuritytokenrequirement.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<nameClaimType>**  
  
## <a name="syntax"></a><span data-ttu-id="c0e31-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c0e31-104">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c0e31-105">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="c0e31-105">Attributes and Elements</span></span>  

 <span data-ttu-id="c0e31-106">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="c0e31-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c0e31-107">Attributs</span><span class="sxs-lookup"><span data-stu-id="c0e31-107">Attributes</span></span>  
  
|<span data-ttu-id="c0e31-108">Attribut</span><span class="sxs-lookup"><span data-stu-id="c0e31-108">Attribute</span></span>|<span data-ttu-id="c0e31-109">Description</span><span class="sxs-lookup"><span data-stu-id="c0e31-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="c0e31-110">value</span><span class="sxs-lookup"><span data-stu-id="c0e31-110">value</span></span>|<span data-ttu-id="c0e31-111">Chaîne qui spécifie l’URI qui représente le type de revendication de la revendication à utiliser pour la <xref:System.Security.Principal.IIdentity.Name%2A> propriété.</span><span class="sxs-lookup"><span data-stu-id="c0e31-111">A string that specifies the URI that represents the claim type of the claim to use for the <xref:System.Security.Principal.IIdentity.Name%2A> property.</span></span> <span data-ttu-id="c0e31-112">Obligatoire.</span><span class="sxs-lookup"><span data-stu-id="c0e31-112">Required.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="c0e31-113">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="c0e31-113">Child Elements</span></span>  

 <span data-ttu-id="c0e31-114">None</span><span class="sxs-lookup"><span data-stu-id="c0e31-114">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="c0e31-115">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="c0e31-115">Parent Elements</span></span>  
  
|<span data-ttu-id="c0e31-116">Élément</span><span class="sxs-lookup"><span data-stu-id="c0e31-116">Element</span></span>|<span data-ttu-id="c0e31-117">Description</span><span class="sxs-lookup"><span data-stu-id="c0e31-117">Description</span></span>|  
|-------------|-----------------|  
|[\<samlSecurityTokenRequirement>](samlsecuritytokenrequirement.md)|<span data-ttu-id="c0e31-118">Fournit la configuration pour la <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> classe, la <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> classe ou une classe dérivée de l’une de ces classes.</span><span class="sxs-lookup"><span data-stu-id="c0e31-118">Provides configuration for the <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> class, the <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> class, or a derived class of either of these classes.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c0e31-119">Notes</span><span class="sxs-lookup"><span data-stu-id="c0e31-119">Remarks</span></span>  

 <span data-ttu-id="c0e31-120">L' `<nameClaimType>` élément définit la <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement.NameClaimType%2A> propriété lorsqu’un <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement> objet est initialisé à partir de la configuration.</span><span class="sxs-lookup"><span data-stu-id="c0e31-120">The `<nameClaimType>` element sets the <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement.NameClaimType%2A> property when a <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement> object is initialized from configuration.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c0e31-121">Exemple</span><span class="sxs-lookup"><span data-stu-id="c0e31-121">Example</span></span>  
  
```xml  
<add type="System.IdentityModel.Tokens.SamlSecurityTokenHandler, System.IdentityModel">  
    <samlSecurityTokenRequirement>  
        <nameClaimType value="http://schemas.xmlsoap.org/ws/2005/05/identity/claims/name" />  
    </samlSecurityTokenRequirement>  
</add>  
```  
  
## <a name="see-also"></a><span data-ttu-id="c0e31-122">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c0e31-122">See also</span></span>

- <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement.NameClaimType%2A>
