---
title: <mexHttpsBinding>
ms.date: 03/30/2017
ms.assetid: f2ed3774-78b9-4a15-b79b-655f1ad68b86
ms.openlocfilehash: 30d1aa27ce29b6aa4091c3e7be05746ad462102a
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69931268"
---
# <a name="mexhttpsbinding"></a><span data-ttu-id="4940e-101">\<mexHttpsBinding></span><span class="sxs-lookup"><span data-stu-id="4940e-101">\<mexHttpsBinding></span></span>
<span data-ttu-id="4940e-102">Spécifie les paramètres pour une liaison utilisée dans le cadre de l’échange de messages WS-MetadataExchange (WS-MEX) sur HTTPS.</span><span class="sxs-lookup"><span data-stu-id="4940e-102">Specifies the settings for a binding used for the WS-MetadataExchange (WS-MEX) message exchange over HTTPS.</span></span>  
  
 <span data-ttu-id="4940e-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="4940e-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="4940e-104">\<bindings></span><span class="sxs-lookup"><span data-stu-id="4940e-104">\<bindings></span></span>  
<span data-ttu-id="4940e-105">\<mexHttpsBinding></span><span class="sxs-lookup"><span data-stu-id="4940e-105">\<mexHttpsBinding></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4940e-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4940e-106">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="4940e-107">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="4940e-107">Attributes and Elements</span></span>  
 <span data-ttu-id="4940e-108">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="4940e-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="4940e-109">Attributs</span><span class="sxs-lookup"><span data-stu-id="4940e-109">Attributes</span></span>  
  
|<span data-ttu-id="4940e-110">Attribut</span><span class="sxs-lookup"><span data-stu-id="4940e-110">Attribute</span></span>|<span data-ttu-id="4940e-111">Description</span><span class="sxs-lookup"><span data-stu-id="4940e-111">Description</span></span>|  
|---------------|-----------------|  
|`closeTimeout`|<span data-ttu-id="4940e-112"><xref:System.TimeSpan> qui spécifie l'intervalle de temps prévu pour la réalisation d'une opération de fermeture.</span><span class="sxs-lookup"><span data-stu-id="4940e-112">A <xref:System.TimeSpan> value that specifies the interval of time provided for a close operation to complete.</span></span> <span data-ttu-id="4940e-113">Cette valeur doit être supérieure ou égale à <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="4940e-113">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="4940e-114">La valeur par défaut est 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="4940e-114">The default is 00:01:00.</span></span>|  
|`name`|<span data-ttu-id="4940e-115">Chaîne qui contient le nom de configuration de la liaison.</span><span class="sxs-lookup"><span data-stu-id="4940e-115">A string that contains the configuration name of the binding.</span></span> <span data-ttu-id="4940e-116">Cette valeur doit être unique car elle permet d'identifier la liaison.</span><span class="sxs-lookup"><span data-stu-id="4940e-116">This value should be unique because it is used as an identification for the binding.</span></span> <span data-ttu-id="4940e-117">Chaque liaison porte un `name` et a un attribut `namespace` qui l’identifient de façon unique dans les métadonnées du service.</span><span class="sxs-lookup"><span data-stu-id="4940e-117">Each binding has a `name` and `namespace` attribute that together uniquely identify it in the metadata of the service.</span></span> <span data-ttu-id="4940e-118">De plus, ce nom est unique parmi les liaisons du même type.</span><span class="sxs-lookup"><span data-stu-id="4940e-118">In addition, this name is unique among bindings of the same type.</span></span> <span data-ttu-id="4940e-119">Depuis [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], les liaisons et les comportements ne sont pas obligés d’avoir un nom.</span><span class="sxs-lookup"><span data-stu-id="4940e-119">Starting with [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="4940e-120">Pour plus d’informations sur la configuration par défaut et les liaisons et les comportements sans valeur, consultez [configuration simplifiée](../../../wcf/simplified-configuration.md) et [configuration simplifiée pour les services WCF](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="4940e-120">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>|  
|`openTimeout`|<span data-ttu-id="4940e-121"><xref:System.TimeSpan> qui spécifie l'intervalle de temps prévu pour la réalisation d'une opération d'ouverture.</span><span class="sxs-lookup"><span data-stu-id="4940e-121">A <xref:System.TimeSpan> value that specifies the interval of time provided for an open operation to complete.</span></span> <span data-ttu-id="4940e-122">Cette valeur doit être supérieure ou égale à <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="4940e-122">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="4940e-123">La valeur par défaut est 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="4940e-123">The default is 00:01:00.</span></span>|  
|`receiveTimeout`|<span data-ttu-id="4940e-124"><xref:System.TimeSpan> qui spécifie l'intervalle de temps prévu pour la réalisation d'une opération de réception.</span><span class="sxs-lookup"><span data-stu-id="4940e-124">A <xref:System.TimeSpan> value that specifies the interval of time provided for a receive operation to complete.</span></span> <span data-ttu-id="4940e-125">Cette valeur doit être supérieure ou égale à <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="4940e-125">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="4940e-126">La valeur par défaut est 00:10:00.</span><span class="sxs-lookup"><span data-stu-id="4940e-126">The default is 00:10:00.</span></span>|  
|`sendTimeout`|<span data-ttu-id="4940e-127"><xref:System.TimeSpan> qui spécifie l'intervalle de temps prévu pour la réalisation d'une opération d'envoi.</span><span class="sxs-lookup"><span data-stu-id="4940e-127">A <xref:System.TimeSpan> value that specifies the interval of time provided for a send operation to complete.</span></span> <span data-ttu-id="4940e-128">Cette valeur doit être supérieure ou égale à <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="4940e-128">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="4940e-129">La valeur par défaut est 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="4940e-129">The default is 00:01:00.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="4940e-130">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="4940e-130">Child Elements</span></span>  
 <span data-ttu-id="4940e-131">Aucun.</span><span class="sxs-lookup"><span data-stu-id="4940e-131">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="4940e-132">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="4940e-132">Parent Elements</span></span>  
  
