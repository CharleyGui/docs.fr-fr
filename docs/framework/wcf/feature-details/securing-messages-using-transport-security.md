---
title: Sécurisation des messages à l'aide de la sécurité de transport
ms.date: 03/30/2017
ms.assetid: 9029771a-097e-448a-a13a-55d2878330b8
ms.openlocfilehash: 7d160f6f0d1d29e34ca3365501b86d1a736de67b
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84589940"
---
# <a name="securing-messages-using-transport-security"></a>Sécurisation des messages à l'aide de la sécurité de transport
Cette section traite de la sécurité de transport Message Queuing (MSMQ) que vous pouvez utiliser pour sécuriser des messages envoyés vers une file d'attente.  
  
> [!NOTE]
> Avant de lire cette rubrique, il est recommandé de lire [concepts de sécurité](security-concepts.md).  
  
 L’illustration suivante fournit un modèle conceptuel de communication en file d’attente à l’aide de Windows Communication Foundation (WCF). Cette illustration et la terminologie sont utilisées pour expliquer les concepts de sécurité de transport.  
  
 ![Diagramme d'application mise en file d'attente](media/distributed-queue-figure.jpg "File d’attente distribuée-figure")  
  
 Lors de l’envoi de messages en file d’attente à l’aide de WCF avec <xref:System.ServiceModel.NetMsmqBinding> , le message WCF est joint en tant que corps du message MSMQ. La sécurité de transport sécurise le message MSMQ entier (en-têtes de message ou propriétés MSMQ et le corps du message). Étant donné qu’il s’agit du corps du message MSMQ, l’utilisation de la sécurité de transport sécurise également le message WCF.  
  
 Le concept clé de la sécurité de transport est que le client doit satisfaire certaines conditions de sécurité pour envoyer le message dans la file d'attente cible. Cela diffère de la sécurité de message, où le message est sécurisé pour l'application qui reçoit le message.  
  
 La sécurité de transport à l'aide de <xref:System.ServiceModel.NetMsmqBinding> et <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding> a un impact sur la manière dont les messages MSMQ sont sécurisés en transit entre la file d'attente de transmission et la file d'attente cible, où le terme « sécurisé » implique les éléments suivants :  
  
- Signature du message afin de s'assurer qu'il n'est pas falsifié.  
  
- Chiffrement du message afin de s'assurer qu'il ne peut pas être vu ou falsifié. Cela est recommandé mais facultatif.  
  
- Le gestionnaire de files d'attente cibles qui identifie l'expéditeur du message pour le non-rejet.  
  
 Dans MSMQ, quelle que soit l'authentification, la file d'attente cible possède une liste de contrôle d'accès (ACL, Access Control List) afin de vérifier si le client est autorisé à envoyer le message à la file d'attente cible. Il est également vérifié si l'application réceptrice est autorisée à recevoir le message depuis la file d'attente cible.  
  
## <a name="wcf-msmq-transport-security-properties"></a>Propriétés de la sécurité de transport MSMQ WCF  
 MSMQ utilise la sécurité Windows pour l'authentification. Il utilise l'identificateur de sécurité Windows (SID) pour identifier le client et utilise le service d'annuaire Active Directory comme autorité de certification lors de l'authentification du client. Cela requiert que MSMQ soit installé avec l'intégration Active Directory. Le SID de domaine Windows étant utilisé pour identifier le client, cette option de sécurité est explicite uniquement lorsque le client et le service font partie du même domaine Windows.  
  
 MSMQ permet également de joindre un certificat au message qui n'est pas inscrit auprès d'Active Directory. Dans ce cas, il s'assure que le message a été signé à l'aide du certificat joint.  
  
 WCF fournit ces deux options dans le cadre de la sécurité du transport MSMQ et il s’agit du pivot clé pour la sécurité du transport.  
  
 Par défaut, la sécurité de transport est activée.  
  
 Étant donné ces principes de base, les sections suivantes détaillent les propriétés de sécurité de transport fournies avec <xref:System.ServiceModel.NetMsmqBinding> et <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding>.  
  
