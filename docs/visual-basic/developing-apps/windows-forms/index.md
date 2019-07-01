---
title: Concepts de base de l'application Windows Forms (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- Windows applications
- Windows Forms, Visual Basic
ms.assetid: 0b919d30-7fd6-42db-85c8-543d15312441
ms.openlocfilehash: dd3385d6459199d56f74abfb1b8e0e218a2adf78
ms.sourcegitcommit: 2d42b7ae4252cfe1232777f501ea9ac97df31b63
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2019
ms.locfileid: "67487789"
---
# <a name="windows-forms-application-basics-visual-basic"></a>Concepts de base de l'application Windows Forms (Visual Basic)
Une partie importante de Visual Basic est la possibilité de créer des applications Windows Forms qui s’exécutent localement sur les ordinateurs des utilisateurs. Vous pouvez utiliser Visual Studio pour créer l’interface utilisateur et d’applications à l’aide de Windows Forms. Une application Windows Forms repose sur les classes de le <xref:System.Windows.Forms> espace de noms.  
  
## <a name="designing-windows-forms-applications"></a>Conception de Windows Forms Applications  
 Vous pouvez créer des Windows Forms et applications de service Windows avec Visual Studio. Pour plus d’informations, consultez les rubriques suivantes :  
  
- [Bien démarrer avec Windows Forms](../../../framework/winforms/getting-started-with-windows-forms.md). Fournit des informations sur la façon de créer et programmer des Windows Forms.  
   
- [Les contrôles Windows Forms](../../../framework/winforms/controls/index.md). Collection de rubriques détaillant l’utilisation de contrôles Windows Forms.  
  
- [Applications de Service Windows](../../../framework/windows-services/index.md). Répertorie les rubriques qui expliquent comment créer des services Windows.  
  
## <a name="building-rich-interactive-user-interfaces"></a>Création d'interfaces utilisateur interactives et enrichies  
 Windows Forms est le composant client intelligent du .NET Framework, un ensemble de bibliothèques gérées qui activent des tâches d’application courantes telles que lire et écrire dans le système de fichiers. À l’aide d’un environnement de développement tels que Visual Studio, vous pouvez créer des applications Windows Forms qui affichent des informations, demandent des entrées d’utilisateurs et communiquent avec des ordinateurs distants sur un réseau.  
  
 Dans les Windows Forms, un formulaire est une surface visuelle sur laquelle vous affichez des informations à l’utilisateur. Généralement, vous générez des applications Windows Forms en plaçant les contrôles de formulaires et développer des réponses aux actions de l’utilisateur, telles que les clics de souris ou des pressions de touches. Un *contrôle* est un élément d’interface utilisateur discret qui affiche des données ou accepte l’entrée de données.  
  
### <a name="events"></a>Événements  
 Lorsqu’un utilisateur modifie un formulaire ou l’un de ses contrôles, il génère un événement. Votre application réagit à ces événements en exécutant du code et traite les événements quand ils se produisent. Pour plus d’informations, consultez [Création de gestionnaires d’événements dans les Windows Forms](../../../framework/winforms/creating-event-handlers-in-windows-forms.md).  
  
### <a name="controls"></a>Contrôles  
 Windows Forms contient divers contrôles que vous pouvez placer sur les formulaires : contrôles qui affichent des zones de texte, boutons, listes déroulantes, cases d’option et même des pages Web. Pour obtenir la liste de tous les contrôles que vous pouvez utiliser sur un formulaire, consultez [Contrôles à utiliser dans les Windows Forms](../../../framework/winforms/controls/controls-to-use-on-windows-forms.md). Si un contrôle existant ne répond pas à vos besoins, Windows Forms prend également en charge la création de vos propres contrôles personnalisés à l'aide de la classe <xref:System.Windows.Forms.UserControl>.  
  
 Windows Forms offre des contrôles d’interface utilisateur enrichis qui émulent les fonctionnalités des applications haut de gamme telles que Microsoft Office. À l’aide de la <xref:System.Windows.Forms.ToolStrip> et <xref:System.Windows.Forms.MenuStrip> contrôle, vous pouvez créer barres d’outils et les menus qui contiennent du texte et des images, affichent des sous-menus et hébergent d’autres contrôles tels que les zones de texte et des zones de liste déroulante.  
  
 Avec le Concepteur de formulaires de glisser-déplacer de Visual Studio, vous pouvez facilement créer des applications Windows Forms : sélectionnez simplement les contrôles avec votre curseur et placez-les où vous voulez sur le formulaire. Le concepteur fournit des outils tels que les lignes de la grille et les « repères d’alignement » pour simplifier l’alignement des contrôles. Et si vous utilisez Visual Studio ou que vous compilez sur la ligne de commande, vous pouvez utiliser la <xref:System.Windows.Forms.FlowLayoutPanel>, <xref:System.Windows.Forms.TableLayoutPanel> et <xref:System.Windows.Forms.SplitContainer> dispositions avec un minimum de temps et d’efforts de formulaire de contrôles pour créer des avancées.  
  
