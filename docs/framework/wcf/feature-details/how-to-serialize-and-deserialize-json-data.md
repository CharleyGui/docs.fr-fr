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
# <a name="how-to-serialize-and-deserialize-json-data"></a>Procédure : Sérialiser et désérialiser des données JSON
JSON (JavaScript Object Notation) est un format d'encodage de données efficace qui permet l'échange rapide de petites quantités de données entre les navigateurs clients et les services Web compatibles AJAX.  
  
 Cet article montre comment sérialiser des objets de type .NET dans des données encodées en JSON et ensuite désérialiser les données au format JSON en instances des types .NET. Cet exemple utilise un contrat de données pour illustrer la sérialisation et désérialisation de défini par l’utilisateur `Person` type et utilise <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>.  
  
 En règle générale, la désérialisation et la sérialisation JSON sont gérées automatiquement par Windows Communication Foundation (WCF) lorsque vous utilisez des types de contrat de données dans des opérations de service exposées sur des points de terminaison compatibles AJAX. Toutefois, dans certains cas, vous devrez peut-être travailler avec des données JSON directement.   
  
> [!NOTE]
>  Si une erreur se produit pendant la sérialisation d’une réponse sortante sur le serveur ou pour une raison quelconque, elle ne peut pas obtenir retournée au client sous forme d’erreur.  
  
 Cet article est basé sur le [sérialisation JSON](../samples/json-serialization.md) exemple.  
  
## <a name="to-define-the-data-contract-for-a-person-type"></a>Pour définir le contrat de données pour un type de personne 
  
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
  
2. Sérialiser le `Person` objet dans un flux de mémoire à l’aide de la <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>.  
  
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
>  Le sérialiseur JSON lève une exception de sérialisation pour les contrats de données dont plusieurs membres portent le même nom, comme illustré dans l'exemple de code suivant.  
  
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
- [Prise en charge de JSON et d’autres données de formats de transfert](support-for-json-and-other-data-transfer-formats.md)
