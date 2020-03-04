---
title: Contrôle de la sérialisation XML à l'aide d'attributs
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
ms.openlocfilehash: d4e30984a232b17d1f40e300655c519ec1a6e191
ms.sourcegitcommit: 00aa62e2f469c2272a457b04e66b4cc3c97a800b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/28/2020
ms.locfileid: "78159908"
---
# <a name="controlling-xml-serialization-using-attributes"></a><span data-ttu-id="7decb-102">Contrôle de la sérialisation XML à l'aide d'attributs</span><span class="sxs-lookup"><span data-stu-id="7decb-102">Controlling XML Serialization Using Attributes</span></span>

<span data-ttu-id="7decb-103">Les attributs peuvent être utilisés pour contrôler la sérialisation XML d'un objet ou pour créer un flux de données XML différent à partir du même ensemble de classes.</span><span class="sxs-lookup"><span data-stu-id="7decb-103">Attributes can be used to control the XML serialization of an object or to create an alternate XML stream from the same set of classes.</span></span> <span data-ttu-id="7decb-104">Pour plus d’informations sur la création d’un flux de données XML différent, consultez [Guide pratique pour spécifier un nom d’élément différent pour un flux XML](how-to-specify-an-alternate-element-name-for-an-xml-stream.md).</span><span class="sxs-lookup"><span data-stu-id="7decb-104">For more details about creating an alternate XML stream, see [How to: Specify an Alternate Element Name for an XML Stream](how-to-specify-an-alternate-element-name-for-an-xml-stream.md).</span></span>

