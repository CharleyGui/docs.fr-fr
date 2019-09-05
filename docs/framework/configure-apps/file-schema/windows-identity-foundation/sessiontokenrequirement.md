---
title: <sessionTokenRequirement>
ms.date: 03/30/2017
ms.assetid: 496a1735-cbb7-49d5-a6aa-dd5550462073
author: BrucePerlerMS
ms.openlocfilehash: 968c48df9e92a1dfbfb6e248b06cf4f97cece8b4
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70251819"
---
# <a name="sessiontokenrequirement"></a><span data-ttu-id="76a78-101">\<sessionTokenRequirement></span><span class="sxs-lookup"><span data-stu-id="76a78-101">\<sessionTokenRequirement></span></span>
<span data-ttu-id="76a78-102">Fournit la configuration pour <xref:System.IdentityModel.Tokens.SessionSecurityTokenHandler> la classe ou les classes dérivées.</span><span class="sxs-lookup"><span data-stu-id="76a78-102">Provides configuration for the <xref:System.IdentityModel.Tokens.SessionSecurityTokenHandler> class or derived classes.</span></span>  
  
<span data-ttu-id="76a78-103">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="76a78-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="76a78-104">&nbsp;&nbsp;[ **\<System. identityModel >** ](system-identitymodel.md)</span><span class="sxs-lookup"><span data-stu-id="76a78-104">&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)</span></span>\
<span data-ttu-id="76a78-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<identityConfiguration >** ](identityconfiguration.md)</span><span class="sxs-lookup"><span data-stu-id="76a78-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)</span></span>\
<span data-ttu-id="76a78-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<securityTokenHandlers >** ](securitytokenhandlers.md)</span><span class="sxs-lookup"><span data-stu-id="76a78-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<securityTokenHandlers>**](securitytokenhandlers.md)</span></span>\
<span data-ttu-id="76a78-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<Ajouter >** ](add.md)</span><span class="sxs-lookup"><span data-stu-id="76a78-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<add>**](add.md)</span></span>\
<span data-ttu-id="76a78-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<sessionTokenRequirement >**</span><span class="sxs-lookup"><span data-stu-id="76a78-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<sessionTokenRequirement>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="76a78-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="76a78-109">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="76a78-110">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="76a78-110">Attributes and Elements</span></span>  
 <span data-ttu-id="76a78-111">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="76a78-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="76a78-112">Attributs</span><span class="sxs-lookup"><span data-stu-id="76a78-112">Attributes</span></span>  
  
|<span data-ttu-id="76a78-113">Attribut</span><span class="sxs-lookup"><span data-stu-id="76a78-113">Attribute</span></span>|<span data-ttu-id="76a78-114">Description</span><span class="sxs-lookup"><span data-stu-id="76a78-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="76a78-115">durée de vie</span><span class="sxs-lookup"><span data-stu-id="76a78-115">lifetime</span></span>|<span data-ttu-id="76a78-116">Spécifie la durée de vie des jetons de session.</span><span class="sxs-lookup"><span data-stu-id="76a78-116">Specifies the lifetime of session tokens.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="76a78-117">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="76a78-117">Child Elements</span></span>  
 <span data-ttu-id="76a78-118">Aucun</span><span class="sxs-lookup"><span data-stu-id="76a78-118">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="76a78-119">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="76a78-119">Parent Elements</span></span>  
  
|<span data-ttu-id="76a78-120">Élément</span><span class="sxs-lookup"><span data-stu-id="76a78-120">Element</span></span>|<span data-ttu-id="76a78-121">Description</span><span class="sxs-lookup"><span data-stu-id="76a78-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="76a78-122">\<add></span><span class="sxs-lookup"><span data-stu-id="76a78-122">\<add></span></span>](add.md)|<span data-ttu-id="76a78-123">Ajoute le gestionnaire de jetons de sécurité spécifié à la collection de gestionnaires de jetons.</span><span class="sxs-lookup"><span data-stu-id="76a78-123">Adds the specified security token handler to the token handler collection.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="76a78-124">Exemple</span><span class="sxs-lookup"><span data-stu-id="76a78-124">Example</span></span>  
  
```xml  
<add type="System.IdentityModel.Tokens.SessionSecurityTokenHandler, System.IdentityModel">           
    <sessionTokenRequirement lifetime="10:00" />  
</add>  
```