### <a name="custom-ui-elements"></a>Éléments d’interface utilisateur personnalisée  
 Enfin, si vous devez créer vos propres éléments d’interface utilisateur personnalisées, le <xref:System.Drawing> espace de noms contient toutes les classes nécessaires pour rendre des lignes, des cercles et autres formes directement sur un formulaire.  
  
 Pour obtenir des informations détaillées sur l’utilisation de ces fonctionnalités, consultez les rubriques d’aide suivantes.  
  
|À|Voir|  
|--------|---------|  
|Créer une application Windows Forms avec Visual Studio|[Tutoriel 1 : Créer une visionneuse d’images](/visualstudio/ide/tutorial-1-create-a-picture-viewer)|  
|Utiliser des contrôles sur des formulaires|[Guide pratique pour Ajouter des contrôles aux Windows Forms](../../../framework/winforms/controls/how-to-add-controls-to-windows-forms.md)|   
|Créer des graphismes avec <xref:System.Drawing>|[Mise en route de la programmation graphique](../../../framework/winforms/advanced/getting-started-with-graphics-programming.md)|  
|Créer des contrôles personnalisés|[Guide pratique pour Hériter de la classe UserControl](../../../framework/winforms/controls/how-to-inherit-from-the-usercontrol-class.md)|  
  
## <a name="displaying-and-manipulating-data"></a>Affichage et manipulation de données  
 De nombreuses applications doivent afficher des données provenant d’une base de données, d’un fichier XML, d’un service web XML ou autre source de données. Windows Forms fournit un contrôle flexible nommé le <xref:System.Windows.Forms.DataGridView> contrôle pour afficher les données tabulaires dans un format de ligne et de colonne classique, afin que chaque élément de données occupe sa propre cellule. À l’aide de <xref:System.Windows.Forms.DataGridView> vous pouvez personnaliser l’apparence des cellules individuelles, verrouiller des lignes et colonnes en place arbitraires et afficher des contrôles complexes dans les cellules, entre autres fonctionnalités.  
  
 La connexion à des sources de données sur un réseau est une tâche simple avec les clients intelligents Windows Forms. Le <xref:System.Windows.Forms.BindingSource> composant, nouveau avec les formulaires de Windows dans Visual Studio 2005 et .NET Framework 2.0, représente une connexion à une source de données et expose des méthodes pour lier des données aux contrôles, naviguer vers les enregistrements précédents et suivants, modifier les enregistrements, et enregistrement des modifications à la source d’origine. Le contrôle <xref:System.Windows.Forms.BindingNavigator> fournit une interface simple sur le composant <xref:System.Windows.Forms.BindingSource> permettant aux utilisateurs de naviguer parmi les enregistrements.  
  
### <a name="data-bound-controls"></a>Contrôles liés aux données  
 Vous pouvez créer des contrôles liés aux données facilement à l’aide de la fenêtre Sources de données, qui affiche les sources de données telles que les bases de données, des services Web et des objets dans votre projet. Pour créer des contrôles liés aux données, vous pouvez faire glisser des éléments depuis cette fenêtre vers des formulaires dans votre projet. Vous pouvez également lier des contrôles existants à des données en faisant glisser des objets depuis la fenêtre Sources de données vers des contrôles existants.  
  
### <a name="settings"></a>Paramètres  
 Un autre type de liaison de données que vous pouvez gérer dans les Windows Forms est paramètres. La plupart des applications smart client doivent conserver des informations sur leur état d’exécution, telles que la dernière taille connue des formulaires et conserver les données de préférence de l’utilisateur, telles que les emplacements par défaut pour les fichiers enregistrés. La fonctionnalité paramètres de l’application répond à ces exigences en offrant un moyen facile de stocker les deux types de paramètres sur l’ordinateur client. Une fois définis à l’aide de Visual Studio ou un éditeur de code, ces paramètres sont conservés au format XML et lus automatiquement en mémoire au moment de l’exécution.  
  
 Pour obtenir des informations détaillées sur l’utilisation de ces fonctionnalités, consultez les rubriques d’aide suivantes.  
  
