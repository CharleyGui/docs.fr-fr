---
title: Concepts de base de l’application Windows Forms
ms.date: 07/20/2015
helpviewer_keywords:
- Windows applications
- Windows Forms, Visual Basic
ms.assetid: 0b919d30-7fd6-42db-85c8-543d15312441
ms.openlocfilehash: 1aa1edf0130e388c6cc87662d83591f41a8e2325
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74349166"
---
# <a name="windows-forms-application-basics-visual-basic"></a>Concepts de base de l'application Windows Forms (Visual Basic)

Une partie importante de Visual Basic est la possibilité de créer des applications Windows Forms qui s’exécutent localement sur les ordinateurs des utilisateurs. Vous pouvez utiliser Visual Studio pour créer l’application et l’interface utilisateur à l’aide de Windows Forms. Une application Windows Forms repose sur des classes de l' <xref:System.Windows.Forms> espace de noms.

## <a name="designing-windows-forms-applications"></a>Conception d’applications Windows Forms

Vous pouvez créer des Windows Forms et des applications de service Windows avec Visual Studio. Pour plus d'informations, voir les rubriques suivantes :

- [Prise en main avec Windows Forms](../../../framework/winforms/getting-started-with-windows-forms.md). Fournit des informations sur la façon de créer et de programmer des Windows Forms.

- [Contrôles Windows Forms](../../../framework/winforms/controls/index.md). Collection de rubriques détaillant l’utilisation des contrôles Windows Forms.

- [Applications de service Windows](../../../framework/windows-services/index.md). Répertorie les rubriques qui expliquent comment créer des services Windows.

## <a name="building-rich-interactive-user-interfaces"></a>Création d'interfaces utilisateur interactives et enrichies

Windows Forms est le composant de client intelligent de l' .NET Framework, un ensemble de bibliothèques managées qui permettent des tâches d’application courantes telles que la lecture et l’écriture dans le système de fichiers. À l’aide d’un environnement de développement tel que Visual Studio, vous pouvez créer des applications Windows Forms qui affichent des informations, demandent une entrée d’utilisateurs et communiquent avec des ordinateurs distants sur un réseau.

Dans Windows Forms, un formulaire est une surface visuelle sur laquelle vous présentez des informations à l'utilisateur. Vous générez généralement des applications Windows Forms en plaçant des contrôles sur des formulaires et en développant des réponses aux actions de l’utilisateur, telles que des clics de souris ou des frappes de touches. Un *contrôle* est un élément d’interface utilisateur discret qui affiche des données ou accepte l’entrée de données.

### <a name="events"></a>Événements

Lorsqu’un utilisateur effectue une opération sur votre formulaire ou sur l’un de ses contrôles, il génère un événement. Votre application réagit à ces événements en exécutant du code et traite les événements quand ils se produisent. Pour plus d’informations, consultez [Création de gestionnaires d’événements dans les Windows Forms](../../../framework/winforms/creating-event-handlers-in-windows-forms.md).

### <a name="controls"></a>Contrôles

Windows Forms contient divers contrôles que vous pouvez placer sur les formulaires : les contrôles qui affichent des zones de texte, des boutons, des zones déroulantes, des cases d’option et même des pages Web. Pour obtenir la liste de tous les contrôles que vous pouvez utiliser sur un formulaire, consultez [Contrôles à utiliser dans les Windows Forms](../../../framework/winforms/controls/controls-to-use-on-windows-forms.md). Si un contrôle existant ne répond pas à vos besoins, Windows Forms prend également en charge la création de vos propres contrôles personnalisés à l'aide de la classe <xref:System.Windows.Forms.UserControl>.

Windows Forms offre des contrôles d’interface utilisateur enrichis qui émulent les fonctionnalités des applications haut de gamme telles que Microsoft Office. À l' <xref:System.Windows.Forms.ToolStrip> aide <xref:System.Windows.Forms.MenuStrip> du contrôle et, vous pouvez créer des barres d’outils et des menus qui contiennent du texte et des images, afficher des sous-menus et héberger d’autres contrôles tels que des zones de texte et des zones de liste déroulante.

Avec le concepteur de formulaires glisser-déplacer de Visual Studio, vous pouvez facilement créer des applications Windows Forms : sélectionnez simplement les contrôles avec votre curseur et placez-les là où vous le souhaitez dans le formulaire. Le concepteur fournit des outils tels que des quadrillages et des « lignes d’alignement » pour éliminer l’alignement des contrôles. Et si vous utilisez Visual Studio ou compilez sur la ligne de commande, vous <xref:System.Windows.Forms.FlowLayoutPanel>pouvez <xref:System.Windows.Forms.TableLayoutPanel> utiliser <xref:System.Windows.Forms.SplitContainer> les contrôles, et pour créer des dispositions de formulaire avancées avec un minimum de temps et d’efforts.

