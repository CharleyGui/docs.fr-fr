---
title: <mexTcpBinding>
ms.date: 03/30/2017
ms.assetid: 01baba8d-d784-4255-9ea2-7afff1482bf0
ms.openlocfilehash: 8d0ae2a1848eaf28c2e408542b8209cf968de4c1
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/06/2020
ms.locfileid: "74430304"
---
# \<mexTcpBinding>
<span data-ttu-id="6a76a-101">Spécifie les paramètres pour une liaison utilisée dans le cadre de l’échange de messages WS-MetadataExchange (WS-MEX) sur TCP.</span><span class="sxs-lookup"><span data-stu-id="6a76a-101">Specifies the settings for a binding used for the WS-MetadataExchange (WS-MEX) message exchange over TCP.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<mexTcpBinding>**  
  
## <a name="syntax"></a><span data-ttu-id="6a76a-102">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6a76a-102">Syntax</span></span>  
  
```xml  
<mexTcpBinding>
  <binding closeTimeout="TimeSpan"
           name="string"
           openTimeout="TimeSpan"
           receiveTimeout="TimeSpan"
           sendTimeout="TimeSpan">
  </binding>
</mexTcpBinding>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="6a76a-103">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="6a76a-103">Attributes and Elements</span></span>  
 <span data-ttu-id="6a76a-104">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="6a76a-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="6a76a-105">Attributs</span><span class="sxs-lookup"><span data-stu-id="6a76a-105">Attributes</span></span>  
  
|<span data-ttu-id="6a76a-106">Attribut</span><span class="sxs-lookup"><span data-stu-id="6a76a-106">Attribute</span></span>|<span data-ttu-id="6a76a-107">Description</span><span class="sxs-lookup"><span data-stu-id="6a76a-107">Description</span></span>|  
|---------------|-----------------|  
|`closeTimeout`|<span data-ttu-id="6a76a-108"><xref:System.TimeSpan> qui spécifie l'intervalle de temps prévu pour la réalisation d'une opération de fermeture.</span><span class="sxs-lookup"><span data-stu-id="6a76a-108">A <xref:System.TimeSpan> value that specifies the interval of time provided for a close operation to complete.</span></span> <span data-ttu-id="6a76a-109">Cette valeur doit être supérieure ou égale à <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="6a76a-109">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="6a76a-110">La valeur par défaut est 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="6a76a-110">The default is 00:01:00.</span></span>|  
|`name`|<span data-ttu-id="6a76a-111">Chaîne qui contient le nom de configuration de la liaison.</span><span class="sxs-lookup"><span data-stu-id="6a76a-111">A string that contains the configuration name of the binding.</span></span> <span data-ttu-id="6a76a-112">Cette valeur doit être unique car elle permet d'identifier la liaison.</span><span class="sxs-lookup"><span data-stu-id="6a76a-112">This value should be unique because it is used as an identification for the binding.</span></span> <span data-ttu-id="6a76a-113">À compter de .NET Framework 4, les liaisons et les comportements n’ont pas besoin d’un nom.</span><span class="sxs-lookup"><span data-stu-id="6a76a-113">Starting with .NET Framework 4, bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="6a76a-114">Pour plus d’informations sur la configuration par défaut et les liaisons et les comportements sans valeur, consultez [configuration simplifiée](../../../wcf/simplified-configuration.md) et [configuration simplifiée pour les services WCF](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="6a76a-114">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>|  
|`openTimeout`|<span data-ttu-id="6a76a-115"><xref:System.TimeSpan> qui spécifie l'intervalle de temps prévu pour la réalisation d'une opération d'ouverture.</span><span class="sxs-lookup"><span data-stu-id="6a76a-115">A <xref:System.TimeSpan> value that specifies the interval of time provided for an open operation to complete.</span></span> <span data-ttu-id="6a76a-116">Cette valeur doit être supérieure ou égale à <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="6a76a-116">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="6a76a-117">La valeur par défaut est 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="6a76a-117">The default is 00:01:00.</span></span>|  
|`receiveTimeout`|<span data-ttu-id="6a76a-118"><xref:System.TimeSpan> qui spécifie l'intervalle de temps prévu pour la réalisation d'une opération de réception.</span><span class="sxs-lookup"><span data-stu-id="6a76a-118">A <xref:System.TimeSpan> value that specifies the interval of time provided for a receive operation to complete.</span></span> <span data-ttu-id="6a76a-119">Cette valeur doit être supérieure ou égale à <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="6a76a-119">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="6a76a-120">La valeur par défaut est 00:10:00.</span><span class="sxs-lookup"><span data-stu-id="6a76a-120">The default is 00:10:00.</span></span>|  
|`sendTimeout`|<span data-ttu-id="6a76a-121"><xref:System.TimeSpan> qui spécifie l'intervalle de temps prévu pour la réalisation d'une opération d'envoi.</span><span class="sxs-lookup"><span data-stu-id="6a76a-121">A <xref:System.TimeSpan> value that specifies the interval of time provided for a send operation to complete.</span></span> <span data-ttu-id="6a76a-122">Cette valeur doit être supérieure ou égale à <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="6a76a-122">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="6a76a-123">La valeur par défaut est 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="6a76a-123">The default is 00:01:00.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="6a76a-124">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="6a76a-124">Child Elements</span></span>  
 <span data-ttu-id="6a76a-125">Aucun.</span><span class="sxs-lookup"><span data-stu-id="6a76a-125">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="6a76a-126">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="6a76a-126">Parent Elements</span></span>  
  
|<span data-ttu-id="6a76a-127">Élément</span><span class="sxs-lookup"><span data-stu-id="6a76a-127">Element</span></span>|<span data-ttu-id="6a76a-128">Description</span><span class="sxs-lookup"><span data-stu-id="6a76a-128">Description</span></span>|  
|-------------|-----------------|  
|[\<bindings>](bindings.md)|<span data-ttu-id="6a76a-129">Cet élément conserve une collection de liaisons standard et personnalisées.</span><span class="sxs-lookup"><span data-stu-id="6a76a-129">This element holds a collection of standard and custom bindings.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="6a76a-130">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="6a76a-130">See also</span></span>

- <xref:System.ServiceModel.Configuration.MexTcpBindingElement>
- <xref:System.ServiceModel.Description.MetadataExchangeBindings.CreateMexTcpBinding%2A>
- [<span data-ttu-id="6a76a-131">Comment : publier les métadonnées d'un service à l'aide d'un fichier de configuration</span><span class="sxs-lookup"><span data-stu-id="6a76a-131">How to: Publish Metadata for a Service Using a Configuration File</span></span>](../../../wcf/feature-details/how-to-publish-metadata-for-a-service-using-a-configuration-file.md)
- [<span data-ttu-id="6a76a-132">Publication et récupération de métadonnées sur une liaison personnalisée</span><span class="sxs-lookup"><span data-stu-id="6a76a-132">Publishing and Retrieving Metadata Over a Custom Binding</span></span>](../../../wcf/extending/publishing-and-retrieving-metadata-over-a-custom-binding.md)
- [<span data-ttu-id="6a76a-133">Métadonnées</span><span class="sxs-lookup"><span data-stu-id="6a76a-133">Metadata</span></span>](../../../wcf/feature-details/metadata.md)
- [<span data-ttu-id="6a76a-134">Liaisons</span><span class="sxs-lookup"><span data-stu-id="6a76a-134">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="6a76a-135">Configuration des liaisons fournies par le système</span><span class="sxs-lookup"><span data-stu-id="6a76a-135">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="6a76a-136">Utilisation de liaisons pour configurer des services et des clients</span><span class="sxs-lookup"><span data-stu-id="6a76a-136">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](bindings.md)
