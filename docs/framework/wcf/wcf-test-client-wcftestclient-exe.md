---
title: Client test WCF (WcfTestClient.exe)
description: Découvrez le client test WCF, qui fournit des tests de service fluides lorsqu’il est associé à l’hôte de service WCF. Soumettre les valeurs de test du client et afficher les réponses du service.
ms.date: 03/30/2017
ms.assetid: d4302855-677f-4640-aa90-c5d785d72fb7
ms.openlocfilehash: 4f636698c538809f89ee356159839a37b73adb57
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/23/2020
ms.locfileid: "85245659"
---
# <a name="wcf-test-client-wcftestclientexe"></a>Client test WCF (WcfTestClient.exe)
Le client de test Windows Communication Foundation (WCF) (WcfTestClient.exe) est un outil d’interface utilisateur graphique qui permet aux utilisateurs d’entrer des paramètres de test, d’envoyer cette entrée au service et d’afficher la réponse renvoyée par le service. Il fournit une expérience de test de service transparente lorsqu’il est associé à l’hôte de service WCF.

Vous pouvez généralement trouver le client test WCF (WcfTestClient.exe) à l’emplacement suivant : `C:\Program Files (x86)\Microsoft Visual Studio\2017\Community\Common7\IDE` -Community peut être « Enterprise », « Professional » ou « Community », selon le niveau de Visual Studio installé.

## <a name="scenarios-for-using-test-client"></a>Scénarios d'utilisation du client test

Les sections suivantes décrivent les scénarios les plus courants dans lesquels vous pouvez utiliser le client test WCF pour simplifier votre processus de développement.

### <a name="inside-visual-studio"></a>Dans Visual Studio

#### <a name="wcf-service-host-starts-wcf-test-client-with-a-single-service"></a>L'Hôte de service WCF démarre le client test WCF avec un service unique.

Après avoir créé un projet de service WCF et appuyé sur la touche F5 pour démarrer le débogueur, l’hôte de service WCF commence à héberger le service dans votre projet. Ensuite, le client test WCF s’ouvre et affiche une liste des points de terminaison de service définis dans le fichier de configuration. Vous pouvez tester les paramètres et appeler le service, et répéter ce processus pour tester et valider régulièrement votre service.

#### <a name="wcf-service-host-starts-wcf-test-client-with-multiple-services"></a>L'Hôte de service WCF démarre le client test WCF avec plusieurs services

Vous pouvez également utiliser le client test WCF pour déboguer un projet de service contenant plusieurs services. Lorsque le client test WCF s’ouvre, il itère automatiquement la liste des services dans votre projet et les ouvre à des fins de test.

### <a name="outside-visual-studio"></a>En dehors de Visual Studio

Vous pouvez également appeler le client test WCF (WcfTestClient.exe) en dehors de Visual Studio pour tester un service arbitraire sur Internet. Pour localiser l'outil, allez à l'emplacement suivant :

`C:\Program Files (x86)\Microsoft Visual Studio\2017\Community\Common7\IDE`(où Communauté peut être « entreprise », « professionnel » ou « communauté » selon le niveau de Visual Studio installé sur l’ordinateur)

Pour utiliser l'outil, double-cliquez sur le nom de fichier afin de l'ouvrir à partir de cet emplacement ou lancez-le à partir d'une ligne de commandes.

Le client test WCF accepte un nombre arbitraire d’URI en tant qu’arguments de ligne de commande.  Il s'agit des URI des services qui peuvent être testés.

`wcfTestClient.exe URI1 URI2 …`

Une fois la fenêtre cliente test WCF ouverte, cliquez sur **fichier** -> **Ajouter un service**, puis entrez l’adresse du point de terminaison du service que vous souhaitez ouvrir.

## <a name="wcf-test-client-user-interface"></a>Interface utilisateur du client test WCF

Vous pouvez utiliser le client test WCF avec un seul service ou plusieurs services.

### <a name="service-operations"></a>Opérations de service

Le volet gauche de la fenêtre principale du client test WCF répertorie tous les services disponibles, ainsi que leurs points de terminaison et opérations respectifs.

