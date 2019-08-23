---
title: <mexNamedPipeBinding>
ms.date: 03/30/2017
ms.assetid: 193412fa-3260-414c-92c6-b32ed3b94a34
ms.openlocfilehash: 0d0904c02e31def1b5264bec9f61eac0c9a8e964
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69931230"
---
# <a name="mexnamedpipebinding"></a><span data-ttu-id="34cc4-101">\<mexNamedPipeBinding></span><span class="sxs-lookup"><span data-stu-id="34cc4-101">\<mexNamedPipeBinding></span></span>
<span data-ttu-id="34cc4-102">Spécifie les paramètres pour une liaison utilisée pour l’échange de messages WS-MetadataExchange (WS-MEX) sur le canal nommé.</span><span class="sxs-lookup"><span data-stu-id="34cc4-102">Specifies the settings for a binding used for the WS-MetadataExchange (WS-MEX) message exchange over named pipe.</span></span>  
  
 <span data-ttu-id="34cc4-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="34cc4-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="34cc4-104">\<bindings></span><span class="sxs-lookup"><span data-stu-id="34cc4-104">\<bindings></span></span>  
<span data-ttu-id="34cc4-105">\<mexNamedPipeBinding></span><span class="sxs-lookup"><span data-stu-id="34cc4-105">\<mexNamedPipeBinding></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="34cc4-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="34cc4-106">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="34cc4-107">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="34cc4-107">Attributes and Elements</span></span>  
 <span data-ttu-id="34cc4-108">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="34cc4-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="34cc4-109">Attributs</span><span class="sxs-lookup"><span data-stu-id="34cc4-109">Attributes</span></span>  
  
|<span data-ttu-id="34cc4-110">Attribut</span><span class="sxs-lookup"><span data-stu-id="34cc4-110">Attribute</span></span>|<span data-ttu-id="34cc4-111">Description</span><span class="sxs-lookup"><span data-stu-id="34cc4-111">Description</span></span>|  
|---------------|-----------------|  
|`closeTimeout`|<span data-ttu-id="34cc4-112"><xref:System.TimeSpan> qui spécifie l'intervalle de temps prévu pour la réalisation d'une opération de fermeture.</span><span class="sxs-lookup"><span data-stu-id="34cc4-112">A <xref:System.TimeSpan> value that specifies the interval of time provided for a close operation to complete.</span></span> <span data-ttu-id="34cc4-113">Cette valeur doit être supérieure ou égale à <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="34cc4-113">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="34cc4-114">La valeur par défaut est 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="34cc4-114">The default is 00:01:00.</span></span>|  
|`name`|<span data-ttu-id="34cc4-115">Chaîne qui contient le nom de configuration de la liaison.</span><span class="sxs-lookup"><span data-stu-id="34cc4-115">A string that contains the configuration name of the binding.</span></span> <span data-ttu-id="34cc4-116">Cette valeur doit être unique car elle permet d'identifier la liaison.</span><span class="sxs-lookup"><span data-stu-id="34cc4-116">This value should be unique because it is used as an identification for the binding.</span></span> <span data-ttu-id="34cc4-117">Chaque liaison porte un `name` et a un attribut `namespace` qui l’identifient de façon unique dans les métadonnées du service.</span><span class="sxs-lookup"><span data-stu-id="34cc4-117">Each binding has a `name` and `namespace` attribute that together uniquely identify it in the metadata of the service.</span></span> <span data-ttu-id="34cc4-118">De plus, ce nom est unique parmi les liaisons du même type.</span><span class="sxs-lookup"><span data-stu-id="34cc4-118">In addition, this name is unique among bindings of the same type.</span></span> <span data-ttu-id="34cc4-119">Depuis [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], les liaisons et les comportements ne sont pas obligés d’avoir un nom.</span><span class="sxs-lookup"><span data-stu-id="34cc4-119">Starting with [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="34cc4-120">Pour plus d’informations sur la configuration par défaut et les liaisons et les comportements sans valeur, consultez [configuration simplifiée](../../../wcf/simplified-configuration.md) et [configuration simplifiée pour les services WCF](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="34cc4-120">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>|  
|`openTimeout`|<span data-ttu-id="34cc4-121"><xref:System.TimeSpan> qui spécifie l'intervalle de temps prévu pour la réalisation d'une opération d'ouverture.</span><span class="sxs-lookup"><span data-stu-id="34cc4-121">A <xref:System.TimeSpan> value that specifies the interval of time provided for an open operation to complete.</span></span> <span data-ttu-id="34cc4-122">Cette valeur doit être supérieure ou égale à <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="34cc4-122">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="34cc4-123">La valeur par défaut est 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="34cc4-123">The default is 00:01:00.</span></span>|  
|`receiveTimeout`|<span data-ttu-id="34cc4-124"><xref:System.TimeSpan> qui spécifie l'intervalle de temps prévu pour la réalisation d'une opération de réception.</span><span class="sxs-lookup"><span data-stu-id="34cc4-124">A <xref:System.TimeSpan> value that specifies the interval of time provided for a receive operation to complete.</span></span> <span data-ttu-id="34cc4-125">Cette valeur doit être supérieure ou égale à <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="34cc4-125">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="34cc4-126">La valeur par défaut est 00:10:00.</span><span class="sxs-lookup"><span data-stu-id="34cc4-126">The default is 00:10:00.</span></span>|  
|`sendTimeout`|<span data-ttu-id="34cc4-127"><xref:System.TimeSpan> qui spécifie l'intervalle de temps prévu pour la réalisation d'une opération d'envoi.</span><span class="sxs-lookup"><span data-stu-id="34cc4-127">A <xref:System.TimeSpan> value that specifies the interval of time provided for a send operation to complete.</span></span> <span data-ttu-id="34cc4-128">Cette valeur doit être supérieure ou égale à <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="34cc4-128">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="34cc4-129">La valeur par défaut est 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="34cc4-129">The default is 00:01:00.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="34cc4-130">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="34cc4-130">Child Elements</span></span>  
 <span data-ttu-id="34cc4-131">Aucun.</span><span class="sxs-lookup"><span data-stu-id="34cc4-131">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="34cc4-132">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="34cc4-132">Parent Elements</span></span>  
  
