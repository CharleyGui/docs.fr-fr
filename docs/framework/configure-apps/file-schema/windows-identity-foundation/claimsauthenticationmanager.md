---
title: <claimsAuthenticationManager>
ms.date: 03/30/2017
ms.assetid: 6d30a450-6d13-4671-81a8-77e0204500c5
author: BrucePerlerMS
ms.openlocfilehash: c901daf4d442a206345301795c7a4bdc076329cd
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70252092"
---
# <a name="claimsauthenticationmanager"></a><span data-ttu-id="8269e-101">\<claimsAuthenticationManager></span><span class="sxs-lookup"><span data-stu-id="8269e-101">\<claimsAuthenticationManager></span></span>
<span data-ttu-id="8269e-102">Inscrit un gestionnaire d’authentification des revendications pour les revendications entrantes.</span><span class="sxs-lookup"><span data-stu-id="8269e-102">Registers a claims authentication manager for the incoming claims.</span></span>  
  
<span data-ttu-id="8269e-103">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="8269e-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="8269e-104">&nbsp;&nbsp;[ **\<System. identityModel >** ](system-identitymodel.md)</span><span class="sxs-lookup"><span data-stu-id="8269e-104">&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)</span></span>\
<span data-ttu-id="8269e-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<identityConfiguration >** ](identityconfiguration.md)</span><span class="sxs-lookup"><span data-stu-id="8269e-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)</span></span>\
<span data-ttu-id="8269e-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<claimsAuthenticationManager >**</span><span class="sxs-lookup"><span data-stu-id="8269e-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<claimsAuthenticationManager>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8269e-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8269e-107">Syntax</span></span>  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <claimsAuthenticationManager type=xs:string>  
      <optionalConfigurationElements />  
    </claimsAuthenticationManager>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="8269e-108">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="8269e-108">Attributes and Elements</span></span>  
 <span data-ttu-id="8269e-109">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="8269e-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="8269e-110">Attributs</span><span class="sxs-lookup"><span data-stu-id="8269e-110">Attributes</span></span>  
  
|<span data-ttu-id="8269e-111">Attribut</span><span class="sxs-lookup"><span data-stu-id="8269e-111">Attribute</span></span>|<span data-ttu-id="8269e-112">Description</span><span class="sxs-lookup"><span data-stu-id="8269e-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="8269e-113">type</span><span class="sxs-lookup"><span data-stu-id="8269e-113">type</span></span>|<span data-ttu-id="8269e-114">Spécifie un type personnalisé qui dérive de <xref:System.Security.Claims.ClaimsAuthenticationManager> la classe.</span><span class="sxs-lookup"><span data-stu-id="8269e-114">Specifies a custom type that derives from the <xref:System.Security.Claims.ClaimsAuthenticationManager> class.</span></span> <span data-ttu-id="8269e-115">Pour plus d’informations sur la spécification de `type` l’attribut, consultez [références de types personnalisés].</span><span class="sxs-lookup"><span data-stu-id="8269e-115">For more information about how to specify the `type` attribute, see [Custom Type References].</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="8269e-116">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="8269e-116">Child Elements</span></span>  
 <span data-ttu-id="8269e-117">S’il n’y `type` a aucun attribut, ou `type` si l’attribut <xref:System.Security.Claims.ClaimsAuthenticationManager> fait référence à `<claimsAuthenticationManager>` la classe, l’élément ne prend pas d’éléments enfants ; <xref:System.Security.Claims.ClaimsAuthenticationManager> Toutefois, les classes dérivées de peuvent définir des éléments de configuration enfants.</span><span class="sxs-lookup"><span data-stu-id="8269e-117">If there is no `type` attribute, or if the `type` attribute references the <xref:System.Security.Claims.ClaimsAuthenticationManager> class, the `<claimsAuthenticationManager>` element does not take child elements; however, classes derived from <xref:System.Security.Claims.ClaimsAuthenticationManager> can define child configuration elements.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="8269e-118">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="8269e-118">Parent Elements</span></span>  
  
