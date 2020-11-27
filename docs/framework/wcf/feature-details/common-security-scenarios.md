---
title: Scénarios de sécurité courants
ms.date: 03/30/2017
helpviewer_keywords:
- security [WCF], scenarios
ms.assetid: 201923b5-5162-4a8a-8d4c-e7bd242748d5
ms.openlocfilehash: 21c8279890d1d1cf746e98f875efb6b1ff869c73
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96295078"
---
# <a name="common-security-scenarios"></a>Scénarios de sécurité courants

Les rubriques de cette section présentent un certain nombre de configurations de sécurité de service et client possibles. Les configurations varient selon un certain nombre de facteurs. Par exemple, si un service ou un client est sur un intranet, ou si la sécurité est fournie par Windows ou un transport (tel que HTTPS).  
  
## <a name="in-this-section"></a>Dans cette section  

 [Service et client Internet non sécurisés](internet-unsecured-client-and-service.md)  
 Exemple de client/service public non sécurisé.  
  
 [Service et client intranet non sécurisés](intranet-unsecured-client-and-service.md)  
 Service de base Windows Communication Foundation (WCF) développé pour fournir des informations sur un réseau privé sécurisé à une application WCF.  
  
 [Sécurité de transport avec l'authentification de base](transport-security-with-basic-authentication.md)  
 L'application autorise les clients à se connecter à l'aide de l'authentification personnalisée.  
  
 [Sécurité de transport avec l'authentification Windows](transport-security-with-windows-authentication.md)  
 Présente un client/service sécurisé par la sécurité Windows.  
  
 [Sécurité de transport avec un client anonyme](transport-security-with-an-anonymous-client.md)  
 Ce scénario utilise la sécurité de transport (tel que HTTPS) pour assurer la confidentialité et l'intégrité.  
  
 [Sécurité de transport avec l'authentification par certificat](transport-security-with-certificate-authentication.md)  
 Présente un client/service sécurisé par un certificat.  
  
 [Sécurité de message avec un client anonyme](message-security-with-an-anonymous-client.md)  
 Affiche un client et un service sécurisés par la sécurité des messages WCF.  
  
 [Sécurité de message avec un client de type Nom d'utilisateur](message-security-with-a-user-name-client.md)  
 Le client est une application Windows Forms qui autorise les clients à se connecter à l'aide d'un mot de passe et d'un nom d'utilisateur de domaine.  
  
 [Sécurité de message avec un client de certificat](message-security-with-a-certificate-client.md)  
 Les serveurs ont des certificats, et chaque client a un certificat. Un contexte de sécurité est établi via la négociation TLS (Transport Layer Security).  
  
 [Sécurité de message avec un client Windows](message-security-with-a-windows-client.md)  
 Variante du client de certificat. Les serveurs ont des certificats, et chaque client a un certificat. Un contexte de sécurité est établi via la négociation TLS.  
  
 [Sécurité de message avec un client Windows sans négociation d'informations d'identification](message-security-with-a-windows-client-without-credential-negotiation.md)  
 Présente un client/service sécurisé par un domaine Kerberos.  
  
 [Sécurité de message avec certificats mutuels](message-security-with-mutual-certificates.md)  
 Les serveurs ont des certificats, et chaque client a un certificat. Le certificat de serveur est distribué avec l'application et est disponible hors bande.  
  
 [Sécurité de message avec jetons émis](message-security-with-issued-tokens.md)  
 Sécurité fédérée qui permet d'établir la confiance entre des domaines indépendants.  
  
 [Sous-système approuvé](trusted-subsystem.md)  
 Un client accède à un ou plusieurs services Web distribués sur un réseau. Les services Web accèdent aux ressources supplémentaires (telles que les bases de données ou autres services Web) qui doivent être sécurisées.  
  
## <a name="reference"></a>Informations de référence  

 <xref:System.ServiceModel>  
  
## <a name="related-sections"></a>Sections connexes  

 [Autorisation](authorization-in-wcf.md)  
  
 [Présentation de la sécurité](security-overview.md)  
  
 [Sécurité](security.md)  
  
 [Liaisons et sécurité](bindings-and-security.md)  
  
 [Sécurisation des services et des clients](securing-services-and-clients.md)  
  
 [Authentification](authentication-in-wcf.md)  
  
 [Autorisation](authorization-in-wcf.md)  
  
 [Fédération et jetons émis](federation-and-issued-tokens.md)  
  
 [Audit](auditing-security-events.md)  
  
## <a name="see-also"></a>Voir aussi

- [Aide sur la sécurité et meilleures pratiques](security-guidance-and-best-practices.md)
- [Modèle de sécurité pour Windows Server AppFabric](/previous-versions/appfabric/ee677202(v=azure.10))
