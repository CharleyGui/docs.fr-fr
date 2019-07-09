---
title: Résolution des problèmes de messagerie en file d'attente
ms.date: 03/30/2017
ms.assetid: a5f2836f-018d-42f5-a571-1e97e64ea5b0
ms.openlocfilehash: 3b149d1b422848e1acdd954ebda4191496ddcc7e
ms.sourcegitcommit: d6e27023aeaffc4b5a3cb4b88685018d6284ada4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/09/2019
ms.locfileid: "67662940"
---
# <a name="troubleshooting-queued-messaging"></a>Résolution des problèmes de messagerie en file d'attente

Cette section contient des questions et résolution des problèmes d’aide pour l’utilisation de files d’attente dans Windows Communication Foundation (WCF).

## <a name="common-questions"></a>Questions courantes

**Q :** J’ai utilisé la version bêta 1 de WCF et j’ai installé le correctif logiciel MSMQ. Est-ce que je dois supprimer le correctif logiciel ?

**R :** Oui. Ce correctif logiciel n'est plus pris en charge. WCF fonctionne maintenant sur MSMQ sans requérir de correctif logiciel.

**Q :** Il existe deux liaisons pour MSMQ : <xref:System.ServiceModel.NetMsmqBinding> et <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding>. Laquelle dois-je utiliser et à quel moment ?

**R :** Utiliser le <xref:System.ServiceModel.NetMsmqBinding> lorsque vous souhaitez utiliser MSMQ comme transport pour la communication en file d’attente entre deux applications WCF. Utiliser le <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding> lorsque vous souhaitez utiliser des applications MSMQ existantes pour communiquer avec les nouvelles applications WCF.

**Q :** Je dois mettre à niveau MSMQ pour utiliser le <xref:System.ServiceModel.NetMsmqBinding> et `MsmqIntegration` liaisons ?

**R :** Non. Les deux liaisons fonctionnent avec MSMQ 3.0 sur [!INCLUDE[wxp](../../../../includes/wxp-md.md)] et [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)]. Certaines fonctionnalités des liaisons deviennent disponibles lorsque vous effectuez la mise à niveau vers MSMQ 4.0 dans [!INCLUDE[wv](../../../../includes/wv-md.md)].

**Q :** Les fonctionnalités de la <xref:System.ServiceModel.NetMsmqBinding> et <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding> liaisons sont disponibles dans MSMQ 4.0 mais pas dans MSMQ 3.0 ?

**R :** Les fonctionnalités suivantes sont disponibles dans MSMQ 4.0 mais pas dans MSMQ 3.0 :

- La file d'attente de lettres mortes personnalisée est uniquement prise en charge sur MSMQ 4.0.

- MSMQ 3.0 et 4.0 gèrent les messages incohérents différemment.

- Seul MSMQ 4.0 prend en charge la lecture transactionnelle à distance.

Pour plus d’informations, consultez [différences de fonctionnalités Queuing dans Windows Vista, Windows Server 2003 et Windows XP](../../../../docs/framework/wcf/feature-details/diff-in-queue-in-vista-server-2003-windows-xp.md).

**Q :** Puis-je utiliser MSMQ 3.0 sur le côté « un » de la communication en file d’attente et MSMQ 4.0 à l’autre extrémité ?

**R :** Oui.

**Q :** Je souhaite intégrer des applications MSMQ existantes avec nouveaux clients WCF ou les serveurs. Est-ce que je dois mettre à niveau les deux côtés de mon infrastructure MSMQ ?

**R :** Non. Vous n'êtes pas obligé d'effectuer la mise à niveau vers MSMQ 4.0 sur l'un ou l'autre des côtés.

## <a name="troubleshooting"></a>Résolution des problèmes

Cette section contient les solutions aux problèmes les plus courants. Certains problèmes correspondant à des restrictions connues sont également décrits dans les notes de publication.

**Q :** J’essaie d’utiliser une file d’attente privée et j’obtiens l’exception suivante : `System.InvalidOperationException`: L'URL n'est pas valide. L'URL de la file d'attente ne peut pas contenir le caractère « $ ». Utilisez la syntaxe dans net.msmq://machine/private/queueName pour adresser une file d'attente privée.

**R :** Vérifiez la file d’attente identificateur URI (Uniform Resource) dans votre configuration et le code. N'utilisez pas le caractère « $ » dans l'URI. Par exemple, pour adresser une file d'attente privée nommée OrdersQueue, spécifiez l'URI comme net.msmq://localhost/private/ordersQueue.

