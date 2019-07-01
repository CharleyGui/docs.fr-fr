---
title: Client test WCF (WcfTestClient.exe)
ms.date: 03/30/2017
ms.assetid: d4302855-677f-4640-aa90-c5d785d72fb7
ms.openlocfilehash: 9044dc2479e8e0a31a6152321231ee1936b74351
ms.sourcegitcommit: 2d42b7ae4252cfe1232777f501ea9ac97df31b63
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2019
ms.locfileid: "67487458"
---
# <a name="wcf-test-client-wcftestclientexe"></a>Client test WCF (WcfTestClient.exe)
Client de Test de Windows Communication Foundation (WCF) (WcfTestClient.exe) est un outil GUI qui permet aux utilisateurs d’entrer des paramètres de test, envoyer ces entrées au service et afficher la réponse que le service renvoie. Il offre de service transparentes lorsqu’il est associé avec l’hôte de Service WCF de test.  
  
 Vous pouvez généralement trouver le Client de Test WCF (WcfTestClient.exe) à l’emplacement suivant : `C:\Program Files (x86)\Microsoft Visual Studio\2017\Community\Common7\IDE` - Communauté peut s’agir de « Enterprise », « Professionnel » ou « Community » selon le niveau de Visual Studio est installé.
  
## <a name="scenarios-for-using-test-client"></a>Scénarios d'utilisation du client test  
 Les sections suivantes décrivent les scénarios les plus courants dans lesquels vous pouvez utiliser le Client Test WCF pour rationaliser votre processus de développement.  
  
### <a name="inside-visual-studio"></a>Dans Visual Studio  
  
#### <a name="wcf-service-host-starts-wcf-test-client-with-a-single-service"></a>L'Hôte de service WCF démarre le client test WCF avec un service unique.  
 Une fois que vous créez un projet de service WCF et appuyez sur F5 pour démarrer le débogueur, l’hôte de Service WCF commence à héberger le service dans votre projet. Ensuite, le Client Test WCF s’ouvre et affiche une liste de points de terminaison de service définis dans le fichier de configuration. Vous pouvez tester les paramètres et appeler le service, et répéter ce processus pour tester et valider régulièrement votre service.  
  
#### <a name="wcf-service-host-starts-wcf-test-client-with-multiple-services"></a>L'Hôte de service WCF démarre le client test WCF avec plusieurs services  
 Vous pouvez également utiliser le Client Test WCF pour aider à déboguer un projet de service qui contient plusieurs services. Lorsque le Client Test WCF s’ouvre, il automatiquement effectue une itération de la liste des services dans votre projet et ouvre à des fins de test.  
  
### <a name="outside-visual-studio"></a>En dehors de Visual Studio  
 Vous pouvez également appeler le Client de Test WCF (WcfTestClient.exe) en dehors de Visual Studio pour tester un service arbitraire sur Internet. Pour localiser l'outil, allez à l'emplacement suivant :  
  
 `C:\Program Files (x86)\Microsoft Visual Studio\2017\Community\Common7\IDE` (où Communauté peut s’agir de « Enterprise », « Professionnel » ou « Community » selon le niveau de Visual Studio est installé sur l’ordinateur)
  
 Pour utiliser l'outil, double-cliquez sur le nom de fichier afin de l'ouvrir à partir de cet emplacement ou lancez-le à partir d'une ligne de commandes.  
  
 Client Test WCF prend un nombre arbitraire d’URI comme arguments de ligne de commande.  Il s'agit des URI des services qui peuvent être testés.  
  
 `wcfTestClient.exe URI1 URI2 …`  
  
 Une fois la fenêtre du Client Test WCF est ouvert, cliquez sur **fichier**->**ajouter un Service**et entrez l’adresse de point de terminaison du service que vous souhaitez ouvrir.  
  
## <a name="wcf-test-client-user-interface"></a>Interface utilisateur du client test WCF  
 Vous pouvez utiliser le Client Test WCF avec un service unique ou plusieurs services.  
  
