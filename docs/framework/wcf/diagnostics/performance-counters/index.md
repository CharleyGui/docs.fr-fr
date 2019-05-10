---
title: Compteurs de performance WCF
ms.date: 03/30/2017
helpviewer_keywords:
- performance counters [WCF]
ms.assetid: f559b2bd-ed83-4988-97a1-e88f06646609
ms.openlocfilehash: 2f4c62ff551ac66c4b7192a4e978db0a9f443f3f
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64613695"
---
# <a name="wcf-performance-counters"></a><span data-ttu-id="021ba-102">Compteurs de performance WCF</span><span class="sxs-lookup"><span data-stu-id="021ba-102">WCF Performance Counters</span></span>
<span data-ttu-id="021ba-103">Windows Communication Foundation (WCF) inclut un grand ensemble de compteurs de performances pour vous aider à mesurer les performances de votre application.</span><span class="sxs-lookup"><span data-stu-id="021ba-103">Windows Communication Foundation (WCF) includes a large set of performance counters to help you gauge your application's performance.</span></span>  
  
## <a name="enabling-performance-counters"></a><span data-ttu-id="021ba-104">Activation des compteurs de performance</span><span class="sxs-lookup"><span data-stu-id="021ba-104">Enabling Performance Counters</span></span>  
 <span data-ttu-id="021ba-105">Vous pouvez activer les compteurs de performances pour un service WCF via le fichier de configuration app.config du service WCF comme suit :</span><span class="sxs-lookup"><span data-stu-id="021ba-105">You can enable performance counters for a WCF service through the app.config configuration file of the WCF service as follows:</span></span>  
  
```xml  
<configuration>  
    <system.serviceModel>  
        <diagnostics performanceCounters="All" />  
    </system.serviceModel>  
</configuration>  
```  
  
 <span data-ttu-id="021ba-106">L'attribut `performanceCounters` peut être configuré pour activer un type spécifique de compteurs de performance.</span><span class="sxs-lookup"><span data-stu-id="021ba-106">The `performanceCounters` attribute can be set to enable a specific type of performance counters.</span></span> <span data-ttu-id="021ba-107">Les valeurs valides sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="021ba-107">Valid values are</span></span>  
  
- <span data-ttu-id="021ba-108">Toutes les : Tous les compteurs de catégorie (ServiceModelService, ServiceModelEndpoint et ServiceModelOperation) sont activés.</span><span class="sxs-lookup"><span data-stu-id="021ba-108">All: All category counters (ServiceModelService, ServiceModelEndpoint and ServiceModelOperation) are enabled.</span></span>  
  
- <span data-ttu-id="021ba-109">ServiceOnly : Seuls les compteurs de catégorie ServiceModelService sont activés.</span><span class="sxs-lookup"><span data-stu-id="021ba-109">ServiceOnly: Only ServiceModelService category counters are enabled.</span></span> <span data-ttu-id="021ba-110">Valeur par défaut.</span><span class="sxs-lookup"><span data-stu-id="021ba-110">This is the default value.</span></span>  
  
- <span data-ttu-id="021ba-111">Désactivé : Les compteurs de performance ServiceModel \* sont désactivés.</span><span class="sxs-lookup"><span data-stu-id="021ba-111">Off: ServiceModel\* performance counters are disabled.</span></span>  
  
 <span data-ttu-id="021ba-112">Si vous souhaitez activer les compteurs de performances pour toutes les applications WCF, vous pouvez placer les paramètres de configuration dans le fichier Machine.config.</span><span class="sxs-lookup"><span data-stu-id="021ba-112">If you want to enable performance counters for all WCF applications, you can place the configuration settings in the Machine.config file.</span></span>  <span data-ttu-id="021ba-113">Veuillez consulter la **augmentation de la taille de mémoire pour les compteurs de performances** section ci-dessous pour plus d’informations sur la configuration de mémoire suffisante pour les compteurs de performances sur votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="021ba-113">Please see the **Increasing Memory Size for Performance Counters** section below for more information on configuring sufficient memory for performance counters on your machine.</span></span>  
  
 <span data-ttu-id="021ba-114">Si vous utilisez des points d’extensibilité WCF tels que les appelants d’opération personnalisé, vous devez aussi émettre vos propres compteurs de performances.</span><span class="sxs-lookup"><span data-stu-id="021ba-114">If you use WCF extensibility points such as custom operation invokers, you should also emit your own performance counters.</span></span> <span data-ttu-id="021ba-115">Il s’agit, car si vous implémentez un point d’extensibilité, WCF peut ne plus émettre les données de compteur de performances standard dans le chemin d’accès par défaut.</span><span class="sxs-lookup"><span data-stu-id="021ba-115">This is because if you implement an extensibility point, WCF may no longer emit the standard performance counter data in the default path.</span></span> <span data-ttu-id="021ba-116">Si vous n'implémentez par la prise en charge manuelle des compteurs de performance, il est possible que vous ne voyiez pas les données de compteurs de performance attendues.</span><span class="sxs-lookup"><span data-stu-id="021ba-116">If you do not implement manual performance counter support, you may not see the performance counter data you expect.</span></span>  
  
 <span data-ttu-id="021ba-117">Vous pouvez aussi activer des compteurs de performance dans votre code comme suit.</span><span class="sxs-lookup"><span data-stu-id="021ba-117">You can also enable performance counters in your code as follows,</span></span>  
  