**Q :** Appel `ServiceHost.Open()` sur mon application en file d’attente lève l’exception suivante : `System.ArgumentException`: Une adresse de base ne peut pas contenir une chaîne de requête URI. Pourquoi ?

**R :** Vérifiez la file d’attente URI dans votre fichier de configuration et dans votre code. Alors que les files d'attente MSMQ prennent en charge l'utilisation du caractère '?', les Uri interprètent ce dernier comme le début d'une requête de chaîne. Pour éviter ce problème, utilisez des noms de file d'attente qui ne comportent pas de caractère '?'.

**Q :** Mon envoi a réussi, mais aucune opération de service est appelée sur le récepteur. Pourquoi ?

**R :** Pour déterminer la réponse, parcourez la liste de vérification suivante :

- Vérifiez que les spécifications de la file d’attente transactionnelle sont compatibles avec les garanties spécifiées. Notez les principes suivants :

  - Vous pouvez envoyer des messages durables (datagrammes et sessions) avec « exactement une fois » garanties (<xref:System.ServiceModel.MsmqBindingBase.ExactlyOnce%2A> = `true`) uniquement à une file d’attente transactionnelle.

  - Vous pouvez envoyer des sessions uniquement avec des garanties « exactly-once ».

  - Une transaction est requise pour recevoir des messages dans une session provenant d’une file d’attente transactionnelle.

  - Vous pouvez envoyer ou recevoir des messages volatiles ou durables (datagrammes uniquement) sans assurances (<xref:System.ServiceModel.MsmqBindingBase.ExactlyOnce%2A> = `false`) uniquement à une file d’attente non transactionnelle.

- Vérifiez la file d'attente de lettres mortes. Si vous y trouvez les messages, déterminez pourquoi ils n'ont pas été remis.

- Recherchez dans les files d'attente sortantes d'éventuels problèmes de connectivité ou d'adressage.

**Q :** J’ai spécifié une file d’attente de lettres mortes personnalisée, mais lorsque je démarre l’application expéditrice, j’obtiens une exception soit la file d’attente de lettres mortes est introuvable ou que l’application émettrice ne possède aucune autorisation sur la file d’attente de lettres mortes. Pourquoi ?

**R :** La file de lettres mortes personnalisée URI doit inclure « localhost » ou le nom d’ordinateur dans le premier segment, par exemple, NET.MSMQ://localhost/Private/myappdead-Letter queue.

**Q :** Est-il toujours nécessaire de définir une file d’attente de lettres mortes personnalisée, ou existe-t-il une file d’attente de lettres mortes par défaut ?

**R :** Si les garanties sont « exactement une fois » (<xref:System.ServiceModel.MsmqBindingBase.ExactlyOnce%2A> = `true`), et si vous ne spécifiez pas une file d’attente de lettres mortes personnalisée, la valeur par défaut est une file d’attente de lettres mortes transactionnel du système.

Si les garanties n’existent pas (<xref:System.ServiceModel.MsmqBindingBase.ExactlyOnce%2A> = `false`), puis la valeur par défaut n’existe aucune fonctionnalité de file d’attente de lettres mortes.

**Q :** Mon service lève sur SvcHost.Open avec un message « les spécifications EndpointListener ne peuvent pas être respectées par ListenerFactory ». Pourquoi ?

Un fichier . Consultez votre contrat de service. Vous avez peut-être oublié de mettre « IsOneWay =`true`» sur toutes les opérations de service. Les files d'attente prennent uniquement en charge les opérations de service monodirectionnelles.

**Q :** Il existe des messages dans la file d’attente, mais aucune opération de service est appelée. Quel est le problème ?

**R :** Déterminer si votre hôte de service est défectueux. Vous pouvez le vérifier en examinant le suivi ou en implémentant `IErrorHandler`. L'hôte de service provoque une erreur, par défaut, si un message incohérent est détecté.

**Q :** Il existe des messages dans la file d’attente, mais mon service en file d’attente hébergée sur le Web n’est pas activé. Pourquoi ?

**R :** La raison la plus courante est d’autorisations.

1. Vérifiez que le processus `NetMsmqActivator` s'exécute et que des autorisations de lecture et de recherche sont attribuées à l'identité du processus `NetMsmqActivator` sur la file d'attente.

