---
title: Inclusion ou importation de schémas XML
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
ms.assetid: fe1b4a11-37f4-4e1a-93c9-239f4fe736c0
ms.openlocfilehash: f382165ca8e2b972c47a080244a3d0054b5eb604
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/18/2020
ms.locfileid: "94822735"
---
# <a name="including-or-importing-xml-schemas"></a><span data-ttu-id="42de1-102">Inclusion ou importation de schémas XML</span><span class="sxs-lookup"><span data-stu-id="42de1-102">Including or Importing XML Schemas</span></span>
<span data-ttu-id="42de1-103">Un schéma XML peut contenir des éléments `<xs:import />`, `<xs:include />` et `<xs:redefine />`.</span><span class="sxs-lookup"><span data-stu-id="42de1-103">An XML schema may contain `<xs:import />`, `<xs:include />`, and `<xs:redefine />` elements.</span></span> <span data-ttu-id="42de1-104">Ces éléments de schéma réfèrent à d'autres schémas XML qui peuvent être utilisés pour compléter la structure du schéma où ils sont inclus ou importés.</span><span class="sxs-lookup"><span data-stu-id="42de1-104">These schema elements refer to other XML schemas that can be used to supplement the structure of the schema that includes or imports them.</span></span> <span data-ttu-id="42de1-105">Les classes <xref:System.Xml.Schema.XmlSchemaImport>, <xref:System.Xml.Schema.XmlSchemaInclude> et <xref:System.Xml.Schema.XmlSchemaRedefine> sont mappées à ces éléments dans l'API SOM (Schema Object Model).</span><span class="sxs-lookup"><span data-stu-id="42de1-105">The <xref:System.Xml.Schema.XmlSchemaImport>, <xref:System.Xml.Schema.XmlSchemaInclude> and <xref:System.Xml.Schema.XmlSchemaRedefine> classes, map to these elements in the Schema Object Model (SOM) API.</span></span>  
  
## <a name="including-or-importing-an-xml-schema"></a><span data-ttu-id="42de1-106">Inclusion ou importation d'un schéma XML</span><span class="sxs-lookup"><span data-stu-id="42de1-106">Including or Importing an XML Schema</span></span>  
 <span data-ttu-id="42de1-107">L'exemple de code suivant complète le schéma utilisateur créé dans la rubrique [Création de schémas XML](building-xml-schemas.md) avec le schéma d'adresse.</span><span class="sxs-lookup"><span data-stu-id="42de1-107">The following code example supplements the customer schema created in the [Building XML Schemas](building-xml-schemas.md) topic with the address schema.</span></span> <span data-ttu-id="42de1-108">Cette opération rend les types d'adresses disponibles dans le schéma utilisateur.</span><span class="sxs-lookup"><span data-stu-id="42de1-108">Supplementing the customer schema with the address schema makes address types available in the customer schema.</span></span>  
  
 <span data-ttu-id="42de1-109">Le schéma d'adresse peut être incorporé à l'aide d'éléments `<xs:include />` ou `<xs:import />` pour utiliser les composants du schéma d'adresse tels quels, ou à l'aide d'un élément `<xs:redefine />` pour modifier l'un quelconque de ses composants en fonction des besoins du schéma utilisateur.</span><span class="sxs-lookup"><span data-stu-id="42de1-109">The address schema can be incorporated using either `<xs:include />` or `<xs:import />` elements to use the components of the address schema as-is, or using an `<xs:redefine />` element to modify any of its components to suit the need of the customer schema.</span></span> <span data-ttu-id="42de1-110">Le schéma d'adresse ayant un `targetNamespace` différent de celui du schéma utilisateur, on utilise l'élément `<xs:import />` et donc la sémantique d'importation.</span><span class="sxs-lookup"><span data-stu-id="42de1-110">Because the address schema has a `targetNamespace` that is different from that of the customer schema, the `<xs:import />` element and therefore import semantics is used.</span></span>  
  
 <span data-ttu-id="42de1-111">L'exemple de code inclut le schéma d'adresse en plusieurs étapes comme suit.</span><span class="sxs-lookup"><span data-stu-id="42de1-111">The code example includes the address schema in the following steps.</span></span>  
  
