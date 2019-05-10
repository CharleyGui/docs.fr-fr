---
title: Vue d'ensemble des Windows Forms
ms.date: 03/30/2017
helpviewer_keywords:
- smart clients
- Windows Forms, about Windows Forms
ms.assetid: 3a2b6284-c8d6-4e1c-8c69-0bed38f38cd4
ms.openlocfilehash: 5eee8b4b046bd4d3f9c71b692f4bac3dd6bcea2c
ms.sourcegitcommit: 0d0a6e96737dfe24d3257b7c94f25d9500f383ea
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/07/2019
ms.locfileid: "65211785"
---
# <a name="windows-forms-overview"></a>Vue d’ensemble des Windows Forms

La présentation suivante décrit les avantages offerts par les applications Smart Client, les principales fonctionnalités de programmation Windows Forms et comment utiliser Windows Forms pour générer des clients intelligents qui répondent aux besoins des utilisateurs finaux et des entreprises d’aujourd’hui.

## <a name="windows-forms-and-smart-client-apps"></a>Windows Forms et des applications de client intelligent

 Avec Windows Forms, vous pouvez développer des clients intelligents (Smart Clients). Les *clients intelligents* sont des applications enrichies du point de vue graphique, faciles à déployer et à mettre à jour, pouvant fonctionner même si elles ne sont pas connectées à Internet et pouvant accéder aux ressources sur l’ordinateur local de façon plus sécurisée que les applications Windows traditionnelles.

### <a name="build-rich-interactive-user-interfaces"></a>Créer des interfaces utilisateur riches et interactives

 Windows Forms est une technologie Smart Client pour [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)], un ensemble de bibliothèques managées qui simplifient les tâches d'application courantes telles que la lecture et l'écriture dans le système de fichiers. Lorsque vous utilisez un environnement de développement tels que Visual Studio, vous pouvez créer des applications clients intelligents Windows Forms qui affichent des informations, demandent des entrées d’utilisateurs et communiquent avec des ordinateurs distants sur un réseau.

 Dans Windows Forms, un *formulaire* est une surface visuelle sur laquelle vous présentez des informations à l’utilisateur. Habituellement, vous générez des applications Windows Forms en ajoutant des contrôles à des formulaires et en développant des réponses aux actions de l’utilisateur, telles que des clics de souris ou des pressions sur des touches du clavier. Un *contrôle* est un élément d’interface utilisateur discret qui affiche des données ou accepte l’entrée de données.

 Quand un utilisateur modifie un formulaire ou l'un de ses contrôles, l'action génère un événement. Votre application réagit à ces événements en exécutant du code et traite les événements quand ils se produisent. Pour plus d’informations, consultez [Création de gestionnaires d’événements dans les Windows Forms](creating-event-handlers-in-windows-forms.md).

 Windows Forms contient divers contrôles que vous pouvez ajouter aux formulaires : des contrôles qui affichent des zones de texte, des boutons, des listes déroulantes, des cases d’option et même des pages web. Pour obtenir la liste de tous les contrôles que vous pouvez utiliser sur un formulaire, consultez [Contrôles à utiliser dans les Windows Forms](./controls/controls-to-use-on-windows-forms.md). Si un contrôle existant ne répond pas à vos besoins, Windows Forms prend également en charge la création de vos propres contrôles personnalisés à l'aide de la classe <xref:System.Windows.Forms.UserControl>.

 Windows Forms offre des contrôles d’interface utilisateur enrichis qui émulent les fonctionnalités des applications haut de gamme telles que Microsoft Office. Quand vous utilisez les contrôles <xref:System.Windows.Forms.ToolStrip> et <xref:System.Windows.Forms.MenuStrip>, vous pouvez créer des barres d'outils et des menus qui contiennent du texte et des images, qui affichent des sous-menus et qui hébergent d'autres contrôles tels que des zones de texte et des zones de liste déroulante.

 Avec le glisser-déplacer **Windows Forms Designer** dans Visual Studio, vous pouvez facilement créer des applications Windows Forms. Il vous suffit de sélectionner les contrôles avec votre curseur et de les ajouter à l'emplacement souhaité sur le formulaire. Le concepteur fournit des outils tels que des quadrillages et des lignes d'alignement pour simplifier l'alignement des contrôles. Et si vous utilisez Visual Studio ou que vous compilez sur la ligne de commande, vous pouvez utiliser la <xref:System.Windows.Forms.FlowLayoutPanel>, <xref:System.Windows.Forms.TableLayoutPanel> et <xref:System.Windows.Forms.SplitContainer> dispositions de formulaire de contrôles pour créer des avancées en moins de temps.

 Pour finir, si vous devez créer vos propres éléments d'interface utilisateur personnalisés, l'espace de noms <xref:System.Drawing> contient une large sélection de classes pour afficher des lignes, des cercles et autres formes directement sur un formulaire.

