---
title: <mexHttpBinding>
ms.date: 03/30/2017
ms.assetid: e50b2e1f-9668-41a5-8077-dee7abff9f0f
ms.openlocfilehash: 8d5b9378bf7769754586d0b13f742659aee18f03
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74430911"
---
# <a name="mexhttpbinding"></a><span data-ttu-id="2b353-101">\<mexHttpBinding ></span><span class="sxs-lookup"><span data-stu-id="2b353-101">\<mexHttpBinding></span></span>
<span data-ttu-id="2b353-102">Spécifie les paramètres pour une liaison utilisée dans le cadre de l’échange de messages WS-MetadataExchange (WS-MEX) sur HTTP.</span><span class="sxs-lookup"><span data-stu-id="2b353-102">Specifies the settings for a binding used for the WS-MetadataExchange (WS-MEX) message exchange over HTTP.</span></span>  
  
<span data-ttu-id="2b353-103">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="2b353-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="2b353-104">&nbsp;&nbsp;[ **\<> System. serviceModel**](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="2b353-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="2b353-105">&nbsp;&nbsp;&nbsp;&nbsp;[**liaisons**](bindings.md)\<></span><span class="sxs-lookup"><span data-stu-id="2b353-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="2b353-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;\<**mexHttpBinding >**</span><span class="sxs-lookup"><span data-stu-id="2b353-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<mexHttpBinding>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2b353-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2b353-107">Syntax</span></span>  
  
