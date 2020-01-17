---
title: Divulgation d'informations
ms.date: 03/30/2017
ms.assetid: 4064c89f-afa6-444a-aa7e-807ef072131c
ms.openlocfilehash: 0bcf1aa04d7ba7477a6c3f1559a77bbda1f974af
ms.sourcegitcommit: 09b4090b78f52fd09b0e430cd4b26576f1fdf96e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/17/2020
ms.locfileid: "76211957"
---
# <a name="information-disclosure"></a>Divulgation d'informations

La divulgation d'informations permet à un intrus d'obtenir des informations précieuses à propos d'un système. Par conséquent, examinez toujours les informations que vous révélez et demandez-vous si elles peuvent être utilisées par un utilisateur malveillant. Vous trouverez ci-dessous la liste des attaques par divulgation d’informations possibles et les moyens d’atténuation pour chacune d’elles.

## <a name="message-security-and-http"></a>Sécurité des messages et HTTP

Si vous utilisez la sécurité au niveau du message sur une couche transport HTTP, sachez que la sécurité au niveau du message ne protège pas les en-têtes HTTP. La seule manière de protéger les en-têtes HTTP est d'utiliser le transport HTTPS au lieu du HTTP. Le transport HTTPS entraîne le chiffrement du message entier, y compris les en-têtes HTTP, à l'aide du protocole SSL (Secure Sockets Layer).

## <a name="policy-information"></a>Informations de stratégie

Il est important de sécuriser la stratégie, surtout dans les scénarios de fédération dans lesquels les spécifications sensibles des jetons émis ou les informations de l'émetteur de jetons sont exposées dans la stratégie. Dans ces cas, il est recommandé de sécuriser le point de terminaison de stratégie du service fédéré pour empêcher les intrus d'obtenir des informations à propos du service, tel que le type de revendications à placer dans le jeton émis, ou de rediriger les clients vers des émetteurs de jetons malveillants. Par exemple, un intrus pourrait découvrir des paires de nom d'utilisateur/mot de passe en reconfigurant la chaîne de confiance fédérée afin qu'elle se termine dans un émetteur qui exécute une attaque de « l'homme du milieu » (« man-in-the-middle »). Il est également recommandé que les clients fédérés qui obtiennent leurs liaisons grâce à la récupération de la stratégie vérifient qu'ils approuvent les émetteurs de la chaîne de confiance fédérée obtenue. Pour plus d’informations sur les scénarios de Fédération, consultez [Federation](../../../../docs/framework/wcf/feature-details/federation.md).

## <a name="memory-dumps-can-reveal-claim-information"></a>Les images mémoire peuvent révéler des informations de revendication

Lorsqu'une application échoue, les fichiers journaux, tels que ceux produits par Dr. Watson, peuvent contenir les informations de revendication. Ces informations ne doivent pas être exportées à d'autres entités, telles que les équipes de support ; sinon, les informations de revendication qui contiennent des données privées sont également exportées. Vous pouvez atténuer cet aspect en n'envoyant pas les fichiers journaux à des entités inconnues.

## <a name="endpoint-addresses"></a>Adresses de point de terminaison

Une adresse de point de terminaison contient les informations nécessaires pour communiquer avec un point de terminaison. La sécurité SOAP doit inclure l'adresse complète dans les messages de négociation de la sécurité qui sont échangés afin de négocier une clé symétrique entre un client et un serveur. Vu que la négociation de sécurité est un processus d'amorçage, les en-têtes d'adresse ne peuvent pas être chiffrés pendant ce processus. Par conséquent, l'adresse ne doit pas contenir de données confidentielles ; sinon, il existe un risque d'attaque par divulgation d'informations.

## <a name="certificates-transferred-unencrypted"></a>Certificats transférés non chiffrés

Lorsque vous utilisez un certificat X.509 pour authentifier un client, le certificat est transféré en clair, à l'intérieur de l'en-tête SOAP. Sachez que cela peut constituer une divulgation d'informations d'identification personnelle (PII). Ce problème ne se pose pas pour le mode `TransportWithMessageCredential`, dans lequel le message entier est chiffré avec la sécurité au niveau du transport.

