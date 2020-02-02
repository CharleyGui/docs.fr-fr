---
title: Résolution des problèmes de messagerie en file d'attente
ms.date: 03/30/2017
ms.assetid: a5f2836f-018d-42f5-a571-1e97e64ea5b0
ms.openlocfilehash: 5c039c34983647884561f33645f26e4a89280248
ms.sourcegitcommit: cdf5084648bf5e77970cbfeaa23f1cab3e6e234e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/01/2020
ms.locfileid: "76921265"
---
# <a name="troubleshooting-queued-messaging"></a>Résolution des problèmes de messagerie en file d'attente

Cette section contient des questions courantes et une aide pour la résolution des problèmes liés à l’utilisation des files d’attente dans Windows Communication Foundation (WCF).

## <a name="common-questions"></a>Questions courantes

**Q :** J’ai utilisé la version bêta 1 de WCF et j’ai installé le correctif MSMQ. Est-ce que je dois supprimer le correctif logiciel ?

**R :** Oui. Ce correctif logiciel n'est plus pris en charge. WCF fonctionne désormais sur MSMQ sans nécessiter de correctif logiciel.

**Q :** Il existe deux liaisons pour MSMQ : <xref:System.ServiceModel.NetMsmqBinding> et <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding>. Laquelle dois-je utiliser et à quel moment ?

**R :** Utilisez la <xref:System.ServiceModel.NetMsmqBinding> lorsque vous souhaitez utiliser MSMQ comme transport pour la communication en file d’attente entre deux applications WCF. Utilisez la <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding> lorsque vous souhaitez utiliser des applications MSMQ existantes pour communiquer avec les nouvelles applications WCF.

**Q :** Dois-je mettre à niveau MSMQ pour utiliser les liaisons <xref:System.ServiceModel.NetMsmqBinding> et `MsmqIntegration` ?

**R :** non. Les deux liaisons fonctionnent avec MSMQ 3,0 sur Windows XP et Windows Server 2003. Certaines fonctionnalités des liaisons deviennent disponibles lorsque vous effectuez une mise à niveau vers MSMQ 4,0 dans Windows Vista.

**Q :** Quelles sont les fonctionnalités des liaisons <xref:System.ServiceModel.NetMsmqBinding> et <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding> sont disponibles dans MSMQ 4,0, mais pas dans MSMQ 3,0 ?

**R :** Les fonctionnalités suivantes sont disponibles dans MSMQ 4,0, mais pas dans MSMQ 3,0 :

- La file d'attente de lettres mortes personnalisée est uniquement prise en charge sur MSMQ 4.0.

- MSMQ 3.0 et 4.0 gèrent les messages incohérents différemment.

- Seul MSMQ 4.0 prend en charge la lecture transactionnelle à distance.

Pour plus d’informations, consultez différences entre les [fonctionnalités de mise en file d’attente dans Windows Vista, Windows Server 2003 et Windows XP](../../../../docs/framework/wcf/feature-details/diff-in-queue-in-vista-server-2003-windows-xp.md).

**Q :** Puis-je utiliser MSMQ 3,0 sur l’un des côtés d’une communication en file d’attente et MSMQ 4,0 de l’autre côté ?

**R :** Oui.

**Q :** Je souhaite intégrer des applications MSMQ existantes à de nouveaux clients ou serveurs WCF. Est-ce que je dois mettre à niveau les deux côtés de mon infrastructure MSMQ ?

**R :** non. Vous n'êtes pas obligé d'effectuer la mise à niveau vers MSMQ 4.0 sur l'un ou l'autre des côtés.

## <a name="troubleshooting"></a>Résolution des problèmes

Cette section contient les solutions aux problèmes les plus courants. Certains problèmes correspondant à des restrictions connues sont également décrits dans les notes de publication.

**Q :** J’essaie d’utiliser une file d’attente privée et j’obtiens l’exception suivante : `System.InvalidOperationException`: l’URL n’est pas valide. L'URL de la file d'attente ne peut pas contenir le caractère « $ ». Utilisez la syntaxe dans net.msmq://machine/private/queueName pour adresser une file d'attente privée.

**R :** Vérifiez la file d’attente Uniform Resource Identifier (URI) dans votre configuration et votre code. N'utilisez pas le caractère « $ » dans l'URI. Par exemple, pour adresser une file d'attente privée nommée OrdersQueue, spécifiez l'URI comme net.msmq://localhost/private/ordersQueue.