```  
using System.Configuration;  
using System.ServiceModel.Configuration;  
using System.ServiceModel.Diagnostics;  
Configuration config = ConfigurationManager.OpenExeConfiguration(  
    ConfigurationUserLevel.None);  
ServiceModelSectionGroup sg = ServiceModelSectionGroup.GetSectionGroup(config);  
sg.Diagnostic.PerformanceCounters = PerformanceCounterScope.All;  
config.Save();  
```  
  
## <a name="viewing-performance-data"></a><span data-ttu-id="021ba-118">Affichage des données de performance</span><span class="sxs-lookup"><span data-stu-id="021ba-118">Viewing Performance Data</span></span>  
 <span data-ttu-id="021ba-119">Pour consulter des données capturées par les compteurs de performance, vous pouvez utiliser l'analyseur de performances (Perfmon.exe) fourni avec Windows.</span><span class="sxs-lookup"><span data-stu-id="021ba-119">To view data captured by the performance counters, you can use the Performance Monitor (Perfmon.exe) that comes with Windows.</span></span> <span data-ttu-id="021ba-120">Vous pouvez lancer cet outil en accédant à **Démarrer**, puis cliquez sur **exécuter** et type `perfmon.exe` dans la boîte de dialogue.</span><span class="sxs-lookup"><span data-stu-id="021ba-120">You can launch this tool by going to **Start**, and click **Run** and type `perfmon.exe` in the dialog box.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="021ba-121">Les instances de compteur de performance peuvent être diffusées avant le traitement des derniers messages par le répartiteur de point de terminaison.</span><span class="sxs-lookup"><span data-stu-id="021ba-121">Performance counter instances may be released before the last messages have been processed by the endpoint dispatcher.</span></span> <span data-ttu-id="021ba-122">Il se peut alors que les données de performance de certains messages ne soient pas capturées.</span><span class="sxs-lookup"><span data-stu-id="021ba-122">This can result in performance data not being captured for a few messages.</span></span>  
  
