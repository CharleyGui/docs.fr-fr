---
title: Outil Éditeur de configuration (SvcConfigEditor.exe)
description: Découvrez comment gérer les paramètres des liaisons, des comportements, des services et des diagnostics WCF à l’aide de l’éditeur de configuration de service WCF.
ms.date: 03/30/2017
helpviewer_keywords:
- configuration files, creating
- configuration files
- Configuration file
- configuration file schema
ms.assetid: 2db21a57-5f64-426f-89df-fb0dc2d2def5
ms.openlocfilehash: 258437ff616b969d40feabbfff364ad2cc6b25bc
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/23/2020
ms.locfileid: "85247647"
---
# <a name="configuration-editor-tool-svcconfigeditorexe"></a>Outil Éditeur de configuration (SvcConfigEditor.exe)

L'Éditeur de configuration de service (SvcConfigEditor.exe) Windows Communication Fondation (WCF) permet aux administrateurs et aux développeurs de créer et de modifier les paramètres de configuration pour les services WCF à l'aide d'une interface utilisateur graphique (GUI). Grâce à cet outil, vous pouvez gérer les paramètres des liaisons, des comportements, des services et des diagnostics WCF sans modifier directement les fichiers de configuration XML.

L’Éditeur de configuration de service se trouve dans le dossier C:\Program Files\Microsoft SDKs\Windows\v6.0\Bin.

## <a name="the-wcf-configuration-editor"></a>Éditeur de configuration WCF

L'Éditeur de configuration de service est fourni avec un Assistant qui vous guide à travers toutes les étapes de configuration d'un service ou d'un client WCF. Il est vivement recommandé d'utiliser l'Assistant au lieu d'utiliser directement l'éditeur.

Si vous avez déjà quelques fichiers de configuration conformes au schéma System.Configuration standard, vous pouvez gérer des paramètres spécifiques pour les liaisons, comportements, services et diagnostics avec l’interface utilisateur. L'Éditeur de configuration de service permet de gérer les paramètres des fichiers de configuration WCF existants, ainsi que les fichiers exécutables, les services COM+ et les services hébergés sur le Web. Lorsque vous ouvrez un service hébergé sur le Web au moyen de l'Éditeur de configuration de service, vous accédez à la propre configuration du service et aux sections de configurations héritées des nœuds de niveau supérieur.

Les paramètres de configuration WCF figurent dans la section `<system.serviceModel>` du fichier de configuration ; par conséquent, l'éditeur fonctionne exclusivement sur le contenu de cet élément et n'accède pas à d'autres éléments du même fichier. Vous pouvez naviguer directement jusqu'aux fichiers de configuration existants ou vous pouvez sélectionner un assembly qui contient un service, un répertoire virtuel ou un service COM+. L'éditeur charge le fichier de configuration pour ce service particulier et autorise l'utilisateur à ajouter des nouveaux éléments ou à modifier des éléments existants imbriqués dans la section `<system.serviceModel>` du fichier de configuration.

L'éditeur prend en charge IntelliSense et applique la conformité de schéma. Le résultat est conformer au schéma du fichier de configuration et possède des valeurs de données correctes syntaxiquement. Toutefois, l'éditeur ne garantit pas que le fichier de configuration soit correct sur un plan sémantique. En d'autres termes, l'éditeur ne garantit pas que le fichier de configuration puisse fonctionner avec le service qu'il configure.

