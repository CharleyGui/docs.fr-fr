---
title: <claimsAuthenticationManager>
ms.date: 03/30/2017
ms.assetid: 6d30a450-6d13-4671-81a8-77e0204500c5
author: BrucePerlerMS
ms.openlocfilehash: a54fc2cea84bb9d08a9725d846fe38efd7b5475a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79152747"
---
# <a name="claimsauthenticationmanager"></a><span data-ttu-id="4c6d0-101">\<revendicationsAuthenticationManager></span><span class="sxs-lookup"><span data-stu-id="4c6d0-101">\<claimsAuthenticationManager></span></span>
<span data-ttu-id="4c6d0-102">Enregistre un gestionnaire d’authentification des réclamations pour les réclamations entrantes.</span><span class="sxs-lookup"><span data-stu-id="4c6d0-102">Registers a claims authentication manager for the incoming claims.</span></span>  
  
<span data-ttu-id="4c6d0-103">[**\<configuration>**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="4c6d0-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="4c6d0-104">&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)</span><span class="sxs-lookup"><span data-stu-id="4c6d0-104">&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)</span></span>\
<span data-ttu-id="4c6d0-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<identitéConfiguration>**](identityconfiguration.md)</span><span class="sxs-lookup"><span data-stu-id="4c6d0-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)</span></span>\
<span data-ttu-id="4c6d0-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<revendicationsAuthenticationManager>**</span><span class="sxs-lookup"><span data-stu-id="4c6d0-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<claimsAuthenticationManager>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4c6d0-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4c6d0-107">Syntax</span></span>  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <claimsAuthenticationManager type=xs:string>  
      <optionalConfigurationElements />  
    </claimsAuthenticationManager>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="4c6d0-108">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="4c6d0-108">Attributes and Elements</span></span>  
 <span data-ttu-id="4c6d0-109">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="4c6d0-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="4c6d0-110">Attributs</span><span class="sxs-lookup"><span data-stu-id="4c6d0-110">Attributes</span></span>  
  
|<span data-ttu-id="4c6d0-111">Attribut</span><span class="sxs-lookup"><span data-stu-id="4c6d0-111">Attribute</span></span>|<span data-ttu-id="4c6d0-112">Description</span><span class="sxs-lookup"><span data-stu-id="4c6d0-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="4c6d0-113">type</span><span class="sxs-lookup"><span data-stu-id="4c6d0-113">type</span></span>|<span data-ttu-id="4c6d0-114">Spécifie un type personnalisé <xref:System.Security.Claims.ClaimsAuthenticationManager> qui dérive de la classe.</span><span class="sxs-lookup"><span data-stu-id="4c6d0-114">Specifies a custom type that derives from the <xref:System.Security.Claims.ClaimsAuthenticationManager> class.</span></span> <span data-ttu-id="4c6d0-115">Pour plus d’informations `type` sur la façon de spécifier l’attribut, voir [Références de type personnalisé].</span><span class="sxs-lookup"><span data-stu-id="4c6d0-115">For more information about how to specify the `type` attribute, see [Custom Type References].</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="4c6d0-116">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="4c6d0-116">Child Elements</span></span>  
 <span data-ttu-id="4c6d0-117">S’il `type` n’y a `type` pas <xref:System.Security.Claims.ClaimsAuthenticationManager> d’attribut, ou si l’attribut fait référence à la classe, l’élément `<claimsAuthenticationManager>` ne prend pas d’éléments pour enfants; cependant, les <xref:System.Security.Claims.ClaimsAuthenticationManager> classes dérivées peuvent définir des éléments de configuration de l’enfant.</span><span class="sxs-lookup"><span data-stu-id="4c6d0-117">If there is no `type` attribute, or if the `type` attribute references the <xref:System.Security.Claims.ClaimsAuthenticationManager> class, the `<claimsAuthenticationManager>` element does not take child elements; however, classes derived from <xref:System.Security.Claims.ClaimsAuthenticationManager> can define child configuration elements.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="4c6d0-118">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="4c6d0-118">Parent Elements</span></span>  
  
