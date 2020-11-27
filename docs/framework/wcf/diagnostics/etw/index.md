---
title: Traçage analytique avec ETW
ms.date: 03/30/2017
helpviewer_keywords:
- diagnostics [WCF], analytic tracing
- administration [WCF], analytic tracing
- analytic tracing [WCF]
ms.assetid: 1d518e47-a38d-41e8-93d7-8c3b361f6a56
ms.openlocfilehash: 4bb31eeac7c5d3c8c30f66090b07de9f8af4d5a4
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96274619"
---
# <a name="analytic-tracing-with-etw"></a>Traçage analytique avec ETW

Le suivi analytique Windows Communication Foundation (WCF) offre un moyen de capturer des informations de diagnostic pendant l’exécution d’un service WCF. Les événements de traçage analytique WCF sont émis à des points clés dans la pile WCF pour permettre la résolution des problèmes des services WCF dans un environnement de production. Le suivi analytique pour les services WCF a un impact minimal sur les performances d’un serveur de produit qui héberge les [!INCLUDE[netfx_current_long](../../../../../includes/netfx-current-long-md.md)] services WCF, car ces événements sont émis très efficacement dans une session suivi d’v nements pour Windows (ETW).  
  
## <a name="in-this-section"></a>Dans cette section  

 [Vue d'ensemble du traçage analytique](analytic-tracing-overview.md)  
 Décrit le fonctionnement du traçage analytique WCF dans [!INCLUDE[netfx_current_long](../../../../../includes/netfx-current-long-md.md)] .  
  
 [Activation dynamique du traçage analytique](dynamically-enabling-analytic-tracing.md)  
 Explique comment activer ou désactiver le traçage de manière dynamique à l'aide d'ETW.  
  
 [Configuration du suivi de flux de messages](configuring-message-flow-tracing.md)  
 Décrit comment configurer le traçage du flux des messages.  
  
 [Référence d'événement de trace analytique](analytic-trace-event-reference.md)  
 Affiche une table d'ID d'événements avec leurs niveaux d'événements, leurs messages d'événements et leurs mots clés.  
  
## <a name="see-also"></a>Voir aussi

- [WCF Services et suivi d'événements Windows](../../samples/wcf-services-and-event-tracing-for-windows.md)
- [Événements de suivi dans Event Tracing for Windows](../../../windows-workflow-foundation/samples/tracking-events-into-event-tracing-in-windows.md)