> [!CAUTION]
> L'éditeur ne peut pas supprimer un élément de configuration du fichier de configuration une fois que vous avez modifié l'élément. Par exemple, si vous utilisez l'éditeur pour affecter au nom de point de terminaison une chaîne non vide et l'enregistrer, le contenu du fichier de configuration est le suivant, comme illustré dans l'exemple suivant.
>
> `<endpoint binding="basicHttpBinding" name="somename" />`
>
> Si vous tentez de supprimer le nom en lui affectant une chaîne vide et que vous enregistrez le fichier, le fichier de configuration contient toujours l'attribut `name`, comme illustré dans l'exemple suivant.
>
> `<endpoint binding="basicHttpBinding" name="" />`
>
> Pour supprimer l'attribut, vous devez modifier manuellement l'élément à l'aide d'un autre éditeur de texte.
>
> Vous devez être particulièrement prudent avec ce problème lorsque vous utilisez l'élément `issueToken` du comportement de point de terminaison `clientCredential`. De façon spécifique, l'attribut `address` de son sous-élément `localIssuer` ne doit pas être une chaîne vide. Si vous avez modifié l'attribut `address` à l'aide de l'Éditeur de configuration et que vous souhaitez le supprimer complètement, vous devez pour cela utiliser un autre outil que l'Éditeur. Sinon, l'attribut contient une chaîne vide et votre application lève une exception.

## <a name="using-the-configuration-editor"></a>Utilisation de l'Éditeur de configuration

L'Éditeur de configuration de service se trouve à l'emplacement d'installation du Kit de développement logiciel (SDK) Windows suivant :

C:\Program Files\Microsoft SDKs\Windows\v6.0\Bin\SvcConfigEditor.exe

Après avoir lancé l’éditeur de configuration de service, vous pouvez utiliser le menu **fichier/ouvrir** pour rechercher le service ou l’assembly que vous souhaitez gérer. Vous pouvez ouvrir des fichiers de configuration directement, rechercher des services WCF/COM + et ouvrir des fichiers de configuration pour des services hébergés par le Web.

L'interface utilisateur de l'Éditeur de configuration de service est divisée dans les zones suivantes :

- Volet (arborescence) qui affiche les éléments de configuration sous forme d’arborescence à gauche. Vous pouvez exécuter des opérations dans l'arbre en cliquant avec le bouton droit sur les nœuds.

- Volet de tâches qui présente les tâches courantes applicables aux éléments actuels dans la partie inférieure gauche de la fenêtre.

- Volet Détail qui affiche les paramètres détaillés du nœud de configuration sélectionné dans l’arborescence à droite.

### <a name="opening-a-configuration-file"></a>Ouverture d'un fichier de configuration

1. Démarrez l’éditeur de configuration de service à l’aide d’une fenêtre de commande pour accéder à votre emplacement d’installation WCF, puis tapez `SvcConfigEditor.exe` .

2. Dans le menu **fichier** , sélectionnez **ouvrir** , puis cliquez sur le type de fichier que vous souhaitez gérer.

3. Dans la boîte de dialogue **ouvrir** , accédez au fichier spécifique que vous souhaitez gérer, puis double-cliquez dessus.

La visionneuse suit automatiquement le chemin d’accès de fusion de la configuration et crée une vue de la configuration fusionnée. Par exemple, la configuration réelle d’un service non hébergé est une combinaison de Machine.config et App.config. Toutes les modifications sont appliquées au fichier actif dans SvcConfigEditor. Si vous souhaitez modifier un fichier spécifique dans le chemin d’accès de fusion de la configuration, vous devez l’ouvrir directement.

> [!NOTE]
> L'Éditeur de configuration recharge le fichier de configuration actuellement ouvert lorsque ce dernier a été modifié à l'extérieur de l'Éditeur. Lorsque cela se produit, toutes les modifications non enregistrées dans l'Éditeur sont perdues. Si les rechargements sont fréquents, la cause la plus probable est l‘accès constant d‘un service au fichier de configuration (par exemple, un logiciel antivirus exécuté en arrière-plan). Pour y remédier, vérifiez que l'éditeur de configuration est l'unique processus autorisé à accéder au fichier lorsque celui-ci est ouvert.

### <a name="services"></a>Services

Le nœud **services** affiche tous les services actuellement attribués dans le fichier de configuration. Chaque sous-nœud de l’arborescence correspond à un sous-élément de l' `services` élément <> dans le fichier de configuration.

Lorsque vous cliquez sur le nœud **services** , vous pouvez afficher ou exécuter des tâches dans la page Résumé du service dans le volet d' **informations** .

#### <a name="creating-a-new-service-configuration"></a>Création d'une configuration de service

