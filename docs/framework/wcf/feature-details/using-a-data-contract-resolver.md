---
title: Utilisation d'un programme de résolution de contrat de données
ms.date: 03/30/2017
ms.assetid: 2e68a16c-36f0-4df4-b763-32021bff2b89
ms.openlocfilehash: 20abd4d928fc51eb359949ecbb216615e9659b7f
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84595022"
---
# <a name="using-a-data-contract-resolver"></a><span data-ttu-id="0c9e0-102">Utilisation d'un programme de résolution de contrat de données</span><span class="sxs-lookup"><span data-stu-id="0c9e0-102">Using a Data Contract Resolver</span></span>
<span data-ttu-id="0c9e0-103">Un programme de résolution de contrat de données vous permet de configurer des types connus de manière dynamique.</span><span class="sxs-lookup"><span data-stu-id="0c9e0-103">A data contract resolver allows you to configure known types dynamically.</span></span> <span data-ttu-id="0c9e0-104">Les types connus sont nécessaires lors de la sérialisation ou de la désérialisation d'un type non attendu par un contrat de données.</span><span class="sxs-lookup"><span data-stu-id="0c9e0-104">Known types are required when serializing or deserializing a type not expected by a data contract.</span></span> <span data-ttu-id="0c9e0-105">Pour plus d’informations sur les types connus, consultez [types connus de contrat de données](data-contract-known-types.md).</span><span class="sxs-lookup"><span data-stu-id="0c9e0-105">For more information about known types, see [Data Contract Known Types](data-contract-known-types.md).</span></span> <span data-ttu-id="0c9e0-106">Les types connus sont généralement spécifiés statiquement.</span><span class="sxs-lookup"><span data-stu-id="0c9e0-106">Known types are normally specified statically.</span></span> <span data-ttu-id="0c9e0-107">Cela signifie que vous devez connaître tous les types possibles qu'une opération peut recevoir pendant son implémentation.</span><span class="sxs-lookup"><span data-stu-id="0c9e0-107">This means you would have to know all the possible types an operation may receive while implementing the operation.</span></span> <span data-ttu-id="0c9e0-108">Voici les scénarios où cela n'est pas vrai et où il est important de pouvoir spécifier les types connus de façon dynamique.</span><span class="sxs-lookup"><span data-stu-id="0c9e0-108">There are scenarios in which this is not true and being able to specify known types dynamically is important.</span></span>  
  