**Q :** L’appel de `ServiceHost.Open()` sur mon application en file d’attente lève l’exception suivante : `System.ArgumentException`: une adresse de base ne peut pas contenir une chaîne de requête d’URI. Pourquoi ?

**R :** Vérifiez l’URI de la file d’attente dans votre fichier de configuration et dans votre code. Alors que les files d'attente MSMQ prennent en charge l'utilisation du caractère '?', les Uri interprètent ce dernier comme le début d'une requête de chaîne. Pour éviter ce problème, utilisez des noms de file d'attente qui ne comportent pas de caractère '?'.

**Q :** Mon envoi a réussi mais aucune opération de service n’est appelée sur le récepteur. Pourquoi ?

**R :** Pour déterminer la réponse, utilisez la liste de vérification suivante :

- Vérifiez que les spécifications de la file d’attente transactionnelle sont compatibles avec les garanties spécifiées. Notez les principes suivants :

  - Vous pouvez envoyer des messages durables (datagrammes et sessions) avec des garanties « exactement une fois » (<xref:System.ServiceModel.MsmqBindingBase.ExactlyOnce%2A> = `true`) uniquement à une file d’attente transactionnelle.

  - Vous pouvez envoyer des sessions uniquement avec des garanties « exactly-once ».

  - Une transaction est requise pour recevoir des messages dans une session provenant d’une file d’attente transactionnelle.

  - Vous pouvez envoyer ou recevoir des messages volatils ou durables (datagrammes uniquement) sans garanties (<xref:System.ServiceModel.MsmqBindingBase.ExactlyOnce%2A> = `false`) qu’à une file d’attente non transactionnelle.

- Vérifiez la file d'attente de lettres mortes. Si vous y trouvez les messages, déterminez pourquoi ils n'ont pas été remis.

- Recherchez dans les files d'attente sortantes d'éventuels problèmes de connectivité ou d'adressage.

**Q :** J’ai spécifié une file d’attente de lettres mortes personnalisée, mais lorsque je démarre l’application expéditeur, j’obtiens une exception indiquant que la file d’attente de lettres mortes est introuvable ou que l’application émettrice n’a pas d’autorisation sur la file d’attente de lettres mortes. Pourquoi ?

**R :** L’URI de la file d’attente de lettres mortes personnalisée doit inclure un « localhost » ou le nom de l’ordinateur dans le premier segment, par exemple, net. msmq://localhost/private/myAppdead-letter queue.

**Q :** Est-il toujours nécessaire de définir une file d’attente de lettres mortes personnalisée, ou existe-t-il une file d’attente de lettres mortes par défaut ?

**R :** Si les assurances sont « exactement une fois » (<xref:System.ServiceModel.MsmqBindingBase.ExactlyOnce%2A> = `true`) et si vous ne spécifiez pas de file d’attente de lettres mortes personnalisée, la valeur par défaut est une file d’attente de lettres mortes transactionnelle à l’ensemble du système.

Si les garanties sont None (<xref:System.ServiceModel.MsmqBindingBase.ExactlyOnce%2A> = `false`), la valeur par défaut est aucune fonctionnalité de file d’attente de lettres mortes.

**Q :** Mon service lève une exception dans SvcHost. Open avec un message « EndpointListener Requirements ne peut pas être respecté par ListenerFactory ». Pourquoi ?

A. Consultez votre contrat de service. Vous avez peut-être oublié de placer « IsOneWay =`true`» sur toutes les opérations de service. Les files d'attente prennent uniquement en charge les opérations de service monodirectionnelles.

**Q :** Il y a des messages dans la file d’attente, mais aucune opération de service n’est appelée. Quel est le problème ?

**R :** Déterminez si votre hôte de service a généré une erreur. Vous pouvez le vérifier en examinant le suivi ou en implémentant `IErrorHandler`. L'hôte de service provoque une erreur, par défaut, si un message incohérent est détecté.

**Q :** La file d’attente contient des messages, mais mon service hébergé sur le Web n’est pas activé. Pourquoi ?

**R :** La raison la plus courante est l’autorisation.

