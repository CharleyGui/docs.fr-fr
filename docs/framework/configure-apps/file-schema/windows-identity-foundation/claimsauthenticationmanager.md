---
title: <claimsAuthenticationManager>
ms.date: 03/30/2017
ms.assetid: 6d30a450-6d13-4671-81a8-77e0204500c5
author: BrucePerlerMS
ms.openlocfilehash: 3602a4805e86833ba6070d801cef6758aaee8a5c
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69941829"
---
# <a name="claimsauthenticationmanager"></a><span data-ttu-id="3d284-101">\<claimsAuthenticationManager></span><span class="sxs-lookup"><span data-stu-id="3d284-101">\<claimsAuthenticationManager></span></span>
<span data-ttu-id="3d284-102">Inscrit un gestionnaire d’authentification des revendications pour les revendications entrantes.</span><span class="sxs-lookup"><span data-stu-id="3d284-102">Registers a claims authentication manager for the incoming claims.</span></span>  
  
 <span data-ttu-id="3d284-103">\<system.identityModel></span><span class="sxs-lookup"><span data-stu-id="3d284-103">\<system.identityModel></span></span>  
<span data-ttu-id="3d284-104">\<identityConfiguration></span><span class="sxs-lookup"><span data-stu-id="3d284-104">\<identityConfiguration></span></span>  
<span data-ttu-id="3d284-105">\<claimsAuthenticationManager></span><span class="sxs-lookup"><span data-stu-id="3d284-105">\<claimsAuthenticationManager></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3d284-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3d284-106">Syntax</span></span>  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <claimsAuthenticationManager type=xs:string>  
      <optionalConfigurationElements />  
    </claimsAuthenticationManager>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="3d284-107">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="3d284-107">Attributes and Elements</span></span>  
 <span data-ttu-id="3d284-108">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="3d284-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="3d284-109">Attributs</span><span class="sxs-lookup"><span data-stu-id="3d284-109">Attributes</span></span>  
  
|<span data-ttu-id="3d284-110">Attribut</span><span class="sxs-lookup"><span data-stu-id="3d284-110">Attribute</span></span>|<span data-ttu-id="3d284-111">Description</span><span class="sxs-lookup"><span data-stu-id="3d284-111">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="3d284-112">type</span><span class="sxs-lookup"><span data-stu-id="3d284-112">type</span></span>|<span data-ttu-id="3d284-113">Spécifie un type personnalisé qui dérive de <xref:System.Security.Claims.ClaimsAuthenticationManager> la classe.</span><span class="sxs-lookup"><span data-stu-id="3d284-113">Specifies a custom type that derives from the <xref:System.Security.Claims.ClaimsAuthenticationManager> class.</span></span> <span data-ttu-id="3d284-114">Pour plus d’informations sur la spécification de `type` l’attribut, consultez [références de types personnalisés].</span><span class="sxs-lookup"><span data-stu-id="3d284-114">For more information about how to specify the `type` attribute, see [Custom Type References].</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="3d284-115">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="3d284-115">Child Elements</span></span>  
 <span data-ttu-id="3d284-116">S’il n’y `type` a aucun attribut, ou `type` si l’attribut <xref:System.Security.Claims.ClaimsAuthenticationManager> fait référence à `<claimsAuthenticationManager>` la classe, l’élément ne prend pas d’éléments enfants; <xref:System.Security.Claims.ClaimsAuthenticationManager> Toutefois, les classes dérivées de peuvent définir des éléments de configuration enfants.</span><span class="sxs-lookup"><span data-stu-id="3d284-116">If there is no `type` attribute, or if the `type` attribute references the <xref:System.Security.Claims.ClaimsAuthenticationManager> class, the `<claimsAuthenticationManager>` element does not take child elements; however, classes derived from <xref:System.Security.Claims.ClaimsAuthenticationManager> can define child configuration elements.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="3d284-117">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="3d284-117">Parent Elements</span></span>  
  
