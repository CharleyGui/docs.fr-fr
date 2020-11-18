---
title: Modification de schémas XML
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
ms.assetid: fa09c8e5-c2b9-49d2-bb0d-40330cd13e4d
ms.openlocfilehash: e900a558c6599d00e8f848ea50e5b30985475d1b
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/18/2020
ms.locfileid: "94830257"
---
# <a name="editing-xml-schemas"></a><span data-ttu-id="327cc-102">Modification de schémas XML</span><span class="sxs-lookup"><span data-stu-id="327cc-102">Editing XML Schemas</span></span>

<span data-ttu-id="327cc-103">La modification d’un schéma XML est l’une des fonctionnalités les plus importantes du SOM (Schema Object Model).</span><span class="sxs-lookup"><span data-stu-id="327cc-103">Editing an XML schema is one of the most important features of the Schema Object Model (SOM).</span></span> <span data-ttu-id="327cc-104">Toutes les propriétés de pré-compilation de schéma du SOM peuvent être utilisées pour changer les valeurs existantes d'un schéma XML.</span><span class="sxs-lookup"><span data-stu-id="327cc-104">All of the pre-schema-compilation properties of the SOM can be used to change the existing values in an XML schema.</span></span> <span data-ttu-id="327cc-105">Le schéma XML peut ensuite être recompilé pour que les changements prennent effet.</span><span class="sxs-lookup"><span data-stu-id="327cc-105">The XML schema can then be recompiled to reflect the changes.</span></span>

<span data-ttu-id="327cc-106">La première étape de la modification d'un schéma chargé dans le SOM consiste à parcourir le schéma.</span><span class="sxs-lookup"><span data-stu-id="327cc-106">The first step in editing a schema loaded into the SOM is to traverse the schema.</span></span> <span data-ttu-id="327cc-107">Vous devriez savoir comment traverser un schéma à l'aide de l'API du SOM avant de tenter de modifier un schéma.</span><span class="sxs-lookup"><span data-stu-id="327cc-107">You should be familiar with traversing a schema using the SOM API before you attempt to edit a schema.</span></span> <span data-ttu-id="327cc-108">Vous devez aussi bien connaître les propriétés de pré- et post-compilation de schéma du PSCI (Post-Schema-Compilation-Infoset).</span><span class="sxs-lookup"><span data-stu-id="327cc-108">You should also be familiar with the pre- and post-schema-compilation properties of the Post-Schema-Compilation-Infoset (PSCI).</span></span>

## <a name="editing-an-xml-schema"></a><span data-ttu-id="327cc-109">Modification d'un schéma XML</span><span class="sxs-lookup"><span data-stu-id="327cc-109">Editing an XML Schema</span></span>

<span data-ttu-id="327cc-110">Cette section présente deux exemples de code, qui modifient tous deux le schéma utilisateur créé dans la rubrique [Création de schémas XML](building-xml-schemas.md).</span><span class="sxs-lookup"><span data-stu-id="327cc-110">In this section, two code examples are provided, both of which edit the customer schema created in the [Building XML Schemas](building-xml-schemas.md) topic.</span></span> <span data-ttu-id="327cc-111">Le premier exemple de code ajoute un nouvel élément `PhoneNumber` à l'élément `Customer` ; le second ajoute un nouvel attribut `Title` à l'élément `FirstName`.</span><span class="sxs-lookup"><span data-stu-id="327cc-111">The first code example adds a new `PhoneNumber` element to the `Customer` element and the second code example adds a new `Title` attribute to the `FirstName` element.</span></span> <span data-ttu-id="327cc-112">Le premier exemple utilise aussi la collection de post-compilation de schéma <xref:System.Xml.Schema.XmlSchema.Elements%2A?displayProperty=nameWithType> comme moyen de traverser le schéma utilisateur, tandis que le second utilise la collection <xref:System.Xml.Schema.XmlSchema.Items%2A?displayProperty=nameWithType> de pré-compilation de schéma.</span><span class="sxs-lookup"><span data-stu-id="327cc-112">The first sample also uses the post-schema-compilation <xref:System.Xml.Schema.XmlSchema.Elements%2A?displayProperty=nameWithType> collection as the means of traversing the customer schema while the second code example uses the pre-schema-compilation <xref:System.Xml.Schema.XmlSchema.Items%2A?displayProperty=nameWithType> collection.</span></span>

