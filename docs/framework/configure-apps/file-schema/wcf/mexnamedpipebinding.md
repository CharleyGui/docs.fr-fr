---
title: <mexNamedPipeBinding>
ms.date: 03/30/2017
ms.assetid: 193412fa-3260-414c-92c6-b32ed3b94a34
ms.openlocfilehash: 41f5b19f5067d9ac7faa2c7329dd07dd9d48e9b3
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74430874"
---
# <a name="mexnamedpipebinding"></a><span data-ttu-id="cf44d-101">\<mexNamedPipeBinding ></span><span class="sxs-lookup"><span data-stu-id="cf44d-101">\<mexNamedPipeBinding></span></span>
<span data-ttu-id="cf44d-102">Spécifie les paramètres pour une liaison utilisée pour l’échange de messages WS-MetadataExchange (WS-MEX) sur le canal nommé.</span><span class="sxs-lookup"><span data-stu-id="cf44d-102">Specifies the settings for a binding used for the WS-MetadataExchange (WS-MEX) message exchange over named pipe.</span></span>  
  
<span data-ttu-id="cf44d-103">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="cf44d-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="cf44d-104">&nbsp;&nbsp;[ **\<> System. serviceModel**](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="cf44d-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="cf44d-105">&nbsp;&nbsp;&nbsp;&nbsp;[**liaisons**](bindings.md)\<></span><span class="sxs-lookup"><span data-stu-id="cf44d-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="cf44d-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;\<**mexNamedPipeBinding >**</span><span class="sxs-lookup"><span data-stu-id="cf44d-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<mexNamedPipeBinding>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cf44d-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="cf44d-107">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="cf44d-108">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="cf44d-108">Attributes and Elements</span></span>  
 <span data-ttu-id="cf44d-109">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="cf44d-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="cf44d-110">Attributs</span><span class="sxs-lookup"><span data-stu-id="cf44d-110">Attributes</span></span>  
  
|<span data-ttu-id="cf44d-111">Attribut</span><span class="sxs-lookup"><span data-stu-id="cf44d-111">Attribute</span></span>|<span data-ttu-id="cf44d-112">Description</span><span class="sxs-lookup"><span data-stu-id="cf44d-112">Description</span></span>|  
|---------------|-----------------|  
|`closeTimeout`|<span data-ttu-id="cf44d-113"><xref:System.TimeSpan> qui spécifie l'intervalle de temps prévu pour la réalisation d'une opération de fermeture.</span><span class="sxs-lookup"><span data-stu-id="cf44d-113">A <xref:System.TimeSpan> value that specifies the interval of time provided for a close operation to complete.</span></span> <span data-ttu-id="cf44d-114">Cette valeur doit être supérieure ou égale à <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="cf44d-114">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="cf44d-115">La valeur par défaut est 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="cf44d-115">The default is 00:01:00.</span></span>|  
|`name`|<span data-ttu-id="cf44d-116">Chaîne qui contient le nom de configuration de la liaison.</span><span class="sxs-lookup"><span data-stu-id="cf44d-116">A string that contains the configuration name of the binding.</span></span> <span data-ttu-id="cf44d-117">Cette valeur doit être unique car elle permet d'identifier la liaison.</span><span class="sxs-lookup"><span data-stu-id="cf44d-117">This value should be unique because it is used as an identification for the binding.</span></span> <span data-ttu-id="cf44d-118">À compter de .NET Framework 4, les liaisons et les comportements n’ont pas besoin d’un nom.</span><span class="sxs-lookup"><span data-stu-id="cf44d-118">Starting with .NET Framework 4, bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="cf44d-119">Pour plus d’informations sur la configuration par défaut et les liaisons et les comportements sans valeur, consultez [configuration simplifiée](../../../wcf/simplified-configuration.md) et [configuration simplifiée pour les services WCF](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="cf44d-119">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>|  
|`openTimeout`|<span data-ttu-id="cf44d-120"><xref:System.TimeSpan> qui spécifie l'intervalle de temps prévu pour la réalisation d'une opération d'ouverture.</span><span class="sxs-lookup"><span data-stu-id="cf44d-120">A <xref:System.TimeSpan> value that specifies the interval of time provided for an open operation to complete.</span></span> <span data-ttu-id="cf44d-121">Cette valeur doit être supérieure ou égale à <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="cf44d-121">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="cf44d-122">La valeur par défaut est 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="cf44d-122">The default is 00:01:00.</span></span>|  
|`receiveTimeout`|<span data-ttu-id="cf44d-123"><xref:System.TimeSpan> qui spécifie l'intervalle de temps prévu pour la réalisation d'une opération de réception.</span><span class="sxs-lookup"><span data-stu-id="cf44d-123">A <xref:System.TimeSpan> value that specifies the interval of time provided for a receive operation to complete.</span></span> <span data-ttu-id="cf44d-124">Cette valeur doit être supérieure ou égale à <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="cf44d-124">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="cf44d-125">La valeur par défaut est 00:10:00.</span><span class="sxs-lookup"><span data-stu-id="cf44d-125">The default is 00:10:00.</span></span>|  
|`sendTimeout`|<span data-ttu-id="cf44d-126"><xref:System.TimeSpan> qui spécifie l'intervalle de temps prévu pour la réalisation d'une opération d'envoi.</span><span class="sxs-lookup"><span data-stu-id="cf44d-126">A <xref:System.TimeSpan> value that specifies the interval of time provided for a send operation to complete.</span></span> <span data-ttu-id="cf44d-127">Cette valeur doit être supérieure ou égale à <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="cf44d-127">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="cf44d-128">La valeur par défaut est 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="cf44d-128">The default is 00:01:00.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="cf44d-129">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="cf44d-129">Child Elements</span></span>  
 <span data-ttu-id="cf44d-130">None.</span><span class="sxs-lookup"><span data-stu-id="cf44d-130">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="cf44d-131">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="cf44d-131">Parent Elements</span></span>  
  
