---
title: Informations de confidentialité relatives à Windows Communication Foundation
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Communication Foundation, privacy information
- WCF, privacy information
- privacy information [WCF]
ms.assetid: c9553724-f3e7-45cb-9ea5-450a22d309d9
ms.openlocfilehash: b724ff1ce85442f64980fdc972188705992d5a4f
ms.sourcegitcommit: 011314e0c8eb4cf4a11d92078f58176c8c3efd2d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/09/2020
ms.locfileid: "77094980"
---
# <a name="windows-communication-foundation-privacy-information"></a>Informations de confidentialité relatives à Windows Communication Foundation
Microsoft s’engage à protéger la confidentialité de l’utilisateur final. Lorsque vous générez une application à l’aide de Windows Communication Foundation (WCF), version 3,0, votre application peut avoir un impact sur la confidentialité de vos utilisateurs finaux. Par exemple, votre application peut recueillir des informations de contact utilisateur de manière explicite ou elle peut demander ou envoyer des informations sur Internet à votre site Web. Si vous incorporez la technologie Microsoft dans votre application, cette technologie peut avoir son propre comportement qui peut affecter la confidentialité. WCF n’envoie pas d’informations à Microsoft à partir de votre application, à moins que vous ou l’utilisateur final ne choisissiez de nous l’envoyer.  
  
## <a name="wcf-in-brief"></a>WCF en bref  
 WCF est une infrastructure de messagerie distribuée utilisant l’infrastructure de Microsoft .NET qui permet aux développeurs de créer des applications distribuées. Les messages transmis entre deux applications contiennent des informations d'en-tête et de corps.  
  
 Les en-têtes peuvent contenir le routage des messages, des informations de sécurité, des transactions et d’autres éléments, en fonction des services utilisés par l’application. Les messages sont en général chiffrés par défaut. L'unique exception concerne l'utilisation du `BasicHttpBinding`, qui a été conçu pour une utilisation avec des services Web hérités non sécurisés. En tant que concepteur d'applications, vous êtes responsable de la conception finale. Les messages dans le corps SOAP contiennent des données spécifiques à l’application ; Toutefois, ces données, telles que les informations personnelles définies par l’application, peuvent être sécurisées à l’aide des fonctionnalités de chiffrement ou de confidentialité WCF. Les sections suivantes décrivent les fonctionnalités qui peuvent avoir un impact sur la confidentialité.  
  
