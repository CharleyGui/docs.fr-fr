---
title: Spécification du transfert de données dans des contrats de service
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- service contracts [WCF], data transfer
ms.assetid: 7c5a26c8-89c9-4bcb-a4bc-7131e6d01f0c
ms.openlocfilehash: e68ca46f9d2c562491063ae66754c469dbe0898e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79184426"
---
# <a name="specifying-data-transfer-in-service-contracts"></a>Spécification du transfert de données dans des contrats de service
La Windows Communication Foundation (WCF) peut être considérée comme une infrastructure de messagerie. Les opérations de service peuvent recevoir des messages, les traiter et leur envoyer des messages. Les messages sont décrits à l'aide de contrats d'opérations. Par exemple, considérons le contrat suivant.  
  
```csharp  
[ServiceContract]  
public interface IAirfareQuoteService  
{  
    [OperationContract]  
    float GetAirfare(string fromCity, string toCity);  
}  
```  
  
```vb  
<ServiceContract()>  
Public Interface IAirfareQuoteService  
  
    <OperationContract()>  
    Function GetAirfare(fromCity As String, toCity As String) As Double  
End Interface  
```  
  
 Ici, l'opération `GetAirfare` accepte un message avec des informations à propos de `fromCity` et `toCity`, puis retourne un message qui contient un nombre.  
  
 Cette rubrique explique les différentes manières par lesquelles un contrat d'opération peut décrire des messages.  
  
## <a name="describing-messages-by-using-parameters"></a>Description de messages à l'aide de paramètres  
 La méthode la plus simple pour décrire un message consiste à utiliser une liste de paramètres et la valeur de retour. Dans l'exemple précédent, les paramètres de chaîne `fromCity` et `toCity` ont été utilisés pour décrire le message de demande et la valeur de retour float a été utilisée pour décrire le message de réponse. Si la valeur de retour seule n'est pas suffisante pour décrire un message de réponse, les paramètres de sortie peuvent être utilisés. Par exemple, l'opération suivante a `fromCity` et `toCity` dans son message de demande, et un nombre et une monnaie dans son message de réponse :  
  
```csharp  
[OperationContract]  
float GetAirfare(string fromCity, string toCity, out string currency);  
```  
  
```vb  
<OperationContract()>  
    Function GetAirfare(fromCity As String, toCity As String) As Double  
```  
  
 En outre, vous pouvez utiliser des paramètres de référence pour intégrer un paramètre à la fois au message de demande et au message de réponse. Les paramètres doivent être de types pouvant être sérialisés (convertis en XML). Par défaut, WCF utilise <xref:System.Runtime.Serialization.DataContractSerializer> un composant appelé la classe pour effectuer cette conversion. La plupart des types primitifs (tels que `int`, `string`, `float` et `DateTime`) sont pris en charge. Les types définis par l'utilisateur doivent normalement avoir un contrat de données. Pour plus d’informations, voir [Utilisation des contrats de données](../../../../docs/framework/wcf/feature-details/using-data-contracts.md).  
  
```csharp
public interface IAirfareQuoteService  
{  
    [OperationContract]  
    float GetAirfare(Itinerary itinerary, DateTime date);  
  
    [DataContract]  
    public class Itinerary  
    {  
        [DataMember]  
        public string fromCity;  
        [DataMember]  
        public string toCity;  
   }  
}  
```  
  
```vb  
Public Interface IAirfareQuoteService  
    <OperationContract()>  
    GetAirfare(itinerary as Itinerary, date as DateTime) as Double  
  
    <DataContract()>  
    Class Itinerary  
  
        <DataMember()>  
        Public fromCity As String  
        <DataMember()>  
        Public toCity As String  
    End Class  
End Interface  
```  
  
 Parfois, `DataContractSerializer` ne convient pas pour sérialiser vos types. WCF prend en charge un <xref:System.Xml.Serialization.XmlSerializer>moteur de sérialisation alternatif, le , que vous pouvez également utiliser pour sérialiser les paramètres. Le <xref:System.Xml.Serialization.XmlSerializer> vous permet de davantage contrôler le XML résultant à l'aide d'attributs tels que `XmlAttributeAttribute`. Pour utiliser le <xref:System.Xml.Serialization.XmlSerializer> pour une opération particulière ou pour le service entier, appliquez l'attribut <xref:System.ServiceModel.XmlSerializerFormatAttribute> à une opération ou à un service. Par exemple :  
  