Vous pouvez créer une configuration de service de l'une des manières suivantes :

- À l’aide d’un Assistant : cliquez sur le lien **créer un nouveau service...** dans le volet de tâches ou la page Résumé pour lancer l’Assistant. Vous pouvez également le faire dans le menu **fichier** -> **Ajouter un nouvel élément**.

- Créer manuellement : vous pouvez cliquer avec le bouton droit sur le nœud **services** et choisir **nouveau service**.

#### <a name="creating-a-new-service-endpoint-configuration"></a>Création d'une configuration de point de terminaison de service

Vous pouvez créer une nouvelle configuration de point de terminaison de service de l'une des manières suivantes :

- Créer à l’aide d’un Assistant : cliquez sur le lien **créer un point de terminaison de service...** dans le volet de tâches ou la page Résumé pour lancer l’Assistant. Vous pouvez également le faire dans le menu **fichier** -> **Ajouter un nouvel élément**.

- Créer manuellement : une fois que vous avez créé un service, vous pouvez cliquer avec le bouton droit sur le nœud **points de terminaison** et choisir «**nouveau point de terminaison de service**».

#### <a name="editing-a-service-configuration"></a>Modification d'une configuration de service

1. Cliquez sur un nœud de **service** .

2. Modifiez les paramètres dans les grilles de propriété.

#### <a name="editing-a-service-endpoint-configuration"></a>Modification d'une configuration de points de terminaison de service

1. Cliquez sur un nœud de **point de terminaison de service** .

2. Modifiez les paramètres dans les grilles de propriété.

#### <a name="adding-a-base-address"></a>Ajout d'une adresse de base

1. Cliquez sur le nœud **hôte** .

2. Cliquez sur le bouton **Nouveau…** dans la section **adresses de base** .

3. Tapez l'URI de l'adresse de base dans la boîte de dialogue.

4. Cliquez sur **OK**.

> [!NOTE]
> Vous ne pouvez pas modifier la valeur de [\<baseAddressPrefixFilters>](../configure-apps/file-schema/wcf/baseaddressprefixfilters.md) dans cet outil. Pour ajouter ou modifier cet élément, vous devez utiliser un éditeur de texte ou Visual Studio.

### <a name="client"></a>Client

Le nœud **client** affiche tous les points de terminaison du client dans le fichier de configuration. Chaque sous-nœud de l’arborescence correspond à un sous-élément de l' `client` élément <> dans le fichier de configuration.

Lorsque vous cliquez sur le nœud **client** , vous pouvez afficher ou exécuter des tâches dans la **page Résumé** du client dans le **volet d’informations**.

#### <a name="creating-a-new-client-endpoint-configuration"></a>Création d'une configuration de point de terminaison client

Vous pouvez créer une configuration de point de terminaison client de l'une des manières suivantes :

- Créer à l’aide d’un Assistant : cliquez sur le lien **créer un nouveau client...** dans le **volet de tâches** en bas à gauche de la fenêtre, ou **page Résumé** pour lancer l’Assistant. Vous pouvez également le faire dans le menu **fichier** -> **Ajouter un nouvel élément**. L'Assistant vous invite à désigner l'emplacement de la configuration du service, à partir duquel la configuration cliente est générée. Vous pouvez alors choisir le point de terminaison de service avec lequel établir une connexion.

- Créez manuellement : cliquez avec le bouton droit sur le nœud **points de terminaison** sous **client**, puis choisissez **nouveau point de terminaison client**.

#### <a name="editing-a-client-endpoint-configuration"></a>Modification d'une configuration de point de terminaison client

1. Cliquez sur un nœud de **point de terminaison client** .

2. Modifiez les paramètres dans les grilles de propriété.

### <a name="standard-endpoint"></a>Point de terminaison standard

Les points de terminaison standard sont des points de terminaison spécialisés possédant une ou plusieurs parties de l’adresse, contrat et liaison définies sur les valeurs par défaut.

