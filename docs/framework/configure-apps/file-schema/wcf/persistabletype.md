---
title: <persistableType>
ms.date: 03/30/2017
ms.assetid: e5425fe6-523a-4076-aab4-2c2515b1d830
ms.openlocfilehash: 6425b21fe50865beb7bb2876ea478b415fbe3944
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91181516"
---
# \<persistableType>

<span data-ttu-id="dc62e-101">Spécifie tous les types persistants.</span><span class="sxs-lookup"><span data-stu-id="dc62e-101">Specifies all the persistable types.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<comContracts>**](comcontracts.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<comContract>**](comcontract.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<persistableTypes>**](persistabletypes.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<persistableType>**  
  
## <a name="syntax"></a><span data-ttu-id="dc62e-102">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="dc62e-102">Syntax</span></span>  
  
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
  
## <a name="type"></a><span data-ttu-id="dc62e-103">Type</span><span class="sxs-lookup"><span data-stu-id="dc62e-103">Type</span></span>  

 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="dc62e-104">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="dc62e-104">Attributes and Elements</span></span>  

 <span data-ttu-id="dc62e-105">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="dc62e-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="dc62e-106">Attributs</span><span class="sxs-lookup"><span data-stu-id="dc62e-106">Attributes</span></span>  
  
|<span data-ttu-id="dc62e-107">Attribut</span><span class="sxs-lookup"><span data-stu-id="dc62e-107">Attribute</span></span>|<span data-ttu-id="dc62e-108">Description</span><span class="sxs-lookup"><span data-stu-id="dc62e-108">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="dc62e-109">id</span><span class="sxs-lookup"><span data-stu-id="dc62e-109">id</span></span>|<span data-ttu-id="dc62e-110">Attribut requis qui contient une chaîne spécifiant un identificateur unique pour un type persistant.</span><span class="sxs-lookup"><span data-stu-id="dc62e-110">A required attribute that contains a string that specifies a unique identifier for a persistable type.</span></span>|  
|<span data-ttu-id="dc62e-111">name</span><span class="sxs-lookup"><span data-stu-id="dc62e-111">name</span></span>|<span data-ttu-id="dc62e-112">Attribut facultatif qui contient une chaîne spécifiant le nom du type persistant.</span><span class="sxs-lookup"><span data-stu-id="dc62e-112">An optional attribute that contains a string that specifies the name of the persistable type.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="dc62e-113">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="dc62e-113">Child Elements</span></span>  

 <span data-ttu-id="dc62e-114">None</span><span class="sxs-lookup"><span data-stu-id="dc62e-114">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="dc62e-115">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="dc62e-115">Parent Elements</span></span>  
  
|<span data-ttu-id="dc62e-116">Élément</span><span class="sxs-lookup"><span data-stu-id="dc62e-116">Element</span></span>|<span data-ttu-id="dc62e-117">Description</span><span class="sxs-lookup"><span data-stu-id="dc62e-117">Description</span></span>|  
|-------------|-----------------|  
|[\<persistableTypes>](persistabletypes.md)|<span data-ttu-id="dc62e-118">Collection d'éléments `persistableType`.</span><span class="sxs-lookup"><span data-stu-id="dc62e-118">A collection of `persistableType` elements.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="dc62e-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="dc62e-119">See also</span></span>

- <xref:System.ServiceModel.Configuration.ComPersistableTypeElementCollection>
- <xref:System.ServiceModel.Configuration.ComPersistableTypeElement>
- [\<comContracts>](comcontracts.md)
- [<span data-ttu-id="dc62e-120">Intégration à des applications COM+</span><span class="sxs-lookup"><span data-stu-id="dc62e-120">Integrating with COM+ Applications</span></span>](../../../wcf/feature-details/integrating-with-com-plus-applications.md)
- [<span data-ttu-id="dc62e-121">Procédure : configurer des paramètres de service COM+</span><span class="sxs-lookup"><span data-stu-id="dc62e-121">How to: Configure COM+ Service Settings</span></span>](../../../wcf/feature-details/how-to-configure-com-service-settings.md)
