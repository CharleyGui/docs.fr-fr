---
title: Traçage analytique avec ETW
ms.date: 03/30/2017
helpviewer_keywords:
- diagnostics [WCF], analytic tracing
- administration [WCF], analytic tracing
- analytic tracing [WCF]
ms.assetid: 1d518e47-a38d-41e8-93d7-8c3b361f6a56
ms.openlocfilehash: dd745730ca186b9489c547f790c546e95bf96372
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70798093"
---
# <a name="analytic-tracing-with-etw"></a>Traçage analytique avec ETW
Le suivi analytique Windows Communication Foundation (WCF) offre un moyen de capturer des informations de diagnostic pendant l’exécution d’un service WCF. Les événements de traçage analytique WCF sont émis à des points clés dans la pile WCF pour permettre la résolution des problèmes des services WCF dans un environnement de production. Le suivi analytique pour les services WCF a un impact minimal sur les performances d’un serveur [!INCLUDE[netfx_current_long](../../../../../includes/netfx-current-long-md.md)] de produit qui héberge les services WCF, car ces événements sont émis très efficacement dans une session suivi d’v nements pour Windows (ETW).  
  
## <a name="in-this-section"></a>Dans cette section  
 [Vue d’ensemble du suivi analytique](analytic-tracing-overview.md)  
 Décrit le fonctionnement du traçage analytique WCF dans [!INCLUDE[netfx_current_long](../../../../../includes/netfx-current-long-md.md)].  
  
 [Activation dynamique du suivi analytique](dynamically-enabling-analytic-tracing.md)  
 Explique comment activer ou désactiver le traçage de manière dynamique à l'aide d'ETW.  
  
 [Configuration du suivi de flux de messages](configuring-message-flow-tracing.md)  
 Décrit comment configurer le traçage du flux des messages.  
  
 [Informations de référence sur les événements de suivi analytique](analytic-trace-event-reference.md)  
 Affiche une table d'ID d'événements avec leurs niveaux d'événements, leurs messages d'événements et leurs mots clés.  
  
## <a name="see-also"></a>Voir aussi

- [Services WCF et suivi des événements pour Windows](../../samples/wcf-services-and-event-tracing-for-windows.md)
- [Événements de suivi dans Event Tracing for Windows](../../../windows-workflow-foundation/samples/tracking-events-into-event-tracing-in-windows.md)