> [!NOTE]
> Les contrôles Windows Forms ne sont pas conçus pour être marshalés entre des domaines d’application. Pour cette raison, Microsoft ne prend pas en charge le passage d'un contrôle Windows Forms à travers une frontière <xref:System.AppDomain>, même si le type de base <xref:System.Windows.Controls.Control> de <xref:System.MarshalByRefObject> semble indiquer que cela est possible. Les applications Windows Forms qui ont plusieurs domaines d’application sont prises en charge tant qu’aucun contrôle Windows Forms ne franchit les frontières des domaines d’applications.

#### <a name="create-forms-and-controls"></a>Créer des formulaires et contrôles

Pour obtenir des informations détaillées sur l'utilisation de ces fonctionnalités, consultez les rubriques d'aide suivantes.

|Description|Rubrique d'aide|
|-----------------|----------------|
|Utilisation de contrôles sur des formulaires|[Guide pratique pour Ajouter des contrôles aux Windows Forms](./controls/how-to-add-controls-to-windows-forms.md)|
|Utilisation du contrôle <xref:System.Windows.Forms.ToolStrip>|[Guide pratique pour Créer un ToolStrip de base avec des éléments Standard à l’aide du Concepteur](./controls/create-a-basic-wf-toolstrip-with-standard-items-using-the-designer.md)|
|Création de graphismes avec <xref:System.Drawing>|[Mise en route de la programmation graphique](./advanced/getting-started-with-graphics-programming.md)|
|Création de contrôles personnalisés|[Guide pratique pour Hériter de la classe UserControl](./controls/how-to-inherit-from-the-usercontrol-class.md)|

### <a name="display-and-manipulate-data"></a>Afficher et manipuler des données
 De nombreuses applications doivent afficher des données provenant d’une base de données, d’un fichier XML, d’un service web XML ou autre source de données. Windows Forms fournit un contrôle flexible, nommé <xref:System.Windows.Forms.DataGridView>, pour afficher ces données tabulaires dans un format classique avec des lignes et des colonnes où chaque élément de données occupe sa propre cellule. Quand vous utilisez <xref:System.Windows.Forms.DataGridView>, vous pouvez personnaliser l'apparence de chaque cellule, verrouiller des lignes et des colonnes arbitraires et afficher des contrôles complexes dans des cellules, entre autres fonctionnalités.

 La connexion à des sources de données sur un réseau est une tâche simple avec les clients intelligents Windows Forms. Le <xref:System.Windows.Forms.BindingSource> composant représente une connexion à une source de données et expose des méthodes pour lier des données aux contrôles, naviguer vers les enregistrements précédents et suivants, modifier les enregistrements et enregistrer les modifications dans la source d’origine. Le contrôle <xref:System.Windows.Forms.BindingNavigator> fournit une interface simple sur le composant <xref:System.Windows.Forms.BindingSource> permettant aux utilisateurs de naviguer parmi les enregistrements.

 Vous pouvez facilement créer des contrôles liés aux données à l'aide de la fenêtre Sources de données. Cette fenêtre affiche des sources de données telles que les bases de données, les services web et les objets dans votre projet. Pour créer des contrôles liés aux données, vous pouvez faire glisser des éléments depuis cette fenêtre vers des formulaires dans votre projet. Vous pouvez également lier des contrôles existants à des données en faisant glisser des objets depuis la fenêtre Sources de données vers des contrôles existants.

 Les *paramètres* sont un autre type de liaison de données que vous pouvez gérer dans Windows Forms. La plupart des applications Smart Client doivent conserver certaines informations sur leur état d'exécution, telles que la dernière taille connue des formulaires, et conserver des données de préférence utilisateur, telles que les emplacements par défaut des fichiers enregistrés. La fonctionnalité Paramètres d'application répond à ces exigences en offrant un mécanisme simple de stockage des deux types de paramètres sur l'ordinateur client. Après avoir défini ces paramètres à l’aide de Visual Studio ou un éditeur de code, les paramètres sont conservés au format XML et lus automatiquement en mémoire au moment de l’exécution.

