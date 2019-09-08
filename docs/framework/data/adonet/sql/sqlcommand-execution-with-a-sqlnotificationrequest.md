---
title: Exécution de SqlCommand avec une SqlNotificationRequest
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 1776f48f-9bea-41f6-83a4-c990c7a2c991
ms.openlocfilehash: 3115bfb80d4e5e61ed49da11e36eaa37bc24334f
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70791534"
---
# <a name="sqlcommand-execution-with-a-sqlnotificationrequest"></a><span data-ttu-id="d8c34-102">Exécution de SqlCommand avec une SqlNotificationRequest</span><span class="sxs-lookup"><span data-stu-id="d8c34-102">SqlCommand Execution with a SqlNotificationRequest</span></span>

<span data-ttu-id="d8c34-103">Un <xref:System.Data.SqlClient.SqlCommand> peut être configuré pour générer une notification lors de la modification de données, une fois qu’il a été récupéré à partir du serveur et que le jeu de résultats est différent en cas de nouvelle exécution de la requête.</span><span class="sxs-lookup"><span data-stu-id="d8c34-103">A <xref:System.Data.SqlClient.SqlCommand> can be configured to generate a notification when data changes after it has been fetched from the server and the result set would be different if the query were executed again.</span></span> <span data-ttu-id="d8c34-104">Cette fonction est utile dans les scénarios où vous voulez utiliser des files d'attente de notification personnalisées sur le serveur ou lorsque vous ne souhaitez pas conserver des objets actifs.</span><span class="sxs-lookup"><span data-stu-id="d8c34-104">This is useful for scenarios where you want to use custom notification queues on the server or when you do not want to maintain live objects.</span></span>

## <a name="creating-the-notification-request"></a><span data-ttu-id="d8c34-105">Création de la demande de notification</span><span class="sxs-lookup"><span data-stu-id="d8c34-105">Creating the Notification Request</span></span>

<span data-ttu-id="d8c34-106">Vous pouvez utiliser un objet <xref:System.Data.Sql.SqlNotificationRequest> pour créer la demande de notification en le liant à un objet `SqlCommand`.</span><span class="sxs-lookup"><span data-stu-id="d8c34-106">You can use a <xref:System.Data.Sql.SqlNotificationRequest> object to create the notification request by binding it to a `SqlCommand` object.</span></span> <span data-ttu-id="d8c34-107">Une fois la demande créée, vous n'avez plus besoin de l'objet `SqlNotificationRequest`.</span><span class="sxs-lookup"><span data-stu-id="d8c34-107">Once the request is created, you no longer need the `SqlNotificationRequest` object.</span></span> <span data-ttu-id="d8c34-108">Vous pouvez interroger la file d'attente pour toute notification et réagir de façon appropriée.</span><span class="sxs-lookup"><span data-stu-id="d8c34-108">You can query the queue for any notifications and respond appropriately.</span></span> <span data-ttu-id="d8c34-109">Des notifications peuvent survenir même si l'application est arrêtée, puis redémarrée.</span><span class="sxs-lookup"><span data-stu-id="d8c34-109">Notifications can occur even if the application is shut down and subsequently restarted.</span></span>

<span data-ttu-id="d8c34-110">Lorsque la commande avec la notification associée est exécutée, toute modification du jeu de résultats d'origine déclenche l'envoi d'un message à la file d'attente SQL Server qui a été configurée dans la demande de notification.</span><span class="sxs-lookup"><span data-stu-id="d8c34-110">When the command with the associated notification is executed, any changes to the original result set trigger sending a message to the SQL Server queue that was configured in the notification request.</span></span>

<span data-ttu-id="d8c34-111">La manière dont vous interrogez la file d'attente SQL Server et interprétez le message est spécifique à votre application.</span><span class="sxs-lookup"><span data-stu-id="d8c34-111">How you poll the SQL Server queue and interpret the message is specific to your application.</span></span> <span data-ttu-id="d8c34-112">L'application est chargée d'interroger la file d'attente et de réagir en fonction du contenu du message.</span><span class="sxs-lookup"><span data-stu-id="d8c34-112">The application is responsible for polling the queue and reacting based on the contents of the message.</span></span>

