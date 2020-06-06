---
title: <add> de <baseAddresses>
ms.date: 03/30/2017
ms.assetid: 1bd7426f-5f4f-43fc-b8e9-de842219aa32
ms.openlocfilehash: d75142209ad8706d0cad5ce188d9d991a5e881bc
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/06/2020
ms.locfileid: "70850583"
---
# <a name="add-of-baseaddresses"></a><span data-ttu-id="6dc31-102">\<add> de \<baseAddresses></span><span class="sxs-lookup"><span data-stu-id="6dc31-102">\<add> of \<baseAddresses></span></span>
<span data-ttu-id="6dc31-103">Représente un élément de configuration qui spécifie les adresses de base utilisées par l'hôte de service.</span><span class="sxs-lookup"><span data-stu-id="6dc31-103">Represents a configuration element that specifies the base addresses used by the service host.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<services>**](services.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<service>**](service.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<host>**](host.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<baseAddresses>**](baseaddresses.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**  
  
## <a name="syntax"></a><span data-ttu-id="6dc31-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6dc31-104">Syntax</span></span>  
  
```xml  
<add baseAddress="string" />
```  
  
## <a name="type"></a><span data-ttu-id="6dc31-105">Type</span><span class="sxs-lookup"><span data-stu-id="6dc31-105">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="6dc31-106">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="6dc31-106">Attributes and Elements</span></span>  
 <span data-ttu-id="6dc31-107">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="6dc31-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="6dc31-108">Attributs</span><span class="sxs-lookup"><span data-stu-id="6dc31-108">Attributes</span></span>  
  
|<span data-ttu-id="6dc31-109">Attribut</span><span class="sxs-lookup"><span data-stu-id="6dc31-109">Attribute</span></span>|<span data-ttu-id="6dc31-110">Description</span><span class="sxs-lookup"><span data-stu-id="6dc31-110">Description</span></span>|  
|---------------|-----------------|  
|`baseAddress`|<span data-ttu-id="6dc31-111">Chaîne indiquant une adresse de base utilisée par l'hôte de service.</span><span class="sxs-lookup"><span data-stu-id="6dc31-111">A string that specifies a base address used by the service host.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="6dc31-112">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="6dc31-112">Child Elements</span></span>  
 <span data-ttu-id="6dc31-113">Aucun.</span><span class="sxs-lookup"><span data-stu-id="6dc31-113">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="6dc31-114">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="6dc31-114">Parent Elements</span></span>  
  
|<span data-ttu-id="6dc31-115">Élément</span><span class="sxs-lookup"><span data-stu-id="6dc31-115">Element</span></span>|<span data-ttu-id="6dc31-116">Description</span><span class="sxs-lookup"><span data-stu-id="6dc31-116">Description</span></span>|  
|-------------|-----------------|  
|[\<baseAddresses>](baseaddresses.md)|<span data-ttu-id="6dc31-117">Collection d'éléments `baseAddress`.</span><span class="sxs-lookup"><span data-stu-id="6dc31-117">A collection of `baseAddress` elements.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="6dc31-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="6dc31-118">See also</span></span>

- <xref:System.ServiceModel.Configuration.HostElement>
- <xref:System.ServiceModel.ServiceHost>
- <xref:System.ServiceModel.ServiceHostBase.BaseAddresses%2A>
- [<span data-ttu-id="6dc31-119">Hosting</span><span class="sxs-lookup"><span data-stu-id="6dc31-119">Hosting</span></span>](../../../wcf/feature-details/hosting.md)
