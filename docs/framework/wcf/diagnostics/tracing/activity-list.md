---
title: Liste des activités
ms.date: 03/30/2017
ms.assetid: 5540e185-ce8e-4db3-83b0-2b9f5bf71829
ms.openlocfilehash: d28ae2e4750c718c35105d090aff8d085025b9d6
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96236089"
---
# <a name="activity-list"></a>Liste des activités

Cette rubrique répertorie toutes les activités définies par Windows Communication Foundation (WCF).  
  
> [!NOTE]
> Vous pouvez également définir des activités par programme pour grouper des suivis utilisateur. Pour plus d’informations, consultez [émission de suivis de User-Code](emitting-user-code-traces.md).  
  
## <a name="servicemodel-activities"></a>Activités ServiceModel  

 Le tableau suivant répertorie toutes les activités pour les principaux scénarios d'utilisation.  
  
|Étiquette|Nom de l’activité|Type d’activité|Description|  
|-----------|-------------------|-------------------|-----------------|  
|A, M|Activité ambiante|N/A (non contrôlé par ServiceModel)|Activité dont l'ID est défini dans TLS avant les appels au code ServiceModel (côté client ou côté serveur).<br /><br /> Exemple : une activité où Open est appelé sur le client WCF ou serviceHost. Open est appelé.|  
|B|Construction<br /><br /> ChannelFactory. ContractType : '[Type]'.|Construction||  
|C|Ouvrir<br /><br /> [ClientBase&#124;ChannelFactory]. ContractType : '[Type]'.|Ouvrir||  
|I|Fermer [ClientBase&#124;ChannelFactory]. ContractType : '[Type]'.|Fermer||  
|M|Construire ServiceHost. ServiceType: '[Type]'.|Construction||  
|N|Ouvrir ServiceHost. ServiceType: '[Type]'.|Ouvrir||  
|Z|Fermer ServiceHost. ServiceType: '[Type]'.|Fermer||  
|O|Écouter à '[address]'.|ListenAt|Cette activité et la suivante sont spécifiques au transport. L'activité ListenAt représente le contenu qui mappe à l'adresse à laquelle l'écouteur de canal écoute. Dans le cas de MSMQ, c'est la file d'attente elle-même qui depuis la file d'attente mappe à une adresse. Cette activité écoute les connexions entrantes dans le cas des transports orientés connexion, et les messages MSMQ dans le cas de MSMQ. Cette activité est créée pendant ServiceHost.Open (), et contient les suivis relatifs à la création et à la suppression de l'écouteur, ainsi qu'au transfert vers toutes les activités ReceiveBytes.|  
|P|Recevoir les octets sur la connexion '[address]'. Recevoir le message MSMQ.|ReceiveBytes|Dans cette activité, les données qui finissent par obtenir un message WCF sont traitées. Des octets entrants sont attendus dans le cas du transport orienté connexion ou http. Pour le TCP/canal nommé, la durée de vie de cette activité correspond à celle de la connexion, car elle est créée à la création de la connexion. Pour http, elle correspond à la durée de vie d'une demande de message et est créée à l'envoi du message. Cette activité contient les suivis relatifs à la création et à la suppression de la connexion le cas échéant, ainsi qu'aux transferts vers toutes les activités de traitement (objet) des messages.<br /><br /> Dans le cas de MSMQ, il s'agit de l'activité dans laquelle le message MSMQ est récupéré.|  
|Q|Traiter le message [number]. (Notez que [number] est une valeur qui augmente de manière monotone et commence à 1.)|ProcessMessage|Cette activité traite un message entrant. Cette activité démarre lorsque toutes les données (octets, message MSMQ) sont reçues pour former un objet message WCF. Les suivis dans cette activité gèrent le traitement d'en-tête.<br /><br /> Une fois qu'un message pouvant être distribué est formé, l'activité de ServiceHost ProcessAction est basculée après avoir recherché l'ID d'activité correspondant.|  
|D, S|Traiter l'action '[action]'.|ProcessAction|Cette activité traite le message via la pile Transport/Security/RM permettant de distribuer le message au code utilisateur lors de la réception, et dans l'ordre inverse lors de l'envoi.<br /><br /> Sur le serveur, cette activité utilise l’ID d’activité propagée s’il est envoyé dans l’en-tête de message via la « propagation d’activité ». dans le cas contraire, un nouveau GUID est créé.<br /><br /> Le message de réponse pour les contrats demande/réponse est également traité dans cette activité.|  
|T|Exécuter '[IContract.Operation]'.|ExecuteUserCode|Cette activité exécute le code utilisateur après distribution sur le côté service. Elle fournit une limite permettant de définir le code ServiceHost à partir du code fourni par l'utilisateur.|  
  
## <a name="security-activities"></a>Activités de sécurité  

 Le tableau suivant répertorie l'ensemble des activités relatives à la sécurité.  
  
|Nom de l’activité|Type d’activité|Description|  
|-------------------|-------------------|-----------------|  
|Installer la session sécurisée|SetupSecurity|Existe uniquement sur le côté client. Contient tous les échanges RST*/SCT pour l'authentification et la définition du contexte de sécurité. Si `propagateActivity` = `true` la méthode est, cette activité est fusionnée avec les activités de processus d’action RST/SCT correspondantes du service correspondantes \* .|  
|Fermer la session sécurisée|SetupSecurity|Existe sur le côté client. Contient l'échange de messages Cancel permettant de fermer la session sécurisée. Si `propagateActivity` = `true` , cette activité est fusionnée avec l’action de traitement « annuler » à partir du service.|  
  
 Le tableau suivant répertorie l'ensemble des activités relatives à COM+.  
  
|Nom de l’activité|Type d’activité|Description|  
|-------------------|-------------------|-----------------|  
|Créer une instance COM+|TransferToCOMPlus|1 instance d’activité pour chaque appel COM+ à partir du code WCF|  
|Exécuter COM+ \<operation>|TransferToCOMPlus|1 instance d’activité pour chaque appel COM+ à partir du code WCF|  
  
## <a name="wmi-activities"></a>Activités WMI  

 Le tableau suivant répertorie l'ensemble des activités relatives WMI.  
  
|Nom de l’activité|Type d’activité|Description|  
|-------------------|-------------------|-----------------|  
|Récupération WMI|WMIGetObject|L'utilisateur récupère des données de WMI.|  
|Mise à jour WMI|WmiPutInstance|L'utilisateur met à jour des données avec WMI.|