### <a name="phonenumber-element-example"></a><span data-ttu-id="327cc-113">Exemple d'élément PhoneNumber</span><span class="sxs-lookup"><span data-stu-id="327cc-113">PhoneNumber Element Example</span></span>

<span data-ttu-id="327cc-114">Le premier exemple de code ajoute un nouvel élément `PhoneNumber` à l'élément `Customer` du schéma utilisateur.</span><span class="sxs-lookup"><span data-stu-id="327cc-114">This first code example adds a new `PhoneNumber` element to the `Customer` element of the customer schema.</span></span> <span data-ttu-id="327cc-115">Cet exemple de code modifie le schéma utilisateur en plusieurs étapes comme suit.</span><span class="sxs-lookup"><span data-stu-id="327cc-115">The code example edits the customer schema in the following steps.</span></span>

1. <span data-ttu-id="327cc-116">Il ajoute le schéma utilisateur à un nouvel objet <xref:System.Xml.Schema.XmlSchemaSet> puis le compile.</span><span class="sxs-lookup"><span data-stu-id="327cc-116">Adds the customer schema to a new <xref:System.Xml.Schema.XmlSchemaSet> object and then compiles it.</span></span> <span data-ttu-id="327cc-117">Les avertissements et erreurs de validation de schéma éventuellement rencontrés pendant la lecture ou la compilation du schéma sont traités par le délégué <xref:System.Xml.Schema.ValidationEventHandler>.</span><span class="sxs-lookup"><span data-stu-id="327cc-117">Any schema validation warnings and errors encountered reading or compiling the schema are handled by the <xref:System.Xml.Schema.ValidationEventHandler> delegate.</span></span>

2. <span data-ttu-id="327cc-118">Il extrait l'objet <xref:System.Xml.Schema.XmlSchema> compilé de l'objet <xref:System.Xml.Schema.XmlSchemaSet> en effectuant une itération sur la propriété <xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A>.</span><span class="sxs-lookup"><span data-stu-id="327cc-118">Retrieves the compiled <xref:System.Xml.Schema.XmlSchema> object from the <xref:System.Xml.Schema.XmlSchemaSet> by iterating over the <xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A> property.</span></span> <span data-ttu-id="327cc-119">Le schéma étant compilé, les propriétés PSCI (Post-Schema-Compilation-Infoset) sont accessibles.</span><span class="sxs-lookup"><span data-stu-id="327cc-119">Because the schema is compiled, Post-Schema-Compilation-Infoset (PSCI) properties are accessible.</span></span>

3. <span data-ttu-id="327cc-120">Il crée l’élément `PhoneNumber` à l’aide de la classe <xref:System.Xml.Schema.XmlSchemaElement>, la restriction de type simple `xs:string` à l’aide des classes <xref:System.Xml.Schema.XmlSchemaSimpleType> et <xref:System.Xml.Schema.XmlSchemaSimpleTypeRestriction>, il ajoute une facette de modèle à la propriété <xref:System.Xml.Schema.XmlSchemaSimpleTypeRestriction.Facets%2A> de la restriction et ajoute la restriction à la propriété <xref:System.Xml.Schema.XmlSchemaSimpleType.Content%2A> du type simple et le type simple à la propriété <xref:System.Xml.Schema.XmlSchemaElement.SchemaType%2A> de l’élément `PhoneNumber`.</span><span class="sxs-lookup"><span data-stu-id="327cc-120">Creates the `PhoneNumber` element using the <xref:System.Xml.Schema.XmlSchemaElement> class, the `xs:string` simple type restriction using the <xref:System.Xml.Schema.XmlSchemaSimpleType> and <xref:System.Xml.Schema.XmlSchemaSimpleTypeRestriction> classes, adds a pattern facet to the <xref:System.Xml.Schema.XmlSchemaSimpleTypeRestriction.Facets%2A> property of the restriction, and adds the restriction to the <xref:System.Xml.Schema.XmlSchemaSimpleType.Content%2A> property of the simple type and the simple type to the <xref:System.Xml.Schema.XmlSchemaElement.SchemaType%2A> of the `PhoneNumber` element.</span></span>