```csharp  
[ServiceContract]  
public interface IAirfareQuoteService  
{  
    [OperationContract]  
    [XmlSerializerFormat]  
    float GetAirfare(Itinerary itinerary, DateTime date);  
}  
public class Itinerary  
{  
    public string fromCity;  
    public string toCity;  
    [XmlAttribute]  
    public bool isFirstClass;  
}  
```  
  
```vb  
<ServiceContract()>  
Public Interface IAirfareQuoteService  
    <OperationContract()>  
    <XmlSerializerFormat>  
    GetAirfare(itinerary as Itinerary, date as DateTime) as Double  
  
End Interface  
  
Class Itinerary  
  
    Public fromCity As String  
    Public toCity As String  
    <XmlSerializerFormat()>  
    Public isFirstClass As Boolean  
End Class  
```  
  
 Pour plus d’informations, voir [Utiliser la classe XmlSerializer](../../../../docs/framework/wcf/feature-details/using-the-xmlserializer-class.md). Souvenez-vous que le basculement manuel vers le <xref:System.Xml.Serialization.XmlSerializer>, comme illustré ici, n'est pas recommandé, à moins que vous n'ayez des raisons spécifiques telles que celles détaillées dans cette rubrique.  
  
 Pour isoler des noms de paramètres .NET des noms de contrats, vous pouvez utiliser l'attribut <xref:System.ServiceModel.MessageParameterAttribute> et utiliser la propriété `Name` pour définir le nom de contrat. Par exemple, le contrat d'opération suivant est équivalent au premier exemple dans cette rubrique.  
  
```csharp  
[OperationContract]  
public float GetAirfare(  
    [MessageParameter(Name="fromCity")] string originCity,  
    [MessageParameter(Name="toCity")] string destinationCity);  
```  
  
```vb  
<OperationContract()>  
  Function GetAirfare(<MessageParameter(Name := "fromCity")> fromCity As String, <MessageParameter(Name := "toCity")> toCity As String) As Double  
```  
  
## <a name="describing-empty-messages"></a>Description de messages vides  
 Un message de demande vide peut être décrit en n'ayant ni entrée ni paramètre de référence. Par exemple, dans CMD :  
  
 `[OperationContract]`  
  
 `public int GetCurrentTemperature();`  
  
 Par exemple, dans Visual Basic:  
  
 `<OperationContract()>`  
  
 `Function GetCurrentTemperature() as Integer`  
  
 Un message de réponse vide peut être décrit en ayant un type de retour `void` et aucune sortie ni paramètre de référence. Par exemple, en :  
  
```csharp  
[OperationContract]  
public void SetTemperature(int temperature);  
```  
  
```vb  
<OperationContract()>  
Sub SetTemperature(temperature As Integer)  
```  
  
 Ceci est différent d'une opération unidirectionnelle telle que :  
  
```csharp  
[OperationContract(IsOneWay=true)]  
public void SetLightbulbStatus(bool isOn);  
```  
  
```vb  
<OperationContract(IsOneWay:=True)>  
Sub SetLightbulbStatus(isOne As Boolean)  
```  
  
 L'opération `SetTemperatureStatus` retourne un message vide. Elle peut retourner une erreur à la place, en cas de problème au niveau du traitement du message d'entrée. L'opération `SetLightbulbStatus` ne retourne rien. Il n'existe aucun moyen de communiquer une condition d'erreur à partir de cette opération.  
  