## <a name="increasing-memory-size-for-performance-counters"></a><span data-ttu-id="021ba-123">Augmentation de la taille de la mémoire pour les compteurs de performance</span><span class="sxs-lookup"><span data-stu-id="021ba-123">Increasing Memory Size for Performance Counters</span></span>  
 <span data-ttu-id="021ba-124">WCF utilise la mémoire partagée séparée pour ses catégories de compteur de performances.</span><span class="sxs-lookup"><span data-stu-id="021ba-124">WCF uses separate shared memory for its performance counter categories.</span></span>  
  
 <span data-ttu-id="021ba-125">Par défaut, la mémoire partagée séparée a pour valeur un quart de la taille de la mémoire globale des compteurs de performance.</span><span class="sxs-lookup"><span data-stu-id="021ba-125">By default, separate shared memory is set to a quarter the size of global performance counter memory.</span></span> <span data-ttu-id="021ba-126">La mémoire globale des compteurs de performance par défaut est de 524 288 octets.</span><span class="sxs-lookup"><span data-stu-id="021ba-126">The default global performance counter memory is 524,288 bytes.</span></span> <span data-ttu-id="021ba-127">Par conséquent, les trois catégories de compteur de performance WCF ont une taille par défaut d’environ 128 Ko chacune.</span><span class="sxs-lookup"><span data-stu-id="021ba-127">Therefore, the three WCF performance counter categories have a default size of approximately 128KB each.</span></span> <span data-ttu-id="021ba-128">Selon les caractéristiques d’exécution des applications WCF sur un ordinateur, mémoire de compteur de performance peut être saturée.</span><span class="sxs-lookup"><span data-stu-id="021ba-128">Depending upon the runtime characteristics of the WCF applications on a machine, performance counter memory may be exhausted.</span></span> <span data-ttu-id="021ba-129">Dans ce cas, WCF écrit une erreur dans le journal des événements application.</span><span class="sxs-lookup"><span data-stu-id="021ba-129">When this happens, WCF writes an error to the application event log.</span></span> <span data-ttu-id="021ba-130">Le contenu de l’erreur indique qu’un compteur de performance n’a pas été chargé, et que l’entrée contient l’exception « System.InvalidOperationException : Affichage des fichiers de compteurs personnalisés mémoire est insuffisante. »</span><span class="sxs-lookup"><span data-stu-id="021ba-130">The content of the error states that a performance counter was not loaded, and the entry contains the exception "System.InvalidOperationException: Custom counters file view is out of memory."</span></span> <span data-ttu-id="021ba-131">Si le suivi est activé au niveau de l'erreur, cette défaillance est également suivie.</span><span class="sxs-lookup"><span data-stu-id="021ba-131">If tracing is enabled at the error level, this failure is also traced.</span></span> <span data-ttu-id="021ba-132">Si la mémoire de compteur de performance est épuisée, continuer à exécuter vos applications WCF avec les compteurs de performance activés peut entraîner une dégradation des performances.</span><span class="sxs-lookup"><span data-stu-id="021ba-132">If performance counter memory is exhausted, continuing to run your WCF applications with performance counters enabled could result in performance degradation.</span></span> <span data-ttu-id="021ba-133">Si vous êtes un administrateur de l'ordinateur, vous devez le configurer pour allouer suffisamment de mémoire afin de prendre en charge le nombre maximal de compteurs de performance pouvant exister à tout moment.</span><span class="sxs-lookup"><span data-stu-id="021ba-133">If you are an administrator of the machine, you should configure it to allocate enough memory to support the maximum number of performance counters that can exist at any time.</span></span>  
  
 <span data-ttu-id="021ba-134">Vous pouvez modifier la quantité de mémoire de compteur de performances pour les catégories WCF dans le Registre.</span><span class="sxs-lookup"><span data-stu-id="021ba-134">You can change the amount of performance counter memory for WCF categories in the registry.</span></span> <span data-ttu-id="021ba-135">Pour cela, vous devez ajouter une nouvelle valeur DWORD nommée `FileMappingSize` aux trois emplacements suivants et lui affecter en octets la valeur désirée.</span><span class="sxs-lookup"><span data-stu-id="021ba-135">To do so, you need to add a new DWORD value named `FileMappingSize` to the three following locations, and set it to the desired value in bytes.</span></span> <span data-ttu-id="021ba-136">Redémarrez votre ordinateur afin que ces modifications prennent effet.</span><span class="sxs-lookup"><span data-stu-id="021ba-136">Reboot your machine so that these changes are taken into effect.</span></span>  
  
- <span data-ttu-id="021ba-137">HKLM\System\CurrentControlSet\Services\ServiceModelEndpoint 4.0.0.0\Performance</span><span class="sxs-lookup"><span data-stu-id="021ba-137">HKLM\System\CurrentControlSet\Services\ServiceModelEndpoint 4.0.0.0\Performance</span></span>  
  
- <span data-ttu-id="021ba-138">HKLM\System\CurrentControlSet\Services\ServiceModelOperation 4.0.0.0\Performance</span><span class="sxs-lookup"><span data-stu-id="021ba-138">HKLM\System\CurrentControlSet\Services\ServiceModelOperation 4.0.0.0\Performance</span></span>  
  
- <span data-ttu-id="021ba-139">HKLM\System\CurrentControlSet\Services\ServiceModelService 4.0.0.0\Performance</span><span class="sxs-lookup"><span data-stu-id="021ba-139">HKLM\System\CurrentControlSet\Services\ServiceModelService 4.0.0.0\Performance</span></span>  
  
 <span data-ttu-id="021ba-140">Lorsqu'un grand nombre d'objets (par exemple, ServiceHost) sont supprimés mais sont en attente d'être récupérés par le garbage collector, le compteur de performance `PrivateBytes` enregistre un nombre exceptionnellement élevé.</span><span class="sxs-lookup"><span data-stu-id="021ba-140">When a large number of objects (for example, ServiceHost) are disposed of but waiting to be garbage-collected, the `PrivateBytes` performance counter will register an unusually high number.</span></span> <span data-ttu-id="021ba-141">Pour résoudre ce problème, vous pouvez ajouter vos propres compteurs spécifiques à l'application ou utiliser l'attribut `performanceCounters` pour activer des compteurs au niveau du service uniquement.</span><span class="sxs-lookup"><span data-stu-id="021ba-141">To resolve this problem, you can either add your own application-specific counters, or use the `performanceCounters` attribute to enable only service-level counters.</span></span>  
  