#### <a name="msmq-authentication-mode"></a>Mode d'authentification MSMQ  
 Le <xref:System.ServiceModel.MsmqTransportSecurity.MsmqAuthenticationMode%2A> indique s'il faut utiliser la sécurité de domaine Windows ou une sécurité externe basée sur certificat pour sécuriser le message. Dans les deux modes d’authentification, le canal de transport de mise en file d’attente WCF utilise le `CertificateValidationMode` spécifié dans la configuration du service. Le mode de validation de certificat spécifie le mécanisme utilisé pour vérifier la validation du certificat.  
  
 Lorsque la sécurité de transport est activée, le paramètre par défaut est <xref:System.ServiceModel.MsmqAuthenticationMode.WindowsDomain>.  
  
#### <a name="windows-domain-authentication-mode"></a>Mode d'authentification de domaine Windows  
 L'utilisation de la sécurité Windows requiert l'intégration Active Directory. Le mode de sécurité du transport par défaut utilisé est <xref:System.ServiceModel.MsmqAuthenticationMode.WindowsDomain>. Lorsque cette valeur est définie, le canal WCF joint le SID Windows au message MSMQ et utilise son certificat interne obtenu à partir de Active Directory. MSMQ utilise ce certificat interne pour sécuriser le message. Le gestionnaire de files d'attente de réception utilise Active Directory pour rechercher un certificat correspondant afin d'authentifier le client et vérifie que le SID correspond également à celui du client. Cette étape d'authentification est exécutée si un certificat, généré en interne en mode d'authentification `WindowsDomain` ou généré de manière externe en mode d'authentification `Certificate`, est joint au message même si la file d'attente cible n'est pas marquée comme nécessitant l'authentification.  
  
> [!NOTE]
> Lorsque vous créez une file d'attente, vous pouvez marquer la file d'attente comme file d'attente authentifiée pour indiquer que la file d'attente nécessite l'authentification des clients envoyant des messages à la file d'attente. Cela garantit qu'aucun message non authentifié n'est accepté dans la file d'attente.  
  
 Le système vérifie également si le SID joint au message figure dans la liste ACL de la file d'attente cible afin de s'assurer que le client est autorisé à envoyer des messages à la file d'attente.  
  
#### <a name="certificate-authentication-mode"></a>Mode d'authentification de certificat  
 L'utilisation du mode d'authentification de certificat ne requiert pas l'intégration Active Directory. En fait, dans certains cas, par exemple lorsque MSMQ est installé en mode de groupe de travail (sans intégration Active Directory) ou lors de l'utilisation du protocole de transfert SRMP (SOAP Reliable Messaging Protocol) pour envoyer des messages à la file d'attente, seul <xref:System.ServiceModel.MsmqAuthenticationMode.Certificate> fonctionne.  
  
 Lors de l’envoi d’un message WCF avec <xref:System.ServiceModel.MsmqAuthenticationMode.Certificate> , le canal WCF n’attache pas de SID Windows au message MSMQ. La liste ACL de file d'attente cible doit autoriser l'accès utilisateur `Anonymous` pour l'envoi vers la file d'attente. Le gestionnaire de files d'attente de réception vérifie si le message MSMQ a été signé avec le certificat mais n'exécute pas d'authentification.  
  
 Le certificat avec ses informations de revendications et d’identité est rempli <xref:System.ServiceModel.ServiceSecurityContext> par le canal de transport en file d’attente WCF. Le service peut utiliser ces informations pour exécuter sa propre authentification de l'expéditeur.  
  
### <a name="msmq-protection-level"></a>Niveau de protection MSMQ  
 Le niveau de protection spécifie comment protéger le message MSMQ afin de s'assurer qu'il n'est pas falsifié. Il est spécifié dans la propriété <xref:System.ServiceModel.MsmqTransportSecurity.MsmqProtectionLevel%2A>. La valeur par défaut est <xref:System.Net.Security.ProtectionLevel.Sign>.  
  
