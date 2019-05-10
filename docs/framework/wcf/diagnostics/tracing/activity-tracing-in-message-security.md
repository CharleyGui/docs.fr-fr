---
title: Suivi d'activité dans la sécurité de message
ms.date: 03/30/2017
ms.assetid: 68862534-3b2e-4270-b097-8121b12a2c97
ms.openlocfilehash: 65b2842c57da8e17c7280a2becd755ba2aae8364
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64656451"
---
# <a name="activity-tracing-in-message-security"></a>Suivi d'activité dans la sécurité de message
Cette rubrique décrit le suivi d'activité pour le traitement de sécurité, qui se produit dans les trois phases suivantes.  
  
- Échange de négociation/SCT. Cela peut se produire au niveau de la couche de transport (via l'échange de données binaires) ou de la couche de message (via les échanges de messages SOAP).  
  
- Chiffrement/déchiffrement des messages, avec vérification et authentification de la signature. Les suivis apparaissent dans l'activité ambiante, en général l'activité « Action de processus ».  
  
- Autorisation et vérification. Cela peut se produire localement ou lors de la communication entre des points de terminaison.  
  
## <a name="negotiationsct-exchange"></a>Échange de négociation/SCT  
 Dans la phase d’échange de négociation/SCT, deux types d’activité sont créés sur le client : « Configurer une Session sécurisée » et « Fermer une Session sécurisée. » Le type « Configurer une session sécurisée » comprend des suivis pour les échanges de messages RST/RSTR/SCT, tandis que le type « Fermer une session sécurisée » inclut des suivis pour le message Cancel.  
  
 Sur le serveur, chaque demande/réponse pour les échanges RST/RSTR/SCT apparaît dans sa propre activité. Si `propagateActivity` = `true` sur le serveur et client, les activités sur le serveur ont le même ID et apparaissent ensemble dans le « le programme d’installation une Session sécurisée » lorsqu’ils sont affichés avec Service Trace Viewer.  
  
 Ce modèle d'activité de suivi est valide pour l'authentification par nom d'utilisateur/mot de passe, l'authentification du certificat et l'authentification NTLM.  
  
 Le tableau suivant répertorie les activités et les suivis pour l'échange de négociation/SCT.  
  
||Occurrence de l'échange de négociation/SCT|Activités|Suivis|  
|-|-------------------------------------------------|----------------|------------|  
|Transport sécurisé<br /><br /> (HTTPS, SSL)|À réception du premier message.|Les suivis sont émis dans l'activité ambiante.|-Les traces Exchange<br />-Canal sécurisé établi<br />-Partager les secrets obtenus.|  
|Couche de message sécurisée<br /><br /> (WSHTTP)|À réception du premier message.|Sur le client :<br /><br /> -« Le programme d’installation Session sécurisée » depuis « Action de processus » de ce premier message, pour chaque demande/réponse pour RST/RSTR/SCT.<br />-« Fermer une Session sécurisée » pour l’échange CANCEL, en dehors de l’activité « fermer le Proxy ». Cette activité peut provenir d'une autre activité ambiante, selon le moment où la session sécurisée est fermée.<br /><br /> Sur le serveur :<br /><br /> -Activité « Traiter l’Action » un pour chaque demande/réponse pour RST/SCT/Cancel sur le serveur. Si `propagateActivity` = `true`, les activités RST/RSTR/SCT sont fusionnées avec « Configurer une Session sécurisée » et Cancel est fusionnée avec l’activité « Fermeture » à partir du client.<br /><br /> Il y a deux étapes pour « Configurer une session sécurisée » :<br /><br /> 1.  Négociation de l'authentification. Facultatif si le client a déjà les informations d'identification qui conviennent. Cette phase peut être accomplie par un transport sécurisé, ou par des échanges de messages. Dans ce dernier cas, 1 ou 2 échanges RST/RSTR peuvent se produire. Pour ces échanges, les suivis sont émis dans de nouvelles activités de demande/réponse comme prévu.<br />2.  Établissement de session sécurisée (SCT), dans laquelle un échange RST/RSTR se produit. A les mêmes activités ambiantes que celles décrites précédemment.|-Les traces Exchange<br />-Canal sécurisé établi<br />-Partager les secrets obtenus.|  
  
> [!NOTE]
>  En mode de sécurité mixte, l'authentification de négociation survient dans les échanges binaires, mais le SCT survient dans l'échange de messages. En mode de transport pur, la négociation survient uniquement dans le transport sans activités supplémentaires.  
  
## <a name="message-encryption-and-decryption"></a>Chiffrement et déchiffrement des messages  
 Le tableau suivant répertorie les activités et les suivis pour le chiffrement/déchiffrement des messages, ainsi que l'authentification de signature.  
  
||Transport sécurisé<br /><br /> (HTTPS, SSL) et couche de message sécurisée<br /><br /> (WSHTTP)|  
|-|---------------------------------------------------------------------------------|  
|Heure à laquelle surviennent le chiffrement/déchiffrement des message et l'authentification de la signature.|À réception du message|  
|Activités|Les suivis sont émis dans l'activité ProcessAction sur le client et le serveur.|  
|Suivis|-   sendSecurityHeader (sender):<br />-Signer le message<br />-Chiffrer les données de la demande<br />-   receiveSecurityHeader (receiver):<br />-Vérifier la signature<br />-Déchiffrer les données de réponse<br />-   Authentication|  
  
> [!NOTE]
>  En mode de transport pur, le chiffrement/déchiffrement des messages se produit uniquement dans le transport sans activités supplémentaires.  
  
## <a name="authorization-and-verification"></a>Autorisation et vérification  
 Le tableau suivant répertorie les activités et les suivis pour l'autorisation.  
  
||Occurrence de l'autorisation|Activités|Suivis|  
|-|-------------------------------------|----------------|------------|  
|Local (valeur par défaut)|Après que le message a été déchiffré sur le serveur|Les suivis sont émis dans l'activité ProcessAction au niveau du serveur.|Utilisateur autorisé.|  
|Remote|Après que le message a été déchiffré sur le serveur|Les suivis sont émis dans une nouvelle activité appelée par l'activité ProcessAction.|Utilisateur autorisé.|
