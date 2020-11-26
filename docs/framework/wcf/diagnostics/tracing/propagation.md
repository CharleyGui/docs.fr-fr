---
title: Propagation
ms.date: 03/30/2017
ms.assetid: f8181e75-d693-48d1-b333-a776ad3b382a
ms.openlocfilehash: be010178d8f0face8f6c7e986107e4ea90d91953
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96240132"
---
# <a name="propagation"></a><span data-ttu-id="80f09-102">Propagation</span><span class="sxs-lookup"><span data-stu-id="80f09-102">Propagation</span></span>

<span data-ttu-id="80f09-103">Cette rubrique décrit la propagation d’activité dans le modèle de suivi Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="80f09-103">This topic describes activity propagation in the Windows Communication Foundation (WCF) tracing model.</span></span>  
  
## <a name="using-propagation-to-correlate-activities-across-endpoints"></a><span data-ttu-id="80f09-104">Utilisation de la propagation pour corréler des activités sur des points de terminaison</span><span class="sxs-lookup"><span data-stu-id="80f09-104">Using Propagation to Correlate Activities Across Endpoints</span></span>  

 <span data-ttu-id="80f09-105">La propagation fournit à l'utilisateur la corrélation directe de suivi d'erreur pour la même unité de traitement sur des points de terminaison d'application, par exemple, une demande.</span><span class="sxs-lookup"><span data-stu-id="80f09-105">Propagation provides the user with direct correlation of error traces for the same unit of processing across application endpoints, for example, a request.</span></span> <span data-ttu-id="80f09-106">Les erreurs émises à des points de terminaison différents pour la même unité de traitement sont groupées dans la même activité, y compris sur les domaines d'application.</span><span class="sxs-lookup"><span data-stu-id="80f09-106">Errors emitted at different endpoints for the same unit of processing are grouped in the same activity, even across application domains.</span></span> <span data-ttu-id="80f09-107">Cette opération s'effectue par la propagation de l'ID d'activité dans les en-têtes de message.</span><span class="sxs-lookup"><span data-stu-id="80f09-107">This is done through propagation of the activity ID in the message headers.</span></span> <span data-ttu-id="80f09-108">Par conséquent, en cas d'expiration d'un client à cause d'une erreur interne dans le serveur, les deux erreurs apparaissent dans la même activité pour une corrélation directe.</span><span class="sxs-lookup"><span data-stu-id="80f09-108">Therefore, if a client times out because of an internal error in the server, both errors appear in the same activity for direct correlation.</span></span>  
  
 <span data-ttu-id="80f09-109">Pour ce faire, utilisez le paramètre `ActivityTracing` comme indiqué dans l'exemple précédent.</span><span class="sxs-lookup"><span data-stu-id="80f09-109">To do this, use the `ActivityTracing` setting as demonstrated in the previous example.</span></span> <span data-ttu-id="80f09-110">Définissez aussi l'attribut `propagateActivity` pour la source de suivi `System.ServiceModel` à tous les points de terminaison.</span><span class="sxs-lookup"><span data-stu-id="80f09-110">In addition, set the `propagateActivity` attribute for the `System.ServiceModel` trace source at all endpoints.</span></span>  
  
```xml  
<source name="System.ServiceModel" switchValue="Verbose,ActivityTracing" propagateActivity="true" >  
```  
  
 <span data-ttu-id="80f09-111">La propagation d’activité est une fonctionnalité configurable qui amène WCF à ajouter un en-tête aux messages sortants, qui comprend l’ID d’activité sur le TLS.</span><span class="sxs-lookup"><span data-stu-id="80f09-111">Activity propagation is a configurable capability that causes WCF to add a header to outbound messages, which includes the activity ID on the TLS.</span></span> <span data-ttu-id="80f09-112">En incluant ces informations dans les suivis ultérieurs sur le côté serveur, il est possible de mettre en corrélation les activités de client et de serveur.</span><span class="sxs-lookup"><span data-stu-id="80f09-112">By including this on subsequent traces on the server side, we can correlate client and server activities.</span></span>  
  
## <a name="propagation-definition"></a><span data-ttu-id="80f09-113">Définition de la propagation</span><span class="sxs-lookup"><span data-stu-id="80f09-113">Propagation Definition</span></span>  

 <span data-ttu-id="80f09-114">Le gAId de l'activité M est propagé à l'activité N si toutes les conditions suivantes s'appliquent.</span><span class="sxs-lookup"><span data-stu-id="80f09-114">Activity M’s gAId is propagated to activity N if all of the following conditions apply.</span></span>  
  
- <span data-ttu-id="80f09-115">N est créé à cause de M</span><span class="sxs-lookup"><span data-stu-id="80f09-115">N is created because of M</span></span>  
  
- <span data-ttu-id="80f09-116">Le gAId de M est connu de N</span><span class="sxs-lookup"><span data-stu-id="80f09-116">M’s gAId is known to N</span></span>  
  
- <span data-ttu-id="80f09-117">Le gAId de N est égal au gAId de M.</span><span class="sxs-lookup"><span data-stu-id="80f09-117">N's gAId is equal to M’s gAId.</span></span>  
  
 <span data-ttu-id="80f09-118">Le gAId est propagé par l'en-tête de message ActivityId, comme illustré dans le schéma XML suivant.</span><span class="sxs-lookup"><span data-stu-id="80f09-118">The gAId is propagated through the ActivityId message header, as illustrated in the following XML schema.</span></span>  
  