|<span data-ttu-id="34cc4-133">Élément</span><span class="sxs-lookup"><span data-stu-id="34cc4-133">Element</span></span>|<span data-ttu-id="34cc4-134">Description</span><span class="sxs-lookup"><span data-stu-id="34cc4-134">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="34cc4-135">\<bindings></span><span class="sxs-lookup"><span data-stu-id="34cc4-135">\<bindings></span></span>](bindings.md)|<span data-ttu-id="34cc4-136">Cet élément conserve une collection de liaisons standard et personnalisées.</span><span class="sxs-lookup"><span data-stu-id="34cc4-136">This element holds a collection of standard and custom bindings.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="34cc4-137">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="34cc4-137">See also</span></span>

- <xref:System.ServiceModel.Description.MetadataExchangeBindings.CreateMexNamedPipeBinding%2A>
- <xref:System.ServiceModel.Configuration.MexNamedPipeBindingElement>
- [<span data-ttu-id="34cc4-138">Guide pratique pour Publier les métadonnées d’un service à l’aide d’un fichier de configuration</span><span class="sxs-lookup"><span data-stu-id="34cc4-138">How to: Publish Metadata for a Service Using a Configuration File</span></span>](../../../wcf/feature-details/how-to-publish-metadata-for-a-service-using-a-configuration-file.md)
- [<span data-ttu-id="34cc4-139">Publication et récupération de métadonnées sur une liaison personnalisée</span><span class="sxs-lookup"><span data-stu-id="34cc4-139">Publishing and Retrieving Metadata Over a Custom Binding</span></span>](../../../wcf/extending/publishing-and-retrieving-metadata-over-a-custom-binding.md)
- [<span data-ttu-id="34cc4-140">Métadonnées</span><span class="sxs-lookup"><span data-stu-id="34cc4-140">Metadata</span></span>](../../../wcf/feature-details/metadata.md)
- [<span data-ttu-id="34cc4-141">Liaisons</span><span class="sxs-lookup"><span data-stu-id="34cc4-141">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="34cc4-142">Configuration des liaisons fournies par le système</span><span class="sxs-lookup"><span data-stu-id="34cc4-142">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="34cc4-143">Utilisation de liaisons pour configurer des services et des clients</span><span class="sxs-lookup"><span data-stu-id="34cc4-143">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="34cc4-144">\<binding></span><span class="sxs-lookup"><span data-stu-id="34cc4-144">\<binding></span></span>](../../../misc/binding.md)
