---
title: <nameClaimType>
ms.date: 03/30/2017
ms.assetid: 17514d95-f0f5-4789-8e28-346640dc227c
author: BrucePerlerMS
ms.openlocfilehash: 4bf8ad2f70499edfc72dd9fcd9a5d8a0aafbbc66
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70251936"
---
# <a name="nameclaimtype"></a><span data-ttu-id="713c0-101">\<nameClaimType></span><span class="sxs-lookup"><span data-stu-id="713c0-101">\<nameClaimType></span></span>
<span data-ttu-id="713c0-102">Définit le type de revendication qui spécifie la <xref:System.Security.Principal.IIdentity.Name%2A> propriété.</span><span class="sxs-lookup"><span data-stu-id="713c0-102">Sets the claim type that specifies the <xref:System.Security.Principal.IIdentity.Name%2A> property.</span></span> <span data-ttu-id="713c0-103">Le type de revendication est utilisé pour rechercher un <xref:System.Security.Claims.Claim> objet dans la collection <xref:System.Security.Claims.ClaimsIdentity> d’objets retournés par la <xref:System.IdentityModel.Tokens.SecurityTokenHandler.ValidateToken%2A> méthode de ce gestionnaire de jetons.</span><span class="sxs-lookup"><span data-stu-id="713c0-103">The claim type is used to search for a <xref:System.Security.Claims.Claim> in the collection of <xref:System.Security.Claims.ClaimsIdentity> objects returned by the <xref:System.IdentityModel.Tokens.SecurityTokenHandler.ValidateToken%2A> method of this token handler.</span></span> <span data-ttu-id="713c0-104">La valeur de la revendication correspondante est ensuite définie en tant que nom du <xref:System.Security.Principal.IIdentity> généré à partir de ce gestionnaire de jetons.</span><span class="sxs-lookup"><span data-stu-id="713c0-104">The value of the matching claim is then set as the name of the <xref:System.Security.Principal.IIdentity> generated from this token handler.</span></span>  
  
<span data-ttu-id="713c0-105">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="713c0-105">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="713c0-106">&nbsp;&nbsp;[ **\<System. identityModel >** ](system-identitymodel.md)</span><span class="sxs-lookup"><span data-stu-id="713c0-106">&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)</span></span>\
<span data-ttu-id="713c0-107">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<identityConfiguration >** ](identityconfiguration.md)</span><span class="sxs-lookup"><span data-stu-id="713c0-107">&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)</span></span>\
<span data-ttu-id="713c0-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<securityTokenHandlers >** ](securitytokenhandlers.md)</span><span class="sxs-lookup"><span data-stu-id="713c0-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<securityTokenHandlers>**](securitytokenhandlers.md)</span></span>\
<span data-ttu-id="713c0-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<Ajouter >** ](add.md)</span><span class="sxs-lookup"><span data-stu-id="713c0-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<add>**](add.md)</span></span>\
<span data-ttu-id="713c0-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<samlSecurityTokenRequirement >** ](samlsecuritytokenrequirement.md)</span><span class="sxs-lookup"><span data-stu-id="713c0-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<samlSecurityTokenRequirement>**](samlsecuritytokenrequirement.md)</span></span>\
<span data-ttu-id="713c0-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<nameClaimType >**</span><span class="sxs-lookup"><span data-stu-id="713c0-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<nameClaimType>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="713c0-112">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="713c0-112">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="713c0-113">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="713c0-113">Attributes and Elements</span></span>  
 <span data-ttu-id="713c0-114">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="713c0-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="713c0-115">Attributs</span><span class="sxs-lookup"><span data-stu-id="713c0-115">Attributes</span></span>  
  
|<span data-ttu-id="713c0-116">Attribut</span><span class="sxs-lookup"><span data-stu-id="713c0-116">Attribute</span></span>|<span data-ttu-id="713c0-117">Description</span><span class="sxs-lookup"><span data-stu-id="713c0-117">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="713c0-118">value</span><span class="sxs-lookup"><span data-stu-id="713c0-118">value</span></span>|<span data-ttu-id="713c0-119">Chaîne qui spécifie l’URI qui représente le type de revendication de la revendication à utiliser pour <xref:System.Security.Principal.IIdentity.Name%2A> la propriété.</span><span class="sxs-lookup"><span data-stu-id="713c0-119">A string that specifies the URI that represents the claim type of the claim to use for the <xref:System.Security.Principal.IIdentity.Name%2A> property.</span></span> <span data-ttu-id="713c0-120">Requis.</span><span class="sxs-lookup"><span data-stu-id="713c0-120">Required.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="713c0-121">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="713c0-121">Child Elements</span></span>  
 <span data-ttu-id="713c0-122">Aucun</span><span class="sxs-lookup"><span data-stu-id="713c0-122">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="713c0-123">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="713c0-123">Parent Elements</span></span>  
  
|<span data-ttu-id="713c0-124">Élément</span><span class="sxs-lookup"><span data-stu-id="713c0-124">Element</span></span>|<span data-ttu-id="713c0-125">Description</span><span class="sxs-lookup"><span data-stu-id="713c0-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="713c0-126">\<samlSecurityTokenRequirement></span><span class="sxs-lookup"><span data-stu-id="713c0-126">\<samlSecurityTokenRequirement></span></span>](samlsecuritytokenrequirement.md)|<span data-ttu-id="713c0-127">Fournit la configuration pour <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> la classe, <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> la classe ou une classe dérivée de l’une de ces classes.</span><span class="sxs-lookup"><span data-stu-id="713c0-127">Provides configuration for the <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> class, the <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> class, or a derived class of either of these classes.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="713c0-128">Notes</span><span class="sxs-lookup"><span data-stu-id="713c0-128">Remarks</span></span>  
 <span data-ttu-id="713c0-129">L' `<nameClaimType>` élément définit la <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement.NameClaimType%2A> propriété lorsqu’un <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement> objet est initialisé à partir de la configuration.</span><span class="sxs-lookup"><span data-stu-id="713c0-129">The `<nameClaimType>` element sets the <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement.NameClaimType%2A> property when a <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement> object is initialized from configuration.</span></span>  
  
## <a name="example"></a><span data-ttu-id="713c0-130">Exemple</span><span class="sxs-lookup"><span data-stu-id="713c0-130">Example</span></span>  
  
```xml  
<add type="System.IdentityModel.Tokens.SamlSecurityTokenHandler, System.IdentityModel">  
    <samlSecurityTokenRequirement>  
        <nameClaimType value="http://schemas.xmlsoap.org/ws/2005/05/identity/claims/name" />  
    </samlSecurityTokenRequirement>  
</add>  
```  
  
## <a name="see-also"></a><span data-ttu-id="713c0-131">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="713c0-131">See also</span></span>

- <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement.NameClaimType%2A>
