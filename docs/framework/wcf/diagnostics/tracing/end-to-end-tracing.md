---
title: Suivi de bout en bout
ms.date: 03/30/2017
ms.assetid: f5ac7fc7-f97c-4313-b068-54e0c471b2aa
ms.openlocfilehash: fc8fc448bdcf94ab25349f6b34961a34e5ed2a5a
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84598578"
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
- [Outil Service Trace Viewer (SvcTraceViewer.exe)](../../service-trace-viewer-tool-svctraceviewer-exe.md)