4. <span data-ttu-id="327cc-121">Il effectue une itération sur chaque objet <xref:System.Xml.Schema.XmlSchemaElement> contenu dans la collection <xref:System.Xml.Schema.XmlSchemaObjectTable.Values%2A> de la collection <xref:System.Xml.Schema.XmlSchema.Elements%2A?displayProperty=nameWithType> de post-compilation de schéma.</span><span class="sxs-lookup"><span data-stu-id="327cc-121">Iterates over each <xref:System.Xml.Schema.XmlSchemaElement> in the <xref:System.Xml.Schema.XmlSchemaObjectTable.Values%2A> collection of the post-schema-compilation <xref:System.Xml.Schema.XmlSchema.Elements%2A?displayProperty=nameWithType> collection.</span></span>

5. <span data-ttu-id="327cc-122">Si la propriété <xref:System.Xml.Schema.XmlSchemaElement.QualifiedName%2A> de l'élément est `"Customer"`, il obtient le type complexe de l'élément `Customer` à l'aide de la classe <xref:System.Xml.Schema.XmlSchemaComplexType> et la particule de séquence du type complexe à l'aide de la classe <xref:System.Xml.Schema.XmlSchemaSequence>.</span><span class="sxs-lookup"><span data-stu-id="327cc-122">If the <xref:System.Xml.Schema.XmlSchemaElement.QualifiedName%2A> of the element is `"Customer"`, gets the complex type of the `Customer` element using the <xref:System.Xml.Schema.XmlSchemaComplexType> class and the sequence particle of the complex type using the <xref:System.Xml.Schema.XmlSchemaSequence> class.</span></span>

6. <span data-ttu-id="327cc-123">Il ajoute le nouvel élément `PhoneNumber` à la séquence contenant les éléments `FirstName` et `LastName` existants à la collection <xref:System.Xml.Schema.XmlSchemaSequence.Items%2A> de pré-compilation de schéma de la séquence.</span><span class="sxs-lookup"><span data-stu-id="327cc-123">Adds the new `PhoneNumber` element to the sequence containing the existing `FirstName` and `LastName` elements using the pre-schema-compilation <xref:System.Xml.Schema.XmlSchemaSequence.Items%2A> collection of the sequence.</span></span>

7. <span data-ttu-id="327cc-124">Enfin, il retraite et compile l'objet <xref:System.Xml.Schema.XmlSchema> modifié à l'aide des méthodes <xref:System.Xml.Schema.XmlSchemaSet.Reprocess%2A> et <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A> de la classe <xref:System.Xml.Schema.XmlSchemaSet> et écrit le résultat à la console.</span><span class="sxs-lookup"><span data-stu-id="327cc-124">Finally, reprocesses and compiles the modified <xref:System.Xml.Schema.XmlSchema> object using the <xref:System.Xml.Schema.XmlSchemaSet.Reprocess%2A> and <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A> methods of the <xref:System.Xml.Schema.XmlSchemaSet> class and writes it to the console.</span></span>

<span data-ttu-id="327cc-125">Voici l'exemple de code complet.</span><span class="sxs-lookup"><span data-stu-id="327cc-125">The following is the complete code example.</span></span>

