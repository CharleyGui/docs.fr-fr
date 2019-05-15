---
title: Consommation de flux OData à partir d’un flux de travail - WF
ms.date: 03/30/2017
ms.assetid: 1b26617c-53e9-476a-81af-675c36d95919
ms.openlocfilehash: e7d5230bb15474d63b2381d3906e07e48ac0134d
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/14/2019
ms.locfileid: "65592981"
---
# <a name="consuming-odata-feeds-from-a-workflow"></a>Consommation de flux OData à partir d’un flux de travail

WCF Data Services est un composant du .NET Framework qui vous permet de créer des services qui utilisent le protocole Open Data Protocol (OData) pour exposer et consommer des données sur le Web ou l’intranet à l’aide de la sémantique representational state Transfer (REST). OData expose les données sous forme de ressources adressables par des URI. Toute application peut interagir avec un service de données basé sur OData si elle peut envoyer une requête HTTP et traiter le flux OData retourné par un service de données. En outre, WCF Data Services inclut des bibliothèques clientes qui fournissent une expérience en programmation plus riche lorsque vous consommez des flux OData à partir d’applications .NET Framework. Cette rubrique fournit une vue d'ensemble de la consommation d'un flux OData dans un workflow avec et sans l'utilisation de bibliothèques clientes.

## <a name="using-the-sample-northwind-odata-service"></a>À l’aide de l’exemple de service Northwind OData

