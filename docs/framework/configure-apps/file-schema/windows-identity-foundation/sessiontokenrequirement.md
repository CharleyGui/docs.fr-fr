---
title: <sessionTokenRequirement>
ms.date: 03/30/2017
ms.assetid: 496a1735-cbb7-49d5-a6aa-dd5550462073
author: BrucePerlerMS
ms.openlocfilehash: ade55a5b26826633faf2e7ef7598a4071d613bbc
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/06/2020
ms.locfileid: "79152539"
---
# \<sessionTokenRequirement>
<span data-ttu-id="3a242-101">Fournit la configuration pour la <xref:System.IdentityModel.Tokens.SessionSecurityTokenHandler> classe ou les classes dérivées.</span><span class="sxs-lookup"><span data-stu-id="3a242-101">Provides configuration for the <xref:System.IdentityModel.Tokens.SessionSecurityTokenHandler> class or derived classes.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<securityTokenHandlers>**](securitytokenhandlers.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<add>**](add.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<sessionTokenRequirement>**  
  
## <a name="syntax"></a><span data-ttu-id="3a242-102">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3a242-102">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="3a242-103">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="3a242-103">Attributes and Elements</span></span>  
 <span data-ttu-id="3a242-104">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="3a242-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="3a242-105">Attributs</span><span class="sxs-lookup"><span data-stu-id="3a242-105">Attributes</span></span>  
  
|<span data-ttu-id="3a242-106">Attribut</span><span class="sxs-lookup"><span data-stu-id="3a242-106">Attribute</span></span>|<span data-ttu-id="3a242-107">Description</span><span class="sxs-lookup"><span data-stu-id="3a242-107">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="3a242-108">lifetime</span><span class="sxs-lookup"><span data-stu-id="3a242-108">lifetime</span></span>|<span data-ttu-id="3a242-109">Spécifie la durée de vie des jetons de session.</span><span class="sxs-lookup"><span data-stu-id="3a242-109">Specifies the lifetime of session tokens.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="3a242-110">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="3a242-110">Child Elements</span></span>  
 <span data-ttu-id="3a242-111">Aucune</span><span class="sxs-lookup"><span data-stu-id="3a242-111">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="3a242-112">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="3a242-112">Parent Elements</span></span>  
  
|<span data-ttu-id="3a242-113">Élément</span><span class="sxs-lookup"><span data-stu-id="3a242-113">Element</span></span>|<span data-ttu-id="3a242-114">Description</span><span class="sxs-lookup"><span data-stu-id="3a242-114">Description</span></span>|  
|-------------|-----------------|  
|[\<add>](add.md)|<span data-ttu-id="3a242-115">Ajoute le gestionnaire de jetons de sécurité spécifié à la collection de gestionnaires de jetons.</span><span class="sxs-lookup"><span data-stu-id="3a242-115">Adds the specified security token handler to the token handler collection.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="3a242-116">Exemple</span><span class="sxs-lookup"><span data-stu-id="3a242-116">Example</span></span>  
  
```xml  
<add type="System.IdentityModel.Tokens.SessionSecurityTokenHandler, System.IdentityModel">
    <sessionTokenRequirement lifetime="10:00" />  
</add>  
```