Ces paramètres de configuration sont stockés dans le nœud de **point de terminaison standard** . Le nœud **point de terminaison standard** affiche tous les paramètres de point de terminaison standard dans le fichier de configuration. Chaque sous-nœud de l’arborescence correspond à un sous-élément de l' `<standardEndpoints>` élément dans le fichier de configuration.

Lorsque vous cliquez sur le nœud **point de terminaison standard** , vous pouvez afficher ou exécuter des tâches dans la **page Résumé** du point de terminaison standard du **volet détail**.

#### <a name="creating-a-new-standard-endpoint-configuration"></a>Création d'une configuration de point de terminaison standard

Vous pouvez créer une configuration de point de terminaison standard de l'une des manières suivantes :

- Cliquez avec le bouton droit sur le nœud **point de terminaison standard** et sélectionnez **nouvelle configuration de point de terminaison standard...** Sélectionnez le type de liaison dans la boîte de dialogue, puis cliquez sur **OK**.

- Sélectionnez le nœud **point de terminaison standard** et cliquez sur **nouvelle configuration de point de terminaison standard...** dans le **volet de tâches** dans la partie inférieure gauche de la fenêtre.

La boîte de dialogue **création d’un point de terminaison standard** affiche et répertorie tous les types de points de terminaison standard inscrits.

#### <a name="viewing-and-editing-a-standard-endpoint-configuration"></a>Affichage et modification d'une configuration de point de terminaison standard

Vous pouvez ouvrir une configuration de point de terminaison standard en vue de l'afficher et de la modifier des façons suivantes :

- Cliquez pour développer le nœud **point de terminaison standard** et cliquez sur le sous-nœud de point de terminaison respectif.

- Cliquez sur le nœud **point de terminaison standard** et cliquez sur le point de terminaison respectif dans le volet Détails.

Les attributs correspondant au point de terminaison s'affichent dans le volet droit pour modification.

#### <a name="deleting-a-standard-endpoint-configuration"></a>Suppression d'une configuration de point de terminaison standard

Vous pouvez supprimer une configuration de point de terminaison standard de l'une des manières suivantes :

- Cliquez pour développer le nœud **point de terminaison standard** et cliquez avec le bouton droit sur le sous-nœud de point de terminaison respectif. Utilisez la commande de contexte **Supprimer la configuration de point de terminaison standard** pour supprimer le point de terminaison.

- Cliquez sur le nœud **point de terminaison standard** . Dans le volet des **tâches** , cliquez sur **Supprimer la configuration de point de terminaison standard**.

Si le point de terminaison standard est utilisé, un message d’avertissement s’affiche lorsque vous tentez de le supprimer : **le point de terminaison standard est en cours d’utilisation. Si vous la supprimez maintenant, veillez à supprimer toutes ses références dans d’autres parties de la configuration (par exemple, dans le point de terminaison de service ou le point de terminaison client). Dans le cas contraire, la configuration ne sera pas valide et ne pourra pas être ouverte la prochaine fois. Voulez-vous vraiment supprimer le point de terminaison standard ?»**

### <a name="binding"></a>Liaison

Les configurations de liaison sont utilisées pour configurer des liaisons sur les points de terminaison. Ces paramètres de configuration sont stockés dans le nœud de **liaison** . Les points de terminaison référencent les configurations de liaison par nom et plusieurs points de terminaison peuvent référencer une configuration de liaison unique.

Le nœud **liaisons** affiche tous les paramètres de liaison dans le fichier de configuration. Chaque sous-nœud de l’arborescence correspond à un sous-élément de l' `bindings` élément <> dans le fichier de configuration.

Lorsque vous cliquez sur le nœud **liaisons** , vous pouvez afficher ou exécuter des tâches dans la **page Résumé** des liaisons du **volet d’informations**.

#### <a name="creating-a-new-binding-configuration"></a>Création d’une configuration de liaison

Vous pouvez créer une configuration de liaison de l’une des manières suivantes :

- Cliquez avec le bouton droit sur le nœud **liaisons** et sélectionnez **nouvelle configuration de liaison**... Sélectionnez le type de liaison dans la boîte de dialogue, puis cliquez sur **OK**.

