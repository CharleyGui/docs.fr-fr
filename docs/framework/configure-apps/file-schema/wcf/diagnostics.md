---
title: <diagnostics>
ms.date: 03/30/2017
ms.assetid: 0c2f95c4-cc12-4fb5-a70c-7fc6fa95db58
ms.openlocfilehash: 170cae5b328c86073c1d8e7710bb19e98ab5688c
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69925878"
---
# <a name="diagnostics"></a><span data-ttu-id="e350a-101">\<diagnostics></span><span class="sxs-lookup"><span data-stu-id="e350a-101">\<diagnostics></span></span>
<span data-ttu-id="e350a-102">L'élément `diagnostics` définit des paramètres qui peuvent être utilisés par un administrateur à des fins d'inspection et de contrôle au moment de l'exécution.</span><span class="sxs-lookup"><span data-stu-id="e350a-102">The `diagnostics` element defines settings that can be used by an administrator for run-time inspection and control.</span></span>  
  
 <span data-ttu-id="e350a-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="e350a-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="e350a-104">\<diagnostics></span><span class="sxs-lookup"><span data-stu-id="e350a-104">\<diagnostics></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e350a-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e350a-105">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e350a-106">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="e350a-106">Attributes and Elements</span></span>  
 <span data-ttu-id="e350a-107">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="e350a-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e350a-108">Attributs</span><span class="sxs-lookup"><span data-stu-id="e350a-108">Attributes</span></span>  
  
|<span data-ttu-id="e350a-109">Attribut</span><span class="sxs-lookup"><span data-stu-id="e350a-109">Attribute</span></span>|<span data-ttu-id="e350a-110">Description</span><span class="sxs-lookup"><span data-stu-id="e350a-110">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="e350a-111">etwProviderId</span><span class="sxs-lookup"><span data-stu-id="e350a-111">etwProviderId</span></span>|<span data-ttu-id="e350a-112">Chaîne qui spécifie l'identificateur du fournisseur de suivi d'événements, qui écrit des événements dans les sessions ETW.</span><span class="sxs-lookup"><span data-stu-id="e350a-112">A string that specifies the identifier for the Event-Tracing provider, which writes events to ETW sessions.</span></span>|  
|<span data-ttu-id="e350a-113">performanceCounters</span><span class="sxs-lookup"><span data-stu-id="e350a-113">performanceCounters</span></span>|<span data-ttu-id="e350a-114">Spécifie si les compteurs de performance de l'assembly sont activés.</span><span class="sxs-lookup"><span data-stu-id="e350a-114">Specifies whether performance counters for the assembly are enabled.</span></span> <span data-ttu-id="e350a-115">Les valeurs valides sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="e350a-115">Valid values are</span></span><br /><br /> <span data-ttu-id="e350a-116">Préférable Les compteurs de performance sont désactivés.</span><span class="sxs-lookup"><span data-stu-id="e350a-116">-   Off: Performance counters are disabled.</span></span><br /><span data-ttu-id="e350a-117">ServiceOnly Seuls les compteurs de performance pertinents pour ce service sont activés.</span><span class="sxs-lookup"><span data-stu-id="e350a-117">-   ServiceOnly: Only performance counters relevant to this service is enabled.</span></span><br /><span data-ttu-id="e350a-118">Tous les Les compteurs de performance peuvent être affichés pendant l'exécution.</span><span class="sxs-lookup"><span data-stu-id="e350a-118">-   All: Performance counters can be viewed at runtime.</span></span><br /><span data-ttu-id="e350a-119">Valeurs Un compteur de performance unique de l'instance _WCF_Admin est créé.</span><span class="sxs-lookup"><span data-stu-id="e350a-119">-   Default: A single performance counter instance _WCF_Admin is created.</span></span> <span data-ttu-id="e350a-120">Cette instance est employée pour activer la collection de données SQM utilisée par l’infrastructure.</span><span class="sxs-lookup"><span data-stu-id="e350a-120">This instance is used to enable the collection of SQM data for used by the infrastructure.</span></span> <span data-ttu-id="e350a-121">Aucune des valeurs du compteur de cette instance n'est mise à jour et par conséquent toutes resteront à zéro.</span><span class="sxs-lookup"><span data-stu-id="e350a-121">None of the counter values for this instance are updated and therefore will remain at zero.</span></span> <span data-ttu-id="e350a-122">Il s'agit de la valeur par défaut si aucune configuration n'est présente pour WCF.</span><span class="sxs-lookup"><span data-stu-id="e350a-122">This is the default value if no configuration is present for WCF.</span></span>|  
|<span data-ttu-id="e350a-123">wmiProviderEnabled</span><span class="sxs-lookup"><span data-stu-id="e350a-123">wmiProviderEnabled</span></span>|<span data-ttu-id="e350a-124">Valeur booléenne qui spécifie si le fournisseur WMI de l'assembly est activé.</span><span class="sxs-lookup"><span data-stu-id="e350a-124">A Boolean value that specifies whether the WMI provider for the assembly is enabled.</span></span> <span data-ttu-id="e350a-125">Le fournisseur WMI est requis pour que l’utilisateur puisse obtenir l’accès au moment de l’exécution aux fonctionnalités d’inspection et de contrôle de Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="e350a-125">The WMI provider is required for user to gain run-time access to the inspection and control features of Windows Communication Foundation (WCF).</span></span> <span data-ttu-id="e350a-126">Par défaut, il s’agit de `false`.</span><span class="sxs-lookup"><span data-stu-id="e350a-126">The default is `false`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="e350a-127">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="e350a-127">Child Elements</span></span>  
  
