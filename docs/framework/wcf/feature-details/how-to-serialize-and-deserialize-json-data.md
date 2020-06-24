---
title: 'Comment : utiliser DataContractJsonSerializer'
description: Découvrez comment sérialiser des objets de type .NET dans des données encodées JSON, puis désérialiser ces données en instances de types .NET.
ms.date: 03/25/2019
ms.assetid: 88abc1fb-8196-4ee3-a23b-c6934144d1dd
ms.openlocfilehash: 4ffa0e9dec0a677a38d244b4a0da476d91852da5
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/23/2020
ms.locfileid: "85246803"
---
# <a name="how-to-use-datacontractjsonserializer"></a><span data-ttu-id="731d2-103">Utilisation de DataContractJsonSerializer</span><span class="sxs-lookup"><span data-stu-id="731d2-103">How to use DataContractJsonSerializer</span></span>

> [!NOTE]
> <span data-ttu-id="731d2-104">Cet article concerne <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> .</span><span class="sxs-lookup"><span data-stu-id="731d2-104">This article is about <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>.</span></span> <span data-ttu-id="731d2-105">Pour la plupart des scénarios qui impliquent la sérialisation et la désérialisation de JSON, nous recommandons les API dans le [System.Text.Jssur l’espace de noms](../../../standard/serialization/system-text-json-overview.md).</span><span class="sxs-lookup"><span data-stu-id="731d2-105">For most scenarios that involve serializing and deserializing JSON, we recommend the APIs in the [System.Text.Json namespace](../../../standard/serialization/system-text-json-overview.md).</span></span>

<span data-ttu-id="731d2-106">JSON (JavaScript Object Notation) est un format d'encodage de données efficace qui permet l'échange rapide de petites quantités de données entre les navigateurs clients et les services Web compatibles AJAX.</span><span class="sxs-lookup"><span data-stu-id="731d2-106">JSON (JavaScript Object Notation) is an efficient data encoding format that enables fast exchanges of small amounts of data between client browsers and AJAX-enabled Web services.</span></span>

<span data-ttu-id="731d2-107">Cet article montre comment sérialiser des objets de type .NET dans des données encodées en JSON, puis comment désérialiser des données au format JSON en instances de types .NET.</span><span class="sxs-lookup"><span data-stu-id="731d2-107">This article demonstrates how to serialize .NET type objects into JSON-encoded data and then deserialize data in the JSON format back into instances of .NET types.</span></span> <span data-ttu-id="731d2-108">Cet exemple utilise un contrat de données pour illustrer la sérialisation et la désérialisation d’un type défini par l’utilisateur `Person` et utilise <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> .</span><span class="sxs-lookup"><span data-stu-id="731d2-108">This example uses a data contract to demonstrate serialization and deserialization of a user-defined `Person` type and uses <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>.</span></span>

<span data-ttu-id="731d2-109">Normalement, la sérialisation et la désérialisation JSON sont gérées automatiquement par Windows Communication Foundation (WCF) quand vous utilisez des types de contrat de données dans des opérations de service exposées sur des points de terminaison compatibles AJAX.</span><span class="sxs-lookup"><span data-stu-id="731d2-109">Normally, JSON serialization and deserialization are handled automatically by Windows Communication Foundation (WCF) when you use data contract types in service operations that are exposed over AJAX-enabled endpoints.</span></span> <span data-ttu-id="731d2-110">Toutefois, dans certains cas, vous devrez peut-être utiliser des données JSON directement.</span><span class="sxs-lookup"><span data-stu-id="731d2-110">However, in some cases you may need to work with JSON data directly.</span></span>

<span data-ttu-id="731d2-111">Cet article est basé sur l' [exemple DataContractJsonSerializer](../samples/json-serialization.md).</span><span class="sxs-lookup"><span data-stu-id="731d2-111">This article is based on the [DataContractJsonSerializer sample](../samples/json-serialization.md).</span></span>

## <a name="to-define-the-data-contract-for-a-person-type"></a><span data-ttu-id="731d2-112">Pour définir le contrat de données pour un type Person</span><span class="sxs-lookup"><span data-stu-id="731d2-112">To define the data contract for a Person type</span></span>

1. <span data-ttu-id="731d2-113">Définissez le contrat de données pour `Person` en joignant <xref:System.Runtime.Serialization.DataContractAttribute> à la classe et l'attribut <xref:System.Runtime.Serialization.DataMemberAttribute> aux membres que vous souhaitez sérialiser.</span><span class="sxs-lookup"><span data-stu-id="731d2-113">Define the data contract for `Person` by attaching the <xref:System.Runtime.Serialization.DataContractAttribute> to the class and <xref:System.Runtime.Serialization.DataMemberAttribute> attribute to the members you want to serialize.</span></span> <span data-ttu-id="731d2-114">Pour plus d’informations sur les contrats de données, consultez [conception de contrats de service](../designing-service-contracts.md).</span><span class="sxs-lookup"><span data-stu-id="731d2-114">For more information about data contracts, see [Designing service contracts](../designing-service-contracts.md).</span></span>

    ```csharp
    [DataContract]
    internal class Person
    {
        [DataMember]
        internal string name;

        [DataMember]
        internal int age;
    }
    ```

