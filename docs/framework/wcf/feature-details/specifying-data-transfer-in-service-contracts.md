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
# <a name="specifying-data-transfer-in-service-contracts"></a><span data-ttu-id="1c321-102">Spécification du transfert de données dans des contrats de service</span><span class="sxs-lookup"><span data-stu-id="1c321-102">Specifying Data Transfer in Service Contracts</span></span>
<span data-ttu-id="1c321-103">La Windows Communication Foundation (WCF) peut être considérée comme une infrastructure de messagerie.</span><span class="sxs-lookup"><span data-stu-id="1c321-103">The Windows Communication Foundation (WCF) can be thought of as a messaging infrastructure.</span></span> <span data-ttu-id="1c321-104">Les opérations de service peuvent recevoir des messages, les traiter et leur envoyer des messages.</span><span class="sxs-lookup"><span data-stu-id="1c321-104">Service operations can receive messages, process them, and send them messages.</span></span> <span data-ttu-id="1c321-105">Les messages sont décrits à l'aide de contrats d'opérations.</span><span class="sxs-lookup"><span data-stu-id="1c321-105">Messages are described using operation contracts.</span></span> <span data-ttu-id="1c321-106">Par exemple, considérons le contrat suivant.</span><span class="sxs-lookup"><span data-stu-id="1c321-106">For example, consider the following contract.</span></span>  
  
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
  
 <span data-ttu-id="1c321-107">Ici, l'opération `GetAirfare` accepte un message avec des informations à propos de `fromCity` et `toCity`, puis retourne un message qui contient un nombre.</span><span class="sxs-lookup"><span data-stu-id="1c321-107">Here, the `GetAirfare` operation accepts a message with information about `fromCity` and `toCity`, and then returns a message that contains a number.</span></span>  
  
 <span data-ttu-id="1c321-108">Cette rubrique explique les différentes manières par lesquelles un contrat d'opération peut décrire des messages.</span><span class="sxs-lookup"><span data-stu-id="1c321-108">This topic explains the various ways in which an operation contract can describe messages.</span></span>  
  
## <a name="describing-messages-by-using-parameters"></a><span data-ttu-id="1c321-109">Description de messages à l'aide de paramètres</span><span class="sxs-lookup"><span data-stu-id="1c321-109">Describing Messages by Using Parameters</span></span>  
 <span data-ttu-id="1c321-110">La méthode la plus simple pour décrire un message consiste à utiliser une liste de paramètres et la valeur de retour.</span><span class="sxs-lookup"><span data-stu-id="1c321-110">The simplest way to describe a message is to use a parameter list and the return value.</span></span> <span data-ttu-id="1c321-111">Dans l'exemple précédent, les paramètres de chaîne `fromCity` et `toCity` ont été utilisés pour décrire le message de demande et la valeur de retour float a été utilisée pour décrire le message de réponse.</span><span class="sxs-lookup"><span data-stu-id="1c321-111">In the preceding example, the `fromCity` and `toCity` string parameters were used to describe the request message, and the float return value was used to describe the reply message.</span></span> <span data-ttu-id="1c321-112">Si la valeur de retour seule n'est pas suffisante pour décrire un message de réponse, les paramètres de sortie peuvent être utilisés.</span><span class="sxs-lookup"><span data-stu-id="1c321-112">If the return value alone is not enough to describe a reply message, out parameters may be used.</span></span> <span data-ttu-id="1c321-113">Par exemple, l'opération suivante a `fromCity` et `toCity` dans son message de demande, et un nombre et une monnaie dans son message de réponse :</span><span class="sxs-lookup"><span data-stu-id="1c321-113">For example, the following operation has `fromCity` and `toCity` in its request message, and a number together with a currency in its reply message:</span></span>  
  
```csharp  
[OperationContract]  
float GetAirfare(string fromCity, string toCity, out string currency);  
```  
  