## <a name="types-of-performance-counters"></a><span data-ttu-id="021ba-142">Types de compteurs de performance</span><span class="sxs-lookup"><span data-stu-id="021ba-142">Types of Performance Counters</span></span>  
 <span data-ttu-id="021ba-143">Compteurs de performances sont limités à trois niveaux différents : Service, point de terminaison et opération.</span><span class="sxs-lookup"><span data-stu-id="021ba-143">Performance counters are scoped to three different levels: Service, Endpoint and Operation.</span></span>  
  
 <span data-ttu-id="021ba-144">Vous pouvez utiliser WMI pour récupérer le nom d'une instance de compteur de performance.</span><span class="sxs-lookup"><span data-stu-id="021ba-144">You can use WMI to retrieve the name of a performance counter instance.</span></span> <span data-ttu-id="021ba-145">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="021ba-145">For example,</span></span>  
  
- <span data-ttu-id="021ba-146">Nom d’instance de compteur de service peut être obtenu via WMI [Service](../../../../../docs/framework/wcf/diagnostics/wmi/service.md) propriété « CounterInstanceName » de l’instance.</span><span class="sxs-lookup"><span data-stu-id="021ba-146">Service counter instance name can be obtained through WMI [Service](../../../../../docs/framework/wcf/diagnostics/wmi/service.md) instance's "CounterInstanceName" property.</span></span>  
  
- <span data-ttu-id="021ba-147">Nom d’instance de compteur de point de terminaison peut être obtenu via WMI [point de terminaison](../../../../../docs/framework/wcf/diagnostics/wmi/endpoint.md) propriété « CounterInstanceName » de l’instance.</span><span class="sxs-lookup"><span data-stu-id="021ba-147">Endpoint counter instance name can be obtained through WMI [Endpoint](../../../../../docs/framework/wcf/diagnostics/wmi/endpoint.md) instance's "CounterInstanceName" property.</span></span>  
  
- <span data-ttu-id="021ba-148">Nom d’instance de compteur d’opération peut être obtenu via WMI [point de terminaison](../../../../../docs/framework/wcf/diagnostics/wmi/endpoint.md) méthode « GetOperationCounterInstanceName » de l’instance.</span><span class="sxs-lookup"><span data-stu-id="021ba-148">Operation counter instance name can be obtained through WMI [Endpoint](../../../../../docs/framework/wcf/diagnostics/wmi/endpoint.md) instance's "GetOperationCounterInstanceName" method.</span></span>  
  
 <span data-ttu-id="021ba-149">Pour plus d’informations sur WMI, consultez [à l’aide de Windows Management Instrumentation pour les Diagnostics](../../../../../docs/framework/wcf/diagnostics/wmi/index.md).</span><span class="sxs-lookup"><span data-stu-id="021ba-149">For more information on WMI, see [Using Windows Management Instrumentation for Diagnostics](../../../../../docs/framework/wcf/diagnostics/wmi/index.md).</span></span>  
  
### <a name="service-performance-counters"></a><span data-ttu-id="021ba-150">Compteurs de performance de service</span><span class="sxs-lookup"><span data-stu-id="021ba-150">Service performance counters</span></span>  
 <span data-ttu-id="021ba-151">Les compteurs de performance de service mesurent le comportement du service dans son ensemble et peuvent être utilisés pour diagnostiquer les performances de la totalité du service.</span><span class="sxs-lookup"><span data-stu-id="021ba-151">Service performance counters measure the service behavior as a whole and can be used to diagnose the performance of the whole service.</span></span> <span data-ttu-id="021ba-152">Ils se trouvent sous l'objet de performance `ServiceModelService 4.0.0.0` dans l'affichage de l'analyseur de performances.</span><span class="sxs-lookup"><span data-stu-id="021ba-152">They can be found under the `ServiceModelService 4.0.0.0` performance object when viewing with Performance Monitor.</span></span> <span data-ttu-id="021ba-153">Les instances sont nommées à l'aide du modèle suivant :</span><span class="sxs-lookup"><span data-stu-id="021ba-153">The instances are named using the following pattern:</span></span>  
  
