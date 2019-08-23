---
title: <certificateValidator>
ms.date: 03/30/2017
ms.assetid: 86161897-c20f-4ad8-9d7f-050c247251bf
author: BrucePerlerMS
ms.openlocfilehash: c25f183679f41f51ffee4f482bfe7a64763647d9
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69941905"
---
# <a name="certificatevalidator"></a><span data-ttu-id="af1a0-101">\<certificateValidator></span><span class="sxs-lookup"><span data-stu-id="af1a0-101">\<certificateValidator></span></span>
<span data-ttu-id="af1a0-102">Spécifie un type personnalisé pour la validation du certificat.</span><span class="sxs-lookup"><span data-stu-id="af1a0-102">Specifies a custom type for certificate validation.</span></span> <span data-ttu-id="af1a0-103">Ce type est utilisé uniquement si l' `certificateValidationMode` attribut de l' [ \<élément certificateValidation >](certificatevalidation.md) a la valeur «Custom».</span><span class="sxs-lookup"><span data-stu-id="af1a0-103">This type is used only if the `certificateValidationMode` attribute of the [\<certificateValidation>](certificatevalidation.md) element is set to "Custom".</span></span>  
  
 <span data-ttu-id="af1a0-104">\<system.identityModel></span><span class="sxs-lookup"><span data-stu-id="af1a0-104">\<system.identityModel></span></span>  
<span data-ttu-id="af1a0-105">\<identityConfiguration></span><span class="sxs-lookup"><span data-stu-id="af1a0-105">\<identityConfiguration></span></span>  
<span data-ttu-id="af1a0-106">\<certificateValidation></span><span class="sxs-lookup"><span data-stu-id="af1a0-106">\<certificateValidation></span></span>  
<span data-ttu-id="af1a0-107">\<certificateValidator></span><span class="sxs-lookup"><span data-stu-id="af1a0-107">\<certificateValidator></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="af1a0-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="af1a0-108">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="af1a0-109">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="af1a0-109">Attributes and Elements</span></span>  
 <span data-ttu-id="af1a0-110">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="af1a0-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="af1a0-111">Attributs</span><span class="sxs-lookup"><span data-stu-id="af1a0-111">Attributes</span></span>  
  
|<span data-ttu-id="af1a0-112">Attribut</span><span class="sxs-lookup"><span data-stu-id="af1a0-112">Attribute</span></span>|<span data-ttu-id="af1a0-113">Description</span><span class="sxs-lookup"><span data-stu-id="af1a0-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="af1a0-114">type</span><span class="sxs-lookup"><span data-stu-id="af1a0-114">type</span></span>|<span data-ttu-id="af1a0-115">Spécifie un type personnalisé qui dérive de <xref:System.IdentityModel.Selectors.X509CertificateValidator> la classe.</span><span class="sxs-lookup"><span data-stu-id="af1a0-115">Specifies a custom type that derives from the <xref:System.IdentityModel.Selectors.X509CertificateValidator> class.</span></span> <span data-ttu-id="af1a0-116">Affectez `certificateValidationMode` la valeur "Custom" à l’attribut de l' [ \<élément certificateValidation >](certificatevalidation.md) pour utiliser ce type.</span><span class="sxs-lookup"><span data-stu-id="af1a0-116">Set the `certificateValidationMode` attribute of the [\<certificateValidation>](certificatevalidation.md) element to "Custom" to use this type.</span></span> <span data-ttu-id="af1a0-117">Pour plus d’informations sur la spécification de `type` l’attribut, consultez [références de types personnalisés](../windows-workflow-foundation/index.md).</span><span class="sxs-lookup"><span data-stu-id="af1a0-117">For more information about how to specify the `type` attribute, see [Custom Type References](../windows-workflow-foundation/index.md).</span></span> <span data-ttu-id="af1a0-118">facultatif.</span><span class="sxs-lookup"><span data-stu-id="af1a0-118">Optional.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="af1a0-119">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="af1a0-119">Child Elements</span></span>  
 <span data-ttu-id="af1a0-120">Aucun</span><span class="sxs-lookup"><span data-stu-id="af1a0-120">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="af1a0-121">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="af1a0-121">Parent Elements</span></span>  
  
|<span data-ttu-id="af1a0-122">Élément</span><span class="sxs-lookup"><span data-stu-id="af1a0-122">Element</span></span>|<span data-ttu-id="af1a0-123">Description</span><span class="sxs-lookup"><span data-stu-id="af1a0-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="af1a0-124">\<certificateValidation></span><span class="sxs-lookup"><span data-stu-id="af1a0-124">\<certificateValidation></span></span>](certificatevalidation.md)|<span data-ttu-id="af1a0-125">Contrôle les paramètres que les gestionnaires de jetons utilisent pour valider les certificats.</span><span class="sxs-lookup"><span data-stu-id="af1a0-125">Controls the settings that token handlers use to validate certificates.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="af1a0-126">Exemples</span><span class="sxs-lookup"><span data-stu-id="af1a0-126">Example</span></span>  
  
```xml  
<certificateValidation certificateValidationMode="Custom"  
                       revocationMode="Online"  
                       trustedStoreLocation="LocalMachine">  
    <certificateValidator type="MyNamespace.CustomValidator, MyAssembly" />    
</certificateValidation>        
```