### <a name="custom-ui-elements"></a>Éléments d’interface utilisateur personnalisés

Enfin, si vous devez créer vos propres éléments d’interface utilisateur personnalisés <xref:System.Drawing> , l’espace de noms contient toutes les classes dont vous avez besoin pour restituer des lignes, des cercles et d’autres formes directement sur un formulaire.

Pour obtenir des informations pas à pas sur l’utilisation de ces fonctionnalités, consultez les rubriques d’aide suivantes.

|À|Consultez|
|--------|---------|
|Créer une application de Windows Forms avec Visual Studio|[Didacticiel 1 : créer une visionneuse d’images](/visualstudio/ide/tutorial-1-create-a-picture-viewer)|
|Utiliser des contrôles sur les formulaires|[Comment : ajouter des contrôles à des Windows Forms](../../../framework/winforms/controls/how-to-add-controls-to-windows-forms.md)|
|Créer des graphiques avec<xref:System.Drawing>|[Mise en route de la programmation graphique](../../../framework/winforms/advanced/getting-started-with-graphics-programming.md)|
|Créer des contrôles personnalisés|[Comment : hériter de la classe UserControl](../../../framework/winforms/controls/how-to-inherit-from-the-usercontrol-class.md)|

## <a name="displaying-and-manipulating-data"></a>Affichage et manipulation de données

De nombreuses applications doivent afficher des données provenant d’une base de données, d’un fichier XML, d’un service web XML ou autre source de données. Windows Forms fournit un contrôle flexible appelé le <xref:System.Windows.Forms.DataGridView> contrôle pour le rendu de ces données tabulaires dans un format de ligne et de colonne traditionnel, de sorte que chaque élément de données occupe sa propre cellule. À <xref:System.Windows.Forms.DataGridView> l’aide de, vous pouvez personnaliser l’apparence de chaque cellule, verrouiller des lignes et des colonnes arbitraires et afficher des contrôles complexes dans des cellules, entre autres fonctionnalités.

La connexion à des sources de données sur un réseau est une tâche simple avec les clients intelligents Windows Forms. Le <xref:System.Windows.Forms.BindingSource> composant, nouveau avec Windows Forms dans Visual Studio 2005 et le .NET Framework 2,0, représente une connexion à une source de données et expose des méthodes pour lier des données aux contrôles, naviguer vers les enregistrements précédents et suivants, modifier des enregistrements et enregistrer les modifications dans la source d’origine. Le contrôle <xref:System.Windows.Forms.BindingNavigator> fournit une interface simple sur le composant <xref:System.Windows.Forms.BindingSource> permettant aux utilisateurs de naviguer parmi les enregistrements.

### <a name="data-bound-controls"></a>Contrôles liés aux données

Vous pouvez créer facilement des contrôles liés aux données à l’aide de la fenêtre sources de données, qui affiche des sources de données telles que des bases de données, des services Web et des objets dans votre projet. Pour créer des contrôles liés aux données, vous pouvez faire glisser des éléments depuis cette fenêtre vers des formulaires dans votre projet. Vous pouvez également lier des contrôles existants à des données en faisant glisser des objets depuis la fenêtre Sources de données vers des contrôles existants.

### <a name="settings"></a>Paramètres

Les paramètres sont un autre type de liaison de données que vous pouvez gérer dans Windows Forms. La plupart des applications clientes intelligentes doivent conserver certaines informations sur leur état d’exécution, telles que la dernière taille connue des formulaires, et conserver des données de préférence utilisateur, telles que les emplacements par défaut des fichiers enregistrés. La fonctionnalité paramètres d’application répond à ces exigences en fournissant un moyen facile de stocker les deux types de paramètres sur l’ordinateur client. Une fois définis à l’aide de Visual Studio ou d’un éditeur de code, ces paramètres sont conservés au format XML et lus automatiquement en mémoire au moment de l’exécution.

Pour obtenir des informations pas à pas sur l’utilisation de ces fonctionnalités, consultez les rubriques d’aide suivantes.

