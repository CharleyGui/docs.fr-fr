---
title: <mexHttpsBinding>
ms.date: 03/30/2017
ms.assetid: f2ed3774-78b9-4a15-b79b-655f1ad68b86
ms.openlocfilehash: 79c3c68d69bf3cf5a018e6cf62f34e5ec2ce0cd5
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/07/2019
ms.locfileid: "73738937"
---
# <a name="mexhttpsbinding"></a><span data-ttu-id="0934b-101">\<mexHttpsBinding ></span><span class="sxs-lookup"><span data-stu-id="0934b-101">\<mexHttpsBinding></span></span>
<span data-ttu-id="0934b-102">Spécifie les paramètres pour une liaison utilisée dans le cadre de l’échange de messages WS-MetadataExchange (WS-MEX) sur HTTPS.</span><span class="sxs-lookup"><span data-stu-id="0934b-102">Specifies the settings for a binding used for the WS-MetadataExchange (WS-MEX) message exchange over HTTPS.</span></span>  
  
<span data-ttu-id="0934b-103">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="0934b-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="0934b-104">&nbsp; &nbsp;[ **\<system. serviceModel >** ](system-servicemodel.md) </span><span class="sxs-lookup"><span data-stu-id="0934b-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="0934b-105">&nbsp;&nbsp;&nbsp;&nbsp;[**liaisons**](bindings.md)\<</span><span class="sxs-lookup"><span data-stu-id="0934b-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\</span></span>
<span data-ttu-id="0934b-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;\<**mexHttpsBinding >**</span><span class="sxs-lookup"><span data-stu-id="0934b-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<mexHttpsBinding>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0934b-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0934b-107">Syntax</span></span>  
  
