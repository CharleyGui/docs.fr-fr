---
title: 'Procédure : sérialiser et désérialiser des données JSON'
ms.date: 03/25/2019
ms.assetid: 88abc1fb-8196-4ee3-a23b-c6934144d1dd
ms.openlocfilehash: 0c56b298737dc9b9902f13c586edffb3d05257f8
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67783014"
---
# <a name="how-to-serialize-and-deserialize-json-data"></a><span data-ttu-id="7e3e2-102">Procédure : Sérialiser et désérialiser des données JSON</span><span class="sxs-lookup"><span data-stu-id="7e3e2-102">How to: Serialize and deserialize JSON data</span></span>
<span data-ttu-id="7e3e2-103">JSON (JavaScript Object Notation) est un format d'encodage de données efficace qui permet l'échange rapide de petites quantités de données entre les navigateurs clients et les services Web compatibles AJAX.</span><span class="sxs-lookup"><span data-stu-id="7e3e2-103">JSON (JavaScript Object Notation) is an efficient data encoding format that enables fast exchanges of small amounts of data between client browsers and AJAX-enabled Web services.</span></span>  
  
 <span data-ttu-id="7e3e2-104">Cet article montre comment sérialiser des objets de type .NET dans des données encodées en JSON et ensuite désérialiser les données au format JSON en instances des types .NET.</span><span class="sxs-lookup"><span data-stu-id="7e3e2-104">This article demonstrates how to serialize .NET type objects into JSON-encoded data and then deserialize data in the JSON format back into instances of .NET types.</span></span> <span data-ttu-id="7e3e2-105">Cet exemple utilise un contrat de données pour illustrer la sérialisation et désérialisation de défini par l’utilisateur `Person` type et utilise <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>.</span><span class="sxs-lookup"><span data-stu-id="7e3e2-105">This example uses a data contract to demonstrate serialization and deserialization of a user-defined `Person` type and uses <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>.</span></span>  
  
 <span data-ttu-id="7e3e2-106">En règle générale, la désérialisation et la sérialisation JSON sont gérées automatiquement par Windows Communication Foundation (WCF) lorsque vous utilisez des types de contrat de données dans des opérations de service exposées sur des points de terminaison compatibles AJAX.</span><span class="sxs-lookup"><span data-stu-id="7e3e2-106">Normally, JSON serialization and deserialization are handled automatically by Windows Communication Foundation (WCF) when you use data contract types in service operations that are exposed over AJAX-enabled endpoints.</span></span> <span data-ttu-id="7e3e2-107">Toutefois, dans certains cas, vous devrez peut-être travailler avec des données JSON directement.</span><span class="sxs-lookup"><span data-stu-id="7e3e2-107">However, in some cases you may need to work with JSON data directly.</span></span>   
  
> [!NOTE]
>  <span data-ttu-id="7e3e2-108">Si une erreur se produit pendant la sérialisation d’une réponse sortante sur le serveur ou pour une raison quelconque, elle ne peut pas obtenir retournée au client sous forme d’erreur.</span><span class="sxs-lookup"><span data-stu-id="7e3e2-108">If an error occurs during serialization of an outgoing reply on the server or for some other reason, it may not get returned to the client as a fault.</span></span>  
  
 <span data-ttu-id="7e3e2-109">Cet article est basé sur le [sérialisation JSON](../samples/json-serialization.md) exemple.</span><span class="sxs-lookup"><span data-stu-id="7e3e2-109">This article is based on the [JSON serialization](../samples/json-serialization.md) sample.</span></span>  
  
## <a name="to-define-the-data-contract-for-a-person-type"></a><span data-ttu-id="7e3e2-110">Pour définir le contrat de données pour un type de personne</span><span class="sxs-lookup"><span data-stu-id="7e3e2-110">To define the data contract for a Person type</span></span> 
  
1. <span data-ttu-id="7e3e2-111">Définissez le contrat de données pour `Person` en joignant <xref:System.Runtime.Serialization.DataContractAttribute> à la classe et l'attribut <xref:System.Runtime.Serialization.DataMemberAttribute> aux membres que vous souhaitez sérialiser.</span><span class="sxs-lookup"><span data-stu-id="7e3e2-111">Define the data contract for `Person` by attaching the <xref:System.Runtime.Serialization.DataContractAttribute> to the class and <xref:System.Runtime.Serialization.DataMemberAttribute> attribute to the members you want to serialize.</span></span> <span data-ttu-id="7e3e2-112">Pour plus d’informations sur les contrats de données, consultez [conception de contrats de service](../designing-service-contracts.md).</span><span class="sxs-lookup"><span data-stu-id="7e3e2-112">For more information about data contracts, see [Designing service contracts](../designing-service-contracts.md).</span></span>  
  
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
  
