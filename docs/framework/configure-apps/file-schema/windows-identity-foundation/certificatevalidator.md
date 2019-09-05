---
title: <certificateValidator>
ms.date: 03/30/2017
ms.assetid: 86161897-c20f-4ad8-9d7f-050c247251bf
author: BrucePerlerMS
ms.openlocfilehash: 30f81dd5948a7d366c1116cffd347c85a396f5ae
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70252126"
---
# <a name="certificatevalidator"></a><span data-ttu-id="20de9-101">\<certificateValidator></span><span class="sxs-lookup"><span data-stu-id="20de9-101">\<certificateValidator></span></span>
<span data-ttu-id="20de9-102">Spécifie un type personnalisé pour la validation du certificat.</span><span class="sxs-lookup"><span data-stu-id="20de9-102">Specifies a custom type for certificate validation.</span></span> <span data-ttu-id="20de9-103">Ce type est utilisé uniquement si l' `certificateValidationMode` attribut de l' [ \<élément certificateValidation >](certificatevalidation.md) a la valeur « Custom ».</span><span class="sxs-lookup"><span data-stu-id="20de9-103">This type is used only if the `certificateValidationMode` attribute of the [\<certificateValidation>](certificatevalidation.md) element is set to "Custom".</span></span>  
  
<span data-ttu-id="20de9-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="20de9-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="20de9-105">&nbsp;&nbsp;[ **\<System. identityModel >** ](system-identitymodel.md)</span><span class="sxs-lookup"><span data-stu-id="20de9-105">&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)</span></span>\
<span data-ttu-id="20de9-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<identityConfiguration >** ](identityconfiguration.md)</span><span class="sxs-lookup"><span data-stu-id="20de9-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)</span></span>\
<span data-ttu-id="20de9-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<certificateValidation >** ](certificatevalidation.md)</span><span class="sxs-lookup"><span data-stu-id="20de9-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<certificateValidation>**](certificatevalidation.md)</span></span>\
<span data-ttu-id="20de9-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<certificateValidator >**</span><span class="sxs-lookup"><span data-stu-id="20de9-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<certificateValidator>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="20de9-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="20de9-109">Syntax</span></span>  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <certificateValidation>  
      <certificateValidator type=xs:string>  
      </certificateValidator>  
    </certificateValidation>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="20de9-110">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="20de9-110">Attributes and Elements</span></span>  
 <span data-ttu-id="20de9-111">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="20de9-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="20de9-112">Attributs</span><span class="sxs-lookup"><span data-stu-id="20de9-112">Attributes</span></span>  
  
|<span data-ttu-id="20de9-113">Attribut</span><span class="sxs-lookup"><span data-stu-id="20de9-113">Attribute</span></span>|<span data-ttu-id="20de9-114">Description</span><span class="sxs-lookup"><span data-stu-id="20de9-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="20de9-115">type</span><span class="sxs-lookup"><span data-stu-id="20de9-115">type</span></span>|<span data-ttu-id="20de9-116">Spécifie un type personnalisé qui dérive de <xref:System.IdentityModel.Selectors.X509CertificateValidator> la classe.</span><span class="sxs-lookup"><span data-stu-id="20de9-116">Specifies a custom type that derives from the <xref:System.IdentityModel.Selectors.X509CertificateValidator> class.</span></span> <span data-ttu-id="20de9-117">Affectez `certificateValidationMode` la valeur "Custom" à l’attribut de l' [ \<élément certificateValidation >](certificatevalidation.md) pour utiliser ce type.</span><span class="sxs-lookup"><span data-stu-id="20de9-117">Set the `certificateValidationMode` attribute of the [\<certificateValidation>](certificatevalidation.md) element to "Custom" to use this type.</span></span> <span data-ttu-id="20de9-118">Pour plus d’informations sur la spécification de `type` l’attribut, consultez [références de types personnalisés](../windows-workflow-foundation/index.md).</span><span class="sxs-lookup"><span data-stu-id="20de9-118">For more information about how to specify the `type` attribute, see [Custom Type References](../windows-workflow-foundation/index.md).</span></span> <span data-ttu-id="20de9-119">facultatif.</span><span class="sxs-lookup"><span data-stu-id="20de9-119">Optional.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="20de9-120">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="20de9-120">Child Elements</span></span>  
 <span data-ttu-id="20de9-121">Aucun</span><span class="sxs-lookup"><span data-stu-id="20de9-121">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="20de9-122">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="20de9-122">Parent Elements</span></span>  
  
|<span data-ttu-id="20de9-123">Élément</span><span class="sxs-lookup"><span data-stu-id="20de9-123">Element</span></span>|<span data-ttu-id="20de9-124">Description</span><span class="sxs-lookup"><span data-stu-id="20de9-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="20de9-125">\<certificateValidation></span><span class="sxs-lookup"><span data-stu-id="20de9-125">\<certificateValidation></span></span>](certificatevalidation.md)|<span data-ttu-id="20de9-126">Contrôle les paramètres que les gestionnaires de jetons utilisent pour valider les certificats.</span><span class="sxs-lookup"><span data-stu-id="20de9-126">Controls the settings that token handlers use to validate certificates.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="20de9-127">Exemple</span><span class="sxs-lookup"><span data-stu-id="20de9-127">Example</span></span>  
  
```xml  
<certificateValidation certificateValidationMode="Custom"  
                       revocationMode="Online"  
                       trustedStoreLocation="LocalMachine">  
    <certificateValidator type="MyNamespace.CustomValidator, MyAssembly" />    
</certificateValidation>        
```
