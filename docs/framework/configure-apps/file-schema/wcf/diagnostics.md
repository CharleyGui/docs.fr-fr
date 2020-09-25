---
title: <diagnostics>
ms.date: 03/30/2017
ms.assetid: 0c2f95c4-cc12-4fb5-a70c-7fc6fa95db58
ms.openlocfilehash: 775ec3a4d3dd8709c61fb46155b5085a3343d218
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91192267"
---
# \<diagnostics>

<span data-ttu-id="e7cdd-101">L'élément `diagnostics` définit des paramètres qui peuvent être utilisés par un administrateur à des fins d'inspection et de contrôle au moment de l'exécution.</span><span class="sxs-lookup"><span data-stu-id="e7cdd-101">The `diagnostics` element defines settings that can be used by an administrator for run-time inspection and control.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<diagnostics>**  
  
## <a name="syntax"></a><span data-ttu-id="e7cdd-102">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e7cdd-102">Syntax</span></span>  
  
```xml  
<system.serviceModel>
  <diagnostics etwProviderId="String"
               performanceCounters="Off/ServiceOnly/All/Default"
               wmiProviderEnabled="Boolean">
    <endToEndTracing activityTracing="Boolean"
                     messageFlowTracing="Boolean"
                     propagateActivity="Boolean" />
    <messageLogging logEntireMessage="Boolean"
                    logMalformedMessages="Boolean"
                    logMessagesAtServiceLevel="Boolean"
                    logMessagesAtTransportLevel="Boolean"
                    maxMessagesToLog="Integer"
                    maxSizeOfMessageToLog="Integer">
      <filters>
        <clear />
      </filters>
    </messageLogging>
  </diagnostics>
</system.serviceModel>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e7cdd-103">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="e7cdd-103">Attributes and Elements</span></span>  

 <span data-ttu-id="e7cdd-104">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="e7cdd-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e7cdd-105">Attributs</span><span class="sxs-lookup"><span data-stu-id="e7cdd-105">Attributes</span></span>  
  
|<span data-ttu-id="e7cdd-106">Attribut</span><span class="sxs-lookup"><span data-stu-id="e7cdd-106">Attribute</span></span>|<span data-ttu-id="e7cdd-107">Description</span><span class="sxs-lookup"><span data-stu-id="e7cdd-107">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="e7cdd-108">etwProviderId</span><span class="sxs-lookup"><span data-stu-id="e7cdd-108">etwProviderId</span></span>|<span data-ttu-id="e7cdd-109">Chaîne qui spécifie l'identificateur du fournisseur de suivi d'événements, qui écrit des événements dans les sessions ETW.</span><span class="sxs-lookup"><span data-stu-id="e7cdd-109">A string that specifies the identifier for the Event-Tracing provider, which writes events to ETW sessions.</span></span>|  
|<span data-ttu-id="e7cdd-110">performanceCounters</span><span class="sxs-lookup"><span data-stu-id="e7cdd-110">performanceCounters</span></span>|<span data-ttu-id="e7cdd-111">Spécifie si les compteurs de performance de l'assembly sont activés.</span><span class="sxs-lookup"><span data-stu-id="e7cdd-111">Specifies whether performance counters for the assembly are enabled.</span></span> <span data-ttu-id="e7cdd-112">Les valeurs valides sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="e7cdd-112">Valid values are</span></span><br /><br /> <span data-ttu-id="e7cdd-113">-OFF : les compteurs de performances sont désactivés.</span><span class="sxs-lookup"><span data-stu-id="e7cdd-113">-   Off: Performance counters are disabled.</span></span><br /><span data-ttu-id="e7cdd-114">-ServiceOnly : seuls les compteurs de performance pertinents pour ce service sont activés.</span><span class="sxs-lookup"><span data-stu-id="e7cdd-114">-   ServiceOnly: Only performance counters relevant to this service is enabled.</span></span><br /><span data-ttu-id="e7cdd-115">-All : les compteurs de performances peuvent être affichés au moment de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="e7cdd-115">-   All: Performance counters can be viewed at runtime.</span></span><br /><span data-ttu-id="e7cdd-116">-Default : une instance de compteur de performance unique _WCF_Admin est créée.</span><span class="sxs-lookup"><span data-stu-id="e7cdd-116">-   Default: A single performance counter instance _WCF_Admin is created.</span></span> <span data-ttu-id="e7cdd-117">Cette instance est employée pour activer la collection de données SQM utilisée par l’infrastructure.</span><span class="sxs-lookup"><span data-stu-id="e7cdd-117">This instance is used to enable the collection of SQM data for used by the infrastructure.</span></span> <span data-ttu-id="e7cdd-118">Aucune des valeurs du compteur de cette instance n'est mise à jour et par conséquent toutes resteront à zéro.</span><span class="sxs-lookup"><span data-stu-id="e7cdd-118">None of the counter values for this instance are updated and therefore will remain at zero.</span></span> <span data-ttu-id="e7cdd-119">Il s'agit de la valeur par défaut si aucune configuration n'est présente pour WCF.</span><span class="sxs-lookup"><span data-stu-id="e7cdd-119">This is the default value if no configuration is present for WCF.</span></span>|  
|<span data-ttu-id="e7cdd-120">wmiProviderEnabled</span><span class="sxs-lookup"><span data-stu-id="e7cdd-120">wmiProviderEnabled</span></span>|<span data-ttu-id="e7cdd-121">Valeur booléenne qui spécifie si le fournisseur WMI de l'assembly est activé.</span><span class="sxs-lookup"><span data-stu-id="e7cdd-121">A Boolean value that specifies whether the WMI provider for the assembly is enabled.</span></span> <span data-ttu-id="e7cdd-122">Le fournisseur WMI est requis pour que l’utilisateur puisse obtenir l’accès au moment de l’exécution aux fonctionnalités d’inspection et de contrôle de Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="e7cdd-122">The WMI provider is required for user to gain run-time access to the inspection and control features of Windows Communication Foundation (WCF).</span></span> <span data-ttu-id="e7cdd-123">Par défaut, il s’agit de `false`.</span><span class="sxs-lookup"><span data-stu-id="e7cdd-123">The default is `false`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="e7cdd-124">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="e7cdd-124">Child Elements</span></span>  
  
|<span data-ttu-id="e7cdd-125">Élément</span><span class="sxs-lookup"><span data-stu-id="e7cdd-125">Element</span></span>|<span data-ttu-id="e7cdd-126">Description</span><span class="sxs-lookup"><span data-stu-id="e7cdd-126">Description</span></span>|  
|-------------|-----------------|  
|[\<endToEndTracing>](endtoendtracing.md)|<span data-ttu-id="e7cdd-127">Élément de configuration qui vous permet d'activer et désactiver différents aspects du suivi de bout en bout pendant l'exécution d'une application de service.</span><span class="sxs-lookup"><span data-stu-id="e7cdd-127">A configuration element that allows you to enable and disable different aspects of end-to-end tracing during the running of a service application.</span></span>|  
|[\<messageLogging>](messagelogging.md)|<span data-ttu-id="e7cdd-128">Décrit les paramètres d'enregistrement des messages WCF.</span><span class="sxs-lookup"><span data-stu-id="e7cdd-128">Describes the settings for WCF message logging.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="e7cdd-129">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="e7cdd-129">Parent Elements</span></span>  
  
|<span data-ttu-id="e7cdd-130">Élément</span><span class="sxs-lookup"><span data-stu-id="e7cdd-130">Element</span></span>|<span data-ttu-id="e7cdd-131">Description</span><span class="sxs-lookup"><span data-stu-id="e7cdd-131">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="e7cdd-132">serviceModel</span><span class="sxs-lookup"><span data-stu-id="e7cdd-132">serviceModel</span></span>|<span data-ttu-id="e7cdd-133">Élément racine de tous les éléments de configuration WCF.</span><span class="sxs-lookup"><span data-stu-id="e7cdd-133">The root element of all WCF configuration elements.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e7cdd-134">Notes</span><span class="sxs-lookup"><span data-stu-id="e7cdd-134">Remarks</span></span>  

 <span data-ttu-id="e7cdd-135">La section `diagnostics` définit les paramètres de diagnostic pour tous les services situés dans un assembly.</span><span class="sxs-lookup"><span data-stu-id="e7cdd-135">The `diagnostics` section defines the diagnostics settings for all services located in an assembly.</span></span> <span data-ttu-id="e7cdd-136">Il est impossible de définir des paramètres de diagnostic distincts au niveau du service à moins qu'il n'y ait qu'un seul service dans l'assembly.</span><span class="sxs-lookup"><span data-stu-id="e7cdd-136">It is not possible to define separate diagnostics settings at the service level unless there is only one service in the assembly.</span></span> <span data-ttu-id="e7cdd-137">Les attributs sont définis d’après les exigences de la section.</span><span class="sxs-lookup"><span data-stu-id="e7cdd-137">Attributes are set according to the requirements of the section.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e7cdd-138">Exemple</span><span class="sxs-lookup"><span data-stu-id="e7cdd-138">Example</span></span>  
  
```xml  
<diagnostics wmiProviderEnabled="false"
             performanceCounters="all">
  <messageLogging logEntireMessage="true"
                  logMalformedMessages="true"
                  logMessagesAtServiceLevel="true"
                  logMessagesAtTransportLevel="true"
                  maxMessagesToLog="42"
                  maxSizeOfMessageToLog="42">
    <filters>
      <clear />
    </filters>
  </messageLogging>
</diagnostics>
```  
  
## <a name="see-also"></a><span data-ttu-id="e7cdd-139">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e7cdd-139">See also</span></span>

- <xref:System.ServiceModel.Configuration.DiagnosticSection>
- <xref:System.ServiceModel.Diagnostics>