- Sélectionnez le nœud **liaisons** et cliquez sur **nouvelle configuration de liaison**... dans le **volet de tâches** dans la partie inférieure gauche de la fenêtre.

- Dans la page Résumé du service ou du client, cliquez sur **cliquez pour créer** dans le champ **configuration de liaison** pour créer une configuration de liaison pour le point de terminaison correspondant.

#### <a name="adding-binding-element-extensions-to-a-custom-binding"></a>Ajout d'extensions d'élément de liaison à une liaison personnalisée

1. Sélectionnez la liaison à laquelle vous souhaitez ajouter une extension d'élément.

2. Cliquez sur **Add**.

3. Dans la liste d'extensions disponibles, sélectionnez l'extension d'élément de liaison que vous souhaitez ajouter. Pour sélectionner plusieurs éléments, appuyez simultanément sur la touche CTRL.

4. Cliquez sur **Add**.

#### <a name="adjusting-the-extension-position-in-a-custom-binding"></a>Ajustement de la position d’extensions dans une liaison personnalisée

Une liaison personnalisée est une collection d’éléments de liaison qui forment une pile. Chaque élément de liaison sur la pile possède ses propres paramètres de configuration. L’ordre des extensions d’élément de liaison dans une liaison personnalisée indique leur position dans la pile. Les éléments en haut de la pile sont appliqués en premier. Pour modifier l'ordre :

1. Sélectionnez le nœud de liaison personnalisé.

2. Sélectionnez un élément d’extension de liaison dans la section position d’extension de l' **élément de liaison** .

3. Utilisez le bouton vers le haut ou **vers** le **haut** sur le côté gauche de la liste pour modifier la position de l’élément sélectionné.

#### <a name="editing-the-configuration-of-binding-element-extensions-in-a-custom-binding"></a>Modification de la configuration d’extensions d’élément de liaison dans une liaison personnalisée

1. Sélectionnez le nœud de liaison dans l’arbre.

2. Sélectionnez la liaison personnalisée qui contient l'élément que vous souhaitez modifier.

3. Sélectionnez l'extension d'élément de liaison que vous souhaitez modifier. Les paramètres de l'élément apparaissent dans le volet droit où ils peuvent être modifiés.

### <a name="diagnostics"></a>Diagnostics

Le nœud **Diagnostics** affiche tous les paramètres de diagnostic dans le fichier de configuration. Elle vous permet d’activer ou de désactiver les compteurs de performance, d’activer ou de désactiver les Windows Management Instrumentation (WMI), de configurer le suivi WCF et de configurer l’enregistrement des messages WCF. Les paramètres du nœud **Diagnostics** correspondent à la section <`system.diagnostics`> et à la `<diagnostics>` section de `<system.serviceModel>` dans le fichier de configuration.

Lorsque vous cliquez sur le nœud **Diagnostics** , vous pouvez afficher ou exécuter des tâches dans la **page Résumé** des diagnostics du **volet détail**.

#### <a name="configuring-performance-counters-and-wmi"></a>Configuration des compteurs de performance et de WMI

1. Cliquez sur le nœud **Diagnostics** .

2. Cliquez sur **activer/désactiver les compteurs de performances**. Le compteur de performance peut avoir trois états : Off (valeur par défaut), ServiceOnly et All. Il est possible de basculer entre les trois états en cliquant sur le lien.

#### <a name="configuring-wmi-provider"></a>Configuration d'un fournisseur WMI

1. Cliquez sur le nœud **Diagnostics** .

2. Pour activer le fournisseur WMI, cliquez sur le lien **activer le fournisseur WMI** .

#### <a name="enabling-wcf-tracing"></a>Activation du suivi WCF

Vous pouvez créer un fichier de suivi WCF avec des propriétés standard ou configurer un fichier de suivi personnalisé.

1. Cliquez sur le nœud **Diagnostics** .

2. Cliquez sur **activer le suivi**.