## <a name="creating-a-data-contract-resolver"></a><span data-ttu-id="0c9e0-109">Création d'un programme de résolution de contrat de données</span><span class="sxs-lookup"><span data-stu-id="0c9e0-109">Creating a Data Contract Resolver</span></span>  
 <span data-ttu-id="0c9e0-110">La création d'un programme de résolution de contrat de données implique l'implémentation de deux méthodes, <xref:System.Runtime.Serialization.DataContractResolver.TryResolveType%2A> et <xref:System.Runtime.Serialization.DataContractResolver.ResolveName%2A>.</span><span class="sxs-lookup"><span data-stu-id="0c9e0-110">Creating a data contract resolver involves implementing two methods, <xref:System.Runtime.Serialization.DataContractResolver.TryResolveType%2A> and <xref:System.Runtime.Serialization.DataContractResolver.ResolveName%2A>.</span></span> <span data-ttu-id="0c9e0-111">Ces deux méthodes implémentent des rappels utilisés respectivement lors de la sérialisation et de la désérialisation.</span><span class="sxs-lookup"><span data-stu-id="0c9e0-111">These two methods implement callbacks that are used during serialization and deserialization, respectively.</span></span> <span data-ttu-id="0c9e0-112">La méthode <xref:System.Runtime.Serialization.DataContractResolver.TryResolveType%2A> est appelée lors de la sérialisation, prend un type de contrat de données et le mappe à un nom et espace de noms `xsi:type`.</span><span class="sxs-lookup"><span data-stu-id="0c9e0-112">The <xref:System.Runtime.Serialization.DataContractResolver.TryResolveType%2A> method is invoked during serialization and takes a data contract type and maps it to an `xsi:type` name and namespace.</span></span> <span data-ttu-id="0c9e0-113">La méthode <xref:System.Runtime.Serialization.DataContractResolver.ResolveName%2A> est appelée lors de la désérialisation, prend un nom et espace de noms `xsi:type` et le résout en type de contrat de données.</span><span class="sxs-lookup"><span data-stu-id="0c9e0-113">The <xref:System.Runtime.Serialization.DataContractResolver.ResolveName%2A> method is invoked during deserialization and takes an `xsi:type` name and namespace and resolves it to a data contract type.</span></span> <span data-ttu-id="0c9e0-114">Ces deux méthodes ont un paramètre `knownTypeResolver` qui peut être utilisé pour utiliser le programme de résolution de type connu par défaut dans votre implémentation.</span><span class="sxs-lookup"><span data-stu-id="0c9e0-114">Both of these methods have a `knownTypeResolver` parameter that can be used to use the default known type resolver in your implementation.</span></span>  
  
 <span data-ttu-id="0c9e0-115">L'exemple suivant indique comment implémenter un objet <xref:System.Runtime.Serialization.DataContractResolver> pour un mappage sur et à partir d'un type de contrat de données nommé `Customer`, dérivé d'un type de contrat de données `Person`.</span><span class="sxs-lookup"><span data-stu-id="0c9e0-115">The following example shows how to implement a <xref:System.Runtime.Serialization.DataContractResolver> to map to and from a data contract type named `Customer` derived from a data contract type `Person`.</span></span>  
  
```csharp  
public class MyCustomerResolver : DataContractResolver  
{  
    public override bool TryResolveType(Type dataContractType, Type declaredType, DataContractResolver knownTypeResolver, out XmlDictionaryString typeName, out XmlDictionaryString typeNamespace)  
    {  
        if (dataContractType == typeof(Customer))  
        {  
            XmlDictionary dictionary = new XmlDictionary();  
            typeName = dictionary.Add("SomeCustomer");  
            typeNamespace = dictionary.Add("http://tempuri.com");  
            return true;  
        }  
        else  
        {  
            return knownTypeResolver.TryResolveType(dataContractType, declaredType, null, out typeName, out typeNamespace);  
        }  
    }  
  
    public override Type ResolveName(string typeName, string typeNamespace, DataContractResolver knownTypeResolver)  
    {  
        if (typeName == "SomeCustomer" && typeNamespace == "http://tempuri.com")  
        {  
            return typeof(Customer);  
        }  
        else  
        {  
            return knownTypeResolver.ResolveName(typeName, typeNamespace, null);  
        }  
    }  
}  
```  
  
 <span data-ttu-id="0c9e0-116">Une fois que vous avez défini un objet <xref:System.Runtime.Serialization.DataContractResolver>, vous pouvez l'utiliser en le transmettant au constructeur <xref:System.Runtime.Serialization.DataContractSerializer>, comme indiqué dans l'exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="0c9e0-116">Once you have defined a <xref:System.Runtime.Serialization.DataContractResolver> you can use it by passing it to the <xref:System.Runtime.Serialization.DataContractSerializer> constructor as shown in the following example.</span></span>  
  