1. Vérifiez que le processus `NetMsmqActivator` s'exécute et que des autorisations de lecture et de recherche sont attribuées à l'identité du processus `NetMsmqActivator` sur la file d'attente.

2. Si `NetMsmqActivator` surveille les files d'attente sur un ordinateur distant, assurez-vous que `NetMsmqActivator` ne s'exécute pas sous un jeton restreint. Pour exécuter `NetMsmqActivator` avec un jeton non restreint :

    ```console
    sc sidtype NetMsmqActivator unrestricted
    ```

Pour les problèmes d’hôte Web non liés à la sécurité, reportez-vous à : [hébergement Web d’une application en file d’attente](../../../../docs/framework/wcf/feature-details/web-hosting-a-queued-application.md).

**Q :** Quel est le moyen le plus simple d’accéder aux sessions ?

**R :** Définissez la saisie semi-automatique =`true` sur l’opération qui correspond au dernier message de la session, puis définissez la saisie semi-automatique =`false` sur toutes les opérations de service restantes.

**Q :** Pourquoi mon service lève-t-il une `ProtocolException` lors de la lecture d’une file d’attente contenant à la fois des messages de session en file d’attente et des messages de datagramme en file d’attente ?

**R :** Il existe une différence fondamentale dans la façon dont les messages de session en file d’attente et les messages de datagramme en file d’attente sont composés. De ce fait, un service conçu pour lire un message de session en file d'attente ne peut pas recevoir de message de datagramme en file d'attente et un service conçu pour lire un message de datagramme en file d'attente ne peut pas recevoir de message de session. La tentative de lire les deux types de messages à partir de la même file d'attente lève l'exception suivante :

```console
System.ServiceModel.MsmqPoisonMessageException: The transport channel detected a poison message. This occurred because the message exceeded the maximum number of delivery attempts or because the channel detected a fundamental problem with the message. The inner exception may contain additional information.
---> System.ServiceModel.ProtocolException: An incoming MSMQ message contained invalid or unexpected .NET Message Framing information in its body. The message cannot be received. Ensure that the sender is using a compatible service contract with a matching SessionMode.
```

La file d'attente de lettres mortes du système, ainsi que toutes les files d'attente de lettres mortes personnalisées, sont particulièrement exposées à ce problème si une application envoie à la fois des messages de session en file d'attente et des messages de datagramme en file d'attente depuis le même ordinateur. Si un message ne peut pas être envoyé avec succès, il est déplacé vers la file d'attente de lettres mortes. Dans ces circonstances, il est possible d'avoir à la fois des messages de session et de datagramme dans la file d'attente de lettres mortes. Il n'existe aucun moyen de séparer les deux types de messages pendant l'exécution lors de la lecture à partir d'une file d'attente, par conséquent, les applications ne doivent pas envoyer à la fois des messages de session en file d'attente et des messages de datagramme en file d'attente depuis le même ordinateur.

### <a name="msmq-integration-specific-troubleshooting"></a>Intégration de MSMQ : Dépannage spécifique

**Q :** Lorsque j’envoie un message, ou lorsque j’ouvre l’hôte de service, j’obtiens une erreur indiquant que le schéma est incorrect. Pourquoi ?

**R :** Lorsque vous utilisez la liaison d’intégration MSMQ, vous devez utiliser le schéma msmq. formatname. Par exemple, msmq.formatname:DIRECT=OS:. \private $ \OrdersQueue. Mais lorsque vous spécifiez la file d'attente de lettres mortes personnalisée, vous devez utiliser le modèle net.msmq.

**Q :** Lorsque j’utilise un nom de format public ou privé et que j’ouvre l’hôte de service sur Windows Vista, j’obtiens une erreur. Pourquoi ?

**R :** Le canal d’intégration WCF sur Windows Vista vérifie si une sous-file d’attente peut être ouverte pour la file d’attente d’application principale pour la gestion des messages incohérents. Le nom de la sous-file d'attente est dérivé d'un URI msmq.formatname transmis à l'écouteur. Le nom de la sous-file d'attente dans MSMQ peut uniquement être un nom de format direct. Donc vous obtenez l'erreur. Remplacez l'URI de la file d'attente par un nom de format direct.

**Q :** Lors de la réception d’un message à partir d’une application MSMQ, le message se trouve dans la file d’attente et n’est pas lu par l’application WCF de réception. Pourquoi ?

