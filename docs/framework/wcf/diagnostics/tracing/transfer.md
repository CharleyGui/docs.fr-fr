---
title: Transférer
ms.date: 03/30/2017
ms.assetid: dfcfa36c-d3bb-44b4-aa15-1c922c6f73e6
ms.openlocfilehash: e0ebfff97cd33e7a588a1ab92399a97a0fbec039
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79185706"
---
# <a name="transfer"></a><span data-ttu-id="62947-102">Transférer</span><span class="sxs-lookup"><span data-stu-id="62947-102">Transfer</span></span>
<span data-ttu-id="62947-103">Ce sujet décrit le transfert dans le modèle de traçage des activités de la Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="62947-103">This topic describes transfer in the Windows Communication Foundation (WCF) activity tracing model.</span></span>  
  
## <a name="transfer-definition"></a><span data-ttu-id="62947-104">Définition d'un transfert</span><span class="sxs-lookup"><span data-stu-id="62947-104">Transfer Definition</span></span>  
 <span data-ttu-id="62947-105">Les transferts entre activités représentent des liens de causalité entre événements dans les activités connexes dans des points de terminaison.</span><span class="sxs-lookup"><span data-stu-id="62947-105">Transfers between activities represent causal relationships between events in the related activities within endpoints.</span></span> <span data-ttu-id="62947-106">Deux activités sont liées à des transferts lorsqu'un contrôle circule entre ces activités, par exemple, un appel de méthode qui traverse des limites d'activité.</span><span class="sxs-lookup"><span data-stu-id="62947-106">Two activities are related with transfers when control flows between these activities, for example, a method call crossing activity boundaries.</span></span> <span data-ttu-id="62947-107">Dans WCF, lorsque les octets arrivent sur le service, l’activité Listen At est transférée à l’activité Des octets reçoivent où l’objet de message est créé.</span><span class="sxs-lookup"><span data-stu-id="62947-107">In WCF, when bytes are incoming on the service, the Listen At activity is transferred to the Receive Bytes activity where the message object is created.</span></span> <span data-ttu-id="62947-108">Pour une liste de scénarios de traçage de bout en bout, ainsi que leur activité respective et leur conception de traçage, voir [scénarios de traçage](../../../../../docs/framework/wcf/diagnostics/tracing/end-to-end-tracing-scenarios.md)de bout en bout .</span><span class="sxs-lookup"><span data-stu-id="62947-108">For a list of end-to-end tracing scenarios, and their respective activity and tracing design, see [End-To-End Tracing Scenarios](../../../../../docs/framework/wcf/diagnostics/tracing/end-to-end-tracing-scenarios.md).</span></span>  
  
 <span data-ttu-id="62947-109">Pour émettre des suivis de transfert, appliquez le paramètre `ActivityTracing` sur la source de suivi, tel que le montre le code de configuration suivant.</span><span class="sxs-lookup"><span data-stu-id="62947-109">To emit transfer traces, use the `ActivityTracing` setting on the trace source as demonstrated by the following configuration code.</span></span>  
  
```xml  
<source name="System.ServiceModel" switchValue="Verbose,ActivityTracing">  
```  
  
