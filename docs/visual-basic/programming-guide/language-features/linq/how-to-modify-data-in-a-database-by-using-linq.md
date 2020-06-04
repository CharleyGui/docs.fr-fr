---
title: 'Guide pratique : modifier des données dans une base de données à l’aide de LINQ'
ms.date: 07/20/2015
helpviewer_keywords:
- inserting rows [LINQ to SQL]
- deleting rows [LINQ to SQL]
- updating rows [LINQ to SQL]
- inserting data [Visual Basic]
- deleting data
- data [Visual Basic], updating
- updating data [LINQ]
- queries [LINQ in Visual Basic], data changes in database
- queries [LINQ in Visual Basic], how-to topics
ms.assetid: cf52635f-0c1b-46c3-aff1-bdf181cf19b1
ms.openlocfilehash: eb076d9156fa66858f2e560422eef0dc61ba22b5
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84403483"
---
# <a name="how-to-modify-data-in-a-database-by-using-linq-visual-basic"></a>Comment : modifier des données dans une base de données à l'aide de LINQ (Visual Basic)

Les requêtes LINQ (Language-Integrated Query) facilitent l’accès aux informations de la base de données et la modification des valeurs dans la base de données.

L’exemple suivant montre comment créer une nouvelle application qui récupère et met à jour des informations dans une base de données SQL Server.

Les exemples de cette rubrique utilisent l’exemple de base de données Northwind. Si cette base de données n’est pas disponible sur votre ordinateur de développement, vous pouvez la télécharger à partir du Centre de téléchargement Microsoft. Pour obtenir des instructions, consultez [téléchargement d’exemples de bases de données](../../../../framework/data/adonet/sql/linq/downloading-sample-databases.md).

### <a name="to-create-a-connection-to-a-database"></a>Pour créer une connexion à une base de données

1. Dans Visual Studio, ouvrez **Explorateur de serveurs** / **Explorateur de base de données** en cliquant sur le menu **affichage** , puis sélectionnez **Explorateur de serveurs** / **Explorateur de base de données**.

2. Cliquez avec le bouton droit sur **connexions de données** dans **Explorateur de serveurs** / **Explorateur de base de données**, puis cliquez sur **Ajouter une connexion**.

3. Spécifiez une connexion valide à l’exemple de base de données Northwind.

### <a name="to-add-a-project-with-a-linq-to-sql-file"></a>Pour ajouter un projet avec un fichier LINQ to SQL

1. Dans Visual Studio, dans le menu **fichier** , pointez sur **nouveau** , puis cliquez sur **projet**. Sélectionnez Visual Basic **Application Windows Forms** comme type de projet.

2. Dans le menu **Projet** , cliquez sur **Ajouter un nouvel élément**. Sélectionnez le modèle d’élément **Classes LINQ to SQL** .

3. Nommez le fichier `northwind.dbml`. Cliquez sur **Add**. Le Concepteur Objet Relationnel (Concepteur O/R) est ouvert pour le `northwind.dbml` fichier.

### <a name="to-add-tables-to-query-and-modify-to-the-designer"></a>Pour ajouter des tables à interroger et à modifier dans le concepteur

1. Dans **Explorateur de serveurs** / **Explorateur de base de données**, développez la connexion à la base de données Northwind. Développez le dossier **Tables** .

     Si vous avez fermé le Concepteur O/R, vous pouvez le rouvrir en double-cliquant sur le `northwind.dbml` fichier que vous avez ajouté précédemment.

2. Cliquez sur la table Customers et faites-la glisser vers le volet gauche du concepteur.

     Le concepteur crée un nouvel objet client pour votre projet.

3. Enregistrez vos modifications et fermez le concepteur.

4. Enregistrez votre projet.

### <a name="to-add-code-to-modify-the-database-and-display-the-results"></a>Pour ajouter du code afin de modifier la base de données et d’afficher les résultats

1. À partir de la **boîte à outils**, faites glisser un <xref:System.Windows.Forms.DataGridView> contrôle sur le Windows Form par défaut de votre projet, Form1.