|<span data-ttu-id="4c6d0-119">Élément</span><span class="sxs-lookup"><span data-stu-id="4c6d0-119">Element</span></span>|<span data-ttu-id="4c6d0-120">Description</span><span class="sxs-lookup"><span data-stu-id="4c6d0-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="4c6d0-121">\<identitéConfiguration></span><span class="sxs-lookup"><span data-stu-id="4c6d0-121">\<identityConfiguration></span></span>](identityconfiguration.md)|<span data-ttu-id="4c6d0-122">Spécifie les paramètres d’identité au niveau du service.</span><span class="sxs-lookup"><span data-stu-id="4c6d0-122">Specifies service-level identity settings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4c6d0-123">Notes </span><span class="sxs-lookup"><span data-stu-id="4c6d0-123">Remarks</span></span>  
 <span data-ttu-id="4c6d0-124">Le comportement par <xref:System.Security.Claims.ClaimsAuthenticationManager> défaut fourni par la classe fait écho aux réclamations entrantes.</span><span class="sxs-lookup"><span data-stu-id="4c6d0-124">The default behavior provided through the <xref:System.Security.Claims.ClaimsAuthenticationManager> class echoes the incoming claims.</span></span> <span data-ttu-id="4c6d0-125">Si `type` aucun attribut n’est spécifié ou si l’attribut `type` spécifie la <xref:System.Security.Claims.ClaimsAuthenticationManager> classe, l’élément `<claimsAuthenticationManager>` ne prend pas d’éléments pour enfants.</span><span class="sxs-lookup"><span data-stu-id="4c6d0-125">If no `type` attribute is specified or if the `type` attribute specifies the <xref:System.Security.Claims.ClaimsAuthenticationManager> class, the `<claimsAuthenticationManager>` element does not take child elements.</span></span> <span data-ttu-id="4c6d0-126">Vous pouvez `type` spécifier l’attribut <xref:System.Security.Claims.ClaimsAuthenticationManager> pour enregistrer un type dérivé de la classe pour implémenter un comportement personnalisé.</span><span class="sxs-lookup"><span data-stu-id="4c6d0-126">You can specify the `type` attribute to register a type derived from the <xref:System.Security.Claims.ClaimsAuthenticationManager> class to implement custom behavior.</span></span> <span data-ttu-id="4c6d0-127">Les classes dérivées peuvent soutenir `<claimsAuthenticationManager>` la configuration par <xref:System.Security.Claims.ClaimsAuthenticationManager.LoadCustomConfiguration%2A> des éléments enfantaux de l’élément en l’emporteant sur la méthode de manutention de ces éléments.</span><span class="sxs-lookup"><span data-stu-id="4c6d0-127">Derived classes can support configuration through child elements of the `<claimsAuthenticationManager>` element by overriding the <xref:System.Security.Claims.ClaimsAuthenticationManager.LoadCustomConfiguration%2A> method to handle these elements.</span></span> <span data-ttu-id="4c6d0-128">Le schéma défini pour les éléments de l’enfant est à la designer de la classe.</span><span class="sxs-lookup"><span data-stu-id="4c6d0-128">The schema defined for the child elements is up to the designer of the class.</span></span>  
  
 <span data-ttu-id="4c6d0-129">L’élément `<claimsAuthenticationManager>` <xref:System.IdentityModel.Configuration.IdentityConfiguration.ClaimsAuthenticationManager%2A?displayProperty=nameWithType> définit la propriété.</span><span class="sxs-lookup"><span data-stu-id="4c6d0-129">The `<claimsAuthenticationManager>` element sets the <xref:System.IdentityModel.Configuration.IdentityConfiguration.ClaimsAuthenticationManager%2A?displayProperty=nameWithType> property.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4c6d0-130"> Exemple</span><span class="sxs-lookup"><span data-stu-id="4c6d0-130">Example</span></span>  
  
```xml  
<system.identityModel>  
    <identityConfiguration name="MyIdentity">  
      <claimsAuthenticationManager type="MyNamespace.CustomClaimsAuthenticationManager, MyAssembly"/>
    </identityConfiguration>  
</system.identityModel>  
```
