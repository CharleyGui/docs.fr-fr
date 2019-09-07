---
title: <mexNamedPipeBinding>
ms.date: 03/30/2017
ms.assetid: 193412fa-3260-414c-92c6-b32ed3b94a34
ms.openlocfilehash: b26201064aad3a8a09d8604a9706fe3c149cbf58
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70400229"
---
# <a name="mexnamedpipebinding"></a><span data-ttu-id="b1c5f-101">\<mexNamedPipeBinding></span><span class="sxs-lookup"><span data-stu-id="b1c5f-101">\<mexNamedPipeBinding></span></span>
<span data-ttu-id="b1c5f-102">Spécifie les paramètres pour une liaison utilisée pour l’échange de messages WS-MetadataExchange (WS-MEX) sur le canal nommé.</span><span class="sxs-lookup"><span data-stu-id="b1c5f-102">Specifies the settings for a binding used for the WS-MetadataExchange (WS-MEX) message exchange over named pipe.</span></span>  
  
<span data-ttu-id="b1c5f-103">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="b1c5f-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="b1c5f-104">&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="b1c5f-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="b1c5f-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<liaisons >** ](bindings.md)</span><span class="sxs-lookup"><span data-stu-id="b1c5f-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="b1c5f-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<mexNamedPipeBinding >**</span><span class="sxs-lookup"><span data-stu-id="b1c5f-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<mexNamedPipeBinding>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b1c5f-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b1c5f-107">Syntax</span></span>  
  