3. Cliquez sur le lien **niveau de suivi** pour ajuster le niveau de suivi. Six niveaux de suivi sont disponibles : Fermé, Critique, Erreur, Avertissement, Information et Commentaires. L’option **suivi d’activité** et **propager l’activité** vous permet d’utiliser la fonctionnalité de suivi d’activité WCF.

4. Cliquez sur le nom de l'écouteur de suivi pour spécifier le fichier et les options de suivi.

#### <a name="enabling-wcf-logging"></a>Activation de la journalisation WCF

Vous pouvez créer un fichier de suivi WCF avec des propriétés standard ou configurer un fichier de suivi personnalisé.

1. Cliquez sur le nœud **Diagnostics** .

2. Cliquez sur **activer la journalisation des messages**.

3. Cliquez sur le lien **niveau de journalisation** pour ajuster le niveau de journalisation. Il existe trois niveaux de journal : Messages malformés, Service et Transport.

4. Cliquez sur le nom de l'écouteur pour spécifier le fichier journal et les options de suivi.

> [!NOTE]
> Si vous souhaitez que les journaux de suivi et de messages soient vidés automatiquement lorsque votre application est fermée, activez l’option de **vidage automatique** .

La **page Résumé** des **Diagnostics** vous permet d’accomplir les tâches les plus courantes de la configuration des Diagnostics. Toutefois, si vous souhaitez modifier manuellement les paramètres des écouteurs et des sources, vous devez développer le nœud **Diagnostics** et modifier les paramètres dans le nœud **enregistrement des messages**, **écouteurs** et **sources** .

#### <a name="enabling-wcf-custom-tracing-or-message-logging"></a>Activation de la journalisation des messages ou le suivi personnalisé de WCF

1. Cliquez sur le nœud **Diagnostics** , puis développez-le.

2. Cliquez avec le bouton droit sur le nœud **écouteurs** et sélectionnez **nouvel écouteur**.

3. Tapez le nom du fichier de trace dans le champ **InitData** . Vous pouvez cliquer sur le « ... » bouton pour accéder à un chemin d’accès.

4. Si vous cliquez sur la ligne **TypeName** , un « ... » s’affiche. bouton. Cliquez sur ce bouton pour ouvrir l' **Explorateur de types d’écouteur de suivi**, que vous pouvez utiliser pour rechercher des écouteurs de suivi préconfigurés qui sont déjà installés.

5. Notez la section **source** . Cliquez sur **Ajouter** dans cette section pour ouvrir une boîte de dialogue avec un menu déroulant qui répertorie les sources de suivi disponibles. Sélectionnez une source de suivi, puis cliquez sur **OK**.

6. Pour modifier les paramètres d’enregistrement des messages, cliquez sur le nœud **enregistrement des messages** . Vous pouvez modifier les paramètres dans la grille des propriétés.

### <a name="advanced"></a>Avancé

#### <a name="behaviors"></a>comportements

Le nœud **comportements** affiche les comportements qui sont actuellement définis dans le fichier de configuration.

Les configurations de comportement sont utilisées pour configurer des comportements de points de terminaison et de services. Ces paramètres de configuration sont stockés dans le nœud **avancé** sous **comportements de service** et comportements de **point de terminaison**. Les comportements de service sont utilisés par les services, alors que les comportements de point de terminaison par les points de terminaison.

Les comportements représentent un ensemble d’éléments d’extension qui forment une pile. L'élément en haut de la pile est appliqué en premier. Chaque élément d’extension peut avoir sa propre configuration.

##### <a name="creating-a-new-behavior-configuration"></a>Création d'une configuration de comportement

Vous pouvez créer une nouvelle configuration de comportement de l'une des manières suivantes :

- Cliquez avec le bouton droit sur l’un des nœuds de comportement et sélectionnez «**nouvelle configuration de comportement...**

- Sélectionnez l’un des nœuds de comportement et cliquez sur la **nouvelle configuration de comportement**... dans le **volet de tâches** dans la partie inférieure gauche de la fenêtre.

##### <a name="adding-behavior-element-extensions-to-a-behavior"></a>Ajout d’extensions d’éléments de comportement à un comportement

1. Sélectionnez l'un des nœuds de comportement.

