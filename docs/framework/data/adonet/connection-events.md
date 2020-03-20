---
title: Événements de connexion
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 5a29de74-acfc-4134-8616-829dd7ce0710
ms.openlocfilehash: a7ad0d4d950da71db0aebca872949fa82669c5c5
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79151698"
---
# <a name="connection-events"></a><span data-ttu-id="0a537-102">Événements de connexion</span><span class="sxs-lookup"><span data-stu-id="0a537-102">Connection Events</span></span>
<span data-ttu-id="0a537-103">Tous les fournisseurs de données .NET Framework ont des objets **de connexion** avec deux événements que vous pouvez utiliser pour récupérer des messages d’information à partir d’une source de données ou pour déterminer si l’état d’une **connexion** a changé.</span><span class="sxs-lookup"><span data-stu-id="0a537-103">All of the .NET Framework data providers have **Connection** objects with two events that you can use to retrieve informational messages from a data source or to determine if the state of a **Connection** has changed.</span></span> <span data-ttu-id="0a537-104">Le tableau suivant décrit les événements de l’objet **Connection.**</span><span class="sxs-lookup"><span data-stu-id="0a537-104">The following table describes the events of the **Connection** object.</span></span>  
  
|<span data-ttu-id="0a537-105">Événement</span><span class="sxs-lookup"><span data-stu-id="0a537-105">Event</span></span>|<span data-ttu-id="0a537-106">Description</span><span class="sxs-lookup"><span data-stu-id="0a537-106">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="0a537-107">**InfoMessage InfoMessage**</span><span class="sxs-lookup"><span data-stu-id="0a537-107">**InfoMessage**</span></span>|<span data-ttu-id="0a537-108">Se produit lorsqu'un message d'information est retourné à partir d'une source de données.</span><span class="sxs-lookup"><span data-stu-id="0a537-108">Occurs when an informational message is returned from a data source.</span></span> <span data-ttu-id="0a537-109">Les messages d'information sont des messages provenant d'une source de données qui ne se traduisent pas par la levée d'une exception.</span><span class="sxs-lookup"><span data-stu-id="0a537-109">Informational messages are messages from a data source that do not result in an exception being thrown.</span></span>|  
|<span data-ttu-id="0a537-110">**StateChange**</span><span class="sxs-lookup"><span data-stu-id="0a537-110">**StateChange**</span></span>|<span data-ttu-id="0a537-111">Se produit lorsque l’état de la **connexion** change.</span><span class="sxs-lookup"><span data-stu-id="0a537-111">Occurs when the state of the **Connection** changes.</span></span>|  
  
## <a name="working-with-the-infomessage-event"></a><span data-ttu-id="0a537-112">Utilisation de l'événement InfoMessage</span><span class="sxs-lookup"><span data-stu-id="0a537-112">Working with the InfoMessage Event</span></span>  
 <span data-ttu-id="0a537-113">Vous pouvez extraire des messages d'avertissement et d'information d'une source de données SQL Server à l'aide de l'événement <xref:System.Data.SqlClient.SqlConnection.InfoMessage> de l'objet <xref:System.Data.SqlClient.SqlConnection>.</span><span class="sxs-lookup"><span data-stu-id="0a537-113">You can retrieve warnings and informational messages from a SQL Server data source using the <xref:System.Data.SqlClient.SqlConnection.InfoMessage> event of the <xref:System.Data.SqlClient.SqlConnection> object.</span></span> <span data-ttu-id="0a537-114">Les erreurs retournées par la source de données, dont le niveau de gravité est compris entre 11 et 16, lèvent une exception.</span><span class="sxs-lookup"><span data-stu-id="0a537-114">Errors returned from the data source with a severity level of 11 through 16 cause an exception to be thrown.</span></span> <span data-ttu-id="0a537-115">L'événement <xref:System.Data.SqlClient.SqlConnection.InfoMessage> peut néanmoins être utilisé pour obtenir des messages de la source de données qui ne sont pas associés à une erreur.</span><span class="sxs-lookup"><span data-stu-id="0a537-115">However, the <xref:System.Data.SqlClient.SqlConnection.InfoMessage> event can be used to obtain messages from the data source that are not associated with an error.</span></span> <span data-ttu-id="0a537-116">Dans le cas de Microsoft SQL Server, toute erreur dont le niveau de gravité est inférieur ou égal à 10 est considérée comme étant un message d'information et peut être capturée à l'aide de l'événement <xref:System.Data.SqlClient.SqlConnection.InfoMessage>.</span><span class="sxs-lookup"><span data-stu-id="0a537-116">In the case of Microsoft SQL Server, any error with a severity of 10 or less is considered to be an informational message, and can be captured by using the <xref:System.Data.SqlClient.SqlConnection.InfoMessage> event.</span></span> <span data-ttu-id="0a537-117">Pour plus d’informations, consultez l’article [de la séparation des erreurs du moteur de base de données.](/sql/relational-databases/errors-events/database-engine-error-severities)</span><span class="sxs-lookup"><span data-stu-id="0a537-117">For more information, see the [Database Engine Error Severities](/sql/relational-databases/errors-events/database-engine-error-severities) article.</span></span>
  
 <span data-ttu-id="0a537-118">L’événement <xref:System.Data.SqlClient.SqlConnection.InfoMessage> <xref:System.Data.SqlClient.SqlInfoMessageEventArgs> reçoit un objet contenant, dans sa propriété **Errors,** une collection des messages de la source de données.</span><span class="sxs-lookup"><span data-stu-id="0a537-118">The <xref:System.Data.SqlClient.SqlConnection.InfoMessage> event receives an <xref:System.Data.SqlClient.SqlInfoMessageEventArgs> object containing, in its **Errors** property, a collection of the messages from the data source.</span></span> <span data-ttu-id="0a537-119">Vous pouvez interroger les objets **d’erreur** dans cette collection pour le numéro d’erreur et le texte de message, ainsi que la source de l’erreur.</span><span class="sxs-lookup"><span data-stu-id="0a537-119">You can query the **Error** objects in this collection for the error number and message text, as well as the source of the error.</span></span> <span data-ttu-id="0a537-120">Le fournisseur de données .NET Framework pour SQL Server contient aussi des détails concernant la base de données, la procédure stockée et le numéro de la ligne d'origine du message.</span><span class="sxs-lookup"><span data-stu-id="0a537-120">The .NET Framework Data Provider for SQL Server also includes detail about the database, stored procedure, and line number that the message came from.</span></span>  
  