#### <a name="display-and-manipulate-data"></a>Afficher et manipuler des données

Pour obtenir des informations détaillées sur l'utilisation de ces fonctionnalités, consultez les rubriques d'aide suivantes.

|Description|Rubrique d'aide|
|-----------------|----------------|
|Utilisation du composant <xref:System.Windows.Forms.BindingSource>|[Guide pratique pour Lier des contrôles Windows Forms au composant BindingSource à l’aide du Concepteur](./controls/bind-wf-controls-with-the-bindingsource.md)|
|Utilisation de sources de données [!INCLUDE[vstecado](../../../includes/vstecado-md.md)]|[Guide pratique pour Trier et filtrer des données ADO.NET avec les Windows Forms composant BindingSource](./controls/sort-and-filter-ado-net-data-with-wf-bindingsource-component.md)|
|Utilisation de la fenêtre Sources de données|[Lier des contrôles Windows Forms à des données dans Visual Studio](/visualstudio/data-tools/bind-windows-forms-controls-to-data-in-visual-studio)|
|Utilisation des paramètres d'application|[Guide pratique pour Créer des paramètres d’Application](./advanced/how-to-create-application-settings.md)|

### <a name="deploy-apps-to-client-computers"></a>Déployer des applications sur les ordinateurs clients

Une fois que vous avez écrit votre application, vous devez l'envoyer à vos utilisateurs pour qu'ils puissent l'installer et l'exécuter sur leurs propres ordinateurs clients. Lorsque vous utilisez le [!INCLUDE[ndptecclick](../../../includes/ndptecclick-md.md)] technologie, vous pouvez déployer vos applications depuis Visual Studio à l’aide de quelques clics et fournir aux utilisateurs une URL pointant vers votre application sur le Web. [!INCLUDE[ndptecclick](../../../includes/ndptecclick-md.md)] gère tous les éléments et dépendances dans votre application et s'assure que l'application est correctement installée sur l'ordinateur client.

Vous pouvez configurer les applications [!INCLUDE[ndptecclick](../../../includes/ndptecclick-md.md)] pour qu'elles s'exécutent uniquement quand l'utilisateur est connecté au réseau ou pour qu'elles s'exécutent en ligne et hors connexion. Quand vous spécifiez qu’une application doit prendre en charge l’exécution hors connexion, [!INCLUDE[ndptecclick](../../../includes/ndptecclick-md.md)] ajoute un lien à votre application dans le menu **Démarrer** de l’utilisateur. L'utilisateur peut alors ouvrir l'application sans utiliser l'URL.

