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
# <a name="detecting-changes-with-sqldependency"></a><span data-ttu-id="b46a0-102">Détection des modifications avec SqlDependency</span><span class="sxs-lookup"><span data-stu-id="b46a0-102">Detecting Changes with SqlDependency</span></span>

<span data-ttu-id="b46a0-103">Un objet <xref:System.Data.SqlClient.SqlDependency> peut être associé à un objet <xref:System.Data.SqlClient.SqlCommand> afin de détecter quand des résultats de requête sont différents des résultats récupérés à l'origine.</span><span class="sxs-lookup"><span data-stu-id="b46a0-103">A <xref:System.Data.SqlClient.SqlDependency> object can be associated with a <xref:System.Data.SqlClient.SqlCommand> in order to detect when query results differ from those originally retrieved.</span></span> <span data-ttu-id="b46a0-104">Vous pouvez également assigner un délégué à l'événement `OnChange`, qui est déclenché lorsque les résultats changent pour une commande associée.</span><span class="sxs-lookup"><span data-stu-id="b46a0-104">You can also assign a delegate to the `OnChange` event, which will fire when the results change for an associated command.</span></span> <span data-ttu-id="b46a0-105">Vous devez associer <xref:System.Data.SqlClient.SqlDependency> à la commande avant d'exécuter celle-ci.</span><span class="sxs-lookup"><span data-stu-id="b46a0-105">You must associate the <xref:System.Data.SqlClient.SqlDependency> with the command before you execute the command.</span></span> <span data-ttu-id="b46a0-106">La propriété `HasChanges` de l'objet <xref:System.Data.SqlClient.SqlDependency> peut également être utilisée pour déterminer si les résultats de la requête ont changé depuis la première récupération des données.</span><span class="sxs-lookup"><span data-stu-id="b46a0-106">The `HasChanges` property of the <xref:System.Data.SqlClient.SqlDependency> can also be used to determine if the query results have changed since the data was first retrieved.</span></span>

## <a name="security-considerations"></a><span data-ttu-id="b46a0-107">Considérations relatives à la sécurité</span><span class="sxs-lookup"><span data-stu-id="b46a0-107">Security Considerations</span></span>

<span data-ttu-id="b46a0-108">L'infrastructure de dépendance repose sur un objet <xref:System.Data.SqlClient.SqlConnection> qui est ouvert lorsque la méthode <xref:System.Data.SqlClient.SqlDependency.Start%2A> est appelée pour recevoir des notifications de modification des données sous-jacentes pour une commande donnée.</span><span class="sxs-lookup"><span data-stu-id="b46a0-108">The dependency infrastructure relies on a <xref:System.Data.SqlClient.SqlConnection> that is opened when <xref:System.Data.SqlClient.SqlDependency.Start%2A> is called in order to receive notifications that the underlying data has changed for a given command.</span></span> <span data-ttu-id="b46a0-109">La capacité d'un client à lancer l'appel de la méthode `SqlDependency.Start` est contrôlée par le biais de l'utilisation de <xref:System.Data.SqlClient.SqlClientPermission> et des attributs de sécurité d'accès du code.</span><span class="sxs-lookup"><span data-stu-id="b46a0-109">The ability for a client to initiate the call to `SqlDependency.Start` is controlled through the use of <xref:System.Data.SqlClient.SqlClientPermission> and code access security attributes.</span></span> <span data-ttu-id="b46a0-110">Pour plus d’informations, consultez [activation des notifications de requêtes](enabling-query-notifications.md) et de la [sécurité d’accès du code et ADO.net](../code-access-security.md).</span><span class="sxs-lookup"><span data-stu-id="b46a0-110">For more information, see [Enabling Query Notifications](enabling-query-notifications.md) and [Code Access Security and ADO.NET](../code-access-security.md).</span></span>

### <a name="example"></a><span data-ttu-id="b46a0-111">Exemples</span><span class="sxs-lookup"><span data-stu-id="b46a0-111">Example</span></span>

<span data-ttu-id="b46a0-112">Les étapes suivantes montrent comment déclarer une dépendance, exécuter une commande et recevoir un notification lorsque le jeu de résultats change :</span><span class="sxs-lookup"><span data-stu-id="b46a0-112">The following steps illustrate how to declare a dependency, execute a command, and receive a notification when the result set changes:</span></span>

1. <span data-ttu-id="b46a0-113">Établissez une connexion `SqlDependency` au serveur.</span><span class="sxs-lookup"><span data-stu-id="b46a0-113">Initiate a `SqlDependency` connection to the server.</span></span>

