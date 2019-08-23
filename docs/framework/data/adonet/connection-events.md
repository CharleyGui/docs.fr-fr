---
title: Événements de connexion
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 5a29de74-acfc-4134-8616-829dd7ce0710
ms.openlocfilehash: 8ed62d0193639b434d66c446e3b9d0c184577a80
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69949559"
---
# <a name="connection-events"></a>Événements de connexion
Tous les fournisseurs de données .NET Framework ont des objets de **connexion** avec deux événements que vous pouvez utiliser pour extraire des messages d’information d’une source de données ou pour déterminer si l’état d’une **connexion** a changé. Le tableau suivant décrit les événements de l’objet de **connexion** .  
  
|Événement|Description|  
|-----------|-----------------|  
|**InfoMessage**|Se produit lorsqu'un message d'information est retourné à partir d'une source de données. Les messages d'information sont des messages provenant d'une source de données qui ne se traduisent pas par la levée d'une exception.|  
|**StateChange**|Se produit lorsque l’état de la **connexion** change.|  
  
## <a name="working-with-the-infomessage-event"></a>Utilisation de l'événement InfoMessage  
 Vous pouvez extraire des messages d'avertissement et d'information d'une source de données SQL Server à l'aide de l'événement <xref:System.Data.SqlClient.SqlConnection.InfoMessage> de l'objet <xref:System.Data.SqlClient.SqlConnection>. Les erreurs retournées par la source de données, dont le niveau de gravité est compris entre 11 et 16, lèvent une exception. L'événement <xref:System.Data.SqlClient.SqlConnection.InfoMessage> peut néanmoins être utilisé pour obtenir des messages de la source de données qui ne sont pas associés à une erreur. Dans le cas de Microsoft SQL Server, toute erreur dont le niveau de gravité est inférieur ou égal à 10 est considérée comme étant un message d'information et peut être capturée à l'aide de l'événement <xref:System.Data.SqlClient.SqlConnection.InfoMessage>. Pour plus d’informations, consultez l’article sur les gravités d' [erreur moteur de base de données](/sql/relational-databases/errors-events/database-engine-error-severities) .
  
 L' <xref:System.Data.SqlClient.SqlConnection.InfoMessage> événement<xref:System.Data.SqlClient.SqlInfoMessageEventArgs> reçoit un objet contenant, dans sa propriété Errors, une collection des messages de la source de données. Vous pouvez interroger les objets d' **erreur** de cette collection pour obtenir le numéro d’erreur et le texte du message, ainsi que la source de l’erreur. Le fournisseur de données .NET Framework pour SQL Server contient aussi des détails concernant la base de données, la procédure stockée et le numéro de la ligne d'origine du message.  
  
### <a name="example"></a>Exemples  
 L'exemple de code suivant montre comment ajouter un gestionnaire d'événements pour l'événement <xref:System.Data.SqlClient.SqlConnection.InfoMessage>.  
  
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
  
## <a name="handling-errors-as-infomessages"></a>Gestion des erreurs comme des InfoMessages  
 L'événement <xref:System.Data.SqlClient.SqlConnection.InfoMessage> se déclenche uniquement pour les messages d'information et d'avertissement en provenance du serveur. Toutefois, lorsqu’une erreur réelle se produit, l’exécution de la méthode **ExecuteNonQuery** ou **ExecuteReader** qui a initié l’opération du serveur est arrêtée et une exception est levée.  
  
 Si vous souhaitez continuer à traiter le reste des instructions d'une commande indépendamment des erreurs générées par le serveur, définissez la propriété <xref:System.Data.SqlClient.SqlConnection.FireInfoMessageEventOnUserErrors%2A> de l'objet <xref:System.Data.SqlClient.SqlConnection> sur `true`. Cela a pour effet de déclencher l'événement <xref:System.Data.SqlClient.SqlConnection.InfoMessage> pour des erreurs, au lieu de lever une exception et d'interrompre le traitement. L'application cliente peut ensuite gérer cet événement et répondre à des conditions d'erreur.  
  
> [!NOTE]
> Une erreur dont le niveau de gravité est égal ou supérieur à 17 qui entraîne un arrêt de traitement de la commande par le serveur doit être gérée comme une exception. Dans ce cas, une exception est levée, indépendamment de la manière dont l'erreur est gérée dans l'événement <xref:System.Data.SqlClient.SqlConnection.InfoMessage>.  
  
## <a name="working-with-the-statechange-event"></a>Utilisation de l'événement StateChange  
 L’événement **StateChange** se produit lorsque l’état d’une **connexion** change. L’événement **StateChange** Receive <xref:System.Data.StateChangeEventArgs> , qui vous permet de déterminer la modification de l’état de la **connexion** à l’aide des propriétés **OriginalState** et **CurrentState** . La propriété **OriginalState** est une <xref:System.Data.ConnectionState> Énumération qui indique l’état de la **connexion** avant sa modification. **CurrentState** est une <xref:System.Data.ConnectionState> Énumération qui indique l’état de la **connexion** après sa modification.  
  
 L’exemple de code suivant utilise l’événement **StateChange** pour écrire un message dans la console lorsque l’état de la **connexion** change.  
  
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
  
## <a name="see-also"></a>Voir aussi

- [Connexion à une source de données](../../../../docs/framework/data/adonet/connecting-to-a-data-source.md)
- [Fournisseurs managés ADO.NET et centre de développement DataSet](https://go.microsoft.com/fwlink/?LinkId=217917)
