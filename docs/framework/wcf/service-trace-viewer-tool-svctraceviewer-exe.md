---
title: Service Trace Viewer Tool (SvcTraceViewer.exe)
description: Utilisez Service Trace Viewer pour fusionner, afficher et filtrer les messages de trace dans le journal afin de pouvoir diagnostiquer, réparer et vérifier les problèmes de service WCF.
ms.date: 03/30/2017
ms.assetid: 9027efd3-df8d-47ed-8bcd-f53d55ed803c
ms.openlocfilehash: 0ad6094965291a965346522688a8334abbd4e6b3
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/23/2020
ms.locfileid: "85244567"
---
# <a name="service-trace-viewer-tool-svctraceviewerexe"></a>Service Trace Viewer Tool (SvcTraceViewer.exe)

L’outil Windows Communication Foundation (WCF) Service Trace Viewer vous aide à analyser les traces de diagnostics générées par WCF. Service Trace Viewer permet de fusionner, d’afficher et de filtrer facilement les messages de suivi dans le journal afin que vous puissiez diagnostiquer, réparer et vérifier les problèmes de service WCF.

## <a name="configuring-tracing"></a>Configuration du traçage

Les suivis de diagnostic vous fournissent des informations qui affichent ce qui arrive pendant le fonctionnement de votre application. Comme son nom l'indique, il permet de suivre le fonctionnement de la source à la destination, ainsi qu'au niveau de points intermédiaires.

Vous pouvez configurer le suivi à l’aide du fichier de configuration de l’application, soit Web.config pour les applications hébergées sur le Web, soit *appname*. config pour les applications auto-hébergées. Voici un exemple :

```xml
<system.diagnostics>
    <trace autoflush="true" />
    <sources>
            <source name="System.ServiceModel"
                    switchValue="Information, ActivityTracing"
                    propagateActivity="true">
            <listeners>
               <add name="sdt"
                   type="System.Diagnostics.XmlWriterTraceListener"
                   initializeData= "SdrConfigExample.e2e" />
            </listeners>
         </source>
    </sources>
</system.diagnostics>
```

Dans cet exemple, le nom et le type de l'écouteur de suivi sont spécifiés. L'écouteur est nommé `sdt` et l'écouteur de suivi standard de .NET Framework (System.Diagnostics.XmlWriterTraceListener) est ajouté comme type. L' `initializeData` attribut est utilisé pour définir le nom du fichier journal de cet écouteur `SdrConfigExample.e2e` . Pour le fichier journal, vous pouvez substituer un chemin d'accès complet par un nom de fichier simple.

Cet exemple crée un fichier dans le répertoire racine appelé SdrConfigExample.e2e. Lorsque vous utilisez la visionneuse de trace pour ouvrir le fichier comme décrit dans la section « ouverture et affichage des fichiers de trace WCF », vous pouvez voir tous les messages qui ont été envoyés.

Le niveau de suivi est contrôlé par le paramètre `switchValue`. Les niveaux de suivi disponibles sont décrits dans le tableau suivant.

|Niveau de suivi|Description|
|-----------------|-----------------|
|Critique|-Journalise les entrées de journal des événements et les échecs rapides et les informations de corrélation de suivi. Les éléments suivants sont quelques exemples de l'utilisation du  niveau critique :<br />-Votre AppDomain s’est déroulé en raison d’une exception non gérée.<br />-Votre application ne démarre pas.<br />-Le message à l’origine de l’échec provient du processus MyApp.exe.|
|Erreur|-Journalise toutes les exceptions. Vous pouvez utiliser le niveau Erreur dans les situations suivantes :<br />-Votre code s’est bloqué en raison d’une exception de cast non valide.<br />-Une exception « échec de la création du point de terminaison » est à l’origine de l’échec du démarrage de votre application.|
|Avertissement|: Il existe une condition qui peut entraîner une erreur ou une défaillance critique. Vous pouvez utiliser ce niveau dans les situations suivantes :<br />-L’application reçoit davantage de demandes que ses paramètres de limitation le permet.<br />-La file d’attente de réception est à 98% de sa capacité configurée.|
|Information|-Les messages utiles pour la surveillance et le diagnostic de l’état du système, la mesure des performances ou le profilage sont générés. Vous pouvez utiliser ces informations pour la planification de capacité et la gestion des performances. Vous pouvez utiliser ce niveau dans les situations suivantes :<br />-Une erreur s’est produite après que le message a atteint le domaine d’application AppDomain et a été désérialisé.<br />-Une erreur s’est produite lors de la création de la liaison HTTP.|
|Commentaires|-Suivi au niveau du débogage pour le code utilisateur et la maintenance. Définissez ce niveau lorsque :<br />-Vous ne savez pas quelle méthode dans votre code a été appelée lorsque l’échec s’est produit.<br />-Un point de terminaison incorrect a été configuré et le service n’a pas pu démarrer car l’entrée dans le magasin de réservations est verrouillée.|
|ActivityTracing|Transfert d'événements entre des activités de traitement et des composants.<br /><br /> Ce niveau permet aux administrateurs et aux développeurs de corréler des applications dans le même domaine d'application.<br /><br /> -Traces pour les limites d’activité : Start/Stop.<br />-Suivis pour les transferts.|

 Vous pouvez utiliser `add` pour indiquer les nom et type de l'écouteur de suivi à utiliser. Dans l'exemple de configuration, l'écouteur est nommé `sdt` et l'écouteur de suivi standard de .NET Framework (`System.Diagnostics.XmlWriterTraceListener`) est ajouté comme type. Utilisez `initializeData` pour définir le nom du fichier journal de cet écouteur. Vous pouvez également remplacer un chemin qualifié complet par un nom de fichier simple.

À partir de .NET Framework 4,8, les contrôles de zone de liste déroulante de certains thèmes à contraste élevé s’affichent dans la couleur correcte. Vous pouvez désactiver cette modification en supprimant le paramètre suivant dans le fichier *svcTraceViewer.exe.config* :

```xml
<AppContextSwitchOverrides value="Switch.UseLegacyAccessibilityFeatures=false;Switch.UseLegacyAccessibilityFeatures.2=false" />
```

## <a name="using-the-service-trace-viewer-tool"></a>Utilisation de l'outil Service Trace Viewer

