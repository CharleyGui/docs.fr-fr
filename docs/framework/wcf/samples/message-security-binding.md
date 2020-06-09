---
title: Liaison de sécurité de message
ms.date: 03/30/2017
ms.assetid: a4570ce7-864e-461b-85d8-0f7bcc53c2c8
ms.openlocfilehash: 7c4b21a8983884cbb4f8ab77568bd4977563b3b1
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84584829"
---
# <a name="message-security-binding"></a>Liaison de sécurité de message
Cette section contient des exemples qui illustrent la liaison de sécurité des messages dans les services Windows dans WCF.  
  
## <a name="in-this-section"></a>Dans cette section  
 [Message Security Anonymous](message-security-anonymous.md)  
 Cet exemple montre comment implémenter une application Windows Communication Foundation (WCF) qui utilise la sécurité au niveau du message sans authentification du client, mais qui requiert l’authentification du serveur à l’aide du certificat X. 509 du serveur.  
  
 [Message Security Certificate](message-security-certificate.md)  
 Cet exemple montre comment implémenter une application qui utilise WS-Security avec l'authentification de certificat X.509 v3 pour le client et requiert l'authentification de serveur à l'aide du certificat X.509 v3 du serveur.  
  
 [Message Security User Name](message-security-user-name.md)  
 Cet exemple montre comment implémenter une application qui utilise WS-Security et l'authentification de nom d'utilisateur pour le client et qui nécessite l'authentification du serveur à l'aide de son certificat X.509v3.  
  
 [Message Security Windows](message-security-windows.md)  
 Cet exemple illustre comment configurer une liaison <xref:System.ServiceModel.WSHttpBinding> pour permettre l'utilisation de la sécurité de niveau message avec authentification Windows.
