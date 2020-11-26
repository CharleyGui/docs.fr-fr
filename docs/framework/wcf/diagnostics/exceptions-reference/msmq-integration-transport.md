---
title: Transport d'intégration MSMQ
ms.date: 03/30/2017
ms.assetid: 2bf9893a-fbd1-41fc-b6de-a41a44279936
ms.openlocfilehash: 032b6886152fb73c382fed1572e8c184a822b44f
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96248745"
---
# <a name="msmq-integration-transport"></a>Transport d'intégration MSMQ

Cette rubrique répertorie toutes les exceptions générées par le transport d'intégration MSMQ.  
  
## <a name="exception-list"></a>Liste des exceptions  
  
|Code de la ressource|Chaîne de la ressource|  
|-------------------|---------------------|  
|MessageSizeMustBeInIntegerRange|Cette fabrique mettant en mémoire tampon des messages, la taille des messages doit donc se trouver dans la plage d'une valeur entière.|  
|MsmqByteArrayBodyExpected|Une incompatibilité s'est produite entre le format de sérialisation spécifié et le corps du message MSMQ. Le message ne peut pas être envoyé ou reçu. Le format de sérialisation ByteArray requiert que le corps du message MSMQ soit de type byte[].|  
|MsmqCannotDeserializeActiveXMessage|Une erreur de sérialisation ActiveX s'est produite. Le message ne peut pas être envoyé ou reçu. Le type de variant spécifié pour le corps ne correspond pas au corps du message MSMQ réel.|  
|MsmqCannotUseBodyTypeWithActiveXSerialization|Les propriétés du message sont incompatibles. Le message ne peut pas être envoyé ou reçu. La propriété de message BodyType ne peut pas être spécifiée si le format de sérialisation ActiveX est utilisé.|  
|MsmqInvalidServiceOperationForMsmqIntegrationBinding|La validation de MsmqIntegrationBinding a échoué. Impossible de démarrer le point de terminaison de service. La liaison ne prend pas en charge la signature de méthode pour l'opération de service spécifiée dans le contrat. Corrigez l'opération de service afin d'utiliser MsmqIntegrationBinding.|  
|MsmqInvalidTypeDeserialization|La sérialisation ActiveX a échoué car le format de sérialisation ne peut pas être reconnu. Le message ne peut pas être envoyé ou reçu.|  
|MsmqInvalidTypeSerialization|Le type de variant n'est pas reconnu. La sérialisation ActiveX a échoué. Le message ne peut pas être envoyé ou reçu. Le type de variant spécifié n'est pas pris en charge.|  
|MsmqStreamBodyExpected|Incompatibilité entre le format de sérialisation et le contenu du corps. Le message ne peut pas être envoyé ou reçu. Seul un corps de type flux peut être envoyé ou reçu à l'aide du mode de sérialisation du flux.|