### <a name="opening-and-viewing-wcf-trace-files"></a>Ouverture et consultation de fichiers de suivi WCF

Service Trace Viewer prend en charge trois types de fichier :

- Fichier de suivi WCF (. svcLog)

- Les fichiers de suivi d'événement (.etl)

- Les fichiers de suivi Crimson

 Service Trace Viewer permet d’ouvrir tout fichier de suivi pris en charge, d’ajouter et d’intégrer des fichiers de suivi supplémentaires ou d’ouvrir et de fusionner simultanément un groupe de fichiers de suivi.

##### <a name="to-open-a-trace-file"></a>Pour ouvrir un fichier de trace

1. Démarrez Service Trace Viewer à l’aide d’une fenêtre de commande pour accéder à votre emplacement d’installation WCF (C:\Program Files\Microsoft SDKs\Windows\v6.0\Bin), puis tapez `SvcTraceViewer.exe` .

> [!NOTE]
> L'outil Service Trace Viewer peut être associé à deux types de fichier : .svclog et .stvproj. Vous pouvez utiliser deux paramètres dans la ligne de commande pour inscrire et supprimer l’inscription des extensions de fichier.
>
> /register : inscrire l’association des extensions de fichier .svclog et .stvproj avec SvcTraceViewer.exe
>
> /unregister : supprimer l'inscription de l'association des extensions de fichier .svclog et .stvproj avec SvcTraceViewer.exe

1. Lorsque Service Trace Viewer démarre, cliquez sur **fichier** , puis pointez sur **ouvrir**. Naviguez jusqu'à l'emplacement où vos fichiers de suivi sont stockés.

2. Double-cliquez sur le fichier de suivi que vous souhaitez ouvrir.

    > [!NOTE]
    > Appuyez sur MAJ en cliquant sur plusieurs fichiers de suivi pour sélectionner et ouvrir simultanément plusieurs fichiers. Service Trace Viewer fusionne le contenu de tous les fichiers et les affiche. Par exemple, vous pouvez ouvrir des fichiers à la fois de clients et de services. Cela est utile lorsque vous avez activé l'enregistrement de message et la propagation d'activité dans la configuration. Ainsi, vous pouvez consulter l'échange de messages entre le client et le service. Vous pouvez également faire glisser plusieurs fichiers dans la visionneuse ou utiliser l’onglet **projet** . Pour plus d’informations, consultez la section gestion du projet.

3. Pour ajouter des fichiers de trace supplémentaires au regroupement ouvert, cliquez sur **fichier** , puis pointez sur **Ajouter**. Dans la fenêtre qui s'affiche, naviguez jusqu'à l'emplacement des fichiers de suivi et double-cliquez sur le fichier que vous souhaitez ajouter.

> [!CAUTION]
> Il n'est pas recommandé de charger un fichier journal de suivi dont la taille est supérieure à 200 Mo. Si vous essayez de charger un fichier plus volumineux, le processus de chargement peut durer longtemps, selon vos ressources informatiques. L'outil Service Trace Viewer peut ne peut pas être réactif pendant une longue période, ou épuiser la mémoire de l'ordinateur. Pour éviter cela, il est recommandé de configurer un chargement partiel. Pour plus d'informations sur la méthode à utiliser, consultez la section consacrée au chargement des fichiers de suivi volumineux.

#### <a name="event-tracing-and-crimson-tracing"></a>Suivi de fichier d'événement et de fichier Crimson

Le format natif de la visionneuse est le format de suivi d’activité que WCF émet. Les suivis émis dans un format différent doivent être convertis avant que Viewer les affiche. Actuellement, Viewer prend en charge le format de suivi d'activité mais également de fichiers d'événement et de fichiers Crimson.

Lorsque vous ouvrez un fichier qui ne contient pas de suivis d'activité, Viewer essaie de convertir le fichier. Vous devez préciser le nom et emplacement du fichier qui contiendra les données de suivi converties. Une fois que les données ont été converties, Viewer affiche le contenu du nouveau fichier.

> [!NOTE]
> La conversion nécessite de l'espace disque pour stocker les données de suivi converties. Assurez-vous que vous disposez de suffisamment d'espace disque pour stocker les données avant de démarrer une conversion. Sinon, la conversion échoue.

### <a name="managing-projects"></a>Gestion de projets

Viewer prend en charge les projets pour faciliter l'affichage de plusieurs fichiers de suivi. Par exemple, si vous avez un fichier de suivi client et un fichier de suivi de service, vous pouvez les ajouter à un projet. Puis, à chaque fois que vous ouvrez le projet, tous les fichiers de suivi du projet sont chargés simultanément.

Il existe deux façons de gérer des projets :

- Dans le menu **fichier** , vous pouvez ouvrir, enregistrer et fermer des projets.

- Dans l’onglet **projet** , vous pouvez ajouter des fichiers à un projet.

### <a name="viewing-wcf-traces"></a>Consultation de fichiers de suivi WCF

WCF émet des traces à l’aide du format de suivi d’activité. Dans le modèle de suivi d'activité, les suivis individuels sont regroupés par activité en fonction de leur but. Le flux de contrôle logique est transféré entre les activités. Par exemple, pendant la durée de vie d'une application, de nombreuses activités d'envoi de messages apparaissent et disparaissent. Pour plus d’informations sur l’affichage des suivis et des activités, ainsi que sur l’interface utilisateur de Service Trace Viewer, consultez [utilisation de Service Trace Viewer pour afficher les suivis corrélés et résoudre les problèmes](./diagnostics/tracing/using-service-trace-viewer-for-viewing-correlated-traces-and-troubleshooting.md).

#### <a name="switching-to-different-views"></a>Basculer vers des vues différentes

Service Trace Viewer propose les différentes vues suivantes. Ils s’affichent sous forme d’onglets dans le volet gauche de la visionneuse et sont également accessibles à partir du menu **affichage** .

- Vue d'activité

- Vue du projet

- Vue du message

- Vue Graphique

##### <a name="activity-view"></a>Vue d'activité

Une fois les fichiers de suivi ouverts, vous pouvez voir les suivis regroupés en activités et affichés dans la vue **activité** dans le volet gauche.