## <a name="describing-messages-by-using-message-contracts"></a>Description de messages à l'aide de contrats de message  
 Vous souhaiterez peut-être utiliser un type unique pour représenter le message entier. Bien qu'il soit possible d'utiliser un contrat de données dans ce but, la méthode recommandée consiste à utiliser un contrat de message ; cela évite des niveaux d'enveloppement inutiles dans le XML résultant. En outre, les contrats de message vous permettent de mieux contrôler les messages résultants. Par exemple, vous pouvez décider des informations qui doivent être dans le corps du message et de celles qui doivent être dans les en-têtes de message. L'exemple suivant illustre l'utilisation des contrats de message.  
  
```csharp  
[ServiceContract]  
public interface IAirfareQuoteService  
{  
    [OperationContract]  
    GetAirfareResponse GetAirfare(GetAirfareRequest request);  
}  
  
[MessageContract]  
public class GetAirfareRequest  
{  
    [MessageHeader] public DateTime date;  
    [MessageBodyMember] public Itinerary itinerary;  
}  
  
[MessageContract]  
public class GetAirfareResponse  
{  
    [MessageBodyMember] public float airfare;  
    [MessageBodyMember] public string currency;  
}  
  
[DataContract]  
public class Itinerary  
{  
    [DataMember] public string fromCity;  
    [DataMember] public string toCity;  
}  
```  
  
```vb  
<ServiceContract()>  
Public Interface IAirfareQuoteService  
    <OperationContract()>  
    Function GetAirfare(request As GetAirfareRequest) As GetAirfareResponse  
End Interface  
  
<MessageContract()>  
Public Class GetAirfareRequest  
    <MessageHeader()>
    Public Property date as DateTime  
    <MessageBodyMember()>  
    Public Property itinerary As Itinerary  
End Class  
  
<MessageContract()>  
Public Class GetAirfareResponse  
    <MessageBodyMember()>  
    Public Property airfare As Double  
    <MessageBodyMember()> Public Property currency As String  
End Class  
  
<DataContract()>  
Public Class Itinerary  
    <DataMember()> Public Property fromCity As String  
    <DataMember()> Public Property toCity As String  
End Class  
```  
  
 Pour plus d’informations, voir [Utiliser les contrats de message](../../../../docs/framework/wcf/feature-details/using-message-contracts.md).  
  
 Dans l'exemple précédent, la classe <xref:System.Runtime.Serialization.DataContractSerializer> est encore utilisée par défaut. La classe <xref:System.Xml.Serialization.XmlSerializer> peut également être utilisée avec des contrats de message. Pour cela, appliquez l'attribut <xref:System.ServiceModel.XmlSerializerFormatAttribute> à l'opération ou au contrat et utilisez des types compatibles avec la classe <xref:System.Xml.Serialization.XmlSerializer> dans les en-têtes de message et les membres de corps.  
  
## <a name="describing-messages-by-using-streams"></a>Description de messages à l'aide de flux  
 Une autre méthode pour décrire des messages dans des opérations consiste à utiliser la classe <xref:System.IO.Stream> ou une de ses classes dérivées dans un contrat d'opération ou en tant que membre de corps de contrat de message (il doit s'agir du seul membre dans ce cas). Pour les messages entrants, le type doit être `Stream` ; vous ne pouvez pas utiliser de classes dérivées.  
  
 Au lieu d’invoquer le sérialisateur, WCF récupère les données d’un flux et les met directement dans un message sortant, ou récupère les données d’un message entrant et les met directement dans un flux. L'exemple suivant illustre l'utilisation des flux.  
  
```csharp  
[OperationContract]  
public Stream DownloadFile(string fileName);  
```  
  
```vb  
<OperationContract()>  
Function DownloadFile(fileName As String) As String  
```  
  
 Vous ne pouvez pas combiner des données `Stream` et des données de non-flux dans un même corps de message. Utilisez un contrat de message pour mettre les données supplémentaires dans les en-têtes de message. L'exemple suivant illustre l'utilisation incorrecte de flux lors de la définition du contrat d'opération.  
  
```csharp  
//Incorrect:  
// [OperationContract]  
// public void UploadFile (string fileName, Stream fileData);  
```  
  
