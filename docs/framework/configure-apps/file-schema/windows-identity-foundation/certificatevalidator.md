---
title: <certificateValidator>
ms.date: 03/30/2017
ms.assetid: 86161897-c20f-4ad8-9d7f-050c247251bf
author: BrucePerlerMS
ms.openlocfilehash: 8476600769b6099bb885566de4c908c78a2dbbda
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91201371"
---
# \<certificateValidator>

<span data-ttu-id="fbe7e-101">Spécifie un type personnalisé pour la validation du certificat.</span><span class="sxs-lookup"><span data-stu-id="fbe7e-101">Specifies a custom type for certificate validation.</span></span> <span data-ttu-id="fbe7e-102">Ce type est utilisé uniquement si l' `certificateValidationMode` attribut de l' [\<certificateValidation>](certificatevalidation.md) élément a la valeur « Custom ».</span><span class="sxs-lookup"><span data-stu-id="fbe7e-102">This type is used only if the `certificateValidationMode` attribute of the [\<certificateValidation>](certificatevalidation.md) element is set to "Custom".</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<certificateValidation>**](certificatevalidation.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<certificateValidator>**  
  
## <a name="syntax"></a><span data-ttu-id="fbe7e-103">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="fbe7e-103">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="fbe7e-104">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="fbe7e-104">Attributes and Elements</span></span>  

 <span data-ttu-id="fbe7e-105">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="fbe7e-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="fbe7e-106">Attributs</span><span class="sxs-lookup"><span data-stu-id="fbe7e-106">Attributes</span></span>  
  
|<span data-ttu-id="fbe7e-107">Attribut</span><span class="sxs-lookup"><span data-stu-id="fbe7e-107">Attribute</span></span>|<span data-ttu-id="fbe7e-108">Description</span><span class="sxs-lookup"><span data-stu-id="fbe7e-108">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="fbe7e-109">type</span><span class="sxs-lookup"><span data-stu-id="fbe7e-109">type</span></span>|<span data-ttu-id="fbe7e-110">Spécifie un type personnalisé qui dérive de la <xref:System.IdentityModel.Selectors.X509CertificateValidator> classe.</span><span class="sxs-lookup"><span data-stu-id="fbe7e-110">Specifies a custom type that derives from the <xref:System.IdentityModel.Selectors.X509CertificateValidator> class.</span></span> <span data-ttu-id="fbe7e-111">Affectez `certificateValidationMode` à l’attribut de l’élément la valeur [\<certificateValidation>](certificatevalidation.md) « Custom » pour utiliser ce type.</span><span class="sxs-lookup"><span data-stu-id="fbe7e-111">Set the `certificateValidationMode` attribute of the [\<certificateValidation>](certificatevalidation.md) element to "Custom" to use this type.</span></span> <span data-ttu-id="fbe7e-112">Pour plus d’informations sur la spécification de l' `type` attribut, consultez [références de types personnalisés](../windows-workflow-foundation/index.md).</span><span class="sxs-lookup"><span data-stu-id="fbe7e-112">For more information about how to specify the `type` attribute, see [Custom Type References](../windows-workflow-foundation/index.md).</span></span> <span data-ttu-id="fbe7e-113">Optionnel.</span><span class="sxs-lookup"><span data-stu-id="fbe7e-113">Optional.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="fbe7e-114">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="fbe7e-114">Child Elements</span></span>  

 <span data-ttu-id="fbe7e-115">None</span><span class="sxs-lookup"><span data-stu-id="fbe7e-115">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="fbe7e-116">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="fbe7e-116">Parent Elements</span></span>  
  
|<span data-ttu-id="fbe7e-117">Élément</span><span class="sxs-lookup"><span data-stu-id="fbe7e-117">Element</span></span>|<span data-ttu-id="fbe7e-118">Description</span><span class="sxs-lookup"><span data-stu-id="fbe7e-118">Description</span></span>|  
|-------------|-----------------|  
|[\<certificateValidation>](certificatevalidation.md)|<span data-ttu-id="fbe7e-119">Contrôle les paramètres que les gestionnaires de jetons utilisent pour valider les certificats.</span><span class="sxs-lookup"><span data-stu-id="fbe7e-119">Controls the settings that token handlers use to validate certificates.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="fbe7e-120">Exemple</span><span class="sxs-lookup"><span data-stu-id="fbe7e-120">Example</span></span>  
  
```xml  
<certificateValidation certificateValidationMode="Custom"  
                       revocationMode="Online"  
                       trustedStoreLocation="LocalMachine">  
    <certificateValidator type="MyNamespace.CustomValidator, MyAssembly" />
</certificateValidation>
```
