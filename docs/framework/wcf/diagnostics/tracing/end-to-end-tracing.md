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
# <a name="end-to-end-tracing"></a>Suivi de bout en bout

Le suivi de bout en bout (E2E) permet aux développeurs de suivre l’exécution du code dans l’infrastructure Windows Communication Foundation (WCF) pour rechercher la raison de l’échec d’un chemin de code ou pour fournir un suivi détaillé pour la planification de la capacité et l’analyse des performances. Windows Communication Foundation (WCF) fournit trois mécanismes de corrélation pour aider à diagnostiquer la cause d’une erreur : activités, transferts et propagation.  
  
 Consultez [scénarios de suivi de bout](end-to-end-tracing-scenarios.md) en bout pour obtenir une liste de scénarios de suivi de bout en bout, ainsi que leur conception d’activité et de suivi respective.  
  
## <a name="in-this-section"></a>Dans cette section  

 [Activity](activity.md): décrit les suivis d’activité dans le modèle de suivi Windows Communication Foundation (WCF).  
  
 [Transfert](transfer.md): décrit le transfert dans le modèle de suivi Windows Communication Foundation (WCF) et l’utilisation de Transfer pour mettre en corrélation les activités au sein des points de terminaison.  
  
 [Propagation](propagation.md): décrit la propagation d’activité dans le modèle de suivi Windows Communication Foundation (WCF) et l’utilisation de la propagation pour corréler des activités sur des points de terminaison.  
  
 [Liste des types de suivis](trace-type-summary.md)  
  
 Fournit un résumé de tous les types de suivi d'activité  
  
## <a name="see-also"></a>Voir aussi

- [Configuration du traçage](configuring-tracing.md)
- [Utilisation de Service Trace Viewer pour afficher les suivis corrélés et résoudre les problèmes](using-service-trace-viewer-for-viewing-correlated-traces-and-troubleshooting.md)
- [Scénarios de suivi de bout en bout](end-to-end-tracing-scenarios.md)
- [Service Trace Viewer Tool (SvcTraceViewer.exe)](../../service-trace-viewer-tool-svctraceviewer-exe.md)