```vb  
'Incorrect:  
    '<OperationContract()>  
    Public Sub UploadFile(fileName As String, fileData As StreamingContext)  
```  
  
 L'exemple suivant illustre l'utilisation correcte de flux lors de la définition d'un contrat d'opération.  
  
```csharp  
[OperationContract]  
public void UploadFile (UploadFileMessage message);  
//code omitted  
[MessageContract]  
public class UploadFileMessage  
{  
    [MessageHeader] public string fileName;  
    [MessageBodyMember] public Stream fileData;  
}  
```  
  
```vb  
<OperationContract()>  
Public Sub UploadFile(fileName As String, fileData As StreamingContext)  
'Code Omitted  
<MessageContract()>  
Public Class UploadFileMessage  
   <MessageHeader()>  
    Public Property fileName As String  
    <MessageBodyMember()>  
    Public Property fileData As Stream  
End Class  
```  
  
 Pour plus d’informations, voir [Grandes données et Streaming](../../../../docs/framework/wcf/feature-details/large-data-and-streaming.md).  
  
## <a name="using-the-message-class"></a>Utilisation de la classe Message  
 Pour avoir un contrôle complet par programmation des messages envoyés ou reçus, vous pouvez utiliser la classe <xref:System.ServiceModel.Channels.Message> directement, comme illustré dans l'exemple de code suivant.  
  
```csharp  
[OperationContract]  
public void LogMessage(Message m);  
```  
  
```vb  
<OperationContract()>  
Sub LogMessage(m As Message)  
```  
  
 Il s’agit d’un scénario avancé, qui est décrit en détail dans [l’utilisation de la classe de message](../../../../docs/framework/wcf/feature-details/using-the-message-class.md).  
  
## <a name="describing-fault-messages"></a>Description des messages d'erreur  
 En plus des messages décrits par la valeur de retour et les paramètres de sortie ou de référence, toute opération qui n'est pas unidirectionnelle peut retourner au moins deux messages possibles : son message de réponse normal et un message d'erreur. Considérez le contrat d'opération suivant.  
  
```csharp  
[OperationContract]  
float GetAirfare(string fromCity, string toCity, DateTime date);  
```  
  
```vb  
<OperationContract()>  
Function GetAirfare(fromCity As String, toCity As String, date as DateTime)  
```  
  
 Cette opération peut retourner un message normal qui contient un nombre `float` ou un message d'erreur qui contient un code d'erreur et une description. Vous pouvez accomplir cela en levant une <xref:System.ServiceModel.FaultException> dans votre implémentation de service.  
  
 Vous pouvez spécifier des messages d'erreur possibles supplémentaires en utilisant l'attribut <xref:System.ServiceModel.FaultContractAttribute>. Les erreurs supplémentaires doivent être sérialisables à l'aide du <xref:System.Runtime.Serialization.DataContractSerializer>, comme illustré dans l'exemple de code suivant.  
  
```csharp  
[OperationContract]  
[FaultContract(typeof(ItineraryNotAvailableFault))]  
float GetAirfare(string fromCity, string toCity, DateTime date);  
  
//code omitted  
  
[DataContract]  
public class ItineraryNotAvailableFault  
{  
    [DataMember]  
    public bool IsAlternativeDateAvailable;  
  
    [DataMember]  
    public DateTime alternativeSuggestedDate;  
}  
```  
  
```vb  
<OperationContract()>  
<FaultContract(GetType(ItineraryNotAvailableFault))>  
Function GetAirfare(fromCity As String, toCity As String, date as DateTime) As Double  
  
'Code Omitted  
<DataContract()>  
Public Class  
  <DataMember()>  
  Public Property IsAlternativeDateAvailable As Boolean  
  <DataMember()>  
  Public Property alternativeSuggestedDate As DateTime  
End Class  
```  
  
 Ces erreurs supplémentaires peuvent être générées en levant une <xref:System.ServiceModel.FaultException%601> du type de contrat de données approprié. Pour plus d’informations, voir [Handling Exceptions and Faults](../../../../docs/framework/wcf/extending/handling-exceptions-and-faults.md).  
  
 Vous ne pouvez pas utiliser la classe <xref:System.Xml.Serialization.XmlSerializer> pour décrire des erreurs. Le <xref:System.ServiceModel.XmlSerializerFormatAttribute> n'a aucun effet sur les contrats d'erreur.  
  
