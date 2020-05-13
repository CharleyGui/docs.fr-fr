---
title: 'Comment : substituer la sérialisation XML encodée selon le protocole SOAP'
description: En savoir plus sur la substitution de la sérialisation XML d’objets en tant que messages SOAP, qui est similaire au processus de substitution de la sérialisation XML standard.
ms.date: 03/30/2017
helpviewer_keywords:
- overriding XML serialization
- SOAP, overriding encoded XML serialization
ms.assetid: d0791df8-04e3-46b4-a6be-fe0ed09267e8
ms.openlocfilehash: 76e8009b83182d8517ff403f4f1e67bf0e7846b8
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/13/2020
ms.locfileid: "83375830"
---
# <a name="how-to-override-encoded-soap-xml-serialization"></a>Comment : substituer la sérialisation XML encodée selon le protocole SOAP

Le processus permettant de substituer la sérialisation XML d'objets en tant que messages SOAP est identique au processus permettant de substituer la sérialisation XML standard. Pour plus d’informations sur la substitution de la sérialisation XML standard, consultez [Guide pratique pour spécifier un nom d’élément différent pour un flux XML](../../../docs/standard/serialization/how-to-specify-an-alternate-element-name-for-an-xml-stream.md).

## <a name="to-override-serialization-of-objects-as-soap-messages"></a>Pour substituer la sérialisation d'objets en tant que messages SOAP

1. Créez une instance de la classe <xref:System.Xml.Serialization.SoapAttributeOverrides>.

2. Créez un `SoapAttributes` pour chaque membre de classe sérialisé.

3. Créez une instance d'un ou plusieurs des attributs qui affectent la sérialisation XML, si nécessaire, pour le membre sérialisé. Pour plus d'informations, consultez « Attributs qui contrôlent la sérialisation codée selon le protocole SOAP ».

4. Définissez la propriété appropriée de `SoapAttributes` avec l’attribut créé à l’étape 3.

5. Ajout de `SoapAttributes` à `SoapAttributeOverrides`.

6. Créez un `XmlTypeMapping` à l'aide de `SoapAttributeOverrides`. Utilisez la méthode `SoapReflectionImporter.ImportTypeMapping`.

7. Créez un `XmlSerializer` à l'aide de `XmlTypeMapping`.

8. Sérialisez ou désérialisez l'objet.

## <a name="example"></a>Exemple

L'exemple de code suivant sérialise un fichier de deux manières différentes : premièrement, sans substituer le comportement de la classe `XmlSerializer` et deuxièmement, en le substituant. L'exemple contient une classe nommée `Group` disposant de plusieurs membres. Différents attributs, tels que `SoapElementAttribute`, ont été appliqués aux membres de classe. Lorsque la classe est sérialisée avec la méthode `SerializeOriginal`, les attributs contrôlent le contenu des messages SOAP. Lorsque la méthode `SerializeOverride` est appelée, le comportement de `XmlSerializer` est substitué en créant différents attributs et en affectant ces attributs aux propriétés d'un `SoapAttributes` (si nécessaire).

