---
title: Création de schémas XML
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
ms.assetid: 8a5ea56c-0140-4b51-8997-875ae6a8e0cb
ms.openlocfilehash: 177c52ea7217821735250b297974ac0ebaa1eb2e
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95725376"
---
# <a name="building-xml-schemas"></a><span data-ttu-id="3544e-102">Création de schémas XML</span><span class="sxs-lookup"><span data-stu-id="3544e-102">Building XML Schemas</span></span>

<span data-ttu-id="3544e-103">Les classes de l'espace de noms <xref:System.Xml.Schema?displayProperty=nameWithType> correspondent aux structures définies dans la recommandation du W3C (World Wide Web Consortium) sur les schémas XML et peuvent permettre de créer des schémas XML en mémoire.</span><span class="sxs-lookup"><span data-stu-id="3544e-103">The classes in the <xref:System.Xml.Schema?displayProperty=nameWithType> namespace map to the structures defined in the World Wide Web Consortium (W3C) XML Schema Recommendation and can be used to build XML schemas in-memory.</span></span>  
  
## <a name="building-an-xml-schema"></a><span data-ttu-id="3544e-104">Création d'un schéma XML</span><span class="sxs-lookup"><span data-stu-id="3544e-104">Building an XML Schema</span></span>  

 <span data-ttu-id="3544e-105">Dans les exemples de code suivants, l'API du SOM permet de créer un schéma XML client en mémoire.</span><span class="sxs-lookup"><span data-stu-id="3544e-105">In the code examples that follow, the SOM API is used to build a customer XML schema in-memory.</span></span>  
  