## <a name="to-serialize-an-instance-of-type-person-to-json"></a><span data-ttu-id="7e3e2-113">Pour sérialiser une instance de type Person à JSON</span><span class="sxs-lookup"><span data-stu-id="7e3e2-113">To serialize an instance of type Person to JSON</span></span>  
  
1. <span data-ttu-id="7e3e2-114">Créez une instance du type `Person`.</span><span class="sxs-lookup"><span data-stu-id="7e3e2-114">Create an instance of the `Person` type.</span></span>  
  
    ```csharp  
    var p = new Person();  
    p.name = "John";  
    p.age = 42;  
    ```  
  
2. <span data-ttu-id="7e3e2-115">Sérialiser le `Person` objet dans un flux de mémoire à l’aide de la <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>.</span><span class="sxs-lookup"><span data-stu-id="7e3e2-115">Serialize the `Person` object to a memory stream by using the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>.</span></span>  
  
    ```csharp  
    var stream1 = new MemoryStream();  
    var ser = new DataContractJsonSerializer(typeof(Person));  
    ```  
  
3. <span data-ttu-id="7e3e2-116">Utilisez la méthode <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.WriteObject%2A> pour écrire les données JSON dans le flux.</span><span class="sxs-lookup"><span data-stu-id="7e3e2-116">Use the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.WriteObject%2A> method to write JSON data to the stream.</span></span>  
  
    ```csharp  
    ser.WriteObject(stream1, p);  
    ```  
  
4. <span data-ttu-id="7e3e2-117">Affichez la sortie JSON.</span><span class="sxs-lookup"><span data-stu-id="7e3e2-117">Show the JSON output.</span></span>  
  
    ```csharp  
    stream1.Position = 0;  
    var sr = new StreamReader(stream1);  
    Console.Write("JSON form of Person object: ");  
    Console.WriteLine(sr.ReadToEnd());  
    ```  
  
## <a name="to-deserialize-an-instance-of-type-person-from-json"></a><span data-ttu-id="7e3e2-118">Pour désérialiser une instance de type Person depuis JSON</span><span class="sxs-lookup"><span data-stu-id="7e3e2-118">To deserialize an instance of type Person from JSON</span></span>  
  
1. <span data-ttu-id="7e3e2-119">Désérialisez les données encodées JSON dans une nouvelle instance de `Person` à l'aide de la méthode <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.ReadObject%2A> de <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>.</span><span class="sxs-lookup"><span data-stu-id="7e3e2-119">Deserialize the JSON-encoded data into a new instance of `Person` by using the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.ReadObject%2A> method of the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>.</span></span>  
  
    ```csharp  
    stream1.Position = 0;  
    var p2 = (Person)ser.ReadObject(stream1);  
    ```  
  
2. <span data-ttu-id="7e3e2-120">Affichez les résultats.</span><span class="sxs-lookup"><span data-stu-id="7e3e2-120">Show the results.</span></span>  
  
    ```csharp  
    Console.WriteLine($"Deserialized back, got name={p2.name}, age={p2.age}");  
    ```  
  
## <a name="example"></a><span data-ttu-id="7e3e2-121">Exemples</span><span class="sxs-lookup"><span data-stu-id="7e3e2-121">Example</span></span>  
  
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
>  <span data-ttu-id="7e3e2-122">Le sérialiseur JSON lève une exception de sérialisation pour les contrats de données dont plusieurs membres portent le même nom, comme illustré dans l'exemple de code suivant.</span><span class="sxs-lookup"><span data-stu-id="7e3e2-122">The JSON serializer throws a serialization exception for data contracts that have multiple members with the same name, as shown in the following sample code.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="7e3e2-123">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="7e3e2-123">See also</span></span>

- [<span data-ttu-id="7e3e2-124">Sérialisation JSON autonome</span><span class="sxs-lookup"><span data-stu-id="7e3e2-124">Stand-alone JSON serialization</span></span>](stand-alone-json-serialization.md)
- [<span data-ttu-id="7e3e2-125">Prise en charge de JSON et d’autres données de formats de transfert</span><span class="sxs-lookup"><span data-stu-id="7e3e2-125">Support for JSON and other data transfer formats</span></span>](support-for-json-and-other-data-transfer-formats.md)