1. <span data-ttu-id="42de1-112">Il ajoute le schéma utilisateur et le schéma d'adresse à un nouvel objet <xref:System.Xml.Schema.XmlSchemaSet> puis les compile.</span><span class="sxs-lookup"><span data-stu-id="42de1-112">Adds the customer schema and the address schema to a new <xref:System.Xml.Schema.XmlSchemaSet> object and then compiles them.</span></span> <span data-ttu-id="42de1-113">Les avertissements et erreurs de validation de schéma éventuellement rencontrés pendant la lecture ou la compilation des schémas sont traités par le délégué <xref:System.Xml.Schema.ValidationEventHandler>.</span><span class="sxs-lookup"><span data-stu-id="42de1-113">Any schema validation warnings and errors encountered reading or compiling the schemas are handled by the <xref:System.Xml.Schema.ValidationEventHandler> delegate.</span></span>  
  
2. <span data-ttu-id="42de1-114">Il extrait les objets <xref:System.Xml.Schema.XmlSchema> compilés, tant pour le schéma utilisateur que pour le schéma d'adresse, de l'objet <xref:System.Xml.Schema.XmlSchemaSet> en effectuant une itération sur la propriété <xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A>.</span><span class="sxs-lookup"><span data-stu-id="42de1-114">Retrieves the compiled <xref:System.Xml.Schema.XmlSchema> objects for both the customer and address schemas from the <xref:System.Xml.Schema.XmlSchemaSet> by iterating over the <xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A> property.</span></span> <span data-ttu-id="42de1-115">Les schémas étant compilés, les propriétés PSCI (Post-Schema-Compilation-Infoset) sont accessibles.</span><span class="sxs-lookup"><span data-stu-id="42de1-115">Because the schemas are compiled, Post-Schema-Compilation-Infoset (PSCI) properties are accessible.</span></span>  
  
3. <span data-ttu-id="42de1-116">Il crée un objet <xref:System.Xml.Schema.XmlSchemaImport>, définit la propriété <xref:System.Xml.Schema.XmlSchemaImport.Namespace%2A> de l'importation comme étant l'espace de noms du schéma d'adresse, définit la propriété <xref:System.Xml.Schema.XmlSchemaExternal.Schema%2A> de l'importation comme étant l'objet <xref:System.Xml.Schema.XmlSchema> du schéma d'adresse et ajoute l'importation à la propriété <xref:System.Xml.Schema.XmlSchema.Includes%2A> du schéma utilisateur.</span><span class="sxs-lookup"><span data-stu-id="42de1-116">Creates an <xref:System.Xml.Schema.XmlSchemaImport> object, sets the <xref:System.Xml.Schema.XmlSchemaImport.Namespace%2A> property of the import to the namespace of the address schema, sets the <xref:System.Xml.Schema.XmlSchemaExternal.Schema%2A> property of the import to the <xref:System.Xml.Schema.XmlSchema> object of the address schema, and adds the import to the <xref:System.Xml.Schema.XmlSchema.Includes%2A> property of the customer schema.</span></span>  
  
4. <span data-ttu-id="42de1-117">Il retraite et compile l'objet <xref:System.Xml.Schema.XmlSchema> modifié du schéma utilisateur à l'aide des méthodes <xref:System.Xml.Schema.XmlSchemaSet.Reprocess%2A> et <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A> de la classe <xref:System.Xml.Schema.XmlSchemaSet> et écrit le résultat à la console.</span><span class="sxs-lookup"><span data-stu-id="42de1-117">Reprocesses and compiles the modified <xref:System.Xml.Schema.XmlSchema> object of the customer schema using the <xref:System.Xml.Schema.XmlSchemaSet.Reprocess%2A> and <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A> methods of the <xref:System.Xml.Schema.XmlSchemaSet> class and writes it to the console.</span></span>  
  