```csharp
XmlObjectSerializer serializer = new DataContractSerializer(typeof(Customer), null, Int32.MaxValue, false, false, null, new MyCustomerResolver());  
```  
  
 <span data-ttu-id="0c9e0-117">Vous pouvez spécifier un objet <xref:System.Runtime.Serialization.DataContractResolver> dans un appel aux méthodes <xref:System.Runtime.Serialization.DataContractSerializer.ReadObject%2A?displayProperty=nameWithType> ou <xref:System.Runtime.Serialization.DataContractSerializer.WriteObject%2A?displayProperty=nameWithType>, comme indiqué dans l'exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="0c9e0-117">You can specify a <xref:System.Runtime.Serialization.DataContractResolver> in a call to the <xref:System.Runtime.Serialization.DataContractSerializer.ReadObject%2A?displayProperty=nameWithType> or <xref:System.Runtime.Serialization.DataContractSerializer.WriteObject%2A?displayProperty=nameWithType> methods, as shown in the following example.</span></span>  
  
```csharp
MemoryStream ms = new MemoryStream();  
DataContractSerializer serializer = new DataContractSerializer(typeof(Customer));  
XmlDictionaryWriter writer = XmlDictionaryWriter.CreateDictionaryWriter(XmlWriter.Create(ms));  
serializer.WriteObject(writer, new Customer(), new MyCustomerResolver());  
writer.Flush();  
ms.Position = 0;  
Console.WriteLine(((Customer)serializer.ReadObject(XmlDictionaryReader.CreateDictionaryReader(XmlReader.Create(ms)), false, new MyCustomerResolver()));  
```  
  
 <span data-ttu-id="0c9e0-118">Vous pouvez également le définir sur l'objet <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior> comme le montre l'exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="0c9e0-118">Or you can set it on the <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior> as shown in the following example.</span></span>  
  
```csharp
ServiceHost host = new ServiceHost(typeof(MyService));  
  
ContractDescription cd = host.Description.Endpoints[0].Contract;  
OperationDescription myOperationDescription = cd.Operations.Find("Echo");  
  
DataContractSerializerOperationBehavior serializerBehavior = myOperationDescription.Behaviors.Find<DataContractSerializerOperationBehavior>();  
if (serializerBehavior == null)  
{  
    serializerBehavior = new DataContractSerializerOperationBehavior(myOperationDescription);  
    myOperationDescription.Behaviors.Add(serializerBehavior);  
}  
  
SerializerBehavior.DataContractResolver = new MyCustomerResolver();  
```  
  
 <span data-ttu-id="0c9e0-119">Spécifiez de façon déclarative un programme de résolution de contrat de données en implémentant un attribut qui peut être appliqué à un service.</span><span class="sxs-lookup"><span data-stu-id="0c9e0-119">You can declaratively specify a data contract resolver by implementing an attribute that can be applied to a service.</span></span>  <span data-ttu-id="0c9e0-120">Pour plus d’informations, consultez l’exemple [KnownAssemblyAttribute](../samples/knownassemblyattribute.md) .</span><span class="sxs-lookup"><span data-stu-id="0c9e0-120">For more information, see the [KnownAssemblyAttribute](../samples/knownassemblyattribute.md) sample.</span></span> <span data-ttu-id="0c9e0-121">Cet exemple implémente un attribut appelé « KnownAssembly » qui ajoute un programme de résolution de contrat de données personnalisé au comportement du service.</span><span class="sxs-lookup"><span data-stu-id="0c9e0-121">This sample implements an attribute called "KnownAssembly" that adds a custom data contract resolver to the service’s behavior.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0c9e0-122">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="0c9e0-122">See also</span></span>

- [<span data-ttu-id="0c9e0-123">Types connus de contrats de données</span><span class="sxs-lookup"><span data-stu-id="0c9e0-123">Data Contract Known Types</span></span>](data-contract-known-types.md)
- [<span data-ttu-id="0c9e0-124">DataContractSerializer, exemple</span><span class="sxs-lookup"><span data-stu-id="0c9e0-124">DataContractSerializer Sample</span></span>](../samples/datacontractserializer-sample.md)
- [<span data-ttu-id="0c9e0-125">KnownAssemblyAttribute</span><span class="sxs-lookup"><span data-stu-id="0c9e0-125">KnownAssemblyAttribute</span></span>](../samples/knownassemblyattribute.md)