|À|Voir|  
|--------|---------|  
|Utilisez le <xref:System.Windows.Forms.BindingSource> composant|[Guide pratique pour Lier des contrôles Windows Forms au composant BindingSource à l’aide du Concepteur](../../../framework/winforms/controls/bind-wf-controls-with-the-bindingsource.md)|  
|Utiliser des sources de données ADO.NET|[Guide pratique pour Trier et filtrer des données ADO.NET avec les Windows Forms composant BindingSource](../../../framework/winforms/controls/sort-and-filter-ado-net-data-with-wf-bindingsource-component.md)|
|Utiliser la fenêtre Sources de données|[Procédure pas à pas : Affichage de données sur un formulaire Windows](/visualstudio/data-tools/accessing-data-in-visual-studio)|  
  
## <a name="deploying-applications-to-client-computers"></a>Déploiement d'applications sur les ordinateurs clients  
 Une fois que vous avez écrit votre application, vous devez l’envoyer à vos utilisateurs afin qu’ils peuvent installer et exécuter sur leurs propres ordinateurs clients. À l’aide de la technologie ClickOnce, vous pouvez déployer vos applications depuis Visual Studio à l’aide de quelques clics et fournir aux utilisateurs une URL pointant vers votre application sur le Web. ClickOnce gère tous les éléments et dépendances dans votre application et s’assure que l’application est correctement installée sur l’ordinateur client.  
  
 Applications ClickOnce peuvent être configurées pour s’exécuter uniquement quand l’utilisateur est connecté au réseau, ou pour s’exécuter à la fois en ligne et hors connexion. Lorsque vous spécifiez qu’une application doit prendre en charge une opération hors connexion, ClickOnce ajoute un lien à votre application de l’utilisateur **Démarrer** menu, afin que l’utilisateur puisse l’ouvrir sans utiliser l’URL.  
  
 Quand vous mettez à jour votre application, vous publiez un nouveau manifeste de déploiement et une nouvelle copie de votre application sur votre serveur web. ClickOnce détecte qu’il est une mise à jour disponible et met à niveau d’installation de l’utilisateur ; aucune programmation personnalisée n’est nécessaire pour mettre à jour les anciens assemblys.  
  
 Pour une introduction complète à ClickOnce, consultez [ClickOnce Security and Deployment](/visualstudio/deployment/clickonce-security-and-deployment). Pour obtenir des informations détaillées sur l’utilisation de ces fonctionnalités, consultez les rubriques d’aide suivantes :  
  
|À|Voir|  
|--------|---------|  
|Déployer une application avec ClickOnce|[Guide pratique pour publier une application ClickOnce à l’aide de l’Assistant Publication](/visualstudio/deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard)<br /><br /> [Procédure pas à pas : déploiement manuel d'une application ClickOnce](/visualstudio/deployment/walkthrough-manually-deploying-a-clickonce-application)|  
|Mettre à jour un déploiement ClickOnce|[Guide pratique pour gérer les mises à jour d’une application ClickOnce](/visualstudio/deployment/how-to-manage-updates-for-a-clickonce-application)|  
|Gérer la sécurité avec ClickOnce|[Guide pratique pour activer les paramètres de sécurité ClickOnce](/visualstudio/deployment/how-to-enable-clickonce-security-settings)|  
  
## <a name="other-controls-and-features"></a>Autres contrôles et fonctionnalités  
 Il existe de nombreuses autres fonctionnalités dans Windows Forms qui simplifient et accélèrent l'implémentation des tâches courantes, par exemple la prise en charge de la création de boîtes de dialogue, de l'impression, de l'ajout d'aide et de documentation et de la localisation de votre application en plusieurs langues. En outre, Windows Forms repose sur le système de sécurité robuste du .NET Framework, ce qui vous permet de publier des applications plus sécurisées à vos clients.  
  
 Pour obtenir des informations détaillées sur l’utilisation de ces fonctionnalités, consultez les rubriques d’aide suivantes :  
  
|À|Voir|  
|--------|---------|  
|Imprimer le contenu d’un formulaire|[Guide pratique pour Imprimer des graphiques dans les Windows Forms](../../../framework/winforms/advanced/how-to-print-graphics-in-windows-forms.md)<br /><br /> [Guide pratique pour Imprimer un fichier texte de plusieurs pages dans les Windows Forms](../../../framework/winforms/advanced/how-to-print-a-multi-page-text-file-in-windows-forms.md)|   
|En savoir plus sur la sécurité Windows Forms|[Vue d’ensemble de la sécurité dans les Windows Forms](../../../framework/winforms/security-in-windows-forms-overview.md)|  
  
## <a name="see-also"></a>Voir aussi

- <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase>
- [Vue d'ensemble des Windows Forms](../../../framework/winforms/windows-forms-overview.md)
- [My.Forms (objet)](../../../visual-basic/language-reference/objects/my-forms-object.md)