|<span data-ttu-id="cf44d-132">Élément</span><span class="sxs-lookup"><span data-stu-id="cf44d-132">Element</span></span>|<span data-ttu-id="cf44d-133">Description</span><span class="sxs-lookup"><span data-stu-id="cf44d-133">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="cf44d-134">liaisons de \<></span><span class="sxs-lookup"><span data-stu-id="cf44d-134">\<bindings></span></span>](bindings.md)|<span data-ttu-id="cf44d-135">Cet élément conserve une collection de liaisons standard et personnalisées.</span><span class="sxs-lookup"><span data-stu-id="cf44d-135">This element holds a collection of standard and custom bindings.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="cf44d-136">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="cf44d-136">See also</span></span>

- <xref:System.ServiceModel.Description.MetadataExchangeBindings.CreateMexNamedPipeBinding%2A>
- <xref:System.ServiceModel.Configuration.MexNamedPipeBindingElement>
- [<span data-ttu-id="cf44d-137">Guide pratique pour publier les métadonnées d’un service à l’aide d’un fichier de configuration</span><span class="sxs-lookup"><span data-stu-id="cf44d-137">How to: Publish Metadata for a Service Using a Configuration File</span></span>](../../../wcf/feature-details/how-to-publish-metadata-for-a-service-using-a-configuration-file.md)
- [<span data-ttu-id="cf44d-138">Publication et récupération de métadonnées sur une liaison personnalisée</span><span class="sxs-lookup"><span data-stu-id="cf44d-138">Publishing and Retrieving Metadata Over a Custom Binding</span></span>](../../../wcf/extending/publishing-and-retrieving-metadata-over-a-custom-binding.md)
- [<span data-ttu-id="cf44d-139">Métadonnées</span><span class="sxs-lookup"><span data-stu-id="cf44d-139">Metadata</span></span>](../../../wcf/feature-details/metadata.md)
- [<span data-ttu-id="cf44d-140">Liaisons</span><span class="sxs-lookup"><span data-stu-id="cf44d-140">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="cf44d-141">Configuration des liaisons fournies par le système</span><span class="sxs-lookup"><span data-stu-id="cf44d-141">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="cf44d-142">Utilisation de liaisons pour configurer des services et des clients</span><span class="sxs-lookup"><span data-stu-id="cf44d-142">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="cf44d-143">liaison de \<></span><span class="sxs-lookup"><span data-stu-id="cf44d-143">\<binding></span></span>](bindings.md)
