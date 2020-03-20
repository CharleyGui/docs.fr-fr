---
title: <sessionTokenRequirement>
ms.date: 03/30/2017
ms.assetid: 496a1735-cbb7-49d5-a6aa-dd5550462073
author: BrucePerlerMS
ms.openlocfilehash: ade55a5b26826633faf2e7ef7598a4071d613bbc
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79152539"
---
# <a name="sessiontokenrequirement"></a><span data-ttu-id="db28e-101">\<sessionTokenRequirement></span><span class="sxs-lookup"><span data-stu-id="db28e-101">\<sessionTokenRequirement></span></span>
<span data-ttu-id="db28e-102">Fournit la <xref:System.IdentityModel.Tokens.SessionSecurityTokenHandler> configuration pour la classe ou les classes dérivées.</span><span class="sxs-lookup"><span data-stu-id="db28e-102">Provides configuration for the <xref:System.IdentityModel.Tokens.SessionSecurityTokenHandler> class or derived classes.</span></span>  
  
<span data-ttu-id="db28e-103">[**\<configuration>**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="db28e-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="db28e-104">&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)</span><span class="sxs-lookup"><span data-stu-id="db28e-104">&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)</span></span>\
<span data-ttu-id="db28e-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<identitéConfiguration>**](identityconfiguration.md)</span><span class="sxs-lookup"><span data-stu-id="db28e-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)</span></span>\
<span data-ttu-id="db28e-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<sécuritéTokenHandlers>**](securitytokenhandlers.md)</span><span class="sxs-lookup"><span data-stu-id="db28e-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<securityTokenHandlers>**](securitytokenhandlers.md)</span></span>\
<span data-ttu-id="db28e-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<ajouter>**](add.md)</span><span class="sxs-lookup"><span data-stu-id="db28e-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<add>**](add.md)</span></span>\
<span data-ttu-id="db28e-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<sessionTokenRequirement>**</span><span class="sxs-lookup"><span data-stu-id="db28e-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<sessionTokenRequirement>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="db28e-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="db28e-109">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="db28e-110">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="db28e-110">Attributes and Elements</span></span>  
 <span data-ttu-id="db28e-111">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="db28e-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="db28e-112">Attributs</span><span class="sxs-lookup"><span data-stu-id="db28e-112">Attributes</span></span>  
  
|<span data-ttu-id="db28e-113">Attribut</span><span class="sxs-lookup"><span data-stu-id="db28e-113">Attribute</span></span>|<span data-ttu-id="db28e-114">Description</span><span class="sxs-lookup"><span data-stu-id="db28e-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="db28e-115">lifetime</span><span class="sxs-lookup"><span data-stu-id="db28e-115">lifetime</span></span>|<span data-ttu-id="db28e-116">Spécifie la durée de vie des jetons de session.</span><span class="sxs-lookup"><span data-stu-id="db28e-116">Specifies the lifetime of session tokens.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="db28e-117">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="db28e-117">Child Elements</span></span>  
 <span data-ttu-id="db28e-118">None</span><span class="sxs-lookup"><span data-stu-id="db28e-118">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="db28e-119">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="db28e-119">Parent Elements</span></span>  
  
|<span data-ttu-id="db28e-120">Élément</span><span class="sxs-lookup"><span data-stu-id="db28e-120">Element</span></span>|<span data-ttu-id="db28e-121">Description</span><span class="sxs-lookup"><span data-stu-id="db28e-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="db28e-122">\<ajouter></span><span class="sxs-lookup"><span data-stu-id="db28e-122">\<add></span></span>](add.md)|<span data-ttu-id="db28e-123">Ajoute le gestionnaire de jetons de sécurité spécifié à la collection de gestionnaires de jetons.</span><span class="sxs-lookup"><span data-stu-id="db28e-123">Adds the specified security token handler to the token handler collection.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="db28e-124"> Exemple</span><span class="sxs-lookup"><span data-stu-id="db28e-124">Example</span></span>  
  
```xml  
<add type="System.IdentityModel.Tokens.SessionSecurityTokenHandler, System.IdentityModel">
    <sessionTokenRequirement lifetime="10:00" />  
</add>  
```