## <a name="using-transfer-to-correlate-activities-within-endpoints"></a><span data-ttu-id="62947-110">Utilisation du suivi Transfert pour corréler des activités dans des points de terminaison</span><span class="sxs-lookup"><span data-stu-id="62947-110">Using Transfer to Correlate Activities Within Endpoints</span></span>  
 <span data-ttu-id="62947-111">Les activités et transferts permettent à l'utilisateur de rechercher de manière probabiliste la cause première d'une erreur.</span><span class="sxs-lookup"><span data-stu-id="62947-111">Activities and transfers permit the user to probabilistically locate the root cause of an error.</span></span> <span data-ttu-id="62947-112">Par exemple, si nous transférons des données entre les activités M et N, dans les composants M et N, et qu'un incident se produit en N juste après le transfert vers M, il est possible de conclure que le problème provient du passage de données de N vers M.</span><span class="sxs-lookup"><span data-stu-id="62947-112">For example, if we transfer back and forth between activities M and N respectively in components M and N, and a crash happens in N right after the transfer back to M, we can draw the conclusion that it is likely due to N’s passing data back to M.</span></span>  
  
 <span data-ttu-id="62947-113">Un suivi de transfert est émis de l'activité M vers l'activité N, lorsqu'il existe un flux de contrôle entre M et N. Par exemple, N exécute une tâche pour M à cause d'un appel de méthode franchissant les limites des activités.</span><span class="sxs-lookup"><span data-stu-id="62947-113">A transfer trace is emitted from activity M to activity N when there is a flow of control between M and N. For example, N performs some work for M because of a method call crossing the activities’ boundaries.</span></span> <span data-ttu-id="62947-114">N existe peut-être déjà ou a été créé.</span><span class="sxs-lookup"><span data-stu-id="62947-114">N may already exist or has been created.</span></span> <span data-ttu-id="62947-115">N est généré par M lorsque N est une nouvelle activité qui exécute une tâche pour M.</span><span class="sxs-lookup"><span data-stu-id="62947-115">N is spawned by M when N is a new activity that performs some work for M.</span></span>  
  
 <span data-ttu-id="62947-116">Un transfert de M à N peut pas être suivi d'un transfert réciproque de N à M. Cela est dû au fait que M peut générer une tâche dans N sans assurer le suivi de l'exécution de cette tâche par N.</span><span class="sxs-lookup"><span data-stu-id="62947-116">A transfer from M to N may not be followed by a transfer back from N to M. This is because M can spawn some work in N and do not track when N completes that work.</span></span> <span data-ttu-id="62947-117">En fait, M peut se terminer avant que N n’ait achevé sa tâche.</span><span class="sxs-lookup"><span data-stu-id="62947-117">In fact, M can terminate before N completes its task.</span></span> <span data-ttu-id="62947-118">Cela se produit dans l’activité "Open ServiceHost" (M) qui engendre les activités de l’auditeur (N) et se termine ensuite.</span><span class="sxs-lookup"><span data-stu-id="62947-118">This happens in the "Open ServiceHost" activity (M) that spawns Listener activities (N) and then terminates.</span></span> <span data-ttu-id="62947-119">Un transfert de N à M indique que N a achevé la tâche liée à M.</span><span class="sxs-lookup"><span data-stu-id="62947-119">A transfer back from N to M means that N completed the work related to M.</span></span>  
  
 <span data-ttu-id="62947-120">N peut continuer à effectuer d'autres traitements non liés à M, par exemple, une activité d'authentificateur existante (N) qui continue à recevoir des demandes de connexion (M) provenant de différentes activités de connexion.</span><span class="sxs-lookup"><span data-stu-id="62947-120">N can continue performing other processing unrelated to M, for example, an existing authenticator activity (N) that keeps receiving login requests (M) from different login activities.</span></span>  
  
 <span data-ttu-id="62947-121">Il n'existe pas nécessairement de relation d'imbrication entre les activités M et N, et ce pour deux raisons :</span><span class="sxs-lookup"><span data-stu-id="62947-121">A nesting relationship does not necessarily exist between activities M and N. This can happen due to two reasons.</span></span> <span data-ttu-id="62947-122">d'une part si l'activité M ne surveille pas le traitement réel effectué dans N bien qu'il ait initié ce traitement, d'autre part si N existe déjà.</span><span class="sxs-lookup"><span data-stu-id="62947-122">First, when activity M does not monitor the actual processing performed in N although M initiated N. Second, when N already exists.</span></span>  
  
## <a name="example-of-transfers"></a><span data-ttu-id="62947-123">Exemples de transferts</span><span class="sxs-lookup"><span data-stu-id="62947-123">Example of Transfers</span></span>  
 <span data-ttu-id="62947-124">Deux exemples de transferts sont présentés ci-dessous.</span><span class="sxs-lookup"><span data-stu-id="62947-124">The following lists two transfer examples.</span></span>  
  