|<span data-ttu-id="e350a-128">Élément</span><span class="sxs-lookup"><span data-stu-id="e350a-128">Element</span></span>|<span data-ttu-id="e350a-129">Description</span><span class="sxs-lookup"><span data-stu-id="e350a-129">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e350a-130">\<endToEndTracing></span><span class="sxs-lookup"><span data-stu-id="e350a-130">\<endToEndTracing></span></span>](endtoendtracing.md)|<span data-ttu-id="e350a-131">Élément de configuration qui vous permet d'activer et désactiver différents aspects du suivi de bout en bout pendant l'exécution d'une application de service.</span><span class="sxs-lookup"><span data-stu-id="e350a-131">A configuration element that allows you to enable and disable different aspects of end-to-end tracing during the running of a service application.</span></span>|  
|[<span data-ttu-id="e350a-132">\<messageLogging></span><span class="sxs-lookup"><span data-stu-id="e350a-132">\<messageLogging></span></span>](messagelogging.md)|<span data-ttu-id="e350a-133">Décrit les paramètres d'enregistrement des messages WCF.</span><span class="sxs-lookup"><span data-stu-id="e350a-133">Describes the settings for WCF message logging.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="e350a-134">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="e350a-134">Parent Elements</span></span>  
  
|<span data-ttu-id="e350a-135">Élément</span><span class="sxs-lookup"><span data-stu-id="e350a-135">Element</span></span>|<span data-ttu-id="e350a-136">Description</span><span class="sxs-lookup"><span data-stu-id="e350a-136">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="e350a-137">serviceModel</span><span class="sxs-lookup"><span data-stu-id="e350a-137">serviceModel</span></span>|<span data-ttu-id="e350a-138">Élément racine de tous les éléments de configuration WCF.</span><span class="sxs-lookup"><span data-stu-id="e350a-138">The root element of all WCF configuration elements.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e350a-139">Notes</span><span class="sxs-lookup"><span data-stu-id="e350a-139">Remarks</span></span>  
 <span data-ttu-id="e350a-140">La section `diagnostics` définit les paramètres de diagnostic pour tous les services situés dans un assembly.</span><span class="sxs-lookup"><span data-stu-id="e350a-140">The `diagnostics` section defines the diagnostics settings for all services located in an assembly.</span></span> <span data-ttu-id="e350a-141">Il est impossible de définir des paramètres de diagnostic distincts au niveau du service à moins qu'il n'y ait qu'un seul service dans l'assembly.</span><span class="sxs-lookup"><span data-stu-id="e350a-141">It is not possible to define separate diagnostics settings at the service level unless there is only one service in the assembly.</span></span> <span data-ttu-id="e350a-142">Les attributs sont définis d’après les exigences de la section.</span><span class="sxs-lookup"><span data-stu-id="e350a-142">Attributes are set according to the requirements of the section.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e350a-143">Exemples</span><span class="sxs-lookup"><span data-stu-id="e350a-143">Example</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="e350a-144">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e350a-144">See also</span></span>

- <xref:System.ServiceModel.Configuration.DiagnosticSection>
- <xref:System.ServiceModel.Diagnostics>
