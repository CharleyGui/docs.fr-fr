---
title: <mexHttpsBinding>
ms.date: 03/30/2017
ms.assetid: f2ed3774-78b9-4a15-b79b-655f1ad68b86
ms.openlocfilehash: 924d68dd828622b74c5e424a695f80874391b453
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74430342"
---
# <a name="mexhttpsbinding"></a><span data-ttu-id="d4a8b-101">\<mexHttpsBinding></span><span class="sxs-lookup"><span data-stu-id="d4a8b-101">\<mexHttpsBinding></span></span>
<span data-ttu-id="d4a8b-102">Spécifie les paramètres pour une liaison utilisée dans le cadre de l’échange de messages WS-MetadataExchange (WS-MEX) sur HTTPS.</span><span class="sxs-lookup"><span data-stu-id="d4a8b-102">Specifies the settings for a binding used for the WS-MetadataExchange (WS-MEX) message exchange over HTTPS.</span></span>  
  
<span data-ttu-id="d4a8b-103">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="d4a8b-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="d4a8b-104">&nbsp;&nbsp;[ **\<system.serviceModel>** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="d4a8b-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="d4a8b-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<bindings>** ](bindings.md)</span><span class="sxs-lookup"><span data-stu-id="d4a8b-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="d4a8b-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<mexHttpsBinding>**</span><span class="sxs-lookup"><span data-stu-id="d4a8b-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<mexHttpsBinding>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d4a8b-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d4a8b-107">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d4a8b-108">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="d4a8b-108">Attributes and Elements</span></span>  
 <span data-ttu-id="d4a8b-109">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="d4a8b-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d4a8b-110">Attributs</span><span class="sxs-lookup"><span data-stu-id="d4a8b-110">Attributes</span></span>  
  
|<span data-ttu-id="d4a8b-111">Attribut</span><span class="sxs-lookup"><span data-stu-id="d4a8b-111">Attribute</span></span>|<span data-ttu-id="d4a8b-112">Description</span><span class="sxs-lookup"><span data-stu-id="d4a8b-112">Description</span></span>|  
|---------------|-----------------|  
|`closeTimeout`|<span data-ttu-id="d4a8b-113"><xref:System.TimeSpan> qui spécifie l'intervalle de temps prévu pour la réalisation d'une opération de fermeture.</span><span class="sxs-lookup"><span data-stu-id="d4a8b-113">A <xref:System.TimeSpan> value that specifies the interval of time provided for a close operation to complete.</span></span> <span data-ttu-id="d4a8b-114">Cette valeur doit être supérieure ou égale à <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="d4a8b-114">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="d4a8b-115">La valeur par défaut est 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="d4a8b-115">The default is 00:01:00.</span></span>|  
|`name`|<span data-ttu-id="d4a8b-116">Chaîne qui contient le nom de configuration de la liaison.</span><span class="sxs-lookup"><span data-stu-id="d4a8b-116">A string that contains the configuration name of the binding.</span></span> <span data-ttu-id="d4a8b-117">Cette valeur doit être unique car elle permet d'identifier la liaison.</span><span class="sxs-lookup"><span data-stu-id="d4a8b-117">This value should be unique because it is used as an identification for the binding.</span></span> <span data-ttu-id="d4a8b-118">Starting with .NET Framework 4, bindings and behaviors are not required to have a name.</span><span class="sxs-lookup"><span data-stu-id="d4a8b-118">Starting with .NET Framework 4, bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="d4a8b-119">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="d4a8b-119">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>|  
|`openTimeout`|<span data-ttu-id="d4a8b-120"><xref:System.TimeSpan> qui spécifie l'intervalle de temps prévu pour la réalisation d'une opération d'ouverture.</span><span class="sxs-lookup"><span data-stu-id="d4a8b-120">A <xref:System.TimeSpan> value that specifies the interval of time provided for an open operation to complete.</span></span> <span data-ttu-id="d4a8b-121">Cette valeur doit être supérieure ou égale à <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="d4a8b-121">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="d4a8b-122">La valeur par défaut est 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="d4a8b-122">The default is 00:01:00.</span></span>|  
|`receiveTimeout`|<span data-ttu-id="d4a8b-123"><xref:System.TimeSpan> qui spécifie l'intervalle de temps prévu pour la réalisation d'une opération de réception.</span><span class="sxs-lookup"><span data-stu-id="d4a8b-123">A <xref:System.TimeSpan> value that specifies the interval of time provided for a receive operation to complete.</span></span> <span data-ttu-id="d4a8b-124">Cette valeur doit être supérieure ou égale à <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="d4a8b-124">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="d4a8b-125">La valeur par défaut est 00:10:00.</span><span class="sxs-lookup"><span data-stu-id="d4a8b-125">The default is 00:10:00.</span></span>|  
|`sendTimeout`|<span data-ttu-id="d4a8b-126"><xref:System.TimeSpan> qui spécifie l'intervalle de temps prévu pour la réalisation d'une opération d'envoi.</span><span class="sxs-lookup"><span data-stu-id="d4a8b-126">A <xref:System.TimeSpan> value that specifies the interval of time provided for a send operation to complete.</span></span> <span data-ttu-id="d4a8b-127">Cette valeur doit être supérieure ou égale à <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="d4a8b-127">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="d4a8b-128">La valeur par défaut est 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="d4a8b-128">The default is 00:01:00.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="d4a8b-129">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="d4a8b-129">Child Elements</span></span>  
 <span data-ttu-id="d4a8b-130">Aucun(e).</span><span class="sxs-lookup"><span data-stu-id="d4a8b-130">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="d4a8b-131">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="d4a8b-131">Parent Elements</span></span>  
  
