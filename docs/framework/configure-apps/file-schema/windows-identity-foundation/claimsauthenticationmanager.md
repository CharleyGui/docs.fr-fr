---
title: <claimsAuthenticationManager>
ms.date: 03/30/2017
ms.assetid: 6d30a450-6d13-4671-81a8-77e0204500c5
author: BrucePerlerMS
ms.openlocfilehash: a54fc2cea84bb9d08a9725d846fe38efd7b5475a
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/06/2020
ms.locfileid: "79152747"
---
# \<claimsAuthenticationManager>
<span data-ttu-id="01d60-101">Inscrit un gestionnaire d’authentification des revendications pour les revendications entrantes.</span><span class="sxs-lookup"><span data-stu-id="01d60-101">Registers a claims authentication manager for the incoming claims.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<claimsAuthenticationManager>**  
  
## <a name="syntax"></a><span data-ttu-id="01d60-102">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="01d60-102">Syntax</span></span>  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <claimsAuthenticationManager type=xs:string>  
      <optionalConfigurationElements />  
    </claimsAuthenticationManager>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="01d60-103">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="01d60-103">Attributes and Elements</span></span>  
 <span data-ttu-id="01d60-104">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="01d60-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="01d60-105">Attributs</span><span class="sxs-lookup"><span data-stu-id="01d60-105">Attributes</span></span>  
  
|<span data-ttu-id="01d60-106">Attribut</span><span class="sxs-lookup"><span data-stu-id="01d60-106">Attribute</span></span>|<span data-ttu-id="01d60-107">Description</span><span class="sxs-lookup"><span data-stu-id="01d60-107">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="01d60-108">type</span><span class="sxs-lookup"><span data-stu-id="01d60-108">type</span></span>|<span data-ttu-id="01d60-109">Spécifie un type personnalisé qui dérive de la <xref:System.Security.Claims.ClaimsAuthenticationManager> classe.</span><span class="sxs-lookup"><span data-stu-id="01d60-109">Specifies a custom type that derives from the <xref:System.Security.Claims.ClaimsAuthenticationManager> class.</span></span> <span data-ttu-id="01d60-110">Pour plus d’informations sur la spécification de l' `type` attribut, consultez [références de types personnalisés].</span><span class="sxs-lookup"><span data-stu-id="01d60-110">For more information about how to specify the `type` attribute, see [Custom Type References].</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="01d60-111">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="01d60-111">Child Elements</span></span>  
 <span data-ttu-id="01d60-112">S’il n’y a aucun `type` attribut, ou si l' `type` attribut fait référence <xref:System.Security.Claims.ClaimsAuthenticationManager> à la classe, l' `<claimsAuthenticationManager>` élément ne prend pas d’éléments enfants ; Toutefois, les classes dérivées de <xref:System.Security.Claims.ClaimsAuthenticationManager> peuvent définir des éléments de configuration enfants.</span><span class="sxs-lookup"><span data-stu-id="01d60-112">If there is no `type` attribute, or if the `type` attribute references the <xref:System.Security.Claims.ClaimsAuthenticationManager> class, the `<claimsAuthenticationManager>` element does not take child elements; however, classes derived from <xref:System.Security.Claims.ClaimsAuthenticationManager> can define child configuration elements.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="01d60-113">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="01d60-113">Parent Elements</span></span>  
  
|<span data-ttu-id="01d60-114">Élément</span><span class="sxs-lookup"><span data-stu-id="01d60-114">Element</span></span>|<span data-ttu-id="01d60-115">Description</span><span class="sxs-lookup"><span data-stu-id="01d60-115">Description</span></span>|  
|-------------|-----------------|  
|[\<identityConfiguration>](identityconfiguration.md)|<span data-ttu-id="01d60-116">Spécifie les paramètres d’identité au niveau du service.</span><span class="sxs-lookup"><span data-stu-id="01d60-116">Specifies service-level identity settings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="01d60-117">Remarques</span><span class="sxs-lookup"><span data-stu-id="01d60-117">Remarks</span></span>  
 <span data-ttu-id="01d60-118">Le comportement par défaut fourni par la <xref:System.Security.Claims.ClaimsAuthenticationManager> classe renvoie en écho les revendications entrantes.</span><span class="sxs-lookup"><span data-stu-id="01d60-118">The default behavior provided through the <xref:System.Security.Claims.ClaimsAuthenticationManager> class echoes the incoming claims.</span></span> <span data-ttu-id="01d60-119">Si aucun `type` attribut n’est spécifié ou si l' `type` attribut spécifie la <xref:System.Security.Claims.ClaimsAuthenticationManager> classe, l' `<claimsAuthenticationManager>` élément ne prend pas d’éléments enfants.</span><span class="sxs-lookup"><span data-stu-id="01d60-119">If no `type` attribute is specified or if the `type` attribute specifies the <xref:System.Security.Claims.ClaimsAuthenticationManager> class, the `<claimsAuthenticationManager>` element does not take child elements.</span></span> <span data-ttu-id="01d60-120">Vous pouvez spécifier l' `type` attribut pour inscrire un type dérivé de la <xref:System.Security.Claims.ClaimsAuthenticationManager> classe afin d’implémenter un comportement personnalisé.</span><span class="sxs-lookup"><span data-stu-id="01d60-120">You can specify the `type` attribute to register a type derived from the <xref:System.Security.Claims.ClaimsAuthenticationManager> class to implement custom behavior.</span></span> <span data-ttu-id="01d60-121">Les classes dérivées peuvent prendre en charge la configuration par le biais d’éléments enfants de l' `<claimsAuthenticationManager>` élément en substituant la <xref:System.Security.Claims.ClaimsAuthenticationManager.LoadCustomConfiguration%2A> méthode pour gérer ces éléments.</span><span class="sxs-lookup"><span data-stu-id="01d60-121">Derived classes can support configuration through child elements of the `<claimsAuthenticationManager>` element by overriding the <xref:System.Security.Claims.ClaimsAuthenticationManager.LoadCustomConfiguration%2A> method to handle these elements.</span></span> <span data-ttu-id="01d60-122">Le schéma défini pour les éléments enfants est jusqu’au concepteur de la classe.</span><span class="sxs-lookup"><span data-stu-id="01d60-122">The schema defined for the child elements is up to the designer of the class.</span></span>  
  
 <span data-ttu-id="01d60-123">L' `<claimsAuthenticationManager>` élément définit la <xref:System.IdentityModel.Configuration.IdentityConfiguration.ClaimsAuthenticationManager%2A?displayProperty=nameWithType> propriété.</span><span class="sxs-lookup"><span data-stu-id="01d60-123">The `<claimsAuthenticationManager>` element sets the <xref:System.IdentityModel.Configuration.IdentityConfiguration.ClaimsAuthenticationManager%2A?displayProperty=nameWithType> property.</span></span>  
  
## <a name="example"></a><span data-ttu-id="01d60-124">Exemple</span><span class="sxs-lookup"><span data-stu-id="01d60-124">Example</span></span>  
  
```xml  
<system.identityModel>  
    <identityConfiguration name="MyIdentity">  
      <claimsAuthenticationManager type="MyNamespace.CustomClaimsAuthenticationManager, MyAssembly"/>
    </identityConfiguration>  
</system.identityModel>  
```
