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
# <a name="datacontractserializer-sample"></a>DataContractSerializer, exemple
Cet exemple illustre l’utilisation du sérialiseur <xref:System.Runtime.Serialization.DataContractSerializer>, lequel est chargé d’effectuer des processus de sérialisation et de désérialisation standard pour les classes de contrat de données. L’exemple crée un `Record` objet, le sérialise dans un flux de mémoire et désérialise le flux de mémoire vers un autre `Record` objet pour illustrer l’utilisation de <xref:System.Runtime.Serialization.DataContractSerializer> . L'exemple sérialise ensuite l'objet `Record` à l'aide d'un enregistreur binaire afin d'illustrer la manière dont l'utilisation d'un tel enregistreur affecte la sérialisation.  
  
> [!NOTE]
> La procédure d'installation ainsi que les instructions de génération relatives à cet exemple figurent à la fin de cette rubrique.  
  
 L'exemple de code suivant contient le contrat de données de l'objet `Record`.  
  
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
  
 L'exemple de code crée un objet `Record` nommé `record1`, puis affiche celui-ci.  
  
```csharp
Record record1 = new Record(1, 2, "+", 3);  
Console.WriteLine("Original record: {0}", record1.ToString());  
```  
  
 L'exemple utilise ensuite le <xref:System.Runtime.Serialization.DataContractSerializer> pour sérialiser `record1` dans un flux de mémoire.  
  
```csharp  
MemoryStream stream1 = new MemoryStream();  
  
//Serialize the Record object to a memory stream using DataContractSerializer.  
DataContractSerializer serializer = new DataContractSerializer(typeof(Record));  
serializer.WriteObject(stream1, record1);  
```  
  
 L'exemple utilise ensuite le <xref:System.Runtime.Serialization.DataContractSerializer> pour désérialiser le flux de mémoire dans un nouvel objet `Record`, puis affiche ce nouvel objet.  
  
```csharp  
stream1.Position = 0;  
  
//Deserialize the Record object back into a new record object.  
Record record2 = (Record)serializer.ReadObject(stream1);  
  
Console.WriteLine("Deserialized record: {0}", record2.ToString());  
```  
  
 Par défaut, le sérialiseur `DataContractSerializer` encode les objets sous la forme d'un flux de données à l'aide d'une représentation XML textuelle. Toutefois, vous pouvez influencer les modalités d'encodage de la représentation XML en passant un enregistreur différent. L'exemple crée un enregistreur binaire en appelant <xref:System.Xml.XmlDictionaryWriter.CreateBinaryWriter%2A>. Il passe ensuite l'enregistreur et l'objet Record au sérialiseur lorsqu'il appelle <xref:System.Runtime.Serialization.DataContractSerializer.WriteObjectContent%2A>. Enfin, l'exemple vide l'enregistreur et génère un rapport sur la longueur des flux de données.  
  
```csharp  
MemoryStream stream2 = new MemoryStream();  
  
XmlDictionaryWriter binaryDictionaryWriter = XmlDictionaryWriter.CreateBinaryWriter(stream2);  
serializer.WriteObject(binaryDictionaryWriter, record1);  
binaryDictionaryWriter.Flush();  
  
//report the length of the streams  
Console.WriteLine("Text Stream is {0} bytes long", stream1.Length);  
Console.WriteLine("Binary Stream is {0} bytes long", stream2.Length);  
```  
  
 Lorsque vous exécutez l'exemple, l'enregistrement d'origine et l'enregistrement désérialisé s'affichent, suivis des différences de longueur entre l'encodage texte et l'encodage binaire. Appuyez sur Entrée dans la fenêtre du client pour l'arrêter.  
  
```console  
Original record: Record: 1 + 2 = 3  
Deserialized record: Record: 1 + 2 = 3  
Text Stream is 233 bytes long  
Binary Stream is 156 bytes long  
  
Press <ENTER> to terminate client.  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Pour configurer, générer et exécuter l'exemple  
  
1. Assurez-vous d’avoir effectué la [procédure d’installation unique pour les exemples de Windows Communication Foundation](one-time-setup-procedure-for-the-wcf-samples.md).  
  
2. Pour générer l’édition C# ou Visual Basic .NET de la solution, conformez-vous aux instructions figurant dans [Building the Windows Communication Foundation Samples](building-the-samples.md).  
  
3. Pour exécuter l'exemple, démarrez le client à partir d'une invite de commandes en tapant client\bin\client.exe.  
  
> [!IMPORTANT]
> Les exemples peuvent déjà être installés sur votre ordinateur. Recherchez le répertoire (par défaut) suivant avant de continuer.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Si ce répertoire n’existe pas, accédez à [Windows Communication Foundation (WCF) et Windows Workflow Foundation (WF) exemples pour .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) pour télécharger tous les exemples Windows Communication Foundation (WCF) et [!INCLUDE[wf1](../../../../includes/wf1-md.md)] . Cet exemple se trouve dans le répertoire suivant.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Data\DataContractSerializer`  