```vb  
<OperationContract()>  
    Function GetAirfare(fromCity As String, toCity As String) As Double  
```  
  
 <span data-ttu-id="1c321-114">En outre, vous pouvez utiliser des paramètres de référence pour intégrer un paramètre à la fois au message de demande et au message de réponse.</span><span class="sxs-lookup"><span data-stu-id="1c321-114">Additionally, you may use reference parameters to make a parameter part of both the request and the reply message.</span></span> <span data-ttu-id="1c321-115">Les paramètres doivent être de types pouvant être sérialisés (convertis en XML).</span><span class="sxs-lookup"><span data-stu-id="1c321-115">The parameters must be of types that can be serialized (converted to XML).</span></span> <span data-ttu-id="1c321-116">Par défaut, WCF utilise <xref:System.Runtime.Serialization.DataContractSerializer> un composant appelé la classe pour effectuer cette conversion.</span><span class="sxs-lookup"><span data-stu-id="1c321-116">By default, WCF uses a component called the <xref:System.Runtime.Serialization.DataContractSerializer> class to perform this conversion.</span></span> <span data-ttu-id="1c321-117">La plupart des types primitifs (tels que `int`, `string`, `float` et `DateTime`) sont pris en charge.</span><span class="sxs-lookup"><span data-stu-id="1c321-117">Most primitive types (such as `int`, `string`, `float`, and `DateTime`.) are supported.</span></span> <span data-ttu-id="1c321-118">Les types définis par l'utilisateur doivent normalement avoir un contrat de données.</span><span class="sxs-lookup"><span data-stu-id="1c321-118">User-defined types must normally have a data contract.</span></span> <span data-ttu-id="1c321-119">Pour plus d’informations, voir [Utilisation des contrats de données](../../../../docs/framework/wcf/feature-details/using-data-contracts.md).</span><span class="sxs-lookup"><span data-stu-id="1c321-119">For more information, see [Using Data Contracts](../../../../docs/framework/wcf/feature-details/using-data-contracts.md).</span></span>  
  
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
  
 <span data-ttu-id="1c321-120">Parfois, `DataContractSerializer` ne convient pas pour sérialiser vos types.</span><span class="sxs-lookup"><span data-stu-id="1c321-120">Occasionally, the `DataContractSerializer` is not adequate to serialize your types.</span></span> <span data-ttu-id="1c321-121">WCF prend en charge un <xref:System.Xml.Serialization.XmlSerializer>moteur de sérialisation alternatif, le , que vous pouvez également utiliser pour sérialiser les paramètres.</span><span class="sxs-lookup"><span data-stu-id="1c321-121">WCF supports an alternative serialization engine, the <xref:System.Xml.Serialization.XmlSerializer>, which you can also use to serialize parameters.</span></span> <span data-ttu-id="1c321-122">Le <xref:System.Xml.Serialization.XmlSerializer> vous permet de davantage contrôler le XML résultant à l'aide d'attributs tels que `XmlAttributeAttribute`.</span><span class="sxs-lookup"><span data-stu-id="1c321-122">The <xref:System.Xml.Serialization.XmlSerializer> allows you to use more control over the resultant XML using attributes such as the `XmlAttributeAttribute`.</span></span> <span data-ttu-id="1c321-123">Pour utiliser le <xref:System.Xml.Serialization.XmlSerializer> pour une opération particulière ou pour le service entier, appliquez l'attribut <xref:System.ServiceModel.XmlSerializerFormatAttribute> à une opération ou à un service.</span><span class="sxs-lookup"><span data-stu-id="1c321-123">To switch to using the <xref:System.Xml.Serialization.XmlSerializer> for a particular operation or for the entire service, apply the <xref:System.ServiceModel.XmlSerializerFormatAttribute> attribute to an operation or a service.</span></span> <span data-ttu-id="1c321-124">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="1c321-124">For example:</span></span>  
  
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
  
 <span data-ttu-id="1c321-125">Pour plus d’informations, voir [Utiliser la classe XmlSerializer](../../../../docs/framework/wcf/feature-details/using-the-xmlserializer-class.md).</span><span class="sxs-lookup"><span data-stu-id="1c321-125">For more information, see [Using the XmlSerializer Class](../../../../docs/framework/wcf/feature-details/using-the-xmlserializer-class.md).</span></span> <span data-ttu-id="1c321-126">Souvenez-vous que le basculement manuel vers le <xref:System.Xml.Serialization.XmlSerializer>, comme illustré ici, n'est pas recommandé, à moins que vous n'ayez des raisons spécifiques telles que celles détaillées dans cette rubrique.</span><span class="sxs-lookup"><span data-stu-id="1c321-126">Remember that manually switching to the <xref:System.Xml.Serialization.XmlSerializer> as shown here is not recommended unless you have specific reasons to do so as detailed in that topic.</span></span>  
  
 <span data-ttu-id="1c321-127">Pour isoler des noms de paramètres .NET des noms de contrats, vous pouvez utiliser l'attribut <xref:System.ServiceModel.MessageParameterAttribute> et utiliser la propriété `Name` pour définir le nom de contrat.</span><span class="sxs-lookup"><span data-stu-id="1c321-127">To isolate .NET parameter names from contract names, you can use the <xref:System.ServiceModel.MessageParameterAttribute> attribute, and use the `Name` property to set the contract name.</span></span> <span data-ttu-id="1c321-128">Par exemple, le contrat d'opération suivant est équivalent au premier exemple dans cette rubrique.</span><span class="sxs-lookup"><span data-stu-id="1c321-128">For example, the following operation contract is equivalent to the first example in this topic.</span></span>  
  
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
  
## <a name="describing-empty-messages"></a><span data-ttu-id="1c321-129">Description de messages vides</span><span class="sxs-lookup"><span data-stu-id="1c321-129">Describing Empty Messages</span></span>  
 <span data-ttu-id="1c321-130">Un message de demande vide peut être décrit en n'ayant ni entrée ni paramètre de référence.</span><span class="sxs-lookup"><span data-stu-id="1c321-130">An empty request message can be described by having no input or reference parameters.</span></span> <span data-ttu-id="1c321-131">Par exemple, dans CMD :</span><span class="sxs-lookup"><span data-stu-id="1c321-131">For example, in C#:</span></span>  
  
 `[OperationContract]`  
  
 `public int GetCurrentTemperature();`  
  
 <span data-ttu-id="1c321-132">Par exemple, dans Visual Basic:</span><span class="sxs-lookup"><span data-stu-id="1c321-132">For example, in Visual Basic:</span></span>  
  
 `<OperationContract()>`  
  
 `Function GetCurrentTemperature() as Integer`  
  
 <span data-ttu-id="1c321-133">Un message de réponse vide peut être décrit en ayant un type de retour `void` et aucune sortie ni paramètre de référence.</span><span class="sxs-lookup"><span data-stu-id="1c321-133">An empty reply message can be described by having a `void` return type and no output or reference parameters.</span></span> <span data-ttu-id="1c321-134">Par exemple, en :</span><span class="sxs-lookup"><span data-stu-id="1c321-134">For example in:</span></span>  
  
```csharp  
[OperationContract]  
public void SetTemperature(int temperature);  
```  
  
```vb  
<OperationContract()>  
Sub SetTemperature(temperature As Integer)  
```  
  
 <span data-ttu-id="1c321-135">Ceci est différent d'une opération unidirectionnelle telle que :</span><span class="sxs-lookup"><span data-stu-id="1c321-135">This is different from a one-way operation, such as:</span></span>  
  
```csharp  
[OperationContract(IsOneWay=true)]  
public void SetLightbulbStatus(bool isOn);  
```  
  
```vb  
<OperationContract(IsOneWay:=True)>  
Sub SetLightbulbStatus(isOne As Boolean)  
```  
  
 <span data-ttu-id="1c321-136">L'opération `SetTemperatureStatus` retourne un message vide.</span><span class="sxs-lookup"><span data-stu-id="1c321-136">The `SetTemperatureStatus` operation returns an empty message.</span></span> <span data-ttu-id="1c321-137">Elle peut retourner une erreur à la place, en cas de problème au niveau du traitement du message d'entrée.</span><span class="sxs-lookup"><span data-stu-id="1c321-137">It may return a fault instead if there is a problem processing the input message.</span></span> <span data-ttu-id="1c321-138">L'opération `SetLightbulbStatus` ne retourne rien.</span><span class="sxs-lookup"><span data-stu-id="1c321-138">The `SetLightbulbStatus` operation returns nothing.</span></span> <span data-ttu-id="1c321-139">Il n'existe aucun moyen de communiquer une condition d'erreur à partir de cette opération.</span><span class="sxs-lookup"><span data-stu-id="1c321-139">There is no way to communicate a fault condition from this operation.</span></span>  
  
