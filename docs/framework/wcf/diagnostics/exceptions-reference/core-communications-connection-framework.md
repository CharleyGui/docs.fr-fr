---
title: 'Communications principales : Framework de connexion'
ms.date: 03/30/2017
ms.assetid: 61ee00e1-896d-47c8-942f-1db28ac89cdc
ms.openlocfilehash: bd90bf75370776382b584388330e59a0701ed772
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96277502"
---
# <a name="core-communications-connection-framework"></a>Communications principales : Framework de connexion

Cette rubrique répertorie toutes les exceptions générées par l’infrastructure de connexion Windows Communication Foundation (WCF).  
  
## <a name="exception-list"></a>Liste des exceptions  
  
|Code de la ressource|Chaîne de la ressource|  
|-------------------|---------------------|  
|CloseTimedOut|La méthode Close a expiré après l'heure spécifiée. Augmentez la valeur du délai d’attente de l’appel à la méthode Close ou la valeur CloseTimeout sur la liaison. Le temps alloué à cette opération peut avoir été une partie d'un délai d'expiration plus long.|  
|ContentTypeMismatch|Le type de contenu spécifié a été envoyé à un service qui attendait . Il se peut que les liaisons client et service ne se correspondent pas.|  
|DuplexChannelAbortedDuringOpen|Le canal duplex vers s'est fermé pendant le processus Open.|  
|FramingValueNotAvailable|La valeur n'est pas accessible parce qu'elle n'est pas complètement décodée.|  
|OperationAbortedDuringConnectionEstablishment|L'opération a pris pendant l'établissement d'une connexion à .|  
|ReceiveTimedOut2|L'opération de réception a dépassé le délai imparti. Le temps alloué à cette opération peut avoir été une partie d'un délai d'expiration plus long.|  
|SendCannotBeCalledAfterCloseOutputSession|Vous ne pouvez pas envoyer des messages sur un canal après que CloseOutputSession a été appelée.|