#### <a name="sign-protection-level"></a>Niveau de protection « Signature »  
 Le message MSMQ est signé à l'aide du certificat généré en interne lors de l'utilisation du mode d'authentification `WindowsDomain` ou d'un certificat généré en externe lors de l'utilisation du mode d'authentification `Certificate`.  
  
#### <a name="sign-and-encrypt-protection-level"></a>Niveau de protection « Signature et chiffrement »  
 Le message MSMQ est signé à l'aide du certificat généré en interne lors de l'utilisation du mode d'authentification `WindowsDomain` ou d'un certificat généré en externe lors de l'utilisation du mode d'authentification `Certificate`.  
  
 Outre la signature du message, le message MSMQ est chiffré à l'aide de la clé publique du certificat obtenue à partir d'Active Directory qui appartient au gestionnaire de files d'attente de réception qui héberge la file d'attente cible. Le gestionnaire de files d'attente d'émission garantit que le message MSMQ est chiffré en transit. Le gestionnaire de files d'attente de réception déchiffre le message MSMQ à l'aide de la clé privée de son certificat interne et stocke le message dans la file d'attente (s'il est authentifié et autorisé) en texte clair.  
  
> [!NOTE]
> Pour chiffrer le message, l'accès Active Directory est requis (la propriété`UseActiveDirectory` de <xref:System.ServiceModel.NetMsmqBinding> doit avoir la valeur `true`) et peut être utilisé avec <xref:System.ServiceModel.MsmqAuthenticationMode.Certificate> et <xref:System.ServiceModel.MsmqAuthenticationMode.WindowsDomain>.  
  
#### <a name="none-protection-level"></a>Niveau de protection « Aucun »  
 Ce niveau est utilisé lorsque <xref:System.ServiceModel.MsmqTransportSecurity.MsmqProtectionLevel%2A> a la valeur <xref:System.Net.Security.ProtectionLevel.None>. Cela ne peut pas être une valeur valide pour d'autres modes d'authentification.  
  
> [!NOTE]
> Si le message MSMQ est signé, MSMQ vérifie si le message est signé avec le certificat joint (interne ou externe) quel que soit l'état de la file d'attente, autrement dit file d'attente authentifiée ou non.  
  
### <a name="msmq-encryption-algorithm"></a>Algorithme de chiffrement MSMQ  
 L'algorithme de chiffrement spécifie l'algorithme à utiliser pour chiffrer le message MSMQ sur le câble. Cette propriété est utilisée uniquement si <xref:System.ServiceModel.MsmqTransportSecurity.MsmqProtectionLevel%2A> a la valeur <xref:System.Net.Security.ProtectionLevel.EncryptAndSign>.  
  
 Les algorithmes pris en charge sont `RC4Stream` et `AES` et la valeur par défaut est `RC4Stream`.  
  
 Vous pouvez utiliser l'algorithme `AES` uniquement si MSMQ 4.0 est installé sur l'expéditeur. De plus, la file d'attente cible doit également être hébergée sur MSMQ 4.0.  
  
### <a name="msmq-hash-algorithm"></a>Algorithme de hachage MSMQ  
 L'algorithme de hachage spécifie l'algorithme utilisé pour créer une signature numérique du message MSMQ. Le gestionnaire de files d'attente de réception utilise ce même algorithme pour authentifier le message MSMQ. Cette propriété est utilisée uniquement si <xref:System.ServiceModel.MsmqTransportSecurity.MsmqProtectionLevel%2A> a la valeur <xref:System.Net.Security.ProtectionLevel.Sign> ou <xref:System.Net.Security.ProtectionLevel.EncryptAndSign>.  
  
 Les algorithmes pris en charge sont `MD5`, `SHA1`, `SHA256` et `SHA512`. Par défaut, il s’agit de `SHA1`.

 En raison de problèmes de collision avec MD5/SHA1, Microsoft recommande SHA256 ou une meilleure solution.
  
## <a name="see-also"></a>Voir aussi

- [Vue d'ensemble des files d'attente](queues-overview.md)
- [Concepts de sécurité](security-concepts.md)
- [Securing Services and Clients](securing-services-and-clients.md)