2. <span data-ttu-id="b46a0-114">Créez les objets <xref:System.Data.SqlClient.SqlConnection> et <xref:System.Data.SqlClient.SqlCommand> pour vous connecter au serveur et définissez une instruction Transact-SQL.</span><span class="sxs-lookup"><span data-stu-id="b46a0-114">Create <xref:System.Data.SqlClient.SqlConnection> and <xref:System.Data.SqlClient.SqlCommand> objects to connect to the server and define a Transact-SQL statement.</span></span>

3. <span data-ttu-id="b46a0-115">Créez un objet `SqlDependency` ou utilisez-en un existant et liez-le à l'objet `SqlCommand`.</span><span class="sxs-lookup"><span data-stu-id="b46a0-115">Create a new `SqlDependency` object, or use an existing one, and bind it to the `SqlCommand` object.</span></span> <span data-ttu-id="b46a0-116">Au niveau interne, cette opération crée un objet <xref:System.Data.Sql.SqlNotificationRequest> et le lie à l'objet de commande de manière appropriée.</span><span class="sxs-lookup"><span data-stu-id="b46a0-116">Internally, this creates a <xref:System.Data.Sql.SqlNotificationRequest> object and binds it to the command object as needed.</span></span> <span data-ttu-id="b46a0-117">La demande de notification contient un identificateur interne qui identifie de façon univoque cet objet `SqlDependency`.</span><span class="sxs-lookup"><span data-stu-id="b46a0-117">This notification request contains an internal identifier that uniquely identifies this `SqlDependency` object.</span></span> <span data-ttu-id="b46a0-118">Elle démarre également l'écouteur client s'il est inactif.</span><span class="sxs-lookup"><span data-stu-id="b46a0-118">It also starts the client listener if it is not already active.</span></span>

4. <span data-ttu-id="b46a0-119">Abonnez un gestionnaire d'événements à l'événement `OnChange` de l'objet `SqlDependency`.</span><span class="sxs-lookup"><span data-stu-id="b46a0-119">Subscribe an event handler to the `OnChange` event of the `SqlDependency` object.</span></span>

5. <span data-ttu-id="b46a0-120">Exécutez la commande à l'aide de l'une des méthodes `Execute` de l'objet `SqlCommand`.</span><span class="sxs-lookup"><span data-stu-id="b46a0-120">Execute the command using any of the `Execute` methods of the `SqlCommand` object.</span></span> <span data-ttu-id="b46a0-121">Comme la commande est liée à l'objet Notification, le serveur reconnaît qu'il doit générer une notification et les informations de file d'attente pointent sur la file d'attente des dépendances.</span><span class="sxs-lookup"><span data-stu-id="b46a0-121">Because the command is bound to the notification object, the server recognizes that it must generate a notification, and the queue information will point to the dependencies queue.</span></span>

6. <span data-ttu-id="b46a0-122">Interrompez la connexion `SqlDependency` au serveur.</span><span class="sxs-lookup"><span data-stu-id="b46a0-122">Stop the `SqlDependency` connection to the server.</span></span>

<span data-ttu-id="b46a0-123">Si un utilisateur modifie ensuite les données sous-jacentes, Microsoft SQL Server détecte qu'il y a une notification en attente pour cette modification et émet une notification qui est traitée et transmise au client via l'objet `SqlConnection` sous-jacent qui a été créé en appelant la méthode `SqlDependency.Start`.</span><span class="sxs-lookup"><span data-stu-id="b46a0-123">If any user subsequently changes the underlying data, Microsoft SQL Server detects that there is a notification pending for such a change, and posts a notification that is processed and forwarded to the client through the underlying `SqlConnection` that was created by calling `SqlDependency.Start`.</span></span> <span data-ttu-id="b46a0-124">L'écouteur client reçoit le message d'invalidation.</span><span class="sxs-lookup"><span data-stu-id="b46a0-124">The client listener receives the invalidation message.</span></span> <span data-ttu-id="b46a0-125">Il localise ensuite l'objet `SqlDependency` associé puis déclenche l'événement `OnChange`.</span><span class="sxs-lookup"><span data-stu-id="b46a0-125">The client listener then locates the associated `SqlDependency` object and fires the `OnChange` event.</span></span>

<span data-ttu-id="b46a0-126">Le fragment de code suivant montre le modèle de design qui peut être utilisé pour créer un exemple d'application.</span><span class="sxs-lookup"><span data-stu-id="b46a0-126">The following code fragment shows the design pattern you would use to create a sample application.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="b46a0-127">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b46a0-127">See also</span></span>

- [<span data-ttu-id="b46a0-128">Notifications de requête dans SQL Server</span><span class="sxs-lookup"><span data-stu-id="b46a0-128">Query Notifications in SQL Server</span></span>](query-notifications-in-sql-server.md)
- [<span data-ttu-id="b46a0-129">Vue d’ensemble d’ADO.NET</span><span class="sxs-lookup"><span data-stu-id="b46a0-129">ADO.NET Overview</span></span>](../ado-net-overview.md)