|<span data-ttu-id="3d284-118">Élément</span><span class="sxs-lookup"><span data-stu-id="3d284-118">Element</span></span>|<span data-ttu-id="3d284-119">Description</span><span class="sxs-lookup"><span data-stu-id="3d284-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="3d284-120">\<identityConfiguration></span><span class="sxs-lookup"><span data-stu-id="3d284-120">\<identityConfiguration></span></span>](identityconfiguration.md)|<span data-ttu-id="3d284-121">Spécifie les paramètres d’identité au niveau du service.</span><span class="sxs-lookup"><span data-stu-id="3d284-121">Specifies service-level identity settings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3d284-122">Notes</span><span class="sxs-lookup"><span data-stu-id="3d284-122">Remarks</span></span>  
 <span data-ttu-id="3d284-123">Le comportement par défaut fourni par <xref:System.Security.Claims.ClaimsAuthenticationManager> la classe renvoie en écho les revendications entrantes.</span><span class="sxs-lookup"><span data-stu-id="3d284-123">The default behavior provided through the <xref:System.Security.Claims.ClaimsAuthenticationManager> class echoes the incoming claims.</span></span> <span data-ttu-id="3d284-124">Si aucun `type` attribut n’est spécifié ou si `type` l’attribut spécifie la <xref:System.Security.Claims.ClaimsAuthenticationManager> classe `<claimsAuthenticationManager>` , l’élément ne prend pas d’éléments enfants.</span><span class="sxs-lookup"><span data-stu-id="3d284-124">If no `type` attribute is specified or if the `type` attribute specifies the <xref:System.Security.Claims.ClaimsAuthenticationManager> class, the `<claimsAuthenticationManager>` element does not take child elements.</span></span> <span data-ttu-id="3d284-125">Vous pouvez spécifier l' `type` attribut pour inscrire un type dérivé de la <xref:System.Security.Claims.ClaimsAuthenticationManager> classe afin d’implémenter un comportement personnalisé.</span><span class="sxs-lookup"><span data-stu-id="3d284-125">You can specify the `type` attribute to register a type derived from the <xref:System.Security.Claims.ClaimsAuthenticationManager> class to implement custom behavior.</span></span> <span data-ttu-id="3d284-126">Les classes dérivées peuvent prendre en charge la configuration `<claimsAuthenticationManager>` par le biais d’éléments <xref:System.Security.Claims.ClaimsAuthenticationManager.LoadCustomConfiguration%2A> enfants de l’élément en substituant la méthode pour gérer ces éléments.</span><span class="sxs-lookup"><span data-stu-id="3d284-126">Derived classes can support configuration through child elements of the `<claimsAuthenticationManager>` element by overriding the <xref:System.Security.Claims.ClaimsAuthenticationManager.LoadCustomConfiguration%2A> method to handle these elements.</span></span> <span data-ttu-id="3d284-127">Le schéma défini pour les éléments enfants est jusqu’au concepteur de la classe.</span><span class="sxs-lookup"><span data-stu-id="3d284-127">The schema defined for the child elements is up to the designer of the class.</span></span>  
  
 <span data-ttu-id="3d284-128">L' `<claimsAuthenticationManager>` élément définit la <xref:System.IdentityModel.Configuration.IdentityConfiguration.ClaimsAuthenticationManager%2A?displayProperty=nameWithType> propriété.</span><span class="sxs-lookup"><span data-stu-id="3d284-128">The `<claimsAuthenticationManager>` element sets the <xref:System.IdentityModel.Configuration.IdentityConfiguration.ClaimsAuthenticationManager%2A?displayProperty=nameWithType> property.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3d284-129">Exemple</span><span class="sxs-lookup"><span data-stu-id="3d284-129">Example</span></span>  
  
```xml  
<system.identityModel>  
    <identityConfiguration name="MyIdentity">  
      <claimsAuthenticationManager type="MyNamespace.CustomClaimsAuthenticationManager, MyAssembly"/>          
    </identityConfiguration>  
</system.identityModel>  
```