## <a name="using-derived-types"></a>Utilisation de types dérivés  
 Vous pouvez utiliser un type de base dans une opération ou un contrat de message, puis utiliser un type dérivé lors de l'appel réel à l'opération. Dans ce cas, vous devez utiliser l'attribut <xref:System.ServiceModel.ServiceKnownTypeAttribute> ou un autre mécanisme pour autoriser l'utilisation de types dérivés. Considérez l'opération suivante.  
  
```csharp  
[OperationContract]  
public bool IsLibraryItemAvailable(LibraryItem item);  
```  
  
```vb
<OperationContract()>  
    Function IsLibraryItemAvailable(item As LibraryItem) As Boolean  
```  
  
 Supposez que deux types, `Book` et `Magazine`, dérivent de `LibraryItem`. Pour utiliser ces types dans l'opération `IsLibraryItemAvailable`, vous pouvez modifier l'opération comme suit :  
  
 `[OperationContract]`  
  
 `[ServiceKnownType(typeof(Book))]`  
  
 `[ServiceKnownType(typeof(Magazine))]`  
  
 `public bool IsLibraryItemAvailable(LibraryItem item);`  
  
 Vous pouvez également utiliser l'attribut <xref:System.Runtime.Serialization.KnownTypeAttribute> lorsque le <xref:System.Runtime.Serialization.DataContractSerializer> par défaut est en cours d'utilisation, comme illustré dans l'exemple de code suivant.  
  
```csharp  
[OperationContract]  
public bool IsLibraryItemAvailable(LibraryItem item);  
  
// code omitted
  
[DataContract]  
[KnownType(typeof(Book))]  
[KnownType(typeof(Magazine))]  
public class LibraryItem  
{  
    //code omitted  
}  
```  
  
```vb  
<OperationContract()>  
Function IsLibraryItemAvailable(item As LibraryItem) As Boolean  
  
'Code Omitted  
<DataContract()>  
<KnownType(GetType(Book))>  
<KnownType(GetType(Magazine))>  
Public Class LibraryItem  
  'Code Omitted  
End Class  
```  
  
 Vous pouvez utiliser l'attribut <xref:System.Xml.Serialization.XmlIncludeAttribute> lors de l'utilisation du <xref:System.Xml.Serialization.XmlSerializer>.  
  
 Vous pouvez appliquer l'attribut <xref:System.ServiceModel.ServiceKnownTypeAttribute> à une opération ou au service entier. Il accepte un type ou le nom de la méthode à appeler pour obtenir une liste des types connus, tout comme l'attribut <xref:System.Runtime.Serialization.KnownTypeAttribute>. Pour plus d’informations, voir [Data Contract Known Types](../../../../docs/framework/wcf/feature-details/data-contract-known-types.md).  
  
## <a name="specifying-the-use-and-style"></a>Spécification de l'utilisation et du style  
 Lors de la description de services à l'aide du langage WSDL (Web Services Description Language), les deux styles couramment utilisés sont Document et appel de procédure distante (RPC). Dans le style Document, le corps du message entier est décrit à l'aide du schéma et le WSDL décrit les différentes parties du corps de message en faisant référence à des éléments dans ce schéma. Dans le style RPC, le WSDL fait référence à un type de schéma pour chaque partie de message plutôt qu'à un élément. Dans certains cas, vous devez sélectionner manuellement l'un de ces styles. Pour cela, vous pouvez appliquer l'attribut <xref:System.ServiceModel.DataContractFormatAttribute> et définir la propriété `Style` (lorsque le <xref:System.Runtime.Serialization.DataContractSerializer> est en cours d'utilisation), ou définir `Style` sur l'attribut <xref:System.ServiceModel.XmlSerializerFormatAttribute> (lors de l'utilisation du <xref:System.Xml.Serialization.XmlSerializer>).  
  
 En outre, <xref:System.Xml.Serialization.XmlSerializer> prend en charge deux formes de XML sérialisé : `Literal` et `Encoded`. `Literal` est la forme la plus couramment acceptée et la seule prise en charge par le <xref:System.Runtime.Serialization.DataContractSerializer>. `Encoded` est une forme héritée décrite à la section 5 de la spécification SOAP qui n'est pas recommandée pour les nouveaux services. Pour basculer en mode `Encoded`, affectez à la propriété `Use` sur l'attribut <xref:System.ServiceModel.XmlSerializerFormatAttribute> la valeur `Encoded`.  
  
 Dans la plupart des cas, vous ne devez pas modifier les paramètres par défaut des propriétés `Style` et `Use`.  
  