```  
ServiceName@ServiceBaseAddress  
```  
  
 <span data-ttu-id="021ba-154">Un compteur dans une portée de service est issu du compteur dans une collection de points de terminaison.</span><span class="sxs-lookup"><span data-stu-id="021ba-154">A counter in a service scope is aggregated from counter in a collection of endpoints.</span></span>  
  
 <span data-ttu-id="021ba-155">Les compteurs de performance pour la création d'une instance de service sont incrémentés lors de la création d'un nouveau InstanceContext.</span><span class="sxs-lookup"><span data-stu-id="021ba-155">Performance counters for service instance creation are incremented when a new InstanceContext is created.</span></span> <span data-ttu-id="021ba-156">Notez qu'un nouveau InstanceContext est créé lorsque vous recevez un message de non activation (avec un service existant), ou lorsque vous vous connectez à une instance à partir d'une session, terminez la session puis reconnectez à partir d'une autre session.</span><span class="sxs-lookup"><span data-stu-id="021ba-156">Note that a new InstanceContext is created even when you receive a non-activating message (with an existing service), or when you connect to an instance from one session, end the session, and then reconnect from another session.</span></span>  
  
### <a name="endpoint-performance-counters"></a><span data-ttu-id="021ba-157">Compteurs de performance de point de terminaison</span><span class="sxs-lookup"><span data-stu-id="021ba-157">Endpoint performance counters</span></span>  
 <span data-ttu-id="021ba-158">Les compteurs de performance de point de terminaison vous permettent de consulter des données en reflétant la manière dont un point de terminaison accepte des messages.</span><span class="sxs-lookup"><span data-stu-id="021ba-158">Endpoint performance counters enable you to look at data reflecting how an endpoint is accepting messages.</span></span> <span data-ttu-id="021ba-159">Ils se trouvent sous l'objet de performance `ServiceModelEndpoint 4.0.0.0` dans l'affichage de l'analyseur de performances.</span><span class="sxs-lookup"><span data-stu-id="021ba-159">They can be found under the `ServiceModelEndpoint 4.0.0.0` performance object when viewing using the Performance Monitor.</span></span> <span data-ttu-id="021ba-160">Les instances sont nommées à l'aide du modèle suivant :</span><span class="sxs-lookup"><span data-stu-id="021ba-160">The instances are named using the following pattern:</span></span>  
  
```  
(ServiceName).(ContractName)@(endpoint listener address)  
```  
  
 <span data-ttu-id="021ba-161">Les données sont semblables à celles recueillies pour des opérations individuelles, mais sont regroupées uniquement sur le point de terminaison.</span><span class="sxs-lookup"><span data-stu-id="021ba-161">The data is similar to what is collected for individual operations, but is only aggregated across the endpoint.</span></span>  
  
 <span data-ttu-id="021ba-162">Un compteur dans une portée de point de terminaison est issu des compteurs dans une collection d’opérations.</span><span class="sxs-lookup"><span data-stu-id="021ba-162">A counter in an endpoint scope is aggregated from counters in a collection of operations.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="021ba-163">Si deux points de terminaison ont des noms de contrat et des adresses identiques, ils sont mappés à la même instance de compteur.</span><span class="sxs-lookup"><span data-stu-id="021ba-163">If two endpoints have identical contract names and addresses, they are mapped to the same counter instance.</span></span>  
  
### <a name="operation-performance-counters"></a><span data-ttu-id="021ba-164">Compteurs de performance d'opération</span><span class="sxs-lookup"><span data-stu-id="021ba-164">Operation performance counters</span></span>  
 <span data-ttu-id="021ba-165">Les compteurs de performance d'opération se trouvent sous l'objet de performance `ServiceModelOperation 4.0.0.0` dans l'affichage de l'analyseur de performances.</span><span class="sxs-lookup"><span data-stu-id="021ba-165">Operation performance counters are found under the `ServiceModelOperation 4.0.0.0` performance object when viewing with the Performance Monitor.</span></span> <span data-ttu-id="021ba-166">Chaque opération a une instance individuelle.</span><span class="sxs-lookup"><span data-stu-id="021ba-166">Each operation has an individual instance.</span></span> <span data-ttu-id="021ba-167">Autrement dit, si un contrat donné a 10 opérations, 10 instances de compteur d'opération sont associées à ce contrat.</span><span class="sxs-lookup"><span data-stu-id="021ba-167">That is, if a given contract has 10 operations, 10 operation counter instances are associated with that contract.</span></span> <span data-ttu-id="021ba-168">Les instances d’objet sont nommées à l’aide du modèle suivant :</span><span class="sxs-lookup"><span data-stu-id="021ba-168">The object instances are named using the following pattern:</span></span>  
  