5. <span data-ttu-id="42de1-118">Enfin, de manière récursive, il écrit à la console tous les schémas importés dans le schéma utilisateur en utilisant la propriété <xref:System.Xml.Schema.XmlSchema.Includes%2A> du schéma utilisateur.</span><span class="sxs-lookup"><span data-stu-id="42de1-118">Finally, recursively writes all of the schemas imported into the customer schema to the console using the <xref:System.Xml.Schema.XmlSchema.Includes%2A> property of the customer schema.</span></span> <span data-ttu-id="42de1-119">La propriété <xref:System.Xml.Schema.XmlSchema.Includes%2A> fournit l'accès à toutes les inclusions, importations ou redéfinitions ajoutées à un schéma.</span><span class="sxs-lookup"><span data-stu-id="42de1-119">The <xref:System.Xml.Schema.XmlSchema.Includes%2A> property provides access to all the includes, imports, or redefines added to a schema.</span></span>  
  
 <span data-ttu-id="42de1-120">Voici l'exemple de code complet et les schémas utilisateur et d'adresse écrits à la console.</span><span class="sxs-lookup"><span data-stu-id="42de1-120">The following is the complete code example and the customer and address schemas written to the console.</span></span>  
  
 [!code-cpp[XmlSchemaImportExample#1](../../../../samples/snippets/cpp/VS_Snippets_Data/XmlSchemaImportExample/CPP/XmlSchemaImportExample.cpp#1)]
 [!code-csharp[XmlSchemaImportExample#1](../../../../samples/snippets/csharp/VS_Snippets_Data/XmlSchemaImportExample/CS/XmlSchemaImportExample.cs#1)]
 [!code-vb[XmlSchemaImportExample#1](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XmlSchemaImportExample/VB/XmlSchemaImportExample.vb#1)]  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<xs:schema xmlns:tns="http://www.tempuri.org" targetNamespace="http://www.tempuri.org" xmlns:xs="http://www.w3.org/2001/XMLSchema">  
  <xs:import namespace="http://www.example.com/IPO" />  
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
<schema targetNamespace="http://www.example.com/IPO" xmlns="http://www.w3.org/2001/XMLSchema" xmlns:ipo="http://www.example.com/IPO">  
  <annotation>  
    <documentation xml:lang="en">  
      Addresses for International Purchase order schema  
      Copyright 2000 Example.com. All rights reserved.  
    </documentation>  
  </annotation>  
  <complexType name="Address">  
    <sequence>  
      <element name="name"   type="string"/>  
      <element name="street" type="string"/>  
      <element name="city"   type="string"/>  
    </sequence>  
  </complexType>  
  <complexType name="USAddress">  
    <complexContent>  
      <extension base="ipo:Address">  
        <sequence>  
          <element name="state" type="ipo:USState"/>  
          <element name="zip"   type="positiveInteger"/>  
        </sequence>  
      </extension>  
    </complexContent>  
  </complexType>  
  <!-- other Address derivations for more countries or regions -->  
  <simpleType name="USState">  
    <restriction base="string">  
      <enumeration value="AK"/>  
      <enumeration value="AL"/>  
      <enumeration value="AR"/>  
      <!-- and so on ... -->  
    </restriction>  
  </simpleType>  
</schema>  
```  
  
 <span data-ttu-id="42de1-121">Pour plus d'informations sur les éléments `<xs:import />`, `<xs:include />` et `<xs:redefine />`, ainsi que sur les classes <xref:System.Xml.Schema.XmlSchemaImport>, <xref:System.Xml.Schema.XmlSchemaInclude> et <xref:System.Xml.Schema.XmlSchemaRedefine>, consultez [W3C XML Schema](https://www.w3.org/XML/Schema) (en anglais) et la documentation de référence de la classe d'espace de noms <xref:System.Xml.Schema?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="42de1-121">For more information about the `<xs:import />`, `<xs:include />`, and `<xs:redefine />` elements and the <xref:System.Xml.Schema.XmlSchemaImport>, <xref:System.Xml.Schema.XmlSchemaInclude> and <xref:System.Xml.Schema.XmlSchemaRedefine> classes, see the [W3C XML Schema](https://www.w3.org/XML/Schema) and the <xref:System.Xml.Schema?displayProperty=nameWithType> namespace class reference documentation.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="42de1-122">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="42de1-122">See also</span></span>

- [<span data-ttu-id="42de1-123">Vue d'ensemble du Modèle Objet du schéma XML</span><span class="sxs-lookup"><span data-stu-id="42de1-123">XML Schema Object Model Overview</span></span>](xml-schema-object-model-overview.md)
- [<span data-ttu-id="42de1-124">Lecture et écriture de schémas XML</span><span class="sxs-lookup"><span data-stu-id="42de1-124">Reading and Writing XML Schemas</span></span>](reading-and-writing-xml-schemas.md)
- [<span data-ttu-id="42de1-125">Création de schémas XML</span><span class="sxs-lookup"><span data-stu-id="42de1-125">Building XML Schemas</span></span>](building-xml-schemas.md)
- [<span data-ttu-id="42de1-126">Traversée de schémas XML</span><span class="sxs-lookup"><span data-stu-id="42de1-126">Traversing XML Schemas</span></span>](traversing-xml-schemas.md)
- [<span data-ttu-id="42de1-127">Modification de schémas XML</span><span class="sxs-lookup"><span data-stu-id="42de1-127">Editing XML Schemas</span></span>](editing-xml-schemas.md)
- [<span data-ttu-id="42de1-128">XmlSchemaSet pour la compilation de schémas</span><span class="sxs-lookup"><span data-stu-id="42de1-128">XmlSchemaSet for Schema Compilation</span></span>](xmlschemaset-for-schema-compilation.md)