2. Quand vous avez ajouté des tables au Concepteur O/R, le concepteur a ajouté un <xref:System.Data.Linq.DataContext> objet à votre projet. Cet objet contient du code que vous pouvez utiliser pour accéder à la table Customers. Il contient également du code qui définit un objet Customer local et une collection Customers pour la table. L' <xref:System.Data.Linq.DataContext> objet de votre projet est nommé en fonction du nom de votre fichier. dbml. Pour ce projet, l' <xref:System.Data.Linq.DataContext> objet est nommé `northwindDataContext` .

     Vous pouvez créer une instance de l' <xref:System.Data.Linq.DataContext> objet dans votre code et interroger et modifier la collection Customers spécifiée par le Concepteur O/R. Les modifications que vous apportez à la collection Customers ne sont pas reflétées dans la base de données tant que vous ne les avez pas envoyées en appelant la <xref:System.Data.Linq.DataContext.SubmitChanges%2A> méthode de l' <xref:System.Data.Linq.DataContext> objet.

     Double-cliquez sur le Windows Form, Form1, pour ajouter du code à l' <xref:System.Windows.Forms.Form.Load> événement afin d’interroger la table Customers exposée en tant que propriété de votre <xref:System.Data.Linq.DataContext> . Ajoutez le code suivant :

    ```vb
    Private db As northwindDataContext

    Private Sub Form1_Load(ByVal sender As System.Object,
                           ByVal e As System.EventArgs
                          ) Handles MyBase.Load
      db = New northwindDataContext()

      RefreshData()
    End Sub

    Private Sub RefreshData()
      Dim customers = From cust In db.Customers
                      Where cust.City(0) = "W"
                      Select cust

      DataGridView1.DataSource = customers
    End Sub
    ```

3. À partir de la **boîte à outils**, faites glisser trois <xref:System.Windows.Forms.Button> contrôles sur le formulaire. Sélectionnez le premier `Button` contrôle. Dans la fenêtre Propriétés, affectez à la **propriété** du contrôle la valeur `Name` `Button` `AddButton` et `Text` à `Add` . Sélectionnez le deuxième bouton et affectez à la propriété la valeur `Name` `UpdateButton` et `Text` à la propriété `Update` . Sélectionnez le troisième bouton et affectez à la propriété la valeur `Name` `DeleteButton` et `Text` à la propriété `Delete` .

4. Double-cliquez sur le bouton **Ajouter** pour ajouter du code à l' `Click` événement. Ajoutez le code suivant :

    ```vb
    Private Sub AddButton_Click(ByVal sender As System.Object,
                                ByVal e As System.EventArgs
                               ) Handles AddButton.Click
      Dim cust As New Customer With {
        .City = "Wellington",
        .CompanyName = "Blue Yonder Airlines",
        .ContactName = "Jill Frank",
        .Country = "New Zealand",
        .CustomerID = "JILLF"}

      db.Customers.InsertOnSubmit(cust)

      Try
        db.SubmitChanges()
      Catch
        ' Handle exception.
      End Try

      RefreshData()
    End Sub
    ```

5. Double-cliquez sur le bouton **mettre à jour** pour ajouter du code à l' `Click` événement. Ajoutez le code suivant :

    ```vb
    Private Sub UpdateButton_Click(ByVal sender As System.Object, _
                                   ByVal e As System.EventArgs
                                  ) Handles UpdateButton.Click
      Dim updateCust = (From cust In db.Customers
                        Where cust.CustomerID = "JILLF").ToList()(0)

      updateCust.ContactName = "Jill Shrader"
      updateCust.Country = "Wales"
      updateCust.CompanyName = "Red Yonder Airlines"
      updateCust.City = "Cardiff"

      Try
        db.SubmitChanges()
      Catch
        ' Handle exception.
      End Try

      RefreshData()
    End Sub
    ```

6. Double-cliquez sur le bouton **supprimer** pour ajouter du code à l' `Click` événement. Ajoutez le code suivant :

    ```vb
    Private Sub DeleteButton_Click(ByVal sender As System.Object, _
                                   ByVal e As System.EventArgs
                                  ) Handles DeleteButton.Click
      Dim deleteCust = (From cust In db.Customers
                        Where cust.CustomerID = "JILLF").ToList()(0)

      db.Customers.DeleteOnSubmit(deleteCust)

      Try
        db.SubmitChanges()
      Catch
        ' Handle exception.
      End Try

      RefreshData()
    End Sub
    ```

7. Appuyez sur F5 pour exécuter votre projet. Cliquez sur **Ajouter** pour ajouter un nouvel enregistrement. Cliquez sur **mettre à jour** pour modifier le nouvel enregistrement. Cliquez sur **supprimer** pour supprimer le nouvel enregistrement.

## <a name="see-also"></a>Voir aussi

- [LINQ](index.md)
- [Requêtes](../../../language-reference/queries/index.md)
- [LINQ to SQL](../../../../framework/data/adonet/sql/linq/index.md)
- [Méthode DataContext (Concepteur O/R)](/visualstudio/data-tools/datacontext-methods-o-r-designer)
- [Guide pratique pour affecter des procédures stockées pour effectuer des mises à jour, des insertions et des suppressions (Concepteur O/R)](/visualstudio/data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer)
