---
title: Journalisation des événements dans WCF
ms.date: 03/30/2017
helpviewer_keywords:
- event logging [WCF]
ms.assetid: aac0530d-f44c-45a1-bada-e30e0677b41f
ms.openlocfilehash: 535b3570f41cbfb277eeb14fb07242b528acea46
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96236154"
---
# <a name="event-logging-in-wcf"></a>Journalisation des événements dans WCF

Windows Communication Foundation (WCF) effectue le suivi des événements internes dans le journal des événements Windows.  
  
## <a name="viewing-event-logs"></a>Consultation des journaux des événements  

 La journalisation des événements est activée automatiquement par défaut et il n'existe aucun mécanisme pour la désactiver. Les événements journalisés par WCF peuvent être affichés à l’aide du observateur d’événements. Pour lancer cet outil, cliquez sur **Démarrer**, sur **panneau de configuration**, double-cliquez sur **Outils d’administration**, puis double-cliquez sur **Observateur d’événements**.  
  
### <a name="application-event-log"></a>Journal des événements de l'application  

 Le **Journal des événements d’application** contient la plupart des événements générés par WCF. La plupart des entrées indiquent qu'une fonctionnalité particulière n'a pas réussi à démarrer pour une application. Voici quelques exemples :  
  
- Journalisation/suivi des messages : WCF écrit un événement dans le journal des événements en cas d’échec de la journalisation des messages et des traces. Toutefois, tous les échecs de suivi ne déclenchent pas un événement. Pour empêcher le journal des événements d’être complètement rempli avec des échecs de suivi, WCF implémente une période d’indisponibilité de 10 minutes pour ce type d’événement. Cela signifie que si WCF écrit un échec de trace dans le journal des événements, il ne le fera pas à nouveau pendant au moins 10 minutes.  
  
- Écouteur partagé : le service de partage de ports TCP WCF journalise un événement lorsqu'il ne réussit pas à démarrer.  
  
- CardSpace : journalise des événements lorsque le service ne parvient pas à démarrer.  
  
- Événements critiques et erreurs, tels que les échecs de démarrage ou les blocages  
  
- Journalisation des messages activée : journalise des événements lorsque la journalisation des messages est activée. L'objectif consiste à avertir l'administrateur que des informations sensibles et spécifiques à l'application peuvent être journalisées dans les en-têtes et les corps des messages.  
  
- Un événement est journalisé lorsque l'attribut `enableLoggingKnownPII` de l'élément `machineSettings` du fichier `machine.config` est défini. Cet attribut indique si toute application qui s'exécute sur l'ordinateur est autorisée à journaliser des informations d'identification personnelle connues.  
  
- Si l'attribut `logKnownPii` dans le fichier `app.config` ou `web.config` a la valeur `true` pour qu'une application spécifique active la journalisation des informations d'identification personnelle, mais que l'attribut `enableLoggingKnownPII` dans l'élément `machineSettings` du fichier `machine.config` a la valeur `false`, un événement est journalisé. En outre, si `logKnownPii` et `enableLoggingKnownPII` ont la valeur `true`, un événement est journalisé. Pour plus d’informations sur ces paramètres de configuration, consultez la section sécurité de la rubrique Configuration de l' [enregistrement des messages](../configuring-message-logging.md) .  
  
### <a name="security-event-log"></a>Journal des événements de sécurité  

 Le **Journal des événements de sécurité** contient les événements d’audit de sécurité enregistrés par WCF.  
  
### <a name="system-event-log"></a>Journal des événements système  

 WCF n’enregistre rien dans le **Journal des événements système**.  
  
### <a name="event-log-entries"></a>Entrées de journal des événements  

 La **source** d’un événement est le nom de l’assembly qui génère l’entrée de journal.  
  
 Le type d'une entrée de journal des événements est utilisé pour indiquer la gravité d'un événement. Chaque événement doit posséder un type unique indiqué par l'application lorsqu'elle signale l'événement. L'observateur d'événements utilise ce type pour déterminer l'icône à afficher dans la vue Liste du journal. Pour connaître les différents types d'événements d'une entrée de journal des événements, consultez <xref:System.Diagnostics.EventLogEntryType>.  
  
 Lorsque vous cliquez sur « plus d’informations » lors de l’affichage d’un événement dans la observateur d’événements, le observateur d’événements peut envoyer des informations sur Internet. Pour plus d'informations, consultez l'aide de l'Observateur d'événements.  
  
## <a name="see-also"></a>Voir aussi

- [Administration et diagnostics](../index.md)
- [Référence générale relative aux événements](events-general-reference.md)
