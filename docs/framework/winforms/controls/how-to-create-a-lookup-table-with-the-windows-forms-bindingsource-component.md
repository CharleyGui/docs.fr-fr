---
title: Créer une table de correspondance avec le composant BindingSource
ms.date: 03/30/2017
helpviewer_keywords:
- lookup tables
- tables [Windows Forms], creating lookup tables
- BindingSource component [Windows Forms], creating a lookup table
- BindingSource component [Windows Forms], examples
ms.assetid: 622fce80-879d-44be-abbf-8350ec22ca2b
ms.openlocfilehash: ccf2bfa6cf3f56a38b55f8c87004c42a46172891
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76736815"
---
# <a name="how-to-create-a-lookup-table-with-the-windows-forms-bindingsource-component"></a>Comment : créer une table de correspondance avec le composant BindingSource Windows Forms
Une table de choix est une table de données ayant une colonne qui affiche les données des enregistrements situés dans une table liée. Dans les procédures suivantes, un contrôle <xref:System.Windows.Forms.ComboBox> permet d'afficher le champ avec la relation de clé étrangère entre la table parent et la table enfant.  
  
 Pour mieux visualiser ces deux tables et cette relation, voici un exemple de table parent et de table enfant :  
  
 CustomersTable (table parent)  
  
|CustomerID|CustomerName|  
|----------------|------------------|  
|712|David Junca|  
|713|Catherine Autier|  
  
 OrdersTable (table enfant)  
  
|OrderID|OrderDate|CustomerID|  
|-------------|---------------|----------------|  
|903|12 février 2004|712|  
|904|13 février 2004|713|  
  
 Dans ce scénario, une table, CustomersTable, stocke les informations réelles que vous souhaitez afficher et enregistrer. Mais pour gagner de l'espace, la table délaisse les données qui ajoutent de la clarté. L'autre table, OrdersTable, contient uniquement des informations relatives à l'apparence, notamment l'équivalence entre le numéro d'identification du client, l'ID de date et l'ID de commande. Les noms des clients ne sont pas mentionnés.  
  
 Quatre propriétés importantes sont définies sur le contrôle [ComboBox](combobox-control-windows-forms.md) pour créer la table de choix.  
  
- La propriété <xref:System.Windows.Forms.ComboBox.DataSource%2A> contient le nom de la table.  
  
- La propriété <xref:System.Windows.Forms.ListControl.DisplayMember%2A> contient la colonne de données de la table que vous souhaitez afficher pour le texte du contrôle (nom du client).  
  
- La propriété <xref:System.Windows.Forms.ListControl.ValueMember%2A> contient la colonne de données de la table ayant les informations stockées (numéro d'identification dans la table parent).  
  
- La propriété <xref:System.Windows.Forms.ListControl.SelectedValue%2A> fournit la valeur de recherche pour la table enfant, en fonction de <xref:System.Windows.Forms.ListControl.ValueMember%2A>.  
  
 Les procédures ci-dessous vous montrent comment présenter votre formulaire sous forme de table de choix et lier les données aux contrôles qui s'y trouvent. Pour mener à bien les procédures, vous devez disposer d'une source de données avec des tables parents et des tables enfants qui ont une relation de clé étrangère, comme indiqué précédemment.  
  
### <a name="to-create-the-user-interface"></a>Pour créer l'interface utilisateur  
  
1. À partir de la **boîte à outils**, faites glisser un contrôle <xref:System.Windows.Forms.ComboBox> sur le formulaire.  
  
     Ce contrôle affiche la colonne de la table parent.  
  
2. Faites glisser d'autres contrôles pour afficher les détails de la table enfant. Le format des données de la table doit déterminer votre choix des contrôles. Pour plus d’informations, consultez [Classement par fonction des contrôles Windows Forms](windows-forms-controls-by-function.md).  
  
3. Faites glisser un contrôle <xref:System.Windows.Forms.BindingNavigator> vers le formulaire. Cela vous permettra de naviguer parmi les données de la table enfant.  
  
### <a name="to-connect-to-the-data-and-bind-it-to-controls"></a>Pour se connecter aux données et les lier aux contrôles  
  
1. Sélectionnez <xref:System.Windows.Forms.ComboBox>, puis cliquez sur le glyphe Tâche guidée pour afficher la boîte de dialogue Tâche guidée.  
  
2. Sélectionnez **Utilisez des éléments liés aux données**.  
  
3. Cliquez sur la flèche à côté de la zone de liste déroulante **Source de données**. Si une source de données a déjà été configurée pour le projet ou le formulaire, elle s'affiche. Sinon, procédez comme suit (cet exemple utilise les tables Customers et Orders de l'exemple de base de données Northwind et fait référence à celles-ci entre parenthèses).  
  
    1. Cliquez sur **Ajouter la source de données du projet** pour vous connecter aux données et créer une source de données.  
  
    2. Sur la page d’accueil de l’**Assistant Configuration de source de données**, cliquez sur **Suivant**.  
  
    3. Sélectionnez **Base de données** sur la page **Choisir un type de source de données**.  
  
    4. Sélectionnez une connexion de données dans la liste des connexions disponibles sur la page **Choisir votre connexion de données**. Si la connexion de données souhaitée n’est pas disponible, sélectionnez **Nouvelle connexion** pour créer une connexion de données.  
  
    5. Cliquez sur **Oui, enregistrer la connexion en tant que** pour enregistrer la chaîne de connexion dans le fichier de configuration de l’application.  
  
    6. Sélectionnez les objets de base de données à mettre dans votre application. Dans le cas présent, sélectionnez une table parent et une table enfant (par exemple Customers et Orders) avec une relation de clé étrangère.  
  
    7. Remplacez le nom du jeu de données par défaut, si vous le souhaitez.  
  
    8. Cliquez sur **Terminer**.  
  
4. Dans la zone de liste déroulante **Afficher le membre**, sélectionnez le nom de la colonne (par exemple ContactName) à afficher dans la zone de liste modifiable.  
  
5. Dans la zone de liste déroulante **Membre Value**, sélectionnez la colonne (par exemple, CustomerID) pour effectuer l’opération de recherche dans la table enfant.  
  
6. Dans la zone de liste déroulante **Valeur sélectionnée**, accédez à **Sources de données du projet** ainsi qu’au jeu de données que vous venez de créer et qui contient les tables parents et les tables enfants. Sélectionnez la même propriété de la table enfant qui représente le membre Value de la table parent (par exemple Orders.CustomerID). Les composants appropriés de <xref:System.Windows.Forms.BindingSource>, de jeu de données et d'adaptateur de table sont créés et ajoutés au formulaire.  
  
7. Liez le contrôle <xref:System.Windows.Forms.BindingNavigator> au <xref:System.Windows.Forms.BindingSource> de la table enfant (par exemple `OrdersBindingSource`).  
  
8. Liez les contrôles autres que <xref:System.Windows.Forms.ComboBox> et <xref:System.Windows.Forms.BindingNavigator> aux champs de détails du <xref:System.Windows.Forms.BindingSource> de la table enfant (par exemple `OrdersBindingSource`) à afficher.  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Forms.BindingSource>
- [BindingSource, composant](bindingsource-component.md)
- [ComboBox, contrôle](combobox-control-windows-forms.md)
- [Lier des contrôles à des données dans Visual Studio](/visualstudio/data-tools/bind-controls-to-data-in-visual-studio)