> [!NOTE]
> <span data-ttu-id="d8c34-113">Lors de l'utilisation de demandes de notification SQL Server avec <xref:System.Data.SqlClient.SqlDependency>, créez votre propre nom de file d'attente au lieu d'utiliser le nom de service par défaut.</span><span class="sxs-lookup"><span data-stu-id="d8c34-113">When using SQL Server notification requests with <xref:System.Data.SqlClient.SqlDependency>, create your own queue name instead of using the default service name.</span></span>

<span data-ttu-id="d8c34-114">Il n'y a pas de nouveaux éléments de sécurité côté client pour <xref:System.Data.Sql.SqlNotificationRequest>.</span><span class="sxs-lookup"><span data-stu-id="d8c34-114">There are no new client-side security elements for <xref:System.Data.Sql.SqlNotificationRequest>.</span></span> <span data-ttu-id="d8c34-115">Il s’agit principalement d’une fonctionnalité du serveur et le serveur a créé des privilèges spéciaux dont les utilisateurs doivent disposer pour demander une notification.</span><span class="sxs-lookup"><span data-stu-id="d8c34-115">This is primarily a server feature, and the server has created special privileges that users must have to request a notification.</span></span>

### <a name="example"></a><span data-ttu-id="d8c34-116">Exemple</span><span class="sxs-lookup"><span data-stu-id="d8c34-116">Example</span></span>

<span data-ttu-id="d8c34-117">Le fragment de code ci-dessous montre comment créer un <xref:System.Data.Sql.SqlNotificationRequest> et l'associer à un <xref:System.Data.SqlClient.SqlCommand>.</span><span class="sxs-lookup"><span data-stu-id="d8c34-117">The following code fragment demonstrates how to create a <xref:System.Data.Sql.SqlNotificationRequest> and associate it with a <xref:System.Data.SqlClient.SqlCommand>.</span></span>

```vb
' Assume connection is an open SqlConnection.
' Create a new SqlCommand object.
Dim command As New SqlCommand( _
  "SELECT ShipperID, CompanyName, Phone FROM dbo.Shippers", connection)

' Create a SqlNotificationRequest object.
Dim notifcationRequest As New SqlNotificationRequest()
notificationRequest.id = "NotificationID"
notificationRequest.Service = "mySSBQueue"

' Associate the notification request with the command.
command.Notification = notificationRequest
' Execute the command.
command.ExecuteReader()
' Process the DataReader.
' You can use Transact-SQL syntax to periodically poll the
' SQL Server queue to see if you have a new message.
```

```csharp
// Assume connection is an open SqlConnection.
// Create a new SqlCommand object.
SqlCommand command=new SqlCommand(
 "SELECT ShipperID, CompanyName, Phone FROM dbo.Shippers", connection);

// Create a SqlNotificationRequest object.
SqlNotificationRequest notificationRequest=new SqlNotificationRequest();
notificationRequest.id="NotificationID";
notificationRequest.Service="mySSBQueue";

// Associate the notification request with the command.
command.Notification=notificationRequest;
// Execute the command.
command.ExecuteReader();
// Process the DataReader.
// You can use Transact-SQL syntax to periodically poll the
// SQL Server queue to see if you have a new message.
```

## <a name="see-also"></a><span data-ttu-id="d8c34-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d8c34-118">See also</span></span>

- [<span data-ttu-id="d8c34-119">Notifications de requête dans SQL Server</span><span class="sxs-lookup"><span data-stu-id="d8c34-119">Query Notifications in SQL Server</span></span>](query-notifications-in-sql-server.md)
- [<span data-ttu-id="d8c34-120">Vue d’ensemble d’ADO.NET</span><span class="sxs-lookup"><span data-stu-id="d8c34-120">ADO.NET Overview</span></span>](../ado-net-overview.md)
