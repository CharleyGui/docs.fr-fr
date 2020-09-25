---
title: <userNameSecurityTokenHandlerRequirement>
ms.date: 03/30/2017
ms.assetid: 6ec3bac1-b014-49ae-843c-c54518cb709a
author: BrucePerlerMS
ms.openlocfilehash: a49b41c04c8f184188b62e04c3b232bd33752fca
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91185520"
---
# \<userNameSecurityTokenHandlerRequirement>

<span data-ttu-id="6c53a-101">Fournit la configuration pour la <xref:System.IdentityModel.Services.Tokens.MembershipUserNameSecurityTokenHandler> classe ou les classes dérivées.</span><span class="sxs-lookup"><span data-stu-id="6c53a-101">Provides configuration for the <xref:System.IdentityModel.Services.Tokens.MembershipUserNameSecurityTokenHandler> class or derived classes.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<securityTokenHandlers>**](securitytokenhandlers.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<add>**](add.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<userNameSecurityTokenHandlerRequirement>**  
  
## <a name="syntax"></a><span data-ttu-id="6c53a-102">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6c53a-102">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="6c53a-103">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="6c53a-103">Attributes and Elements</span></span>  

 <span data-ttu-id="6c53a-104">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="6c53a-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="6c53a-105">Attributs</span><span class="sxs-lookup"><span data-stu-id="6c53a-105">Attributes</span></span>  
  
|<span data-ttu-id="6c53a-106">Attribut</span><span class="sxs-lookup"><span data-stu-id="6c53a-106">Attribute</span></span>|<span data-ttu-id="6c53a-107">Description</span><span class="sxs-lookup"><span data-stu-id="6c53a-107">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="6c53a-108">membershipProviderName</span><span class="sxs-lookup"><span data-stu-id="6c53a-108">membershipProviderName</span></span>|<span data-ttu-id="6c53a-109">Spécifie le <xref:System.Web.Security.MembershipProvider> qui doit être utilisé par le gestionnaire de jetons de sécurité.</span><span class="sxs-lookup"><span data-stu-id="6c53a-109">Specifies the <xref:System.Web.Security.MembershipProvider> that should be used by the security token handler.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="6c53a-110">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="6c53a-110">Child Elements</span></span>  

 <span data-ttu-id="6c53a-111">None</span><span class="sxs-lookup"><span data-stu-id="6c53a-111">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="6c53a-112">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="6c53a-112">Parent Elements</span></span>  
  
|<span data-ttu-id="6c53a-113">Élément</span><span class="sxs-lookup"><span data-stu-id="6c53a-113">Element</span></span>|<span data-ttu-id="6c53a-114">Description</span><span class="sxs-lookup"><span data-stu-id="6c53a-114">Description</span></span>|  
|-------------|-----------------|  
|[\<add>](add.md)|<span data-ttu-id="6c53a-115">Ajoute le gestionnaire de jetons de sécurité spécifié à la collection de gestionnaires de jetons.</span><span class="sxs-lookup"><span data-stu-id="6c53a-115">Adds the specified security token handler to the token handler collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6c53a-116">Notes</span><span class="sxs-lookup"><span data-stu-id="6c53a-116">Remarks</span></span>  

 <span data-ttu-id="6c53a-117">L' `<userNameSecurityTokenHandlerRequirement>` élément définit la <xref:System.IdentityModel.Services.Tokens.MembershipUserNameSecurityTokenHandler.MembershipProvider%2A> propriété lorsqu’un <xref:System.IdentityModel.Services.Tokens.MembershipUserNameSecurityTokenHandler> objet est initialisé à partir de la configuration.</span><span class="sxs-lookup"><span data-stu-id="6c53a-117">The `<userNameSecurityTokenHandlerRequirement>` element sets the <xref:System.IdentityModel.Services.Tokens.MembershipUserNameSecurityTokenHandler.MembershipProvider%2A> property when a <xref:System.IdentityModel.Services.Tokens.MembershipUserNameSecurityTokenHandler> object is initialized from configuration.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6c53a-118">Exemple</span><span class="sxs-lookup"><span data-stu-id="6c53a-118">Example</span></span>  
  
```xml  
<add type="System.IdentityModel.Services.Tokens.MembershipUserNameSecurityTokenHandler, System.IdentityModel.Services">  
    <userNameSecurityTokenHandlerRequirement membershipProviderName="AspNetSqlProvider/>  
</add>  
```
