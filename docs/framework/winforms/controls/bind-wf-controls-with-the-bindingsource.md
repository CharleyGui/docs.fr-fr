---
title: Lier des contrôles au composant BindingSource à l’aide du concepteur
ms.date: 03/30/2017
helpviewer_keywords:
- controls [Windows Forms], binding
- BindingSource component [Windows Forms], binding controls
- data binding [Windows Forms], BindingSource component
ms.assetid: 391ae170-de5c-40f8-8233-91cb2ee4683a
ms.openlocfilehash: 35b3fb7b9884f07dd6e2aef311a01d3090c44227
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76744390"
---
# <a name="how-to-bind-windows-forms-controls-with-the-bindingsource-component-using-the-designer"></a>Comment : lier des contrôles Windows Forms au composant BindingSource à l'aide du concepteur
Une fois que vous avez ajouté des contrôles à votre formulaire et déterminé l’interface utilisateur de votre application, vous pouvez lier les contrôles à une source de données, de sorte qu’au moment de l’exécution, les utilisateurs puissent modifier et enregistrer des données relatives à l’application.

 La liaison d’un contrôle ou d’une série de contrôles dans Windows Forms s’effectue plus facilement à l’aide du contrôle <xref:System.Windows.Forms.BindingSource> en tant que pont entre les contrôles sur le formulaire et la source de données.

 Un ou plusieurs contrôles d’un formulaire peuvent être liés à des données ; dans la procédure suivante, un contrôle de <xref:System.Windows.Forms.TextBox> est lié à une source de données.

 Pour terminer la procédure, il est supposé que vous allez établir une liaison avec une source de données dérivée d’une base de données. Pour plus d’informations sur la création de sources de données à partir d’autres magasins de données, consultez [ajouter de nouvelles sources de données](/visualstudio/data-tools/add-new-data-sources).

## <a name="to-bind-a-control-at-design-time"></a>Pour lier un contrôle au moment du design

1. Faites glisser un contrôle <xref:System.Windows.Forms.TextBox> sur le formulaire.

2. Dans la fenêtre **Propriétés** :

    1. Développez le nœud **(DataBindings)** .

    2. Cliquez sur la flèche en regard de la propriété <xref:System.Windows.Forms.TextBox.Text%2A>.

         L’éditeur de types de l’interface utilisateur **DataSource** s’ouvre.

         Si une source de données a déjà été configurée pour le projet ou le formulaire, elle s’affiche.

3. Cliquez sur **Ajouter la source de données du projet** pour vous connecter aux données et créer une source de données.

4. Sur la page d’accueil de l’**Assistant Configuration de source de données**, cliquez sur **Suivant**.

5. Dans la page **choisir un type de source de données** , sélectionnez **base de**données.

6. Sur la page **choisir votre connexion de données** , sélectionnez une connexion de données dans la liste des connexions disponibles. Si la connexion de données souhaitée n’est pas disponible, sélectionnez **nouvelle connexion** pour créer une nouvelle connexion de données.

7. Sélectionnez **Oui, enregistrer la connexion** pour enregistrer la chaîne de connexion dans le fichier de configuration de l’application.

8. Sélectionnez les objets de base de données à mettre dans votre application. Dans ce cas, sélectionnez un champ dans une table que vous souhaitez afficher à l' <xref:System.Windows.Forms.TextBox>.

9. Remplacez le nom du jeu de données par défaut, si vous le souhaitez.

10. Cliquez sur **Finish**.

11. Dans la fenêtre **Propriétés** , cliquez à nouveau sur la flèche à côté de la propriété <xref:System.Windows.Forms.TextBox.Text%2A>. Dans l’éditeur de types d’interface utilisateur **DataSource** , sélectionnez le nom du champ auquel lier l' <xref:System.Windows.Forms.TextBox>.

     L’éditeur de type d’interface utilisateur **DataSource** se ferme et le jeu de données, <xref:System.Windows.Forms.BindingSource> et l’adaptateur de table propre à cette connexion de données sont ajoutés à votre formulaire.

## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Forms.BindingSource>
- <xref:System.Windows.Forms.BindingNavigator>
- [Ajouter de nouvelles sources de données](/visualstudio/data-tools/add-new-data-sources)
- [Fenêtre sources de données](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/6ckyxa83(v=vs.120))