## <a name="service-references"></a>Références de service

Une référence de service est une référence à un autre service. Par exemple, un service peut passer une référence de service à un client au cours d'une opération. La référence de service est également utilisée avec un *vérificateur d’identité de confiance*, un composant interne qui garantit l’identité de l’entité de sécurité cible avant de divulguer des informations telles que les données d’application ou les informations d’identification à la cible. Si l'identité de la confiance distante ne peut pas être vérifiée ou est incorrecte, l'expéditeur doit s'assurer qu'aucune donnée n'a été divulguée qui pourrait le compromettre, compromettre l'application ou l'utilisateur.

Les mesures d'atténuation des risques sont les suivantes :

- Les références de service sont supposées dignes de confiance. Prenez soin, chaque fois que vous transférez des instances de références de service, de vérifier qu'elles n'ont pas fait l'objet d'une falsification.

- Certaines applications peuvent présenter une expérience utilisateur qui autorise l'établissement interactif de la confiance selon les données de la référence de service et les données de confiance prouvées par l'hôte distant. WCF fournit des points d’extensibilité pour une telle fonctionnalité, mais l’utilisateur doit les implémenter.

## <a name="ntlm"></a>NTLM

Par défaut, dans l'environnement de domaine Windows, l'authentification Windows utilise le protocole Kerberos pour authentifier et autoriser des utilisateurs. Si le protocole Kerberos ne peut pas être utilisé pour quelque raison que ce soit, l'authentification NTLM (NT LAN Manager) est utilisée en guise de secours. Vous pouvez désactiver ce comportement en attribuant à la propriété <xref:System.ServiceModel.Security.WindowsClientCredential.AllowNtlm%2A> la valeur `false`. Sachez que l'activation de NTLM entraîne les problèmes suivants :

- NTLM expose le nom d'utilisateur du client. Si le nom d'utilisateur doit rester confidentiel, affectez `AllowNTLM` à la propriété `false` sur la liaison.

- NTLM n'assure pas l'authentification du serveur. Par conséquent, le client ne peut pas vérifier qu'il communique avec le bon service lorsque vous utilisez le protocole d'authentification NTLM.

### <a name="specifying-client-credentials-or-invalid-identity-forces-ntlm-usage"></a>Spécification des informations d'identification du client ou utilisation forcée de NTLM sur une identité non valide

Lorsque vous créez un client, le fait de spécifier des informations d'identification du client sans un nom de domaine ou de spécifier une identité de serveur non valide provoque l'utilisation de NTLM au lieu du protocole Kerberos (si la propriété `AllowNtlm` a la valeur `true`). Vu que NTLM ne procède pas à l'authentification du serveur, les informations peuvent potentiellement être divulguées.

Par exemple, il est possible de spécifier les informations d’identification du client Windows sans un nom de domaine, comme illustré C# dans le code visuel suivant.

```csharp
MyChannelFactory.Credentials.Windows.ClientCredential = new System.Net.NetworkCredential("username", "password");
```

Le code ne spécifie pas de nom de domaine, et par conséquent, NTLM sera utilisé.

Si le domaine est spécifié, mais qu’un nom de principal du service non valide est spécifié à l’aide de la fonctionnalité d’identité du point de terminaison, alors NTLM est utilisé. Pour plus d’informations sur la spécification de l’identité du point de terminaison, consultez [identité du service et authentification](../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md).

## <a name="see-also"></a>Voir aussi

- [Considérations relatives à la sécurité](../../../../docs/framework/wcf/feature-details/security-considerations-in-wcf.md)
- [Élévation de privilèges](../../../../docs/framework/wcf/feature-details/elevation-of-privilege.md)
- [Déni de service](../../../../docs/framework/wcf/feature-details/denial-of-service.md)
- [Falsification](../../../../docs/framework/wcf/feature-details/tampering.md)
- [Scénarios non pris en charge](../../../../docs/framework/wcf/feature-details/unsupported-scenarios.md)
- [Attaques par relecture](../../../../docs/framework/wcf/feature-details/replay-attacks.md)
