---
title: Détection des modifications avec SqlDependency
description: Associez un objet SqlDependency à un SqlCommand pour détecter les différences entre les résultats de la requête et ceux qui ont été récupérés à l’origine dans ADO.NET.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: e6a58316-f005-4477-92e1-45cc2eb8c5b4
ms.openlocfilehash: b196d42477e1778c45df64b1390502645fdd649d
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84286466"
---
# <a name="detecting-changes-with-sqldependency"></a>Détection des modifications avec SqlDependency

Un objet <xref:System.Data.SqlClient.SqlDependency> peut être associé à une <xref:System.Data.SqlClient.SqlCommand> afin de détecter si les résultats de la requête diffèrent de ceux qui sont récupérés à l’origine. Vous pouvez également attribuer un délégué à l’événement `OnChange`, qui se déclenche lorsque les résultats changent pour une commande associée. Vous devez associer la <xref:System.Data.SqlClient.SqlDependency> à la commande avant d’exécuter la commande. La propriété `HasChanges` de la <xref:System.Data.SqlClient.SqlDependency> peut également être utilisée pour déterminer si les résultats de la requête ont changé depuis la première récupération des données.

## <a name="security-considerations"></a>Considérations relatives à la sécurité

L’infrastructure de dépendance repose sur une <xref:System.Data.SqlClient.SqlConnection> qui est ouverte lorsque <xref:System.Data.SqlClient.SqlDependency.Start%2A> est appelé pour recevoir des notifications de modification des données sous-jacentes pour une commande donnée. La possibilité pour un client d’initier l’appel à `SqlDependency.Start` est contrôlée par le biais de l’utilisation de <xref:System.Data.SqlClient.SqlClientPermission> et des attributs de sécurité d’accès du code. Pour plus d’informations, consultez [activation des notifications de requêtes](enabling-query-notifications.md) et de la [sécurité d’accès du code et ADO.net](../code-access-security.md).

### <a name="example"></a>Exemple

Les étapes suivantes montrent comment déclarer une dépendance, exécuter une commande et recevoir une notification lorsque le jeu de résultats change :

1. Établit une connexion `SqlDependency` au serveur.

2. Créez des objets <xref:System.Data.SqlClient.SqlConnection> et <xref:System.Data.SqlClient.SqlCommand> pour vous connecter au serveur et définir une instruction Transact-SQL.

3. Créez un objet `SqlDependency` ou utilisez un objet existant, puis liez-le à l’objet `SqlCommand`. En interne, cela crée un objet <xref:System.Data.Sql.SqlNotificationRequest> et le lie à l’objet de commande en fonction des besoins. Cette requête de notification contient un identificateur interne qui identifie de façon unique cet objet `SqlDependency`. L’écouteur client est également démarré s’il n’est pas déjà actif.

4. Abonnez un gestionnaire d’événements à l’événement `OnChange` de l’objet `SqlDependency`.

5. Exécutez la commande à l’aide de l’une des méthodes `Execute` de l’objet `SqlCommand`. Étant donné que la commande est liée à l’objet de notification, le serveur reconnaît qu’il doit générer une notification, et les informations de la file d’attente pointent vers la file d’attente des dépendances.

6. Arrêtez la connexion `SqlDependency` au serveur.

Si un utilisateur modifie ensuite les données sous-jacentes, Microsoft SQL Server détecte qu’il existe une notification en attente pour une telle modification, puis publie une notification qui est traitée et transférée au client via la `SqlConnection` sous-jacente qui a été créée en appelant `SqlDependency.Start`. L’écouteur client reçoit le message d’invalidation. L’écouteur client localise ensuite l’objet `SqlDependency` associé et déclenche l’événement `OnChange`.

Le fragment de code suivant montre le modèle de conception que vous utiliseriez pour créer un exemple d’application.

```vb
Sub Initialization()
    ' Create a dependency connection.
    SqlDependency.Start(connectionString, queueName)
End Sub

Sub SomeMethod()
    ' Assume connection is an open SqlConnection.
    ' Create a new SqlCommand object.
    Using command As New SqlCommand( _
      "SELECT ShipperID, CompanyName, Phone FROM dbo.Shippers", _
      connection)

        ' Create a dependency and associate it with the SqlCommand.
        Dim dependency As New SqlDependency(command)
        ' Maintain the refernce in a class member.
        ' Subscribe to the SqlDependency event.
        AddHandler dependency.OnChange, AddressOf OnDependencyChange

        ' Execute the command.
        Using reader = command.ExecuteReader()
            ' Process the DataReader.
        End Using
    End Using
End Sub

' Handler method
Sub OnDependencyChange(ByVal sender As Object, _
    ByVal e As SqlNotificationEventArgs)
    ' Handle the event (for example, invalidate this cache entry).
End Sub

Sub Termination()
    ' Release the dependency
    SqlDependency.Stop(connectionString, queueName)
End Sub
```

```csharp
void Initialization()
{
    // Create a dependency connection.
    SqlDependency.Start(connectionString, queueName);
}

void SomeMethod()
{
    // Assume connection is an open SqlConnection.

    // Create a new SqlCommand object.
    using (SqlCommand command=new SqlCommand(
        "SELECT ShipperID, CompanyName, Phone FROM dbo.Shippers",
        connection))
    {

        // Create a dependency and associate it with the SqlCommand.
        SqlDependency dependency=new SqlDependency(command);
        // Maintain the reference in a class member.

        // Subscribe to the SqlDependency event.
        dependency.OnChange+=new
           OnChangeEventHandler(OnDependencyChange);

        // Execute the command.
        using (SqlDataReader reader = command.ExecuteReader())
        {
            // Process the DataReader.
        }
    }
}

// Handler method
void OnDependencyChange(object sender,
   SqlNotificationEventArgs e )
{
  // Handle the event (for example, invalidate this cache entry).
}

void Termination()
{
    // Release the dependency.
    SqlDependency.Stop(connectionString, queueName);
}
```

## <a name="see-also"></a>Voir aussi

- [Notifications de requêtes dans SQL Server](query-notifications-in-sql-server.md)
- [Vue d'ensemble d’ADO.NET](../ado-net-overview.md)
