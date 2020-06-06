---
title: <persistableType>
ms.date: 03/30/2017
ms.assetid: e5425fe6-523a-4076-aab4-2c2515b1d830
ms.openlocfilehash: 328caaefe0cc24da45b460cab0a672dc8a6ccce1
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/06/2020
ms.locfileid: "70855069"
---
# \<persistableType>
<span data-ttu-id="3f0f1-101">Spécifie tous les types persistants.</span><span class="sxs-lookup"><span data-stu-id="3f0f1-101">Specifies all the persistable types.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<comContracts>**](comcontracts.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<comContract>**](comcontract.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<persistableTypes>**](persistabletypes.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<persistableType>**  
  
## <a name="syntax"></a><span data-ttu-id="3f0f1-102">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3f0f1-102">Syntax</span></span>  
  
```xml  
<comContracts>
  <comContract>
    <persistableTypes>
      <persistableType id="String"
                       name="String">
      </persistableType>
    </persistableTypes>
  </comContract>
</comContracts>
```  
  
## <a name="type"></a><span data-ttu-id="3f0f1-103">Type</span><span class="sxs-lookup"><span data-stu-id="3f0f1-103">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="3f0f1-104">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="3f0f1-104">Attributes and Elements</span></span>  
 <span data-ttu-id="3f0f1-105">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="3f0f1-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="3f0f1-106">Attributs</span><span class="sxs-lookup"><span data-stu-id="3f0f1-106">Attributes</span></span>  
  
|<span data-ttu-id="3f0f1-107">Attribut</span><span class="sxs-lookup"><span data-stu-id="3f0f1-107">Attribute</span></span>|<span data-ttu-id="3f0f1-108">Description</span><span class="sxs-lookup"><span data-stu-id="3f0f1-108">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="3f0f1-109">id</span><span class="sxs-lookup"><span data-stu-id="3f0f1-109">id</span></span>|<span data-ttu-id="3f0f1-110">Attribut requis qui contient une chaîne spécifiant un identificateur unique pour un type persistant.</span><span class="sxs-lookup"><span data-stu-id="3f0f1-110">A required attribute that contains a string that specifies a unique identifier for a persistable type.</span></span>|  
|<span data-ttu-id="3f0f1-111">name</span><span class="sxs-lookup"><span data-stu-id="3f0f1-111">name</span></span>|<span data-ttu-id="3f0f1-112">Attribut facultatif qui contient une chaîne spécifiant le nom du type persistant.</span><span class="sxs-lookup"><span data-stu-id="3f0f1-112">An optional attribute that contains a string that specifies the name of the persistable type.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="3f0f1-113">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="3f0f1-113">Child Elements</span></span>  
 <span data-ttu-id="3f0f1-114">Aucune</span><span class="sxs-lookup"><span data-stu-id="3f0f1-114">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="3f0f1-115">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="3f0f1-115">Parent Elements</span></span>  
  
|<span data-ttu-id="3f0f1-116">Élément</span><span class="sxs-lookup"><span data-stu-id="3f0f1-116">Element</span></span>|<span data-ttu-id="3f0f1-117">Description</span><span class="sxs-lookup"><span data-stu-id="3f0f1-117">Description</span></span>|  
|-------------|-----------------|  
|[\<persistableTypes>](persistabletypes.md)|<span data-ttu-id="3f0f1-118">Collection d'éléments `persistableType`.</span><span class="sxs-lookup"><span data-stu-id="3f0f1-118">A collection of `persistableType` elements.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="3f0f1-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3f0f1-119">See also</span></span>

- <xref:System.ServiceModel.Configuration.ComPersistableTypeElementCollection>
- <xref:System.ServiceModel.Configuration.ComPersistableTypeElement>
- [\<comContracts>](comcontracts.md)
- [<span data-ttu-id="3f0f1-120">Intégration à des applications COM+</span><span class="sxs-lookup"><span data-stu-id="3f0f1-120">Integrating with COM+ Applications</span></span>](../../../wcf/feature-details/integrating-with-com-plus-applications.md)
- [<span data-ttu-id="3f0f1-121">Comment : configurer des paramètres de service COM+</span><span class="sxs-lookup"><span data-stu-id="3f0f1-121">How to: Configure COM+ Service Settings</span></span>](../../../wcf/feature-details/how-to-configure-com-service-settings.md)