### <a name="creating-element-and-attributes"></a><span data-ttu-id="3544e-106">Création d'éléments et d'attributs</span><span class="sxs-lookup"><span data-stu-id="3544e-106">Creating Element and Attributes</span></span>  

 <span data-ttu-id="3544e-107">Les exemples de codes génèrent le schéma client à partir de rien en créant les attributs et les éléments enfants, puis les types qui leur correspondent et enfin les éléments de niveau supérieur.</span><span class="sxs-lookup"><span data-stu-id="3544e-107">The code examples build the customer schema from the bottom up, creating the child elements, attributes, and their corresponding types first, and then the top-level elements.</span></span>  
  
 <span data-ttu-id="3544e-108">Dans l'exemple de code suivant, les éléments `FirstName` et `LastName` ainsi que l'attribut `CustomerId` du schéma client sont créés à l'aide des classes <xref:System.Xml.Schema.XmlSchemaElement> et <xref:System.Xml.Schema.XmlSchemaAttribute> du SOM.</span><span class="sxs-lookup"><span data-stu-id="3544e-108">In the following code example, the `FirstName` and `LastName` elements, as well as the `CustomerId` attribute of the customer schema are created using the <xref:System.Xml.Schema.XmlSchemaElement> and <xref:System.Xml.Schema.XmlSchemaAttribute> classes of the SOM.</span></span> <span data-ttu-id="3544e-109">Exception faite des propriétés <xref:System.Xml.Schema.XmlSchemaElement.Name%2A> des classes <xref:System.Xml.Schema.XmlSchemaElement> et <xref:System.Xml.Schema.XmlSchemaAttribute>, qui correspondent à l'attribut « name » des éléments `<xs:element />` et `<xs:attribute />` d'un schéma XML, tous les autres attributs autorisés par le schéma (`defaultValue`, `fixedValue`, `form`, etc.) possèdent des propriétés correspondantes dans les classes <xref:System.Xml.Schema.XmlSchemaElement> et <xref:System.Xml.Schema.XmlSchemaAttribute>.</span><span class="sxs-lookup"><span data-stu-id="3544e-109">Apart from the <xref:System.Xml.Schema.XmlSchemaElement.Name%2A> properties of the <xref:System.Xml.Schema.XmlSchemaElement> and <xref:System.Xml.Schema.XmlSchemaAttribute> classes, which correspond to the "name" attribute of the `<xs:element />` and `<xs:attribute />` elements in an XML schema, all other attributes allowed by the schema (`defaultValue`, `fixedValue`, `form`, and so on) have corresponding properties in the <xref:System.Xml.Schema.XmlSchemaElement> and <xref:System.Xml.Schema.XmlSchemaAttribute> classes.</span></span>  
  
 [!code-cpp[XmlSchemaCreateExample#2](../../../../samples/snippets/cpp/VS_Snippets_Data/XmlSchemaCreateExample/CPP/XmlSchemaCreateExample.cpp#2)]
 [!code-csharp[XmlSchemaCreateExample#2](../../../../samples/snippets/csharp/VS_Snippets_Data/XmlSchemaCreateExample/CS/XmlSchemaCreateExample.cs#2)]
 [!code-vb[XmlSchemaCreateExample#2](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XmlSchemaCreateExample/VB/XmlSchemaCreateExample.vb#2)]  
  
### <a name="creating-schema-types"></a><span data-ttu-id="3544e-110">Création de types de schéma</span><span class="sxs-lookup"><span data-stu-id="3544e-110">Creating Schema Types</span></span>  

 <span data-ttu-id="3544e-111">Le contenu des éléments et des attributs est défini par leurs types.</span><span class="sxs-lookup"><span data-stu-id="3544e-111">The content of elements and attributes is defined by their types.</span></span> <span data-ttu-id="3544e-112">Pour créer des éléments et des attributs dont les types sont l'un des types de schéma intégrés, la propriété <xref:System.Xml.Schema.XmlSchemaElement.SchemaTypeName%2A> des classes <xref:System.Xml.Schema.XmlSchemaElement> ou <xref:System.Xml.Schema.XmlSchemaAttribute> sont définies sur le nom qualifié correspondant du type intégré à l'aide de la classe <xref:System.Xml.XmlQualifiedName>.</span><span class="sxs-lookup"><span data-stu-id="3544e-112">To create elements and attributes whose types are one of the built-in schema types, the <xref:System.Xml.Schema.XmlSchemaElement.SchemaTypeName%2A> property of the <xref:System.Xml.Schema.XmlSchemaElement> or <xref:System.Xml.Schema.XmlSchemaAttribute> classes are set with the corresponding qualified name of the built-in type using the <xref:System.Xml.XmlQualifiedName> class.</span></span> <span data-ttu-id="3544e-113">Pour créer un type défini par l'utilisateur pour les éléments et les attributs, un nouveau type simple ou complexe est créé à l'aide de la classe <xref:System.Xml.Schema.XmlSchemaSimpleType> ou <xref:System.Xml.Schema.XmlSchemaComplexType>.</span><span class="sxs-lookup"><span data-stu-id="3544e-113">To create a user-defined type for elements and attributes, a new simple or complex type is created using the <xref:System.Xml.Schema.XmlSchemaSimpleType> or <xref:System.Xml.Schema.XmlSchemaComplexType> class.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="3544e-114">Pour créer des types simples ou complexes sans nom qui sont des enfants anonymes d'un élément ou d'un attribut (seuls les types simples s'appliquent aux attributs), définissez la propriété <xref:System.Xml.Schema.XmlSchemaElement.SchemaType%2A> des classes <xref:System.Xml.Schema.XmlSchemaElement> ou <xref:System.Xml.Schema.XmlSchemaAttribute> sur le type simple ou complexe sans nom au lieu de la propriété <xref:System.Xml.Schema.XmlSchemaElement.SchemaTypeName%2A> des classes <xref:System.Xml.Schema.XmlSchemaElement> ou <xref:System.Xml.Schema.XmlSchemaAttribute>.</span><span class="sxs-lookup"><span data-stu-id="3544e-114">To create unnamed simple or complex types that are anonymous children of an element or attribute (only simple types apply for attributes), set the <xref:System.Xml.Schema.XmlSchemaElement.SchemaType%2A> property of the <xref:System.Xml.Schema.XmlSchemaElement> or <xref:System.Xml.Schema.XmlSchemaAttribute> classes to the unnamed simple or complex type, instead of the <xref:System.Xml.Schema.XmlSchemaElement.SchemaTypeName%2A> property of the <xref:System.Xml.Schema.XmlSchemaElement> or <xref:System.Xml.Schema.XmlSchemaAttribute> classes.</span></span>  
  
 <span data-ttu-id="3544e-115">Les schémas XML autorisent les types simples nommés et sans nom à être dérivés par restriction à partir d'autres types simples (intégrés ou définis par l'utilisateur) ou construits comme une liste ou l'union d'autres types simples.</span><span class="sxs-lookup"><span data-stu-id="3544e-115">XML schemas allow both anonymous and named simple types to be derived by restriction from other simple types (built-in or user-defined) or constructed as a list or union of other simple types.</span></span> <span data-ttu-id="3544e-116">La classe <xref:System.Xml.Schema.XmlSchemaSimpleTypeRestriction> permet de créer un type simple par restriction du type `xs:string` intégré.</span><span class="sxs-lookup"><span data-stu-id="3544e-116">The <xref:System.Xml.Schema.XmlSchemaSimpleTypeRestriction> class is used to create a simple type by restricting the built-in `xs:string` type.</span></span> <span data-ttu-id="3544e-117">Vous pouvez également utiliser les classes <xref:System.Xml.Schema.XmlSchemaSimpleTypeList> ou <xref:System.Xml.Schema.XmlSchemaSimpleTypeUnion> pour créer des types liste ou union.</span><span class="sxs-lookup"><span data-stu-id="3544e-117">You can also use the <xref:System.Xml.Schema.XmlSchemaSimpleTypeList> or <xref:System.Xml.Schema.XmlSchemaSimpleTypeUnion> classes to create list or union types.</span></span> <span data-ttu-id="3544e-118">La propriété <xref:System.Xml.Schema.XmlSchemaSimpleType.Content%2A?displayProperty=nameWithType> indique s'il s'agit d'une union, d'une liste ou d'une restriction de types simples.</span><span class="sxs-lookup"><span data-stu-id="3544e-118">The <xref:System.Xml.Schema.XmlSchemaSimpleType.Content%2A?displayProperty=nameWithType> property denotes whether it is a simple type restriction, list, or union.</span></span>  
  
 <span data-ttu-id="3544e-119">Dans l'exemple de code suivant, le type de l'élément `FirstName` est le type `xs:string` intégré, le type de l'élément `LastName` est un type simple nommé qui est une restriction du type `xs:string`, avec une valeur de facette `MaxLength` de 20 et le type de l'attribut `CustomerId` est le type `xs:positiveInteger` intégré.</span><span class="sxs-lookup"><span data-stu-id="3544e-119">In the following code example, the `FirstName` element's type is the built-in type `xs:string`, the `LastName` element's type is a named simple type that is a restriction of the built-in type `xs:string`, with a `MaxLength` facet value of 20, and the `CustomerId` attribute's type is the built-in type `xs:positiveInteger`.</span></span> <span data-ttu-id="3544e-120">L'élément `Customer` est un type complexe anonyme dont la particule est la séquence des éléments `FirstName` et `LastName` et dont les attributs contiennent l'attribut `CustomerId`.</span><span class="sxs-lookup"><span data-stu-id="3544e-120">The `Customer` element is an anonymous complex type whose particle is the sequence of the `FirstName` and `LastName` elements and whose attributes contains the `CustomerId` attribute.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="3544e-121">Vous pouvez également utiliser les classes <xref:System.Xml.Schema.XmlSchemaChoice> ou <xref:System.Xml.Schema.XmlSchemaAll> comme particule du type complexe pour répliquer les sémantiques `<xs:choice />` ou `<xs:all />`.</span><span class="sxs-lookup"><span data-stu-id="3544e-121">You can also use the <xref:System.Xml.Schema.XmlSchemaChoice> or <xref:System.Xml.Schema.XmlSchemaAll> classes as the particle of the complex type to replicate `<xs:choice />` or `<xs:all />` semantics.</span></span>  
  
 [!code-cpp[XmlSchemaCreateExample#3](../../../../samples/snippets/cpp/VS_Snippets_Data/XmlSchemaCreateExample/CPP/XmlSchemaCreateExample.cpp#3)]
 [!code-csharp[XmlSchemaCreateExample#3](../../../../samples/snippets/csharp/VS_Snippets_Data/XmlSchemaCreateExample/CS/XmlSchemaCreateExample.cs#3)]
 [!code-vb[XmlSchemaCreateExample#3](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XmlSchemaCreateExample/VB/XmlSchemaCreateExample.vb#3)]  
  
### <a name="creating-and-compiling-schemas"></a><span data-ttu-id="3544e-122">Création et compilation de schémas</span><span class="sxs-lookup"><span data-stu-id="3544e-122">Creating and Compiling Schemas</span></span>  

 <span data-ttu-id="3544e-123">À ce stade, les attributs et les éléments enfants, les types qui leur correspondent et les éléments `Customer` de niveau supérieur ont été créés en mémoire à l'aide de l'API du SOM.</span><span class="sxs-lookup"><span data-stu-id="3544e-123">At this point, the child elements and attributes, their corresponding types, and the top-level `Customer` element have been created in-memory using the SOM API.</span></span> <span data-ttu-id="3544e-124">Dans l'exemple de code suivant, l'élément de schéma est créé à l'aide de la classe <xref:System.Xml.Schema.XmlSchema>, les éléments de niveau supérieur et les types y sont ajoutés à l'aide de la propriété <xref:System.Xml.Schema.XmlSchema.Items%2A?displayProperty=nameWithType> et le schéma complet est compilé à l'aide de la classe <xref:System.Xml.Schema.XmlSchemaSet> et écrit dans la console.</span><span class="sxs-lookup"><span data-stu-id="3544e-124">In the following code example, the schema element is created using the <xref:System.Xml.Schema.XmlSchema> class, the top-level elements and types are added to it using the <xref:System.Xml.Schema.XmlSchema.Items%2A?displayProperty=nameWithType> property and the complete schema is compiled using the <xref:System.Xml.Schema.XmlSchemaSet> class and written to the console.</span></span>  
  
 [!code-cpp[XmlSchemaCreateExample#4](../../../../samples/snippets/cpp/VS_Snippets_Data/XmlSchemaCreateExample/CPP/XmlSchemaCreateExample.cpp#4)]
 [!code-csharp[XmlSchemaCreateExample#4](../../../../samples/snippets/csharp/VS_Snippets_Data/XmlSchemaCreateExample/CS/XmlSchemaCreateExample.cs#4)]
 [!code-vb[XmlSchemaCreateExample#4](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XmlSchemaCreateExample/VB/XmlSchemaCreateExample.vb#4)]  
  
 <span data-ttu-id="3544e-125">La méthode <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A?displayProperty=nameWithType> valide le schéma client par rapport aux règles d'un schéma XML et rend les propriétés de post-compilation de schéma disponibles.</span><span class="sxs-lookup"><span data-stu-id="3544e-125">The <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A?displayProperty=nameWithType> method validates the customer schema against the rules for an XML schema and makes post-schema-compilation properties available.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="3544e-126">Toutes les propriétés de post-compilation de schéma de l’API du SOM diffèrent de celles du jeu d’informations de post-validation de schéma.</span><span class="sxs-lookup"><span data-stu-id="3544e-126">All post-schema-compilation properties in the SOM API differ from the Post-Schema-Validation-Infoset.</span></span>  
  
 <span data-ttu-id="3544e-127">L'objet <xref:System.Xml.Schema.ValidationEventHandler> ajouté à <xref:System.Xml.Schema.XmlSchemaSet> est un délégué qui appelle la méthode de rappel `ValidationCallback` pour gérer les erreurs et les avertissements de validation de schéma.</span><span class="sxs-lookup"><span data-stu-id="3544e-127">The <xref:System.Xml.Schema.ValidationEventHandler> added to the <xref:System.Xml.Schema.XmlSchemaSet> is a delegate that calls the callback method `ValidationCallback` to handle schema validation warnings and errors.</span></span>  
  
 <span data-ttu-id="3544e-128">L'exemple de code suivant est complet et le schéma client est écrit dans la console.</span><span class="sxs-lookup"><span data-stu-id="3544e-128">The following is the complete code example, and the customer schema written to the console.</span></span>  
  
 [!code-cpp[XmlSchemaCreateExample#1](../../../../samples/snippets/cpp/VS_Snippets_Data/XmlSchemaCreateExample/CPP/XmlSchemaCreateExample.cpp#1)]
 [!code-csharp[XmlSchemaCreateExample#1](../../../../samples/snippets/csharp/VS_Snippets_Data/XmlSchemaCreateExample/CS/XmlSchemaCreateExample.cs#1)]
 [!code-vb[XmlSchemaCreateExample#1](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XmlSchemaCreateExample/VB/XmlSchemaCreateExample.vb#1)]  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<xs:schema xmlns:tns="http://www.tempuri.org" targetNamespace="http://www.tempuri.org" xmlns:xs="http://www.w3.org/2001/XMLSchema">  
   <xs:element name="Customer">  
      <xs:complexType>  
         <xs:sequence>  
            <xs:element name="FirstName" type="xs:string" />  
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
</xs:schema>  
```  
  
## <a name="see-also"></a><span data-ttu-id="3544e-129">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3544e-129">See also</span></span>

- [<span data-ttu-id="3544e-130">Vue d'ensemble du Modèle Objet du schéma XML</span><span class="sxs-lookup"><span data-stu-id="3544e-130">XML Schema Object Model Overview</span></span>](xml-schema-object-model-overview.md)
- [<span data-ttu-id="3544e-131">Lecture et écriture de schémas XML</span><span class="sxs-lookup"><span data-stu-id="3544e-131">Reading and Writing XML Schemas</span></span>](reading-and-writing-xml-schemas.md)
- [<span data-ttu-id="3544e-132">Traversée de schémas XML</span><span class="sxs-lookup"><span data-stu-id="3544e-132">Traversing XML Schemas</span></span>](traversing-xml-schemas.md)
- [<span data-ttu-id="3544e-133">Modification de schémas XML</span><span class="sxs-lookup"><span data-stu-id="3544e-133">Editing XML Schemas</span></span>](editing-xml-schemas.md)
- [<span data-ttu-id="3544e-134">Inclusion ou importation de schémas XML</span><span class="sxs-lookup"><span data-stu-id="3544e-134">Including or Importing XML Schemas</span></span>](including-or-importing-xml-schemas.md)
- [<span data-ttu-id="3544e-135">XmlSchemaSet pour la compilation de schémas</span><span class="sxs-lookup"><span data-stu-id="3544e-135">XmlSchemaSet for Schema Compilation</span></span>](xmlschemaset-for-schema-compilation.md)
- [<span data-ttu-id="3544e-136">Jeu d'informations de post-compilation de schéma</span><span class="sxs-lookup"><span data-stu-id="3544e-136">Post-Schema Compilation Infoset</span></span>](post-schema-compilation-infoset.md)