```xml  
<xsd:element name="ActivityId" type="integer" minOccurs="0">  
  <xsd:attribute name="CorrelationId" type="integer" minOccurs="0"/>  
</xsd:element>  
```  
  
 <span data-ttu-id="80f09-119">Les éléments suivants sont un exemple de l'en-tête de message.</span><span class="sxs-lookup"><span data-stu-id="80f09-119">The following is an example of the message header.</span></span>  
  
```xml  
<MessageLogTraceRecord>  
  <s:Envelope xmlns:s="http://www.w3.org/2003/05/soap-envelope"
                      xmlns:a="http://www.w3.org/2005/08/addressing">  
    <s:Header>  
      <a:Action s:mustUnderstand="1">http://Microsoft.ServiceModel.Samples/ICalculator/Subtract  
      </a:Action>  
      <a:MessageID>urn:uuid:f0091eae-d339-4c7e-9408-ece34602f1ce  
      </a:MessageID>  
      <ActivityId CorrelationId="f94c6af1-7d5d-4295-b693-4670a8a0ce34"
               xmlns="http://schemas.microsoft.com/2004/09/ServiceModel/Diagnostics">  
        17f59a29-b435-4a15-bf7b-642ffc40eac8  
      </ActivityId>  
      <a:ReplyTo>  
          <a:Address>http://www.w3.org/2005/08/addressing/anonymous</a:Address>  
      </a:ReplyTo>  
      <a:To s:mustUnderstand="1">net.tcp://localhost/servicemodelsamples/service</a:To>  
   </s:Header>  
   <s:Body>  
     <Subtract xmlns="http://Microsoft.ServiceModel.Samples">  
       <n1>145</n1>  
       <n2>76.54</n2>  
     </Subtract>  
   </s:Body>  
  </s:Envelope>  
</MessageLogTraceRecord>  
```  
  
## <a name="propagation-and-activity-boundaries"></a><span data-ttu-id="80f09-120">Limites de propagation et d'activité</span><span class="sxs-lookup"><span data-stu-id="80f09-120">Propagation and Activity Boundaries</span></span>  

 <span data-ttu-id="80f09-121">Lorsque l'ID d'activité est propagé sur des points de terminaison, le récepteur de message émet un suivi de démarrage et d'arrêt avec cet ID d'activité (propagé).</span><span class="sxs-lookup"><span data-stu-id="80f09-121">When the activity ID is propagated across endpoints, the message receiver emits a Start and Stop traces with that (propagated) activity ID.</span></span> <span data-ttu-id="80f09-122">Par conséquent, il y a un suivi de démarrage et d'arrêt avec ce gAId à partir de chaque source de suivi.</span><span class="sxs-lookup"><span data-stu-id="80f09-122">Therefore, there is a Start and Stop trace with that gAId from each trace source.</span></span> <span data-ttu-id="80f09-123">Si les points de terminaison sont dans le même processus et utilisent le même nom de source de suivi, plusieurs suivis Démarrer et Arrêter ayant le même lAId (gAId identique, source de suivi et processus identiques) sont créés.</span><span class="sxs-lookup"><span data-stu-id="80f09-123">If the endpoints are in the same process and use the same trace source name, multiple Start and Stop with the same lAId (same gAId, same trace source, same process) are created.</span></span>  
  
## <a name="synchronization"></a><span data-ttu-id="80f09-124">Synchronization</span><span class="sxs-lookup"><span data-stu-id="80f09-124">Synchronization</span></span>  

 <span data-ttu-id="80f09-125">Pour synchroniser des événements sur les points de terminaison qui s’exécutent sur des ordinateurs différents, CorrelationId est ajouté à l’en-tête ActivityId propagé dans les messages.</span><span class="sxs-lookup"><span data-stu-id="80f09-125">To synchronize events across endpoints that run on different machines, a CorrelationId is added to the ActivityId header that is propagated in messages.</span></span> <span data-ttu-id="80f09-126">Les outils peuvent utiliser cet ID pour synchroniser des événements sur des ordinateurs présentant des différences d'horloge.</span><span class="sxs-lookup"><span data-stu-id="80f09-126">Tools can use this ID to synchronize events across machines with clock discrepancy.</span></span> <span data-ttu-id="80f09-127">En particulier, l'outil Service Trace Viewer utilise cet ID pour afficher les flux de messages d'un point de terminaison à un autre.</span><span class="sxs-lookup"><span data-stu-id="80f09-127">Specifically, the Service Trace Viewer tool uses this ID for showing message flows between endpoints.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="80f09-128">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="80f09-128">See also</span></span>

- [<span data-ttu-id="80f09-129">Configuration du traçage</span><span class="sxs-lookup"><span data-stu-id="80f09-129">Configuring Tracing</span></span>](configuring-tracing.md)
- [<span data-ttu-id="80f09-130">Utilisation de Service Trace Viewer pour afficher les suivis corrélés et résoudre les problèmes</span><span class="sxs-lookup"><span data-stu-id="80f09-130">Using Service Trace Viewer for Viewing Correlated Traces and Troubleshooting</span></span>](using-service-trace-viewer-for-viewing-correlated-traces-and-troubleshooting.md)
- [<span data-ttu-id="80f09-131">Scénarios de suivi de bout en bout</span><span class="sxs-lookup"><span data-stu-id="80f09-131">End-To-End Tracing Scenarios</span></span>](end-to-end-tracing-scenarios.md)
- [<span data-ttu-id="80f09-132">Service Trace Viewer Tool (SvcTraceViewer.exe)</span><span class="sxs-lookup"><span data-stu-id="80f09-132">Service Trace Viewer Tool (SvcTraceViewer.exe)</span></span>](../../service-trace-viewer-tool-svctraceviewer-exe.md)
