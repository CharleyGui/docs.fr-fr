---
title: Sérialisation de base
ms.date: 03/30/2017
helpviewer_keywords:
- binary serialization, basic serialization
- serialization, basic serialization
ms.assetid: d899d43c-335a-433e-a589-cd187192984f
dev_langs:
- CSharp
ms.openlocfilehash: a2dde9f795dfe31ff6ef821272a0d5e8d20e8b2f
ms.sourcegitcommit: 00aa62e2f469c2272a457b04e66b4cc3c97a800b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/28/2020
ms.locfileid: "78159947"
---
# <a name="basic-serialization"></a>Sérialisation de base

[!INCLUDE [binary-serialization-warning](../../../includes/binary-serialization-warning.md)]

La façon la plus simple de rendre une classe sérialisable est de la marquer avec l’attribut <xref:System.SerializableAttribute> comme suit.  
  
```csharp  
[Serializable]  
public class MyObject {  
  public int n1 = 0;  
  public int n2 = 0;  
  public String str = null;  
}  
```  
  
L’exemple de code suivant illustre comment une instance de cette classe peut être sérialisée dans un fichier.  
  
```csharp  
MyObject obj = new MyObject();  
obj.n1 = 1;  
obj.n2 = 24;  
obj.str = "Some String";  
IFormatter formatter = new BinaryFormatter();  
Stream stream = new FileStream("MyFile.bin", FileMode.Create, FileAccess.Write, FileShare.None);  
formatter.Serialize(stream, obj);  
stream.Close();  
```  
  
Cet exemple utilise un formateur binaire pour effectuer la sérialisation. Il vous suffit de créer une instance du flux de données et du formateur que vous envisagez d’utiliser, puis d’appeler la méthode **Serialize** sur le formateur. Le flux de données et l'objet à sérialiser sont fournis comme paramètres de cet appel. Bien que cela n'apparaisse pas explicitement dans cet exemple, toutes les variables membres d'une classe seront sérialisées, même celles marquées comme privées. Dans ce cadre, la sérialisation binaire diffère de la classe <xref:System.Xml.Serialization.XmlSerializer>, qui sérialise uniquement des champs publics. Pour plus d’informations sur l’exclusion de variables membres de la sérialisation binaire, consultez [Sérialisation sélective](selective-serialization.md).  
  
La restauration de l'objet à son état précédent est très facile. En premier lieu, créez un flux servant à la lecture et un <xref:System.Runtime.Serialization.Formatter>, puis demandez au formateur de désérialiser l’objet. L'exemple de code suivant illustre cette procédure.  
  
```csharp  
IFormatter formatter = new BinaryFormatter();  
Stream stream = new FileStream("MyFile.bin", FileMode.Open, FileAccess.Read, FileShare.Read);  
MyObject obj = (MyObject) formatter.Deserialize(stream);  
stream.Close();  
  
// Here's the proof.  
Console.WriteLine("n1: {0}", obj.n1);  
Console.WriteLine("n2: {0}", obj.n2);  
Console.WriteLine("str: {0}", obj.str);  
```  
  
Le <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> utilisé ci-dessus est très efficace et génère un flux d’octets compact. Ce formateur permet aussi bien de sérialiser que de désérialiser des objets, ce qui en fait l'outil idéal pour sérialiser des objets qui seront désérialisés sur le .NET Framework. Il est important de noter que les constructeurs ne sont pas appelés lorsqu'un objet est désérialisé. Pour des raisons de performances, la désérialisation repose sur cette contrainte. Toutefois, cela enfreint les termes de certains contrats habituels que l'exécution passe avec le writer d'objets et les développeurs doivent s'assurer qu'ils comprennent les ramifications lorsqu'ils marquent un objet comme sérialisable.  
  
Si la portabilité est une exigence, utilisez plutôt le <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter>. Remplacez simplement le **BinaryFormatter** dans le code ci-dessus par **SoapFormatter** et appelez **Serialize** et **Deserialize** comme précédemment. Ce formateur génère le résultat suivant pour l'exemple utilisé ci-dessus.  
  
```xml  
<SOAP-ENV:Envelope  
  xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"  
  xmlns:xsd="http://www.w3.org/2001/XMLSchema"
  xmlns:SOAP-ENC="http://schemas.xmlsoap.org/soap/encoding/"  
  xmlns:SOAP-ENV="http://schemas.xmlsoap.org/soap/envelope/"  
  SOAP-ENV:encodingStyle=  
  "http://schemas.microsoft.com/soap/encoding/clr/1.0"  
  "http://schemas.xmlsoap.org/soap/encoding/"  
  xmlns:a1="http://schemas.microsoft.com/clr/assem/ToFile">  
  
  <SOAP-ENV:Body>  
    <a1:MyObject id="ref-1">  
      <n1>1</n1>  
      <n2>24</n2>  
      <str id="ref-3">Some String</str>  
    </a1:MyObject>  
  </SOAP-ENV:Body>  
</SOAP-ENV:Envelope>  
```  
  
Il est important de noter que l’attribut [Serializable](xref:System.SerializableAttribute) ne peut pas être hérité. Si vous dérivez une nouvelle classe à partir de `MyObject`, elle doit également être marquée avec l'attribut. Sinon, elle ne peut pas être sérialisée. Par exemple, quand vous tentez de sérialiser une instance de la classe ci-dessous, vous obtenez un <xref:System.Runtime.Serialization.SerializationException> vous informant que le type `MyStuff` n’est pas marqué comme sérialisable.  
  
```csharp  
public class MyStuff : MyObject
{  
  public int n3;  
}  
```  
  
 L’utilisation de l’attribut [Serializable](xref:System.SerializableAttribute) est pratique, mais comporte des limites comme illustré précédemment. Reportez-vous aux [Indications concernant la sérialisation](serialization-guidelines.md) pour savoir à quel moment il convient de marquer une classe en vue de la sérialisation. La sérialisation ne peut pas être ajoutée à une classe une fois que cette dernière a été compilée.  
  
## <a name="see-also"></a>Voir aussi

- [Sérialisation binaire](binary-serialization.md)
- [Sérialisation XML et SOAP](xml-and-soap-serialization.md)