2. Si `NetMsmqActivator` surveille les files d'attente sur un ordinateur distant, assurez-vous que `NetMsmqActivator` ne s'exécute pas sous un jeton restreint. Pour exécuter `NetMsmqActivator` avec un jeton non restreint :

    ```
    sc sidtype NetMsmqActivator unrestricted
    ```

Pour les non Web hôte des problèmes de sécurité, reportez-vous à : [Web hébergeant une Application en file d’attente](../../../../docs/framework/wcf/feature-details/web-hosting-a-queued-application.md).

**Q :** Qu’est le moyen le plus simple d’accéder aux sessions ?

**R :** Définir la saisie semi-automatique =`true` sur l’opération qui correspond au dernier message de la session, puis définissez la saisie semi-automatique =`false` sur toutes les opérations de service restantes.

**Q :** Où puis-je trouver des réponses aux questions courantes sur MSMQ ?

**R :** Pour plus d’informations sur MSMQ, consultez [Microsoft Message Queuing](https://go.microsoft.com/fwlink/?LinkId=87810).

**Q :** Pourquoi mon service lève-t-il une `ProtocolException` lorsque la lecture à partir d’une file d’attente qui contient à la fois en file d’attente de messages de session et en file d’attente de messages de datagramme ?

**R :** Il existe une différence fondamentale dans les messages de façon en file d’attente de session et les messages de datagramme en file d’attente. De ce fait, un service conçu pour lire un message de session en file d'attente ne peut pas recevoir de message de datagramme en file d'attente et un service conçu pour lire un message de datagramme en file d'attente ne peut pas recevoir de message de session. La tentative de lire les deux types de messages à partir de la même file d'attente lève l'exception suivante :

```
System.ServiceModel.MsmqPoisonMessageException: The transport channel detected a poison message. This occurred because the message exceeded the maximum number of delivery attempts or because the channel detected a fundamental problem with the message. The inner exception may contain additional information.
---> System.ServiceModel.ProtocolException: An incoming MSMQ message contained invalid or unexpected .NET Message Framing information in its body. The message cannot be received. Ensure that the sender is using a compatible service contract with a matching SessionMode.
```

La file d'attente de lettres mortes du système, ainsi que toutes les files d'attente de lettres mortes personnalisées, sont particulièrement exposées à ce problème si une application envoie à la fois des messages de session en file d'attente et des messages de datagramme en file d'attente depuis le même ordinateur. Si un message ne peut pas être envoyé avec succès, il est déplacé vers la file d'attente de lettres mortes. Dans ces circonstances, il est possible d'avoir à la fois des messages de session et de datagramme dans la file d'attente de lettres mortes. Il n'existe aucun moyen de séparer les deux types de messages pendant l'exécution lors de la lecture à partir d'une file d'attente, par conséquent, les applications ne doivent pas envoyer à la fois des messages de session en file d'attente et des messages de datagramme en file d'attente depuis le même ordinateur.

### <a name="msmq-integration-specific-troubleshooting"></a>Intégration de MSMQ : Résolution des problèmes spécifiques

**Q :** Lorsque j’envoie un message, ou lorsque j’ouvre l’hôte de service, j’obtiens une erreur indiquant que le modèle est incorrect. Pourquoi ?

**R :** Lorsque vous utilisez la liaison d’intégration MSMQ, vous devez utiliser le modèle msmq.formatname. Par exemple, msmq.formatname:DIRECT=OS:. \private $ \OrdersQueue. Mais lorsque vous spécifiez la file d'attente de lettres mortes personnalisée, vous devez utiliser le modèle net.msmq.

**Q :** Lorsque vous utilisez un nom de format public ou privé, que vous ouvrez l’hôte de service sur [!INCLUDE[wv](../../../../includes/wv-md.md)], j’obtiens une erreur. Pourquoi ?

**R :** Le canal d’intégration WCF sur [!INCLUDE[wv](../../../../includes/wv-md.md)] vérifie si une sous-file d’attente peut être ouverts pour la file d’attente de l’application principale pour la gestion des messages incohérents. Le nom de la sous-file d'attente est dérivé d'un URI msmq.formatname transmis à l'écouteur. Le nom de la sous-file d'attente dans MSMQ peut uniquement être un nom de format direct. Donc vous obtenez l'erreur. Remplacez l'URI de la file d'attente par un nom de format direct.

**Q :** Lors de la réception d’une application MSMQ, le message se trouve dans la file d’attente et n’est pas lu par l’application de réception WCF. Pourquoi ?

**R :** Vérifiez si le message a un corps. Si le message n'a aucun corps, le canal d'intégration MSMQ l'ignore. Implémentez `IErrorHandler` pour être averti des exceptions et vérifiez les suivis.

### <a name="security-related-troubleshooting"></a>Résolution des problèmes liés à la sécurité

**Q :** Lorsque j’exécute l’exemple qui utilise une liaison par défaut en mode de groupe de travail, les messages semblent être envoyés mais ne sont jamais reçus par le destinataire.

**R :** Par défaut, les messages sont signés à l’aide d’un certificat interne MSMQ qui requiert le service d’annuaire Active Directory. En mode groupe de travail, parce qu'Active Directory n'est pas disponible, la signature des messages échoue. Par conséquent, le message arrive dans la file d’attente de lettres mortes et les causes de défaillance, telles que « Signature incorrecte », sont indiquée.

La solution à ce problème consiste à désactiver la sécurité. Cela est effectué en définissant <xref:System.ServiceModel.NetMsmqSecurity.Mode%2A>  =  <xref:System.ServiceModel.NetMsmqSecurityMode.None> pour qu’il fonctionne en mode de groupe de travail.

Une autre solution consiste à obtenir <xref:System.ServiceModel.MsmqTransportSecurity> de la propriété <xref:System.ServiceModel.NetMsmqSecurity.Transport%2A> et à lui affecter la valeur <xref:System.ServiceModel.MsmqAuthenticationMode.Certificate>, puis à définir le certificat client.

Une autre solution consiste à installer MSMQ avec l'intégration Active Directory.

**Q :** Lorsque j’envoie un message avec la liaison par défaut (sécurité de transport activée) dans Active Directory à une file d’attente, j’obtiens un message « certificat interne introuvable ». Comment puis-je résoudre ce problème ?

**R :** Cela signifie que le certificat dans Active Directory pour l’expéditeur doit être renouvelé. Pour ce faire, ouvrez **le panneau de configuration**, **outils d’administration**, **gestion de l’ordinateur**, avec le bouton droit **MSMQ**, puis sélectionnez **Propriétés**. Sélectionnez le **certificat utilisateur** onglet et cliquez sur le **Renew** bouton.

**Q :** Lorsque j’envoie un message à l’aide <xref:System.ServiceModel.MsmqAuthenticationMode.Certificate> et spécifier le certificat à utiliser, j’obtiens un message « Certificat non valide ». Comment puis-je résoudre ce problème ?

**R :** Vous ne pouvez pas utiliser un magasin de certificats ordinateur local avec le mode de certificat. Vous devez copier le certificat du magasin de certificats de l'ordinateur vers le magasin de l'utilisateur actuel à l'aide du composant logiciel enfichable Certificat. Pour obtenir le composant logiciel enfichable Certificat :

1. Cliquez sur **Démarrer**, sélectionnez **exécuter**, type `mmc`, puis cliquez sur **OK**.

2. Dans le **Microsoft Management Console**, ouvrez le **fichier** menu et sélectionnez **ajouter/supprimer un composant logiciel enfichable**.

3. Dans le **ajouter/supprimer un composant logiciel enfichable** boîte de dialogue, cliquez sur le **ajouter** bouton.

4. Dans le **ajouter Standalone Snap-in** boîte de dialogue, sélectionnez certificats et cliquez sur **ajouter**.

5. Dans le **certificats** boîte de dialogue composant logiciel enfichable, sélectionnez **mon compte d’utilisateur,** et cliquez sur **Terminer**.

6. Ensuite, ajoutez une seconde certificats composant logiciel enfichable à l’aide des étapes précédentes, mais cette fois-ci, sélectionnez **compte d’ordinateur** et cliquez sur **suivant**.

7. Sélectionnez **ordinateur Local** et cliquez sur **Terminer**. Vous pouvez à présent glisser et déposer des certificats depuis le magasin de certificats de l’ordinateur vers le magasin de l’utilisateur actuel.

**Q :** Lorsque mon service lit à partir d’une file d’attente sur un autre ordinateur en mode de groupe de travail, j’obtiens une exception « accès refusé ».

**R :** En mode groupe de travail, pour une application à distance accéder à la file d’attente, l’application doit avoir l’autorisation pour accéder à la file d’attente. Ajoutez « Connexion anonyme » à la liste de contrôle d’accès (ACL) de la file d’attente et lui donner une autorisation de lecture.

**Q :** Lorsqu’un client de service réseau (ou n’importe quel client qui n’a pas d’un compte de domaine) envoie un message en file d’attente, l’envoi échoue avec un certificat non valide. Comment puis-je résoudre ce problème ?

**R :** Vérifiez la configuration de liaison. Pour la liaison par défaut, la sécurité de transport MSMQ est activée afin de signer le message. Désactivez-la.

### <a name="remote-transacted-receives"></a>Réceptions avec transactions distantes

**Q :** Lorsque j’ai une file d’attente un et un service WCF qui lit les messages à partir d’une file d’attente sur l’ordinateur B (scénario de réception l’avec transaction distante) de l’ordinateur, ils sont ne pas lus à partir de la file d’attente. Les informations de traçage indiquent la réception a échoué avec le message « Transaction ne peut pas être importé. » Que puis-je faire pour résoudre ce problème ?

**R :** Il existe trois raisons possibles à ce problème :

- Si vous êtes en mode domaine, la réception avec transaction distante requiert l'accès réseau MSDTC (Microsoft Distributed Transaction Coordinator). Vous pouvez l’activer à l’aide de **ajouter/supprimer des composants**.

  ![Capture d’écran montrant l’activation de réseau DTC accès.](./media/troubleshooting-queued-messaging/enable-distributed-transaction-coordinator-access.jpg)

- Vérifiez le mode d’authentification pour communiquer avec le gestionnaire de transactions. Si vous êtes en mode groupe de travail, « Aucune authentification requise » ne doit être sélectionnée. Si vous êtes en mode de domaine, « Authentification mutuelle requise » doit être sélectionnée.

  ![Activation des transactions XA](../../../../docs/framework/wcf/feature-details/media/4f3695e0-fb0b-4c5b-afac-75f8860d2bb0.jpg "4f3695e0-fb0b-4c5b-afac-75f8860d2bb0")

- Vérifiez que MSDTC est dans la liste des exceptions dans le **pare-feu** paramètres.

- Vérifiez que vous utilisez [!INCLUDE[wv](../../../../includes/wv-md.md)]. MSMQ sur [!INCLUDE[wv](../../../../includes/wv-md.md)] prend en charge la lecture avec transaction distante. MSMQ sur les mises en production antérieures de Windows ne prend pas en charge la lecture avec transaction distante.

**Q :** Lorsque le service qui lit à partir de la file d’attente est un service réseau, par exemple, dans un site Web hôte, je reçois une exception d’accès refusé est générée lors de la lecture à partir de la file d’attente ?

**R :** Accès en lecture de service réseau doit être ajouté à la liste ACL pour s’assurer qu’un service réseau peut lire à partir de la file d’attente de la file d’attente.

**Q :** Puis-je utiliser le service d’activation MSMQ pour activer des applications basées sur les messages dans une file d’attente sur un ordinateur distant ?

**R :** Oui. Pour cela, vous devez configurer le service d'activation MSMQ afin qu'il s'exécute comme un service réseau, puis ajouter l'accès au service réseau à la file d'attente sur l'ordinateur distant.

## <a name="using-custom-msmq-bindings-with-receivecontext-enabled"></a>Utilisation de liaisons MSMQ personnalisées avec ReceiveContext activé

Si vous utilisez une liaison MSMQ personnalisée avec <xref:System.ServiceModel.Channels.ReceiveContext> activé, le traitement d'un message entrant utilisera un thread de pool de threads car le protocole MSMQ natif ne prend pas en charge les ports de terminaison d'E/S pour les réceptions <xref:System.ServiceModel.Channels.ReceiveContext> asynchrones. En effet, le traitement de ce message utilise des transactions internes pour <xref:System.ServiceModel.Channels.ReceiveContext> et  MSMQ ne prend pas en charge le traitement asynchrone. Pour contourner ce problème vous pouvez ajouter un <xref:System.ServiceModel.Description.SynchronousReceiveBehavior> au point de terminaison pour forcer le traitement synchrone ou affecter la valeur 1 à la propriété <xref:System.ServiceModel.Description.DispatcherSynchronizationBehavior.MaxPendingReceives%2A>.