## <a name="to-serialize-an-instance-of-type-person-to-json"></a><span data-ttu-id="731d2-115">Pour sérialiser une instance de type Person à JSON</span><span class="sxs-lookup"><span data-stu-id="731d2-115">To serialize an instance of type Person to JSON</span></span>

> [!NOTE]
> <span data-ttu-id="731d2-116">Si une erreur se produit pendant la sérialisation d’une réponse sortante sur le serveur ou pour une autre raison, il se peut qu’elle ne soit pas retournée au client en tant qu’erreur.</span><span class="sxs-lookup"><span data-stu-id="731d2-116">If an error occurs during serialization of an outgoing reply on the server or for some other reason, it may not get returned to the client as a fault.</span></span>

1. <span data-ttu-id="731d2-117">Créez une instance du type `Person`.</span><span class="sxs-lookup"><span data-stu-id="731d2-117">Create an instance of the `Person` type.</span></span>

    ```csharp
    var p = new Person();
    p.name = "John";
    p.age = 42;
    ```

2. <span data-ttu-id="731d2-118">Sérialisez l' `Person` objet dans un flux de mémoire à l’aide de <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> .</span><span class="sxs-lookup"><span data-stu-id="731d2-118">Serialize the `Person` object to a memory stream by using the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>.</span></span>

    ```csharp
    var stream1 = new MemoryStream();
    var ser = new DataContractJsonSerializer(typeof(Person));
    ```

3. <span data-ttu-id="731d2-119">Utilisez la méthode <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.WriteObject%2A> pour écrire les données JSON dans le flux.</span><span class="sxs-lookup"><span data-stu-id="731d2-119">Use the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.WriteObject%2A> method to write JSON data to the stream.</span></span>

    ```csharp
    ser.WriteObject(stream1, p);
    ```

4. <span data-ttu-id="731d2-120">Affichez la sortie JSON.</span><span class="sxs-lookup"><span data-stu-id="731d2-120">Show the JSON output.</span></span>

    ```csharp
    stream1.Position = 0;
    var sr = new StreamReader(stream1);
    Console.Write("JSON form of Person object: ");
    Console.WriteLine(sr.ReadToEnd());
    ```

## <a name="to-deserialize-an-instance-of-type-person-from-json"></a><span data-ttu-id="731d2-121">Pour désérialiser une instance de type Person depuis JSON</span><span class="sxs-lookup"><span data-stu-id="731d2-121">To deserialize an instance of type Person from JSON</span></span>

1. <span data-ttu-id="731d2-122">Désérialisez les données encodées JSON dans une nouvelle instance de `Person` à l'aide de la méthode <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.ReadObject%2A> de <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>.</span><span class="sxs-lookup"><span data-stu-id="731d2-122">Deserialize the JSON-encoded data into a new instance of `Person` by using the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.ReadObject%2A> method of the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>.</span></span>

    ```csharp
    stream1.Position = 0;
    var p2 = (Person)ser.ReadObject(stream1);
    ```

2. <span data-ttu-id="731d2-123">Affichez les résultats.</span><span class="sxs-lookup"><span data-stu-id="731d2-123">Show the results.</span></span>

    ```csharp
    Console.WriteLine($"Deserialized back, got name={p2.name}, age={p2.age}");
    ```

## <a name="example"></a><span data-ttu-id="731d2-124">Exemple</span><span class="sxs-lookup"><span data-stu-id="731d2-124">Example</span></span>

```csharp
// Create a User object and serialize it to a JSON stream.
public static string WriteFromObject()
{
    // Create User object.
    var user = new User("Bob", 42);

    // Create a stream to serialize the object to.
    var ms = new MemoryStream();

    // Serializer the User object to the stream.
    var ser = new DataContractJsonSerializer(typeof(User));
    ser.WriteObject(ms, user);
    byte[] json = ms.ToArray();
    ms.Close();
    return Encoding.UTF8.GetString(json, 0, json.Length);
}

// Deserialize a JSON stream to a User object.
public static User ReadToObject(string json)
{
    var deserializedUser = new User();
    var ms = new MemoryStream(Encoding.UTF8.GetBytes(json));
    var ser = new DataContractJsonSerializer(deserializedUser.GetType());
    deserializedUser = ser.ReadObject(ms) as User;
    ms.Close();
    return deserializedUser;
}
```

> [!NOTE]
> <span data-ttu-id="731d2-125">Le sérialiseur JSON lève une exception de sérialisation pour les contrats de données dont plusieurs membres portent le même nom, comme illustré dans l'exemple de code suivant.</span><span class="sxs-lookup"><span data-stu-id="731d2-125">The JSON serializer throws a serialization exception for data contracts that have multiple members with the same name, as shown in the following sample code.</span></span>

```csharp
[DataContract]
public class TestDuplicateDataBase
{
    [DataMember]
    public int field1 = 123;
}

[DataContract]
public class TestDuplicateDataDerived : TestDuplicateDataBase
{
    [DataMember]
    public new int field1 = 999;
}
```

## <a name="see-also"></a><span data-ttu-id="731d2-126">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="731d2-126">See also</span></span>

- [<span data-ttu-id="731d2-127">Sérialisation JSON dans .NET</span><span class="sxs-lookup"><span data-stu-id="731d2-127">JSON serialization in .NET</span></span>](../../../standard/serialization/system-text-json-overview.md)