Lorsque vous double-cliquez sur une opération, vous pouvez afficher son contenu dans le volet droit d'un nouvel onglet portant le nom de l'opération.

Le volet gauche répertorie également les fichiers de configuration du client. Double-cliquez sur l'un des éléments pour afficher le contenu du fichier correspondant dans une nouvelle page à onglets, dans le volet droit.

### <a name="entering-test-parameters"></a>Saisie de paramètres de test

Pour afficher les paramètres de test, double-cliquez sur une opération afin de l'ouvrir dans le volet droit. Les paramètres sont affichés dans la vue **mise en forme** par défaut, et vous pouvez entrer des valeurs arbitraires pour les paramètres afin de tester le service.

Pour afficher le code XML du message, cliquez sur **XML**. Pour les envoyer au service, cliquez sur **appeler**.

Pour un paramètre de DataSet, cliquez sur **...** bouton en regard de **modifier...** pour le modifier dans une nouvelle fenêtre qui montre le DataGrid. Notez l’apparence des boutons **copier le DataSet** et **coller le jeu de données** . Si le schéma de l'objet DataSet est inconnu lors de la première modification, DataGrid est vide. Vous devez coller un objet DataSet avec le même schéma dans l'objet actuel de DataGrid. (Notez que vous devez copier le schéma à partir d’un autre emplacement avant l’opération de collage.) Vous pouvez également copier un objet DataSet pour une utilisation ultérieure en cliquant sur le bouton **copier le DataSet** .

La réponse du service apparaît au-dessous des paramètres de test.

> [!NOTE]
> Si la valeur de retour attendue est une chaîne, le résultat est affiché sous la forme d'une chaîne entre guillemet même si l'entrée fournie n'est pas incluse entre guillemet.

Si vous avez spécifié une opération particulière comme étant unidirectionnelle lorsque vous avez créé le contrat pour le service, aucune réponse de service n'est affichée. Dès que le message est placé en file d'attente en vue de sa transmission, une boîte de dialogue apparaît pour vous notifier que le message a été envoyé avec succès.

### <a name="session-support"></a>Prise en charge des sessions

La case à cocher **Démarrer un nouveau proxy** dans l’onglet d’une opération de service vous permet d’activer ou de désactiver la prise en charge des sessions. Elle est désactivée par défaut.

Lorsque vous entrez des paramètres de test pour une opération spécifique (ou une autre opération dans le même point de terminaison de service) et que vous cliquez sur **appeler** plusieurs fois avec la case à cocher désactivée, ces opérations partagent un proxy et l’état du service est rendu persistant entre plusieurs opérations.

Si la case à cocher **Démarrer un nouveau proxy** est activée, un nouveau proxy est démarré pour chaque **appel**, le scénario de session précédent est terminé et l’état du service est réinitialisé.

### <a name="editing-client-configuration"></a>Modification de la configuration client

Le volet gauche de la fenêtre principale du client test WCF répertorie les fichiers de configuration du client. Double-cliquez sur l'un des éléments pour afficher le contenu du fichier dans le volet droit.

#### <a name="edit-with-service-configuration-editor"></a>Modifier avec l'Éditeur de configuration de service

Cliquez avec le bouton droit sur **fichier de configuration** dans le volet gauche et sélectionnez le menu contextuel **modifier avec SvcConfigEditor**. L'Éditeur de configuration de service est lancé avec le contenu de la configuration client. Vous pouvez modifier la configuration et l'enregistrer dans l'outil.

Une fois le fichier enregistré dans l’éditeur de configuration de service, le client test WCF affiche un message d’avertissement pour vous informer que le fichier a été modifié en dehors de et vous demande si vous voulez le recharger.

Si vous sélectionnez **Oui**, le contenu de configuration dans l’onglet « Client.dll.config » reflète les modifications que vous avez apportées dans l’éditeur.

Si vous sélectionnez **non**, le contenu de configuration dans l’onglet « Client.dll.config » reste inchangé et le contenu modifié est automatiquement enregistré dans le fichier source.

