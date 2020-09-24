---
title: <sessionTokenRequirement>
ms.date: 03/30/2017
ms.assetid: 496a1735-cbb7-49d5-a6aa-dd5550462073
author: BrucePerlerMS
ms.openlocfilehash: 4560c55cee5caf975e83ce9d4dc0b379ab905f8d
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91156847"
---
# \<sessionTokenRequirement>

<span data-ttu-id="0088b-101">Fournit la configuration pour la <xref:System.IdentityModel.Tokens.SessionSecurityTokenHandler> classe ou les classes dérivées.</span><span class="sxs-lookup"><span data-stu-id="0088b-101">Provides configuration for the <xref:System.IdentityModel.Tokens.SessionSecurityTokenHandler> class or derived classes.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<securityTokenHandlers>**](securitytokenhandlers.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<add>**](add.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<sessionTokenRequirement>**  
  
## <a name="syntax"></a><span data-ttu-id="0088b-102">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0088b-102">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="0088b-103">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="0088b-103">Attributes and Elements</span></span>  

 <span data-ttu-id="0088b-104">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="0088b-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="0088b-105">Attributs</span><span class="sxs-lookup"><span data-stu-id="0088b-105">Attributes</span></span>  
  
|<span data-ttu-id="0088b-106">Attribut</span><span class="sxs-lookup"><span data-stu-id="0088b-106">Attribute</span></span>|<span data-ttu-id="0088b-107">Description</span><span class="sxs-lookup"><span data-stu-id="0088b-107">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="0088b-108">lifetime</span><span class="sxs-lookup"><span data-stu-id="0088b-108">lifetime</span></span>|<span data-ttu-id="0088b-109">Spécifie la durée de vie des jetons de session.</span><span class="sxs-lookup"><span data-stu-id="0088b-109">Specifies the lifetime of session tokens.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="0088b-110">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="0088b-110">Child Elements</span></span>  

 <span data-ttu-id="0088b-111">None</span><span class="sxs-lookup"><span data-stu-id="0088b-111">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="0088b-112">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="0088b-112">Parent Elements</span></span>  
  
|<span data-ttu-id="0088b-113">Élément</span><span class="sxs-lookup"><span data-stu-id="0088b-113">Element</span></span>|<span data-ttu-id="0088b-114">Description</span><span class="sxs-lookup"><span data-stu-id="0088b-114">Description</span></span>|  
|-------------|-----------------|  
|[\<add>](add.md)|<span data-ttu-id="0088b-115">Ajoute le gestionnaire de jetons de sécurité spécifié à la collection de gestionnaires de jetons.</span><span class="sxs-lookup"><span data-stu-id="0088b-115">Adds the specified security token handler to the token handler collection.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="0088b-116">Exemple</span><span class="sxs-lookup"><span data-stu-id="0088b-116">Example</span></span>  
  
```xml  
<add type="System.IdentityModel.Tokens.SessionSecurityTokenHandler, System.IdentityModel">
    <sessionTokenRequirement lifetime="10:00" />  
</add>  
```
