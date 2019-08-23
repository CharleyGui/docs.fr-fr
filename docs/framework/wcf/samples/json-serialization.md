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
# <a name="json-serialization"></a>Sérialisation JSON
Cet exemple montre comment utiliser le <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> pour sérialiser et désérialiser des données au format JSON (JavaScript Objet Notation). Ce moteur de sérialisation convertit les données JSON en instances de .NET Framework types et les renvoie en données JSON. <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> prend en charge les mêmes types que <xref:System.Runtime.Serialization.DataContractSerializer>. Le format de données JSON est particulièrement utile lors de l'écriture d'applications Web de style JavaScript et XML (AJAX) asynchrones. La prise en charge d’AJAX dans Windows Communication Foundation (WCF) est optimisée pour une utilisation avec ASP.NET AJAX par le biais du contrôle ScriptManager. Pour obtenir des exemples d’utilisation de Windows Communication Foundation (WCF) avec ASP.NET AJAX, consultez les [exemples Ajax](ajax.md).  
  
> [!NOTE]
> La procédure d'installation ainsi que les instructions de génération correspondant à cet exemple figurent en fin de rubrique.  
  
 L'exemple utilise un contrat de données `Person` pour illustrer la sérialisation et la désérialisation.  

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

 Pour sérialiser une instance du type `Person` en JSON, créez d'abord le <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> et utilisez la méthode `WriteObject` pour écrire des données JSON dans un flux.  

```csharp
Person p = new Person();
//Set up Person object...
MemoryStream stream1 = new MemoryStream();
DataContractJsonSerializer ser = new DataContractJsonSerializer(typeof(Person));
ser.WriteObject(stream1, p);
```

 Le flux de mémoire contient des données JSON valides.
  
```json  
{"age":42,"name":"John"}  
```  
  
 L'exemple illustre la désérialisation de données JSON dans un objet. Ensuite, vous rembobinez le flux et appelez `ReadObject`.  

```csharp
Person p2 = (Person)ser.ReadObject(stream1);
```

 L'examen de l'objet `p2` révèle que les données JSON ont été correctement désérialisées.  
  
> [!IMPORTANT]
>  Les exemples peuvent déjà être installés sur votre ordinateur. Recherchez le répertoire (par défaut) suivant avant de continuer.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Si ce répertoire n’existe pas, accédez à [Windows Communication Foundation (WCF) et Windows Workflow Foundation (WF) exemples pour .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) pour télécharger tous les exemples Windows Communication Foundation (WCF [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ) et. Cet exemple se trouve dans le répertoire suivant.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Ajax\JsonSerialization`  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Pour configurer, générer et exécuter l'exemple  
  
1. Générez la solution JsonSerialization. sln comme décrit dans [génération des exemples de Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
2. Exécutez l'application console qui en résulte.  
