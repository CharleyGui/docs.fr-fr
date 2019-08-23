---
title: <sessionTokenRequirement>
ms.date: 03/30/2017
ms.assetid: 496a1735-cbb7-49d5-a6aa-dd5550462073
author: BrucePerlerMS
ms.openlocfilehash: 254d34149892abeaf31b9227f7567eb0a66ec0b6
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69943678"
---
# <a name="sessiontokenrequirement"></a><span data-ttu-id="77dc5-101">\<sessionTokenRequirement></span><span class="sxs-lookup"><span data-stu-id="77dc5-101">\<sessionTokenRequirement></span></span>
<span data-ttu-id="77dc5-102">Fournit la configuration pour <xref:System.IdentityModel.Tokens.SessionSecurityTokenHandler> la classe ou les classes dérivées.</span><span class="sxs-lookup"><span data-stu-id="77dc5-102">Provides configuration for the <xref:System.IdentityModel.Tokens.SessionSecurityTokenHandler> class or derived classes.</span></span>  
  
 <span data-ttu-id="77dc5-103">\<system.identityModel></span><span class="sxs-lookup"><span data-stu-id="77dc5-103">\<system.identityModel></span></span>  
<span data-ttu-id="77dc5-104">\<identityConfiguration></span><span class="sxs-lookup"><span data-stu-id="77dc5-104">\<identityConfiguration></span></span>  
<span data-ttu-id="77dc5-105">\<securityTokenHandlers></span><span class="sxs-lookup"><span data-stu-id="77dc5-105">\<securityTokenHandlers></span></span>  
<span data-ttu-id="77dc5-106">\<add></span><span class="sxs-lookup"><span data-stu-id="77dc5-106">\<add></span></span>  
<span data-ttu-id="77dc5-107">\<sessionTokenRequirement></span><span class="sxs-lookup"><span data-stu-id="77dc5-107">\<sessionTokenRequirement></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="77dc5-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="77dc5-108">Syntax</span></span>  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <securityTokenHandlers>  
      <add type="System.IdentityModel.Tokens.SessionSecurityTokenHandler, System.IdentityModel">  
        <sessionTokenRequirement lifetime=TimeSpan >  
        </sessionTokenRequirement>  
      </add>  
    </securityTokenHandlers>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="77dc5-109">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="77dc5-109">Attributes and Elements</span></span>  
 <span data-ttu-id="77dc5-110">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="77dc5-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="77dc5-111">Attributs</span><span class="sxs-lookup"><span data-stu-id="77dc5-111">Attributes</span></span>  
  
|<span data-ttu-id="77dc5-112">Attribut</span><span class="sxs-lookup"><span data-stu-id="77dc5-112">Attribute</span></span>|<span data-ttu-id="77dc5-113">Description</span><span class="sxs-lookup"><span data-stu-id="77dc5-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="77dc5-114">durée de vie</span><span class="sxs-lookup"><span data-stu-id="77dc5-114">lifetime</span></span>|<span data-ttu-id="77dc5-115">Spécifie la durée de vie des jetons de session.</span><span class="sxs-lookup"><span data-stu-id="77dc5-115">Specifies the lifetime of session tokens.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="77dc5-116">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="77dc5-116">Child Elements</span></span>  
 <span data-ttu-id="77dc5-117">Aucun</span><span class="sxs-lookup"><span data-stu-id="77dc5-117">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="77dc5-118">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="77dc5-118">Parent Elements</span></span>  
  
|<span data-ttu-id="77dc5-119">Élément</span><span class="sxs-lookup"><span data-stu-id="77dc5-119">Element</span></span>|<span data-ttu-id="77dc5-120">Description</span><span class="sxs-lookup"><span data-stu-id="77dc5-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="77dc5-121">\<add></span><span class="sxs-lookup"><span data-stu-id="77dc5-121">\<add></span></span>](add.md)|<span data-ttu-id="77dc5-122">Ajoute le gestionnaire de jetons de sécurité spécifié à la collection de gestionnaires de jetons.</span><span class="sxs-lookup"><span data-stu-id="77dc5-122">Adds the specified security token handler to the token handler collection.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="77dc5-123">Exemple</span><span class="sxs-lookup"><span data-stu-id="77dc5-123">Example</span></span>  
  
```xml  
<add type="System.IdentityModel.Tokens.SessionSecurityTokenHandler, System.IdentityModel">           
    <sessionTokenRequirement lifetime="10:00" />  
</add>  
```
