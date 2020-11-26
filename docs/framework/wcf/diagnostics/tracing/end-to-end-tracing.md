---
title: Suivi de bout en bout
ms.date: 03/30/2017
ms.assetid: f5ac7fc7-f97c-4313-b068-54e0c471b2aa
ms.openlocfilehash: a8c06b9e4f70321e6ef3756863390dc62c659557
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96243948"
---
# <a name="end-to-end-tracing"></a><span data-ttu-id="e8523-102">Suivi de bout en bout</span><span class="sxs-lookup"><span data-stu-id="e8523-102">End-to-End Tracing</span></span>

<span data-ttu-id="e8523-103">Le suivi de bout en bout (E2E) permet aux développeurs de suivre l’exécution du code dans l’infrastructure Windows Communication Foundation (WCF) pour rechercher la raison de l’échec d’un chemin de code ou pour fournir un suivi détaillé pour la planification de la capacité et l’analyse des performances.</span><span class="sxs-lookup"><span data-stu-id="e8523-103">End to End (e2e) Tracing allows developers to follow the execution of code in the Windows Communication Foundation (WCF) infrastructure to investigate why a code path has failed, or to provide detailed tracing for capacity planning and performance analysis.</span></span> <span data-ttu-id="e8523-104">Windows Communication Foundation (WCF) fournit trois mécanismes de corrélation pour aider à diagnostiquer la cause d’une erreur : activités, transferts et propagation.</span><span class="sxs-lookup"><span data-stu-id="e8523-104">Windows Communication Foundation (WCF) provides three correlation mechanisms to help diagnose the cause of an error: activities, transfers, and propagation.</span></span>  
  
 <span data-ttu-id="e8523-105">Consultez [scénarios de suivi de bout](end-to-end-tracing-scenarios.md) en bout pour obtenir une liste de scénarios de suivi de bout en bout, ainsi que leur conception d’activité et de suivi respective.</span><span class="sxs-lookup"><span data-stu-id="e8523-105">See [End-To-End Tracing Scenarios](end-to-end-tracing-scenarios.md) for a list of end-to-end tracing scenarios, and their respective activity and tracing design.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="e8523-106">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="e8523-106">In This Section</span></span>  

 <span data-ttu-id="e8523-107">[Activity](activity.md): décrit les suivis d’activité dans le modèle de suivi Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="e8523-107">[Activity](activity.md):  Describes activity traces in the Windows Communication Foundation (WCF) tracing model.</span></span>  
  
 <span data-ttu-id="e8523-108">[Transfert](transfer.md): décrit le transfert dans le modèle de suivi Windows Communication Foundation (WCF) et l’utilisation de Transfer pour mettre en corrélation les activités au sein des points de terminaison.</span><span class="sxs-lookup"><span data-stu-id="e8523-108">[Transfer](transfer.md):  Describes transfer in the Windows Communication Foundation (WCF) tracing model, and using transfer to correlate activities within endpoints.</span></span>  
  
 <span data-ttu-id="e8523-109">[Propagation](propagation.md): décrit la propagation d’activité dans le modèle de suivi Windows Communication Foundation (WCF) et l’utilisation de la propagation pour corréler des activités sur des points de terminaison.</span><span class="sxs-lookup"><span data-stu-id="e8523-109">[Propagation](propagation.md):  Describes activity propagation in the Windows Communication Foundation (WCF) tracing model, and using propagation to correlate activities across endpoints.</span></span>  
  
 [<span data-ttu-id="e8523-110">Liste des types de suivis</span><span class="sxs-lookup"><span data-stu-id="e8523-110">Trace Type Summary</span></span>](trace-type-summary.md)  
  
 <span data-ttu-id="e8523-111">Fournit un résumé de tous les types de suivi d'activité</span><span class="sxs-lookup"><span data-stu-id="e8523-111">Provides a summary of all activity trace types</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e8523-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e8523-112">See also</span></span>

- [<span data-ttu-id="e8523-113">Configuration du traçage</span><span class="sxs-lookup"><span data-stu-id="e8523-113">Configuring Tracing</span></span>](configuring-tracing.md)
- [<span data-ttu-id="e8523-114">Utilisation de Service Trace Viewer pour afficher les suivis corrélés et résoudre les problèmes</span><span class="sxs-lookup"><span data-stu-id="e8523-114">Using Service Trace Viewer for Viewing Correlated Traces and Troubleshooting</span></span>](using-service-trace-viewer-for-viewing-correlated-traces-and-troubleshooting.md)
- [<span data-ttu-id="e8523-115">Scénarios de suivi de bout en bout</span><span class="sxs-lookup"><span data-stu-id="e8523-115">End-To-End Tracing Scenarios</span></span>](end-to-end-tracing-scenarios.md)
- [<span data-ttu-id="e8523-116">Service Trace Viewer Tool (SvcTraceViewer.exe)</span><span class="sxs-lookup"><span data-stu-id="e8523-116">Service Trace Viewer Tool (SvcTraceViewer.exe)</span></span>](../../service-trace-viewer-tool-svctraceviewer-exe.md)