La vue **activité** affiche les noms d’activité, le nombre de suivis dans l’activité, la durée, l’heure de début et l’heure de fin.

Lorsque vous cliquez sur chacune des activités répertoriées, les suivis de cette activité sont affichés à droite dans le volet de suivi. Vous pouvez ensuite sélectionner un suivi pour afficher ses détails.

Vous pouvez sélectionner plusieurs activités en appuyant sur la touche **CTRL** ou **MAJ** et en cliquant sur les activités souhaitées. Le volet de suivi affiche tous les suivis des activités sélectionnées.

Vous pouvez double-cliquer sur une activité pour l’afficher dans la vue du **graphique** . L’autre méthode consiste à sélectionner une activité et à basculer vers la vue du **graphique** .

> [!NOTE]
> L’activité « 000000000000 » est une activité spéciale qui ne peut pas être affichée dans la vue du graphique. Étant donné que toutes les autres activités sont liées à cette activité, l'affichage de celle-ci a une incidence importante en termes de performances.

Vous pouvez cliquer sur le titre de colonne pour trier la liste d'activités. Les activités qui contiennent des suivis d'avertissement ont un arrière-plan jaune et celles qui contiennent des suivis d'erreur ont un arrière-plan rouge.

Il existe différents types d'activité et chaque type correspond à une icône sur le côté gauche de chaque activité. Vous pouvez vous reporter à la section Présentation des icônes de suivi pour connaître leur signification.

##### <a name="project-view"></a>Vue du projet

Cette vue vous permet de gérer des fichiers de suivi dans le projet actif. Pour plus d'informations, voir la section Gestion de projet.

##### <a name="message-view"></a>Vue du message

Cette vue vous permet d’afficher toutes les traces des journaux de messages, y compris l’action, la date/heure, le processus, activité et from/to, et d’accéder aux détails du suivi du journal des messages associé. Vous pouvez regrouper les suivis des journaux de messages par limite d’activité, processus/thread ou envoyer & réception pour faciliter la navigation dans le message.

##### <a name="graph-view"></a>Vue Graphique

Cet affichage présente les données de suivi pour une activité donnée sous forme de graphique. Le graphique vous permet de voir l'exécution des événements pas à pas et les relations entre plusieurs activités alors que des données circulent entre elles.

Pour basculer vers la vue **graphique** , sélectionnez une activité dans la vue **activité** et cliquez sur l’onglet **activité** ou sur un suivi du journal des messages dans la vue **message** . Si plusieurs fichiers de suivi sont chargés et que l'activité regroupe des suivis de plusieurs fichiers, tous les suivis concernés apparaissent dans la vue Graphique. Le double-clic sur les activités et les suivis du journal des messages vous amène également sur la vue du **graphique** .

Dans la vue du **graphique** , chaque colonne verticale représente une activité, et chaque bloc dans la colonne représente une trace. Les activités sont regroupées par processus (ou thread). Les petites flèches entre les activités représentent des transferts. Les grandes flèches entre les processus représentent l'échange de messages. L'activité sélectionnée est toujours en jaune.

###### <a name="selecting-traces-in-the-graph"></a>Sélection de suivis dans le graphique

1. Cliquez sur un bloc dans le graphique.

2. Utilisez les touches haut et bas pour sélectionner les suivis précédents et suivants.

3. Observez les informations de suivi dans le volet Suivi et le volet Détail.

###### <a name="expanding-or-collapsing-activity-transfers"></a>Développement ou réduction de transferts d’activité

Vous pouvez développer les transferts d’activité lors du transfert de l’activité sélectionnée vers une autre activité. Cela vous permet de suivre les transferts.

Pour développer ou réduire des transferts d‘activité

1. Localisez le suivi de transfert avec un signe « + » à gauche de l’icône de transfert.

2. Cliquez sur « + » ou appuyez sur **CTRL** et « + » à l’aide du clavier.

3. L'activité suivante apparaît dans le graphique.

4. Un « - » s’affiche à gauche de l’icône de transfert. Cliquez sur le signe « - » ou appuyez sur Ctrl et « - » pour réduire le transfert d’activité.

> [!NOTE]
>  Lorsqu'une activité se compose de plusieurs transferts et que vous développez l'un des transferts, les activités entre l'activité racine et la nouvelle activité s'affichent. Ces nouvelles activités apparaissent sous forme réduite. Si vous souhaitez consulter les détails de ces activités, développez-les verticalement en cliquant sur l’icône de développement dans l’en-tête du graphique.

###### <a name="expanding-or-collapsing-activities-vertically"></a>Développement ou réduction verticaux des activités

La visionneuse masque les détails inutiles dans le graphique d'activité en réduisant les activités. Dans une activité réduite, les suivis individuels ne sont pas affichés. Seuls les transferts de suivi apparaissent. Si vous souhaitez consulter tous les suivis d’une activité, développez l’activité verticalement en cliquant sur l’icône de développement de l’activité dans l’en-tête du graphique.

Pour développer ou réduire verticalement des activités :

1. Cliquez sur l’icône + dans l’en-tête d’activité pour développer verticalement l’activité.

2. Remarquez que tous les suivis sont affichés dans le graphique.

3. Cliquez sur l’icône « - » dans l’en-tête d’activité pour réduire verticalement l’activité.

4. Remarquez que seuls les transferts, journaux de messages, suivis d'avertissement et d'exception importants sont affichés dans l'activité.

###### <a name="options"></a>Options

Vous pouvez sélectionner deux options **dans le menu options de** la vue du graphique.

- Si Afficher les suivis de limite d'activité est désactivé, les suivis de limite d'activité sont ignorés dans le graphique.

- Si Afficher les suivis de détail d'informations hors message est désactivé, les suivis au niveau de détail d'informations sont ignorés, à l'exception des suivis de messages. Dans la plupart des cas, les suivis au niveau de détail d'informations sont moins importants pour l'analyse. Cette option est utile lorsque vous ne souhaitez pas analyser des suivis au niveau de détail d'informations et que vous souhaitez uniquement vous concentrer sur des suivis plus importants.

###### <a name="layout-mode"></a>Mode disposition