```csharp
using System;
using System.IO;
using System.Xml;
using System.Xml.Serialization;
using System.Xml.Schema;

public class Group
{
    [SoapAttribute (Namespace = "http://www.cpandl.com")]
    public string GroupName;

    [SoapAttribute(DataType = "base64Binary")]
    public Byte [] GroupNumber;

    [SoapAttribute(DataType = "date", AttributeName = "CreationDate")]
    public DateTime Today;
    [SoapElement(DataType = "nonNegativeInteger", ElementName = "PosInt")]
    public string PositiveInt;
    // This is ignored when serialized unless it is overridden.
    [SoapIgnore]
    public bool IgnoreThis;

    public GroupType Grouptype;

    [SoapInclude(typeof(Car))]
    public Vehicle myCar(string licNumber)
    {
        Vehicle v;
        if(licNumber == "")
            {
                v = new Car();
            v.licenseNumber = "!!!!!!";
        }
        else
        {
            v = new Car();
            v.licenseNumber = licNumber;
        }
        return v;
    }
}

public abstract class Vehicle
{
    public string licenseNumber;
    public DateTime makeDate;
}

public class Car: Vehicle
{
}

public enum GroupType
{
    // These enums can be overridden.
    small,
    large
}

public class Run
{
    public static void Main()
    {
        Run test = new Run();
        test.SerializeOriginal("SoapOriginal.xml");
        test.SerializeOverride("SoapOverrides.xml");
        test.DeserializeOriginal("SoapOriginal.xml");
        test.DeserializeOverride("SoapOverrides.xml");

    }
    public void SerializeOriginal(string filename)
    {
        // Creates an instance of the XmlSerializer class.
        XmlTypeMapping myMapping =
        (new SoapReflectionImporter().ImportTypeMapping(
        typeof(Group)));
        XmlSerializer mySerializer =
        new XmlSerializer(myMapping);

        // Writing the file requires a TextWriter.
        TextWriter writer = new StreamWriter(filename);

        // Creates an instance of the class that will be serialized.
        Group myGroup = new Group();

        // Sets the object properties.
        myGroup.GroupName = ".NET";

        Byte [] hexByte = new Byte[2]{Convert.ToByte(100),
        Convert.ToByte(50)};
        myGroup.GroupNumber = hexByte;

        DateTime myDate = new DateTime(2002,5,2);
        myGroup.Today = myDate;

        myGroup.PositiveInt= "10000";
        myGroup.IgnoreThis=true;
        myGroup.Grouptype= GroupType.small;
        Car thisCar =(Car)  myGroup.myCar("1234566");

        // Prints the license number just to prove the car was created.
        Console.WriteLine("License#: " + thisCar.licenseNumber + "\n");

        // Serializes the class and closes the TextWriter.
        mySerializer.Serialize(writer, myGroup);
        writer.Close();
    }

    public void SerializeOverride(string filename)
    {
        // Creates an instance of the XmlSerializer class
        // that overrides the serialization.
        XmlSerializer overRideSerializer = CreateOverrideSerializer();

        // Writing the file requires a TextWriter.
        TextWriter writer = new StreamWriter(filename);

        // Creates an instance of the class that will be serialized.
        Group myGroup = new Group();

        // Sets the object properties.
        myGroup.GroupName = ".NET";

        Byte [] hexByte = new Byte[2]{Convert.ToByte(100),
        Convert.ToByte(50)};
        myGroup.GroupNumber = hexByte;

        DateTime myDate = new DateTime(2002,5,2);
        myGroup.Today = myDate;

        myGroup.PositiveInt= "10000";
        myGroup.IgnoreThis=true;
        myGroup.Grouptype= GroupType.small;
        Car thisCar =(Car)  myGroup.myCar("1234566");

        // Serializes the class and closes the TextWriter.
        overRideSerializer.Serialize(writer, myGroup);
         writer.Close();
    }

    public void DeserializeOriginal(string filename)
    {
        // Creates an instance of the XmlSerializer class.
        XmlTypeMapping myMapping =
        (new SoapReflectionImporter().ImportTypeMapping(
        typeof(Group)));
        XmlSerializer mySerializer =
        new XmlSerializer(myMapping);

        TextReader reader = new StreamReader(filename);

        // Deserializes and casts the object.
        Group myGroup;
        myGroup = (Group) mySerializer.Deserialize(reader);

        Console.WriteLine(myGroup.GroupName);
        Console.WriteLine(myGroup.GroupNumber[0]);
        Console.WriteLine(myGroup.GroupNumber[1]);
        Console.WriteLine(myGroup.Today);
        Console.WriteLine(myGroup.PositiveInt);
        Console.WriteLine(myGroup.IgnoreThis);
        Console.WriteLine();
    }

    public void DeserializeOverride(string filename)
    {
        // Creates an instance of the XmlSerializer class.
        XmlSerializer overRideSerializer = CreateOverrideSerializer();
        // Reading the file requires a TextReader.
        TextReader reader = new StreamReader(filename);

        // Deserializes and casts the object.
        Group myGroup;
        myGroup = (Group) overRideSerializer.Deserialize(reader);

        Console.WriteLine(myGroup.GroupName);
        Console.WriteLine(myGroup.GroupNumber[0]);
        Console.WriteLine(myGroup.GroupNumber[1]);
        Console.WriteLine(myGroup.Today);
        Console.WriteLine(myGroup.PositiveInt);
        Console.WriteLine(myGroup.IgnoreThis);
    }

    private XmlSerializer CreateOverrideSerializer()
    {
        SoapAttributeOverrides mySoapAttributeOverrides =
        new SoapAttributeOverrides();
        SoapAttributes soapAtts = new SoapAttributes();

        SoapElementAttribute mySoapElement = new SoapElementAttribute();
        mySoapElement.ElementName = "xxxx";
        soapAtts.SoapElement = mySoapElement;
        mySoapAttributeOverrides.Add(typeof(Group), "PositiveInt",
        soapAtts);

        // Overrides the IgnoreThis property.
        SoapIgnoreAttribute myIgnore = new SoapIgnoreAttribute();
        soapAtts = new SoapAttributes();
        soapAtts.SoapIgnore = false;
        mySoapAttributeOverrides.Add(typeof(Group), "IgnoreThis",
        soapAtts);

        // Overrides the GroupType enumeration.
        soapAtts = new SoapAttributes();
        SoapEnumAttribute xSoapEnum = new SoapEnumAttribute();
        xSoapEnum.Name = "Over1000";
        soapAtts.SoapEnum = xSoapEnum;

        // Adds the SoapAttributes to the
        // mySoapAttributeOverrides.
        mySoapAttributeOverrides.Add(typeof(GroupType), "large",
        soapAtts);

        // Creates a second enumeration and adds it.
        soapAtts = new SoapAttributes();
        xSoapEnum = new SoapEnumAttribute();
        xSoapEnum.Name = "ZeroTo1000";
        soapAtts.SoapEnum = xSoapEnum;
        mySoapAttributeOverrides.Add(typeof(GroupType), "small",
        soapAtts);

        // Overrides the Group type.
        soapAtts = new SoapAttributes();
        SoapTypeAttribute soapType = new SoapTypeAttribute();
        soapType.TypeName = "Team";
        soapAtts.SoapType = soapType;
        mySoapAttributeOverrides.Add(typeof(Group),soapAtts);

        // Creates an XmlTypeMapping that is used to create an instance
        // of the XmlSerializer class. Then returns the XmlSerializer.
        XmlTypeMapping myMapping = (new SoapReflectionImporter(
        mySoapAttributeOverrides)).ImportTypeMapping(typeof(Group));

        XmlSerializer ser = new XmlSerializer(myMapping);
        return ser;
    }
}
```

## <a name="see-also"></a>Voir aussi

- [Sérialisation XML et SOAP](../../../docs/standard/serialization/xml-and-soap-serialization.md)
- [Attributs qui contrôlent la sérialisation encodée selon le protocole SOAP](../../../docs/standard/serialization/attributes-that-control-encoded-soap-serialization.md)
- [Sérialisation XML avec les services Web XML](../../../docs/standard/serialization/xml-serialization-with-xml-web-services.md)
- [Guide pratique pour sérialiser un objet](../../../docs/standard/serialization/how-to-serialize-an-object.md)
- [Guide pratique pour désérialiser un objet](../../../docs/standard/serialization/how-to-deserialize-an-object.md)
- [Comment : sérialiser un objet en tant que flux XML encodé selon le protocole SOAP](../../../docs/standard/serialization/how-to-serialize-an-object-as-a-soap-encoded-xml-stream.md)