## <a name="controlling-the-serialization-process"></a>Contrôle du processus de sérialisation  
 Vous pouvez effectuer plusieurs actions pour personnaliser la manière dont les données sont sérialisées.  
  
### <a name="changing-server-serialization-settings"></a>Modification des paramètres de sérialisation du serveur  
 Lorsque le <xref:System.Runtime.Serialization.DataContractSerializer> par défaut est en cours d'utilisation, vous pouvez contrôler certains aspects du processus de sérialisation sur le service en appliquant l'attribut <xref:System.ServiceModel.ServiceBehaviorAttribute> au service. Spécifiquement, vous pouvez utiliser la propriété `MaxItemsInObjectGraph` pour définir le quota qui limite le nombre maximal d'objets que le <xref:System.Runtime.Serialization.DataContractSerializer> désérialise. Vous pouvez utiliser la propriété `IgnoreExtensionDataObject` pour désactiver la fonctionnalité de suivi des versions aller-retour. Pour plus d’informations sur les quotas, consultez [Considérations sur la sécurité des données](../../../../docs/framework/wcf/feature-details/security-considerations-for-data.md). Pour plus d’informations sur les aller-retours, voir [Contrats de données compatibles avec l’avenir](../../../../docs/framework/wcf/feature-details/forward-compatible-data-contracts.md).  
  
```csharp  
[ServiceBehavior(MaxItemsInObjectGraph=100000)]  
public class MyDataService:IDataService  
{  
    public DataPoint[] GetData()  
    {  
       // Implementation omitted  
    }  
}  
```  
  
```vb  
<ServiceBehavior(MaxItemsInObjectGraph:=100000)>  
Public Class MyDataService Implements IDataService  
  
    Function GetData() As DataPoint()  
         ‘ Implementation omitted  
    End Function  
End Interface  
```  
  
### <a name="serialization-behaviors"></a>Comportements de sérialisation  
 Deux comportements sont disponibles dans <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior> WCF, le et le <xref:System.ServiceModel.Description.XmlSerializerOperationBehavior> qui sont automatiquement branchés en fonction de quel sérialisateur est utilisé pour une opération particulière. Ces comportements étant appliqués automatiquement, il n'est normalement pas nécessaire de s'en soucier.  
  
 Toutefois, le `DataContractSerializerOperationBehavior` a les propriétés `MaxItemsInObjectGraph`, `IgnoreExtensionDataObject` et `DataContractSurrogate` que vous pouvez utiliser pour personnaliser le processus de sérialisation. Les deux premières propriétés ont la même signification que dans la section précédente. Vous pouvez utiliser la propriété `DataContractSurrogate` pour activer des substituts de contrat de données, qui sont un mécanisme puissant pour personnaliser et étendre le processus de sérialisation. Pour plus d’informations, voir [Substituts contrat de données](../../../../docs/framework/wcf/extending/data-contract-surrogates.md).  
  
 Vous pouvez utiliser le `DataContractSerializerOperationBehavior` pour personnaliser à la fois la sérialisation de client et de serveur. L'exemple suivant indique comment augmenter le quota `MaxItemsInObjectGraph` sur le client.  
  
