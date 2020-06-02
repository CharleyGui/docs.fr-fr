---
title: Contrôle de la sérialisation XML à l'aide d'attributs
description: Les attributs peuvent être utilisés pour contrôler la sérialisation XML d'un objet ou pour créer un flux de données XML différent à partir du même ensemble de classes.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- classes, serializing
- XML serialization, examples
- derived classes, serializing
- arrays, serializing
- XML serialization, attributes
- preventing serialization
- attributes [.NET Framework], XML serialization
- serialization, examples
- serialization, attributes
ms.assetid: 47d4c39d-30e1-4c7b-8a2e-301325390647
ms.openlocfilehash: 79c5541b4c384e91fbec8c8f1b2130887e79a252
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84289679"
---
# <a name="controlling-xml-serialization-using-attributes"></a>Contrôle de la sérialisation XML à l'aide d'attributs

Les attributs peuvent être utilisés pour contrôler la sérialisation XML d'un objet ou pour créer un flux de données XML différent à partir du même ensemble de classes. Pour plus d’informations sur la création d’un flux de données XML différent, consultez [Guide pratique pour spécifier un nom d’élément différent pour un flux XML](how-to-specify-an-alternate-element-name-for-an-xml-stream.md).

> [!NOTE]
> Si le code XML généré doit se conformer à la section 5 du document World Wide Web Consortium (W3C) intitulé [simple Object Access Protocol (SOAP) 1,1](https://www.w3.org/TR/2000/NOTE-SOAP-20000508/), utilisez les attributs listés dans [attributs qui contrôlent la sérialisation encodée](attributes-that-control-encoded-soap-serialization.md)selon le protocole SOAP.

Par défaut, un nom d'élément XML est déterminé par le nom de la classe ou du membre. Dans une classe simple nommée `Book` , un champ nommé `ISBN` génère une balise d’élément XML \<ISBN> , comme illustré dans l’exemple suivant.

```vb
Public Class Book
    Public ISBN As String
End Class
' When an instance of the Book class is serialized, it might
' produce this XML:
' <ISBN>1234567890</ISBN>.
```

```csharp
public class Book
{
    public string ISBN;
}
// When an instance of the Book class is serialized, it might
// produce this XML:
// <ISBN>1234567890</ISBN>.
```

Ce comportement par défaut peut être modifié si vous souhaitez donner un nouveau nom à l'élément. Le code suivant affiche la manière dont un attribut active cette option en définissant la propriété <xref:System.Xml.Serialization.XmlElementAttribute.ElementName%2A> d'un <xref:System.Xml.Serialization.XmlElementAttribute>.

```vb
Public Class TaxRates
   < XmlElement(ElementName = "TaxRate")> _
    Public ReturnTaxRate As Decimal
End Class
```

```csharp
public class TaxRates {
    [XmlElement(ElementName = "TaxRate")]
    public decimal ReturnTaxRate;
}
```

Pour plus d’informations sur les attributs, consultez [Attributs](../attributes/index.md). Pour obtenir une liste complète des attributs qui contrôlent la sérialisation XML, consultez [Attributs qui contrôlent la sérialisation XML](attributes-that-control-xml-serialization.md).

## <a name="controlling-array-serialization"></a>Contrôle de la sérialisation de tableau

Les attributs <xref:System.Xml.Serialization.XmlArrayAttribute> et <xref:System.Xml.Serialization.XmlArrayItemAttribute> sont conçus pour contrôler la sérialisation de tableaux. À l'aide de ces attributs, vous pouvez contrôler le type de données de nom d'élément, d'espace de noms et de schéma XML (XSD) (comme défini dans le document du World Wide Web Consortium [www.w3.org] intitulé « XML Schema Part 2: Datatypes »). Vous pouvez également spécifier les types qui peuvent être inclus dans un tableau.

<xref:System.Xml.Serialization.XmlArrayAttribute> détermine les propriétés de l'élément XML englobant obtenu lorsqu'un tableau est sérialisé. Par exemple, la sérialisation du tableau suivant génère par défaut un élément XML nommé `Employees`. L'élément `Employees` contient une série d'éléments nommée d'après le type de tableau `Employee`.

```vb
Public Class Group
    Public Employees() As Employee
End Class
Public Class Employee
    Public Name As String
End Class
```

```csharp
public class Group {
    public Employee[] Employees;
}
public class Employee {
    public string Name;
}
```

Une instance sérialisée peut se présenter comme suit.

```xml
<Group>
<Employees>
    <Employee>
        <Name>Haley</Name>
    </Employee>
</Employees>
</Group>
```

En appliquant un <xref:System.Xml.Serialization.XmlArrayAttribute>, vous pouvez modifier le nom de l'élément XML, comme suit.

```vb
Public Class Group
    <XmlArray("TeamMembers")> _
    Public Employees() As Employee
End Class
```

```csharp
public class Group {
    [XmlArray("TeamMembers")]
    public Employee[] Employees;
}
```

Le code XML obtenu peut se présenter comme suit.

```xml
<Group>
<TeamMembers>
    <Employee>
        <Name>Haley</Name>
    </Employee>
</TeamMembers>
</Group>
```

En revanche, <xref:System.Xml.Serialization.XmlArrayItemAttribute> contrôle la manière dont les éléments contenus dans le tableau sont sérialisés. Notez que l'attribut est appliqué au champ retournant le tableau.

```vb
Public Class Group
    <XmlArrayItem("MemberName")> _
    Public Employee() As Employees
End Class
```

```csharp
public class Group {
    [XmlArrayItem("MemberName")]
    public Employee[] Employees;
}
```

Le code XML obtenu peut se présenter comme suit.

```xml
<Group>
<Employees>
    <MemberName>Haley</MemberName>
</Employees>
</Group>
```

## <a name="serializing-derived-classes"></a>Sérialisation de classes dérivées

<xref:System.Xml.Serialization.XmlArrayItemAttribute> permet également de sérialiser des classes dérivées. Par exemple, une autre classe nommée `Manager`, dérivée de `Employee`, peut être ajoutée à l'exemple précédent. Si vous n'appliquez pas <xref:System.Xml.Serialization.XmlArrayItemAttribute>, le code ne pourra pas s'exécuter car le type de classe dérivée ne sera pas reconnu. Pour résoudre ce problème, appliquez l'attribut deux fois, en définissant à chaque fois la propriété <xref:System.Xml.Serialization.XmlArrayItemAttribute.Type%2A> pour chaque type acceptable (type de base et dérivé).

```vb
Public Class Group
    <XmlArrayItem(Type:=GetType(Employee)), _
    XmlArrayItem(Type:=GetType(Manager))> _
    Public Employees() As Employee
End Class
Public Class Employee
    Public Name As String
End Class
Public Class Manager
Inherits Employee
    Public Level As Integer
End Class
```

```csharp
public class Group {
    [XmlArrayItem(Type = typeof(Employee)),
    XmlArrayItem(Type = typeof(Manager))]
    public Employee[] Employees;
}
public class Employee {
    public string Name;
}
public class Manager:Employee {
    public int Level;
}
```

Une instance sérialisée peut se présenter comme suit.

```xml
<Group>
<Employees>
    <Employee>
        <Name>Haley</Name>
    </Employee>
    <Employee xsi:type = "Manager">
        <Name>Ann</Name>
        <Level>3</Level>
    </Employee>
</Employees>
</Group>
```

## <a name="serializing-an-array-as-a-sequence-of-elements"></a>Sérialisation d'un tableau sous forme de séquence d'éléments

Vous pouvez également sérialiser un tableau sous forme de séquence en deux dimensions d'éléments XML en appliquant <xref:System.Xml.Serialization.XmlElementAttribute> au champ retournant le tableau suivant.

```vb
Public Class Group
    <XmlElement> _
    Public Employees() As Employee
End Class
```

```csharp
public class Group {
    [XmlElement]
    public Employee[] Employees;
}
```

Une instance sérialisée peut se présenter comme suit.

```xml
<Group>
<Employees>
    <Name>Haley</Name>
</Employees>
<Employees>
    <Name>Noriko</Name>
</Employees>
<Employees>
    <Name>Marco</Name>
</Employees>
</Group>
```

Pour différencier les deux flux de données XML, vous pouvez également utiliser l'outil XML Schema Definition pour générer des fichiers de document de schéma XML (XSD) à partir du code compilé. (Pour plus d’informations sur l’utilisation de l’outil, consultez [l’outil XML Schema Definition et SÉRIALISATION XML](the-xml-schema-definition-tool-and-xml-serialization.md).) Quand aucun attribut n’est appliqué au champ, le schéma décrit l’élément de la manière suivante.

```xml
<xs:element minOccurs="0" maxOccurs ="1" name="Employees" type="ArrayOfEmployee" />
```

Lorsque <xref:System.Xml.Serialization.XmlElementAttribute> est appliqué au champ, le schéma obtenu décrit l'élément comme suit.

```xml
<xs:element minOccurs="0" maxOccurs="unbounded" name="Employees" type="Employee" />
```

## <a name="serializing-an-arraylist"></a>Sérialisation d'un ArrayList

La classe <xref:System.Collections.ArrayList> peut contenir une collection d'objets divers. Par conséquent, vous pouvez utiliser un <xref:System.Collections.ArrayList> plus souvent qu'un tableau. Au lieu de créer un champ qui retourne un tableau d'objets typés, vous pouvez cependant créer un champ qui retourne un <xref:System.Collections.ArrayList> unique. Toutefois, comme avec les tableaux, vous devez indiquer à <xref:System.Xml.Serialization.XmlSerializer> les types d'objets que contient l'<xref:System.Collections.ArrayList>. Pour ce faire, assignez plusieurs instances de <xref:System.Xml.Serialization.XmlElementAttribute> à ce champ, comme illustré dans l'exemple suivant.

```vb
Public Class Group
    <XmlElement(Type:=GetType(Employee)), _
    XmlElement(Type:=GetType(Manager))> _
    Public Info As ArrayList
End Class
```

```csharp
public class Group {
    [XmlElement(Type = typeof(Employee)),
    XmlElement(Type = typeof(Manager))]
    public ArrayList Info;
}
```

## <a name="controlling-serialization-of-classes-using-xmlrootattribute-and-xmltypeattribute"></a>Contrôle de la sérialisation de classes à l'aide de XmlRootAttribute et XmlTypeAttribute

Il est possible d'appliquer deux attributs à une seule et même classe : <xref:System.Xml.Serialization.XmlRootAttribute> et <xref:System.Xml.Serialization.XmlTypeAttribute>. Ces attributs sont très semblables. <xref:System.Xml.Serialization.XmlRootAttribute> peut être appliqué à une seule classe : celle qui, une fois sérialisée, représente l'élément ouvrant et fermant du document XML, c'est-à-dire l'élément racine. En revanche, <xref:System.Xml.Serialization.XmlTypeAttribute> peut être appliqué à n'importe quelle classe, y compris la classe racine.

Par exemple, la classe `Group` correspond à la classe racine dans les exemples précédents, et tous ses champs et propriétés publics deviennent les éléments XML recherchés dans le document XML. Par conséquent, il ne peut y avoir qu'une seule classe racine. En appliquant <xref:System.Xml.Serialization.XmlRootAttribute>, vous pouvez contrôler le flux de données XML généré par <xref:System.Xml.Serialization.XmlSerializer>. Par exemple, vous pouvez modifier le nom de l'élément et l'espace de noms.

<xref:System.Xml.Serialization.XmlTypeAttribute> vous permet de contrôler le schéma du code XML généré. Cette fonction est utile lorsque vous devez publier le schéma via un service Web XML. L'exemple suivant applique <xref:System.Xml.Serialization.XmlTypeAttribute> et <xref:System.Xml.Serialization.XmlRootAttribute> à la même classe.

```vb
<XmlRoot("NewGroupName"), _
XmlType("NewTypeName")> _
Public Class Group
    Public Employees() As Employee
End Class
```

```csharp
[XmlRoot("NewGroupName")]
[XmlType("NewTypeName")]
public class Group {
    public Employee[] Employees;
}
```

Si cette classe est compilée et que l'outil XML Schema Definition est utilisé pour générer son schéma, vous obtenez le code XML suivant qui décrit `Group`.

```xml
<xs:element name="NewGroupName" type="NewTypeName" />
```

En revanche, si vous deviez sérialiser une instance de la classe, vous obtiendriez uniquement `NewGroupName` dans le document XML.

```xml
<NewGroupName>
    . . .
</NewGroupName>
```

## <a name="preventing-serialization-with-the-xmlignoreattribute"></a>Empêcher la sérialisation avec XmlIgnoreAttribute

Dans certains cas, une propriété ou un champ public ne doit pas être sérialisé. Par exemple, un champ ou une propriété peut servir à contenir des métadonnées. Dans de tels cas, appliquez <xref:System.Xml.Serialization.XmlIgnoreAttribute> au champ ou à la propriété pour que <xref:System.Xml.Serialization.XmlSerializer> puisse l'ignorer.

## <a name="see-also"></a>Voir aussi

- [Attributs qui contrôlent la sérialisation XML](attributes-that-control-xml-serialization.md)
- [Attributs qui contrôlent la sérialisation encodée selon le protocole SOAP](attributes-that-control-encoded-soap-serialization.md)
- [Introduction à la sérialisation XML](introducing-xml-serialization.md)
- [Exemples de sérialisation XML](examples-of-xml-serialization.md)
- [Guide pratique pour spécifier un nom d’élément différent pour un flux XML](how-to-specify-an-alternate-element-name-for-an-xml-stream.md)
- [Guide pratique pour sérialiser un objet](how-to-serialize-an-object.md)
- [Guide pratique pour désérialiser un objet](how-to-deserialize-an-object.md)