### <a name="service-operations"></a>Opérations de service  
 Le volet gauche de la fenêtre principale du Client Test WCF répertorie tous les services disponibles, ainsi que leurs points de terminaison respectifs et les opérations.  
  
 Lorsque vous double-cliquez sur une opération, vous pouvez afficher son contenu dans le volet droit d'un nouvel onglet portant le nom de l'opération.  
  
 Le volet gauche répertorie également les fichiers de configuration du client. Double-cliquez sur l'un des éléments pour afficher le contenu du fichier correspondant dans une nouvelle page à onglets, dans le volet droit.  
  
### <a name="entering-test-parameters"></a>Saisie de paramètres de test  
 Pour afficher les paramètres de test, double-cliquez sur une opération afin de l'ouvrir dans le volet droit. Les paramètres sont affichés dans **mise en forme** vue par défaut, et vous pouvez entrer des valeurs arbitraires pour les paramètres tester le service.  
  
 Pour afficher le fichier XML du message, cliquez sur **XML**. Pour les envoyer au service, cliquez sur **Invoke**.  
  
 Pour un paramètre de jeu de données, cliquez sur le **...** situé en regard **modifier...** pour le modifier dans une nouvelle fenêtre affichant le DataGrid. Notez l’apparence de la **copier le DataSet** et **coller le DataSet** boutons. Si le schéma de l'objet DataSet est inconnu lors de la première modification, DataGrid est vide. Vous devez coller un objet DataSet avec le même schéma dans l'objet actuel de DataGrid. (Notez que vous devez copier le schéma à partir d'un autre endroit avant l'opération de collage.) Vous pouvez également copier un objet de jeu de données pour une utilisation ultérieure en cliquant sur le **copier le DataSet** bouton.  
  
 La réponse du service apparaît au-dessous des paramètres de test.  
  
> [!NOTE]
>  Si la valeur de retour attendue est une chaîne, le résultat est affiché sous la forme d'une chaîne entre guillemet même si l'entrée fournie n'est pas incluse entre guillemet.  
  
 Si vous avez spécifié une opération particulière comme étant unidirectionnelle lorsque vous avez créé le contrat pour le service, aucune réponse de service n'est affichée. Dès que le message est placé en file d'attente en vue de sa transmission, une boîte de dialogue apparaît pour vous notifier que le message a été envoyé avec succès.  
  
### <a name="session-support"></a>Prise en charge des sessions  
 Le **démarrer un nouveau proxy** case à cocher dans l’onglet d’une opération service vous permet d’activer/désactiver la prise en charge de la session. Elle est désactivée par défaut.  
  
 Lorsque vous entrez des paramètres de test pour une opération spécifique (ou une autre opération dans le même point de terminaison de service) et cliquez sur **Invoke** plusieurs fois avec la case à cocher, ces opérations partagent un proxy et l’état du service est rendu persistant entre plusieurs opérations.  
  
 Si le **démarrer un nouveau proxy** case à cocher est activée, un nouveau proxy est démarré chaque **Invoke**, le scénario de session précédente est terminé, et l’état du service est réinitialisé.  
  
### <a name="editing-client-configuration"></a>Modification de la configuration client  
 Le volet gauche de la fenêtre principale du Client Test WCF répertorie les fichiers de configuration de client. Double-cliquez sur l'un des éléments pour afficher le contenu du fichier dans le volet droit.  
  
#### <a name="edit-with-service-configuration-editor"></a>Modifier avec l'Éditeur de configuration de service  
 Avec le bouton droit **fichier de configuration** dans le volet gauche, puis sélectionnez le menu contextuel **modifier avec SvcConfigEditor**. L'Éditeur de configuration de service est lancé avec le contenu de la configuration client. Vous pouvez modifier la configuration et l'enregistrer dans l'outil.  
  
 Après avoir enregistré le fichier dans l’éditeur de Configuration de Service, le Client Test WCF affiche un message d’avertissement pour vous informer que le fichier a été modifié en dehors et vous demande si vous souhaitez recharger.  
  
 Si vous sélectionnez **Oui**, le contenu de la configuration de l’onglet « Client.dll.config » reflète les modifications apportées dans l’éditeur.  
  
 Si vous sélectionnez **non**, le contenu de la configuration de l’onglet « Client.dll.config » reste inchangé et le contenu modifié est automatiquement enregistré dans le fichier source.  
  