## <a name="describing-messages-by-using-message-contracts"></a><span data-ttu-id="1c321-140">Description de messages à l'aide de contrats de message</span><span class="sxs-lookup"><span data-stu-id="1c321-140">Describing Messages by Using Message Contracts</span></span>  
 <span data-ttu-id="1c321-141">Vous souhaiterez peut-être utiliser un type unique pour représenter le message entier.</span><span class="sxs-lookup"><span data-stu-id="1c321-141">You may want to use a single type to represent the entire message.</span></span> <span data-ttu-id="1c321-142">Bien qu'il soit possible d'utiliser un contrat de données dans ce but, la méthode recommandée consiste à utiliser un contrat de message ; cela évite des niveaux d'enveloppement inutiles dans le XML résultant.</span><span class="sxs-lookup"><span data-stu-id="1c321-142">While it is possible to use a data contract for this purpose, the recommended way to do this is to use a message contract—this avoids unnecessary levels of wrapping in the resultant XML.</span></span> <span data-ttu-id="1c321-143">En outre, les contrats de message vous permettent de mieux contrôler les messages résultants.</span><span class="sxs-lookup"><span data-stu-id="1c321-143">Additionally, message contracts allow you to exercise more control over resultant messages.</span></span> <span data-ttu-id="1c321-144">Par exemple, vous pouvez décider des informations qui doivent être dans le corps du message et de celles qui doivent être dans les en-têtes de message.</span><span class="sxs-lookup"><span data-stu-id="1c321-144">For instance, you can decide which pieces of information should be in the message body and which should be in the message headers.</span></span> <span data-ttu-id="1c321-145">L'exemple suivant illustre l'utilisation des contrats de message.</span><span class="sxs-lookup"><span data-stu-id="1c321-145">The following example shows the use of message contracts.</span></span>  
  
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
  
 <span data-ttu-id="1c321-146">Pour plus d’informations, voir [Utiliser les contrats de message](../../../../docs/framework/wcf/feature-details/using-message-contracts.md).</span><span class="sxs-lookup"><span data-stu-id="1c321-146">For more information, see [Using Message Contracts](../../../../docs/framework/wcf/feature-details/using-message-contracts.md).</span></span>  
  
 <span data-ttu-id="1c321-147">Dans l'exemple précédent, la classe <xref:System.Runtime.Serialization.DataContractSerializer> est encore utilisée par défaut.</span><span class="sxs-lookup"><span data-stu-id="1c321-147">In the previous example, the <xref:System.Runtime.Serialization.DataContractSerializer> class is still used by default.</span></span> <span data-ttu-id="1c321-148">La classe <xref:System.Xml.Serialization.XmlSerializer> peut également être utilisée avec des contrats de message.</span><span class="sxs-lookup"><span data-stu-id="1c321-148">The <xref:System.Xml.Serialization.XmlSerializer> class can also be used with message contracts.</span></span> <span data-ttu-id="1c321-149">Pour cela, appliquez l'attribut <xref:System.ServiceModel.XmlSerializerFormatAttribute> à l'opération ou au contrat et utilisez des types compatibles avec la classe <xref:System.Xml.Serialization.XmlSerializer> dans les en-têtes de message et les membres de corps.</span><span class="sxs-lookup"><span data-stu-id="1c321-149">To do this, apply the <xref:System.ServiceModel.XmlSerializerFormatAttribute> attribute to either the operation or the contract, and use types compatible with the <xref:System.Xml.Serialization.XmlSerializer> class in the message headers and body members.</span></span>  
  
## <a name="describing-messages-by-using-streams"></a><span data-ttu-id="1c321-150">Description de messages à l'aide de flux</span><span class="sxs-lookup"><span data-stu-id="1c321-150">Describing Messages by Using Streams</span></span>  
 <span data-ttu-id="1c321-151">Une autre méthode pour décrire des messages dans des opérations consiste à utiliser la classe <xref:System.IO.Stream> ou une de ses classes dérivées dans un contrat d'opération ou en tant que membre de corps de contrat de message (il doit s'agir du seul membre dans ce cas).</span><span class="sxs-lookup"><span data-stu-id="1c321-151">Another way to describe messages in operations is to use the <xref:System.IO.Stream> class or one of its derived classes in an operation contract or as a message contract body member (it must be the only member in this case).</span></span> <span data-ttu-id="1c321-152">Pour les messages entrants, le type doit être `Stream` ; vous ne pouvez pas utiliser de classes dérivées.</span><span class="sxs-lookup"><span data-stu-id="1c321-152">For incoming messages, the type must be `Stream`—you cannot use derived classes.</span></span>  
  
 <span data-ttu-id="1c321-153">Au lieu d’invoquer le sérialisateur, WCF récupère les données d’un flux et les met directement dans un message sortant, ou récupère les données d’un message entrant et les met directement dans un flux.</span><span class="sxs-lookup"><span data-stu-id="1c321-153">Instead of invoking the serializer, WCF retrieves data from a stream and puts it directly into an outgoing message, or retrieves data from an incoming message and puts it directly into a stream.</span></span> <span data-ttu-id="1c321-154">L'exemple suivant illustre l'utilisation des flux.</span><span class="sxs-lookup"><span data-stu-id="1c321-154">The following sample shows the use of streams.</span></span>  
  
```csharp  
[OperationContract]  
public Stream DownloadFile(string fileName);  
```  
  
```vb  
<OperationContract()>  
Function DownloadFile(fileName As String) As String  
```  
  
 <span data-ttu-id="1c321-155">Vous ne pouvez pas combiner des données `Stream` et des données de non-flux dans un même corps de message.</span><span class="sxs-lookup"><span data-stu-id="1c321-155">You cannot combine `Stream` and non-stream data in a single message body.</span></span> <span data-ttu-id="1c321-156">Utilisez un contrat de message pour mettre les données supplémentaires dans les en-têtes de message.</span><span class="sxs-lookup"><span data-stu-id="1c321-156">Use a message contract to put the extra data in message headers.</span></span> <span data-ttu-id="1c321-157">L'exemple suivant illustre l'utilisation incorrecte de flux lors de la définition du contrat d'opération.</span><span class="sxs-lookup"><span data-stu-id="1c321-157">The following example shows the incorrect usage of streams when defining the operation contract.</span></span>  
  
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
  
 <span data-ttu-id="1c321-158">L'exemple suivant illustre l'utilisation correcte de flux lors de la définition d'un contrat d'opération.</span><span class="sxs-lookup"><span data-stu-id="1c321-158">The following sample shows the correct usage of streams when defining an operation contract.</span></span>  
  
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
  
 <span data-ttu-id="1c321-159">Pour plus d’informations, voir [Grandes données et Streaming](../../../../docs/framework/wcf/feature-details/large-data-and-streaming.md).</span><span class="sxs-lookup"><span data-stu-id="1c321-159">For more information, see [Large Data and Streaming](../../../../docs/framework/wcf/feature-details/large-data-and-streaming.md).</span></span>  
  