```xml  
<mexHttpsBinding>
  <binding closeTimeout="TimeSpan"
            name="string"
            openTimeout="TimeSpan"
            receiveTimeout="TimeSpan"
            sendTimeout="TimeSpan">
  </binding>
</mexHttpsBinding>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="0934b-108">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="0934b-108">Attributes and Elements</span></span>  
 <span data-ttu-id="0934b-109">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="0934b-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="0934b-110">Attributs</span><span class="sxs-lookup"><span data-stu-id="0934b-110">Attributes</span></span>  
  
|<span data-ttu-id="0934b-111">Attribut</span><span class="sxs-lookup"><span data-stu-id="0934b-111">Attribute</span></span>|<span data-ttu-id="0934b-112">Description</span><span class="sxs-lookup"><span data-stu-id="0934b-112">Description</span></span>|  
|---------------|-----------------|  
|`closeTimeout`|<span data-ttu-id="0934b-113"><xref:System.TimeSpan> qui spécifie l'intervalle de temps prévu pour la réalisation d'une opération de fermeture.</span><span class="sxs-lookup"><span data-stu-id="0934b-113">A <xref:System.TimeSpan> value that specifies the interval of time provided for a close operation to complete.</span></span> <span data-ttu-id="0934b-114">Cette valeur doit être supérieure ou égale à <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="0934b-114">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="0934b-115">La valeur par défaut est 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="0934b-115">The default is 00:01:00.</span></span>|  
|`name`|<span data-ttu-id="0934b-116">Chaîne qui contient le nom de configuration de la liaison.</span><span class="sxs-lookup"><span data-stu-id="0934b-116">A string that contains the configuration name of the binding.</span></span> <span data-ttu-id="0934b-117">Cette valeur doit être unique car elle permet d'identifier la liaison.</span><span class="sxs-lookup"><span data-stu-id="0934b-117">This value should be unique because it is used as an identification for the binding.</span></span> <span data-ttu-id="0934b-118">Chaque liaison porte un `name` et a un attribut `namespace` qui l’identifient de façon unique dans les métadonnées du service.</span><span class="sxs-lookup"><span data-stu-id="0934b-118">Each binding has a `name` and `namespace` attribute that together uniquely identify it in the metadata of the service.</span></span> <span data-ttu-id="0934b-119">De plus, ce nom est unique parmi les liaisons du même type.</span><span class="sxs-lookup"><span data-stu-id="0934b-119">In addition, this name is unique among bindings of the same type.</span></span> <span data-ttu-id="0934b-120">Depuis [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], les liaisons et les comportements ne sont pas obligés d’avoir un nom.</span><span class="sxs-lookup"><span data-stu-id="0934b-120">Starting with [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="0934b-121">Pour plus d’informations sur la configuration par défaut et les liaisons et les comportements sans valeur, consultez [configuration simplifiée](../../../wcf/simplified-configuration.md) et [configuration simplifiée pour les services WCF](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="0934b-121">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>|  
|`openTimeout`|<span data-ttu-id="0934b-122"><xref:System.TimeSpan> qui spécifie l'intervalle de temps prévu pour la réalisation d'une opération d'ouverture.</span><span class="sxs-lookup"><span data-stu-id="0934b-122">A <xref:System.TimeSpan> value that specifies the interval of time provided for an open operation to complete.</span></span> <span data-ttu-id="0934b-123">Cette valeur doit être supérieure ou égale à <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="0934b-123">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="0934b-124">La valeur par défaut est 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="0934b-124">The default is 00:01:00.</span></span>|  
|`receiveTimeout`|<span data-ttu-id="0934b-125"><xref:System.TimeSpan> qui spécifie l'intervalle de temps prévu pour la réalisation d'une opération de réception.</span><span class="sxs-lookup"><span data-stu-id="0934b-125">A <xref:System.TimeSpan> value that specifies the interval of time provided for a receive operation to complete.</span></span> <span data-ttu-id="0934b-126">Cette valeur doit être supérieure ou égale à <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="0934b-126">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="0934b-127">La valeur par défaut est 00:10:00.</span><span class="sxs-lookup"><span data-stu-id="0934b-127">The default is 00:10:00.</span></span>|  
|`sendTimeout`|<span data-ttu-id="0934b-128"><xref:System.TimeSpan> qui spécifie l'intervalle de temps prévu pour la réalisation d'une opération d'envoi.</span><span class="sxs-lookup"><span data-stu-id="0934b-128">A <xref:System.TimeSpan> value that specifies the interval of time provided for a send operation to complete.</span></span> <span data-ttu-id="0934b-129">Cette valeur doit être supérieure ou égale à <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="0934b-129">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="0934b-130">La valeur par défaut est 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="0934b-130">The default is 00:01:00.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="0934b-131">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="0934b-131">Child Elements</span></span>  
 <span data-ttu-id="0934b-132">Aucun(e).</span><span class="sxs-lookup"><span data-stu-id="0934b-132">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="0934b-133">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="0934b-133">Parent Elements</span></span>  
  
|<span data-ttu-id="0934b-134">Élément</span><span class="sxs-lookup"><span data-stu-id="0934b-134">Element</span></span>|<span data-ttu-id="0934b-135">Description</span><span class="sxs-lookup"><span data-stu-id="0934b-135">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="0934b-136">liaisons de\<</span><span class="sxs-lookup"><span data-stu-id="0934b-136">\<bindings></span></span>](bindings.md)|<span data-ttu-id="0934b-137">Cet élément conserve une collection de liaisons standard et personnalisées.</span><span class="sxs-lookup"><span data-stu-id="0934b-137">This element holds a collection of standard and custom bindings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0934b-138">Notes</span><span class="sxs-lookup"><span data-stu-id="0934b-138">Remarks</span></span>  
 <span data-ttu-id="0934b-139">Cette liaison est essentiellement une liaison `WSHttpBinding` qui prend en charge la sécurité au niveau du transport à l’aide de certificats.</span><span class="sxs-lookup"><span data-stu-id="0934b-139">This binding is essentially a `WSHttpBinding` binding that supports transport-level security using certificates.</span></span> <span data-ttu-id="0934b-140">Pour plus d’informations sur la configuration et l’utilisation de ce type de point de terminaison de métadonnées, consultez [Comment : configurer une liaison de WS-Metadata Exchange personnalisée](../../../wcf/extending/how-to-configure-a-custom-ws-metadata-exchange-binding.md), [Comment : récupérer des métadonnées sur une liaison non MEX](../../../wcf/extending/how-to-retrieve-metadata-over-a-non-mex-binding.md)et l’exemple de [point de terminaison de métadonnées sécurisé personnalisé](../../../wcf/samples/custom-secure-metadata-endpoint.md) .</span><span class="sxs-lookup"><span data-stu-id="0934b-140">For more information about configuring and using such a metadata endpoint, see [How to: Configure a Custom WS-Metadata Exchange Binding](../../../wcf/extending/how-to-configure-a-custom-ws-metadata-exchange-binding.md), [How to: Retrieve Metadata Over a non-MEX Binding](../../../wcf/extending/how-to-retrieve-metadata-over-a-non-mex-binding.md), and the sample [Custom Secure Metadata Endpoint](../../../wcf/samples/custom-secure-metadata-endpoint.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0934b-141">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="0934b-141">See also</span></span>

- <xref:System.ServiceModel.Description.MetadataExchangeBindings.CreateMexHttpsBinding%2A>
- <xref:System.ServiceModel.Configuration.MexHttpsBindingElement>
- [<span data-ttu-id="0934b-142">Guide pratique pour publier les métadonnées d’un service à l’aide d’un fichier de configuration</span><span class="sxs-lookup"><span data-stu-id="0934b-142">How to: Publish Metadata for a Service Using a Configuration File</span></span>](../../../wcf/feature-details/how-to-publish-metadata-for-a-service-using-a-configuration-file.md)
- [<span data-ttu-id="0934b-143">Publication et récupération de métadonnées sur une liaison personnalisée</span><span class="sxs-lookup"><span data-stu-id="0934b-143">Publishing and Retrieving Metadata Over a Custom Binding</span></span>](../../../wcf/extending/publishing-and-retrieving-metadata-over-a-custom-binding.md)
- [<span data-ttu-id="0934b-144">Guide pratique pour configurer une liaison WS-Metadata Exchange personnalisée</span><span class="sxs-lookup"><span data-stu-id="0934b-144">How to: Configure a Custom WS-Metadata Exchange Binding</span></span>](../../../wcf/extending/how-to-configure-a-custom-ws-metadata-exchange-binding.md)
- [<span data-ttu-id="0934b-145">Guide pratique pour récupérer des métadonnées sur une liaison non-MEX</span><span class="sxs-lookup"><span data-stu-id="0934b-145">How to: Retrieve Metadata Over a non-MEX Binding</span></span>](../../../wcf/extending/how-to-retrieve-metadata-over-a-non-mex-binding.md)
- [<span data-ttu-id="0934b-146">Point de terminaison de métadonnées sécurisé personnalisé</span><span class="sxs-lookup"><span data-stu-id="0934b-146">Custom Secure Metadata Endpoint</span></span>](../../../wcf/samples/custom-secure-metadata-endpoint.md)
- [<span data-ttu-id="0934b-147">Métadonnées</span><span class="sxs-lookup"><span data-stu-id="0934b-147">Metadata</span></span>](../../../wcf/feature-details/metadata.md)
- [<span data-ttu-id="0934b-148">Liaisons</span><span class="sxs-lookup"><span data-stu-id="0934b-148">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="0934b-149">Configuration des liaisons fournies par le système</span><span class="sxs-lookup"><span data-stu-id="0934b-149">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="0934b-150">Utilisation de liaisons pour configurer des services et des clients</span><span class="sxs-lookup"><span data-stu-id="0934b-150">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="0934b-151">liaison de \<</span><span class="sxs-lookup"><span data-stu-id="0934b-151">\<binding></span></span>](bindings.md)
