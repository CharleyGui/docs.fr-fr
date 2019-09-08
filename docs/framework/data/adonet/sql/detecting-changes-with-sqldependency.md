---
title: Détection des modifications avec SqlDependency
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: e6a58316-f005-4477-92e1-45cc2eb8c5b4
ms.openlocfilehash: 3719188064388b00c756dd037d4a475ca6debd13
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70782420"
---
# <a name="detecting-changes-with-sqldependency"></a>Détection des modifications avec SqlDependency

Un objet <xref:System.Data.SqlClient.SqlDependency> peut être associé à un objet <xref:System.Data.SqlClient.SqlCommand> afin de détecter quand des résultats de requête sont différents des résultats récupérés à l'origine. Vous pouvez également assigner un délégué à l'événement `OnChange`, qui est déclenché lorsque les résultats changent pour une commande associée. Vous devez associer <xref:System.Data.SqlClient.SqlDependency> à la commande avant d'exécuter celle-ci. La propriété `HasChanges` de l'objet <xref:System.Data.SqlClient.SqlDependency> peut également être utilisée pour déterminer si les résultats de la requête ont changé depuis la première récupération des données.

## <a name="security-considerations"></a>Considérations relatives à la sécurité

L'infrastructure de dépendance repose sur un objet <xref:System.Data.SqlClient.SqlConnection> qui est ouvert lorsque la méthode <xref:System.Data.SqlClient.SqlDependency.Start%2A> est appelée pour recevoir des notifications de modification des données sous-jacentes pour une commande donnée. La capacité d'un client à lancer l'appel de la méthode `SqlDependency.Start` est contrôlée par le biais de l'utilisation de <xref:System.Data.SqlClient.SqlClientPermission> et des attributs de sécurité d'accès du code. Pour plus d’informations, consultez [activation des notifications de requêtes](enabling-query-notifications.md) et de la [sécurité d’accès du code et ADO.net](../code-access-security.md).

### <a name="example"></a>Exemples

Les étapes suivantes montrent comment déclarer une dépendance, exécuter une commande et recevoir un notification lorsque le jeu de résultats change :

1. Établissez une connexion `SqlDependency` au serveur.

2. Créez les objets <xref:System.Data.SqlClient.SqlConnection> et <xref:System.Data.SqlClient.SqlCommand> pour vous connecter au serveur et définissez une instruction Transact-SQL.

3. Créez un objet `SqlDependency` ou utilisez-en un existant et liez-le à l'objet `SqlCommand`. Au niveau interne, cette opération crée un objet <xref:System.Data.Sql.SqlNotificationRequest> et le lie à l'objet de commande de manière appropriée. La demande de notification contient un identificateur interne qui identifie de façon univoque cet objet `SqlDependency`. Elle démarre également l'écouteur client s'il est inactif.

4. Abonnez un gestionnaire d'événements à l'événement `OnChange` de l'objet `SqlDependency`.

5. Exécutez la commande à l'aide de l'une des méthodes `Execute` de l'objet `SqlCommand`. Comme la commande est liée à l'objet Notification, le serveur reconnaît qu'il doit générer une notification et les informations de file d'attente pointent sur la file d'attente des dépendances.

6. Interrompez la connexion `SqlDependency` au serveur.

Si un utilisateur modifie ensuite les données sous-jacentes, Microsoft SQL Server détecte qu'il y a une notification en attente pour cette modification et émet une notification qui est traitée et transmise au client via l'objet `SqlConnection` sous-jacent qui a été créé en appelant la méthode `SqlDependency.Start`. L'écouteur client reçoit le message d'invalidation. Il localise ensuite l'objet `SqlDependency` associé puis déclenche l'événement `OnChange`.

Le fragment de code suivant montre le modèle de design qui peut être utilisé pour créer un exemple d'application.

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

- [Notifications de requête dans SQL Server](query-notifications-in-sql-server.md)
- [Vue d’ensemble d’ADO.NET](../ado-net-overview.md)
