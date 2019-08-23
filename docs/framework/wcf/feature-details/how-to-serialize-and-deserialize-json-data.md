---
title: 'Procédure : sérialiser et désérialiser des données JSON'
ms.date: 03/25/2019
ms.assetid: 88abc1fb-8196-4ee3-a23b-c6934144d1dd
ms.openlocfilehash: 0bebdbb3d74d58db093c4ec1e0e88138c7080335
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69947896"
---
# <a name="how-to-serialize-and-deserialize-json-data"></a>Procédure : Sérialiser et désérialiser des données JSON
JSON (JavaScript Object Notation) est un format d'encodage de données efficace qui permet l'échange rapide de petites quantités de données entre les navigateurs clients et les services Web compatibles AJAX.  
  
 Cet article montre comment sérialiser des objets de type .NET dans des données encodées en JSON, puis comment désérialiser des données au format JSON en instances de types .NET. Cet exemple utilise un contrat de données pour illustrer la sérialisation et la désérialisation d’un type `Person` défini par l' <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>utilisateur et utilise.  
  
 Normalement, la sérialisation et la désérialisation JSON sont gérées automatiquement par Windows Communication Foundation (WCF) quand vous utilisez des types de contrat de données dans des opérations de service exposées sur des points de terminaison compatibles AJAX. Toutefois, dans certains cas, vous devrez peut-être utiliser des données JSON directement.   
  
> [!NOTE]
> Si une erreur se produit pendant la sérialisation d’une réponse sortante sur le serveur ou pour une autre raison, il se peut qu’elle ne soit pas retournée au client en tant qu’erreur.  
  
 Cet article est basé sur l’exemple de [sérialisation JSON](../samples/json-serialization.md) .  
  
## <a name="to-define-the-data-contract-for-a-person-type"></a>Pour définir le contrat de données pour un type Person 
  
1. Définissez le contrat de données pour `Person` en joignant <xref:System.Runtime.Serialization.DataContractAttribute> à la classe et l'attribut <xref:System.Runtime.Serialization.DataMemberAttribute> aux membres que vous souhaitez sérialiser. Pour plus d’informations sur les contrats de données, consultez [conception de contrats de service](../designing-service-contracts.md).  
  
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
  
## <a name="to-serialize-an-instance-of-type-person-to-json"></a>Pour sérialiser une instance de type Person à JSON  
  
1. Créez une instance du type `Person`.  
  
    ```csharp  
    var p = new Person();  
    p.name = "John";  
    p.age = 42;  
    ```  
  
2. Sérialisez l' `Person` objet dans un flux de mémoire à <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>l’aide de.  
  
    ```csharp  
    var stream1 = new MemoryStream();  
    var ser = new DataContractJsonSerializer(typeof(Person));  
    ```  
  
3. Utilisez la méthode <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.WriteObject%2A> pour écrire les données JSON dans le flux.  
  
    ```csharp  
    ser.WriteObject(stream1, p);  
    ```  
  
4. Affichez la sortie JSON.  
  
    ```csharp  
    stream1.Position = 0;  
    var sr = new StreamReader(stream1);  
    Console.Write("JSON form of Person object: ");  
    Console.WriteLine(sr.ReadToEnd());  
    ```  
  
## <a name="to-deserialize-an-instance-of-type-person-from-json"></a>Pour désérialiser une instance de type Person depuis JSON  
  
1. Désérialisez les données encodées JSON dans une nouvelle instance de `Person` à l'aide de la méthode <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.ReadObject%2A> de <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>.  
  
    ```csharp  
    stream1.Position = 0;  
    var p2 = (Person)ser.ReadObject(stream1);  
    ```  
  
2. Affichez les résultats.  
  
    ```csharp  
    Console.WriteLine($"Deserialized back, got name={p2.name}, age={p2.age}");  
    ```  
  
## <a name="example"></a>Exemples  
  
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
> Le sérialiseur JSON lève une exception de sérialisation pour les contrats de données dont plusieurs membres portent le même nom, comme illustré dans l'exemple de code suivant.  
  
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
  
## <a name="see-also"></a>Voir aussi

- [Sérialisation JSON autonome](stand-alone-json-serialization.md)
- [Prise en charge de JSON et d’autres formats de transfert de données](support-for-json-and-other-data-transfer-formats.md)