### <a name="example"></a><span data-ttu-id="0a537-121"> Exemple</span><span class="sxs-lookup"><span data-stu-id="0a537-121">Example</span></span>  
 <span data-ttu-id="0a537-122">L'exemple de code suivant montre comment ajouter un gestionnaire d'événements pour l'événement <xref:System.Data.SqlClient.SqlConnection.InfoMessage>.</span><span class="sxs-lookup"><span data-stu-id="0a537-122">The following code example shows how to add an event handler for the <xref:System.Data.SqlClient.SqlConnection.InfoMessage> event.</span></span>  
  
```vb  
' Assumes that connection represents a SqlConnection object.  
  AddHandler connection.InfoMessage, _  
    New SqlInfoMessageEventHandler(AddressOf OnInfoMessage)  
  
Private Shared Sub OnInfoMessage(sender As Object, _  
  args As SqlInfoMessageEventArgs)  
  Dim err As SqlError  
  For Each err In args.Errors  
    Console.WriteLine("The {0} has received a severity {1}, _  
       state {2} error number {3}\n" & _  
      "on line {4} of procedure {5} on server {6}:\n{7}", _  
      err.Source, err.Class, err.State, err.Number, err.LineNumber, _  
    err.Procedure, err.Server, err.Message)  
  Next  
End Sub  
```  
  
```csharp  
// Assumes that connection represents a SqlConnection object.  
  connection.InfoMessage +=
    new SqlInfoMessageEventHandler(OnInfoMessage);  
  
protected static void OnInfoMessage(  
  object sender, SqlInfoMessageEventArgs args)  
{  
  foreach (SqlError err in args.Errors)  
  {  
    Console.WriteLine(  
  "The {0} has received a severity {1}, state {2} error number {3}\n" +  
  "on line {4} of procedure {5} on server {6}:\n{7}",  
   err.Source, err.Class, err.State, err.Number, err.LineNumber,
   err.Procedure, err.Server, err.Message);  
  }  
}  
```  
  
## <a name="handling-errors-as-infomessages"></a><span data-ttu-id="0a537-123">Gestion des erreurs comme des InfoMessages</span><span class="sxs-lookup"><span data-stu-id="0a537-123">Handling Errors as InfoMessages</span></span>  
 <span data-ttu-id="0a537-124">L'événement <xref:System.Data.SqlClient.SqlConnection.InfoMessage> se déclenche uniquement pour les messages d'information et d'avertissement en provenance du serveur.</span><span class="sxs-lookup"><span data-stu-id="0a537-124">The <xref:System.Data.SqlClient.SqlConnection.InfoMessage> event will normally fire only for informational and warning messages that are sent from the server.</span></span> <span data-ttu-id="0a537-125">Toutefois, lorsqu’une erreur réelle se produit, l’exécution de la méthode **ExecuteNonQuery** ou **ExecuteReader** qui a lancé l’opération du serveur est interrompue et une exception est lancée.</span><span class="sxs-lookup"><span data-stu-id="0a537-125">However, when an actual error occurs, the execution of the **ExecuteNonQuery** or **ExecuteReader** method that initiated the server operation is halted and an exception is thrown.</span></span>  
  
 <span data-ttu-id="0a537-126">Si vous souhaitez continuer à traiter le reste des instructions d'une commande indépendamment des erreurs générées par le serveur, définissez la propriété <xref:System.Data.SqlClient.SqlConnection.FireInfoMessageEventOnUserErrors%2A> de l'objet <xref:System.Data.SqlClient.SqlConnection> sur `true`.</span><span class="sxs-lookup"><span data-stu-id="0a537-126">If you want to continue processing the rest of the statements in a command regardless of any errors produced by the server, set the <xref:System.Data.SqlClient.SqlConnection.FireInfoMessageEventOnUserErrors%2A> property of the <xref:System.Data.SqlClient.SqlConnection> to `true`.</span></span> <span data-ttu-id="0a537-127">Cela a pour effet de déclencher l'événement <xref:System.Data.SqlClient.SqlConnection.InfoMessage> pour des erreurs, au lieu de lever une exception et d'interrompre le traitement.</span><span class="sxs-lookup"><span data-stu-id="0a537-127">Doing this causes the connection to fire the <xref:System.Data.SqlClient.SqlConnection.InfoMessage> event for errors instead of throwing an exception and interrupting processing.</span></span> <span data-ttu-id="0a537-128">L'application cliente peut ensuite gérer cet événement et répondre à des conditions d'erreur.</span><span class="sxs-lookup"><span data-stu-id="0a537-128">The client application can then handle this event and respond to error conditions.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="0a537-129">Une erreur dont le niveau de gravité est égal ou supérieur à 17 qui entraîne un arrêt de traitement de la commande par le serveur doit être gérée comme une exception.</span><span class="sxs-lookup"><span data-stu-id="0a537-129">An error with a severity level of 17 or above that causes the server to stop processing the command must be handled as an exception.</span></span> <span data-ttu-id="0a537-130">Dans ce cas, une exception est levée, indépendamment de la manière dont l'erreur est gérée dans l'événement <xref:System.Data.SqlClient.SqlConnection.InfoMessage>.</span><span class="sxs-lookup"><span data-stu-id="0a537-130">In this case, an exception is thrown regardless of how the error is handled in the <xref:System.Data.SqlClient.SqlConnection.InfoMessage> event.</span></span>  
  