**R :** Vérifiez si le message a un corps. Si le message n'a aucun corps, le canal d'intégration MSMQ l'ignore. Implémentez `IErrorHandler` pour être averti des exceptions et vérifiez les suivis.

### <a name="security-related-troubleshooting"></a>Résolution des problèmes liés à la sécurité

**Q :** Lorsque j’exécute l’exemple qui utilise une liaison par défaut en mode groupe de travail, les messages semblent être envoyés mais ne sont jamais reçus par le destinataire.

**R :** Par défaut, les messages sont signés à l’aide d’un certificat MSMQ interne qui requiert le service d’annuaire Active Directory. En mode groupe de travail, parce qu'Active Directory n'est pas disponible, la signature des messages échoue. Par conséquent, le message arrive dans la file d’attente de lettres mortes et la cause de l’échec, par exemple « signature incorrecte », est indiquée.

La solution à ce problème consiste à désactiver la sécurité. Pour ce faire, définissez <xref:System.ServiceModel.NetMsmqSecurity.Mode%2A> = <xref:System.ServiceModel.NetMsmqSecurityMode.None> pour qu’il fonctionne en mode groupe de travail.

Une autre solution consiste à obtenir <xref:System.ServiceModel.MsmqTransportSecurity> de la propriété <xref:System.ServiceModel.NetMsmqSecurity.Transport%2A> et à lui affecter la valeur <xref:System.ServiceModel.MsmqAuthenticationMode.Certificate>, puis à définir le certificat client.

Une autre solution consiste à installer MSMQ avec l'intégration Active Directory.

**Q :** Lorsque j’envoie un message avec la liaison par défaut (sécurité de transport activée) dans Active Directory vers une file d’attente, j’obtiens un message « certificat interne introuvable ». Comment puis-je résoudre ce problème ?

**R :** Cela signifie que le certificat de Active Directory pour l’expéditeur doit être renouvelé. Pour ce faire, ouvrez le **panneau de configuration**, **Outils d’administration**, gestion de l' **ordinateur**, cliquez avec le bouton droit sur **MSMQ**, puis sélectionnez **Propriétés**. Sélectionnez l’onglet **certificat utilisateur** , puis cliquez sur le bouton **renouveler** .

**Q :** Lorsque j’envoie un message à l’aide de <xref:System.ServiceModel.MsmqAuthenticationMode.Certificate> et que vous spécifiez le certificat à utiliser, j’obtiens un message « certificat non valide ». Comment puis-je résoudre ce problème ?

**R :** Vous ne pouvez pas utiliser un magasin de certificats de l’ordinateur local avec le mode certificat. Vous devez copier le certificat du magasin de certificats de l'ordinateur vers le magasin de l'utilisateur actuel à l'aide du composant logiciel enfichable Certificat. Pour obtenir le composant logiciel enfichable Certificat :

1. Cliquez sur **Démarrer**, sélectionnez **exécuter**, tapez `mmc`, puis cliquez sur **OK**.

2. Dans **Microsoft Management Console**, ouvrez le menu **fichier** et sélectionnez **Ajouter/supprimer un composant logiciel enfichable**.

3. Dans la boîte de dialogue **Ajouter/supprimer un composant logiciel enfichable** , cliquez sur le bouton **Ajouter** .

4. Dans la boîte de dialogue **Ajout d’un composant logiciel enfichable autonome** , sélectionnez certificats, puis cliquez sur **Ajouter**.

5. Dans la boîte de dialogue composant logiciel enfichable **certificats** , sélectionnez **mon compte d’utilisateur,** puis cliquez sur **Terminer**.

6. Ensuite, ajoutez un deuxième composant logiciel enfichable certificats à l’aide des étapes précédentes, mais cette fois, sélectionnez **compte d’ordinateur** , puis cliquez sur **suivant**.

7. Sélectionnez **ordinateur local** , puis cliquez sur **Terminer**. Vous pouvez à présent glisser et déposer des certificats depuis le magasin de certificats de l’ordinateur vers le magasin de l’utilisateur actuel.

**Q :** Lorsque mon service lit à partir d’une file d’attente sur un autre ordinateur en mode groupe de travail, j’obtiens une exception « accès refusé ».