|<span data-ttu-id="8269e-119">Élément</span><span class="sxs-lookup"><span data-stu-id="8269e-119">Element</span></span>|<span data-ttu-id="8269e-120">Description</span><span class="sxs-lookup"><span data-stu-id="8269e-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="8269e-121">\<identityConfiguration></span><span class="sxs-lookup"><span data-stu-id="8269e-121">\<identityConfiguration></span></span>](identityconfiguration.md)|<span data-ttu-id="8269e-122">Spécifie les paramètres d’identité au niveau du service.</span><span class="sxs-lookup"><span data-stu-id="8269e-122">Specifies service-level identity settings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8269e-123">Notes</span><span class="sxs-lookup"><span data-stu-id="8269e-123">Remarks</span></span>  
 <span data-ttu-id="8269e-124">Le comportement par défaut fourni par <xref:System.Security.Claims.ClaimsAuthenticationManager> la classe renvoie en écho les revendications entrantes.</span><span class="sxs-lookup"><span data-stu-id="8269e-124">The default behavior provided through the <xref:System.Security.Claims.ClaimsAuthenticationManager> class echoes the incoming claims.</span></span> <span data-ttu-id="8269e-125">Si aucun `type` attribut n’est spécifié ou si `type` l’attribut spécifie la <xref:System.Security.Claims.ClaimsAuthenticationManager> classe `<claimsAuthenticationManager>` , l’élément ne prend pas d’éléments enfants.</span><span class="sxs-lookup"><span data-stu-id="8269e-125">If no `type` attribute is specified or if the `type` attribute specifies the <xref:System.Security.Claims.ClaimsAuthenticationManager> class, the `<claimsAuthenticationManager>` element does not take child elements.</span></span> <span data-ttu-id="8269e-126">Vous pouvez spécifier l' `type` attribut pour inscrire un type dérivé de la <xref:System.Security.Claims.ClaimsAuthenticationManager> classe afin d’implémenter un comportement personnalisé.</span><span class="sxs-lookup"><span data-stu-id="8269e-126">You can specify the `type` attribute to register a type derived from the <xref:System.Security.Claims.ClaimsAuthenticationManager> class to implement custom behavior.</span></span> <span data-ttu-id="8269e-127">Les classes dérivées peuvent prendre en charge la configuration `<claimsAuthenticationManager>` par le biais d’éléments <xref:System.Security.Claims.ClaimsAuthenticationManager.LoadCustomConfiguration%2A> enfants de l’élément en substituant la méthode pour gérer ces éléments.</span><span class="sxs-lookup"><span data-stu-id="8269e-127">Derived classes can support configuration through child elements of the `<claimsAuthenticationManager>` element by overriding the <xref:System.Security.Claims.ClaimsAuthenticationManager.LoadCustomConfiguration%2A> method to handle these elements.</span></span> <span data-ttu-id="8269e-128">Le schéma défini pour les éléments enfants est jusqu’au concepteur de la classe.</span><span class="sxs-lookup"><span data-stu-id="8269e-128">The schema defined for the child elements is up to the designer of the class.</span></span>  
  
 <span data-ttu-id="8269e-129">L' `<claimsAuthenticationManager>` élément définit la <xref:System.IdentityModel.Configuration.IdentityConfiguration.ClaimsAuthenticationManager%2A?displayProperty=nameWithType> propriété.</span><span class="sxs-lookup"><span data-stu-id="8269e-129">The `<claimsAuthenticationManager>` element sets the <xref:System.IdentityModel.Configuration.IdentityConfiguration.ClaimsAuthenticationManager%2A?displayProperty=nameWithType> property.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8269e-130">Exemple</span><span class="sxs-lookup"><span data-stu-id="8269e-130">Example</span></span>  
  
```xml  
<system.identityModel>  
    <identityConfiguration name="MyIdentity">  
      <claimsAuthenticationManager type="MyNamespace.CustomClaimsAuthenticationManager, MyAssembly"/>          
    </identityConfiguration>  
</system.identityModel>  
```