La visionneuse a deux modes de disposition : **processus** et **thread**. Ce paramètre définit la plus grande unité d'organisation. Le mode de disposition par défaut est **processus**, ce qui signifie que les activités sont regroupées par processus dans le graphique.

###### <a name="execution-list"></a>Liste d'exécution

Dans cette liste déroulante, vous pouvez sélectionner quel processus ou thread vous souhaitez afficher dans le graphique. Par exemple, si les fichiers de suivi de deux clients (A et B) et un service sont ouverts, et que vous souhaitiez seulement afficher le service et le client A dans le graphique, vous pouvez désélectionner le client B dans la liste.

#### <a name="viewing-trace-details"></a>Affichage des détails de suivi

Pour consulter un détail de suivi, sélectionnez un suivi dans le volet Suivi. Les détails sont affichés dans le volet Détails.

##### <a name="trace-pane"></a>Volet Suivi

Le volet supérieur droit de Service Trace Viewer est le Volet Trace. Il répertorie tous les suivis dans l'activité sélectionnée et inclut des informations supplémentaires telles que le niveau de suivi, l'ID de thread, le nom du processus.

Vous pouvez copier le code XML brut de la trace dans le presse-papiers en cliquant avec le bouton droit sur une trace et en sélectionnant **copier la trace dans le presse-papiers**.

##### <a name="detail-pane"></a>Volet d'informations

Le volet gauche inférieur du Service Trace Viewer est le volet Détails. Il se compose de trois onglets pour afficher les détails de suivi.

La vue **mise en forme** affiche les informations de façon plus organisée. Elle répertorie tous les éléments XML connus dans les tables et les arbres et simplifie ainsi la lecture et la compréhension des informations.

La vue **XML** affiche le XML correspondant à la trace sélectionnée. Elle prend en charge la mise en surbrillance et la couleur de syntaxe. Lorsque **vous utilisez la** recherche pour rechercher des chaînes, elle met en surbrillance les résultats de la recherche.

La vue **message** affiche la partie message du document XML dans les traces du journal des messages. Elle est invisible lorsque vous sélectionnez un suivi qui ne contient pas de message.

### <a name="filtering-wcf-traces"></a>Filtrage de suivis WCF

Pour simplifier l'analyse de fichiers de suivi, vous pouvez les filtrer selon les méthodes suivantes :

- La barre d'outils de filtre permet d'accéder aux filtres prédéfinis et personnalisés. Il peut être activé par le biais du menu **affichage** .

- Le filtre prédéfini de la visionneuse peut être utilisé pour filtrer de manière sélective les parties des traces WCF. Par défaut, il est configuré pour permettre à tous les suivis d'infrastructure de passer. Les paramètres de ce filtre sont définis dans le sous-menu **options de filtre** sous le menu **affichage** .

- Les filtres XPath personnalisés permettent aux utilisateurs de contrôler entièrement les filtres. Ils peuvent être définis dans le **filtre personnalisé** sous le menu **affichage** .

Seuls les suivis qui traversent tous les filtres actifs sont affichés.

#### <a name="using-the-filter-toolbar"></a>Utilisation de la barre d'outils de filtre

La barre d'outils de filtre apparaît dans la partie supérieure de l'outil. S’il n’est pas présent, vous pouvez l’activer dans le menu **affichage** . La barre inclut trois composants :

- Rechercher : **recherche** définit l’objet à rechercher dans l’opération de filtrage. Par exemple, si vous souhaitez rechercher toutes les traces qui ont été émises dans le contexte du processus X, définissez ce champ sur X et le champ **Rechercher dans** sur « process name ». Ce champ se transforme en contrôle de sélecteur DateTime lorsqu'un filtre temporel est sélectionné.

- Rechercher dans : ce champ définit le type de filtre à appliquer.

- Niveau : le paramètre de niveau permet de définir le niveau de suivi minimal autorisé par le filtre. Par exemple, si le niveau est défini sur « Erreur et Haut », seuls les suivis de niveau Erreur et Critique s'affichent. Ce filtre s'associe aux critères spécifiés par Rechercher et Rechercher dans.

Le bouton **Filtrer maintenant** démarre l’opération de filtre. Certains filtres, surtout lorsqu'ils s'appliquent à un ensemble important de données, prennent du temps à se terminer. Vous pouvez annuler l’opération de filtre en appuyant sur le bouton **arrêter** qui apparaît dans la barre d’État sous le menu **opérations** .

Le bouton **Effacer** réinitialise les filtres prédéfinis et personnalisés pour permettre à tous les suivis de passer.

#### <a name="filter-options"></a>Options du filtre

Trace Viewer peut supprimer automatiquement les suivis WCF de la vue. Il est possible de sélectionner les suivis émis en fonction des zones spécifiques de WCF, par exemple, en supprimant de la vue les suivis liés aux transactions.

Les paramètres de ce filtre sont définis dans le sous-menu **options de filtre** sous le menu **affichage** .

#### <a name="custom-filters"></a>Filtres personnalisés

Si vous connaissez le langage XML XPath, vous pouvez l'utiliser pour créer des filtres personnalisés et rechercher des éléments XML intéressants dans les données de suivi. Vous pouvez accéder aux filtres par la barre d'outils de filtre.

Les filtres personnalisés peuvent inclure des paramètres. Vous pouvez également importer des filtres préexistants personnalisés.

##### <a name="creating-a-custom-filter"></a>Création d'un filtre personnalisé

Il existe deux façons de créer des filtres :

###### <a name="creating-a-custom-filter-using-the-template-wizard"></a>Création d'un filtre personnalisé à l'aide de l'Assistant Modèle

Vous pouvez cliquer sur un suivi existant et créer un filtre en fonction de la structure du suivi. Cet exemple permet de créer un filtre personnalisé en fonction de l'ID de thread.

1. Dans le volet de suivi, dans la zone supérieure droite de Trace Viewer, sélectionnez un suivi qui inclut l'élément que vous souhaitez filtrer.

2. Cliquez sur le bouton **créer un filtre personnalisé** situé en haut du volet de suivi.

3. Dans la boîte de dialogue qui s'affiche, entrez un nom pour votre filtre. Dans cet exemple, entrez `Thread ID` . Vous pouvez également fournir une description de votre filtre.