2. Sélectionnez le comportement que vous souhaitez modifier.

3. Cliquez sur **Add**.

4. Dans la liste d’extensions disponibles, sélectionnez l’extension d’élément de comportement que vous souhaitez ajouter.

5. Cliquez sur **Add**.

##### <a name="adjusting-the-extension-position-in-a-behavior"></a>Ajustement de la position d’extension dans un comportement

Les comportements sont des collections d'élément qui forment une pile. Chaque élément sur la pile possède sa propre configuration. L’ordre des extensions d’éléments de comportement dans un comportement personnalisé indique leur position dans la pile. Les éléments en haut de la pile sont appliqués en premier. Pour modifier l'ordre :

1. Sélectionnez l'un des nœuds de comportement.

2. Sélectionnez le comportement que vous souhaitez modifier.

3. Sélectionnez un élément d’extension de comportement dans la section position d’extension de l' **élément de comportement** .

4. Utilisez le bouton vers le haut ou **vers** le **haut** sur le côté gauche de la liste pour modifier la position de l’élément sélectionné.

##### <a name="editing-the-configuration-of-behavior-element-extensions"></a>Modification la configuration des extensions d’élément de comportement

1. Sélectionnez l’un des nœuds de comportement dans l’arbre.

2. Sélectionnez le comportement qui contient l'élément que vous souhaitez modifier.

3. Sélectionnez l'extension d'élément de comportement que vous souhaitez modifier. Les paramètres de l'élément apparaissent dans le volet droit où ils peuvent être modifiés.

#### <a name="protocolmapping"></a>ProtocolMapping

Cette section permet de configurer des types de liaison par défaut pour différents protocoles (tels que HTTP, TCP, MSMQ ou net.pipe) en appliquant un mappage défini entre les schémas d'adresse de protocole et les liaisons possibles. Vous pouvez également ajouter de nouveaux mappages à d'autres protocoles.

#### <a name="extensions"></a>Extensions

Les nouvelles extensions de liaison, les extensions d’élément de liaison, les extensions de point de terminaison standard et les extensions de comportement peuvent être enregistrées pour une utilisation dans la configuration WCF. Les extensions sont des paires de nom/type. Le nom définit le nom de l’extension dans la configuration, alors que le type implémente l’extension. Il existe quatre types d’extension :

- Les extensions de liaison définissent un type de liaison entier. Exemple : `basicHttpBinding`.

- Les extensions d'élément de liaison définissent un élément d'une liaison. Exemple : `textMessageEncoding`.

- Les extensions de point de terminaison standard définissent un point de terminaison standard entier. Exemple : `discoveryEndpoint`.

- Les extensions d’élément de comportement définissent un élément d’un comportement. Exemple : `clientVia`.

 Les extensions inscrites dans la configuration peuvent être utilisées comme tout autre composant WCF du même type.

##### <a name="adding-a-new-extension"></a>Ajout d'une nouvelle extension

Sélectionnez l’un des nœuds d’extension parmi les nœuds avancés.

1. Cliquez sur **Nouveau**.

2. Entrez un nom et un type.

3. Cliquez sur **OK**.

4. L’extension apparaît maintenant dans l’éditeur à l’endroit approprié. Par exemple, si vous ajoutez une extension d’élément de comportement, elle apparaît dans la liste des extensions disponibles.

#### <a name="hosting-environment"></a>Environnement d'hébergement

Cette section permet de définir des paramètres d'instanciation pour l'environnement d'hébergement de service.

### <a name="creating-a-configuration-file-using-the-wizard"></a>Création d'un fichier de configuration à l'aide de l'Assistant

Pour créer un fichier de configuration, vous pouvez notamment utiliser l'Assistant Nouvel élément de service. L’Assistant recherche les types de service installés et d’autres éléments compatibles avec WCF sur l’ordinateur, y compris les répertoires virtuels hébergés sur le Web et les COM+, et les charge afin de simplifier la création de la configuration.

#### <a name="creating-a-configuration-file"></a>Création d'un fichier de configuration

