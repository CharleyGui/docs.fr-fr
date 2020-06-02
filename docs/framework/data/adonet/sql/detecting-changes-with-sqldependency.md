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
# <a name="detecting-changes-with-sqldependency"></a><span data-ttu-id="95837-103">Détection des modifications avec SqlDependency</span><span class="sxs-lookup"><span data-stu-id="95837-103">Detecting Changes with SqlDependency</span></span>

<span data-ttu-id="95837-104">Un objet <xref:System.Data.SqlClient.SqlDependency> peut être associé à une <xref:System.Data.SqlClient.SqlCommand> afin de détecter si les résultats de la requête diffèrent de ceux qui sont récupérés à l’origine.</span><span class="sxs-lookup"><span data-stu-id="95837-104">A <xref:System.Data.SqlClient.SqlDependency> object can be associated with a <xref:System.Data.SqlClient.SqlCommand> in order to detect when query results differ from those originally retrieved.</span></span> <span data-ttu-id="95837-105">Vous pouvez également attribuer un délégué à l’événement `OnChange`, qui se déclenche lorsque les résultats changent pour une commande associée.</span><span class="sxs-lookup"><span data-stu-id="95837-105">You can also assign a delegate to the `OnChange` event, which will fire when the results change for an associated command.</span></span> <span data-ttu-id="95837-106">Vous devez associer la <xref:System.Data.SqlClient.SqlDependency> à la commande avant d’exécuter la commande.</span><span class="sxs-lookup"><span data-stu-id="95837-106">You must associate the <xref:System.Data.SqlClient.SqlDependency> with the command before you execute the command.</span></span> <span data-ttu-id="95837-107">La propriété `HasChanges` de la <xref:System.Data.SqlClient.SqlDependency> peut également être utilisée pour déterminer si les résultats de la requête ont changé depuis la première récupération des données.</span><span class="sxs-lookup"><span data-stu-id="95837-107">The `HasChanges` property of the <xref:System.Data.SqlClient.SqlDependency> can also be used to determine if the query results have changed since the data was first retrieved.</span></span>

## <a name="security-considerations"></a><span data-ttu-id="95837-108">Considérations relatives à la sécurité</span><span class="sxs-lookup"><span data-stu-id="95837-108">Security Considerations</span></span>

<span data-ttu-id="95837-109">L’infrastructure de dépendance repose sur une <xref:System.Data.SqlClient.SqlConnection> qui est ouverte lorsque <xref:System.Data.SqlClient.SqlDependency.Start%2A> est appelé pour recevoir des notifications de modification des données sous-jacentes pour une commande donnée.</span><span class="sxs-lookup"><span data-stu-id="95837-109">The dependency infrastructure relies on a <xref:System.Data.SqlClient.SqlConnection> that is opened when <xref:System.Data.SqlClient.SqlDependency.Start%2A> is called in order to receive notifications that the underlying data has changed for a given command.</span></span> <span data-ttu-id="95837-110">La possibilité pour un client d’initier l’appel à `SqlDependency.Start` est contrôlée par le biais de l’utilisation de <xref:System.Data.SqlClient.SqlClientPermission> et des attributs de sécurité d’accès du code.</span><span class="sxs-lookup"><span data-stu-id="95837-110">The ability for a client to initiate the call to `SqlDependency.Start` is controlled through the use of <xref:System.Data.SqlClient.SqlClientPermission> and code access security attributes.</span></span> <span data-ttu-id="95837-111">Pour plus d’informations, consultez [activation des notifications de requêtes](enabling-query-notifications.md) et de la [sécurité d’accès du code et ADO.net](../code-access-security.md).</span><span class="sxs-lookup"><span data-stu-id="95837-111">For more information, see [Enabling Query Notifications](enabling-query-notifications.md) and [Code Access Security and ADO.NET](../code-access-security.md).</span></span>

### <a name="example"></a><span data-ttu-id="95837-112">Exemple</span><span class="sxs-lookup"><span data-stu-id="95837-112">Example</span></span>

<span data-ttu-id="95837-113">Les étapes suivantes montrent comment déclarer une dépendance, exécuter une commande et recevoir une notification lorsque le jeu de résultats change :</span><span class="sxs-lookup"><span data-stu-id="95837-113">The following steps illustrate how to declare a dependency, execute a command, and receive a notification when the result set changes:</span></span>

1. <span data-ttu-id="95837-114">Établit une connexion `SqlDependency` au serveur.</span><span class="sxs-lookup"><span data-stu-id="95837-114">Initiate a `SqlDependency` connection to the server.</span></span>