4. L’arborescence sur la gauche affiche la structure de l’enregistrement de suivi que vous avez sélectionné lors de la première étape. Naviguez jusqu'à l'élément pour lequel vous souhaitez créer une condition. Dans cet exemple, accédez au ThreadID à localiser dans le nœud XPath : /E2ETraceEvent/System/Execution/@ThreadID . Double-cliquez sur l'attribut ThreadID dans l'arborescence. Cela crée à droite de la boîte de dialogue une expression pour l'attribut.

5. Modifiez le champ de paramètre pour la condition ThreadID de None en « {0} ». Cette étape permet de configurer la valeur de ThreadID lorsque le filtre est appliqué (voir la section Comment appliquer un filtre). Vous pouvez définir jusqu'à quatre paramètres. Les conditions sont associées à l'aide de l'opérateur OR.

6. Cliquez sur **OK** pour créer le filtre.

> [!NOTE]
> Une fois qu'un filtre a été créé à l'aide de l'Assistant Modèle, il peut être modifié uniquement manuellement. Il n'est pas possible d'activer l'Assistant pour un filtre qui a été créé précédemment. De plus, les conditions d'un filtre XPath créé dans l'Assistant Modèle sont associées à l'aide de l'opérateur OR. Si vous avez besoin d'une opération AND, vous pouvez modifier l'expression de filtre une fois qu'elle a été créée.

###### <a name="creating-a-custom-filter-manually"></a>Création manuelle d'un filtre personnalisé

Le menu Filtres personnalisés vous permet d’entrer des filtres XPath manuellement.

1. Dans le menu Affichage, cliquez sur l’élément de menu **filtres personnalisés** .

2. Dans la boîte de dialogue qui s’affiche, cliquez sur **nouveau.**

3. Au minimum, précisez un nom de filtre et une expression XPath.

4. Cliquez sur **OK**.

###### <a name="applying-a-custom-filter"></a>Application d'un filtre personnalisé

Une fois qu'un filtre personnalisé a été créé, il est accessible via la barre d'outils de filtre. Sélectionnez le filtre que vous souhaitez appliquer dans le champ **Rechercher dans** de la barre d’outils filtre. Pour l'exemple précédent, sélectionnez 'ID Thread'.

1. Spécifiez la valeur que vous recherchez dans le champ **Rechercher** . Dans notre exemple, entrez l'ID du thread pour lequel vous souhaitez effectuer une recherche.

2. Cliquez sur **Filtrer maintenant**et observez le résultat de l’opération.

Si votre filtre utilise plusieurs paramètres, entrez-les en utilisant « ; » comme séparateur dans le champ **Rechercher** . Par exemple, la chaîne suivante définit trois paramètres : '1;findValue;text'. La visionneuse applique « 1 » au {0} paramètre du filtre. 'findValue’et’text’sont appliqués {1} respectivement à et {2} .

###### <a name="sharing-custom-filters"></a>Partage de filtres personnalisés

Les filtres personnalisés peuvent être partagés entre différentes sessions et différents utilisateurs. Vous pouvez exporter les filtres vers un fichier de définition et importer ce fichier vers un autre emplacement.

 Pour importer un filtre personnalisé :

1. Dans le menu **affichage** , cliquez sur **filtres personnalisés**.

2. Dans la boîte de dialogue qui s’ouvre, cliquez sur le bouton **Importer** .

3. Accédez au fichier de filtre personnalisé (. stvcf), cliquez sur le fichier, puis cliquez sur le bouton **ouvrir** .

Pour exporter un filtre personnalisé :

1. Dans le menu Affichage, cliquez sur **filtres personnalisés**.

2. Dans la boîte de dialogue qui s'affiche, sélectionnez le filtre que vous souhaitez exporter.

3. Cliquez sur le bouton **Exporter**.

4. Spécifiez le nom et l’emplacement du fichier de définition de filtre personnalisé (. stvcf), puis cliquez sur le bouton **Enregistrer** .

> [!NOTE]
> Ces filtres personnalisés peuvent uniquement être importés et exportés à partir de Service Trace Viewer. Ils ne peuvent pas être lus par d'autres outils.

### <a name="finding-data"></a>Recherche de données

L'outil Viewer permet de rechercher des données selon les méthodes suivantes :

- La barre d'outils Rechercher fournit un accès rapide aux options de recherche les plus courantes.

- La boîte de dialogue Rechercher fournit des options de recherche supplémentaires. Elle est accessible via le menu **Edition** ou par la touche de raccourci Ctrl + F.

La barre d'outils Rechercher apparaît en haut de l'outil Viewer. S’il n’est pas présent, vous pouvez l’activer dans le menu **affichage** . La barre se compose de deux composants :

- Rechercher : vous pouvez y entrer un mot clé de recherche.

- Regardez dans : vous pouvez y entrer la zone de recherche. Vous pouvez choisir d'effectuer une recherche dans toutes les activités ou dans l'activité en cours uniquement.

La boîte de dialogue de recherche fournit deux options supplémentaires :

- Rechercher la cible :

  - L’option « données brutes du journal » recherche le mot clé dans toutes les données brutes.

  - Les options « XML Text » et « XML attribute » recherchent uniquement dans les éléments XML.

  - L’option « message journalisé » recherche le mot clé uniquement dans les messages.

- Ignorer l’activité racine : la recherche ignore les traces dans l’activité « 000000000000 ». Cela permet d'améliorer les performance dans les fichiers de suivi volumineux lorsque l'activité racine se compose de milliers de suivis dont la plupart sont des transferts.

### <a name="navigating-traces"></a>Navigation parmi les suivis

Parce que les suivis sont enregistrés pas à pas pendant l'exécution des applications, la navigation parmi les suivis peut vous aider à déboguer votre application. Service Trace Viewer fournit différentes façons de naviguer dans les suivis.

#### <a name="step-forward-or-backward"></a>Étape suivante ou Étape précédente

Si vous considérez chaque trace comme une ligne de code dans le programme, le pas à pas détaillé est très similaire à « pas à pas principal » dans l’environnement de développement intégré (IDE) de Visual Studio. La différence est que vous pouvez également revenir en arrière dans les suivis. « Étape suivante » vous permet de passer au suivi suivant dans l'activité.

