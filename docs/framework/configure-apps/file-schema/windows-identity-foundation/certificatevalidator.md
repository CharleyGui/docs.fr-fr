---
title: <certificateValidator>
ms.date: 03/30/2017
ms.assetid: 86161897-c20f-4ad8-9d7f-050c247251bf
author: BrucePerlerMS
ms.openlocfilehash: 3f3d79d3567c1714a79423b7767ce3f454b9d52d
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/06/2020
ms.locfileid: "79152786"
---
# \<certificateValidator>
<span data-ttu-id="82b5b-101">Spécifie un type personnalisé pour la validation du certificat.</span><span class="sxs-lookup"><span data-stu-id="82b5b-101">Specifies a custom type for certificate validation.</span></span> <span data-ttu-id="82b5b-102">Ce type est utilisé uniquement si l' `certificateValidationMode` attribut de l' [\<certificateValidation>](certificatevalidation.md) élément a la valeur « Custom ».</span><span class="sxs-lookup"><span data-stu-id="82b5b-102">This type is used only if the `certificateValidationMode` attribute of the [\<certificateValidation>](certificatevalidation.md) element is set to "Custom".</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<certificateValidation>**](certificatevalidation.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<certificateValidator>**  
  
## <a name="syntax"></a><span data-ttu-id="82b5b-103">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="82b5b-103">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="82b5b-104">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="82b5b-104">Attributes and Elements</span></span>  
 <span data-ttu-id="82b5b-105">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="82b5b-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="82b5b-106">Attributs</span><span class="sxs-lookup"><span data-stu-id="82b5b-106">Attributes</span></span>  
  
|<span data-ttu-id="82b5b-107">Attribut</span><span class="sxs-lookup"><span data-stu-id="82b5b-107">Attribute</span></span>|<span data-ttu-id="82b5b-108">Description</span><span class="sxs-lookup"><span data-stu-id="82b5b-108">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="82b5b-109">type</span><span class="sxs-lookup"><span data-stu-id="82b5b-109">type</span></span>|<span data-ttu-id="82b5b-110">Spécifie un type personnalisé qui dérive de la <xref:System.IdentityModel.Selectors.X509CertificateValidator> classe.</span><span class="sxs-lookup"><span data-stu-id="82b5b-110">Specifies a custom type that derives from the <xref:System.IdentityModel.Selectors.X509CertificateValidator> class.</span></span> <span data-ttu-id="82b5b-111">Affectez `certificateValidationMode` à l’attribut de l’élément la valeur [\<certificateValidation>](certificatevalidation.md) « Custom » pour utiliser ce type.</span><span class="sxs-lookup"><span data-stu-id="82b5b-111">Set the `certificateValidationMode` attribute of the [\<certificateValidation>](certificatevalidation.md) element to "Custom" to use this type.</span></span> <span data-ttu-id="82b5b-112">Pour plus d’informations sur la spécification de l' `type` attribut, consultez [références de types personnalisés](../windows-workflow-foundation/index.md).</span><span class="sxs-lookup"><span data-stu-id="82b5b-112">For more information about how to specify the `type` attribute, see [Custom Type References](../windows-workflow-foundation/index.md).</span></span> <span data-ttu-id="82b5b-113">facultatif.</span><span class="sxs-lookup"><span data-stu-id="82b5b-113">Optional.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="82b5b-114">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="82b5b-114">Child Elements</span></span>  
 <span data-ttu-id="82b5b-115">Aucune</span><span class="sxs-lookup"><span data-stu-id="82b5b-115">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="82b5b-116">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="82b5b-116">Parent Elements</span></span>  
  
|<span data-ttu-id="82b5b-117">Élément</span><span class="sxs-lookup"><span data-stu-id="82b5b-117">Element</span></span>|<span data-ttu-id="82b5b-118">Description</span><span class="sxs-lookup"><span data-stu-id="82b5b-118">Description</span></span>|  
|-------------|-----------------|  
|[\<certificateValidation>](certificatevalidation.md)|<span data-ttu-id="82b5b-119">Contrôle les paramètres que les gestionnaires de jetons utilisent pour valider les certificats.</span><span class="sxs-lookup"><span data-stu-id="82b5b-119">Controls the settings that token handlers use to validate certificates.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="82b5b-120">Exemple</span><span class="sxs-lookup"><span data-stu-id="82b5b-120">Example</span></span>  
  
```xml  
<certificateValidation certificateValidationMode="Custom"  
                       revocationMode="Online"  
                       trustedStoreLocation="LocalMachine">  
    <certificateValidator type="MyNamespace.CustomValidator, MyAssembly" />
</certificateValidation>
```
