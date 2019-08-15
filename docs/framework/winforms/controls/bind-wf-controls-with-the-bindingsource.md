---
title: 'Procédure : lier des contrôles Windows Forms au composant BindingSource à l’aide du concepteur'
ms.date: 03/30/2017
helpviewer_keywords:
- controls [Windows Forms], binding
- BindingSource component [Windows Forms], binding controls
- data binding [Windows Forms], BindingSource component
ms.assetid: 391ae170-de5c-40f8-8233-91cb2ee4683a
ms.openlocfilehash: 180fafa9ace5927fd84ec5dc0a1b2a342f771efd
ms.sourcegitcommit: cf9515122fce716bcfb6618ba366e39b5a2eb81e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/15/2019
ms.locfileid: "69040015"
---
# <a name="how-to-bind-windows-forms-controls-with-the-bindingsource-component-using-the-designer"></a>Procédure : lier des contrôles Windows Forms au composant BindingSource à l’aide du concepteur
Une fois que vous avez ajouté des contrôles à votre formulaire et déterminé l’interface utilisateur de votre application, vous pouvez lier les contrôles à une source de données, de sorte qu’au moment de l’exécution, les utilisateurs puissent modifier et enregistrer des données relatives à l’application.

 La liaison d’un contrôle ou d’une série de contrôles dans Windows Forms est plus <xref:System.Windows.Forms.BindingSource> facile à effectuer à l’aide du contrôle comme un pont entre les contrôles sur le formulaire et la source de données.

 Un ou plusieurs contrôles d’un formulaire peuvent être liés à des données; dans la procédure suivante, un <xref:System.Windows.Forms.TextBox> contrôle est lié à une source de données.

 Pour terminer la procédure, il est supposé que vous allez établir une liaison avec une source de données dérivée d’une base de données. Pour plus d’informations sur la création de sources de données à partir d’autres magasins de données, consultez [ajouter de nouvelles sources de données](/visualstudio/data-tools/add-new-data-sources).

## <a name="to-bind-a-control-at-design-time"></a>Pour lier un contrôle au moment du design

1. Faites glisser <xref:System.Windows.Forms.TextBox> un contrôle sur le formulaire.

2. Dans la fenêtre **Propriétés** :

    1. Développez le nœud **(DataBindings)** .

    2. Cliquez sur la flèche en regard <xref:System.Windows.Forms.TextBox.Text%2A> de la propriété.

         L’éditeur de types de l’interface utilisateur **DataSource** s’ouvre.

         Si une source de données a déjà été configurée pour le projet ou le formulaire, elle s’affiche.

3. Cliquez sur **Ajouter la source de données du projet** pour vous connecter aux données et créer une source de données.

4. Sur la page d’accueil de l’**Assistant Configuration de source de données**, cliquez sur **Suivant**.

5. Dans la page **choisir un type de source de données** , sélectionnez **base de**données.

6. Sur la page **choisir votre connexion de données** , sélectionnez une connexion de données dans la liste des connexions disponibles. Si la connexion de données souhaitée n’est pas disponible, sélectionnez **nouvelle connexion** pour créer une nouvelle connexion de données.

7. Sélectionnez **Oui, enregistrer la connexion** pour enregistrer la chaîne de connexion dans le fichier de configuration de l’application.

8. Sélectionnez les objets de base de données à mettre dans votre application. Dans ce cas, sélectionnez un champ dans une table que vous <xref:System.Windows.Forms.TextBox> souhaitez afficher.

9. Remplacez le nom du jeu de données par défaut, si vous le souhaitez.

10. Cliquez sur **Terminer**.

11. Dans la fenêtre **Propriétés** , cliquez à nouveau sur la flèche <xref:System.Windows.Forms.TextBox.Text%2A> à côté de la propriété. Dans l’éditeur de types d’interface utilisateur **DataSource** , sélectionnez le nom du champ <xref:System.Windows.Forms.TextBox> auquel vous souhaitez lier.

     L’éditeur de type d’interface utilisateur **DataSource** se ferme et <xref:System.Windows.Forms.BindingSource> le jeu de données, et l’adaptateur de table propre à cette connexion de données sont ajoutés à votre formulaire.

## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Forms.BindingSource>
- <xref:System.Windows.Forms.BindingNavigator>
- [Ajouter de nouvelles sources de données](/visualstudio/data-tools/add-new-data-sources)
- [Fenêtre sources de données](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/6ckyxa83(v=vs.120))