## <a name="working-with-the-statechange-event"></a><span data-ttu-id="0a537-131">Utilisation de l'événement StateChange</span><span class="sxs-lookup"><span data-stu-id="0a537-131">Working with the StateChange Event</span></span>  
 <span data-ttu-id="0a537-132">**L’événement StateChange** se produit lorsque l’état d’une **connexion** change.</span><span class="sxs-lookup"><span data-stu-id="0a537-132">The **StateChange** event occurs when the state of a **Connection** changes.</span></span> <span data-ttu-id="0a537-133">**L’événement StateChange** <xref:System.Data.StateChangeEventArgs> reçoit qui vous permettent de déterminer le changement d’état de la **connexion** en utilisant les propriétés **OriginalState** et **CurrentState.**</span><span class="sxs-lookup"><span data-stu-id="0a537-133">The **StateChange** event receives <xref:System.Data.StateChangeEventArgs> that enable you to determine the change in state of the **Connection** by using the **OriginalState** and **CurrentState** properties.</span></span> <span data-ttu-id="0a537-134">La propriété **OriginalState** est un <xref:System.Data.ConnectionState> recensement qui indique l’état de la **connexion** avant qu’il ne change.</span><span class="sxs-lookup"><span data-stu-id="0a537-134">The **OriginalState** property is a <xref:System.Data.ConnectionState> enumeration that indicates the state of the **Connection** before it changed.</span></span> <span data-ttu-id="0a537-135">**CurrentState** est <xref:System.Data.ConnectionState> un recensement qui indique l’état de la **connexion** après qu’il a changé.</span><span class="sxs-lookup"><span data-stu-id="0a537-135">**CurrentState** is a <xref:System.Data.ConnectionState> enumeration that indicates the state of the **Connection** after it changed.</span></span>  
  
 <span data-ttu-id="0a537-136">L’exemple de code suivant utilise **l’événement StateChange** pour écrire un message à la console lorsque l’état de la **connexion** change.</span><span class="sxs-lookup"><span data-stu-id="0a537-136">The following code example uses the **StateChange** event to write a message to the console when the state of the **Connection** changes.</span></span>  
  
```vb  
' Assumes connection represents a SqlConnection object.  
  AddHandler connection.StateChange, _  
    New StateChangeEventHandler(AddressOf OnStateChange)  
  
Protected Shared Sub OnStateChange( _  
  sender As Object, args As StateChangeEventArgs)  
  
  Console.WriteLine( _  
  "The current Connection state has changed from {0} to {1}.", _  
  args.OriginalState, args.CurrentState)  
End Sub  
```  
  
```csharp  
// Assumes connection represents a SqlConnection object.  
  connection.StateChange  += new StateChangeEventHandler(OnStateChange);  
  
protected static void OnStateChange(object sender,
  StateChangeEventArgs args)  
{  
  Console.WriteLine(  
    "The current Connection state has changed from {0} to {1}.",  
      args.OriginalState, args.CurrentState);  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="0a537-137">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="0a537-137">See also</span></span>

- [<span data-ttu-id="0a537-138">Connexion à une source de données</span><span class="sxs-lookup"><span data-stu-id="0a537-138">Connecting to a Data Source</span></span>](connecting-to-a-data-source.md)
- [<span data-ttu-id="0a537-139">Vue d'ensemble d’ADO.NET</span><span class="sxs-lookup"><span data-stu-id="0a537-139">ADO.NET Overview</span></span>](ado-net-overview.md)
