---
title: <persistableType>
ms.date: 03/30/2017
ms.assetid: e5425fe6-523a-4076-aab4-2c2515b1d830
ms.openlocfilehash: 328caaefe0cc24da45b460cab0a672dc8a6ccce1
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/10/2019
ms.locfileid: "70855069"
---
# <a name="persistabletype"></a><span data-ttu-id="42241-101">\<persistableType></span><span class="sxs-lookup"><span data-stu-id="42241-101">\<persistableType></span></span>
<span data-ttu-id="42241-102">Spécifie tous les types persistants.</span><span class="sxs-lookup"><span data-stu-id="42241-102">Specifies all the persistable types.</span></span>  
  
<span data-ttu-id="42241-103">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="42241-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="42241-104">&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="42241-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="42241-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> de comconventions**](comcontracts.md)</span><span class="sxs-lookup"><span data-stu-id="42241-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<comContracts>**](comcontracts.md)</span></span>\
<span data-ttu-id="42241-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<comContract >** ](comcontract.md)</span><span class="sxs-lookup"><span data-stu-id="42241-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<comContract>**](comcontract.md)</span></span>\
<span data-ttu-id="42241-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<persistableTypes >** ](persistabletypes.md)</span><span class="sxs-lookup"><span data-stu-id="42241-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<persistableTypes>**](persistabletypes.md)</span></span>\
<span data-ttu-id="42241-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<persistableType >**</span><span class="sxs-lookup"><span data-stu-id="42241-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<persistableType>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="42241-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="42241-109">Syntax</span></span>  
  
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
  
## <a name="type"></a><span data-ttu-id="42241-110">Type</span><span class="sxs-lookup"><span data-stu-id="42241-110">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="42241-111">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="42241-111">Attributes and Elements</span></span>  
 <span data-ttu-id="42241-112">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="42241-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="42241-113">Attributs</span><span class="sxs-lookup"><span data-stu-id="42241-113">Attributes</span></span>  
  
|<span data-ttu-id="42241-114">Attribut</span><span class="sxs-lookup"><span data-stu-id="42241-114">Attribute</span></span>|<span data-ttu-id="42241-115">Description</span><span class="sxs-lookup"><span data-stu-id="42241-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="42241-116">id</span><span class="sxs-lookup"><span data-stu-id="42241-116">id</span></span>|<span data-ttu-id="42241-117">Attribut requis qui contient une chaîne spécifiant un identificateur unique pour un type persistant.</span><span class="sxs-lookup"><span data-stu-id="42241-117">A required attribute that contains a string that specifies a unique identifier for a persistable type.</span></span>|  
|<span data-ttu-id="42241-118">name</span><span class="sxs-lookup"><span data-stu-id="42241-118">name</span></span>|<span data-ttu-id="42241-119">Attribut facultatif qui contient une chaîne spécifiant le nom du type persistant.</span><span class="sxs-lookup"><span data-stu-id="42241-119">An optional attribute that contains a string that specifies the name of the persistable type.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="42241-120">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="42241-120">Child Elements</span></span>  
 <span data-ttu-id="42241-121">Aucun</span><span class="sxs-lookup"><span data-stu-id="42241-121">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="42241-122">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="42241-122">Parent Elements</span></span>  
  
|<span data-ttu-id="42241-123">Élément</span><span class="sxs-lookup"><span data-stu-id="42241-123">Element</span></span>|<span data-ttu-id="42241-124">Description</span><span class="sxs-lookup"><span data-stu-id="42241-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="42241-125">\<persistableTypes></span><span class="sxs-lookup"><span data-stu-id="42241-125">\<persistableTypes></span></span>](persistabletypes.md)|<span data-ttu-id="42241-126">Collection d'éléments `persistableType`.</span><span class="sxs-lookup"><span data-stu-id="42241-126">A collection of `persistableType` elements.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="42241-127">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="42241-127">See also</span></span>

- <xref:System.ServiceModel.Configuration.ComPersistableTypeElementCollection>
- <xref:System.ServiceModel.Configuration.ComPersistableTypeElement>
- [<span data-ttu-id="42241-128">\<comContracts></span><span class="sxs-lookup"><span data-stu-id="42241-128">\<comContracts></span></span>](comcontracts.md)
- [<span data-ttu-id="42241-129">Intégration à des applications COM+</span><span class="sxs-lookup"><span data-stu-id="42241-129">Integrating with COM+ Applications</span></span>](../../../wcf/feature-details/integrating-with-com-plus-applications.md)
- [<span data-ttu-id="42241-130">Guide pratique : Configurer les paramètres du service COM+</span><span class="sxs-lookup"><span data-stu-id="42241-130">How to: Configure COM+ Service Settings</span></span>](../../../wcf/feature-details/how-to-configure-com-service-settings.md)