#### <a name="restore-to-default-configuration"></a>Restaurer la configuration par défaut

Si vous souhaitez annuler toutes les modifications et restaurer la configuration du client par défaut, cliquez avec le bouton droit sur **fichier de configuration** dans le volet gauche, puis sélectionnez le menu contextuel restaurer la configuration **par défaut**. La valeur de configuration par défaut est chargée et le contenu de l’onglet « Client.dll.config » est restauré.

#### <a name="validate-changes"></a>Valider des modifications

Lorsque des modifications enregistrées sont chargées dans le client test WCF, la validité de la configuration est vérifiée par rapport au schéma WCF. Si les erreurs sont rencontrées, une boîte de dialogue est affichée pour afficher des détails d'erreur.

Pendant la génération de proxy, la compilation binaire ou l’appel de service, les éléments de menu qui prennent en charge la modification (autrement dit, « Edit... », « Restore... », etc.) sont désactivés. L’appel de service est également désactivé lors du chargement de la configuration mise à jour vers le client test WCF.

#### <a name="persist-client-configuration"></a>Rendre la configuration client persistante

L' **Tools** -> **Options** -> onglet Configuration du**client** options des outils contient une option **toujours régénérer la configuration au démarrage des services** , qui est activée par défaut. Cette option spécifie que chaque fois que le client test WCF charge un service, il régénère un fichier de configuration basé sur les derniers contrats de service et fichiers de App.config de service.

Si vous avez modifié la configuration du client pour votre service WCF et que vous souhaitez toujours utiliser ce fichier mis à jour pour déboguer votre service, vous pouvez décocher l’option **régénérer** . En procédant ainsi, même lorsque vous mettez à jour le service et rouvrez le client test WCF, le fichier Client.dll.config est celui que vous avez précédemment mis à jour au lieu d’un client regénéré en fonction du service mis à jour.

Toutefois, il peut s'avérer nécessaire de modifier le fichier de configuration afin qu'il soit conforme au proxy régénéré. Si le proxy régénéré et fichier de configuration ne correspondent pas en raison de la mise à jour d'un service, des erreurs se produiront à l'appel du service.

> [!CAUTION]
> Si vous avez modifié le fichier de configuration client et décidez de le réutiliser ultérieurement, vous le trouverez à l'emplacement suivant :
>
> \Documents and Settings \\ [User Account] \Mes Documents\test client Projects.
>
> Toutes les informations d'identification mises à jour stockées dans le fichier de configuration client sont protégées par la Liste de contrôle d'Accès (ACL) de ce dossier.

### <a name="adding-removing-and-refreshing-services"></a>Ajout, suppression et actualisation des services

#### <a name="add-service"></a>Add Service

Cliquez sur **fichier** -> **Ajouter un service** pour ajouter un service au client test WCF. Vous devez alors taper l'URI (adresse de point de terminaison) du service à ajouter. L'adresse du service peut être une adresse mex ou WSDL.

Vous pouvez également trouver une liste de 10 points de terminaison de services récemment ajoutés dans le sous-menu **services récents** . Si vous en sélectionnez un, le service spécifié est ajouté au client test WCF.

Vous pouvez également cliquer avec le bouton droit sur la racine de l’arborescence des services **mes projets de service**, puis sélectionner **Ajouter un service** pour obtenir le même résultat.

Pendant la génération d'un proxy, une compilation binaire ou l'appel d'un service, les éléments de menu qui prennent en charge l'ajout d'un service sont désactivés. L'appel de service est également désactivé.

#### <a name="remove-service"></a>Supprimer un service

Cliquez avec le bouton droit sur la racine du service à supprimer, puis sélectionnez **supprimer le service** pour supprimer un service du client test WCF.

Pendant la génération d'un proxy, une compilation binaire ou l'appel d'un service, les éléments de menu qui prennent en charge la suppression d'un service sont désactivés. L'appel de service est également désactivé.

#### <a name="refresh-service"></a>Actualiser un service