## <a name="using-the-message-class"></a><span data-ttu-id="1c321-160">Utilisation de la classe Message</span><span class="sxs-lookup"><span data-stu-id="1c321-160">Using the Message Class</span></span>  
 <span data-ttu-id="1c321-161">Pour avoir un contrôle complet par programmation des messages envoyés ou reçus, vous pouvez utiliser la classe <xref:System.ServiceModel.Channels.Message> directement, comme illustré dans l'exemple de code suivant.</span><span class="sxs-lookup"><span data-stu-id="1c321-161">To have complete programmatic control over messages sent or received, you can use the <xref:System.ServiceModel.Channels.Message> class directly, as shown in the following example code.</span></span>  
  
```csharp  
[OperationContract]  
public void LogMessage(Message m);  
```  
  
```vb  
<OperationContract()>  
Sub LogMessage(m As Message)  
```  
  
 <span data-ttu-id="1c321-162">Il s’agit d’un scénario avancé, qui est décrit en détail dans [l’utilisation de la classe de message](../../../../docs/framework/wcf/feature-details/using-the-message-class.md).</span><span class="sxs-lookup"><span data-stu-id="1c321-162">This is an advanced scenario, which is described in detail in [Using the Message Class](../../../../docs/framework/wcf/feature-details/using-the-message-class.md).</span></span>  
  
## <a name="describing-fault-messages"></a><span data-ttu-id="1c321-163">Description des messages d'erreur</span><span class="sxs-lookup"><span data-stu-id="1c321-163">Describing Fault Messages</span></span>  
 <span data-ttu-id="1c321-164">En plus des messages décrits par la valeur de retour et les paramètres de sortie ou de référence, toute opération qui n'est pas unidirectionnelle peut retourner au moins deux messages possibles : son message de réponse normal et un message d'erreur.</span><span class="sxs-lookup"><span data-stu-id="1c321-164">In addition to the messages that are described by the return value and output or reference parameters, any operation that is not one-way can return at least two possible messages: its normal response message and a fault message.</span></span> <span data-ttu-id="1c321-165">Considérez le contrat d'opération suivant.</span><span class="sxs-lookup"><span data-stu-id="1c321-165">Consider the following operation contract.</span></span>  
  
```csharp  
[OperationContract]  
float GetAirfare(string fromCity, string toCity, DateTime date);  
```  
  
```vb  
<OperationContract()>  
Function GetAirfare(fromCity As String, toCity As String, date as DateTime)  
```  
  
 <span data-ttu-id="1c321-166">Cette opération peut retourner un message normal qui contient un nombre `float` ou un message d'erreur qui contient un code d'erreur et une description.</span><span class="sxs-lookup"><span data-stu-id="1c321-166">This operation may either return a normal message that contains a `float` number, or a fault message that contains a fault code and a description.</span></span> <span data-ttu-id="1c321-167">Vous pouvez accomplir cela en levant une <xref:System.ServiceModel.FaultException> dans votre implémentation de service.</span><span class="sxs-lookup"><span data-stu-id="1c321-167">You can accomplish this by throwing a <xref:System.ServiceModel.FaultException> in your service implementation.</span></span>  
  
 <span data-ttu-id="1c321-168">Vous pouvez spécifier des messages d'erreur possibles supplémentaires en utilisant l'attribut <xref:System.ServiceModel.FaultContractAttribute>.</span><span class="sxs-lookup"><span data-stu-id="1c321-168">You can specify additional possible fault messages by using the <xref:System.ServiceModel.FaultContractAttribute> attribute.</span></span> <span data-ttu-id="1c321-169">Les erreurs supplémentaires doivent être sérialisables à l'aide du <xref:System.Runtime.Serialization.DataContractSerializer>, comme illustré dans l'exemple de code suivant.</span><span class="sxs-lookup"><span data-stu-id="1c321-169">The additional faults must be serializable using the <xref:System.Runtime.Serialization.DataContractSerializer>, as shown in the following example code.</span></span>  
  
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
  
 <span data-ttu-id="1c321-170">Ces erreurs supplémentaires peuvent être générées en levant une <xref:System.ServiceModel.FaultException%601> du type de contrat de données approprié.</span><span class="sxs-lookup"><span data-stu-id="1c321-170">These additional faults can be generated by throwing a <xref:System.ServiceModel.FaultException%601> of the appropriate data contract type.</span></span> <span data-ttu-id="1c321-171">Pour plus d’informations, voir [Handling Exceptions and Faults](../../../../docs/framework/wcf/extending/handling-exceptions-and-faults.md).</span><span class="sxs-lookup"><span data-stu-id="1c321-171">For more information, see [Handling Exceptions and Faults](../../../../docs/framework/wcf/extending/handling-exceptions-and-faults.md).</span></span>  
  
 <span data-ttu-id="1c321-172">Vous ne pouvez pas utiliser la classe <xref:System.Xml.Serialization.XmlSerializer> pour décrire des erreurs.</span><span class="sxs-lookup"><span data-stu-id="1c321-172">You cannot use the <xref:System.Xml.Serialization.XmlSerializer> class to describe faults.</span></span> <span data-ttu-id="1c321-173">Le <xref:System.ServiceModel.XmlSerializerFormatAttribute> n'a aucun effet sur les contrats d'erreur.</span><span class="sxs-lookup"><span data-stu-id="1c321-173">The <xref:System.ServiceModel.XmlSerializerFormatAttribute> has no effect on fault contracts.</span></span>  
  
## <a name="using-derived-types"></a><span data-ttu-id="1c321-174">Utilisation de types dérivés</span><span class="sxs-lookup"><span data-stu-id="1c321-174">Using Derived Types</span></span>  
 <span data-ttu-id="1c321-175">Vous pouvez utiliser un type de base dans une opération ou un contrat de message, puis utiliser un type dérivé lors de l'appel réel à l'opération.</span><span class="sxs-lookup"><span data-stu-id="1c321-175">You may want to use a base type in an operation or a message contract, and then use a derived type when actually invoking the operation.</span></span> <span data-ttu-id="1c321-176">Dans ce cas, vous devez utiliser l'attribut <xref:System.ServiceModel.ServiceKnownTypeAttribute> ou un autre mécanisme pour autoriser l'utilisation de types dérivés.</span><span class="sxs-lookup"><span data-stu-id="1c321-176">In this case, you must use either the <xref:System.ServiceModel.ServiceKnownTypeAttribute> attribute or some alternative mechanism to allow the use of derived types.</span></span> <span data-ttu-id="1c321-177">Considérez l'opération suivante.</span><span class="sxs-lookup"><span data-stu-id="1c321-177">Consider the following operation.</span></span>  
  
