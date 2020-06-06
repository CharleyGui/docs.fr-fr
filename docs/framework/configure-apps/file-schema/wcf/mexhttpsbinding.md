---
title: <mexHttpsBinding>
ms.date: 03/30/2017
ms.assetid: f2ed3774-78b9-4a15-b79b-655f1ad68b86
ms.openlocfilehash: 924d68dd828622b74c5e424a695f80874391b453
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/06/2020
ms.locfileid: "74430342"
---
# \<mexHttpsBinding>
<span data-ttu-id="16645-101">Spécifie les paramètres pour une liaison utilisée dans le cadre de l’échange de messages WS-MetadataExchange (WS-MEX) sur HTTPS.</span><span class="sxs-lookup"><span data-stu-id="16645-101">Specifies the settings for a binding used for the WS-MetadataExchange (WS-MEX) message exchange over HTTPS.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<mexHttpsBinding>**  
  
## <a name="syntax"></a><span data-ttu-id="16645-102">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="16645-102">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="16645-103">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="16645-103">Attributes and Elements</span></span>  
 <span data-ttu-id="16645-104">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="16645-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="16645-105">Attributs</span><span class="sxs-lookup"><span data-stu-id="16645-105">Attributes</span></span>  
  
|<span data-ttu-id="16645-106">Attribut</span><span class="sxs-lookup"><span data-stu-id="16645-106">Attribute</span></span>|<span data-ttu-id="16645-107">Description</span><span class="sxs-lookup"><span data-stu-id="16645-107">Description</span></span>|  
|---------------|-----------------|  
|`closeTimeout`|<span data-ttu-id="16645-108"><xref:System.TimeSpan> qui spécifie l'intervalle de temps prévu pour la réalisation d'une opération de fermeture.</span><span class="sxs-lookup"><span data-stu-id="16645-108">A <xref:System.TimeSpan> value that specifies the interval of time provided for a close operation to complete.</span></span> <span data-ttu-id="16645-109">Cette valeur doit être supérieure ou égale à <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="16645-109">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="16645-110">La valeur par défaut est 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="16645-110">The default is 00:01:00.</span></span>|  
|`name`|<span data-ttu-id="16645-111">Chaîne qui contient le nom de configuration de la liaison.</span><span class="sxs-lookup"><span data-stu-id="16645-111">A string that contains the configuration name of the binding.</span></span> <span data-ttu-id="16645-112">Cette valeur doit être unique car elle permet d'identifier la liaison.</span><span class="sxs-lookup"><span data-stu-id="16645-112">This value should be unique because it is used as an identification for the binding.</span></span> <span data-ttu-id="16645-113">À compter de .NET Framework 4, les liaisons et les comportements n’ont pas besoin d’un nom.</span><span class="sxs-lookup"><span data-stu-id="16645-113">Starting with .NET Framework 4, bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="16645-114">Pour plus d’informations sur la configuration par défaut et les liaisons et les comportements sans valeur, consultez [configuration simplifiée](../../../wcf/simplified-configuration.md) et [configuration simplifiée pour les services WCF](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="16645-114">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>|  
|`openTimeout`|<span data-ttu-id="16645-115"><xref:System.TimeSpan> qui spécifie l'intervalle de temps prévu pour la réalisation d'une opération d'ouverture.</span><span class="sxs-lookup"><span data-stu-id="16645-115">A <xref:System.TimeSpan> value that specifies the interval of time provided for an open operation to complete.</span></span> <span data-ttu-id="16645-116">Cette valeur doit être supérieure ou égale à <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="16645-116">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="16645-117">La valeur par défaut est 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="16645-117">The default is 00:01:00.</span></span>|  
|`receiveTimeout`|<span data-ttu-id="16645-118"><xref:System.TimeSpan> qui spécifie l'intervalle de temps prévu pour la réalisation d'une opération de réception.</span><span class="sxs-lookup"><span data-stu-id="16645-118">A <xref:System.TimeSpan> value that specifies the interval of time provided for a receive operation to complete.</span></span> <span data-ttu-id="16645-119">Cette valeur doit être supérieure ou égale à <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="16645-119">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="16645-120">La valeur par défaut est 00:10:00.</span><span class="sxs-lookup"><span data-stu-id="16645-120">The default is 00:10:00.</span></span>|  
|`sendTimeout`|<span data-ttu-id="16645-121"><xref:System.TimeSpan> qui spécifie l'intervalle de temps prévu pour la réalisation d'une opération d'envoi.</span><span class="sxs-lookup"><span data-stu-id="16645-121">A <xref:System.TimeSpan> value that specifies the interval of time provided for a send operation to complete.</span></span> <span data-ttu-id="16645-122">Cette valeur doit être supérieure ou égale à <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="16645-122">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="16645-123">La valeur par défaut est 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="16645-123">The default is 00:01:00.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="16645-124">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="16645-124">Child Elements</span></span>  
 <span data-ttu-id="16645-125">Aucun.</span><span class="sxs-lookup"><span data-stu-id="16645-125">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="16645-126">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="16645-126">Parent Elements</span></span>  
  