#### <a name="restore-to-default-configuration"></a>Restaurer la configuration par défaut  
 Si vous souhaitez annuler toutes les modifications et restaurer la configuration de client par défaut, avec le bouton droit **fichier de configuration** dans le volet gauche, puis sélectionnez le menu contextuel **restaurer la configuration de la valeur par défaut**. La valeur de la configuration par défaut est chargée et contenu dans l’onglet de « Client.dll.config » est restauré.  
  
#### <a name="validate-changes"></a>Valider des modifications  
 Lorsque les modifications enregistrées sont chargées dans le Client Test WCF, la configuration de validité est vérifiée par rapport à schéma WCF. Si les erreurs sont rencontrées, une boîte de dialogue est affichée pour afficher des détails d'erreur.  
  
 Pendant la génération de proxy, une compilation binaire ou l’appel de service, les éléments de menu qui prennent en charge la modification (autrement dit, « Modifier... », « restaurer... » et ainsi de suite) sont désactivées. Appel de service est également désactivé lors de la configuration de la mise à jour de chargement pour le Client Test WCF.  
  
#### <a name="persist-client-configuration"></a>Rendre la configuration client persistante  
 Le **outils**->**Options**->**Configuration du Client** onglet contient un **toujours régénérer la configuration lors de lancement Services** option, qui est activée par défaut. Cette option spécifie que chaque fois que le Client Test WCF se charge d’un service, il régénère un fichier de configuration basé sur le dernier contrat de service et les fichiers App.config du service.  
  
 Si vous avez modifié la configuration du client pour votre service WCF et que vous souhaitez toujours utiliser ce fichier mis à jour pour déboguer votre service, vous pouvez désactiver le **régénérer** option. En procédant ainsi, même lorsque vous mettez à jour le service et rouvrez le Client Test WCF, le fichier Client.dll.config est celui qui que vous mis à jour précédemment au lieu de régénéré selon le service de mise à jour.  
  
 Toutefois, il peut s'avérer nécessaire de modifier le fichier de configuration afin qu'il soit conforme au proxy régénéré. Si le proxy régénéré et fichier de configuration ne correspondent pas en raison de la mise à jour d'un service, des erreurs se produiront à l'appel du service.  
  
> [!CAUTION]
>  Si vous avez modifié le fichier de configuration client et décidez de le réutiliser ultérieurement, vous le trouverez à l'emplacement suivant :  
>   
>  \Documents and Settings\\[compte d’utilisateur] \My Documents\Test Client Projects.  
>   
>  Toutes les informations d'identification mises à jour stockées dans le fichier de configuration client sont protégées par la Liste de contrôle d'Accès (ACL) de ce dossier.  
  
### <a name="adding-removing-and-refreshing-services"></a>Ajout, suppression et actualisation des services  
  
#### <a name="add-service"></a>Ajouter un service  
 Cliquez sur **fichier**->**ajouter un Service** pour ajouter un service au Client Test WCF. Vous devez alors taper l'URI (adresse de point de terminaison) du service à ajouter. L'adresse du service peut être une adresse mex ou WSDL.  
  
 Vous trouverez également une liste de points de terminaison de services ajoutés récemment 10 dans le **Services récents** sous-menu. Si vous sélectionnez un d’eux, le service spécifié est ajouté au Client Test WCF.  
  
 Vous pouvez également cliquer sur la racine de l’arborescence de services **Mes projets de Service**, puis sélectionnez **ajouter un Service** pour obtenir le même résultat.  
  
 Pendant la génération d'un proxy, une compilation binaire ou l'appel d'un service, les éléments de menu qui prennent en charge l'ajout d'un service sont désactivés. L'appel de service est également désactivé.  
  
#### <a name="remove-service"></a>Supprimer un service  
 Avec le bouton droit de la racine du service du service à supprimer, puis sélectionnez **supprimer le Service** pour supprimer un service à partir du Client Test WCF.  
  
 Pendant la génération d'un proxy, une compilation binaire ou l'appel d'un service, les éléments de menu qui prennent en charge la suppression d'un service sont désactivés. L'appel de service est également désactivé.  
  
#### <a name="refresh-service"></a>Actualiser un service  
 Si une modification est apportée au service pendant que le Client Test WCF est en cours d’exécution et que vous souhaitez vous assurer que l’implémentation de Client Test WCF pour ce service est à jour, cliquez sur la racine du service du service et sélectionnez **actualiser le Service**. Notez qu'après avoir actualisé un service, son état est réinitialisé.  
  
 Pendant la génération d'un proxy, une compilation binaire ou l'appel d'un service, les éléments de menu qui prennent en charge l'actualisation d'un service sont désactivés. L'appel de service est également désactivé.  
  