```xml  
<mexHttpBinding>
  <binding closeTimeout="TimeSpan"
           name="string"
           openTimeout="TimeSpan"
           receiveTimeout="TimeSpan"
           sendTimeout="TimeSpan">
  </binding>
</mexHttpBinding>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="2b353-108">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="2b353-108">Attributes and Elements</span></span>  
 <span data-ttu-id="2b353-109">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="2b353-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="2b353-110">Attributs</span><span class="sxs-lookup"><span data-stu-id="2b353-110">Attributes</span></span>  
  
|<span data-ttu-id="2b353-111">Attribut</span><span class="sxs-lookup"><span data-stu-id="2b353-111">Attribute</span></span>|<span data-ttu-id="2b353-112">Description</span><span class="sxs-lookup"><span data-stu-id="2b353-112">Description</span></span>|  
|---------------|-----------------|  
|`closeTimeout`|<span data-ttu-id="2b353-113"><xref:System.TimeSpan> qui spécifie l'intervalle de temps prévu pour la réalisation d'une opération de fermeture.</span><span class="sxs-lookup"><span data-stu-id="2b353-113">A <xref:System.TimeSpan> value that specifies the interval of time provided for a close operation to complete.</span></span> <span data-ttu-id="2b353-114">Cette valeur doit être supérieure ou égale à <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="2b353-114">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="2b353-115">La valeur par défaut est 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="2b353-115">The default is 00:01:00.</span></span>|  
|`name`|<span data-ttu-id="2b353-116">Chaîne qui contient le nom de configuration de la liaison.</span><span class="sxs-lookup"><span data-stu-id="2b353-116">A string that contains the configuration name of the binding.</span></span> <span data-ttu-id="2b353-117">Cette valeur doit être unique car elle permet d'identifier la liaison.</span><span class="sxs-lookup"><span data-stu-id="2b353-117">This value should be unique because it is used as an identification for the binding.</span></span> <span data-ttu-id="2b353-118">À compter de .NET Framework 4, les liaisons et les comportements n’ont pas besoin d’un nom.</span><span class="sxs-lookup"><span data-stu-id="2b353-118">Starting with .NET Framework 4, bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="2b353-119">Pour plus d’informations sur la configuration par défaut et les liaisons et les comportements sans valeur, consultez [configuration simplifiée](../../../wcf/simplified-configuration.md) et [configuration simplifiée pour les services WCF](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="2b353-119">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>|  
|`openTimeout`|<span data-ttu-id="2b353-120"><xref:System.TimeSpan> qui spécifie l'intervalle de temps prévu pour la réalisation d'une opération d'ouverture.</span><span class="sxs-lookup"><span data-stu-id="2b353-120">A <xref:System.TimeSpan> value that specifies the interval of time provided for an open operation to complete.</span></span> <span data-ttu-id="2b353-121">Cette valeur doit être supérieure ou égale à <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="2b353-121">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="2b353-122">La valeur par défaut est 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="2b353-122">The default is 00:01:00.</span></span>|  
|`receiveTimeout`|<span data-ttu-id="2b353-123"><xref:System.TimeSpan> qui spécifie l'intervalle de temps prévu pour la réalisation d'une opération de réception.</span><span class="sxs-lookup"><span data-stu-id="2b353-123">A <xref:System.TimeSpan> value that specifies the interval of time provided for a receive operation to complete.</span></span> <span data-ttu-id="2b353-124">Cette valeur doit être supérieure ou égale à <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="2b353-124">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="2b353-125">La valeur par défaut est 00:10:00.</span><span class="sxs-lookup"><span data-stu-id="2b353-125">The default is 00:10:00.</span></span>|  
|`sendTimeout`|<span data-ttu-id="2b353-126"><xref:System.TimeSpan> qui spécifie l'intervalle de temps prévu pour la réalisation d'une opération d'envoi.</span><span class="sxs-lookup"><span data-stu-id="2b353-126">A <xref:System.TimeSpan> value that specifies the interval of time provided for a send operation to complete.</span></span> <span data-ttu-id="2b353-127">Cette valeur doit être supérieure ou égale à <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="2b353-127">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="2b353-128">La valeur par défaut est 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="2b353-128">The default is 00:01:00.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="2b353-129">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="2b353-129">Child Elements</span></span>  
 <span data-ttu-id="2b353-130">None.</span><span class="sxs-lookup"><span data-stu-id="2b353-130">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="2b353-131">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="2b353-131">Parent Elements</span></span>  
  
|<span data-ttu-id="2b353-132">Élément</span><span class="sxs-lookup"><span data-stu-id="2b353-132">Element</span></span>|<span data-ttu-id="2b353-133">Description</span><span class="sxs-lookup"><span data-stu-id="2b353-133">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="2b353-134">liaisons de \<></span><span class="sxs-lookup"><span data-stu-id="2b353-134">\<bindings></span></span>](bindings.md)|<span data-ttu-id="2b353-135">Cet élément conserve une collection de liaisons standard et personnalisées.</span><span class="sxs-lookup"><span data-stu-id="2b353-135">This element holds a collection of standard and custom bindings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2b353-136">Notes</span><span class="sxs-lookup"><span data-stu-id="2b353-136">Remarks</span></span>  
 <span data-ttu-id="2b353-137">Cette liaison est essentiellement une liaison `WSHttpBinding` dont la sécurité est désactivée.</span><span class="sxs-lookup"><span data-stu-id="2b353-137">This binding is essentially a `WSHttpBinding` binding with security disabled.</span></span> <span data-ttu-id="2b353-138">Elle prend en charge la plupart des demandes de métadonnées.</span><span class="sxs-lookup"><span data-stu-id="2b353-138">It supports most metadata requests.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2b353-139">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2b353-139">See also</span></span>

- <xref:System.ServiceModel.Description.MetadataExchangeBindings.CreateMexHttpBinding%2A>
- <xref:System.ServiceModel.Configuration.MexHttpBindingElement>
- [<span data-ttu-id="2b353-140">Guide pratique pour publier les métadonnées d’un service à l’aide d’un fichier de configuration</span><span class="sxs-lookup"><span data-stu-id="2b353-140">How to: Publish Metadata for a Service Using a Configuration File</span></span>](../../../wcf/feature-details/how-to-publish-metadata-for-a-service-using-a-configuration-file.md)
- [<span data-ttu-id="2b353-141">Publication et récupération de métadonnées sur une liaison personnalisée</span><span class="sxs-lookup"><span data-stu-id="2b353-141">Publishing and Retrieving Metadata Over a Custom Binding</span></span>](../../../wcf/extending/publishing-and-retrieving-metadata-over-a-custom-binding.md)
- [<span data-ttu-id="2b353-142">Métadonnées</span><span class="sxs-lookup"><span data-stu-id="2b353-142">Metadata</span></span>](../../../wcf/feature-details/metadata.md)
- [<span data-ttu-id="2b353-143">Liaisons</span><span class="sxs-lookup"><span data-stu-id="2b353-143">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="2b353-144">Configuration des liaisons fournies par le système</span><span class="sxs-lookup"><span data-stu-id="2b353-144">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="2b353-145">Utilisation de liaisons pour configurer des services et des clients</span><span class="sxs-lookup"><span data-stu-id="2b353-145">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="2b353-146">liaison de \<></span><span class="sxs-lookup"><span data-stu-id="2b353-146">\<binding></span></span>](bindings.md)