|À|Consultez|
|--------|---------|
|Utiliser le <xref:System.Windows.Forms.BindingSource> composant|[Comment : lier des contrôles Windows Forms au composant BindingSource à l'aide du concepteur](../../../framework/winforms/controls/bind-wf-controls-with-the-bindingsource.md)|
|Utiliser des sources de données ADO.NET|[Comment : trier et filtrer des données ADO.NET avec le composant BindingSource Windows Forms](../../../framework/winforms/controls/sort-and-filter-ado-net-data-with-wf-bindingsource-component.md)|
|Utiliser la fenêtre sources de données|[Procédure pas à pas : affichage de données sur un Windows Form](/visualstudio/data-tools/accessing-data-in-visual-studio)|

## <a name="deploying-applications-to-client-computers"></a>Déploiement d'applications sur les ordinateurs clients

Une fois que vous avez écrit votre application, vous devez l’envoyer à vos utilisateurs afin qu’ils puissent l’installer et l’exécuter sur leurs propres ordinateurs clients. À l’aide de la technologie ClickOnce, vous pouvez déployer vos applications à partir de Visual Studio à l’aide de quelques clics et fournir aux utilisateurs une URL pointant vers votre application sur le Web. ClickOnce gère tous les éléments et dépendances dans votre application et s’assure que l’application est correctement installée sur l’ordinateur client.

Les applications ClickOnce peuvent être configurées pour s’exécuter uniquement lorsque l’utilisateur est connecté au réseau ou pour s’exécuter à la fois en ligne et hors connexion. Lorsque vous spécifiez qu’une application doit prendre en charge l’opération hors connexion, ClickOnce ajoute un lien à votre application dans le menu **Démarrer** de l’utilisateur, afin que l’utilisateur puisse l’ouvrir sans utiliser l’URL.

Quand vous mettez à jour votre application, vous publiez un nouveau manifeste de déploiement et une nouvelle copie de votre application sur votre serveur web. ClickOnce détecte qu’une mise à jour est disponible et met à niveau l’installation de l’utilisateur. aucune programmation personnalisée n’est requise pour mettre à jour les anciens assemblys.

Pour une présentation complète de ClickOnce, consultez [sécurité et déploiement ClickOnce](/visualstudio/deployment/clickonce-security-and-deployment). Pour obtenir des informations pas à pas sur l’utilisation de ces fonctionnalités, consultez les rubriques d’aide suivantes :

|À|Consultez|
|--------|---------|
|Déployer une application avec ClickOnce|[Comment : publier une application ClickOnce à l'aide de l'Assistant Publication](/visualstudio/deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard)<br /><br /> [Procédure pas à pas : déploiement manuel d’une application ClickOnce](/visualstudio/deployment/walkthrough-manually-deploying-a-clickonce-application)|
|Mettre à jour un déploiement ClickOnce|[Comment : gérer des mises à jour pour une application ClickOnce](/visualstudio/deployment/how-to-manage-updates-for-a-clickonce-application)|
|Gérer la sécurité avec ClickOnce|[Comment : activer les paramètres de sécurité ClickOnce](/visualstudio/deployment/how-to-enable-clickonce-security-settings)|

## <a name="other-controls-and-features"></a>Autres contrôles et fonctionnalités

Il existe de nombreuses autres fonctionnalités dans Windows Forms qui simplifient et accélèrent l'implémentation des tâches courantes, par exemple la prise en charge de la création de boîtes de dialogue, de l'impression, de l'ajout d'aide et de documentation et de la localisation de votre application en plusieurs langues. En outre, Windows Forms s’appuie sur le système de sécurité fiable du .NET Framework, ce qui vous permet de publier des applications plus sécurisées pour vos clients.

Pour obtenir des informations pas à pas sur l’utilisation de ces fonctionnalités, consultez les rubriques d’aide suivantes :

|À|Consultez|
|--------|---------|
|Imprimer le contenu d’un formulaire|[Comment : imprimer des graphiques dans Windows Forms](../../../framework/winforms/advanced/how-to-print-graphics-in-windows-forms.md)<br /><br /> [Comment : imprimer un fichier texte composé de plusieurs pages dans les Windows Forms](../../../framework/winforms/advanced/how-to-print-a-multi-page-text-file-in-windows-forms.md)|
|En savoir plus sur la sécurité Windows Forms|[Vue d'ensemble de la sécurité dans les Windows Forms](../../../framework/winforms/security-in-windows-forms-overview.md)|

## <a name="see-also"></a>Voir aussi

- <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase>
- [Vue d'ensemble des Windows Forms](../../../framework/winforms/windows-forms-overview.md)
- [My.Forms, objet](../../../visual-basic/language-reference/objects/my-forms-object.md)