```csharp  
[OperationContract]  
public bool IsLibraryItemAvailable(LibraryItem item);  
```  
  
```vb
<OperationContract()>  
    Function IsLibraryItemAvailable(item As LibraryItem) As Boolean  
```  
  
 <span data-ttu-id="1c321-178">Supposez que deux types, `Book` et `Magazine`, dérivent de `LibraryItem`.</span><span class="sxs-lookup"><span data-stu-id="1c321-178">Assume that two types, `Book` and `Magazine`, derive from `LibraryItem`.</span></span> <span data-ttu-id="1c321-179">Pour utiliser ces types dans l'opération `IsLibraryItemAvailable`, vous pouvez modifier l'opération comme suit :</span><span class="sxs-lookup"><span data-stu-id="1c321-179">To use these types in the `IsLibraryItemAvailable` operation, you can change the operation as follows:</span></span>  
  
 `[OperationContract]`  
  
 `[ServiceKnownType(typeof(Book))]`  
  
 `[ServiceKnownType(typeof(Magazine))]`  
  
 `public bool IsLibraryItemAvailable(LibraryItem item);`  
  
 <span data-ttu-id="1c321-180">Vous pouvez également utiliser l'attribut <xref:System.Runtime.Serialization.KnownTypeAttribute> lorsque le <xref:System.Runtime.Serialization.DataContractSerializer> par défaut est en cours d'utilisation, comme illustré dans l'exemple de code suivant.</span><span class="sxs-lookup"><span data-stu-id="1c321-180">Alternatively, you can use the <xref:System.Runtime.Serialization.KnownTypeAttribute> attribute when the default <xref:System.Runtime.Serialization.DataContractSerializer> is in use, as shown in the following example code.</span></span>  
  
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
  
 <span data-ttu-id="1c321-181">Vous pouvez utiliser l'attribut <xref:System.Xml.Serialization.XmlIncludeAttribute> lors de l'utilisation du <xref:System.Xml.Serialization.XmlSerializer>.</span><span class="sxs-lookup"><span data-stu-id="1c321-181">You can use the <xref:System.Xml.Serialization.XmlIncludeAttribute> attribute when using the <xref:System.Xml.Serialization.XmlSerializer>.</span></span>  
  
 <span data-ttu-id="1c321-182">Vous pouvez appliquer l'attribut <xref:System.ServiceModel.ServiceKnownTypeAttribute> à une opération ou au service entier.</span><span class="sxs-lookup"><span data-stu-id="1c321-182">You can apply the <xref:System.ServiceModel.ServiceKnownTypeAttribute> attribute to an operation or to the entire service.</span></span> <span data-ttu-id="1c321-183">Il accepte un type ou le nom de la méthode à appeler pour obtenir une liste des types connus, tout comme l'attribut <xref:System.Runtime.Serialization.KnownTypeAttribute>.</span><span class="sxs-lookup"><span data-stu-id="1c321-183">It accepts either a type or the name of the method to call to get a list of known types, just like the <xref:System.Runtime.Serialization.KnownTypeAttribute> attribute.</span></span> <span data-ttu-id="1c321-184">Pour plus d’informations, voir [Data Contract Known Types](../../../../docs/framework/wcf/feature-details/data-contract-known-types.md).</span><span class="sxs-lookup"><span data-stu-id="1c321-184">For more information, see [Data Contract Known Types](../../../../docs/framework/wcf/feature-details/data-contract-known-types.md).</span></span>  
  
## <a name="specifying-the-use-and-style"></a><span data-ttu-id="1c321-185">Spécification de l'utilisation et du style</span><span class="sxs-lookup"><span data-stu-id="1c321-185">Specifying the Use and Style</span></span>  
 <span data-ttu-id="1c321-186">Lors de la description de services à l'aide du langage WSDL (Web Services Description Language), les deux styles couramment utilisés sont Document et appel de procédure distante (RPC).</span><span class="sxs-lookup"><span data-stu-id="1c321-186">When describing services using Web Services Description Language (WSDL), the two commonly used styles are Document and remote procedure call (RPC).</span></span> <span data-ttu-id="1c321-187">Dans le style Document, le corps du message entier est décrit à l'aide du schéma et le WSDL décrit les différentes parties du corps de message en faisant référence à des éléments dans ce schéma.</span><span class="sxs-lookup"><span data-stu-id="1c321-187">In the Document style, the entire message body is described using the schema, and the WSDL describes the various message body parts by referring to elements within that schema.</span></span> <span data-ttu-id="1c321-188">Dans le style RPC, le WSDL fait référence à un type de schéma pour chaque partie de message plutôt qu'à un élément.</span><span class="sxs-lookup"><span data-stu-id="1c321-188">In the RPC style, the WSDL refers to a schema type for each message part rather than an element.</span></span> <span data-ttu-id="1c321-189">Dans certains cas, vous devez sélectionner manuellement l'un de ces styles.</span><span class="sxs-lookup"><span data-stu-id="1c321-189">In some cases, you have to manually select one of these styles.</span></span> <span data-ttu-id="1c321-190">Pour cela, vous pouvez appliquer l'attribut <xref:System.ServiceModel.DataContractFormatAttribute> et définir la propriété `Style` (lorsque le <xref:System.Runtime.Serialization.DataContractSerializer> est en cours d'utilisation), ou définir `Style` sur l'attribut <xref:System.ServiceModel.XmlSerializerFormatAttribute> (lors de l'utilisation du <xref:System.Xml.Serialization.XmlSerializer>).</span><span class="sxs-lookup"><span data-stu-id="1c321-190">You can do this by applying the <xref:System.ServiceModel.DataContractFormatAttribute> attribute and setting the `Style` property (when the <xref:System.Runtime.Serialization.DataContractSerializer> is in use), or by setting `Style` on the <xref:System.ServiceModel.XmlSerializerFormatAttribute> attribute (when using the <xref:System.Xml.Serialization.XmlSerializer>).</span></span>  
  
 <span data-ttu-id="1c321-191">En outre, <xref:System.Xml.Serialization.XmlSerializer> prend en charge deux formes de XML sérialisé : `Literal` et `Encoded`.</span><span class="sxs-lookup"><span data-stu-id="1c321-191">Additionally, the <xref:System.Xml.Serialization.XmlSerializer> supports two forms of serialized XML: `Literal` and `Encoded`.</span></span> <span data-ttu-id="1c321-192">`Literal` est la forme la plus couramment acceptée et la seule prise en charge par le <xref:System.Runtime.Serialization.DataContractSerializer>.</span><span class="sxs-lookup"><span data-stu-id="1c321-192">`Literal` is the most commonly accepted form, and is the only form the <xref:System.Runtime.Serialization.DataContractSerializer> supports.</span></span> <span data-ttu-id="1c321-193">`Encoded` est une forme héritée décrite à la section 5 de la spécification SOAP qui n'est pas recommandée pour les nouveaux services.</span><span class="sxs-lookup"><span data-stu-id="1c321-193">`Encoded` is a legacy form described in section 5 of the SOAP specification, and is not recommended for new services.</span></span> <span data-ttu-id="1c321-194">Pour basculer en mode `Encoded`, affectez à la propriété `Use` sur l'attribut <xref:System.ServiceModel.XmlSerializerFormatAttribute> la valeur `Encoded`.</span><span class="sxs-lookup"><span data-stu-id="1c321-194">To switch to `Encoded` mode, set the `Use` property on the <xref:System.ServiceModel.XmlSerializerFormatAttribute> attribute to `Encoded`.</span></span>  
  
 <span data-ttu-id="1c321-195">Dans la plupart des cas, vous ne devez pas modifier les paramètres par défaut des propriétés `Style` et `Use`.</span><span class="sxs-lookup"><span data-stu-id="1c321-195">In most cases, you should not change the default settings for the `Style` and `Use` properties.</span></span>  
  