|<span data-ttu-id="4940e-133">Élément</span><span class="sxs-lookup"><span data-stu-id="4940e-133">Element</span></span>|<span data-ttu-id="4940e-134">Description</span><span class="sxs-lookup"><span data-stu-id="4940e-134">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="4940e-135">\<bindings></span><span class="sxs-lookup"><span data-stu-id="4940e-135">\<bindings></span></span>](bindings.md)|<span data-ttu-id="4940e-136">Cet élément conserve une collection de liaisons standard et personnalisées.</span><span class="sxs-lookup"><span data-stu-id="4940e-136">This element holds a collection of standard and custom bindings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4940e-137">Notes</span><span class="sxs-lookup"><span data-stu-id="4940e-137">Remarks</span></span>  
 <span data-ttu-id="4940e-138">Cette liaison est essentiellement une liaison `WSHttpBinding` qui prend en charge la sécurité au niveau du transport à l’aide de certificats.</span><span class="sxs-lookup"><span data-stu-id="4940e-138">This binding is essentially a `WSHttpBinding` binding that supports transport-level security using certificates.</span></span> <span data-ttu-id="4940e-139">Pour plus d’informations sur la configuration et l’utilisation de ce type de [point de terminaison de métadonnées, consultez Procédure: Configurer une liaison](../../../wcf/extending/how-to-configure-a-custom-ws-metadata-exchange-binding.md)de WS-Metadata Exchange personnalisée [, procédure: Récupérez les métadonnées sur une liaison](../../../wcf/extending/how-to-retrieve-metadata-over-a-non-mex-binding.md)non MEX et l’exemple de [point de terminaison de métadonnées sécurisé personnalisé](../../../wcf/samples/custom-secure-metadata-endpoint.md).</span><span class="sxs-lookup"><span data-stu-id="4940e-139">For more information about configuring and using such a metadata endpoint, see [How to: Configure a Custom WS-Metadata Exchange Binding](../../../wcf/extending/how-to-configure-a-custom-ws-metadata-exchange-binding.md), [How to: Retrieve Metadata Over a non-MEX Binding](../../../wcf/extending/how-to-retrieve-metadata-over-a-non-mex-binding.md), and the sample [Custom Secure Metadata Endpoint](../../../wcf/samples/custom-secure-metadata-endpoint.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4940e-140">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4940e-140">See also</span></span>

- <xref:System.ServiceModel.Description.MetadataExchangeBindings.CreateMexHttpsBinding%2A>
- <xref:System.ServiceModel.Configuration.MexHttpsBindingElement>
- [<span data-ttu-id="4940e-141">Guide pratique pour Publier les métadonnées d’un service à l’aide d’un fichier de configuration</span><span class="sxs-lookup"><span data-stu-id="4940e-141">How to: Publish Metadata for a Service Using a Configuration File</span></span>](../../../wcf/feature-details/how-to-publish-metadata-for-a-service-using-a-configuration-file.md)
- [<span data-ttu-id="4940e-142">Publication et récupération de métadonnées sur une liaison personnalisée</span><span class="sxs-lookup"><span data-stu-id="4940e-142">Publishing and Retrieving Metadata Over a Custom Binding</span></span>](../../../wcf/extending/publishing-and-retrieving-metadata-over-a-custom-binding.md)
- [<span data-ttu-id="4940e-143">Guide pratique : Configurer une liaison d’échange WS-Metadata personnalisée</span><span class="sxs-lookup"><span data-stu-id="4940e-143">How to: Configure a Custom WS-Metadata Exchange Binding</span></span>](../../../wcf/extending/how-to-configure-a-custom-ws-metadata-exchange-binding.md)
- [<span data-ttu-id="4940e-144">Guide pratique pour Récupérer des métadonnées sur une liaison non MEX</span><span class="sxs-lookup"><span data-stu-id="4940e-144">How to: Retrieve Metadata Over a non-MEX Binding</span></span>](../../../wcf/extending/how-to-retrieve-metadata-over-a-non-mex-binding.md)
- [<span data-ttu-id="4940e-145">Point de terminaison de métadonnées sécurisé personnalisé</span><span class="sxs-lookup"><span data-stu-id="4940e-145">Custom Secure Metadata Endpoint</span></span>](../../../wcf/samples/custom-secure-metadata-endpoint.md)
- [<span data-ttu-id="4940e-146">Métadonnées</span><span class="sxs-lookup"><span data-stu-id="4940e-146">Metadata</span></span>](../../../wcf/feature-details/metadata.md)
- [<span data-ttu-id="4940e-147">Liaisons</span><span class="sxs-lookup"><span data-stu-id="4940e-147">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="4940e-148">Configuration des liaisons fournies par le système</span><span class="sxs-lookup"><span data-stu-id="4940e-148">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="4940e-149">Utilisation de liaisons pour configurer des services et des clients</span><span class="sxs-lookup"><span data-stu-id="4940e-149">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="4940e-150">\<binding></span><span class="sxs-lookup"><span data-stu-id="4940e-150">\<binding></span></span>](../../../misc/binding.md)
