---
title: Exemple DataContractJsonSerializer
ms.date: 03/30/2017
ms.assetid: 3c2c4747-7510-4bdf-b4fe-64f98428ef4a
ms.openlocfilehash: 4aa0ee679ae424251000b14abfbacf0590a6ccd3
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84592019"
---
# <a name="datacontractjsonserializer-sample"></a><span data-ttu-id="1a4dd-102">Exemple DataContractJsonSerializer</span><span class="sxs-lookup"><span data-stu-id="1a4dd-102">DataContractJsonSerializer sample</span></span>

> [!NOTE]
> <span data-ttu-id="1a4dd-103">Cet exemple est destiné à <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> .</span><span class="sxs-lookup"><span data-stu-id="1a4dd-103">This sample is for <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>.</span></span> <span data-ttu-id="1a4dd-104">Pour la plupart des scénarios qui impliquent la sérialisation et la désérialisation de JSON, nous vous recommandons d’utiliser les API de l' [espace de noms System. Text. JSON](../../../standard/serialization/system-text-json-overview.md).</span><span class="sxs-lookup"><span data-stu-id="1a4dd-104">For most scenarios that involve serializing and deserializing JSON, we recommend the APIs in the [System.Text.Json namespace](../../../standard/serialization/system-text-json-overview.md).</span></span>

<span data-ttu-id="1a4dd-105"><xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> prend en charge les mêmes types que <xref:System.Runtime.Serialization.DataContractSerializer>.</span><span class="sxs-lookup"><span data-stu-id="1a4dd-105"><xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> supports the same types as <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span> <span data-ttu-id="1a4dd-106">Le format de données JSON est particulièrement utile lors de l'écriture d'applications Web de style JavaScript et XML (AJAX) asynchrones.</span><span class="sxs-lookup"><span data-stu-id="1a4dd-106">The JSON data format is especially useful when writing Asynchronous JavaScript and XML (AJAX)-style Web applications.</span></span> <span data-ttu-id="1a4dd-107">La prise en charge d’AJAX dans Windows Communication Foundation (WCF) est optimisée pour une utilisation avec ASP.NET AJAX par le biais du contrôle ScriptManager.</span><span class="sxs-lookup"><span data-stu-id="1a4dd-107">AJAX support in Windows Communication Foundation (WCF) is optimized for use with ASP.NET AJAX through the ScriptManager control.</span></span> <span data-ttu-id="1a4dd-108">Pour obtenir des exemples d’utilisation de Windows Communication Foundation (WCF) avec ASP.NET AJAX, consultez les [exemples Ajax](ajax.md).</span><span class="sxs-lookup"><span data-stu-id="1a4dd-108">For examples of how to use Windows Communication Foundation (WCF) with ASP.NET AJAX, see the [AJAX Samples](ajax.md).</span></span>  
  
<span data-ttu-id="1a4dd-109">La procédure d'installation ainsi que les instructions de génération correspondant à cet exemple figurent en fin de rubrique.</span><span class="sxs-lookup"><span data-stu-id="1a4dd-109">The set-up procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
<span data-ttu-id="1a4dd-110">L'exemple utilise un contrat de données `Person` pour illustrer la sérialisation et la désérialisation.</span><span class="sxs-lookup"><span data-stu-id="1a4dd-110">The sample uses a `Person` data contract to demonstrate serialization and deserialization.</span></span>  

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

 <span data-ttu-id="1a4dd-111">Pour sérialiser une instance du type `Person` en JSON, créez d'abord le <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> et utilisez la méthode `WriteObject` pour écrire des données JSON dans un flux.</span><span class="sxs-lookup"><span data-stu-id="1a4dd-111">To serialize an instance of the `Person` type to JSON, create the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> first and use the `WriteObject` method to write JSON data to a stream.</span></span>  

```csharp
Person p = new Person();
//Set up Person object...
MemoryStream stream1 = new MemoryStream();
DataContractJsonSerializer ser = new DataContractJsonSerializer(typeof(Person));
ser.WriteObject(stream1, p);
```

 <span data-ttu-id="1a4dd-112">Le flux de mémoire contient des données JSON valides.</span><span class="sxs-lookup"><span data-stu-id="1a4dd-112">The memory stream contains valid JSON data.</span></span>
  
```json  
{"age":42,"name":"John"}  
```  
  
 <span data-ttu-id="1a4dd-113">L'exemple illustre la désérialisation de données JSON dans un objet.</span><span class="sxs-lookup"><span data-stu-id="1a4dd-113">The sample demonstrates deserializing from JSON data into an object.</span></span> <span data-ttu-id="1a4dd-114">Ensuite, vous rembobinez le flux et appelez `ReadObject`.</span><span class="sxs-lookup"><span data-stu-id="1a4dd-114">You then rewind the stream and call `ReadObject`.</span></span>  

```csharp
Person p2 = (Person)ser.ReadObject(stream1);
```

 <span data-ttu-id="1a4dd-115">L'examen de l'objet `p2` révèle que les données JSON ont été correctement désérialisées.</span><span class="sxs-lookup"><span data-stu-id="1a4dd-115">Examining the `p2` object reveals that the JSON data has been deserialized correctly.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="1a4dd-116">Les exemples peuvent déjà être installés sur votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="1a4dd-116">The samples may already be installed on your machine.</span></span> <span data-ttu-id="1a4dd-117">Recherchez le répertoire (par défaut) suivant avant de continuer.</span><span class="sxs-lookup"><span data-stu-id="1a4dd-117">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="1a4dd-118">Si ce répertoire n’existe pas, accédez à [Windows Communication Foundation (WCF) et Windows Workflow Foundation (WF) exemples pour .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) pour télécharger tous les exemples Windows Communication Foundation (WCF) et [!INCLUDE[wf1](../../../../includes/wf1-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="1a4dd-118">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="1a4dd-119">Cet exemple se trouve dans le répertoire suivant.</span><span class="sxs-lookup"><span data-stu-id="1a4dd-119">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Ajax\JsonSerialization`  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="1a4dd-120">Pour configurer, générer et exécuter l'exemple</span><span class="sxs-lookup"><span data-stu-id="1a4dd-120">To set up, build and run the sample</span></span>  
  
1. <span data-ttu-id="1a4dd-121">Générez la solution JsonSerialization. sln comme décrit dans [génération des exemples de Windows Communication Foundation](building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="1a4dd-121">Build the solution JsonSerialization.sln as described in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>  
  
2. <span data-ttu-id="1a4dd-122">Exécutez l'application console qui en résulte.</span><span class="sxs-lookup"><span data-stu-id="1a4dd-122">Run the resulting console application.</span></span>  