## <a name="controlling-the-serialization-process"></a><span data-ttu-id="1c321-196">Contrôle du processus de sérialisation</span><span class="sxs-lookup"><span data-stu-id="1c321-196">Controlling the Serialization Process</span></span>  
 <span data-ttu-id="1c321-197">Vous pouvez effectuer plusieurs actions pour personnaliser la manière dont les données sont sérialisées.</span><span class="sxs-lookup"><span data-stu-id="1c321-197">You can do a number of things to customize the way data is serialized.</span></span>  
  
### <a name="changing-server-serialization-settings"></a><span data-ttu-id="1c321-198">Modification des paramètres de sérialisation du serveur</span><span class="sxs-lookup"><span data-stu-id="1c321-198">Changing Server Serialization Settings</span></span>  
 <span data-ttu-id="1c321-199">Lorsque le <xref:System.Runtime.Serialization.DataContractSerializer> par défaut est en cours d'utilisation, vous pouvez contrôler certains aspects du processus de sérialisation sur le service en appliquant l'attribut <xref:System.ServiceModel.ServiceBehaviorAttribute> au service.</span><span class="sxs-lookup"><span data-stu-id="1c321-199">When the default <xref:System.Runtime.Serialization.DataContractSerializer> is in use, you can control some aspects of the serialization process on the service by applying the <xref:System.ServiceModel.ServiceBehaviorAttribute> attribute to the service.</span></span> <span data-ttu-id="1c321-200">Spécifiquement, vous pouvez utiliser la propriété `MaxItemsInObjectGraph` pour définir le quota qui limite le nombre maximal d'objets que le <xref:System.Runtime.Serialization.DataContractSerializer> désérialise.</span><span class="sxs-lookup"><span data-stu-id="1c321-200">Specifically, you may use the `MaxItemsInObjectGraph` property to set the quota that limits the maximum number of objects the <xref:System.Runtime.Serialization.DataContractSerializer> deserializes.</span></span> <span data-ttu-id="1c321-201">Vous pouvez utiliser la propriété `IgnoreExtensionDataObject` pour désactiver la fonctionnalité de suivi des versions aller-retour.</span><span class="sxs-lookup"><span data-stu-id="1c321-201">You can use the `IgnoreExtensionDataObject` property to turn off the round-tripping versioning feature.</span></span> <span data-ttu-id="1c321-202">Pour plus d’informations sur les quotas, consultez [Considérations sur la sécurité des données](../../../../docs/framework/wcf/feature-details/security-considerations-for-data.md).</span><span class="sxs-lookup"><span data-stu-id="1c321-202">For more information about quotas, see [Security Considerations for Data](../../../../docs/framework/wcf/feature-details/security-considerations-for-data.md).</span></span> <span data-ttu-id="1c321-203">Pour plus d’informations sur les aller-retours, voir [Contrats de données compatibles avec l’avenir](../../../../docs/framework/wcf/feature-details/forward-compatible-data-contracts.md).</span><span class="sxs-lookup"><span data-stu-id="1c321-203">For more information about round-tripping, see [Forward-Compatible Data Contracts](../../../../docs/framework/wcf/feature-details/forward-compatible-data-contracts.md).</span></span>  
  
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
  
### <a name="serialization-behaviors"></a><span data-ttu-id="1c321-204">Comportements de sérialisation</span><span class="sxs-lookup"><span data-stu-id="1c321-204">Serialization Behaviors</span></span>  
 <span data-ttu-id="1c321-205">Deux comportements sont disponibles dans <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior> WCF, le et le <xref:System.ServiceModel.Description.XmlSerializerOperationBehavior> qui sont automatiquement branchés en fonction de quel sérialisateur est utilisé pour une opération particulière.</span><span class="sxs-lookup"><span data-stu-id="1c321-205">Two behaviors are available in WCF, the <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior> and the <xref:System.ServiceModel.Description.XmlSerializerOperationBehavior> that are automatically plugged in depending on which serializer is in use for a particular operation.</span></span> <span data-ttu-id="1c321-206">Ces comportements étant appliqués automatiquement, il n'est normalement pas nécessaire de s'en soucier.</span><span class="sxs-lookup"><span data-stu-id="1c321-206">Because these behaviors are applied automatically, you normally do not have to be aware of them.</span></span>  
  
 <span data-ttu-id="1c321-207">Toutefois, le `DataContractSerializerOperationBehavior` a les propriétés `MaxItemsInObjectGraph`, `IgnoreExtensionDataObject` et `DataContractSurrogate` que vous pouvez utiliser pour personnaliser le processus de sérialisation.</span><span class="sxs-lookup"><span data-stu-id="1c321-207">However, the `DataContractSerializerOperationBehavior` has the `MaxItemsInObjectGraph`, `IgnoreExtensionDataObject`, and `DataContractSurrogate` properties that you may use to customize the serialization process.</span></span> <span data-ttu-id="1c321-208">Les deux premières propriétés ont la même signification que dans la section précédente.</span><span class="sxs-lookup"><span data-stu-id="1c321-208">The first two properties have the same meaning as discussed in the previous section.</span></span> <span data-ttu-id="1c321-209">Vous pouvez utiliser la propriété `DataContractSurrogate` pour activer des substituts de contrat de données, qui sont un mécanisme puissant pour personnaliser et étendre le processus de sérialisation.</span><span class="sxs-lookup"><span data-stu-id="1c321-209">You can use the `DataContractSurrogate` property to enable data contract surrogates, which are a powerful mechanism for customizing and extending the serialization process.</span></span> <span data-ttu-id="1c321-210">Pour plus d’informations, voir [Substituts contrat de données](../../../../docs/framework/wcf/extending/data-contract-surrogates.md).</span><span class="sxs-lookup"><span data-stu-id="1c321-210">For more information, see [Data Contract Surrogates](../../../../docs/framework/wcf/extending/data-contract-surrogates.md).</span></span>  
  
 <span data-ttu-id="1c321-211">Vous pouvez utiliser le `DataContractSerializerOperationBehavior` pour personnaliser à la fois la sérialisation de client et de serveur.</span><span class="sxs-lookup"><span data-stu-id="1c321-211">You can use the `DataContractSerializerOperationBehavior` to customize both client and server serialization.</span></span> <span data-ttu-id="1c321-212">L'exemple suivant indique comment augmenter le quota `MaxItemsInObjectGraph` sur le client.</span><span class="sxs-lookup"><span data-stu-id="1c321-212">The following example shows how to increase the `MaxItemsInObjectGraph` quota on the client.</span></span>  
  
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
  