- <span data-ttu-id="62947-125">Lorsque vous créez un hôte de service, le constructeur prend le contrôle à partir du code appelant, ou le code appelant est transféré au constructeur.</span><span class="sxs-lookup"><span data-stu-id="62947-125">When you create a service host, the constructor gains control from the calling code, or the calling code transfers to the constructor.</span></span> <span data-ttu-id="62947-126">Lorsque le constructeur a terminé de s'exécuter, il retourne le contrôle au code appelant, ou le constructeur est transféré au code appelant.</span><span class="sxs-lookup"><span data-stu-id="62947-126">When the constructor has finished executing, it returns control to the calling code, or the constructor transfers back to the calling code.</span></span> <span data-ttu-id="62947-127">C'est le cas d'une relation imbriquée.</span><span class="sxs-lookup"><span data-stu-id="62947-127">This is the case of a nested relationship.</span></span>  
  
- <span data-ttu-id="62947-128">Lorsqu'un écouteur commence à traiter des données de transport, il crée un nouveau thread et remet à l'activité Recevoir des octets le contexte de traitement approprié, c'est-à-dire en passant le contrôle et les données.</span><span class="sxs-lookup"><span data-stu-id="62947-128">When a listener starts processing transport data, it creates a new thread and hands to the Receive Bytes activity the appropriate context for processing, passing control and data.</span></span> <span data-ttu-id="62947-129">Lorsque ce thread a fini de traiter la demande, l'activité Recevoir des octets ne repasse aucune donnée à l'écouteur.</span><span class="sxs-lookup"><span data-stu-id="62947-129">When that thread has finished processing the request, the Receive Bytes activity passes nothing back to the listener.</span></span> <span data-ttu-id="62947-130">Dans ce cas, la nouvelle activité de thread fait l'objet d'un transfert entrant mais pas d'un transfert sortant.</span><span class="sxs-lookup"><span data-stu-id="62947-130">In this case, we have a transfer in but no transfer out of the new thread activity.</span></span> <span data-ttu-id="62947-131">Les deux activités sont liées mais pas imbriquées.</span><span class="sxs-lookup"><span data-stu-id="62947-131">The two activities are related but not nested.</span></span>  
  
## <a name="activity-transfer-sequence"></a><span data-ttu-id="62947-132">Séquence de transfert d'activité</span><span class="sxs-lookup"><span data-stu-id="62947-132">Activity Transfer Sequence</span></span>  
 <span data-ttu-id="62947-133">Une séquence de transfert d'activité bien formée comprend les étapes suivantes.</span><span class="sxs-lookup"><span data-stu-id="62947-133">A well-formed activity transfer sequence includes the following steps.</span></span>  
  
1. <span data-ttu-id="62947-134">Commencer une nouvelle activité, qui consiste à sélectionner un nouveau gAId</span><span class="sxs-lookup"><span data-stu-id="62947-134">Begin a new activity, which consists of selecting a new gAId.</span></span>  
  
2. <span data-ttu-id="62947-135">Émettre un suivi de transfert vers ce nouveau gAId à partir de l'ID d'activité actuel</span><span class="sxs-lookup"><span data-stu-id="62947-135">Emit a transfer trace to that new gAId from the current activity ID</span></span>  
  
3. <span data-ttu-id="62947-136">Définir le nouvel ID dans le stockage local des threads (TLS)</span><span class="sxs-lookup"><span data-stu-id="62947-136">Set the new ID in TLS</span></span>  
  
4. <span data-ttu-id="62947-137">Émettre un suivi de démarrage pour indiquer le début de la nouvelle activité</span><span class="sxs-lookup"><span data-stu-id="62947-137">Emit a start trace to indicate the beginning of the new activity by.</span></span>  
  
5. <span data-ttu-id="62947-138">Retourner à l'activité d'origine implique les étapes suivantes :</span><span class="sxs-lookup"><span data-stu-id="62947-138">Return to the original activity consists of the following:</span></span>  
  