[!code-cpp[XmlSchemaEditExample1#1](../../../../samples/snippets/cpp/VS_Snippets_Data/XmlSchemaEditExample1/CPP/XmlSchemaEditExample1.cpp#1)]
[!code-csharp[XmlSchemaEditExample1#1](../../../../samples/snippets/csharp/VS_Snippets_Data/XmlSchemaEditExample1/CS/XmlSchemaEditExample1.cs#1)]
[!code-vb[XmlSchemaEditExample1#1](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XmlSchemaEditExample1/VB/XmlSchemaEditExample1.vb#1)]

<span data-ttu-id="327cc-126">Voici le schéma utilisateur modifié créé dans la rubrique [Création de schémas XML](building-xml-schemas.md).</span><span class="sxs-lookup"><span data-stu-id="327cc-126">The following is the modified customer schema created in the [Building XML Schemas](building-xml-schemas.md) topic.</span></span>

```xml
<?xml version="1.0" encoding="utf-8"?>
<xs:schema xmlns:tns="http://www.tempuri.org" targetNamespace="http://www.tempuri.org" xmlns:xs="http://www.w3.org/2001/XMLSchema">
  <xs:element name="Customer">
    <xs:complexType>
      <xs:sequence>
        <xs:element name="FirstName" type="xs:string" />
        <xs:element name="LastName" type="tns:LastNameType" />
        <xs:element name="PhoneNumber">           <xs:simpleType>             <xs:restriction base="xs:string">               <xs:pattern value="\d{3}-\d{3}-\d(4)" />             </xs:restriction>           </xs:simpleType>         </xs:element>
      </xs:sequence>
      <xs:attribute name="CustomerId" type="xs:positiveInteger" use="required" />
    </xs:complexType>
  </xs:element>
  <xs:simpleType name="LastNameType">
    <xs:restriction base="xs:string">
      <xs:maxLength value="20" />
    </xs:restriction>
  </xs:simpleType>
</xs:schema>
```

### <a name="title-attribute-example"></a><span data-ttu-id="327cc-127">Exemple d'attribut Title</span><span class="sxs-lookup"><span data-stu-id="327cc-127">Title Attribute Example</span></span>

<span data-ttu-id="327cc-128">Le second exemple de code ajoute un nouvel attribut `Title` à l'élément `FirstName` du schéma utilisateur.</span><span class="sxs-lookup"><span data-stu-id="327cc-128">This second code example, adds a new `Title` attribute to the `FirstName` element of the customer schema.</span></span> <span data-ttu-id="327cc-129">Dans le premier exemple, le type de l'élément `FirstName` est `xs:string`.</span><span class="sxs-lookup"><span data-stu-id="327cc-129">In the first code example, the type of the `FirstName` element is `xs:string`.</span></span> <span data-ttu-id="327cc-130">Pour que l'élément `FirstName` ait un attribut en plus de son contenu de type chaîne, le type de l'élément doit être changé en un type complexe avec un modèle de contenu d'extension de contenu simple.</span><span class="sxs-lookup"><span data-stu-id="327cc-130">For the `FirstName` element to have an attribute along with string content, its type must be changed to a complex type with a simple content extension content model.</span></span>

<span data-ttu-id="327cc-131">Cet exemple de code modifie le schéma utilisateur en plusieurs étapes comme suit.</span><span class="sxs-lookup"><span data-stu-id="327cc-131">The code example edits the customer schema in the following steps.</span></span>

1. <span data-ttu-id="327cc-132">Il ajoute le schéma utilisateur à un nouvel objet <xref:System.Xml.Schema.XmlSchemaSet> puis le compile.</span><span class="sxs-lookup"><span data-stu-id="327cc-132">Adds the customer schema to a new <xref:System.Xml.Schema.XmlSchemaSet> object and then compiles it.</span></span> <span data-ttu-id="327cc-133">Les avertissements et erreurs de validation de schéma éventuellement rencontrés pendant la lecture ou la compilation du schéma sont traités par le délégué <xref:System.Xml.Schema.ValidationEventHandler>.</span><span class="sxs-lookup"><span data-stu-id="327cc-133">Any schema validation warnings and errors encountered reading or compiling the schema are handled by the <xref:System.Xml.Schema.ValidationEventHandler> delegate.</span></span>

2. <span data-ttu-id="327cc-134">Il extrait l'objet <xref:System.Xml.Schema.XmlSchema> compilé de l'objet <xref:System.Xml.Schema.XmlSchemaSet> en effectuant une itération sur la propriété <xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A>.</span><span class="sxs-lookup"><span data-stu-id="327cc-134">Retrieves the compiled <xref:System.Xml.Schema.XmlSchema> object from the <xref:System.Xml.Schema.XmlSchemaSet> by iterating over the <xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A> property.</span></span> <span data-ttu-id="327cc-135">Le schéma étant compilé, les propriétés PSCI (Post-Schema-Compilation-Infoset) sont accessibles.</span><span class="sxs-lookup"><span data-stu-id="327cc-135">Because the schema is compiled, Post-Schema-Compilation-Infoset (PSCI) properties are accessible.</span></span>

3. <span data-ttu-id="327cc-136">Il crée un type complexe pour l'élément `FirstName` en utilisant la classe <xref:System.Xml.Schema.XmlSchemaComplexType>.</span><span class="sxs-lookup"><span data-stu-id="327cc-136">Creates a new complex type for the `FirstName` element using the <xref:System.Xml.Schema.XmlSchemaComplexType> class.</span></span>

4. <span data-ttu-id="327cc-137">Il crée une extension de contenu simple, avec `xs:string` comme type de base, à l'aide des classes <xref:System.Xml.Schema.XmlSchemaSimpleContent> et <xref:System.Xml.Schema.XmlSchemaSimpleContentExtension>.</span><span class="sxs-lookup"><span data-stu-id="327cc-137">Creates a new simple content extension, with a base type of `xs:string`, using the <xref:System.Xml.Schema.XmlSchemaSimpleContent> and <xref:System.Xml.Schema.XmlSchemaSimpleContentExtension> classes.</span></span>

5. <span data-ttu-id="327cc-138">Il crée l'attribut `Title` à l'aide de la classe <xref:System.Xml.Schema.XmlSchemaAttribute>, avec un <xref:System.Xml.Schema.XmlSchemaAttribute.SchemaTypeName%2A> comme propriété `xs:string` et ajoute l'attribut à l'extension de contenu simple.</span><span class="sxs-lookup"><span data-stu-id="327cc-138">Creates the new `Title` attribute using the <xref:System.Xml.Schema.XmlSchemaAttribute> class, with a <xref:System.Xml.Schema.XmlSchemaAttribute.SchemaTypeName%2A> of `xs:string` and adds the attribute to the simple content extension.</span></span>

6. <span data-ttu-id="327cc-139">Il définit le modèle de contenu du contenu simple comme étant l’extension de contenu simple et celui du type complexe comme étant le contenu simple.</span><span class="sxs-lookup"><span data-stu-id="327cc-139">Sets the content model of the simple content to the simple content extension and the content model of the complex type to the simple content.</span></span>

7. <span data-ttu-id="327cc-140">Il ajoute le nouveau type complexe à la collection de pré-compilation de schéma <xref:System.Xml.Schema.XmlSchema.Items%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="327cc-140">Adds the new complex type to the pre-schema-compilation <xref:System.Xml.Schema.XmlSchema.Items%2A?displayProperty=nameWithType> collection.</span></span>

8. <span data-ttu-id="327cc-141">Il effectue une itération sur chaque objet <xref:System.Xml.Schema.XmlSchemaObject> contenu dans la collection <xref:System.Xml.Schema.XmlSchema.Items%2A?displayProperty=nameWithType> de pré-compilation de schéma.</span><span class="sxs-lookup"><span data-stu-id="327cc-141">Iterates over each <xref:System.Xml.Schema.XmlSchemaObject> in the pre-schema-compilation <xref:System.Xml.Schema.XmlSchema.Items%2A?displayProperty=nameWithType> collection.</span></span>

> [!NOTE]
> <span data-ttu-id="327cc-142">Puisque l'élément `FirstName` n'est pas un élément global dans le schéma, il n'est pas disponible dans les collections <xref:System.Xml.Schema.XmlSchema.Items%2A?displayProperty=nameWithType> ou <xref:System.Xml.Schema.XmlSchema.Elements%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="327cc-142">Because the `FirstName` element is not a global element in the schema, it is not available in the <xref:System.Xml.Schema.XmlSchema.Items%2A?displayProperty=nameWithType> or <xref:System.Xml.Schema.XmlSchema.Elements%2A?displayProperty=nameWithType> collections.</span></span> <span data-ttu-id="327cc-143">L'exemple de code localise l'élément `FirstName` en localisant d'abord l'élément `Customer`.</span><span class="sxs-lookup"><span data-stu-id="327cc-143">The code example locates the `FirstName` element by first locating the `Customer` element.</span></span>
>
> <span data-ttu-id="327cc-144">Le premier exemple de code traversait le schéma en utilisant la collection <xref:System.Xml.Schema.XmlSchema.Elements%2A?displayProperty=nameWithType> de post-compilation de schéma.</span><span class="sxs-lookup"><span data-stu-id="327cc-144">The first code example traversed the schema using the post-schema-compilation <xref:System.Xml.Schema.XmlSchema.Elements%2A?displayProperty=nameWithType> collection.</span></span> <span data-ttu-id="327cc-145">Dans ce deuxième exemple, c’est la collection <xref:System.Xml.Schema.XmlSchema.Items%2A?displayProperty=nameWithType> de pré-compilation de schéma qui est utilisée pour traverser le schéma.</span><span class="sxs-lookup"><span data-stu-id="327cc-145">In this sample, the pre-schema-compilation <xref:System.Xml.Schema.XmlSchema.Items%2A?displayProperty=nameWithType> collection is used to traverse the schema.</span></span> <span data-ttu-id="327cc-146">Les deux collections offrent un accès aux éléments globaux du schéma, mais une itération via la collection <xref:System.Xml.Schema.XmlSchema.Items%2A> prend plus de temps car vous devez effectuer l’itération sur tous les éléments globaux du schéma et cette collection n’a pas de propriétés PSCI.</span><span class="sxs-lookup"><span data-stu-id="327cc-146">While both collections provide access to the global elements in the schema, iterating through the <xref:System.Xml.Schema.XmlSchema.Items%2A> collection is more time consuming because you must iterate over all global elements in the schema and it does not have any PSCI properties.</span></span> <span data-ttu-id="327cc-147">Les collections PSCI (propriétés <xref:System.Xml.Schema.XmlSchema.Elements%2A?displayProperty=nameWithType>, <xref:System.Xml.Schema.XmlSchema.Attributes%2A?displayProperty=nameWithType>, <xref:System.Xml.Schema.XmlSchema.SchemaTypes%2A?displayProperty=nameWithType>, etc.) offrent un accès direct à leurs éléments, attributs et types globaux ainsi qu’à leurs propriétés PSCI.</span><span class="sxs-lookup"><span data-stu-id="327cc-147">The PSCI collections (<xref:System.Xml.Schema.XmlSchema.Elements%2A?displayProperty=nameWithType>, <xref:System.Xml.Schema.XmlSchema.Attributes%2A?displayProperty=nameWithType>, <xref:System.Xml.Schema.XmlSchema.SchemaTypes%2A?displayProperty=nameWithType>, and so on) provide direct access to their global elements, attributes, and types and their PSCI properties.</span></span>

1. <span data-ttu-id="327cc-148">Si l'objet <xref:System.Xml.Schema.XmlSchemaObject> est un élément dont la propriété <xref:System.Xml.Schema.XmlSchemaElement.QualifiedName%2A> est `"Customer"`, il obtient le type complexe de l'élément `Customer` à l'aide de la classe <xref:System.Xml.Schema.XmlSchemaComplexType> et la particule de séquence du type complexe à l'aide de la classe <xref:System.Xml.Schema.XmlSchemaSequence>.</span><span class="sxs-lookup"><span data-stu-id="327cc-148">If the <xref:System.Xml.Schema.XmlSchemaObject> is an element, whose <xref:System.Xml.Schema.XmlSchemaElement.QualifiedName%2A> is `"Customer"`, gets the complex type of the `Customer` element using the <xref:System.Xml.Schema.XmlSchemaComplexType> class and the sequence particle of the complex type using the <xref:System.Xml.Schema.XmlSchemaSequence> class.</span></span>

2. <span data-ttu-id="327cc-149">Il effectue une itération sur chaque objet <xref:System.Xml.Schema.XmlSchemaParticle> contenu dans la collection <xref:System.Xml.Schema.XmlSchemaSequence.Items%2A?displayProperty=nameWithType> de pré-compilation de schéma.</span><span class="sxs-lookup"><span data-stu-id="327cc-149">Iterates over each <xref:System.Xml.Schema.XmlSchemaParticle> in the pre-schema-compilation <xref:System.Xml.Schema.XmlSchemaSequence.Items%2A?displayProperty=nameWithType> collection.</span></span>

3. <span data-ttu-id="327cc-150">Si l'objet <xref:System.Xml.Schema.XmlSchemaParticle> est un élément dont la propriété <xref:System.Xml.Schema.XmlSchemaElement.QualifiedName%2A> est `"FirstName"`, il définit la propriété <xref:System.Xml.Schema.XmlSchemaElement.SchemaTypeName%2A> de l'élément `FirstName` comme étant le nouveau type complexe `FirstName`.</span><span class="sxs-lookup"><span data-stu-id="327cc-150">If the <xref:System.Xml.Schema.XmlSchemaParticle> is an element, who's <xref:System.Xml.Schema.XmlSchemaElement.QualifiedName%2A> is `"FirstName"`, sets the <xref:System.Xml.Schema.XmlSchemaElement.SchemaTypeName%2A> of the `FirstName` element to the new `FirstName` complex type.</span></span>

4. <span data-ttu-id="327cc-151">Enfin, il retraite et compile l'objet <xref:System.Xml.Schema.XmlSchema> modifié à l'aide des méthodes <xref:System.Xml.Schema.XmlSchemaSet.Reprocess%2A> et <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A> de la classe <xref:System.Xml.Schema.XmlSchemaSet> et écrit le résultat à la console.</span><span class="sxs-lookup"><span data-stu-id="327cc-151">Finally, reprocesses and compiles the modified <xref:System.Xml.Schema.XmlSchema> object using the <xref:System.Xml.Schema.XmlSchemaSet.Reprocess%2A> and <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A> methods of the <xref:System.Xml.Schema.XmlSchemaSet> class and writes it to the console.</span></span>

<span data-ttu-id="327cc-152">Voici l'exemple de code complet.</span><span class="sxs-lookup"><span data-stu-id="327cc-152">The following is the complete code example.</span></span>

[!code-cpp[XmlSchemaEditExample2#1](../../../../samples/snippets/cpp/VS_Snippets_Data/XmlSchemaEditExample2/CPP/XmlSchemaEditExample2.cpp#1)]
[!code-csharp[XmlSchemaEditExample2#1](../../../../samples/snippets/csharp/VS_Snippets_Data/XmlSchemaEditExample2/CS/XmlSchemaEditExample2.cs#1)]
[!code-vb[XmlSchemaEditExample2#1](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XmlSchemaEditExample2/VB/XmlSchemaEditExample2.vb#1)]

<span data-ttu-id="327cc-153">Voici le schéma utilisateur modifié créé dans la rubrique [Création de schémas XML](building-xml-schemas.md).</span><span class="sxs-lookup"><span data-stu-id="327cc-153">The following is the modified customer schema created in the [Building XML Schemas](building-xml-schemas.md) topic.</span></span>

```xml
<?xml version="1.0" encoding=" utf-8"?>
<xs:schema xmlns:tns="http://www.tempuri.org" targetNamespace="http://www.tempuri.org" xmlns:xs="http://www.w3.org/2001/XMLSchema">
  <xs:element name="Customer">
    <xs:complexType>
      <xs:sequence>
        <xs:element name="FirstName" type="tns:FirstNameComplexType" />
        <xs:element name="LastName" type="tns:LastNameType" />
      </xs:sequence>
      <xs:attribute name="CustomerId" type="xs:positiveInteger" use="required" />
    </xs:complexType>
  </xs:element>
  <xs:simpleType name="LastNameType">
    <xs:restriction base="xs:string">
      <xs:maxLength value="20" />
    </xs:restriction>
  </xs:simpleType>
  <xs:complexType name="FirstNameComplexType">     <xs:simpleContent>       <xs:extension base="xs:string">         <xs:attribute name="Title" type="xs:string" />       </xs:extension>     </xs:simpleContent>   </xs:complexType>
</xs:schema>
```

## <a name="see-also"></a><span data-ttu-id="327cc-154">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="327cc-154">See also</span></span>

- [<span data-ttu-id="327cc-155">Vue d'ensemble du Modèle Objet du schéma XML</span><span class="sxs-lookup"><span data-stu-id="327cc-155">XML Schema Object Model Overview</span></span>](xml-schema-object-model-overview.md)
- [<span data-ttu-id="327cc-156">Lecture et écriture de schémas XML</span><span class="sxs-lookup"><span data-stu-id="327cc-156">Reading and Writing XML Schemas</span></span>](reading-and-writing-xml-schemas.md)
- [<span data-ttu-id="327cc-157">Création de schémas XML</span><span class="sxs-lookup"><span data-stu-id="327cc-157">Building XML Schemas</span></span>](building-xml-schemas.md)
- [<span data-ttu-id="327cc-158">Traversée de schémas XML</span><span class="sxs-lookup"><span data-stu-id="327cc-158">Traversing XML Schemas</span></span>](traversing-xml-schemas.md)
- [<span data-ttu-id="327cc-159">Inclusion ou importation de schémas XML</span><span class="sxs-lookup"><span data-stu-id="327cc-159">Including or Importing XML Schemas</span></span>](including-or-importing-xml-schemas.md)
- [<span data-ttu-id="327cc-160">XmlSchemaSet pour la compilation de schémas</span><span class="sxs-lookup"><span data-stu-id="327cc-160">XmlSchemaSet for Schema Compilation</span></span>](xmlschemaset-for-schema-compilation.md)
- [<span data-ttu-id="327cc-161">Jeu d'informations de post-compilation de schéma</span><span class="sxs-lookup"><span data-stu-id="327cc-161">Post-Schema Compilation Infoset</span></span>](post-schema-compilation-infoset.md)