```xml  
<mexNamedPipeBinding>
  <binding closeTimeout="TimeSpan"
           name="string"
           openTimeout="TimeSpan"
           receiveTimeout="TimeSpan"
           sendTimeout="TimeSpan">
  </binding>
</mexNamedPipeBinding>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b1c5f-108">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="b1c5f-108">Attributes and Elements</span></span>  
 <span data-ttu-id="b1c5f-109">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="b1c5f-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b1c5f-110">Attributs</span><span class="sxs-lookup"><span data-stu-id="b1c5f-110">Attributes</span></span>  
  
|<span data-ttu-id="b1c5f-111">Attribut</span><span class="sxs-lookup"><span data-stu-id="b1c5f-111">Attribute</span></span>|<span data-ttu-id="b1c5f-112">Description</span><span class="sxs-lookup"><span data-stu-id="b1c5f-112">Description</span></span>|  
|---------------|-----------------|  
|`closeTimeout`|<span data-ttu-id="b1c5f-113"><xref:System.TimeSpan> qui spécifie l'intervalle de temps prévu pour la réalisation d'une opération de fermeture.</span><span class="sxs-lookup"><span data-stu-id="b1c5f-113">A <xref:System.TimeSpan> value that specifies the interval of time provided for a close operation to complete.</span></span> <span data-ttu-id="b1c5f-114">Cette valeur doit être supérieure ou égale à <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="b1c5f-114">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="b1c5f-115">La valeur par défaut est 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="b1c5f-115">The default is 00:01:00.</span></span>|  
|`name`|<span data-ttu-id="b1c5f-116">Chaîne qui contient le nom de configuration de la liaison.</span><span class="sxs-lookup"><span data-stu-id="b1c5f-116">A string that contains the configuration name of the binding.</span></span> <span data-ttu-id="b1c5f-117">Cette valeur doit être unique car elle permet d'identifier la liaison.</span><span class="sxs-lookup"><span data-stu-id="b1c5f-117">This value should be unique because it is used as an identification for the binding.</span></span> <span data-ttu-id="b1c5f-118">Chaque liaison porte un `name` et a un attribut `namespace` qui l’identifient de façon unique dans les métadonnées du service.</span><span class="sxs-lookup"><span data-stu-id="b1c5f-118">Each binding has a `name` and `namespace` attribute that together uniquely identify it in the metadata of the service.</span></span> <span data-ttu-id="b1c5f-119">De plus, ce nom est unique parmi les liaisons du même type.</span><span class="sxs-lookup"><span data-stu-id="b1c5f-119">In addition, this name is unique among bindings of the same type.</span></span> <span data-ttu-id="b1c5f-120">Depuis [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], les liaisons et les comportements ne sont pas obligés d’avoir un nom.</span><span class="sxs-lookup"><span data-stu-id="b1c5f-120">Starting with [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="b1c5f-121">Pour plus d’informations sur la configuration par défaut et les liaisons et les comportements sans valeur, consultez [configuration simplifiée](../../../wcf/simplified-configuration.md) et [configuration simplifiée pour les services WCF](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="b1c5f-121">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>|  
|`openTimeout`|<span data-ttu-id="b1c5f-122"><xref:System.TimeSpan> qui spécifie l'intervalle de temps prévu pour la réalisation d'une opération d'ouverture.</span><span class="sxs-lookup"><span data-stu-id="b1c5f-122">A <xref:System.TimeSpan> value that specifies the interval of time provided for an open operation to complete.</span></span> <span data-ttu-id="b1c5f-123">Cette valeur doit être supérieure ou égale à <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="b1c5f-123">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="b1c5f-124">La valeur par défaut est 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="b1c5f-124">The default is 00:01:00.</span></span>|  
|`receiveTimeout`|<span data-ttu-id="b1c5f-125"><xref:System.TimeSpan> qui spécifie l'intervalle de temps prévu pour la réalisation d'une opération de réception.</span><span class="sxs-lookup"><span data-stu-id="b1c5f-125">A <xref:System.TimeSpan> value that specifies the interval of time provided for a receive operation to complete.</span></span> <span data-ttu-id="b1c5f-126">Cette valeur doit être supérieure ou égale à <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="b1c5f-126">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="b1c5f-127">La valeur par défaut est 00:10:00.</span><span class="sxs-lookup"><span data-stu-id="b1c5f-127">The default is 00:10:00.</span></span>|  
|`sendTimeout`|<span data-ttu-id="b1c5f-128"><xref:System.TimeSpan> qui spécifie l'intervalle de temps prévu pour la réalisation d'une opération d'envoi.</span><span class="sxs-lookup"><span data-stu-id="b1c5f-128">A <xref:System.TimeSpan> value that specifies the interval of time provided for a send operation to complete.</span></span> <span data-ttu-id="b1c5f-129">Cette valeur doit être supérieure ou égale à <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="b1c5f-129">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="b1c5f-130">La valeur par défaut est 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="b1c5f-130">The default is 00:01:00.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="b1c5f-131">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="b1c5f-131">Child Elements</span></span>  
 <span data-ttu-id="b1c5f-132">Aucun.</span><span class="sxs-lookup"><span data-stu-id="b1c5f-132">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="b1c5f-133">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="b1c5f-133">Parent Elements</span></span>  
  
|<span data-ttu-id="b1c5f-134">Élément</span><span class="sxs-lookup"><span data-stu-id="b1c5f-134">Element</span></span>|<span data-ttu-id="b1c5f-135">Description</span><span class="sxs-lookup"><span data-stu-id="b1c5f-135">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b1c5f-136">\<bindings></span><span class="sxs-lookup"><span data-stu-id="b1c5f-136">\<bindings></span></span>](bindings.md)|<span data-ttu-id="b1c5f-137">Cet élément conserve une collection de liaisons standard et personnalisées.</span><span class="sxs-lookup"><span data-stu-id="b1c5f-137">This element holds a collection of standard and custom bindings.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="b1c5f-138">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b1c5f-138">See also</span></span>

- <xref:System.ServiceModel.Description.MetadataExchangeBindings.CreateMexNamedPipeBinding%2A>
- <xref:System.ServiceModel.Configuration.MexNamedPipeBindingElement>
- [<span data-ttu-id="b1c5f-139">Guide pratique pour Publier les métadonnées d’un service à l’aide d’un fichier de configuration</span><span class="sxs-lookup"><span data-stu-id="b1c5f-139">How to: Publish Metadata for a Service Using a Configuration File</span></span>](../../../wcf/feature-details/how-to-publish-metadata-for-a-service-using-a-configuration-file.md)
- [<span data-ttu-id="b1c5f-140">Publication et récupération de métadonnées sur une liaison personnalisée</span><span class="sxs-lookup"><span data-stu-id="b1c5f-140">Publishing and Retrieving Metadata Over a Custom Binding</span></span>](../../../wcf/extending/publishing-and-retrieving-metadata-over-a-custom-binding.md)
- [<span data-ttu-id="b1c5f-141">Métadonnées</span><span class="sxs-lookup"><span data-stu-id="b1c5f-141">Metadata</span></span>](../../../wcf/feature-details/metadata.md)
- [<span data-ttu-id="b1c5f-142">Liaisons</span><span class="sxs-lookup"><span data-stu-id="b1c5f-142">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="b1c5f-143">Configuration des liaisons fournies par le système</span><span class="sxs-lookup"><span data-stu-id="b1c5f-143">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="b1c5f-144">Utilisation de liaisons pour configurer des services et des clients</span><span class="sxs-lookup"><span data-stu-id="b1c5f-144">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="b1c5f-145">\<binding></span><span class="sxs-lookup"><span data-stu-id="b1c5f-145">\<binding></span></span>](../../../misc/binding.md)