1. Démarrez l’éditeur de configuration de service à l’aide d’une fenêtre de commande pour accéder à votre emplacement d’installation WCF, puis tapez `SvcConfigEditor.exe` .

2. Dans le menu **fichier** , sélectionnez **ouvrir** , puis cliquez sur **exécutable**, **service com+** ou **service hébergé**sur le serveur, selon le type de fichier de configuration que vous souhaitez créer.

3. Dans la boîte de dialogue **ouvrir** , accédez au fichier spécifique pour lequel vous souhaitez créer un fichier de configuration, puis double-cliquez dessus.

4. Dans le menu **fichier** , pointez sur **Ajouter un nouvel élément** , puis cliquez sur **service**. L'Assistant Nouvel élément de service s'ouvre.

5. Suivez les étapes de création de service dans l'Assistant.

> [!NOTE]
> Si vous souhaitez utiliser NetPeerTcpBinding inclus dans le fichier de configuration (généré par l’Assistant), vous devez ajouter manuellement un élément de configuration de liaison et modifier l’attribut `mode` de son élément `security` en spécifiant "Aucun."

## <a name="configuring-com"></a>Configuration de COM+

L'Éditeur de configuration de service vous permet de créer un fichier de configuration pour une application COM+ existante ou de modifier une configuration COM+ existante. Le nœud de **contrat com** est visible uniquement lorsque la `comContract` section <> existe dans le fichier de configuration.

### <a name="creating-a-new-com-configuration"></a>Création d'une nouvelle configuration COM+

Avant de créer une configuration COM+, assurez-vous que votre application COM+ est installée dans les services de composants et enregistrée dans le Global Assembly Cache (GAC).

1. Sélectionnez le menu **fichier** -> **intégrer**l'  ->  **application com+.** Cette opération ferme le fichier actuellement ouvert. Si des données ne sont pas enregistrées dans le fichier actif, une boîte de dialogue d'enregistrement apparaît. L' **Assistant intégration com+** est ensuite lancé.

2. Dans la première page, sélectionnez l'application COM+ de l'arbre. Si vous ne trouvez pas votre application COM+ dans l’arbre, vérifiez qu’il est installé dans les services de composants et enregistré dans le Global Assembly Cache (GAC).

3. Dans la page suivante, sélectionnez les méthodes que vous souhaitez exposer en tant que services WCF. Toutes les méthodes prises en charge dans l'application COM+ sont affichées et sélectionnées par défaut.

4. Choisissez une méthode d'hébergement.

5. Configurez d'autres paramètres conformément aux indications de l'Assistant.

6. L'Éditeur de configuration de service utilise ComSvcConfig.exe en arrière-plan pour générer un fichier de configuration. Une fois terminé, vous pouvez consulter un résumé et quitter l'Assistant. Le fichier de configuration généré est ouvert afin que vous puissiez le modifier directement.

### <a name="editing-an-existing-com-configuration"></a>Modification d'une configuration COM+ existante

1. Sélectionnez le menu **fichier** -> **ouvrir**le  ->  **service com+**...

2. Sélectionnez le service COM+ que vous souhaitez modifier dans la liste.

3. Modifiez les paramètres de configuration dans le nœud **contrats com** .

    > [!NOTE]
    > Vous pouvez également ouvrir et modifier directement un fichier de configuration qui contient des contrats COM+.

## <a name="security"></a>Sécurité

Le caractère sécurisé des fichiers de configuration de service générés par l'Éditeur de configuration n'est pas garanti. Reportez-vous à la documentation relative à la [sécurité](./feature-details/security.md) pour savoir comment sécuriser vos services WCF.

De plus, l'Éditeur de configuration peut être utilisé uniquement pour lire et écrire des éléments de configuration WCF valides. Cet outil ignore les éléments conformes à des schémas, définis par l'utilisateur. Il ne tente pas non plus de supprimer ces éléments du fichier de configuration ou de déterminer leurs effets sur les éléments WCF connus. Il incombe à l'utilisateur de déterminer si ces éléments font peser une menace à l'application ou au système.