Les exemples de cette rubrique utilisent l’exemple de service de données Northwind à l’adresse [ http://services.odata.org/Northwind/Northwind.svc/ ](https://go.microsoft.com/fwlink/?LinkID=187426). Ce service fait partie du [SDK OData](https://go.microsoft.com/fwlink/?LinkID=185248) et fournit un accès en lecture seule à l’exemple de base de données Northwind. Si vous souhaitez un accès en écriture ou un service de données WCF local, vous pouvez suivre la procédure de [démarrage rapide WCF Data Services](https://go.microsoft.com/fwlink/?LinkID=131076) pour créer un service OData local qui donne accès à la base de données Northwind. Si vous suivez la procédure de démarrage rapide, remplacez l'URI local par celui fourni dans l'exemple de code de cette rubrique.

## <a name="consuming-an-odata-feed-using-the-client-libraries"></a>Consommation d’un OData flux à l’aide de bibliothèques clientes

WCF Data Services inclut des bibliothèques clientes qui vous permettent de consommer plus facilement un flux OData depuis .NET Framework et les applications clientes. Ces bibliothèques simplifient l'envoi et la réception des messages HTTP. Elles traduisent également la charge utile de message dans les objets CLR qui représentent des données d'entité. Les bibliothèques clientes comprennent les deux classes principales <xref:System.Data.Services.Client.DataServiceContext> et <xref:System.Data.Services.Client.DataServiceQuery%601>. Ces classes vous permettent d'interroger un service de données, puis d'utiliser les données d'entité retournées sous forme d'objets CLR. Cette rubrique décrit deux approches de création d'activités qui utilisent les bibliothèques clientes.

### <a name="adding-a-service-reference-to-the-wcf-data-service"></a>Ajout d’une référence de service pour le service de données WCF

Pour générer les bibliothèques clientes Northwind, vous pouvez utiliser la **ajouter une référence de Service** boîte de dialogue dans Visual Studio 2012 pour ajouter une référence au service Northwind OData.

![Capture d’écran qui affiche la boîte de dialogue Ajouter une référence de Service.](./media/consuming-odata-feeds-from-a-workflow/add-service-reference-dialog.gif)

Notez qu'aucune opération du service n'est exposée par le service et que la liste **Services** contient des éléments représentant les entités exposées par le service de données Northwind. Lorsqu'une référence de service est ajoutée, les classes sont générées pour ces entités et peuvent être utilisées dans le code client. Les exemples de cette rubrique utilisent ces classes et la classe `NorthwindEntities` pour exécuter les requêtes.

> [!NOTE]
> Pour plus d’informations, consultez [génération de la bibliothèque de Client de Service de données (WCF Data Services)](../data/wcf/generating-the-data-service-client-library-wcf-data-services.md).

### <a name="using-asynchronous-methods"></a>À l’aide de méthodes asynchrones

Pour résoudre les problèmes de latence possibles qui peuvent se produire lors de l'accès aux ressources sur le Web, il est recommandé d'accéder à WCF Data Services de façon asynchrone. Les bibliothèques de client WCF Data Services contiennent des méthodes asynchrones pour appeler les requêtes, et Windows Workflow Foundation (WF) fournit la <xref:System.Activities.AsyncCodeActivity> classe pour la création d’activités asynchrones. <xref:System.Activities.AsyncCodeActivity> activités dérivées peuvent être écrites pour tirer parti des classes de .NET Framework qui ont des méthodes asynchrones, ou le code doit être exécuté de façon asynchrone peut être inséré dans une méthode et appelé à l’aide d’un délégué. Cette section contient deux exemples d'une activité dérivée <xref:System.Activities.AsyncCodeActivity> ; une qui utilise les méthodes asynchrones des bibliothèques clientes WCF Data Services et une qui utilise un délégué.

> [!NOTE]
> Pour plus d’informations, consultez [opérations asynchrones (WCF Data Services)](../data/wcf/asynchronous-operations-wcf-data-services.md) et [création d’activités asynchrones](creating-asynchronous-activities-in-wf.md).

### <a name="using-client-library-asynchronous-methods"></a>À l’aide de méthodes asynchrones des bibliothèques de client

La classe <xref:System.Data.Services.Client.DataServiceQuery%601> fournit les méthodes <xref:System.Data.Services.Client.DataServiceQuery%601.BeginExecute%2A> et <xref:System.Data.Services.Client.DataServiceQuery%601.EndExecute%2A> pour interroger un service OData de façon asynchrone. Ces méthodes peuvent être appelées à partir des substitutions <xref:System.Activities.AsyncCodeActivity.BeginExecute%2A> et <xref:System.Activities.AsyncCodeActivity.EndExecute%2A> d'une classe dérivée <xref:System.Activities.AsyncCodeActivity> . Si la substitution <xref:System.Activities.AsyncCodeActivity> <xref:System.Activities.AsyncCodeActivity.BeginExecute%2A> retourne, le workflow peut être inactif (mais pas persistant), et si la tâche asynchrone est terminée, la méthode <xref:System.Activities.AsyncCodeActivity.EndExecute%2A> est appelée par le runtime.

Dans l'exemple suivant, une activité `OrdersByCustomer` est définie et contient deux arguments d'entrée. L'argument `CustomerId` représente le client qui identifie les commandes à retourner, et l'argument `ServiceUri` représente l'URI du service Odata à interroger. Comme l'activité dérive de `AsyncCodeActivity<IEnumerable<Order>>` , il y a aussi un argument de sortie <xref:System.Activities.Activity%601.Result%2A> , utilisé pour retourner le résultat de la requête. La substitution <xref:System.Activities.AsyncCodeActivity.BeginExecute%2A> crée une requête LINQ qui sélectionne toutes les commandes du client spécifié. Cette requête est spécifiée comme <xref:System.Activities.AsyncCodeActivityContext.UserState%2A> du <xref:System.Activities.AsyncCodeActivityContext>passé, puis la méthode <xref:System.Data.Services.Client.DataServiceQuery%601.BeginExecute%2A> de la requête est appelée. Notez que le rappel et l'état qui sont passés à la méthode <xref:System.Data.Services.Client.DataServiceQuery%601.BeginExecute%2A> de la requête sont ceux qui sont passés à la méthode <xref:System.Activities.AsyncCodeActivity.BeginExecute%2A> de l'activité. Lorsque l'exécution de la requête est terminée, la méthode <xref:System.Activities.AsyncCodeActivity.EndExecute%2A> de l'activité est appelée. La requête est récupérée dans la propriété <xref:System.Activities.AsyncCodeActivityContext.UserState%2A>, puis la méthode <xref:System.Data.Services.Client.DataServiceQuery%601.EndExecute%2A> de la requête est appelée. Cette méthode retourne un <xref:System.Collections.Generic.IEnumerable%601> du type d'entité spécifié, dans ce cas `Order`. `IEnumerable<Order>` étant le type générique de <xref:System.Activities.AsyncCodeActivity%601>, ce <xref:System.Collections.IEnumerable> est défini comme <xref:System.Activities.Activity%601.Result%2A> <xref:System.Activities.OutArgument%601> de l'activité.

[!code-csharp[CFX_WCFDataServicesActivityExample#100](~/samples/snippets/csharp/VS_Snippets_CFX/CFX_WCFDataServicesActivityExample/cs/Program.cs#100)]

Dans l'exemple suivant, l'activité `OrdersByCustomer` récupère une liste de commandes pour le client spécifié, puis une activité <xref:System.Activities.Statements.ForEach%601> énumère les commandes retournées et écrit la date de chacune d'elles dans la console.

[!code-csharp[CFX_WCFDataServicesActivityExample#10](~/samples/snippets/csharp/VS_Snippets_CFX/CFX_WCFDataServicesActivityExample/cs/Program.cs#10)]

Lorsque ce workflow est appelé, les données suivantes sont écrites dans la console :

```console
Calling WCF Data Service...
8/25/1997
10/3/1997
10/13/1997
1/15/1998
3/16/1998
4/9/1998
```

> [!NOTE]
> S'il est impossible d'établir une connexion au serveur OData, vous obtiendrez une exception semblable à la suivante :
>
> Exception non prise en charge : System.InvalidOperationException : Une erreur s’est produite lors du traitement de cette demande. ---> System.Net.WebException : Impossible de se connecter au serveur distant---> System.Net.Sockets.SocketException : Une tentative de connexion a échoué car la partie connectée n’a pas répondu convenablement après une période de temps ou la connexion établie a échoué, car l’hôte connecté n’a pas répondu.

Si un traitement supplémentaire des données retournées par la requête est nécessaire, il peut être effectué dans la substitution <xref:System.Activities.AsyncCodeActivity%601.EndExecute%2A> de l'activité. Les méthodes <xref:System.Activities.AsyncCodeActivity%601.BeginExecute%2A> et <xref:System.Activities.AsyncCodeActivity%601.EndExecute%2A> sont appelées à l'aide du thread de workflow, et le code de ces substitutions ne s'exécute pas de façon asynchrone. Si le traitement supplémentaire est étendu ou de longue durée, ou les résultats de la requête sont paginés, vous devez envisager d'adopter l'approche décrite dans la section suivante. Cette approche utilise un délégué pour exécuter la requête et effectuer le traitement supplémentaire de façon asynchrone.

### <a name="using-a-delegate"></a>À l’aide d’un délégué

En plus d’appeler la méthode asynchrone d’une classe .NET Framework, un <xref:System.Activities.AsyncCodeActivity>-activité basée sur peut également définir la logique asynchrone dans une de ses méthodes. Cette méthode est spécifiée en utilisant un délégué dans la substitution <xref:System.Activities.AsyncCodeActivity.BeginExecute%2A> de l'activité. Lorsque la méthode retourne, le runtime appelle la substitution <xref:System.Activities.AsyncCodeActivity.EndExecute%2A> de l'activité. Lors de l'appel d'un service OData d'un workflow, cette méthode peut être utilisée pour interroger le service et fournir un traitement supplémentaire.

Dans l'exemple suivant, une activité `ListCustomers` est définie. Cette activité interroge l'exemple de service de données Northwind et retourne un `List<Customer>` qui contient tous les clients dans la base de données Northwind. La tâche asynchrone est effectuée par la méthode `GetCustomers` . Cette méthode interroge le service pour tous les clients, puis les copie dans un `List<Customer>`. Elle vérifie ensuite si les résultats sont paginés. Le cas échéant, elle interroge le service pour la page suivante de résultats, les ajoute à la liste et continue jusqu'à ce que tous les clients aient été récupérés.

> [!NOTE]
> Pour plus d’informations sur la pagination dans WCF Data Services, consultez [Comment : Charge résultats paginés (WCF Data Services)](../data/wcf/how-to-load-paged-results-wcf-data-services.md).

Une fois tous les clients ajoutés, la liste est retournée. La méthode `GetCustomers` est spécifiée dans la substitution <xref:System.Activities.AsyncCodeActivity.BeginExecute%2A> de l'activité. Comme la méthode a une valeur de retour, un `Func<string, List<Customer>>` est créé pour spécifier la méthode.

> [!NOTE]
> Si la méthode qui effectue la tâche asynchrone n'a pas de valeur de retour, un <xref:System.Action> est utilisé à la place d'un <xref:System.Func%601>. Pour obtenir des exemples de création d’un exemple asynchrone à l’aide de ces deux approches, consultez [création d’activités asynchrones](creating-asynchronous-activities-in-wf.md).

Ce <xref:System.Func%601> est assigné au <xref:System.Activities.AsyncCodeActivityContext.UserState%2A>, puis `BeginInvoke` est appelé. Comme la méthode à appeler n'a pas accès à l'environnement des arguments de l'activité, la valeur de l'argument `ServiceUri` est passée comme premier paramètre, avec le rappel et l'état passés dans la méthode <xref:System.Activities.AsyncCodeActivity.BeginExecute%2A>. Lorsque `GetCustomers` retourne, le runtime appelle <xref:System.Activities.AsyncCodeActivity.EndExecute%2A>. Le code dans la méthode <xref:System.Activities.AsyncCodeActivity.EndExecute%2A> récupère le délégué à partir de la propriété <xref:System.Activities.AsyncCodeActivityContext.UserState%2A>, appelle `EndInvoke`, et retourne le résultat, qui correspond à la liste des clients retournés à partir de la méthode `GetCustomers` .

[!code-csharp[CFX_WCFDataServicesActivityExample#200](~/samples/snippets/csharp/VS_Snippets_CFX/CFX_WCFDataServicesActivityExample/cs/Program.cs#200)]

Dans l'exemple suivant, l'activité `ListCustomers` récupère une liste de clients, puis une activité <xref:System.Activities.Statements.ForEach%601> les énumère et écrit le nom de la société et du contact de chacun des clients dans la console.

[!code-csharp[CFX_WCFDataServicesActivityExample#20](~/samples/snippets/csharp/VS_Snippets_CFX/CFX_WCFDataServicesActivityExample/cs/Program.cs#20)]

Lorsque ce workflow est appelé, les données suivantes sont écrites dans la console : Comme cette requête retourne de nombreux clients, une seule partie du résultat s'affiche ici.

```console
Calling WCF Data Service...
Alfreds Futterkiste, Contact: Maria Anders
Ana Trujillo Emparedados y helados, Contact: Ana Trujillo
Antonio Moreno Taquería, Contact: Antonio Moreno
Around the Horn, Contact: Thomas Hardy
Berglunds snabbköp, Contact: Christina Berglund
...
```

## <a name="consuming-an-odata-feed-without-using-the-client-libraries"></a>Consommation d’un OData flux sans utiliser les bibliothèques clientes

OData expose les données sous forme de ressources adressables par des URI. Lorsque vous utilisez les bibliothèques clientes, ces URI sont créés pour vous, mais vous n'avez pas besoin d'utiliser les bibliothèques clientes. Si vous le souhaitez, vous pouvez accéder aux services OData directement sans utiliser les bibliothèques clientes. Le cas échéant, l'emplacement du service et les données voulues sont spécifiés par l'URI et les résultats sont retournés dans la réponse à la requête HTTP. Vous pouvez ensuite traiter ou manipuler ces données brutes de la façon appropriée. Pour récupérer les résultats d'une requête OData, vous pouvez utiliser la classe <xref:System.Net.WebClient> . Dans cet exemple, le contact du client représenté par la clé ALFKI est récupéré.

[!code-csharp[CFX_WCFDataServicesActivityExample#2](~/samples/snippets/csharp/VS_Snippets_CFX/CFX_WCFDataServicesActivityExample/cs/Program.cs#2)]

Lorsque ce code s'exécute, la sortie suivante s'affiche sur la console :

```console
Raw data returned:
<?xml version="1.0" encoding="utf-8" standalone="yes"?>
<ContactName xmlns="http://schemas.microsoft.com/ado/2007/08/dataservices">Maria Anders</ContactName>
```

Dans un workflow, le code de cet exemple peut être incorporé dans la substitution <xref:System.Activities.CodeActivity.Execute%2A> d'une activité personnalisée basée sur <xref:System.Activities.CodeActivity>, mais cette même fonctionnalité peut aussi être obtenue à l'aide de l'activité <xref:System.Activities.Expressions.InvokeMethod%601>. L'activité <xref:System.Activities.Expressions.InvokeMethod%601> permet aux auteurs de workflow d'appeler des méthodes d'instance et statiques d'une classe, ainsi que d'appeler la méthode spécifiée de façon asynchrone. Dans l'exemple suivant, une activité <xref:System.Activities.Expressions.InvokeMethod%601> est configurée pour appeler la méthode <xref:System.Net.WebClient.DownloadString%2A> de la classe <xref:System.Net.WebClient> et retourner une liste de clients.

[!code-csharp[CFX_WCFDataServicesActivityExample#3](~/samples/snippets/csharp/VS_Snippets_CFX/CFX_WCFDataServicesActivityExample/cs/Program.cs#3)]

<xref:System.Activities.Expressions.InvokeMethod%601> peut appeler à la fois des méthodes d'instance et statiques d'une classe. Comme <xref:System.Net.WebClient.DownloadString%2A> est une méthode d'instance de la classe <xref:System.Net.WebClient> , une nouvelle instance de la classe <xref:System.Net.WebClient> est spécifiée pour <xref:System.Activities.Expressions.InvokeMethod%601.TargetObject%2A>. `DownloadString` est spécifiée pour la propriété <xref:System.Activities.Expressions.InvokeMethod%601.MethodName%2A>, l'URI qui contient la requête est spécifié dans la collection <xref:System.Activities.Expressions.InvokeMethod%601.Parameters%2A> , et la propriété <xref:System.Activities.Activity%601.Result%2A> est affectée à la valeur de retour. La valeur <xref:System.Activities.Expressions.InvokeMethod%601.RunAsynchronously%2A> est affectée à la propriété `true`, ce qui signifie que l'appel de la méthode s'exécutera de façon asynchrone par rapport au workflow. Dans l'exemple suivant, un workflow est construit qui utilise l'activité <xref:System.Activities.Expressions.InvokeMethod%601> pour interroger l'exemple de service de données Northwind pour une liste de commandes d'un client spécifique, puis les données retournées sont écrites dans la console.

[!code-csharp[CFX_WCFDataServicesActivityExample#1](~/samples/snippets/csharp/VS_Snippets_CFX/CFX_WCFDataServicesActivityExample/cs/Program.cs#1)]

Lorsque ce workflow est appelé, la sortie suivante s'affiche sur la console. Comme cette requête retourne plusieurs commandes, une seule partie du résultat s'affiche ici.

```console
Calling WCF Data Service...
Raw data returned:

<?xml version="1.0" encoding="utf-8" standalone="yes"?>*
<feed
xml:base="http://services.odata.org/Northwind/Northwind.svc/"
xmlns:d="http://schemas.microsoft.com/ado/2007/08/dataservices"
xmlns:m="http://schemas.microsoft.com/ado/2007/08/dataservices/metadata"
xmlns="http://www.w3.org/2005/Atom">
<title type="text">Orders\</title>
<id>http://services.odata.org/Northwind/Northwind.svc/Customers('ALFKI')/Orders\</id>
<updated>2010-05-19T19:37:07Z\</updated>
<link rel="self" title="Orders" href="Orders" />
<entry>
<id>http://services.odata.org/Northwind/Northwind.svc/Orders(10643)\</id>
<title type="text">\</title>
<updated>2010-05-19T19:37:07Z\</updated>
<author>
<name />
</author>
<link rel="edit" title="Order" href="Orders(10643)" />
<link rel="http://schemas.microsoft.com/ado/2007/08/dataservices/related/Customer" type="application/atom+xml;type=entry" title="Customer" href="Orders(10643)/Customer" />
...
```

Cet exemple fournit une méthode que les auteurs d'applications de workflow peuvent utiliser pour consommer les données brutes retournées par un service OData. Pour plus d’informations sur l’accès aux Services de données WCF à l’aide d’URI, consultez [accès aux ressources de Service de données (WCF Data Services)](../data/wcf/accessing-data-service-resources-wcf-data-services.md) et [OData : Conventions d’URI](https://go.microsoft.com/fwlink/?LinkId=185564).
