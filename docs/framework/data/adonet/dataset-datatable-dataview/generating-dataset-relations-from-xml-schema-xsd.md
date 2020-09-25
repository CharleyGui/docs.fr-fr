---
title: Génération de relations de DataSet à partir du schéma XML (XSD)
ms.date: 03/30/2017
ms.assetid: 1c9a1413-c0d2-4447-88ba-9a2b0cbc0aa8
ms.openlocfilehash: 2673280ebb94dcc10c130f3969f3e3250d3706a2
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91198585"
---
# <a name="generating-dataset-relations-from-xml-schema-xsd"></a><span data-ttu-id="2e432-102">Génération de relations de DataSet à partir du schéma XML (XSD)</span><span class="sxs-lookup"><span data-stu-id="2e432-102">Generating DataSet Relations from XML Schema (XSD)</span></span>

<span data-ttu-id="2e432-103">Dans un objet <xref:System.Data.DataSet>, vous créez une association entre deux ou plusieurs colonnes en établissant une relation parent-enfant.</span><span class="sxs-lookup"><span data-stu-id="2e432-103">In a <xref:System.Data.DataSet>, you form an association between two or more columns by creating a parent-child relation.</span></span> <span data-ttu-id="2e432-104">Il existe trois façons de représenter une relation de **DataSet** dans un schéma en langage XSD (XML Schema Definition) :</span><span class="sxs-lookup"><span data-stu-id="2e432-104">There are three ways to represent a **DataSet** relation within an XML Schema definition language (XSD) schema:</span></span>  
  
- <span data-ttu-id="2e432-105">spécifier des types complexes imbriqués ;</span><span class="sxs-lookup"><span data-stu-id="2e432-105">Specify nested complex types.</span></span>  
  
- <span data-ttu-id="2e432-106">Utilisez l’annotation **msdata : Relationship** .</span><span class="sxs-lookup"><span data-stu-id="2e432-106">Use the **msdata:Relationship** annotation.</span></span>  
  
- <span data-ttu-id="2e432-107">Spécifiez un **XS : keyref** sans l’annotation **msdata : ConstraintOnly** .</span><span class="sxs-lookup"><span data-stu-id="2e432-107">Specify an **xs:keyref** without the **msdata:ConstraintOnly** annotation.</span></span>  
  
## <a name="nested-complex-types"></a><span data-ttu-id="2e432-108">Types complexes imbriqués</span><span class="sxs-lookup"><span data-stu-id="2e432-108">Nested Complex Types</span></span>  

 <span data-ttu-id="2e432-109">Les définitions de types complexes imbriqués dans un schéma indiquent les relations parent-enfant des éléments.</span><span class="sxs-lookup"><span data-stu-id="2e432-109">Nested complex type definitions in a schema indicate the parent-child relationships of the elements.</span></span> <span data-ttu-id="2e432-110">Le fragment de schéma XML suivant montre que **OrderDetail** est un élément enfant de l’élément **Order** .</span><span class="sxs-lookup"><span data-stu-id="2e432-110">The following XML Schema fragment shows that **OrderDetail** is a child element of the **Order** element.</span></span>  
  
```xml  
<xs:element name="Order">  
  <xs:complexType>  
     <xs:sequence>
       <xs:element name="OrderDetail" />  
           <xs:complexType>
           </xs:complexType>  
     </xs:sequence>  
  </xs:complexType>  
</xs:element>  
```  
  
 <span data-ttu-id="2e432-111">Le processus de mappage de schéma XML crée dans le **DataSet** des tables qui correspondent aux types complexes imbriqués dans le schéma.</span><span class="sxs-lookup"><span data-stu-id="2e432-111">The XML Schema mapping process creates tables in the **DataSet** that correspond to the nested complex types in the schema.</span></span> <span data-ttu-id="2e432-112">Il crée également des colonnes supplémentaires qui sont utilisées comme **-** colonnes enfants parentes pour les tables générées.</span><span class="sxs-lookup"><span data-stu-id="2e432-112">It also creates additional columns that are used as parent**-** child columns for the generated tables.</span></span> <span data-ttu-id="2e432-113">Notez que ces **-** colonnes enfants parentes spécifient des relations, ce qui n’est pas le même que la spécification de contraintes de clé primaire/clé étrangère.</span><span class="sxs-lookup"><span data-stu-id="2e432-113">Note that these parent**-** child columns specify relationships, which is not the same as specifying primary key/foreign key constraints.</span></span>  
  