|<span data-ttu-id="16645-127">Élément</span><span class="sxs-lookup"><span data-stu-id="16645-127">Element</span></span>|<span data-ttu-id="16645-128">Description</span><span class="sxs-lookup"><span data-stu-id="16645-128">Description</span></span>|  
|-------------|-----------------|  
|[\<bindings>](bindings.md)|<span data-ttu-id="16645-129">Cet élément conserve une collection de liaisons standard et personnalisées.</span><span class="sxs-lookup"><span data-stu-id="16645-129">This element holds a collection of standard and custom bindings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="16645-130">Remarques</span><span class="sxs-lookup"><span data-stu-id="16645-130">Remarks</span></span>  
 <span data-ttu-id="16645-131">Cette liaison est essentiellement une liaison `WSHttpBinding` qui prend en charge la sécurité au niveau du transport à l’aide de certificats.</span><span class="sxs-lookup"><span data-stu-id="16645-131">This binding is essentially a `WSHttpBinding` binding that supports transport-level security using certificates.</span></span> <span data-ttu-id="16645-132">Pour plus d’informations sur la configuration et l’utilisation d’un tel point de terminaison de métadonnées, consultez [Comment : configurer une liaison de WS-Metadata Exchange personnalisée](../../../wcf/extending/how-to-configure-a-custom-ws-metadata-exchange-binding.md), [Comment : récupérer des métadonnées sur une liaison non MEX](../../../wcf/extending/how-to-retrieve-metadata-over-a-non-mex-binding.md)et l’exemple de [point de terminaison de métadonnées sécurisé personnalisé](../../../wcf/samples/custom-secure-metadata-endpoint.md).</span><span class="sxs-lookup"><span data-stu-id="16645-132">For more information about configuring and using such a metadata endpoint, see [How to: Configure a Custom WS-Metadata Exchange Binding](../../../wcf/extending/how-to-configure-a-custom-ws-metadata-exchange-binding.md), [How to: Retrieve Metadata Over a non-MEX Binding](../../../wcf/extending/how-to-retrieve-metadata-over-a-non-mex-binding.md), and the sample [Custom Secure Metadata Endpoint](../../../wcf/samples/custom-secure-metadata-endpoint.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="16645-133">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="16645-133">See also</span></span>

- <xref:System.ServiceModel.Description.MetadataExchangeBindings.CreateMexHttpsBinding%2A>
- <xref:System.ServiceModel.Configuration.MexHttpsBindingElement>
- [<span data-ttu-id="16645-134">Comment : publier les métadonnées d'un service à l'aide d'un fichier de configuration</span><span class="sxs-lookup"><span data-stu-id="16645-134">How to: Publish Metadata for a Service Using a Configuration File</span></span>](../../../wcf/feature-details/how-to-publish-metadata-for-a-service-using-a-configuration-file.md)
- [<span data-ttu-id="16645-135">Publication et récupération de métadonnées sur une liaison personnalisée</span><span class="sxs-lookup"><span data-stu-id="16645-135">Publishing and Retrieving Metadata Over a Custom Binding</span></span>](../../../wcf/extending/publishing-and-retrieving-metadata-over-a-custom-binding.md)
- [<span data-ttu-id="16645-136">Guide pratique pour configurer une liaison WS-Metadata Exchange personnalisée</span><span class="sxs-lookup"><span data-stu-id="16645-136">How to: Configure a Custom WS-Metadata Exchange Binding</span></span>](../../../wcf/extending/how-to-configure-a-custom-ws-metadata-exchange-binding.md)
- [<span data-ttu-id="16645-137">Procédure : récupérer des métadonnées sur une liaison non-MEX</span><span class="sxs-lookup"><span data-stu-id="16645-137">How to: Retrieve Metadata Over a non-MEX Binding</span></span>](../../../wcf/extending/how-to-retrieve-metadata-over-a-non-mex-binding.md)
- [<span data-ttu-id="16645-138">Point de terminaison de métadonnées sécurisé personnalisée</span><span class="sxs-lookup"><span data-stu-id="16645-138">Custom Secure Metadata Endpoint</span></span>](../../../wcf/samples/custom-secure-metadata-endpoint.md)
- [<span data-ttu-id="16645-139">Métadonnées</span><span class="sxs-lookup"><span data-stu-id="16645-139">Metadata</span></span>](../../../wcf/feature-details/metadata.md)
- [<span data-ttu-id="16645-140">Liaisons</span><span class="sxs-lookup"><span data-stu-id="16645-140">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="16645-141">Configuration des liaisons fournies par le système</span><span class="sxs-lookup"><span data-stu-id="16645-141">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="16645-142">Utilisation de liaisons pour configurer des services et des clients</span><span class="sxs-lookup"><span data-stu-id="16645-142">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](bindings.md)
