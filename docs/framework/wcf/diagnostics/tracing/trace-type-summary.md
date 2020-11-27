---
title: Liste des types de suivis
ms.date: 03/30/2017
ms.assetid: e639410b-d1d1-479c-b78e-a4701d4e4085
ms.openlocfilehash: e8d222d6f093f5db3bd620194bfde7edd4b998a8
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96259243"
---
# <a name="trace-type-summary"></a>Liste des types de suivis

Les [niveaux source](xref:System.Diagnostics.SourceLevels) définissent différents niveaux de suivi : critique, erreur, avertissement, informations et commentaires. ils fournissent également une description de l' `ActivityTracing` indicateur, qui bascule la sortie des événements de limite de suivi et de transfert d’activité.  
  
 Vous pouvez également passer en revue <xref:System.Diagnostics.TraceEventType> les types de traces qui peuvent être émis à partir de <xref:System.Diagnostics> .  
  
 Le tableau suivant répertorie les plus importants.  
  
|Type de suivi|Description|  
|----------------|-----------------|  
|Critique|Erreur irrécupérable ou panne d'application.|  
|Error|Erreur récupérable.|  
|Avertissement|Message d’information.|  
|Informations|Problème non critique.|  
|Commentaires|Suivi de débogage.|  
|Démarrer|Démarrage d'une unité logique de traitement.|  
|Interrompre|Interruption d'une unité logique de traitement.|  
|Reprendre|Reprise d'une unité logique de traitement.|  
|Arrêter|Arrêt d'une unité logique de traitement.|  
|Transférer|Changement d'identité de corrélation.|  
  
 Une activité est définie comme une combinaison des types de suivi ci-dessus.  
  
 Le code suivant est une expression régulière qui définit une activité idéale dans une étendue locale (source de suivi).  
  
 `R = Start (Critical | Error | Warning | Information | Verbose | Transfer | (Transfer Suspend Transfer Resume) )* Stop`  
  
 Cela signifie qu'une activité doit remplir les conditions suivantes.  
  
- Elle doit respectivement démarrer et s'arrêter avec les suivis Démarrer et Arrêter.  
  
- Elle doit contenir un suivi Transfert immédiatement avant un suivi Interrompre ou Reprendre.  
  
- Elle ne doit pas contenir de suivi entre les suivis Interrompre et Reprendre, s'ils existent.  
  
- Elle peut contenir n'importe quel type de suivi Critique/Avertissement/Informations/Commentaires/Transfert, en nombre illimité, tant que les conditions précédentes sont observées.  
  
 Le code suivant est une expression régulière qui définit une activité idéale dans la portée globale,  
  
`R+`  
  
 R étant l'expression régulière d'une activité dans l'étendue locale. Cela se traduit par :  
  
`[R+ = Start ( Critical | Error | Warning | Information | Verbose | Transfer | (Transfer Suspend Transfer Resume) )* Stop]+`