2. <span data-ttu-id="95837-115">Créez des objets <xref:System.Data.SqlClient.SqlConnection> et <xref:System.Data.SqlClient.SqlCommand> pour vous connecter au serveur et définir une instruction Transact-SQL.</span><span class="sxs-lookup"><span data-stu-id="95837-115">Create <xref:System.Data.SqlClient.SqlConnection> and <xref:System.Data.SqlClient.SqlCommand> objects to connect to the server and define a Transact-SQL statement.</span></span>

3. <span data-ttu-id="95837-116">Créez un objet `SqlDependency` ou utilisez un objet existant, puis liez-le à l’objet `SqlCommand`.</span><span class="sxs-lookup"><span data-stu-id="95837-116">Create a new `SqlDependency` object, or use an existing one, and bind it to the `SqlCommand` object.</span></span> <span data-ttu-id="95837-117">En interne, cela crée un objet <xref:System.Data.Sql.SqlNotificationRequest> et le lie à l’objet de commande en fonction des besoins.</span><span class="sxs-lookup"><span data-stu-id="95837-117">Internally, this creates a <xref:System.Data.Sql.SqlNotificationRequest> object and binds it to the command object as needed.</span></span> <span data-ttu-id="95837-118">Cette requête de notification contient un identificateur interne qui identifie de façon unique cet objet `SqlDependency`.</span><span class="sxs-lookup"><span data-stu-id="95837-118">This notification request contains an internal identifier that uniquely identifies this `SqlDependency` object.</span></span> <span data-ttu-id="95837-119">L’écouteur client est également démarré s’il n’est pas déjà actif.</span><span class="sxs-lookup"><span data-stu-id="95837-119">It also starts the client listener if it is not already active.</span></span>

4. <span data-ttu-id="95837-120">Abonnez un gestionnaire d’événements à l’événement `OnChange` de l’objet `SqlDependency`.</span><span class="sxs-lookup"><span data-stu-id="95837-120">Subscribe an event handler to the `OnChange` event of the `SqlDependency` object.</span></span>

5. <span data-ttu-id="95837-121">Exécutez la commande à l’aide de l’une des méthodes `Execute` de l’objet `SqlCommand`.</span><span class="sxs-lookup"><span data-stu-id="95837-121">Execute the command using any of the `Execute` methods of the `SqlCommand` object.</span></span> <span data-ttu-id="95837-122">Étant donné que la commande est liée à l’objet de notification, le serveur reconnaît qu’il doit générer une notification, et les informations de la file d’attente pointent vers la file d’attente des dépendances.</span><span class="sxs-lookup"><span data-stu-id="95837-122">Because the command is bound to the notification object, the server recognizes that it must generate a notification, and the queue information will point to the dependencies queue.</span></span>

6. <span data-ttu-id="95837-123">Arrêtez la connexion `SqlDependency` au serveur.</span><span class="sxs-lookup"><span data-stu-id="95837-123">Stop the `SqlDependency` connection to the server.</span></span>

<span data-ttu-id="95837-124">Si un utilisateur modifie ensuite les données sous-jacentes, Microsoft SQL Server détecte qu’il existe une notification en attente pour une telle modification, puis publie une notification qui est traitée et transférée au client via la `SqlConnection` sous-jacente qui a été créée en appelant `SqlDependency.Start`.</span><span class="sxs-lookup"><span data-stu-id="95837-124">If any user subsequently changes the underlying data, Microsoft SQL Server detects that there is a notification pending for such a change, and posts a notification that is processed and forwarded to the client through the underlying `SqlConnection` that was created by calling `SqlDependency.Start`.</span></span> <span data-ttu-id="95837-125">L’écouteur client reçoit le message d’invalidation.</span><span class="sxs-lookup"><span data-stu-id="95837-125">The client listener receives the invalidation message.</span></span> <span data-ttu-id="95837-126">L’écouteur client localise ensuite l’objet `SqlDependency` associé et déclenche l’événement `OnChange`.</span><span class="sxs-lookup"><span data-stu-id="95837-126">The client listener then locates the associated `SqlDependency` object and fires the `OnChange` event.</span></span>

<span data-ttu-id="95837-127">Le fragment de code suivant montre le modèle de conception que vous utiliseriez pour créer un exemple d’application.</span><span class="sxs-lookup"><span data-stu-id="95837-127">The following code fragment shows the design pattern you would use to create a sample application.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="95837-128">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="95837-128">See also</span></span>

- [<span data-ttu-id="95837-129">Notifications de requêtes dans SQL Server</span><span class="sxs-lookup"><span data-stu-id="95837-129">Query Notifications in SQL Server</span></span>](query-notifications-in-sql-server.md)
- [<span data-ttu-id="95837-130">Vue d'ensemble d’ADO.NET</span><span class="sxs-lookup"><span data-stu-id="95837-130">ADO.NET Overview</span></span>](../ado-net-overview.md)