|<span data-ttu-id="d4a8b-132">Élément</span><span class="sxs-lookup"><span data-stu-id="d4a8b-132">Element</span></span>|<span data-ttu-id="d4a8b-133">Description</span><span class="sxs-lookup"><span data-stu-id="d4a8b-133">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d4a8b-134">\<bindings></span><span class="sxs-lookup"><span data-stu-id="d4a8b-134">\<bindings></span></span>](bindings.md)|<span data-ttu-id="d4a8b-135">Cet élément conserve une collection de liaisons standard et personnalisées.</span><span class="sxs-lookup"><span data-stu-id="d4a8b-135">This element holds a collection of standard and custom bindings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d4a8b-136">Notes</span><span class="sxs-lookup"><span data-stu-id="d4a8b-136">Remarks</span></span>  
 <span data-ttu-id="d4a8b-137">Cette liaison est essentiellement une liaison `WSHttpBinding` qui prend en charge la sécurité au niveau du transport à l’aide de certificats.</span><span class="sxs-lookup"><span data-stu-id="d4a8b-137">This binding is essentially a `WSHttpBinding` binding that supports transport-level security using certificates.</span></span> <span data-ttu-id="d4a8b-138">For more information about configuring and using such a metadata endpoint, see [How to: Configure a Custom WS-Metadata Exchange Binding](../../../wcf/extending/how-to-configure-a-custom-ws-metadata-exchange-binding.md), [How to: Retrieve Metadata Over a non-MEX Binding](../../../wcf/extending/how-to-retrieve-metadata-over-a-non-mex-binding.md), and the sample [Custom Secure Metadata Endpoint](../../../wcf/samples/custom-secure-metadata-endpoint.md).</span><span class="sxs-lookup"><span data-stu-id="d4a8b-138">For more information about configuring and using such a metadata endpoint, see [How to: Configure a Custom WS-Metadata Exchange Binding](../../../wcf/extending/how-to-configure-a-custom-ws-metadata-exchange-binding.md), [How to: Retrieve Metadata Over a non-MEX Binding](../../../wcf/extending/how-to-retrieve-metadata-over-a-non-mex-binding.md), and the sample [Custom Secure Metadata Endpoint](../../../wcf/samples/custom-secure-metadata-endpoint.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d4a8b-139">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d4a8b-139">See also</span></span>

- <xref:System.ServiceModel.Description.MetadataExchangeBindings.CreateMexHttpsBinding%2A>
- <xref:System.ServiceModel.Configuration.MexHttpsBindingElement>
- [<span data-ttu-id="d4a8b-140">Guide pratique pour publier les métadonnées d’un service à l’aide d’un fichier de configuration</span><span class="sxs-lookup"><span data-stu-id="d4a8b-140">How to: Publish Metadata for a Service Using a Configuration File</span></span>](../../../wcf/feature-details/how-to-publish-metadata-for-a-service-using-a-configuration-file.md)
- [<span data-ttu-id="d4a8b-141">Publication et récupération de métadonnées sur une liaison personnalisée</span><span class="sxs-lookup"><span data-stu-id="d4a8b-141">Publishing and Retrieving Metadata Over a Custom Binding</span></span>](../../../wcf/extending/publishing-and-retrieving-metadata-over-a-custom-binding.md)
- [<span data-ttu-id="d4a8b-142">Guide pratique pour configurer une liaison WS-Metadata Exchange personnalisée</span><span class="sxs-lookup"><span data-stu-id="d4a8b-142">How to: Configure a Custom WS-Metadata Exchange Binding</span></span>](../../../wcf/extending/how-to-configure-a-custom-ws-metadata-exchange-binding.md)
- [<span data-ttu-id="d4a8b-143">Guide pratique pour récupérer des métadonnées sur une liaison non-MEX</span><span class="sxs-lookup"><span data-stu-id="d4a8b-143">How to: Retrieve Metadata Over a non-MEX Binding</span></span>](../../../wcf/extending/how-to-retrieve-metadata-over-a-non-mex-binding.md)
- [<span data-ttu-id="d4a8b-144">Point de terminaison de métadonnées sécurisé personnalisé</span><span class="sxs-lookup"><span data-stu-id="d4a8b-144">Custom Secure Metadata Endpoint</span></span>](../../../wcf/samples/custom-secure-metadata-endpoint.md)
- [<span data-ttu-id="d4a8b-145">Métadonnées</span><span class="sxs-lookup"><span data-stu-id="d4a8b-145">Metadata</span></span>](../../../wcf/feature-details/metadata.md)
- [<span data-ttu-id="d4a8b-146">Liaisons</span><span class="sxs-lookup"><span data-stu-id="d4a8b-146">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="d4a8b-147">Configuration des liaisons fournies par le système</span><span class="sxs-lookup"><span data-stu-id="d4a8b-147">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="d4a8b-148">Utilisation de liaisons pour configurer des services et des clients</span><span class="sxs-lookup"><span data-stu-id="d4a8b-148">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="d4a8b-149">\<binding></span><span class="sxs-lookup"><span data-stu-id="d4a8b-149">\<binding></span></span>](bindings.md)
