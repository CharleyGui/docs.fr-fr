---
title: <certificateValidator>
ms.date: 03/30/2017
ms.assetid: 86161897-c20f-4ad8-9d7f-050c247251bf
author: BrucePerlerMS
ms.openlocfilehash: 3f3d79d3567c1714a79423b7767ce3f454b9d52d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79152786"
---
# <a name="certificatevalidator"></a><span data-ttu-id="5b9b4-101">\<certificateValidator></span><span class="sxs-lookup"><span data-stu-id="5b9b4-101">\<certificateValidator></span></span>
<span data-ttu-id="5b9b4-102">Spécifie un type personnalisé pour la validation des certificats.</span><span class="sxs-lookup"><span data-stu-id="5b9b4-102">Specifies a custom type for certificate validation.</span></span> <span data-ttu-id="5b9b4-103">Ce type n’est `certificateValidationMode` utilisé que si l’attribut du [ \<certificatValidation>](certificatevalidation.md) élément est réglé sur "Custom".</span><span class="sxs-lookup"><span data-stu-id="5b9b4-103">This type is used only if the `certificateValidationMode` attribute of the [\<certificateValidation>](certificatevalidation.md) element is set to "Custom".</span></span>  
  
<span data-ttu-id="5b9b4-104">[**\<configuration>**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="5b9b4-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="5b9b4-105">&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)</span><span class="sxs-lookup"><span data-stu-id="5b9b4-105">&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)</span></span>\
<span data-ttu-id="5b9b4-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<identitéConfiguration>**](identityconfiguration.md)</span><span class="sxs-lookup"><span data-stu-id="5b9b4-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)</span></span>\
<span data-ttu-id="5b9b4-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<certificateValidation>**](certificatevalidation.md)</span><span class="sxs-lookup"><span data-stu-id="5b9b4-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<certificateValidation>**](certificatevalidation.md)</span></span>\
<span data-ttu-id="5b9b4-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<certificateValidator>**</span><span class="sxs-lookup"><span data-stu-id="5b9b4-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<certificateValidator>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5b9b4-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5b9b4-109">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="5b9b4-110">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="5b9b4-110">Attributes and Elements</span></span>  
 <span data-ttu-id="5b9b4-111">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="5b9b4-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="5b9b4-112">Attributs</span><span class="sxs-lookup"><span data-stu-id="5b9b4-112">Attributes</span></span>  
  
|<span data-ttu-id="5b9b4-113">Attribut</span><span class="sxs-lookup"><span data-stu-id="5b9b4-113">Attribute</span></span>|<span data-ttu-id="5b9b4-114">Description</span><span class="sxs-lookup"><span data-stu-id="5b9b4-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="5b9b4-115">type</span><span class="sxs-lookup"><span data-stu-id="5b9b4-115">type</span></span>|<span data-ttu-id="5b9b4-116">Spécifie un type personnalisé <xref:System.IdentityModel.Selectors.X509CertificateValidator> qui dérive de la classe.</span><span class="sxs-lookup"><span data-stu-id="5b9b4-116">Specifies a custom type that derives from the <xref:System.IdentityModel.Selectors.X509CertificateValidator> class.</span></span> <span data-ttu-id="5b9b4-117">Définissez `certificateValidationMode` l’attribut du [ \<certificatValidation>](certificatevalidation.md) élément à "Custom" pour utiliser ce type.</span><span class="sxs-lookup"><span data-stu-id="5b9b4-117">Set the `certificateValidationMode` attribute of the [\<certificateValidation>](certificatevalidation.md) element to "Custom" to use this type.</span></span> <span data-ttu-id="5b9b4-118">Pour plus d’informations `type` sur la façon de spécifier l’attribut, voir [Références de type personnalisé](../windows-workflow-foundation/index.md).</span><span class="sxs-lookup"><span data-stu-id="5b9b4-118">For more information about how to specify the `type` attribute, see [Custom Type References](../windows-workflow-foundation/index.md).</span></span> <span data-ttu-id="5b9b4-119">facultatif.</span><span class="sxs-lookup"><span data-stu-id="5b9b4-119">Optional.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="5b9b4-120">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="5b9b4-120">Child Elements</span></span>  
 <span data-ttu-id="5b9b4-121">None</span><span class="sxs-lookup"><span data-stu-id="5b9b4-121">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="5b9b4-122">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="5b9b4-122">Parent Elements</span></span>  
  
|<span data-ttu-id="5b9b4-123">Élément</span><span class="sxs-lookup"><span data-stu-id="5b9b4-123">Element</span></span>|<span data-ttu-id="5b9b4-124">Description</span><span class="sxs-lookup"><span data-stu-id="5b9b4-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="5b9b4-125">\<certificateValidation></span><span class="sxs-lookup"><span data-stu-id="5b9b4-125">\<certificateValidation></span></span>](certificatevalidation.md)|<span data-ttu-id="5b9b4-126">Contrôle les paramètres utilisés par les gestionnaires de jetons pour valider les certificats.</span><span class="sxs-lookup"><span data-stu-id="5b9b4-126">Controls the settings that token handlers use to validate certificates.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="5b9b4-127"> Exemple</span><span class="sxs-lookup"><span data-stu-id="5b9b4-127">Example</span></span>  
  
```xml  
<certificateValidation certificateValidationMode="Custom"  
                       revocationMode="Online"  
                       trustedStoreLocation="LocalMachine">  
    <certificateValidator type="MyNamespace.CustomValidator, MyAssembly" />
</certificateValidation>
```