6. <span data-ttu-id="62947-139">Émettre un suivi de transfert vers le gAId d'origine</span><span class="sxs-lookup"><span data-stu-id="62947-139">Emit a transfer trace to the original gAId</span></span>  
  
7. <span data-ttu-id="62947-140">Émettre un suivi d'arrêt pour indiquer la fin de la nouvelle activité</span><span class="sxs-lookup"><span data-stu-id="62947-140">Emit a Stop trace to indicate the end of the new activity</span></span>  
  
8. <span data-ttu-id="62947-141">Affecter au TLS l'ancien gAId</span><span class="sxs-lookup"><span data-stu-id="62947-141">Set TLS to the old gAId.</span></span>  
  
 <span data-ttu-id="62947-142">L'exemple de code suivant montre comment procéder.</span><span class="sxs-lookup"><span data-stu-id="62947-142">The following code example demonstrates how to do this.</span></span> <span data-ttu-id="62947-143">Cet exemple suppose qu'un appel bloquant est effectué lors du transfert vers la nouvelle activité, et inclut des suivis de suspension/reprise.</span><span class="sxs-lookup"><span data-stu-id="62947-143">This sample assumes a blocking call is made when transferring to the new activity, and includes suspend/resume traces.</span></span>  
  
```csharp
// 0. Create a trace source  
TraceSource ts = new TraceSource("myTS");  

// 1. remember existing ("ambient") activity for clean up  
Guid oldGuid = Trace.CorrelationManager.ActivityId;  
// this will be our new activity  
Guid newGuid = Guid.NewGuid();

// 2. call transfer, indicating that we are switching to the new AID  
ts.TraceTransfer(667, "Transferring.", newGuid);  

// 3. Suspend the current activity.  
ts.TraceEvent(TraceEventType.Suspend, 667, "Suspend: Activity " + i-1);  

// 4. set the new AID in TLS  
Trace.CorrelationManager.ActivityId = newGuid;  

// 5. Emit the start trace  
ts.TraceEvent(TraceEventType.Start, 667, "Boundary: Activity " + i);  

// trace something  
ts.TraceEvent(TraceEventType.Information, 667, "Hello from activity " + i);  

// Perform Work  
// some work.  
// Return  
ts.TraceEvent(TraceEventType.Information, 667, "Work complete on activity " + i);

// 6. Emit the transfer returning to the original activity  
ts.TraceTransfer(667, "Transferring Back.", oldGuid);  

// 7. Emit the End trace  
ts.TraceEvent(TraceEventType.Stop, 667, "Boundary: Activity " + i);  

// 8. Change the tls variable to the original AID  
Trace.CorrelationManager.ActivityId = oldGuid;

// 9. Resume the old activity  
ts.TraceEvent(TraceEventType.Resume, 667, "Resume: Activity " + i-1);  
```  
  
## <a name="see-also"></a><span data-ttu-id="62947-144">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="62947-144">See also</span></span>

- [<span data-ttu-id="62947-145">Configuration du traçage</span><span class="sxs-lookup"><span data-stu-id="62947-145">Configuring Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/configuring-tracing.md)
- [<span data-ttu-id="62947-146">Utilisation de Service Trace Viewer pour afficher les suivis corrélés et résoudre les problèmes</span><span class="sxs-lookup"><span data-stu-id="62947-146">Using Service Trace Viewer for Viewing Correlated Traces and Troubleshooting</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-service-trace-viewer-for-viewing-correlated-traces-and-troubleshooting.md)
- [<span data-ttu-id="62947-147">Scénarios de suivi de bout en bout</span><span class="sxs-lookup"><span data-stu-id="62947-147">End-To-End Tracing Scenarios</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/end-to-end-tracing-scenarios.md)
- [<span data-ttu-id="62947-148">Outil Service Trace Viewer (SvcTraceViewer.exe)</span><span class="sxs-lookup"><span data-stu-id="62947-148">Service Trace Viewer Tool (SvcTraceViewer.exe)</span></span>](../../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md)