Si une modification est apportée au service alors que le client test WCF est en cours d’exécution et que vous souhaitez vous assurer que l’implémentation du client test WCF pour ce service est à jour, cliquez avec le bouton droit sur la racine du service, puis sélectionnez **Actualiser le service**. Notez qu'après avoir actualisé un service, son état est réinitialisé.

Pendant la génération d'un proxy, une compilation binaire ou l'appel d'un service, les éléments de menu qui prennent en charge l'actualisation d'un service sont désactivés. L'appel de service est également désactivé.

## <a name="location-of-files-generated-by-the-test-client"></a>Emplacement des fichiers générés par le client test

Par défaut, le client test WCF stocke les fichiers de code client et de configuration générés dans le dossier « %appdata%\Local\temp\Test client Projects ». Ce dossier est supprimé après la sortie du client test WCF. Si un fichier de configuration est modifié dans le client test WCF et que l’option **toujours régénérer la configuration au démarrage des services** est désactivée, le fichier modifié est copié dans le dossier « CachedConfig » sous « mes projets client Documents\test » avec un fichier XML de mappage (nom de métadonnées-adresse-fichier) en tant qu’index.

Vous pouvez également démarrer le client test WCF dans une ligne de commande, utiliser le `/ProjectPath` commutateur pour spécifier un nouveau chemin d’accès souhaité pour le stockage des fichiers générés ou utiliser le `/RestoreProjectPath` commutateur pour restaurer l’emplacement par défaut. La syntaxe est la suivante :

`wcfTestClient.exe /ProjectPath [desired location]`

L’exécution de cette commande n’ouvre pas le client test WCF. Seul l’emplacement du dossier est changé. Vous pouvez exécuter cette commande si le client test WCF s’exécute ou non. Le nouvel emplacement est appliqué lorsque le client test WCF est redémarré. Les informations d’emplacement peuvent être enregistrées dans le registre ou dans le fichier WcfTestClient.exe. option du dossier « %appdata%\Local\temp\Test client Projects ».

## <a name="features-supported-by-wcf-test-client"></a>Fonctionnalités prises en charge par le client test WCF

Voici une liste des fonctionnalités prises en charge par le client test WCF :

- Appel de service : message unidirectionnel et demande/réponse.

- Liaisons : toutes les liaisons prises en charge par Svcutil.exe.

- Contrôle de session.

- Contrat de message.

- Sérialisation XML.

La liste suivante répertorie les fonctionnalités non prises en charge par le client test WCF :

- Types : <xref:System.IO.Stream>, <xref:System.ServiceModel.Channels.Message>, <xref:System.Xml.XmlElement>, <xref:System.Xml.XmlAttribute>, <xref:System.Xml.XmlNode>, types qui implémentent l'interface <xref:System.Xml.Serialization.IXmlSerializable>, y compris l'attribut <xref:System.Xml.Serialization.XmlSchemaProviderAttribute> associé et les types <xref:System.Xml.Linq.XDocument> et <xref:System.Xml.Linq.XElement>, ainsi que le type ADO.NET <xref:System.Data.DataTable>.

- Contrat duplex.

- Transaction.

- Sécurité : CardSpace, Certificate et nom d’utilisateur/mot de passe.

- Liaisons : WSFederationbinding, toute liaison de contexte et Https, WebHttpbinding (prise en charge des messages de réponse Json).

## <a name="closing-wcf-test-client"></a>Fermeture du client test WCF

Vous pouvez fermer le client test WCF des manières suivantes :

- Dans le menu **Fichier** , cliquez sur **Quitter**. Sinon, dans la fenêtre principale du client test WCF, cliquez sur **Fermer**. Ces deux actions ferment également l’hôte auto du service WCF et arrêtent le processus de débogage de Visual Studio si le client test WCF a été lancé par Visual Studio.

- Cliquez avec le bouton droit sur l’icône **hôte de service WCF** dans la zone de notification, puis cliquez sur **quitter.** Cela arrête à la fois l’hôte de service WCF et le client de test WCF et arrête le processus de débogage de Visual Studio.

## <a name="see-also"></a>Voir aussi

- [WCF Service Host (WcfSvcHost.exe)](wcf-service-host-wcfsvchost-exe.md)