## <a name="messaging"></a>Messagerie  
 Chaque message WCF possède un en-tête d’adresse qui spécifie la destination du message et l’emplacement où la réponse doit s’afficher.  
  
 Le composant adresse d'une adresse de point de terminaison est un URI (Uniform Resource Identifier) qui identifie le point de terminaison. L'adresse peut être une adresse réseau ou une adresse logique. L'adresse peut inclure le nom de l'ordinateur (nom d'hôte, nom de domaine complet) et une adresse IP. L’adresse de point de terminaison peut également contenir un identificateur global unique (GUID) ou une collection de GUID pour l’adressage temporaire utilisé pour distinguer chaque adresse. Chaque message contient un ID de message qui est un GUID. Cette fonctionnalité respecte la norme de référence WS-Addressing.  
  
 La couche de messagerie WCF n’écrit aucune information personnelle sur l’ordinateur local. Toutefois, elle peut propager des informations personnelles au niveau du réseau si un développeur de service a créé un service qui expose de telles informations (par exemple, en utilisant le nom d'une personne dans un nom de point de terminaison, ou en incluant des informations personnelles dans le Web Services Description Language du point de terminaison sans exiger que les clients utilisent https pour accéder au WSDL). En outre, si un développeur exécute l’outil [ServiceModel Metadata Utility Tool (Svcutil. exe)](servicemodel-metadata-utility-tool-svcutil-exe.md) sur un point de terminaison qui expose des informations personnelles, la sortie de l’outil peut contenir ces informations et le fichier de sortie est écrit sur le disque dur local.  
  
## <a name="hosting"></a>Hébergement  
 La fonctionnalité d’hébergement de WCF permet aux applications de démarrer à la demande ou d’activer le partage de port entre plusieurs applications. Une application WCF peut être hébergée dans Internet Information Services (IIS), similaire à ASP.NET.  
  
 L'hébergement n'expose aucune information spécifique sur le réseau et ne conserve aucune donnée sur l'ordinateur.  
  
## <a name="message-security"></a>Sécurité des messages  
 La sécurité WCF offre des fonctionnalités de sécurité pour les applications de messagerie. Les fonctions de sécurité fournies incluent l'authentification et l'autorisation.  
  
 L'authentification est exécutée en passant des informations d'identification entre les clients et services. L'authentification peut s'effectuer par le biais de la sécurité de niveau transport ou par le biais de la sécurité de niveau message SOAP, comme suit :  
  
- Avec la sécurité des messages SOAP, l'authentification est exécutée par le biais des informations d'identification telles que nom d'utilisateur/mots de passe, certificats X.509, tickets Kerberos et jetons SAML, qui peuvent tous contenir des informations personnelles selon l'émetteur.  
  
- Avec la sécurité de transport, l’authentification est effectuée par le biais des mécanismes d’authentification de transport traditionnels tels que les modèles d’authentification HTTP (De base, Digest, Négocier, Autorisation Windows Intégrée, NTLM, Aucun et Anonyme) et l’authentification par formulaire.  
  
 L'authentification peut entraîner l'établissement d'une session sécurisée entre les points de terminaison communicants. La session est identifiée par un GUID valide pendant toute la durée de vie de la session de sécurité. Le tableau suivant indique ce qui est conservé, et à quel emplacement.  
  
|Données|Stockage|  
|----------|-------------|  
|Informations d'identification de présentation, telles que nom d'utilisateur, certificats X.509, jetons Kerberos et références aux informations d'identification.|Mécanismes de gestion des informations d'identification Windows standard tels que le magasin de certificats Windows.|  
|Informations d'appartenance utilisateur, telles que noms d'utilisateur et mots de passe.|Fournisseurs d’appartenances ASP.NET.|  
|Informations d'identité à propos du service utilisé pour authentifier le service aux clients.|Adresse de point de terminaison du service.|  
|Informations sur l'appelant.|Journaux d'audit.|  
  
## <a name="auditing"></a>Audit  
 L'audit permet d'enregistrer le succès et l'échec des événements d'authentification et d'autorisation. Les enregistrements d'audit contiennent les données suivantes : URI de service, URI d'action et identification de l'appelant.  
  
 L'audit note également lorsque l'administrateur modifie la configuration d'enregistrement des messages (activation ou désactivation), car l'enregistrement des messages peut enregistrer des données spécifiques à l'application dans les en-têtes et les corps. Pour Windows XP, un enregistrement est enregistré dans le journal des événements de l’application. Pour Windows Vista et Windows Server 2003, un enregistrement est enregistré dans le journal des événements de sécurité.  
  
## <a name="transactions"></a>Transactions  
 La fonctionnalité transactions fournit des services transactionnels à une application WCF.  
  
 Les en-têtes de transaction utilisés dans la propagation de transaction peuvent contenir des ID de transaction ou des ID d'inscription, qui sont des GUID.  
  
 La fonctionnalité Transactions utilise le gestionnaire de transactions Microsoft Distributed Transaction Coordinator (MSDTC) (un composant Windows) pour gérer l’état des transactions. Par défaut, les communications entre les gestionnaires de transactions sont chiffrées. Les gestionnaires de transactions peuvent enregistrer des références à des points de terminaison, des ID de transaction et des ID d'inscription dans le cadre de leur état durable. La durée de vie de cet état est déterminée par la durée de vie du fichier journal du gestionnaire de transactions. Le service MSDTC détient la propriété et assure la maintenance de ce journal.  
  
 La fonctionnalité Transactions implémente les normes WS-Coordination et WS-Atomic Transaction.  
  
## <a name="reliable-sessions"></a>Sessions fiables  
 Les sessions fiables dans WCF permettent de transférer des messages en cas de défaillances de transport ou d’intermédiaires. Elles fournissent un transfert de message « exactly-once » même lorsque le transport sous-jacent se déconnecte (par exemple, une connexion TCP sur un réseau sans fil) ou perd un message (un proxy HTTP qui rejette un message sortant ou entrant). Les sessions fiables récupèrent également la réorganisation des messages (comme il peut arriver dans le cas du routage multivoie), en conservant l'ordre dans lequel les messages ont été envoyés.  
  
 Les sessions fiables sont implémentées à l'aide du protocole WS-RM (WS-ReliableMessaging). Elles ajoutent des en-têtes WS-RM qui contiennent des informations de session, utilisées pour identifier tous les messages associés à une session fiable particulière. Chaque session WS-RM a un identificateur, qui est un GUID.  
  
 Aucune information personnelle n’est conservée sur l’ordinateur de l’utilisateur final.  
  
## <a name="queued-channels"></a>Canaux mis en file d'attente  
 Les files d'attente stockent des messages d'une application émettrice pour le compte d'une application réceptrice et envoient ultérieurement ces messages à l'application réceptrice. Elles aident à garantir le transfert des messages des applications émettrices aux applications réceptrices lorsque, par exemple, l'application réceptrice est transitoire. WCF prend en charge la mise en file d’attente à l’aide de Microsoft Message Queuing (MSMQ) en tant que transport.  
  
 La fonctionnalité de canaux en file d'attente n'ajoute pas d'en-tête à un message. Au lieu de cela, elle crée un message Message Queuing avec les propriétés de message Message Queuing appropriées définies et elle appelle des méthodes Message Queuing pour mettre le message dans la file d'attente Message Queuing. Message Queuing est un composant facultatif fourni avec Windows.  
  
 Aucune information n’est conservée sur l’ordinateur de l’utilisateur final par la fonctionnalité de canaux en file d’attente, car elle utilise Message Queuing comme infrastructure de mise en file d’attente.  
  
## <a name="com-integration"></a>Intégration COM+  
 Cette fonctionnalité encapsule les fonctionnalités COM et COM+ existantes pour créer des services compatibles avec les services WCF. Cette fonctionnalité n’utilise pas d’en-têtes spécifiques et ne conserve pas les données sur l’ordinateur de l’utilisateur final.  
  
## <a name="com-service-moniker"></a>Moniker de service COM  
 Cela fournit un wrapper non managé à un client WCF standard. Cette fonctionnalité n’a pas d’en-têtes spécifiques sur le câble et ne conserve pas de données sur l’ordinateur.  
  
## <a name="peer-channel"></a>Canal homologue  
 Un canal homologue permet le développement d’applications à parties égales à l’aide de WCF. La messagerie pluripartite se produit dans le contexte d'une maille. Les mailles sont identifiées par un nom que les nœuds peuvent joindre. Chaque nœud du canal homologue crée un écouteur TCP à un port spécifié par l'utilisateur et établit des connexions avec d'autres nœuds dans la maille afin de garantir la résilience. Pour se connecter à d'autres nœuds de la maille, les nœuds échangent également certaines données, y compris l'adresse d'écouteur et les adresses IP de l'ordinateur, avec d'autres nœuds de la maille. Les messages envoyés dans la maille peuvent contenir des informations de sécurité relatives à l'expéditeur afin d'empêcher l'usurpation et la falsification de message.  
  
 Aucune information personnelle n’est stockée sur l’ordinateur de l’utilisateur final.  
  
## <a name="it-professional-experience"></a>Expérience professionnelle en informatique  
  
### <a name="tracing"></a>Traçage  
 La fonctionnalité de diagnostic de l’infrastructure WCF journalise les messages qui passent par les couches de modèle de transport et de service, ainsi que les activités et événements associés à ces messages. Cette fonctionnalité est désactivée par défaut. Il est activé à l’aide du fichier de configuration de l’application et le comportement de suivi peut être modifié à l’aide du fournisseur WMI WCF au moment de l’exécution. Lorsque cette fonctionnalité est activée, l'infrastructure de suivi émet un suivi de diagnostic qui contient des messages, des activités et des événements de traitement aux écouteurs configurés. Le format et l'emplacement de la sortie sont déterminés par les choix de configuration d'écouteur de l'administrateur, mais il s'agit en général d'un fichier au format XML. L'administrateur est chargé de définir la liste de contrôle d'accès (ACL) sur les fichiers de suivi. En particulier, en cas d'hébergement par le système WAS (Windows Activation System), l'administrateur doit s'assurer que les fichiers ne sont pas servis depuis le répertoire racine virtuel public si cela n'est pas souhaité.  
  
 Il existe deux types de suivi : l'enregistrement des messages et le suivi du diagnostic de modèle de service, décrits dans la section suivante. Chaque type est configuré par le biais de sa propre source de suivi : <xref:System.ServiceModel.Configuration.DiagnosticSection.MessageLogging%2A> et <xref:System.ServiceModel>. Ces deux sources de suivi d'enregistrement capturent des données qui sont locales à l'application.  
  
### <a name="message-logging"></a>Journalisation des messages  
 La source de suivi d'enregistrement des messages (<xref:System.ServiceModel.Configuration.DiagnosticSection.MessageLogging%2A>) permet à un administrateur d'enregistrer les messages qui sont transmis sur le système. Par le biais de la configuration, l'utilisateur peut décider d'enregistrer uniquement des messages entiers ou des en-têtes de message, s'il faut enregistrer les couches de modèle de transport et/ou de service et s'il faut inclure les messages malformés. En outre, l'utilisateur peut configurer le filtrage de façon à limiter les messages enregistrés.  
  
 Par défaut, l'enregistrement des messages est désactivé. L'administrateur de l'ordinateur local peut empêcher l'administrateur au niveau de l'application d'activer l'enregistrement des messages.  
  
#### <a name="encrypted-and-decrypted-message-logging"></a>Enregistrement des messages chiffrés et déchiffrés  
 Les messages sont enregistrés, chiffrés ou déchiffrés, comme décrit dans les termes suivants.  
  
 Enregistrement de transport  
 Enregistre les messages reçus et envoyés au niveau du transport. Ces messages contiennent tous les en-têtes et peuvent être chiffrés avant d'être envoyés sur le câble et lors de la réception.  
  
 Si les messages sont chiffrés avant d'être envoyés sur le câble et lors de leur réception, ils sont enregistrés chiffrés également. Une exception est lorsqu'un protocole de sécurité est utilisé (https) : ils sont alors enregistrés déchiffrés avant d'être envoyés et après avoir été reçus même s'ils sont chiffrés sur le câble.  
  
 Enregistrement de service  
 Enregistre les messages reçus ou envoyés au niveau du modèle de service, après que le traitement d'en-tête de canal a eu lieu, juste avant et après l'entrée du code utilisateur.  
  
 Les messages enregistrés à ce niveau sont déchiffrés même s'ils ont été sécurisés et chiffrés sur le câble.  
  
 Enregistrement des messages malformés  
 Journalise les messages que l’infrastructure WCF ne peut pas comprendre ni traiter.  
  
 Les messages sont enregistrés tels quels, autrement dit chiffrés ou non  
  
 Lorsque les messages sont consignés sous une forme déchiffrée ou non chiffrée, WCF supprime par défaut les clés de sécurité et les informations potentiellement personnelles des messages avant de les enregistrer. Les sections suivantes décrivent quelles informations sont supprimées, et quand. L'administrateur de l'ordinateur et le responsable du déploiement d'applications doivent prendre certaines mesures de configuration pour modifier le comportement par défaut afin d'enregistrer les clés et les informations potentiellement personnelles.  
  
#### <a name="information-removed-from-message-headers-when-logging-decryptedunencrypted-messages"></a>Informations supprimées des en-têtes de messages lors de l'enregistrement des messages déchiffrés/non chiffrés  
 Lorsque les messages sont enregistrés sous forme déchiffrés/non chiffrés, les clés de sécurité et les informations potentiellement personnelles sont supprimées par défaut des en-têtes de messages et des corps de message avant d'être enregistrées. La liste suivante indique ce que WCF considère comme des clés et des informations potentiellement personnelles.  
  
 Clés qui sont supprimées :  
  
 \- pour xmlns : WST = "http://schemas.xmlsoap.org/ws/2004/04/trust" et xmlns : WST = "http://schemas.xmlsoap.org/ws/2005/02/trust"  
  
 wst:BinarySecret  
  
 wst:Entropy  
  
 \- pour xmlns : wsse = "http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.1.xsd" et xmlns : wsse = "http://docs.oasis-open.org/wss/2005/xx/oasis-2005xx-wss-wssecurity-secext-1.1.xsd"  
  
 wsse:Password  
  
 wsse:Nonce  
  
 Informations potentiellement personnelles qui sont supprimées :  
  
 \- pour xmlns : wsse = "http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.1.xsd" et xmlns : wsse = "http://docs.oasis-open.org/wss/2005/xx/oasis-2005xx-wss-wssecurity-secext-1.1.xsd"  
  
 wsse:Username  
  
 wsse:BinarySecurityToken  
  
 \- pour xmlns : SAML = "urn : Oasis : Names : TC : SAML : 1.0 : assertion" les éléments en gras (ci-dessous) sont supprimés :  
  
 Assertion de \<  
  
 MajorVersion="1"  
  
 MinorVersion="1"  
  
 AssertionId="[ID]"  
  
 Issuer="[chaîne]"  
  
 IssueInstant="[horodatage]"  
  
 >  
  
 \<conditions NotBefore = "[dateTime]" NotOnOrAfter = "[dateTime]" >  
  
 \<AudienceRestrictionCondition >  
  
 \<audience > [URI]\</audience > +  
  
 \</AudienceRestrictionCondition > *  
  
 \<DoNotCacheCondition/> *  
  
 <\!--type de base abstrait  
  
 \<condition/> *  
  
 -->  
  
 \<>/conditions ?  
  
 > de Conseil \<  
  
 \<AssertionIDReference > [ID]\</AssertionIDReference > *  
  
 \<assertion > [assertion]\</assertion > *  
  
 [indifférent]*  
  
 \<>/Advice ?  
  
 <\!--types de base abstraits  
  
 Instruction \</> *  
  
 \<SubjectStatement >  
  
 \<objet >  
  
 `<NameIdentifier`  
  
 `NameQualifier="[string]"?`  
  
 `Format="[uri]"?`  
  
 `>`  
  
 `[string]`  
  
 `</NameIdentifier>?`  
  
 \<SubjectConfirmation >  
  
 \<ConfirmationMethod > [anyURI]\</ConfirmationMethod > +  
  
 \<SubjectConfirmationData > [Any]\</SubjectConfirmationData >?  
  
 \<DS : KeyInfo >...\</DS : KeyInfo >?  
  
 \<>/SubjectConfirmation ?  
  
 \</Subject >  
  
 \</SubjectStatement > *  
  
 -->  
  
 \<AuthenticationStatement  
  
 AuthenticationMethod="[uri]"  
  
 AuthenticationInstant="[horodatage]"  
  
 >  
  
 [Objet]  
  
 `<SubjectLocality`  
  
 `IPAddress="[string]"?`  
  
 `DNSAddress="[string]"?`  
  
 `/>?`  
  
 < AuthorityBinding  
  
 AuthorityKind="[NomQ]"  
  
 Location="[uri]"  
  
 Binding="[uri]"  
  
 />*  
  
 \</AuthenticationStatement > *  
  
 \<AttributeStatement >  
  
 [Objet]  
  
 Attribut \<  
  
 AttributeName="[chaîne]"  
  
 AttributeNamespace="[uri]"  
  
 >  
  
 `<AttributeValue>[any]</AttributeValue>+`  
  
 \</attribute > +  
  
 \</AttributeStatement > *  
  
 \<AuthorizationDecisionStatement  
  
 Resource="[uri]"  
  
 Decision="[Permit&#124;Deny&#124;Indeterminate]"  
  
 >  
  
 [Objet]  
  
 \<action Namespace = "[URI]" > [String]\</action > +  
  
 > de preuve \<  
  
 \<AssertionIDReference > [ID]\</AssertionIDReference > +  
  
 \<assertion > [assertion]\</assertion > +  
  
 \<>/Evidence ?  
  
 \</AuthorizationDecisionStatement > *  
  
 \</assertion >  
  
#### <a name="information-removed-from-message-bodies-when-logging-decryptedunencrypted-messages"></a>Informations supprimées des corps de messages lors de l'enregistrement des messages déchiffrés/non chiffrés  
 Comme décrit précédemment, WCF supprime les clés et les informations potentiellement personnelles connues des en-têtes de message pour les messages déchiffrés/non chiffrés. En outre, WCF supprime les clés et les informations potentiellement personnelles connues des corps de message pour les éléments et actions du corps de la liste suivante, qui décrivent les messages de sécurité impliqués dans l’échange de clés.  
  
 Pour les espaces de noms suivants :  
  
 xmlns : WST = "http://schemas.xmlsoap.org/ws/2004/04/trust" et xmlns : WST = "http://schemas.xmlsoap.org/ws/2005/02/trust" (par exemple, si aucune action n’est disponible)  
  
 Les informations sont supprimées pour ces éléments de corps, qui impliquent l'échange de clé :  
  
 wst:RequestSecurityToken  
  
 wst:RequestSecurityTokenResponse  
  
 wst:RequestSecurityTokenResponseCollection  
  
 Les informations sont également supprimées pour chacune des actions suivantes :  
  
- `http://schemas.xmlsoap.org/ws/2005/02/trust/RST/Issue`
  
- `http://schemas.xmlsoap.org/ws/2005/02/trust/RSTR/Issue`
  
- `http://schemas.xmlsoap.org/ws/2005/02/trust/RST/Renew`
  
- `http://schemas.xmlsoap.org/ws/2005/02/trust/RSTR/Renew`
  
- `http://schemas.xmlsoap.org/ws/2005/02/trust/RST/Cancel`
  
- `http://schemas.xmlsoap.org/ws/2005/02/trust/RSTR/Cancel`
  
- `http://schemas.xmlsoap.org/ws/2005/02/trust/RST/Validate`
  
- `http://schemas.xmlsoap.org/ws/2005/02/trust/RSTR/Validate`
  
- `http://schemas.xmlsoap.org/ws/2005/02/trust/RST/SCT`
  
- `http://schemas.xmlsoap.org/ws/2005/02/trust/RSTR/SCT`
  
- `http://schemas.xmlsoap.org/ws/2005/02/trust/RST/SCT/Amend`
  
- `http://schemas.xmlsoap.org/ws/2005/02/trust/RSTR/SCT/Amend`
  
- `http://schemas.xmlsoap.org/ws/2005/02/trust/RST/SCT/Renew`
  
- `http://schemas.xmlsoap.org/ws/2005/02/trust/RSTR/SCT/Renew`
  
- `http://schemas.xmlsoap.org/ws/2005/02/trust/RST/SCT/Cancel`
  
- `http://schemas.xmlsoap.org/ws/2005/02/trust/RSTR/SCT/Cancel`
  
- `http://schemas.xmlsoap.org/ws/2004/04/security/trust/RST/SCT`
  
- `http://schemas.xmlsoap.org/ws/2004/04/security/trust/RSTR/SCT`
  
- `http://schemas.xmlsoap.org/ws/2004/04/security/trust/RST/SCT-Amend`
  
- `http://schemas.xmlsoap.org/ws/2004/04/security/trust/RSTR/SCT-Amend`
  
#### <a name="no-information-is-removed-from-application-specific-headers-and-body-data"></a>Aucune information n'est supprimé des données de corps et en-têtes spécifiques aux applications  
 WCF n’effectue pas le suivi des informations personnelles dans les en-têtes spécifiques à l’application (par exemple, les chaînes de requête) ou les données de corps (par exemple, le numéro de carte de crédit).  
  
 Lorsque l'enregistrement des messages est activé, les informations personnelles contenues dans des en-têtes spécifiques aux application et les informations de corps peuvent être visibles dans les journaux. Là encore, le responsable du déploiement d'applications est chargé de définir les listes ACL sur les fichiers de configuration et les fichiers journaux. Ils peuvent également désactiver la journalisation s’ils ne souhaitent pas que ces informations soient visibles, ou filtrer ces informations à partir des fichiers journaux après leur enregistrement.  
  
### <a name="service-model-tracing"></a>Suivi du modèle de service  
 La source de suivi de modèle de service (<xref:System.ServiceModel>) autorise le suivi des activités et événements liés au traitement des messages. Cette fonctionnalité utilise la fonctionnalité de diagnostic du .NET Framework de <xref:System.Diagnostics>. Comme avec la propriété <xref:System.ServiceModel.Configuration.DiagnosticSection.MessageLogging%2A>, l'emplacement et sa liste ACL sont configurables par l'utilisateur à l'aide de fichiers de configuration d'application .NET Framework. Comme avec l'enregistrement des messages, l'emplacement des fichiers est toujours configuré lorsque l'administrateur active le suivi ; par conséquent, l'administrateur contrôle la liste ACL.  
  
 Les suivis contiennent des en-têtes de messages lorsqu'un message est dans la portée. On applique les mêmes règles de masquage des informations potentiellement personnelles dans les en-têtes de messages que celles décrites dans la section précédente : les informations personnelles précédemment identifiées sont supprimées par défaut des en-têtes dans les suivis. L'administrateur d'ordinateur et le responsable du déploiement d'applications doivent modifier la configuration afin d'enregistrer les informations potentiellement personnelles. Toutefois, les informations personnelles contenues dans les en-têtes spécifiques aux applications sont enregistrées dans les suivis. Le responsable du déploiement d'applications est chargé de définir les listes ACL sur les fichiers de configuration et les fichiers de suivi. Ils peuvent également désactiver le suivi pour masquer ces informations ou filtrer ces informations à partir des fichiers de trace après leur enregistrement.  
  
 Dans le cadre du suivi ServiceModel, des ID uniques (nommés ID d'activité, et correspondant en général à un GUID) relient différentes activités à mesure qu'un message parcoure différentes parties de l'infrastructure.  
  
#### <a name="custom-trace-listeners"></a>Écouteurs de suivi personnalisés  
 Pour l'enregistrement des messages et le suivi, un écouteur de suivi personnalisé peut être configuré de façon à envoyer des suivis et des messages sur le câble (par exemple à une base de données distante). Le responsable du déploiement d'applications est chargé de configurer les écouteurs personnalisés ou de déléguer cette opération aux utilisateurs. Ils sont également responsables des informations personnelles exposées à l’emplacement distant et pour l’application correcte des listes de contrôle d’accès à cet emplacement.  
  
### <a name="other-features-for-it-professionals"></a>Autres fonctionnalités pour les professionnels de l'informatique  
 WCF dispose d’un fournisseur WMI qui expose les informations de configuration de l’infrastructure WCF par le biais de WMI (fourni avec Windows). Par défaut, l'interface WMI est accessible aux administrateurs.  
  
 La configuration WCF utilise le mécanisme de configuration .NET Framework. Les fichiers de configuration sont stockés sur l'ordinateur. Le développeur d’applications et l’administrateur créent les fichiers de configuration et la liste ACL pour chacune des exigences de l’application. Un fichier de configuration peut contenir des adresses de point de terminaison et des liens vers des certificats dans le magasin de certificats. Les certificats peuvent être utilisés pour fournir des données d’application afin de configurer différentes propriétés des fonctionnalités utilisées par l’application.  
  
 WCF utilise également la fonctionnalité de vidage de processus .NET Framework en appelant la méthode <xref:System.Environment.FailFast%2A>.  
  
### <a name="it-pro-tools"></a>Outils pour professionnels de l'informatique  
 WCF fournit également les outils professionnels de l’informatique suivants, qui sont fournis dans le SDK Windows.  
  
#### <a name="svctraceviewerexe"></a>SvcTraceViewer.exe  
 La visionneuse affiche les fichiers de trace WCF. La visionneuse affiche toutes les informations contenues dans les suivis.  
  
#### <a name="svcconfigeditorexe"></a>SvcConfigEditor.exe  
 L’éditeur permet à l’utilisateur de créer et de modifier des fichiers de configuration WCF. L'éditeur affiche toutes les informations contenues dans les fichiers de configuration. La même tâche peut être accomplie avec un éditeur de texte.  
  
#### <a name="servicemodel_reg"></a>ServiceModel_Reg  
 Cet outil permet à l'utilisateur de gérer les installations de ServiceModel sur un ordinateur. L’outil affiche les messages d’État dans une fenêtre de console lorsqu’il s’exécute et, dans le processus, peut afficher des informations sur la configuration de l’installation WCF.  
  
#### <a name="wsatconfigexe-and-wsatuidll"></a>WSATConfig.exe et WSATUI.dll  
 Ces outils permettent aux professionnels de l’informatique de configurer la prise en charge du réseau WS-AtomicTransaction interopérable dans WCF. Les outils affichent et permettent aux utilisateurs de modifier les valeurs des paramètres WS-AtomicTransaction le plus couramment utilisés stockés dans le Registre.  
  
## <a name="cross-cutting-features"></a>Fonctionnalités composites  
 Les fonctionnalités suivantes sont composites. En d’autres termes, elles peuvent être composées de n’importe lesquelles des fonctionnalités précédentes.  
  
### <a name="service-framework"></a>Infrastructure de service  
 Les en-têtes peuvent contenir un ID d'instance, qui est un GUID qui associe un message à une instance d'une classe CLR.  
  
 Le langage WDSL (Web Services Description Language) contient une définition du port. Chaque port a une adresse de point de terminaison et une liaison qui représente les services utilisés par l'application. L'exposition du langage WSDL peut être désactivée à l'aide de la configuration. Aucune information n'est conservée sur l'ordinateur.  
  
## <a name="see-also"></a>Voir aussi

- [Windows Communication Foundation](index.md)
- [Sécurité](./feature-details/security.md)