- Étape suivante : utilisez le menu **activité** ou appuyez sur F10. Vous pouvez également utiliser la touche de direction « bas » dans le volet de suivi.

- Pas à pas précédent : utilisez le menu **activité** ou appuyez sur « F9 ». Vous pouvez également utiliser la touche de direction « haut » dans le volet de suivi.

> [!NOTE]
> Cela peut vous permettre d’atteindre une activité qui se produit dans un processus différent ou même sur un autre ordinateur, car les messages WCF peuvent transporter des ID d’activité qui s’étendent sur les ordinateurs.

#### <a name="follow-transfer"></a>Suivre le transfert

Les suivi de transfert sont des suivis spéciaux dans le fichier de suivi. Il est possible d'effectuer un transfert d'une activité vers une autre activité par le biais d'un suivi de transfert. Par exemple, « activité A » peut être transféré à « Activity B ». Dans ce cas, il existe un suivi de transfert dans le « Activity A » avec le nom « to : Activity » et l’icône de transfert. Ce suivi de transfert est un lien entre les deux suivis. Dans « Activity B », il peut également y avoir un suivi de transfert à la fin de l’activité à transférer à « activité A ». Ce processus est identique aux appels de fonctions dans les programmes: A appelle B, puis B retourne l'appel.

« Suivre le transfert » est semblable à « pas à pas détaillé » dans un débogueur. Il suit le transfert de l'activité A vers l'activité B. Il n'a aucun effet sur les autres suivis.

Il existe deux façons de suivre un transfert : à l'aide de la souris ou du clavier :

- À l'aide de la souris : double-cliquez sur le suivi de transfert dans le volet de suivi.

- Par clavier : sélectionnez un suivi de transfert et utilisez « suivre le transfert » dans le menu **activité** ou appuyez sur « F11 ».

> [!NOTE]
> Dans de nombreux cas, lors d'un transfert de l'activité A vers l'activité B, l'activité A attend le transfert de retour de l'activité B vers l'activité A. Cela signifie qu'aucun suivi n'est enregistré par l'activité A lors du suivi actif de l'activité B. Toutefois, il est également possible que l'activité A n'attende pas et continue à enregistrer des suivis. Il est également possible que l'activité B n'effectue pas de transfert en retour vers l'activité A. Par conséquent, les transferts d'activité sont encore différents des appels de fonction. La vue Graphique vous permet de mieux comprendre les transferts d'activité.

#### <a name="jump-to-next-or-previous-transfer"></a>Passer au transfert suivant ou précédent

Lorsque vous analysez l'activité en cours ou certaines activités sélectionnées en cas de sélection de plusieurs activités, vous pouvez rechercher rapidement les activités vers lesquelles des transferts sont effectués. « Passer au transfert suivant » vous permet de localiser le suivi de transfert suivant dans l’activité. Une fois que vous avez trouvé le suivi de transfert, vous pouvez utiliser « suivre le transfert » pour effectuer un pas à pas détaillé dans l’activité suivante.

- Passer au transfert suivant : utilisez le menu **activité** ou appuyez sur « Ctrl + F10 ».

- Passer au transfert précédent : utilisez le menu **activité** ou appuyez sur « CTRL + F9 ».

#### <a name="navigate-in-graph-view"></a>Naviguer dans la vue Graphique

Bien que la navigation dans le volet d’activité et le volet de suivi est similaire au débogage, l’utilisation de la vue de **graphique** offre une meilleure expérience de navigation. Pour plus d’informations, consultez la section « vue du graphique ».

### <a name="loading-large-trace-files"></a>Chargement de fichiers de suivi volumineux

Les fichiers de suivi peuvent être volumineux. Par exemple, si vous activez le suivi au niveau « commentaires », le fichier de trace résultant pour une exécution de quelques minutes peut facilement atteindre des centaines de mégaoctets, voire plus, en fonction de la vitesse du réseau et du modèle de communication.

Lorsque vous ouvrez un fichier de suivi volumineux dans Service Trace Viewer, cela peut avoir une incidence néfaste sur les performances système. La vitesse de chargement et le temps de réponse après le chargement peut être lent. La vitesse réelle diffère et dépend de votre configuration matérielle. Dans la plupart des PC, le chargement d'un fichier de suivi de taille supérieure à 200 Mo peut avoir une incidence néfaste sur les performances. Pour les fichiers de suivi de taille supérieure à 1 Go, il est possible que l'outil utilise toute la mémoire disponible ou cesse de répondre pendant un très long moment.

Pour éviter le ralentissement du chargement et du temps de réponse lors de l’analyse de fichiers de trace volumineux, Service Trace Viewer fournit une fonctionnalité appelée « chargement partiel », qui charge uniquement une petite partie de la trace à la fois. Par exemple, un fichier de suivi de taille supérieure à 1 Go peut s'exécuter pendant plusieurs jours sur le serveur. Lorsque certaines erreurs se sont produites et que vous souhaitez analyser le suivi, vous n'avez pas besoin d'ouvrir entièrement le fichier de suivi. Vous pouvez charger les suivis au moment où l'erreur a pu se produire. Étant donné que l'étendue est plus petite, l'outil Service Trace Viewer peut charger le fichier plus rapidement et vous pouvez identifier les erreurs à l'aide d'un groupe de données plus petit.

#### <a name="enabling-partial-loading"></a>Activation du chargement partiel

Vous n'avez pas besoin d'activer manuellement le chargement partiel. Si la taille totale des fichiers de suivi que vous essayez de charger dépasse 40 Mo, Service Trace Viewer affiche automatiquement une boîte de dialogue Chargement partiel pour que vous puissiez sélectionner la partie que vous souhaitez charger.

> [!NOTE]
> Étant donné que les suivis ne sont pas toujours répartis de façon régulière dans l'intervalle de temps, la durée que vous spécifiez dans la barre d'outils Chargement partiel n'est peut être pas proportionnelle à la taille de chargement affichée. La taille de chargement réelle peut être plus petite que la taille estimée dans la boite de dialogue de chargement partiel.

#### <a name="adjusting-partial-loading"></a>Ajuster le chargement partiel

Une fois que vous avez chargé partiellement le fichier de suivi, vous pouvez modifier le groupe de données en cours de chargement. Vous pouvez l'effectuer en ajustant la barre d'outils Chargement partiel dans la partie supérieure de Viewer.

