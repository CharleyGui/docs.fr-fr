---
title: Sérialisation JSON
ms.date: 03/30/2017
ms.assetid: 3c2c4747-7510-4bdf-b4fe-64f98428ef4a
ms.openlocfilehash: 9b1e20c6262f286a4b81f8c368a153fb5a26193b
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69913960"
---
# <a name="json-serialization"></a><span data-ttu-id="dc7ac-102">Sérialisation JSON</span><span class="sxs-lookup"><span data-stu-id="dc7ac-102">JSON Serialization</span></span>
<span data-ttu-id="dc7ac-103">Cet exemple montre comment utiliser le <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> pour sérialiser et désérialiser des données au format JSON (JavaScript Objet Notation).</span><span class="sxs-lookup"><span data-stu-id="dc7ac-103">This sample demonstrates how to use the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> to serialize and deserialize data in the JavaScript Object Notation (JSON) format.</span></span> <span data-ttu-id="dc7ac-104">Ce moteur de sérialisation convertit les données JSON en instances de .NET Framework types et les renvoie en données JSON.</span><span class="sxs-lookup"><span data-stu-id="dc7ac-104">This serialization engine converts JSON data into instances of .NET Framework types and back into JSON data.</span></span> <span data-ttu-id="dc7ac-105"><xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> prend en charge les mêmes types que <xref:System.Runtime.Serialization.DataContractSerializer>.</span><span class="sxs-lookup"><span data-stu-id="dc7ac-105"><xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> supports the same types as <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span> <span data-ttu-id="dc7ac-106">Le format de données JSON est particulièrement utile lors de l'écriture d'applications Web de style JavaScript et XML (AJAX) asynchrones.</span><span class="sxs-lookup"><span data-stu-id="dc7ac-106">The JSON data format is especially useful when writing Asynchronous JavaScript and XML (AJAX)-style Web applications.</span></span> <span data-ttu-id="dc7ac-107">La prise en charge d’AJAX dans Windows Communication Foundation (WCF) est optimisée pour une utilisation avec ASP.NET AJAX par le biais du contrôle ScriptManager.</span><span class="sxs-lookup"><span data-stu-id="dc7ac-107">AJAX support in Windows Communication Foundation (WCF) is optimized for use with ASP.NET AJAX through the ScriptManager control.</span></span> <span data-ttu-id="dc7ac-108">Pour obtenir des exemples d’utilisation de Windows Communication Foundation (WCF) avec ASP.NET AJAX, consultez les [exemples Ajax](ajax.md).</span><span class="sxs-lookup"><span data-stu-id="dc7ac-108">For examples of how to use Windows Communication Foundation (WCF) with ASP.NET AJAX, see the [AJAX Samples](ajax.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="dc7ac-109">La procédure d'installation ainsi que les instructions de génération correspondant à cet exemple figurent en fin de rubrique.</span><span class="sxs-lookup"><span data-stu-id="dc7ac-109">The set-up procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="dc7ac-110">L'exemple utilise un contrat de données `Person` pour illustrer la sérialisation et la désérialisation.</span><span class="sxs-lookup"><span data-stu-id="dc7ac-110">The sample uses a `Person` data contract to demonstrate serialization and deserialization.</span></span>  

```csharp
[DataContract]
class Person
{
    [DataMember]
    internal string name;

    [DataMember]
    internal int age;
}
```

 <span data-ttu-id="dc7ac-111">Pour sérialiser une instance du type `Person` en JSON, créez d'abord le <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> et utilisez la méthode `WriteObject` pour écrire des données JSON dans un flux.</span><span class="sxs-lookup"><span data-stu-id="dc7ac-111">To serialize an instance of the `Person` type to JSON, create the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> first and use the `WriteObject` method to write JSON data to a stream.</span></span>  

```csharp
Person p = new Person();
//Set up Person object...
MemoryStream stream1 = new MemoryStream();
DataContractJsonSerializer ser = new DataContractJsonSerializer(typeof(Person));
ser.WriteObject(stream1, p);
```

 <span data-ttu-id="dc7ac-112">Le flux de mémoire contient des données JSON valides.</span><span class="sxs-lookup"><span data-stu-id="dc7ac-112">The memory stream contains valid JSON data.</span></span>
  
```json  
{"age":42,"name":"John"}  
```  
  
 <span data-ttu-id="dc7ac-113">L'exemple illustre la désérialisation de données JSON dans un objet.</span><span class="sxs-lookup"><span data-stu-id="dc7ac-113">The sample demonstrates deserializing from JSON data into an object.</span></span> <span data-ttu-id="dc7ac-114">Ensuite, vous rembobinez le flux et appelez `ReadObject`.</span><span class="sxs-lookup"><span data-stu-id="dc7ac-114">You then rewind the stream and call `ReadObject`.</span></span>  

```csharp
Person p2 = (Person)ser.ReadObject(stream1);
```

 <span data-ttu-id="dc7ac-115">L'examen de l'objet `p2` révèle que les données JSON ont été correctement désérialisées.</span><span class="sxs-lookup"><span data-stu-id="dc7ac-115">Examining the `p2` object reveals that the JSON data has been deserialized correctly.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="dc7ac-116">Les exemples peuvent déjà être installés sur votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="dc7ac-116">The samples may already be installed on your machine.</span></span> <span data-ttu-id="dc7ac-117">Recherchez le répertoire (par défaut) suivant avant de continuer.</span><span class="sxs-lookup"><span data-stu-id="dc7ac-117">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="dc7ac-118">Si ce répertoire n’existe pas, accédez à [Windows Communication Foundation (WCF) et Windows Workflow Foundation (WF) exemples pour .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) pour télécharger tous les exemples Windows Communication Foundation (WCF [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ) et.</span><span class="sxs-lookup"><span data-stu-id="dc7ac-118">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="dc7ac-119">Cet exemple se trouve dans le répertoire suivant.</span><span class="sxs-lookup"><span data-stu-id="dc7ac-119">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Ajax\JsonSerialization`  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="dc7ac-120">Pour configurer, générer et exécuter l'exemple</span><span class="sxs-lookup"><span data-stu-id="dc7ac-120">To set up, build and run the sample</span></span>  
  
1. <span data-ttu-id="dc7ac-121">Générez la solution JsonSerialization. sln comme décrit dans [génération des exemples de Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="dc7ac-121">Build the solution JsonSerialization.sln as described in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
2. <span data-ttu-id="dc7ac-122">Exécutez l'application console qui en résulte.</span><span class="sxs-lookup"><span data-stu-id="dc7ac-122">Run the resulting console application.</span></span>  