**R :** En mode groupe de travail, pour qu’une application distante ait accès à la file d’attente, elle doit avoir l’autorisation d’accéder à la file d’attente. Ajoutez « connexion anonyme » à la liste de contrôle d’accès (ACL) de la file d’attente et accordez-lui l’autorisation lecture.

**Q :** Lorsqu’un client de service réseau (ou un client qui n’a pas de compte de domaine) envoie un message mis en file d’attente, l’envoi échoue avec un certificat non valide. Comment puis-je résoudre ce problème ?

**R :** Vérifiez la configuration de la liaison. Pour la liaison par défaut, la sécurité de transport MSMQ est activée afin de signer le message. Désactivez-la.

### <a name="remote-transacted-receives"></a>Réceptions avec transactions distantes

**Q :** Lorsque j’ai une file d’attente sur l’ordinateur A et un service WCF qui lit les messages d’une file d’attente sur l’ordinateur B (scénario de réception avec transaction distante), les messages ne sont pas lus à partir de la file d’attente. Les informations de traçage indiquent que la réception a échoué avec le message « Impossible d’importer la transaction ». Que puis-je faire pour résoudre ce problème ?

**R :** Il existe trois raisons possibles :

- Si vous êtes en mode domaine, la réception avec transaction distante requiert l'accès réseau MSDTC (Microsoft Distributed Transaction Coordinator). Vous pouvez l’activer à l’aide de l' **Ajout/suppression de composants**.

  ![Capture d’écran montrant l’activation de l’accès DTC réseau.](./media/troubleshooting-queued-messaging/enable-distributed-transaction-coordinator-access.jpg)

- Vérifiez le mode d’authentification pour communiquer avec le gestionnaire de transactions. Si vous êtes en mode groupe de travail, vous devez sélectionner « aucune authentification requise ». Si vous êtes en mode de domaine, vous devez sélectionner « authentification mutuelle requise ».

  ![Activation des transactions XA](../../../../docs/framework/wcf/feature-details/media/4f3695e0-fb0b-4c5b-afac-75f8860d2bb0.jpg "4f3695e0-fb0b-4c5b-afac-75f8860d2bb0")

- Assurez-vous que MSDTC figure dans la liste des exceptions dans les paramètres du **pare-feu de connexion Internet** .

- Vérifiez que vous utilisez Windows Vista. MSMQ sur Windows Vista prend en charge la lecture transactionnelle à distance. MSMQ sur les mises en production antérieures de Windows ne prend pas en charge la lecture avec transaction distante.

**Q :** Lorsque le service lisant à partir de la file d’attente est un service réseau, par exemple, dans un hôte Web, pourquoi est-ce que j’obtiens une exception d’accès refusé est déclenchée lors de la lecture à partir de la file d’attente ?

**R :** L’accès en lecture au service réseau doit être ajouté à la liste de contrôle d’accès de file d’attente pour garantir qu’un service réseau peut lire à partir de la file d’attente.

**Q :** Puis-je utiliser le service d’activation MSMQ pour activer des applications basées sur des messages dans une file d’attente sur un ordinateur distant ?

**R :** Oui. Pour cela, vous devez configurer le service d'activation MSMQ afin qu'il s'exécute comme un service réseau, puis ajouter l'accès au service réseau à la file d'attente sur l'ordinateur distant.

## <a name="using-custom-msmq-bindings-with-receivecontext-enabled"></a>Utilisation de liaisons MSMQ personnalisées avec ReceiveContext activé

Si vous utilisez une liaison MSMQ personnalisée avec <xref:System.ServiceModel.Channels.ReceiveContext> activé, le traitement d'un message entrant utilisera un thread de pool de threads car le protocole MSMQ natif ne prend pas en charge les ports de terminaison d'E/S pour les réceptions <xref:System.ServiceModel.Channels.ReceiveContext> asynchrones. En effet, le traitement de ce message utilise des transactions internes pour <xref:System.ServiceModel.Channels.ReceiveContext> et  MSMQ ne prend pas en charge le traitement asynchrone. Pour contourner ce problème vous pouvez ajouter un <xref:System.ServiceModel.Description.SynchronousReceiveBehavior> au point de terminaison pour forcer le traitement synchrone ou affecter la valeur 1 à la propriété <xref:System.ServiceModel.Description.DispatcherSynchronizationBehavior.MaxPendingReceives%2A>.