```csharp  
ChannelFactory<IDataService> factory = new ChannelFactory<IDataService>(binding, address);  
foreach (OperationDescription op in factory.Endpoint.Contract.Operations)  
{  
    DataContractSerializerOperationBehavior dataContractBehavior =  
                op.Behaviors.Find<DataContractSerializerOperationBehavior>()  
                as DataContractSerializerOperationBehavior;  
    if (dataContractBehavior != null)  
    {  
        dataContractBehavior.MaxItemsInObjectGraph = 100000;  
    }  
}  
IDataService client = factory.CreateChannel();  
```  
  
```vb  
Dim factory As ChannelFactory(Of IDataService) = New ChannelFactory(Of IDataService)(binding, address)  
For Each op As OperationDescription In factory.Endpoint.Contract.Operations  
        Dim dataContractBehavior As DataContractSerializerOperationBehavior = op.Behaviors.Find(Of DataContractSerializerOperationBehavior)()  
        If dataContractBehavior IsNot Nothing Then  
            dataContractBehavior.MaxItemsInObjectGraph = 100000  
        End If  
     Next  
    Dim client As IDataService = factory.CreateChannel  
```  
  
Ce qui suit est le code équivalent sur le service, dans le cas auto-hébergé:
  
```csharp  
ServiceHost serviceHost = new ServiceHost(typeof(IDataService))  
foreach (ServiceEndpoint ep in serviceHost.Description.Endpoints)  
{  
foreach (OperationDescription op in ep.Contract.Operations)  
{  
        DataContractSerializerOperationBehavior dataContractBehavior =  
           op.Behaviors.Find<DataContractSerializerOperationBehavior>()  
                as DataContractSerializerOperationBehavior;  
        if (dataContractBehavior != null)  
        {  
            dataContractBehavior.MaxItemsInObjectGraph = 100000;  
        }  
}  
}  
serviceHost.Open();  
```  
  
```vb  
Dim serviceHost As ServiceHost = New ServiceHost(GetType(IDataService))  
        For Each ep As ServiceEndpoint In serviceHost.Description.Endpoints  
            For Each op As OperationDescription In ep.Contract.Operations  
                Dim dataContractBehavior As DataContractSerializerOperationBehavior = op.Behaviors.Find(Of DataContractSerializerOperationBehavior)()  
  
                If dataContractBehavior IsNot Nothing Then  
                    dataContractBehavior.MaxItemsInObjectGraph = 100000  
                End If  
            Next  
        Next  
        serviceHost.Open()  
```  
  
 Dans le cas d'un hébergement sur le Web, vous devez créer une classe dérivée `ServiceHost` et utiliser une fabrication hôte de service pour le brancher.  
  
### <a name="controlling-serialization-settings-in-configuration"></a>Contrôle des paramètres de sérialisation dans la configuration  
 Le `MaxItemsInObjectGraph` et le `IgnoreExtensionDataObject` peuvent être contrôlés par le biais de la configuration en utilisant le comportement de service ou le point de terminaison `dataContractSerializer`, comme illustré dans l'exemple suivant.  
  
```xml  
<configuration>  
    <system.serviceModel>  
        <behaviors>  
            <endpointBehaviors>  
                <behavior name="LargeQuotaBehavior">  
                    <dataContractSerializer  
                      maxItemsInObjectGraph="100000" />  
                </behavior>  
            </endpointBehaviors>  
        </behaviors>  
        <client>  
            <endpoint address="http://example.com/myservice"  
                  behaviorConfiguration="LargeQuotaBehavior"  
                binding="basicHttpBinding" bindingConfiguration=""
                            contract="IDataService"  
                name="" />  
        </client>  
    </system.serviceModel>  
</configuration>  
```  
  