## <a name="msdatarelationship-annotation"></a><span data-ttu-id="2e432-114">Annotation msdata:Relationship</span><span class="sxs-lookup"><span data-stu-id="2e432-114">msdata:Relationship Annotation</span></span>  

 <span data-ttu-id="2e432-115">L’annotation **msdata : Relationship** vous permet de spécifier explicitement les relations parent-enfant entre les éléments du schéma qui ne sont pas imbriqués.</span><span class="sxs-lookup"><span data-stu-id="2e432-115">The **msdata:Relationship** annotation allows you to explicitly specify parent-child relationships between elements in the schema that are not nested.</span></span> <span data-ttu-id="2e432-116">L’exemple suivant illustre la structure de l’élément **Relationship** .</span><span class="sxs-lookup"><span data-stu-id="2e432-116">The following example shows the structure of the **Relationship** element.</span></span>  
  
```xml  
<msdata:Relationship name="CustOrderRelationship"
msdata:parent=""
msdata:child=""
msdata:parentkey=""
msdata:childkey="" />  
```  
  
 <span data-ttu-id="2e432-117">Les attributs de l’annotation **msdata : Relationship** identifient les éléments impliqués dans la relation parent-enfant, ainsi que les éléments et attributs **ParentKey** et **childkey** impliqués dans la relation.</span><span class="sxs-lookup"><span data-stu-id="2e432-117">The attributes of the **msdata:Relationship** annotation identify the elements involved in the parent-child relationship, as well as the **parentkey** and **childkey** elements and attributes involved in the relationship.</span></span> <span data-ttu-id="2e432-118">Le processus de mappage utilise ces informations pour générer des tables dans le **jeu de données** et pour créer la relation clé primaire/clé étrangère entre ces tables.</span><span class="sxs-lookup"><span data-stu-id="2e432-118">The mapping process uses this information to generate tables in the **DataSet** and to create the primary key/foreign key relationship between these tables.</span></span>  
  
 <span data-ttu-id="2e432-119">Par exemple, le fragment de schéma suivant spécifie les éléments **Order** et **OrderDetail** au même niveau (non imbriqué).</span><span class="sxs-lookup"><span data-stu-id="2e432-119">For example, the following schema fragment specifies **Order** and **OrderDetail** elements at the same level (not nested).</span></span> <span data-ttu-id="2e432-120">Le schéma spécifie une annotation **msdata : Relationship** , qui spécifie la relation parent-enfant entre ces deux éléments.</span><span class="sxs-lookup"><span data-stu-id="2e432-120">The schema specifies an **msdata:Relationship** annotation, which specifies the parent-child relationship between these two elements.</span></span> <span data-ttu-id="2e432-121">Dans ce cas, une relation explicite doit être spécifiée à l’aide de l’annotation **msdata : Relationship** .</span><span class="sxs-lookup"><span data-stu-id="2e432-121">In this case, an explicit relationship must be specified using the **msdata:Relationship** annotation.</span></span>  
  
```xml  
 <xs:element name="MyDataSet" msdata:IsDataSet="true">  
  <xs:complexType>  
    <xs:choice maxOccurs="unbounded">  
        <xs:element name="OrderDetail">  
          <xs:complexType>  
  
          </xs:complexType>  
       </xs:element>  
       <xs:element name="Order">  
          <xs:complexType>  
  
          </xs:complexType>  
       </xs:element>  
    </xs:choice>  
  </xs:complexType>  
</xs:element>  
   <xs:annotation>  
     <xs:appinfo>  
       <msdata:Relationship name="OrdOrdDetailRelation"  
          msdata:parent="Order"  
          msdata:child="OrderDetail"
          msdata:parentkey="OrderNumber"  
          msdata:childkey="OrderNo"/>  
     </xs:appinfo>  
  </xs:annotation>  
```  
  
 <span data-ttu-id="2e432-122">Le processus de mappage utilise l’élément **Relationship** pour créer une relation parent-enfant entre la colonne **OrderNumber** de la table **Order** et la colonne **OrderNo** de la table **OrderDetail** du **DataSet**.</span><span class="sxs-lookup"><span data-stu-id="2e432-122">The mapping process uses the **Relationship** element to create a parent-child relationship between the **OrderNumber** column in the **Order** table and the **OrderNo** column in the **OrderDetail** table in the **DataSet**.</span></span> <span data-ttu-id="2e432-123">Il ne spécifie que la relation ; il ne spécifie pas automatiquement de contraintes sur les valeurs de ces colonnes comme le font des contraintes de clé primaire/clé étrangère dans des bases de données relationnelles.</span><span class="sxs-lookup"><span data-stu-id="2e432-123">The mapping process only specifies the relationship; it does not automatically specify any constraints on the values in these columns, as do the primary key/foreign key constraints in relational databases.</span></span>  
  