<span data-ttu-id="1c321-213">Ce qui suit est le code équivalent sur le service, dans le cas auto-hébergé:</span><span class="sxs-lookup"><span data-stu-id="1c321-213">The following is the equivalent code on the service, in the self-hosted case:</span></span>
  
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
  
 <span data-ttu-id="1c321-214">Dans le cas d'un hébergement sur le Web, vous devez créer une classe dérivée `ServiceHost` et utiliser une fabrication hôte de service pour le brancher.</span><span class="sxs-lookup"><span data-stu-id="1c321-214">In the Web-hosted case, you must create a new `ServiceHost` derived class and use a service host factory to plug it in.</span></span>  
  
### <a name="controlling-serialization-settings-in-configuration"></a><span data-ttu-id="1c321-215">Contrôle des paramètres de sérialisation dans la configuration</span><span class="sxs-lookup"><span data-stu-id="1c321-215">Controlling Serialization Settings in Configuration</span></span>  
 <span data-ttu-id="1c321-216">Le `MaxItemsInObjectGraph` et le `IgnoreExtensionDataObject` peuvent être contrôlés par le biais de la configuration en utilisant le comportement de service ou le point de terminaison `dataContractSerializer`, comme illustré dans l'exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="1c321-216">The `MaxItemsInObjectGraph` and `IgnoreExtensionDataObject` can be controlled through configuration by using the `dataContractSerializer` endpoint or service behavior, as shown in the following example.</span></span>  
  
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
  