### <a name="shared-type-serialization-object-graph-preservation-and-custom-serializers"></a>Sérialisation de type partagé, conservation de graphique d'objet et sérialiseurs personnalisés  
 Le <xref:System.Runtime.Serialization.DataContractSerializer> sérialise à l'aide des noms de contrats de données, et non des noms de types .NET. Ceci est cohérent avec les doctrines d'architecture orientée services et procure un niveau élevé de flexibilité : les types .NET peuvent changer sans affecter le contrat de câble. Dans de rares cas, vous souhaiterez peut-être sérialiser des noms de types .NET réels, introduisant ainsi un couplage étroit entre le client et le serveur, semblable à la technologie de .NET Framework Remoting. Ce n’est pas une pratique recommandée, sauf dans de rares cas qui se produisent habituellement lors de la migration vers WCF à partir de .NET Framework remoting. Dans ce cas, vous devez utiliser la classe <xref:System.Runtime.Serialization.NetDataContractSerializer> au lieu de la classe <xref:System.Runtime.Serialization.DataContractSerializer>.  
  
 Le <xref:System.Runtime.Serialization.DataContractSerializer> sérialise normalement les graphiques d'objets en tant qu'arborescences d'objets. Autrement dit, s'il est fait référence plusieurs fois au même objet, il est sérialisé plusieurs fois. Par exemple, considérez une instance `PurchaseOrder` qui a deux champs de type Adresse nommés `billTo` et `shipTo`. Si les deux champs ont pour valeur la même instance Adresse, il existe deux instances Adresse identiques après la sérialisation et la désérialisation. Cela est dû au fait qu'il n'existe aucune méthode interopérable standard pour représenter des graphiques d'objets en XML (hormis la norme encodée SOAP héritée disponible sur le <xref:System.Xml.Serialization.XmlSerializer>, comme décrit dans la section précédente sur `Style` et `Use`). La sérialisation de graphiques d’objets en tant qu’arborescences a certains inconvénients ; par exemple, les graphiques avec des références circulaires ne peuvent pas être sérialisés. Parfois, il est nécessaire de basculer vers la sérialisation de graphiques d'objets vraie, bien que cela ne soit pas interopérable. Vous devez pour cela utiliser le <xref:System.Runtime.Serialization.DataContractSerializer> construit avec le paramètre `preserveObjectReferences` défini à `true`.  
  
 Parfois, les sérialiseurs intégrés ne sont pas suffisants pour votre scénario. Dans la plupart des cas, vous pouvez encore utiliser l'abstraction <xref:System.Runtime.Serialization.XmlObjectSerializer> à partir de laquelle le <xref:System.Runtime.Serialization.DataContractSerializer> et le <xref:System.Runtime.Serialization.NetDataContractSerializer> dérivent.  
  
 Les trois cas précédents (conservation de type .NET, conservation des graphiques d'objets et sérialisation `XmlObjectSerializer` complètement personnalisée) requièrent tous le branchement d'un sérialiseur personnalisé. Pour ce faire, procédez comme suit :  
  
1. Écrivez votre propre comportement dérivant du <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior>.  
  
2. Substituez les deux méthodes `CreateSerializer` pour retourner votre propre sérialiseur (le <xref:System.Runtime.Serialization.NetDataContractSerializer>, le <xref:System.Runtime.Serialization.DataContractSerializer> avec `preserveObjectReferences` défini à `true`, ou votre propre <xref:System.Runtime.Serialization.XmlObjectSerializer> personnalisé).  
  
3. Avant d'ouvrir l'hôte de service ou de créer un canal client, supprimez le comportement <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior> existant et branchez la classe dérivée personnalisée que vous avez créée aux étapes précédentes.  
  
 Pour plus d’informations sur les concepts avancés de sérialisation, voir [La sérialisation et la désétérisation.](../../../../docs/framework/wcf/feature-details/serialization-and-deserialization.md)  
  
## <a name="see-also"></a>Voir aussi

- [Utilisation de la classe XmlSerializer](../../../../docs/framework/wcf/feature-details/using-the-xmlserializer-class.md)
- [Comment : activer la diffusion en continu](../../../../docs/framework/wcf/feature-details/how-to-enable-streaming.md)
- [Guide pratique pour créer un contrat de données de base destiné à une classe ou une structure](../../../../docs/framework/wcf/feature-details/how-to-create-a-basic-data-contract-for-a-class-or-structure.md)
