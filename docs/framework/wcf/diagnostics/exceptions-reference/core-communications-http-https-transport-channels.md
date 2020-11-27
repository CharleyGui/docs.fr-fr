---
title: 'Communications principales : canaux de transport HTTP-HTTPs'
ms.date: 03/30/2017
ms.assetid: 6c0a23c9-a663-461c-bdab-58b4d3e23642
ms.openlocfilehash: 5d33d153c6c527398b035ad9d027593a0fefd0e8
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96277411"
---
# <a name="core-communications-httphttps-transport-channels"></a>Communications principales : Canaux de transport HTTP/HTTPS

Cette rubrique répertorie toutes les exceptions générées par les canaux de transport HTTP/HTTPs Windows Communication Foundation (WCF).  
  
## <a name="exception-list"></a>Liste des exceptions  
  
|Code de la ressource|Chaîne de la ressource|  
|-------------------|---------------------|  
|DigestExplicitCredsImpersonationLevel|Le niveau d'emprunt d'identité spécifié a été spécifié. L'authentification Digest HTTP prend en charge le niveau d'emprunt d'identité uniquement lorsque celui-ci est utilisé avec des informations d'identification explicites.|  
|FramingContentTypeMismatch|Le type de contenu spécifié n'est pas pris en charge par le service spécifié. Il se peut que les liaisons client et service ne se correspondent pas.|  
|Hosting_SslSettingsMisconfigured|Les paramètre SSL du service spécifié ne correspondent pas à ceux des services IIS.|  
|HttpAuthSchemeAndClientCert|La configuration de la fabrication d'écouteur HTTPS nécessite le recours à un certificat client ainsi qu'au schéma d'authentification spécifié. Cependant, un seul mode d'authentification client peut être utilisé à la fois.|  
|HttpReceiveFailure|Une erreur s'est produite lors de la réception de la réponse HTTP sur le spécifié. La liaison de point de terminaison de service n'utilise peut-être pas le protocole HTTP. Le serveur a peut-être également arrêté le contexte de requête HTTP à cause de la fermeture du service. Pour plus d'informations, consultez les journaux du serveur.|  
|HttpRegistrationAccessDenied|HTTP ne parvient pas à enregistrer l'adresse URL spécifiée. Votre processus ne dispose pas de droits d’accès à cet espace de noms (consultez [Réservations d’espace de noms, inscriptions et routage](/windows/desktop/http/namespace-reservations-registrations-and-routing) pour plus d’informations).|  
|HttpRegistrationAlreadyExists|HTTP ne parvient pas à enregistrer l'adresse URL spécifiée. Une autre application a déjà enregistré cette adresse URL avec HTTP.SYS.|  
|HttpRegistrationPortInUse|HTTP ne parvient pas à enregistrer l'adresse URL spécifiée car le port TCP indiqué est utilisé par une autre application. .|  
|HttpSendFailure|Une erreur s'est produite lors de la requête HTTP au spécifié. Assurez-vous qu’un éventuel problème de disparité au niveau des liaisons de sécurité n’est pas à l’origine de cette erreur. Assurez-vous également que la configuration du service ne requiert pas l'utilisation du protocole SSL.|  
|MessageXmlProtocolError|Un problème s'est produit au niveau du document XML reçu depuis le réseau. Pour plus d'informations, consultez l'exception interne.|  
|MissingContentType|Le destinataire a retourné une erreur indiquant que le type de contenu ne figurait pas sur la demande au spécifié. Pour plus d'informations, consultez l'exception interne.|  
|ProxyAuthenticationLevelMismatch|Les informations d’identification dans le cadre de l’authentification proxy HTTP exigent un niveau d’authentification (authentification mutuelle) plus rigoureux que le niveau d’authentification requis par l’authentification du serveur cible.|  
|ProxyImpersonationLevelMismatch|Les informations d'identification dans le cadre de l'authentification proxy HTTP définissent une restriction en matière de niveau d'emprunt d'identité plus rigoureuse que la restriction définie par l'authentification du serveur cible.|  
|SecureChannelFailure|Il n'est pas possible de générer un canal sécurisé pour SSL / TLS avec l'autorité spécifiée.|  
|TrustFailure|Impossible d'établir une relation d'approbation pour le canal sécurisé SSL / TLS avec l'autorité spécifiée.|  
|UseDefaultWebProxyCantBeUsedWithExplicitProxyAddress|Vous ne pouvez pas spécifier une adresse de proxy explicite et affecter la valeur true à la propriété UseDefaultWebProxy de votre élément HttpTransportBinding.|