## <a name="location-of-files-generated-by-the-test-client"></a>Emplacement des fichiers générés par le client test  
 Par défaut, le Client Test WCF stocke généré les fichiers de code et la configuration client dans le dossier « %appdata%\Local\temp\Test Client Projects ». Ce dossier est supprimé lorsque l’utilisateur quitte le Client Test WCF. Si un fichier de configuration est modifié dans le Client Test WCF et le **toujours régénérer la configuration au démarrage des Services** option est désactivée, le fichier modifié est copié dans le dossier « CachedConfig » sous « Mes Documents\Test Client Projects » avec un fichier mappage de XML (métadonnées-adresse-à-nom de fichier) en tant qu’index.  
  
 Vous pouvez également démarrer le Client Test WCF dans une ligne de commande, utilisez le `/ProjectPath` passer pour spécifier un nouveau chemin d’accès souhaité pour le stockage des fichiers générés, ou utiliser le `/RestoreProjectPath` commutateur pour restaurer l’emplacement par défaut. La syntaxe est la suivante :  
  
 `wcfTestClient.exe /ProjectPath [desired location]`  
  
 Exécution de cette commande n’ouvre pas le Client Test WCF. Seul l’emplacement du dossier est changé. Vous pouvez exécuter cette commande si le Client Test WCF est en cours d’exécution ou non. Le nouvel emplacement est appliqué lorsque le Client Test WCF est redémarré. Les informations d’emplacement peuvent être enregistrées dans le Registre ou dans le fichier WcfTestClient.exe.option, dans le dossier « %appdata%\Local\temp\Test Client Projects ».  
  
## <a name="features-supported-by-wcf-test-client"></a>Fonctionnalités prises en charge par le client test WCF  
 Voici une liste des fonctionnalités prises en charge par le Client Test WCF :  
  
- Appel de service : Message unidirectionnel et demande/réponse.  
  
- Liaisons : toutes les liaisons prises en charge par Svcutil.exe.  
  
- Contrôle de session.  
  
- Contrat de message.  
  
- Sérialisation XML.  
  
 Voici une liste des fonctionnalités non prises en charge par le Client Test WCF :  
  
- Types : <xref:System.IO.Stream>, <xref:System.ServiceModel.Channels.Message>, <xref:System.Xml.XmlElement>, <xref:System.Xml.XmlAttribute>, <xref:System.Xml.XmlNode>, types qui implémentent l'interface <xref:System.Xml.Serialization.IXmlSerializable>, y compris l'attribut <xref:System.Xml.Serialization.XmlSchemaProviderAttribute> associé et les types <xref:System.Xml.Linq.XDocument> et <xref:System.Xml.Linq.XElement>, ainsi que le type ADO.NET <xref:System.Data.DataTable>.  
  
- Contrat duplex.  
  
- Transaction.  
  
- Sécurité : CardSpace, certificat et nom d’utilisateur/mot de passe.  
  
- Liaisons : WSFederationbinding, les liaisons de contexte et la liaison Https, WebHttpbinding (prise en charge Json réponse message).  
  
## <a name="closing-wcf-test-client"></a>Fermeture du client test WCF  
 Vous pouvez fermer le Client Test WCF de plusieurs manières :  
  
- Sur le **fichier** menu, cliquez sur **Exit**. Vous pouvez également, dans la fenêtre principale du Client Test WCF, cliquez sur **fermer**. À la fois de ces actions également arrêté hôte de Service WCF et arrêter le processus de débogage de Visual Studio si le Client Test WCF a été lancé par Visual Studio.  
  
- Cliquez sur le **hôte de Service WCF** icône dans la zone de notification, puis cliquez sur **Exit.** Cela arrête d’hôte de Service WCF et le Client Test WCF et arrête le processus de débogage de Visual Studio.  
  
## <a name="see-also"></a>Voir aussi

- [WCF Service Host (WcfSvcHost.exe)](../../../docs/framework/wcf/wcf-service-host-wcfsvchost-exe.md)