### <a name="shared-type-serialization-object-graph-preservation-and-custom-serializers"></a><span data-ttu-id="1c321-217">Sérialisation de type partagé, conservation de graphique d'objet et sérialiseurs personnalisés</span><span class="sxs-lookup"><span data-stu-id="1c321-217">Shared Type Serialization, Object Graph Preservation, and Custom Serializers</span></span>  
 <span data-ttu-id="1c321-218">Le <xref:System.Runtime.Serialization.DataContractSerializer> sérialise à l'aide des noms de contrats de données, et non des noms de types .NET.</span><span class="sxs-lookup"><span data-stu-id="1c321-218">The <xref:System.Runtime.Serialization.DataContractSerializer> serializes using data contract names and not .NET type names.</span></span> <span data-ttu-id="1c321-219">Ceci est cohérent avec les doctrines d'architecture orientée services et procure un niveau élevé de flexibilité : les types .NET peuvent changer sans affecter le contrat de câble.</span><span class="sxs-lookup"><span data-stu-id="1c321-219">This is consistent with service-oriented architecture tenets and allows for a great degree of flexibility—the .NET types can change without affecting the wire contract.</span></span> <span data-ttu-id="1c321-220">Dans de rares cas, vous souhaiterez peut-être sérialiser des noms de types .NET réels, introduisant ainsi un couplage étroit entre le client et le serveur, semblable à la technologie de .NET Framework Remoting.</span><span class="sxs-lookup"><span data-stu-id="1c321-220">In rare cases, you may want to serialize actual .NET type names, thereby introducing a tight coupling between the client and the server, similar to the .NET Framework remoting technology.</span></span> <span data-ttu-id="1c321-221">Ce n’est pas une pratique recommandée, sauf dans de rares cas qui se produisent habituellement lors de la migration vers WCF à partir de .NET Framework remoting.</span><span class="sxs-lookup"><span data-stu-id="1c321-221">This is not a recommended practice, except in rare cases that usually occur when migrating to WCF from .NET Framework remoting.</span></span> <span data-ttu-id="1c321-222">Dans ce cas, vous devez utiliser la classe <xref:System.Runtime.Serialization.NetDataContractSerializer> au lieu de la classe <xref:System.Runtime.Serialization.DataContractSerializer>.</span><span class="sxs-lookup"><span data-stu-id="1c321-222">In this case, you must use the <xref:System.Runtime.Serialization.NetDataContractSerializer> class instead of the <xref:System.Runtime.Serialization.DataContractSerializer> class.</span></span>  
  
 <span data-ttu-id="1c321-223">Le <xref:System.Runtime.Serialization.DataContractSerializer> sérialise normalement les graphiques d'objets en tant qu'arborescences d'objets.</span><span class="sxs-lookup"><span data-stu-id="1c321-223">The <xref:System.Runtime.Serialization.DataContractSerializer> normally serializes object graphs as object trees.</span></span> <span data-ttu-id="1c321-224">Autrement dit, s'il est fait référence plusieurs fois au même objet, il est sérialisé plusieurs fois.</span><span class="sxs-lookup"><span data-stu-id="1c321-224">That is, if the same object is referred to more than once, it is serialized more than once.</span></span> <span data-ttu-id="1c321-225">Par exemple, considérez une instance `PurchaseOrder` qui a deux champs de type Adresse nommés `billTo` et `shipTo`.</span><span class="sxs-lookup"><span data-stu-id="1c321-225">For example, consider a `PurchaseOrder` instance that has two fields of type Address called `billTo` and `shipTo`.</span></span> <span data-ttu-id="1c321-226">Si les deux champs ont pour valeur la même instance Adresse, il existe deux instances Adresse identiques après la sérialisation et la désérialisation.</span><span class="sxs-lookup"><span data-stu-id="1c321-226">If both fields are set to the same Address instance, there are two identical Address instances after serialization and deserialization.</span></span> <span data-ttu-id="1c321-227">Cela est dû au fait qu'il n'existe aucune méthode interopérable standard pour représenter des graphiques d'objets en XML (hormis la norme encodée SOAP héritée disponible sur le <xref:System.Xml.Serialization.XmlSerializer>, comme décrit dans la section précédente sur `Style` et `Use`).</span><span class="sxs-lookup"><span data-stu-id="1c321-227">This is done because there is no standard interoperable way to represent object graphs in XML (except for the legacy SOAP encoded standard available on the <xref:System.Xml.Serialization.XmlSerializer>, as described in the previous section on `Style` and `Use`).</span></span> <span data-ttu-id="1c321-228">La sérialisation de graphiques d’objets en tant qu’arborescences a certains inconvénients ; par exemple, les graphiques avec des références circulaires ne peuvent pas être sérialisés.</span><span class="sxs-lookup"><span data-stu-id="1c321-228">Serializing object graphs as trees has certain disadvantages, for example, graphs with circular references cannot be serialized.</span></span> <span data-ttu-id="1c321-229">Parfois, il est nécessaire de basculer vers la sérialisation de graphiques d'objets vraie, bien que cela ne soit pas interopérable.</span><span class="sxs-lookup"><span data-stu-id="1c321-229">Occasionally, it is necessary to switch to true object graph serialization, even though it is not interoperable.</span></span> <span data-ttu-id="1c321-230">Vous devez pour cela utiliser le <xref:System.Runtime.Serialization.DataContractSerializer> construit avec le paramètre `preserveObjectReferences` défini à `true`.</span><span class="sxs-lookup"><span data-stu-id="1c321-230">This can be done by using the <xref:System.Runtime.Serialization.DataContractSerializer> constructed with the `preserveObjectReferences` parameter set to `true`.</span></span>  
  
 <span data-ttu-id="1c321-231">Parfois, les sérialiseurs intégrés ne sont pas suffisants pour votre scénario.</span><span class="sxs-lookup"><span data-stu-id="1c321-231">Occasionally, the built-in serializers are not enough for your scenario.</span></span> <span data-ttu-id="1c321-232">Dans la plupart des cas, vous pouvez encore utiliser l'abstraction <xref:System.Runtime.Serialization.XmlObjectSerializer> à partir de laquelle le <xref:System.Runtime.Serialization.DataContractSerializer> et le <xref:System.Runtime.Serialization.NetDataContractSerializer> dérivent.</span><span class="sxs-lookup"><span data-stu-id="1c321-232">In most cases, you can still use the <xref:System.Runtime.Serialization.XmlObjectSerializer> abstraction from which both the <xref:System.Runtime.Serialization.DataContractSerializer> and the <xref:System.Runtime.Serialization.NetDataContractSerializer> derive.</span></span>  
  
 <span data-ttu-id="1c321-233">Les trois cas précédents (conservation de type .NET, conservation des graphiques d'objets et sérialisation `XmlObjectSerializer` complètement personnalisée) requièrent tous le branchement d'un sérialiseur personnalisé.</span><span class="sxs-lookup"><span data-stu-id="1c321-233">The previous three cases (.NET type preservation, object graph preservation, and completely custom `XmlObjectSerializer`-based serialization) all require a custom serializer be plugged in.</span></span> <span data-ttu-id="1c321-234">Pour ce faire, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="1c321-234">To do this, perform the following steps:</span></span>  
  
1. <span data-ttu-id="1c321-235">Écrivez votre propre comportement dérivant du <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior>.</span><span class="sxs-lookup"><span data-stu-id="1c321-235">Write your own behavior deriving from the <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior>.</span></span>  
  
2. <span data-ttu-id="1c321-236">Substituez les deux méthodes `CreateSerializer` pour retourner votre propre sérialiseur (le <xref:System.Runtime.Serialization.NetDataContractSerializer>, le <xref:System.Runtime.Serialization.DataContractSerializer> avec `preserveObjectReferences` défini à `true`, ou votre propre <xref:System.Runtime.Serialization.XmlObjectSerializer> personnalisé).</span><span class="sxs-lookup"><span data-stu-id="1c321-236">Override the two `CreateSerializer` methods to return your own serializer (either the <xref:System.Runtime.Serialization.NetDataContractSerializer>, the <xref:System.Runtime.Serialization.DataContractSerializer> with `preserveObjectReferences` set to `true`, or your own custom <xref:System.Runtime.Serialization.XmlObjectSerializer>).</span></span>  
  
3. <span data-ttu-id="1c321-237">Avant d'ouvrir l'hôte de service ou de créer un canal client, supprimez le comportement <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior> existant et branchez la classe dérivée personnalisée que vous avez créée aux étapes précédentes.</span><span class="sxs-lookup"><span data-stu-id="1c321-237">Before opening the service host or creating a client channel, remove the existing <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior> behavior and plug in the custom derived class that you created in the previous steps.</span></span>  
  
 <span data-ttu-id="1c321-238">Pour plus d’informations sur les concepts avancés de sérialisation, voir [La sérialisation et la désétérisation.](../../../../docs/framework/wcf/feature-details/serialization-and-deserialization.md)</span><span class="sxs-lookup"><span data-stu-id="1c321-238">For more information about advanced serialization concepts, see [Serialization and Deserialization](../../../../docs/framework/wcf/feature-details/serialization-and-deserialization.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1c321-239">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="1c321-239">See also</span></span>

- [<span data-ttu-id="1c321-240">Utilisation de la classe XmlSerializer</span><span class="sxs-lookup"><span data-stu-id="1c321-240">Using the XmlSerializer Class</span></span>](../../../../docs/framework/wcf/feature-details/using-the-xmlserializer-class.md)
- [<span data-ttu-id="1c321-241">Comment : activer la diffusion en continu</span><span class="sxs-lookup"><span data-stu-id="1c321-241">How to: Enable Streaming</span></span>](../../../../docs/framework/wcf/feature-details/how-to-enable-streaming.md)
- [<span data-ttu-id="1c321-242">Guide pratique pour créer un contrat de données de base destiné à une classe ou une structure</span><span class="sxs-lookup"><span data-stu-id="1c321-242">How to: Create a Basic Data Contract for a Class or Structure</span></span>](../../../../docs/framework/wcf/feature-details/how-to-create-a-basic-data-contract-for-a-class-or-structure.md)
