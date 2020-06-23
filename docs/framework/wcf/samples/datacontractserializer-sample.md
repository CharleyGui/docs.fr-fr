---
title: DataContractSerializer, exemple
description: Cet exemple illustre DataContractSerializer dans WCF, qui effectue des services généraux de sérialisation et de désérialisation pour les classes de contrat de données.
ms.date: 03/30/2017
helpviewer_keywords:
- XML Formatter
ms.assetid: e0a2fe89-3534-48c8-aa3c-819862224571
ms.openlocfilehash: c2f62c8926f09e2d4cdea1941909e7d8f59c43a0
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/23/2020
ms.locfileid: "85244398"
---
# <a name="datacontractserializer-sample"></a><span data-ttu-id="ab8c2-103">DataContractSerializer, exemple</span><span class="sxs-lookup"><span data-stu-id="ab8c2-103">DataContractSerializer Sample</span></span>
<span data-ttu-id="ab8c2-104">Cet exemple illustre l’utilisation du sérialiseur <xref:System.Runtime.Serialization.DataContractSerializer>, lequel est chargé d’effectuer des processus de sérialisation et de désérialisation standard pour les classes de contrat de données.</span><span class="sxs-lookup"><span data-stu-id="ab8c2-104">The DataContractSerializer sample demonstrates the <xref:System.Runtime.Serialization.DataContractSerializer>, which performs general serialization and deserialization services for the data contract classes.</span></span> <span data-ttu-id="ab8c2-105">L’exemple crée un `Record` objet, le sérialise dans un flux de mémoire et désérialise le flux de mémoire vers un autre `Record` objet pour illustrer l’utilisation de <xref:System.Runtime.Serialization.DataContractSerializer> .</span><span class="sxs-lookup"><span data-stu-id="ab8c2-105">The sample creates a `Record` object, serializes it to a memory stream and deserializes the memory stream back to another `Record` object to demonstrate the use of the <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span> <span data-ttu-id="ab8c2-106">L'exemple sérialise ensuite l'objet `Record` à l'aide d'un enregistreur binaire afin d'illustrer la manière dont l'utilisation d'un tel enregistreur affecte la sérialisation.</span><span class="sxs-lookup"><span data-stu-id="ab8c2-106">The sample then serializes the `Record` object using a binary writer to demonstrate how the writer affects serialization.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="ab8c2-107">La procédure d'installation ainsi que les instructions de génération relatives à cet exemple figurent à la fin de cette rubrique.</span><span class="sxs-lookup"><span data-stu-id="ab8c2-107">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="ab8c2-108">L'exemple de code suivant contient le contrat de données de l'objet `Record`.</span><span class="sxs-lookup"><span data-stu-id="ab8c2-108">The data contract for `Record` is shown in the following sample code.</span></span>  
  
```csharp  
[DataContract(Namespace="http://Microsoft.ServiceModel.Samples")]  
internal class Record  
{  
    private double n1;  
    private double n2;  
    private string operation;  
    private double result;  
  
    internal Record(double n1, double n2, string operation, double result)  
    {  
        this.n1 = n1;  
        this.n2 = n2;  
        this.operation = operation;  
        this.result = result;  
    }  
  
    [DataMember]  
    internal double OperandNumberOne  
    {  
        get { return n1; }  
        set { n1 = value; }  
    }  
  
    [DataMember]  
    internal double OperandNumberTwo  
    {  
        get { return n2; }  
        set { n2 = value; }  
    }  
  
    [DataMember]  
    internal string Operation  
    {  
        get { return operation; }  
        set { operation = value; }  
    }  
  
    [DataMember]  
    internal double Result  
    {  
        get { return result; }  
        set { result = value; }  
    }  
  
    public override string ToString()  
    {  
        return $"Record: {n1} {operation} {n2} = {result}";
    }  
}  
```  
  
 <span data-ttu-id="ab8c2-109">L'exemple de code crée un objet `Record` nommé `record1`, puis affiche celui-ci.</span><span class="sxs-lookup"><span data-stu-id="ab8c2-109">The sample code creates a `Record` object named `record1` then displays the object.</span></span>  
  
```csharp
Record record1 = new Record(1, 2, "+", 3);  
Console.WriteLine("Original record: {0}", record1.ToString());  
```  
  
 <span data-ttu-id="ab8c2-110">L'exemple utilise ensuite le <xref:System.Runtime.Serialization.DataContractSerializer> pour sérialiser `record1` dans un flux de mémoire.</span><span class="sxs-lookup"><span data-stu-id="ab8c2-110">The sample then uses the <xref:System.Runtime.Serialization.DataContractSerializer> to serialize `record1` into a memory stream.</span></span>  
  
```csharp  
MemoryStream stream1 = new MemoryStream();  
  
//Serialize the Record object to a memory stream using DataContractSerializer.  
DataContractSerializer serializer = new DataContractSerializer(typeof(Record));  
serializer.WriteObject(stream1, record1);  
```  
  
 <span data-ttu-id="ab8c2-111">L'exemple utilise ensuite le <xref:System.Runtime.Serialization.DataContractSerializer> pour désérialiser le flux de mémoire dans un nouvel objet `Record`, puis affiche ce nouvel objet.</span><span class="sxs-lookup"><span data-stu-id="ab8c2-111">Next, the sample uses the <xref:System.Runtime.Serialization.DataContractSerializer> to deserialize the memory stream back into a new `Record` object and displays it.</span></span>  
  