Quand vous mettez à jour votre application, vous publiez un nouveau manifeste de déploiement et une nouvelle copie de votre application sur votre serveur web. [!INCLUDE[ndptecclick](../../../includes/ndptecclick-md.md)] détectera qu'une mise à jour est disponible et mettra à niveau l'installation de l'utilisateur. Aucune programmation personnalisée n'est nécessaire pour mettre à jour les anciens assemblys.

#### <a name="deploy-clickonce-apps"></a>Déployer des applications ClickOnce

Pour obtenir une introduction complète à [!INCLUDE[ndptecclick](../../../includes/ndptecclick-md.md)], consultez [Sécurité et déploiement ClickOnce](/visualstudio/deployment/clickonce-security-and-deployment). Pour obtenir des informations détaillées sur l’utilisation de ces fonctionnalités, consultez les rubriques d’aide suivantes.

|Description|Rubrique d'aide|
|-----------------|----------------|
|Déploiement d'une application à l'aide de [!INCLUDE[ndptecclick](../../../includes/ndptecclick-md.md)]|[Guide pratique pour publier une application ClickOnce à l’aide de l’Assistant Publication](/visualstudio/deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard)<br /><br /> [Procédure pas à pas : déploiement manuel d'une application ClickOnce](/visualstudio/deployment/walkthrough-manually-deploying-a-clickonce-application)|
|Mise à jour d'un déploiement [!INCLUDE[ndptecclick](../../../includes/ndptecclick-md.md)]|[Guide pratique pour gérer les mises à jour d’une application ClickOnce](/visualstudio/deployment/how-to-manage-updates-for-a-clickonce-application)|
|Gestion de la sécurité avec [!INCLUDE[ndptecclick](../../../includes/ndptecclick-md.md)]|[Guide pratique pour activer les paramètres de sécurité ClickOnce](/visualstudio/deployment/how-to-enable-clickonce-security-settings)|

### <a name="other-controls-and-features"></a>Autres contrôles et fonctionnalités

Il existe de nombreuses autres fonctionnalités dans Windows Forms qui simplifient et accélèrent l'implémentation des tâches courantes, par exemple la prise en charge de la création de boîtes de dialogue, de l'impression, de l'ajout d'aide et de documentation et de la localisation de votre application en plusieurs langues. De plus, Windows Forms repose sur le système de sécurité fiable de [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)]. Ce système vous permet de distribuer des applications plus sécurisées à vos clients.

#### <a name="implement-other-controls-and-features"></a>Implémenter d’autres contrôles et fonctionnalités

Pour obtenir des informations détaillées sur l'utilisation de ces fonctionnalités, consultez les rubriques d'aide suivantes.

|Description|Rubrique d'aide|
|-----------------|----------------|
|Impression du contenu d'un formulaire|[Guide pratique pour Imprimer des graphiques dans les Windows Forms](./advanced/how-to-print-graphics-in-windows-forms.md)<br /><br /> [Guide pratique pour Imprimer un fichier texte de plusieurs pages dans les Windows Forms](./advanced/how-to-print-a-multi-page-text-file-in-windows-forms.md)|
|En savoir plus sur la sécurité Windows Forms|[Vue d’ensemble de la sécurité dans les Windows Forms](security-in-windows-forms-overview.md)|

## <a name="see-also"></a>Voir aussi

- [Bien démarrer avec Windows Forms](getting-started-with-windows-forms.md)
- [Création d’un nouveau Windows Form](creating-a-new-windows-form.md)
- [Vue d’ensemble du contrôle ToolStrip](./controls/toolstrip-control-overview-windows-forms.md)
- [Vue d’ensemble du contrôle DataGridView](./controls/datagridview-control-overview-windows-forms.md)
- [Vue d'ensemble du composant BindingSource](./controls/bindingsource-component-overview.md)
- [Vue d'ensemble des paramètres d'application](./advanced/application-settings-overview.md)
- [Sécurité et déploiement ClickOnce](/visualstudio/deployment/clickonce-security-and-deployment)