1. Déplacez la barre d'outils à l'aide de la souris ou indiquez le début et la fin du chargement partiel.

2. Cliquez sur le bouton **ajuster** .

## <a name="understanding-trace-icons"></a>Fonctionnement des icônes de suivi

La liste suivante répertorie les icônes que l’outil Service Trace Viewer utilise dans l’affichage des **activités** , la vue du **graphique** et le volet de **suivi** pour représenter des éléments différents.

> [!NOTE]
> Certaines traces qui ne sont pas catégorisées (par exemple, « un message est fermé ») n’ont aucune icône.

### <a name="activity-tracing-traces"></a>Suivi d'activité

|Icône|Description|
|----------|-----------------|
|![Suivi d'avertissement](./media/7457c4ed-8383-4ac7-bada-bcb27409da58.gif "7457c4ed-8383-4ac7-bada-bcb27409da58")|Suivi d'avertissement : suivi émis au niveau avertissement|
|![Suivi d'erreur](./media/7d908807-4967-4f6d-9226-d52125db69ca.gif "7d908807-4967-4f6d-9226-d52125db69ca")|Suivi d'erreur: suivi émis au niveau erreur.|
|![Suivi de démarrage d'activité :](./media/8a728f91-5f80-4a95-afe8-0b6acd6e0317.gif "8a728f91-5f80-4a95-afe8-0b6acd6e0317")|Suivi de démarrage d'activité : suivi qui marque le début d'une activité. Il contient le nom de l'activité. En tant que concepteur ou développeur d'applications, vous devez définir un suivi de démarrage d'activité par ID d'activité par processus ou thread.<br /><br /> Si l'ID d'activité est propagé à travers des sources de suivi pour la corrélation de suivis, vous pouvez consulter plusieurs démarrages pour le même ID d'activité (un par source de suivi). Le suivi de démarrage est émis si le suivi d'activités est activé pour la source de suivi.|
|![Suivi d'arrêt d'activité](./media/a0493e95-653e-4af8-84a4-4d09a400bc31.gif "a0493e95-653e-4af8-84a4-4d09a400bc31")|Suivi d'arrêt d'activité : suivi qui marque la fin d'une activité. . Il contient le nom de l'activité. En tant que concepteur ou développeur d'applications, vous devez définir un suivi d'arrêt d'activité par ID d'activité par source de suivi. Aucun suivi de source de suivi n'apparaît après le suivi d'arrêt d'activité émis par la source de suivi, sauf si la granularité de l'heure du suivi n'est pas suffisamment réduite. Lorsque cela se produit, deux suivis portant la même heure, y compris un arrêt, peuvent être entrelacés lorsqu'ils sont affichés. Si l'ID d'activité est propagé à travers les sources de suivi pour la corrélation de suivis, vous pouvez consulter plusieurs arrêts pour le même ID d'activité (un par source de suivi). Le suivi d'arrêt est émis si le suivi d'activités est activé pour la source de suivi.|
|![Suivi d'interruption d'activité](./media/6f7f4191-df2b-4592-8998-8379769e2d32.gif "6f7f4191-df2b-4592-8998-8379769e2d32")|Suivi d'interruption d'activité : suivi qui marque l'heure à laquelle une activité marque une pause. Aucun suivi n'est émis pendant l'interruption d'une activité, jusqu'à ce que l'activité reprenne. Une activité interrompue indique qu'aucun traitement ne parvient à cette activité au niveau de la source de suivi. Les suivis d'interruption/reprise sont utiles pour effecteur des profilages. Le suivi d'interruption est émis si le suivi d'activités est activé pour la source de suivi.|
|![Suivi de reprise d'activité](./media/1060d9d2-c9c8-4e0a-9988-cdc2f7030f17.gif "1060d9d2-c9c8-4E0A-9988-cdc2f7030f17")|Suivi de reprise d'activité : suivi qui marque l'heure à laquelle une activité reprend après avoir été interrompue. Les suivis peuvent être émis de nouveau dans cette activité. Les suivis d'interruption/reprise sont utiles pour effecteur des profilages. Le suivi de reprise est émis si le suivi d'activités est activé pour la source de suivi.|
|![Transférer](./media/b2d9850e-f362-4ae5-bb8d-9f6f3ca036a5.gif "b2d9850e-f362-4ae5-bb8d-9f6f3ca036a5")|Transfert : un suivi est émis lorsque le flux de contrôle logique est transféré d'une activité à une autre. L'activité dont provient le transfert peut continuer à fonctionner en parallèle de l'activité vers laquelle le transfert se dirige. Le suivi de transfert est émis si le suivi d'activités est activé pour la source de suivi.|
|![Transférer de](./media/1df215cb-b344-4f36-a20d-195999bda741.gif "1df215cb-b344-4f36-a20d-195999bda741")|Transfert De : suivi qui définit un transfert d'une autre activité vers l'activité actuelle.|
|![Transférer vers](./media/74255b6e-7c47-46ef-8e53-870c76b04c3f.gif "74255b6e-7c47-46ef-8e53-870c76b04c3f")|Transfert A : suivi qui définit un transfert de flux de contrôle logique de l'activité actuelle vers une autre activité.|

### <a name="wcf-traces"></a>Suivis WCF

|Icône|Description|
|----------|-----------------|
|![Suivi du journal des messages](./media/7c66e994-2476-4260-a0db-98948b9af197.gif "7c66e994-2476-4260-a0db-98948b9af197")|Suivi du journal des messages : suivi émis lorsqu’un message WCF est enregistré par la fonctionnalité de journalisation des messages, lorsque la `System.ServiceModel.MessageLogging` source de suivi est activée. Un clic sur ce suivi permet d'afficher le message. Il existe quatre points d'enregistrement configurables pour un message : ServiceLevelSendRequest, TransportSend, TransportReceive et ServiceLevelReceiveRequest, qui peut également être spécifié par l'attribut `messageSource` dans le suivi du journal des messages.|
|![Suivi de message reçu](./media/de4f586c-c5dd-41ec-b1c3-ac56b4dfa35c.gif "de4f586c-c5dd-41ec-b1c3-ac56b4dfa35c")|Trace message received : suivi émis lors de la réception d’un message WCF, si la `System.ServiceModel` source de suivi est activée au niveau des informations ou du niveau de détail. Ce suivi est essentiel pour afficher la flèche de la corrélation des messages dans la vue du **graphique** d’activité.|
|![Trace du message envoyé](./media/558943c4-17cf-4c12-9405-677e995ac387.gif "558943c4-17cf-4c12-9405-677e995ac387")|Trace du message envoyé : suivi émis lorsqu’un message WCF est envoyé si la `System.ServiceModel` source de suivi est activée au niveau des informations ou des commentaires. Ce suivi est essentiel pour afficher la flèche de la corrélation des messages dans la vue du **graphique** d’activité.|

### <a name="activities"></a>Activités

|Icône|Description|
|----------|-----------------|
|![Activité](./media/wcfc-defaultactivityc.gif "wcfc_defaultActivityc")|Activité : indique que l'activité actuelle est une activité générique.|
|![Activité racine](./media/5dc8e0eb-1c32-4076-8c66-594935beaee9.gif "5dc8e0eb-1c32-4076-8c66-594935beaee9")|Activité racine : indique l'activité racine d'un processus.|

### <a name="wcf-activities"></a>Activités WCF

|Icône|Description|
|----------|-----------------|
|![Activité d'environnement](./media/29fa00ac-cf78-46e5-822d-56222fff61d1.gif "29fa00ac-cf78-46e5-822d-56222fff61d1")|Activité de l’environnement : activité qui crée, ouvre ou ferme un hôte ou un client WCF. Les erreurs qui se sont produites pendant ces phases apparaîtront dans cette activité.|
|![Activité d'écoute](./media/d7b135f6-ec7d-45d7-9913-037ab30e4c26.gif "d7b135f6-ec7d-45d7-9913-037ab30e4c26")|Activité d'écoute : activité qui enregistre les suivis relatifs à un écouteur. À l'intérieur de cette activité, vous pouvez consulter des informations et des demandes de connexion relatives à l'écouteur.|
|![Activité Recevoir des octets](./media/2f628580-b80f-45a7-925b-616c96426c0e.gif "2f628580-b80f-45a7-925b-616c96426c0e")|Activité Recevoir des octets : activité qui regroupe toutes les traces en rapport avec les octets entrants et sortants sur une connexion entre deux points de terminaison. Cette activité est essentielle pour la corrélation avec les activités de transport qui propagent leur ID d'activité tel que http.sys. Les erreurs de connexion telles que les abandons apparaîtront dans cette activité.|
|![Activité de traitement de message](./media/wcfc-executionactivityiconc.GIF "wcfc_ExecutionActivityIconc")|Activité traiter le message : activité qui regroupe les traces associées à la création d’un message WCF. Les erreurs dues à une mauvaise enveloppe ou à un message erroné apparaîtront dans cette activité. À l'intérieur de cette activité, vous pouvez contrôler les en-têtes de message à afficher si un ID d'activité a été propagé à partir de l'appelant. Si cela se vérifie, lors du transfert vers l'activité Traiter l'action (l'icône suivante), vous pouvez également assigner à cette activité l'ID d'activité propagé pour la corrélation entre l'appelant et les suivis d'appelé.|
|![Suivi du journal des messages](./media/7c66e994-2476-4260-a0db-98948b9af197.gif "7c66e994-2476-4260-a0db-98948b9af197")|Activité traiter l’action : activité qui regroupe toutes les traces associées à une demande WCF entre deux points de terminaison. Si `propagateActivity` a la valeur `true` sur les deux points de terminaison de la configuration, tous les suivis des deux points de terminaison sont fusionnés au sein d'une activité, à des fins de corrélation directe. Cette activité contiendra des erreurs en raison du traitement du transport ou de la sécurité, au niveau de la limite du code utilisateur (si une réponse existe).|
|![Activité de traitement de message](./media/wcfc-executionactivityiconc.GIF "wcfc_ExecutionActivityIconc")|Activité Exécuter le code utilisateur : activité qui regroupe les suivis de code utilisateur pour le traitement d'une demande.|

## <a name="troubleshooting"></a>Dépannage

Si vous n’êtes pas autorisé à écrire dans le registre, vous recevez le message d’erreur suivant : « Microsoft Service Trace Viewer n’a pas été inscrit au système » lorsque vous utilisez la `svctraceviewer /register` commande «» pour inscrire l’outil. Si cela se produit, vous devez vous connecter en utilisant un compte qui possède un accès en écriture au registre.

De plus, l'outil Service Trace Viewer écrit certains paramètres (par exemple, filtres personnalisés et options du filtre) dans le fichier SvcTraceViewer.exe., dans son dossier assembly. Si vous ne disposez pas d'une autorisation de lecture pour le fichier, vous pouvez malgré tout lancer l'outil, mais vous ne pouvez pas charger les paramètres.

Si le message d'erreur « Une erreur inconnue s'est produite lors du traitement d'un ou de plusieurs suivis. » lors de l'ouverture du fichier .etl, cela signifie que le format du fichier .etl n'est pas valide.

Si vous ouvrez un journal des suivis créé à l'aide d'un système d'exploitation arabe, vous pouvez remarquer que le filtre temporel ne fonctionne pas. Par exemple, l'année 2005 correspond à année 1427 dans le calendrier arabe. Toutefois, la plage temporelle prise en charge par le filtre de l'outil Service Trace Viewer ne prend pas en charge de date antérieure à 1752. Cela peut vous empêcher de sélectionner une date correcte dans le filtre. Pour résoudre ce problème, vous pouvez créer un filtre personnalisé (**affichage/filtres personnalisés**) à l’aide d’une expression XPath pour inclure une plage de temps spécifique.

## <a name="see-also"></a>Voir aussi

- [Utilisation de Service Trace Viewer pour afficher les suivis corrélés et résoudre les problèmes](./diagnostics/tracing/using-service-trace-viewer-for-viewing-correlated-traces-and-troubleshooting.md)
- [Configuration du traçage](./diagnostics/tracing/configuring-tracing.md)
- [Suivi de bout en bout](./diagnostics/tracing/end-to-end-tracing.md)