```csharp  
stream1.Position = 0;  
  
//Deserialize the Record object back into a new record object.  
Record record2 = (Record)serializer.ReadObject(stream1);  
  
Console.WriteLine("Deserialized record: {0}", record2.ToString());  
```  
  
 <span data-ttu-id="ab8c2-112">Par défaut, le sérialiseur `DataContractSerializer` encode les objets sous la forme d'un flux de données à l'aide d'une représentation XML textuelle.</span><span class="sxs-lookup"><span data-stu-id="ab8c2-112">By default, the `DataContractSerializer` encodes objects into a stream using a textual representation of XML.</span></span> <span data-ttu-id="ab8c2-113">Toutefois, vous pouvez influencer les modalités d'encodage de la représentation XML en passant un enregistreur différent.</span><span class="sxs-lookup"><span data-stu-id="ab8c2-113">However, you can influence the encoding of the XML by passing in a different writer.</span></span> <span data-ttu-id="ab8c2-114">L'exemple crée un enregistreur binaire en appelant <xref:System.Xml.XmlDictionaryWriter.CreateBinaryWriter%2A>.</span><span class="sxs-lookup"><span data-stu-id="ab8c2-114">The sample creates a binary writer by calling <xref:System.Xml.XmlDictionaryWriter.CreateBinaryWriter%2A>.</span></span> <span data-ttu-id="ab8c2-115">Il passe ensuite l'enregistreur et l'objet Record au sérialiseur lorsqu'il appelle <xref:System.Runtime.Serialization.DataContractSerializer.WriteObjectContent%2A>.</span><span class="sxs-lookup"><span data-stu-id="ab8c2-115">It then passes the writer and the record object to the serializer when it calls <xref:System.Runtime.Serialization.DataContractSerializer.WriteObjectContent%2A>.</span></span> <span data-ttu-id="ab8c2-116">Enfin, l'exemple vide l'enregistreur et génère un rapport sur la longueur des flux de données.</span><span class="sxs-lookup"><span data-stu-id="ab8c2-116">Finally, the sample flushes the writer and reports on the length of the streams.</span></span>  
  
```csharp  
MemoryStream stream2 = new MemoryStream();  
  
XmlDictionaryWriter binaryDictionaryWriter = XmlDictionaryWriter.CreateBinaryWriter(stream2);  
serializer.WriteObject(binaryDictionaryWriter, record1);  
binaryDictionaryWriter.Flush();  
  
//report the length of the streams  
Console.WriteLine("Text Stream is {0} bytes long", stream1.Length);  
Console.WriteLine("Binary Stream is {0} bytes long", stream2.Length);  
```  
  
 <span data-ttu-id="ab8c2-117">Lorsque vous exécutez l'exemple, l'enregistrement d'origine et l'enregistrement désérialisé s'affichent, suivis des différences de longueur entre l'encodage texte et l'encodage binaire.</span><span class="sxs-lookup"><span data-stu-id="ab8c2-117">When you run the sample, the original record and the deserialized record are displayed, followed by the comparison between the length of the text encoding and the binary encoding.</span></span> <span data-ttu-id="ab8c2-118">Appuyez sur Entrée dans la fenêtre du client pour l'arrêter.</span><span class="sxs-lookup"><span data-stu-id="ab8c2-118">Press ENTER in the client window to shut down the client.</span></span>  
  
```console  
Original record: Record: 1 + 2 = 3  
Deserialized record: Record: 1 + 2 = 3  
Text Stream is 233 bytes long  
Binary Stream is 156 bytes long  
  
Press <ENTER> to terminate client.  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="ab8c2-119">Pour configurer, générer et exécuter l'exemple</span><span class="sxs-lookup"><span data-stu-id="ab8c2-119">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="ab8c2-120">Assurez-vous d’avoir effectué la [procédure d’installation unique pour les exemples de Windows Communication Foundation](one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="ab8c2-120">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="ab8c2-121">Pour générer l’édition C# ou Visual Basic .NET de la solution, conformez-vous aux instructions figurant dans [Building the Windows Communication Foundation Samples](building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="ab8c2-121">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="ab8c2-122">Pour exécuter l'exemple, démarrez le client à partir d'une invite de commandes en tapant client\bin\client.exe.</span><span class="sxs-lookup"><span data-stu-id="ab8c2-122">To run the sample, start the client from the command prompt by typing client\bin\client.exe.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="ab8c2-123">Les exemples peuvent déjà être installés sur votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="ab8c2-123">The samples may already be installed on your machine.</span></span> <span data-ttu-id="ab8c2-124">Recherchez le répertoire (par défaut) suivant avant de continuer.</span><span class="sxs-lookup"><span data-stu-id="ab8c2-124">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="ab8c2-125">Si ce répertoire n’existe pas, accédez à [Windows Communication Foundation (WCF) et Windows Workflow Foundation (WF) exemples pour .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) pour télécharger tous les exemples Windows Communication Foundation (WCF) et [!INCLUDE[wf1](../../../../includes/wf1-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="ab8c2-125">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="ab8c2-126">Cet exemple se trouve dans le répertoire suivant.</span><span class="sxs-lookup"><span data-stu-id="ab8c2-126">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Data\DataContractSerializer`  