> [!NOTE]
> <span data-ttu-id="7decb-105">Si le code XML généré doit se conformer à la section 5 du document World Wide Web Consortium (W3C) intitulé [simple Object Access Protocol (SOAP) 1,1](https://www.w3.org/TR/2000/NOTE-SOAP-20000508/), utilisez les attributs listés dans [attributs qui contrôlent la sérialisation encodée](attributes-that-control-encoded-soap-serialization.md)selon le protocole SOAP.</span><span class="sxs-lookup"><span data-stu-id="7decb-105">If the XML generated must conform to section 5 of the World Wide Web Consortium (W3C) document titled [Simple Object Access Protocol (SOAP) 1.1](https://www.w3.org/TR/2000/NOTE-SOAP-20000508/), use the attributes listed in [Attributes That Control Encoded SOAP Serialization](attributes-that-control-encoded-soap-serialization.md).</span></span>

<span data-ttu-id="7decb-106">Par défaut, un nom d'élément XML est déterminé par le nom de la classe ou du membre.</span><span class="sxs-lookup"><span data-stu-id="7decb-106">By default, an XML element name is determined by the class or member name.</span></span> <span data-ttu-id="7decb-107">Dans une classe simple nommée `Book`, un champ nommé `ISBN` génère une balise d’élément XML \<ISBN>, comme illustré dans l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="7decb-107">In a simple class named `Book`, a field named `ISBN` will produce an XML element tag \<ISBN>, as shown in the following example.</span></span>

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

<span data-ttu-id="7decb-108">Ce comportement par défaut peut être modifié si vous souhaitez donner un nouveau nom à l'élément.</span><span class="sxs-lookup"><span data-stu-id="7decb-108">This default behavior can be changed if you want to give the element a new name.</span></span> <span data-ttu-id="7decb-109">Le code suivant affiche la manière dont un attribut active cette option en définissant la propriété <xref:System.Xml.Serialization.XmlElementAttribute.ElementName%2A> d'un <xref:System.Xml.Serialization.XmlElementAttribute>.</span><span class="sxs-lookup"><span data-stu-id="7decb-109">The following code shows how an attribute enables this by setting the <xref:System.Xml.Serialization.XmlElementAttribute.ElementName%2A> property of a <xref:System.Xml.Serialization.XmlElementAttribute>.</span></span>

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

<span data-ttu-id="7decb-110">Pour plus d’informations sur les attributs, consultez [Attributs](../../../docs/standard/attributes/index.md).</span><span class="sxs-lookup"><span data-stu-id="7decb-110">For more information about attributes, see [Attributes](../../../docs/standard/attributes/index.md).</span></span> <span data-ttu-id="7decb-111">Pour obtenir une liste complète des attributs qui contrôlent la sérialisation XML, consultez [Attributs qui contrôlent la sérialisation XML](attributes-that-control-xml-serialization.md).</span><span class="sxs-lookup"><span data-stu-id="7decb-111">For a list of attributes that control XML serialization, see [Attributes That Control XML Serialization](attributes-that-control-xml-serialization.md).</span></span>

## <a name="controlling-array-serialization"></a><span data-ttu-id="7decb-112">Contrôle de la sérialisation de tableau</span><span class="sxs-lookup"><span data-stu-id="7decb-112">Controlling Array Serialization</span></span>

<span data-ttu-id="7decb-113">Les attributs <xref:System.Xml.Serialization.XmlArrayAttribute> et <xref:System.Xml.Serialization.XmlArrayItemAttribute> sont conçus pour contrôler la sérialisation de tableaux.</span><span class="sxs-lookup"><span data-stu-id="7decb-113">The <xref:System.Xml.Serialization.XmlArrayAttribute> and the <xref:System.Xml.Serialization.XmlArrayItemAttribute> attributes are designed to control the serialization of arrays.</span></span> <span data-ttu-id="7decb-114">À l'aide de ces attributs, vous pouvez contrôler le type de données de nom d'élément, d'espace de noms et de schéma XML (XSD) (comme défini dans le document du World Wide Web Consortium [www.w3.org] intitulé « XML Schema Part 2: Datatypes »).</span><span class="sxs-lookup"><span data-stu-id="7decb-114">Using these attributes, you can control the element name, namespace, and XML Schema (XSD) data type (as defined in the World Wide Web Consortium [www.w3.org] document titled "XML Schema Part 2: Datatypes").</span></span> <span data-ttu-id="7decb-115">Vous pouvez également spécifier les types qui peuvent être inclus dans un tableau.</span><span class="sxs-lookup"><span data-stu-id="7decb-115">You can also specify the types that can be included in an array.</span></span>

<span data-ttu-id="7decb-116"><xref:System.Xml.Serialization.XmlArrayAttribute> détermine les propriétés de l'élément XML englobant obtenu lorsqu'un tableau est sérialisé.</span><span class="sxs-lookup"><span data-stu-id="7decb-116">The <xref:System.Xml.Serialization.XmlArrayAttribute> will determine the properties of the enclosing XML element that results when an array is serialized.</span></span> <span data-ttu-id="7decb-117">Par exemple, la sérialisation du tableau suivant génère par défaut un élément XML nommé `Employees`.</span><span class="sxs-lookup"><span data-stu-id="7decb-117">For example, by default, serializing the array below will result in an XML element named `Employees`.</span></span> <span data-ttu-id="7decb-118">L'élément `Employees` contient une série d'éléments nommée d'après le type de tableau `Employee`.</span><span class="sxs-lookup"><span data-stu-id="7decb-118">The `Employees` element will contain a series of elements named after the array type `Employee`.</span></span>

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

<span data-ttu-id="7decb-119">Une instance sérialisée peut se présenter comme suit.</span><span class="sxs-lookup"><span data-stu-id="7decb-119">A serialized instance might resemble the following.</span></span>

```xml
<Group>
<Employees>
    <Employee>
        <Name>Haley</Name>
    </Employee>
</Employees>
</Group>
```

<span data-ttu-id="7decb-120">En appliquant un <xref:System.Xml.Serialization.XmlArrayAttribute>, vous pouvez modifier le nom de l'élément XML, comme suit.</span><span class="sxs-lookup"><span data-stu-id="7decb-120">By applying a <xref:System.Xml.Serialization.XmlArrayAttribute>, you can change the name of the XML element, as follows.</span></span>

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

<span data-ttu-id="7decb-121">Le code XML obtenu peut se présenter comme suit.</span><span class="sxs-lookup"><span data-stu-id="7decb-121">The resulting XML might resemble the following.</span></span>

```xml
<Group>
<TeamMembers>
    <Employee>
        <Name>Haley</Name>
    </Employee>
</TeamMembers>
</Group>
```

<span data-ttu-id="7decb-122">En revanche, <xref:System.Xml.Serialization.XmlArrayItemAttribute> contrôle la manière dont les éléments contenus dans le tableau sont sérialisés.</span><span class="sxs-lookup"><span data-stu-id="7decb-122">The <xref:System.Xml.Serialization.XmlArrayItemAttribute>, on the other hand, controls how the items contained in the array are serialized.</span></span> <span data-ttu-id="7decb-123">Notez que l'attribut est appliqué au champ retournant le tableau.</span><span class="sxs-lookup"><span data-stu-id="7decb-123">Note that the attribute is applied to the field returning the array.</span></span>

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

<span data-ttu-id="7decb-124">Le code XML obtenu peut se présenter comme suit.</span><span class="sxs-lookup"><span data-stu-id="7decb-124">The resulting XML might resemble the following.</span></span>

```xml
<Group>
<Employees>
    <MemberName>Haley</MemberName>
</Employees>
</Group>
```

## <a name="serializing-derived-classes"></a><span data-ttu-id="7decb-125">Sérialisation de classes dérivées</span><span class="sxs-lookup"><span data-stu-id="7decb-125">Serializing Derived Classes</span></span>

<span data-ttu-id="7decb-126"><xref:System.Xml.Serialization.XmlArrayItemAttribute> permet également de sérialiser des classes dérivées.</span><span class="sxs-lookup"><span data-stu-id="7decb-126">Another use of the <xref:System.Xml.Serialization.XmlArrayItemAttribute> is to allow the serialization of derived classes.</span></span> <span data-ttu-id="7decb-127">Par exemple, une autre classe nommée `Manager`, dérivée de `Employee`, peut être ajoutée à l'exemple précédent.</span><span class="sxs-lookup"><span data-stu-id="7decb-127">For example, another class named `Manager` that derives from `Employee` can be added to the previous example.</span></span> <span data-ttu-id="7decb-128">Si vous n'appliquez pas <xref:System.Xml.Serialization.XmlArrayItemAttribute>, le code ne pourra pas s'exécuter car le type de classe dérivée ne sera pas reconnu.</span><span class="sxs-lookup"><span data-stu-id="7decb-128">If you do not apply the <xref:System.Xml.Serialization.XmlArrayItemAttribute>, the code will fail at run time because the derived class type will not be recognized.</span></span> <span data-ttu-id="7decb-129">Pour résoudre ce problème, appliquez l'attribut deux fois, en définissant à chaque fois la propriété <xref:System.Xml.Serialization.XmlArrayItemAttribute.Type%2A> pour chaque type acceptable (type de base et dérivé).</span><span class="sxs-lookup"><span data-stu-id="7decb-129">To remedy this, apply the attribute twice, each time setting the <xref:System.Xml.Serialization.XmlArrayItemAttribute.Type%2A> property for each acceptable type (base and derived).</span></span>

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

<span data-ttu-id="7decb-130">Une instance sérialisée peut se présenter comme suit.</span><span class="sxs-lookup"><span data-stu-id="7decb-130">A serialized instance might resemble the following.</span></span>

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

## <a name="serializing-an-array-as-a-sequence-of-elements"></a><span data-ttu-id="7decb-131">Sérialisation d'un tableau sous forme de séquence d'éléments</span><span class="sxs-lookup"><span data-stu-id="7decb-131">Serializing an Array as a Sequence of Elements</span></span>

<span data-ttu-id="7decb-132">Vous pouvez également sérialiser un tableau sous forme de séquence en deux dimensions d'éléments XML en appliquant <xref:System.Xml.Serialization.XmlElementAttribute> au champ retournant le tableau suivant.</span><span class="sxs-lookup"><span data-stu-id="7decb-132">You can also serialize an array as a flat sequence of XML elements by applying a <xref:System.Xml.Serialization.XmlElementAttribute> to the field returning the array as follows.</span></span>

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

<span data-ttu-id="7decb-133">Une instance sérialisée peut se présenter comme suit.</span><span class="sxs-lookup"><span data-stu-id="7decb-133">A serialized instance might resemble the following.</span></span>

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

<span data-ttu-id="7decb-134">Pour différencier les deux flux de données XML, vous pouvez également utiliser l'outil XML Schema Definition pour générer des fichiers de document de schéma XML (XSD) à partir du code compilé.</span><span class="sxs-lookup"><span data-stu-id="7decb-134">Another way to differentiate the two XML streams is to use the XML Schema Definition tool to generate the XML Schema (XSD) document files from the compiled code.</span></span> <span data-ttu-id="7decb-135">(Pour plus d’informations sur l’utilisation de l’outil, consultez [l’outil XML Schema Definition et SÉRIALISATION XML](the-xml-schema-definition-tool-and-xml-serialization.md).) Quand aucun attribut n’est appliqué au champ, le schéma décrit l’élément de la manière suivante.</span><span class="sxs-lookup"><span data-stu-id="7decb-135">(For more details on using the tool, see [The XML Schema Definition Tool and XML Serialization](the-xml-schema-definition-tool-and-xml-serialization.md).) When no attribute is applied to the field, the schema describes the element in the following manner.</span></span>

```xml
<xs:element minOccurs="0" maxOccurs ="1" name="Employees" type="ArrayOfEmployee" />
```

<span data-ttu-id="7decb-136">Lorsque <xref:System.Xml.Serialization.XmlElementAttribute> est appliqué au champ, le schéma obtenu décrit l'élément comme suit.</span><span class="sxs-lookup"><span data-stu-id="7decb-136">When the <xref:System.Xml.Serialization.XmlElementAttribute> is applied to the field, the resulting schema describes the element as follows.</span></span>

```xml
<xs:element minOccurs="0" maxOccurs="unbounded" name="Employees" type="Employee" />
```

## <a name="serializing-an-arraylist"></a><span data-ttu-id="7decb-137">Sérialisation d'un ArrayList</span><span class="sxs-lookup"><span data-stu-id="7decb-137">Serializing an ArrayList</span></span>

<span data-ttu-id="7decb-138">La classe <xref:System.Collections.ArrayList> peut contenir une collection d'objets divers.</span><span class="sxs-lookup"><span data-stu-id="7decb-138">The <xref:System.Collections.ArrayList> class can contain a collection of diverse objects.</span></span> <span data-ttu-id="7decb-139">Par conséquent, vous pouvez utiliser un <xref:System.Collections.ArrayList> plus souvent qu'un tableau.</span><span class="sxs-lookup"><span data-stu-id="7decb-139">You can therefore use a <xref:System.Collections.ArrayList> much as you use an array.</span></span> <span data-ttu-id="7decb-140">Au lieu de créer un champ qui retourne un tableau d'objets typés, vous pouvez cependant créer un champ qui retourne un <xref:System.Collections.ArrayList> unique.</span><span class="sxs-lookup"><span data-stu-id="7decb-140">Instead of creating a field that returns an array of typed objects, however, you can create a field that returns a single <xref:System.Collections.ArrayList>.</span></span> <span data-ttu-id="7decb-141">Toutefois, comme avec les tableaux, vous devez indiquer à <xref:System.Xml.Serialization.XmlSerializer> les types d'objets que contient l'<xref:System.Collections.ArrayList>.</span><span class="sxs-lookup"><span data-stu-id="7decb-141">However, as with arrays, you must inform the <xref:System.Xml.Serialization.XmlSerializer> of the types of objects the <xref:System.Collections.ArrayList> contains.</span></span> <span data-ttu-id="7decb-142">Pour ce faire, assignez plusieurs instances de <xref:System.Xml.Serialization.XmlElementAttribute> à ce champ, comme illustré dans l'exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="7decb-142">To accomplish this, assign multiple instances of the <xref:System.Xml.Serialization.XmlElementAttribute> to the field, as shown in the following example.</span></span>

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

## <a name="controlling-serialization-of-classes-using-xmlrootattribute-and-xmltypeattribute"></a><span data-ttu-id="7decb-143">Contrôle de la sérialisation de classes à l'aide de XmlRootAttribute et XmlTypeAttribute</span><span class="sxs-lookup"><span data-stu-id="7decb-143">Controlling Serialization of Classes Using XmlRootAttribute and XmlTypeAttribute</span></span>

<span data-ttu-id="7decb-144">Il est possible d'appliquer deux attributs à une seule et même classe : <xref:System.Xml.Serialization.XmlRootAttribute> et <xref:System.Xml.Serialization.XmlTypeAttribute>.</span><span class="sxs-lookup"><span data-stu-id="7decb-144">There are two attributes that can be applied to a class (and only a class): <xref:System.Xml.Serialization.XmlRootAttribute> and <xref:System.Xml.Serialization.XmlTypeAttribute>.</span></span> <span data-ttu-id="7decb-145">Ces attributs sont très semblables.</span><span class="sxs-lookup"><span data-stu-id="7decb-145">These attributes are very similar.</span></span> <span data-ttu-id="7decb-146"><xref:System.Xml.Serialization.XmlRootAttribute> peut être appliqué à une seule classe : celle qui, une fois sérialisée, représente l'élément ouvrant et fermant du document XML, c'est-à-dire l'élément racine.</span><span class="sxs-lookup"><span data-stu-id="7decb-146">The <xref:System.Xml.Serialization.XmlRootAttribute> can be applied to only one class: the class that, when serialized, represents the XML document's opening and closing element—in other words, the root element.</span></span> <span data-ttu-id="7decb-147">En revanche, <xref:System.Xml.Serialization.XmlTypeAttribute> peut être appliqué à n'importe quelle classe, y compris la classe racine.</span><span class="sxs-lookup"><span data-stu-id="7decb-147">The <xref:System.Xml.Serialization.XmlTypeAttribute>, on the other hand, can be applied to any class, including the root class.</span></span>

<span data-ttu-id="7decb-148">Par exemple, la classe `Group` correspond à la classe racine dans les exemples précédents, et tous ses champs et propriétés publics deviennent les éléments XML recherchés dans le document XML.</span><span class="sxs-lookup"><span data-stu-id="7decb-148">For example, in the previous examples, the `Group` class is the root class, and all its public fields and properties become the XML elements found in the XML document.</span></span> <span data-ttu-id="7decb-149">Par conséquent, il ne peut y avoir qu'une seule classe racine.</span><span class="sxs-lookup"><span data-stu-id="7decb-149">Therefore, there can be only one root class.</span></span> <span data-ttu-id="7decb-150">En appliquant <xref:System.Xml.Serialization.XmlRootAttribute>, vous pouvez contrôler le flux de données XML généré par <xref:System.Xml.Serialization.XmlSerializer>.</span><span class="sxs-lookup"><span data-stu-id="7decb-150">By applying the <xref:System.Xml.Serialization.XmlRootAttribute>, you can control the XML stream generated by the <xref:System.Xml.Serialization.XmlSerializer>.</span></span> <span data-ttu-id="7decb-151">Par exemple, vous pouvez modifier le nom de l'élément et l'espace de noms.</span><span class="sxs-lookup"><span data-stu-id="7decb-151">For example, you can change the element name and namespace.</span></span>

<span data-ttu-id="7decb-152"><xref:System.Xml.Serialization.XmlTypeAttribute> vous permet de contrôler le schéma du code XML généré.</span><span class="sxs-lookup"><span data-stu-id="7decb-152">The <xref:System.Xml.Serialization.XmlTypeAttribute> allows you to control the schema of the generated XML.</span></span> <span data-ttu-id="7decb-153">Cette fonction est utile lorsque vous devez publier le schéma via un service Web XML.</span><span class="sxs-lookup"><span data-stu-id="7decb-153">This capability is useful when you need to publish the schema through an XML Web service.</span></span> <span data-ttu-id="7decb-154">L'exemple suivant applique <xref:System.Xml.Serialization.XmlTypeAttribute> et <xref:System.Xml.Serialization.XmlRootAttribute> à la même classe.</span><span class="sxs-lookup"><span data-stu-id="7decb-154">The following example applies both the <xref:System.Xml.Serialization.XmlTypeAttribute> and the <xref:System.Xml.Serialization.XmlRootAttribute> to the same class.</span></span>

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

<span data-ttu-id="7decb-155">Si cette classe est compilée et que l'outil XML Schema Definition est utilisé pour générer son schéma, vous obtenez le code XML suivant qui décrit `Group`.</span><span class="sxs-lookup"><span data-stu-id="7decb-155">If this class is compiled, and the XML Schema Definition tool is used to generate its schema, you would find the following XML describing `Group`.</span></span>

```xml
<xs:element name="NewGroupName" type="NewTypeName">
```

<span data-ttu-id="7decb-156">En revanche, si vous deviez sérialiser une instance de la classe, vous obtiendriez uniquement `NewGroupName` dans le document XML.</span><span class="sxs-lookup"><span data-stu-id="7decb-156">In contrast, if you were to serialize an instance of the class, only `NewGroupName` would be found in the XML document.</span></span>

```xml
<NewGroupName>
    . . .
</NewGroupName>
```

## <a name="preventing-serialization-with-the-xmlignoreattribute"></a><span data-ttu-id="7decb-157">Empêcher la sérialisation avec XmlIgnoreAttribute</span><span class="sxs-lookup"><span data-stu-id="7decb-157">Preventing Serialization with the XmlIgnoreAttribute</span></span>

<span data-ttu-id="7decb-158">Dans certains cas, une propriété ou un champ public ne doit pas être sérialisé.</span><span class="sxs-lookup"><span data-stu-id="7decb-158">There might be situations when a public property or field does not need to be serialized.</span></span> <span data-ttu-id="7decb-159">Par exemple, un champ ou une propriété peut servir à contenir des métadonnées.</span><span class="sxs-lookup"><span data-stu-id="7decb-159">For example, a field or property could be used to contain metadata.</span></span> <span data-ttu-id="7decb-160">Dans de tels cas, appliquez <xref:System.Xml.Serialization.XmlIgnoreAttribute> au champ ou à la propriété pour que <xref:System.Xml.Serialization.XmlSerializer> puisse l'ignorer.</span><span class="sxs-lookup"><span data-stu-id="7decb-160">In such cases, apply the <xref:System.Xml.Serialization.XmlIgnoreAttribute> to the field or property and the <xref:System.Xml.Serialization.XmlSerializer> will skip over it.</span></span>

## <a name="see-also"></a><span data-ttu-id="7decb-161">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="7decb-161">See also</span></span>

- [<span data-ttu-id="7decb-162">Attributs qui contrôlent la sérialisation XML</span><span class="sxs-lookup"><span data-stu-id="7decb-162">Attributes That Control XML Serialization</span></span>](attributes-that-control-xml-serialization.md)
- [<span data-ttu-id="7decb-163">Attributs qui contrôlent la sérialisation encodée selon le protocole SOAP</span><span class="sxs-lookup"><span data-stu-id="7decb-163">Attributes That Control Encoded SOAP Serialization</span></span>](attributes-that-control-encoded-soap-serialization.md)
- [<span data-ttu-id="7decb-164">Introduction à la sérialisation XML</span><span class="sxs-lookup"><span data-stu-id="7decb-164">Introducing XML Serialization</span></span>](introducing-xml-serialization.md)
- [<span data-ttu-id="7decb-165">Exemples de sérialisation XML</span><span class="sxs-lookup"><span data-stu-id="7decb-165">Examples of XML Serialization</span></span>](examples-of-xml-serialization.md)
- [<span data-ttu-id="7decb-166">Guide pratique pour spécifier un nom d’élément différent pour un flux XML</span><span class="sxs-lookup"><span data-stu-id="7decb-166">How to: Specify an Alternate Element Name for an XML Stream</span></span>](how-to-specify-an-alternate-element-name-for-an-xml-stream.md)
- [<span data-ttu-id="7decb-167">Guide pratique pour sérialiser un objet</span><span class="sxs-lookup"><span data-stu-id="7decb-167">How to: Serialize an Object</span></span>](how-to-serialize-an-object.md)
- [<span data-ttu-id="7decb-168">Guide pratique pour désérialiser un objet</span><span class="sxs-lookup"><span data-stu-id="7decb-168">How to: Deserialize an Object</span></span>](how-to-deserialize-an-object.md)