### <a name="in-this-section"></a><span data-ttu-id="2e432-124">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="2e432-124">In This Section</span></span>  

 [<span data-ttu-id="2e432-125">Mapper les relations implicites entre éléments de schéma imbriqués</span><span class="sxs-lookup"><span data-stu-id="2e432-125">Map Implicit Relations Between Nested Schema Elements</span></span>](map-implicit-relations-between-nested-schema-elements.md)  
 <span data-ttu-id="2e432-126">Décrit les contraintes et les relations qui sont créées implicitement dans un **DataSet** lorsque des éléments imbriqués sont rencontrés dans le schéma XML.</span><span class="sxs-lookup"><span data-stu-id="2e432-126">Describes the constraints and relations that are implicitly created in a **DataSet** when nested elements are encountered in XML Schema.</span></span>  
  
 [<span data-ttu-id="2e432-127">Mapper les relations spécifiées pour les éléments imbriqués</span><span class="sxs-lookup"><span data-stu-id="2e432-127">Map Relations Specified for Nested Elements</span></span>](map-relations-specified-for-nested-elements.md)  
 <span data-ttu-id="2e432-128">Décrit comment définir explicitement des relations dans un **DataSet** pour les éléments imbriqués dans le schéma XML.</span><span class="sxs-lookup"><span data-stu-id="2e432-128">Describes how to explicitly set relations in a **DataSet** for nested elements in XML Schema.</span></span>  
  
 [<span data-ttu-id="2e432-129">Spécifier les relations entre éléments sans imbrication</span><span class="sxs-lookup"><span data-stu-id="2e432-129">Specify Relations Between Elements with No Nesting</span></span>](specify-relations-between-elements-with-no-nesting.md)  
 <span data-ttu-id="2e432-130">Décrit comment créer des relations dans un **DataSet** entre des éléments de schéma XML qui ne sont pas imbriqués.</span><span class="sxs-lookup"><span data-stu-id="2e432-130">Describes how to create relations in a **DataSet** between XML Schema elements that are not nested.</span></span>  
  
### <a name="related-sections"></a><span data-ttu-id="2e432-131">Sections connexes</span><span class="sxs-lookup"><span data-stu-id="2e432-131">Related Sections</span></span>  

 [<span data-ttu-id="2e432-132">Dérivation de la structure relationnelle des DataSet à partir du schéma XML (XSD)</span><span class="sxs-lookup"><span data-stu-id="2e432-132">Deriving DataSet Relational Structure from XML Schema (XSD)</span></span>](deriving-dataset-relational-structure-from-xml-schema-xsd.md)  
 <span data-ttu-id="2e432-133">Décrit la structure relationnelle, ou schéma, d’un **DataSet** créé à partir du schéma en langage XSD (XML Schema Definition).</span><span class="sxs-lookup"><span data-stu-id="2e432-133">Describes the relational structure, or schema, of a **DataSet** that is created from XML Schema definition language (XSD) schema.</span></span>  
  
 [<span data-ttu-id="2e432-134">Mappage des contraintes de schéma XML (XSD) aux contraintes de DataSet</span><span class="sxs-lookup"><span data-stu-id="2e432-134">Mapping XML Schema (XSD) Constraints to DataSet Constraints</span></span>](mapping-xml-schema-xsd-constraints-to-dataset-constraints.md)  
 <span data-ttu-id="2e432-135">Décrit les éléments de schéma XML utilisés pour créer des contraintes de clé étrangère et uniques dans un **DataSet**.</span><span class="sxs-lookup"><span data-stu-id="2e432-135">Describes the XML Schema elements used to create unique and foreign key constraints in a **DataSet**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2e432-136">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2e432-136">See also</span></span>

- [<span data-ttu-id="2e432-137">Vue d'ensemble d’ADO.NET</span><span class="sxs-lookup"><span data-stu-id="2e432-137">ADO.NET Overview</span></span>](../ado-net-overview.md)
