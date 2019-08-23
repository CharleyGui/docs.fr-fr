---
title: <userNameSecurityTokenHandlerRequirement>
ms.date: 03/30/2017
ms.assetid: 6ec3bac1-b014-49ae-843c-c54518cb709a
author: BrucePerlerMS
ms.openlocfilehash: fed8964e03b80e365fdc5eafd45b4fc372a6e352
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69944253"
---
# <a name="usernamesecuritytokenhandlerrequirement"></a><span data-ttu-id="1c5e1-101">\<userNameSecurityTokenHandlerRequirement></span><span class="sxs-lookup"><span data-stu-id="1c5e1-101">\<userNameSecurityTokenHandlerRequirement></span></span>
<span data-ttu-id="1c5e1-102">Fournit la configuration pour <xref:System.IdentityModel.Services.Tokens.MembershipUserNameSecurityTokenHandler> la classe ou les classes dérivées.</span><span class="sxs-lookup"><span data-stu-id="1c5e1-102">Provides configuration for the <xref:System.IdentityModel.Services.Tokens.MembershipUserNameSecurityTokenHandler> class or derived classes.</span></span>  
  
 <span data-ttu-id="1c5e1-103">\<system.identityModel></span><span class="sxs-lookup"><span data-stu-id="1c5e1-103">\<system.identityModel></span></span>  
<span data-ttu-id="1c5e1-104">\<identityConfiguration></span><span class="sxs-lookup"><span data-stu-id="1c5e1-104">\<identityConfiguration></span></span>  
<span data-ttu-id="1c5e1-105">\<securityTokenHandlers></span><span class="sxs-lookup"><span data-stu-id="1c5e1-105">\<securityTokenHandlers></span></span>  
<span data-ttu-id="1c5e1-106">\<add></span><span class="sxs-lookup"><span data-stu-id="1c5e1-106">\<add></span></span>  
<span data-ttu-id="1c5e1-107">\<userNameSecurityTokenHandlerRequirement></span><span class="sxs-lookup"><span data-stu-id="1c5e1-107">\<userNameSecurityTokenHandlerRequirement></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1c5e1-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1c5e1-108">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="1c5e1-109">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="1c5e1-109">Attributes and Elements</span></span>  
 <span data-ttu-id="1c5e1-110">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="1c5e1-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="1c5e1-111">Attributs</span><span class="sxs-lookup"><span data-stu-id="1c5e1-111">Attributes</span></span>  
  
|<span data-ttu-id="1c5e1-112">Attribut</span><span class="sxs-lookup"><span data-stu-id="1c5e1-112">Attribute</span></span>|<span data-ttu-id="1c5e1-113">Description</span><span class="sxs-lookup"><span data-stu-id="1c5e1-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="1c5e1-114">membershipProviderName</span><span class="sxs-lookup"><span data-stu-id="1c5e1-114">membershipProviderName</span></span>|<span data-ttu-id="1c5e1-115">Spécifie <xref:System.Web.Security.MembershipProvider> le qui doit être utilisé par le gestionnaire de jetons de sécurité.</span><span class="sxs-lookup"><span data-stu-id="1c5e1-115">Specifies the <xref:System.Web.Security.MembershipProvider> that should be used by the security token handler.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="1c5e1-116">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="1c5e1-116">Child Elements</span></span>  
 <span data-ttu-id="1c5e1-117">Aucun</span><span class="sxs-lookup"><span data-stu-id="1c5e1-117">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="1c5e1-118">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="1c5e1-118">Parent Elements</span></span>  
  
|<span data-ttu-id="1c5e1-119">Élément</span><span class="sxs-lookup"><span data-stu-id="1c5e1-119">Element</span></span>|<span data-ttu-id="1c5e1-120">Description</span><span class="sxs-lookup"><span data-stu-id="1c5e1-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="1c5e1-121">\<add></span><span class="sxs-lookup"><span data-stu-id="1c5e1-121">\<add></span></span>](add.md)|<span data-ttu-id="1c5e1-122">Ajoute le gestionnaire de jetons de sécurité spécifié à la collection de gestionnaires de jetons.</span><span class="sxs-lookup"><span data-stu-id="1c5e1-122">Adds the specified security token handler to the token handler collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1c5e1-123">Notes</span><span class="sxs-lookup"><span data-stu-id="1c5e1-123">Remarks</span></span>  
 <span data-ttu-id="1c5e1-124">L' `<userNameSecurityTokenHandlerRequirement>` élément définit la <xref:System.IdentityModel.Services.Tokens.MembershipUserNameSecurityTokenHandler.MembershipProvider%2A> propriété lorsqu’un <xref:System.IdentityModel.Services.Tokens.MembershipUserNameSecurityTokenHandler> objet est initialisé à partir de la configuration.</span><span class="sxs-lookup"><span data-stu-id="1c5e1-124">The `<userNameSecurityTokenHandlerRequirement>` element sets the <xref:System.IdentityModel.Services.Tokens.MembershipUserNameSecurityTokenHandler.MembershipProvider%2A> property when a <xref:System.IdentityModel.Services.Tokens.MembershipUserNameSecurityTokenHandler> object is initialized from configuration.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1c5e1-125">Exemple</span><span class="sxs-lookup"><span data-stu-id="1c5e1-125">Example</span></span>  
  
```xml  
<add type="System.IdentityModel.Services.Tokens.MembershipUserNameSecurityTokenHandler, System.IdentityModel.Services">  
    <userNameSecurityTokenHandlerRequirement membershipProviderName="AspNetSqlProvider/>  
</add>  
```
