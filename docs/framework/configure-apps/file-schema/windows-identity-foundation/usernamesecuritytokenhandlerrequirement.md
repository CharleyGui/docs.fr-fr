---
title: <userNameSecurityTokenHandlerRequirement>
ms.date: 03/30/2017
ms.assetid: 6ec3bac1-b014-49ae-843c-c54518cb709a
author: BrucePerlerMS
ms.openlocfilehash: 5863c01e97e7f5fb6fe07c43174c0d6cb7a0a25d
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70251749"
---
# <a name="usernamesecuritytokenhandlerrequirement"></a><span data-ttu-id="24ed9-101">\<userNameSecurityTokenHandlerRequirement></span><span class="sxs-lookup"><span data-stu-id="24ed9-101">\<userNameSecurityTokenHandlerRequirement></span></span>
<span data-ttu-id="24ed9-102">Fournit la configuration pour <xref:System.IdentityModel.Services.Tokens.MembershipUserNameSecurityTokenHandler> la classe ou les classes dérivées.</span><span class="sxs-lookup"><span data-stu-id="24ed9-102">Provides configuration for the <xref:System.IdentityModel.Services.Tokens.MembershipUserNameSecurityTokenHandler> class or derived classes.</span></span>  
  
<span data-ttu-id="24ed9-103">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="24ed9-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="24ed9-104">&nbsp;&nbsp;[ **\<System. identityModel >** ](system-identitymodel.md)</span><span class="sxs-lookup"><span data-stu-id="24ed9-104">&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)</span></span>\
<span data-ttu-id="24ed9-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<identityConfiguration >** ](identityconfiguration.md)</span><span class="sxs-lookup"><span data-stu-id="24ed9-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)</span></span>\
<span data-ttu-id="24ed9-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<securityTokenHandlers >** ](securitytokenhandlers.md)</span><span class="sxs-lookup"><span data-stu-id="24ed9-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<securityTokenHandlers>**](securitytokenhandlers.md)</span></span>\
<span data-ttu-id="24ed9-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<Ajouter >** ](add.md)</span><span class="sxs-lookup"><span data-stu-id="24ed9-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<add>**](add.md)</span></span>\
<span data-ttu-id="24ed9-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<userNameSecurityTokenHandlerRequirement >**</span><span class="sxs-lookup"><span data-stu-id="24ed9-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<userNameSecurityTokenHandlerRequirement>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="24ed9-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="24ed9-109">Syntax</span></span>  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <securityTokenHandlers>  
      <add type="System.IdentityModel.Services.Tokens.MembershipUserNameSecurityTokenHandler, System.IdentityModel.Services">  
        <userNameSecurityTokenHandlerRequirement membershipProviderName=xs:string >  
        </userNameSecurityTokenHandlerRequirement>  
      </add>  
    </securityTokenHandlers>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="24ed9-110">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="24ed9-110">Attributes and Elements</span></span>  
 <span data-ttu-id="24ed9-111">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="24ed9-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="24ed9-112">Attributs</span><span class="sxs-lookup"><span data-stu-id="24ed9-112">Attributes</span></span>  
  
|<span data-ttu-id="24ed9-113">Attribut</span><span class="sxs-lookup"><span data-stu-id="24ed9-113">Attribute</span></span>|<span data-ttu-id="24ed9-114">Description</span><span class="sxs-lookup"><span data-stu-id="24ed9-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="24ed9-115">membershipProviderName</span><span class="sxs-lookup"><span data-stu-id="24ed9-115">membershipProviderName</span></span>|<span data-ttu-id="24ed9-116">Spécifie <xref:System.Web.Security.MembershipProvider> le qui doit être utilisé par le gestionnaire de jetons de sécurité.</span><span class="sxs-lookup"><span data-stu-id="24ed9-116">Specifies the <xref:System.Web.Security.MembershipProvider> that should be used by the security token handler.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="24ed9-117">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="24ed9-117">Child Elements</span></span>  
 <span data-ttu-id="24ed9-118">Aucun</span><span class="sxs-lookup"><span data-stu-id="24ed9-118">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="24ed9-119">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="24ed9-119">Parent Elements</span></span>  
  
|<span data-ttu-id="24ed9-120">Élément</span><span class="sxs-lookup"><span data-stu-id="24ed9-120">Element</span></span>|<span data-ttu-id="24ed9-121">Description</span><span class="sxs-lookup"><span data-stu-id="24ed9-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="24ed9-122">\<add></span><span class="sxs-lookup"><span data-stu-id="24ed9-122">\<add></span></span>](add.md)|<span data-ttu-id="24ed9-123">Ajoute le gestionnaire de jetons de sécurité spécifié à la collection de gestionnaires de jetons.</span><span class="sxs-lookup"><span data-stu-id="24ed9-123">Adds the specified security token handler to the token handler collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="24ed9-124">Notes</span><span class="sxs-lookup"><span data-stu-id="24ed9-124">Remarks</span></span>  
 <span data-ttu-id="24ed9-125">L' `<userNameSecurityTokenHandlerRequirement>` élément définit la <xref:System.IdentityModel.Services.Tokens.MembershipUserNameSecurityTokenHandler.MembershipProvider%2A> propriété lorsqu’un <xref:System.IdentityModel.Services.Tokens.MembershipUserNameSecurityTokenHandler> objet est initialisé à partir de la configuration.</span><span class="sxs-lookup"><span data-stu-id="24ed9-125">The `<userNameSecurityTokenHandlerRequirement>` element sets the <xref:System.IdentityModel.Services.Tokens.MembershipUserNameSecurityTokenHandler.MembershipProvider%2A> property when a <xref:System.IdentityModel.Services.Tokens.MembershipUserNameSecurityTokenHandler> object is initialized from configuration.</span></span>  
  
## <a name="example"></a><span data-ttu-id="24ed9-126">Exemples</span><span class="sxs-lookup"><span data-stu-id="24ed9-126">Example</span></span>  
  
```xml  
<add type="System.IdentityModel.Services.Tokens.MembershipUserNameSecurityTokenHandler, System.IdentityModel.Services">  
    <userNameSecurityTokenHandlerRequirement membershipProviderName="AspNetSqlProvider/>  
</add>  
```