```  
(ServiceName).(ContractName).(OperationName)@(first endpoint listener address)  
```  
  
 <span data-ttu-id="021ba-169">Ce compteur vous permet de mesurer la manière dont l'appel est utilisé et comment l'opération s'exécute.</span><span class="sxs-lookup"><span data-stu-id="021ba-169">This counter enables you to measure how the call is being used and how well the operation is performing.</span></span>  
  
 <span data-ttu-id="021ba-170">Lorsque les compteurs sont visibles au niveau de plusieurs portées, les données issues d'une portée supérieure sont regroupées avec les données des portées inférieures.</span><span class="sxs-lookup"><span data-stu-id="021ba-170">When counters are visible at multiple scopes, data gathered from a higher scope are aggregated with data from lower scopes.</span></span> <span data-ttu-id="021ba-171">Par exemple, `Calls` à un point de terminaison représente la somme de tous les appels d'opération dans le point de terminaison ; `Calls` à un service représente la somme de tous les appels à tous les points de terminaison dans le service.</span><span class="sxs-lookup"><span data-stu-id="021ba-171">For example, `Calls` at an endpoint represents the sum of all operation calls within the endpoint; `Calls` at a service represents the sum of all calls to all endpoints within the service.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="021ba-172">Si vous avez des noms d'opération en double sur un contrat, vous recevez seulement une instance de compteur pour les deux opérations.</span><span class="sxs-lookup"><span data-stu-id="021ba-172">If you have duplicate operation names on a contract, you only get one counter instances for both operations.</span></span>  
  
## <a name="programming-the-wcf-performance-counters"></a><span data-ttu-id="021ba-173">Programmation des compteurs de performance WCF</span><span class="sxs-lookup"><span data-stu-id="021ba-173">Programming the WCF Performance Counters</span></span>  
 <span data-ttu-id="021ba-174">Plusieurs fichiers sont installés dans le dossier d’installation SDK afin que vous pouvez accéder par programmation les compteurs de performance WCF.</span><span class="sxs-lookup"><span data-stu-id="021ba-174">Several files are installed in the SDK install folder so that you can access the WCF performance counters programmatically.</span></span> <span data-ttu-id="021ba-175">Ces fichiers sont répertoriés comme suit.</span><span class="sxs-lookup"><span data-stu-id="021ba-175">These files are listed as follows.</span></span>  
  
- <span data-ttu-id="021ba-176">_ServiceModelEndpointPerfCounters.vrg</span><span class="sxs-lookup"><span data-stu-id="021ba-176">_ServiceModelEndpointPerfCounters.vrg</span></span>  
  
- <span data-ttu-id="021ba-177">_ServiceModelOperationPerfCounters.vrg</span><span class="sxs-lookup"><span data-stu-id="021ba-177">_ServiceModelOperationPerfCounters.vrg</span></span>  
  
- <span data-ttu-id="021ba-178">_ServiceModelServicePerfCounters.vrg</span><span class="sxs-lookup"><span data-stu-id="021ba-178">_ServiceModelServicePerfCounters.vrg</span></span>  
  
- <span data-ttu-id="021ba-179">_SMSvcHostPerfCounters.vrg</span><span class="sxs-lookup"><span data-stu-id="021ba-179">_SMSvcHostPerfCounters.vrg</span></span>  
  
- <span data-ttu-id="021ba-180">_TransactionBridgePerfCounters.vrg</span><span class="sxs-lookup"><span data-stu-id="021ba-180">_TransactionBridgePerfCounters.vrg</span></span>  
  
 <span data-ttu-id="021ba-181">Pour plus d’informations sur la façon d’accéder par programme aux compteurs, consultez [Architecture de programmation de compteur de performances](https://go.microsoft.com/fwlink/?LinkId=95179).</span><span class="sxs-lookup"><span data-stu-id="021ba-181">For more information on how to access the counters programmatically, see [Performance Counter Programming Architecture](https://go.microsoft.com/fwlink/?LinkId=95179).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="021ba-182">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="021ba-182">See also</span></span>

- [<span data-ttu-id="021ba-183">Administration et diagnostics</span><span class="sxs-lookup"><span data-stu-id="021ba-183">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
