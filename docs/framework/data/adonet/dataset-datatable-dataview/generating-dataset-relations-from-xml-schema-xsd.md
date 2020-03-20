---
title: Génération de relations de DataSet à partir du schéma XML (XSD)
ms.date: 03/30/2017
ms.assetid: 1c9a1413-c0d2-4447-88ba-9a2b0cbc0aa8
ms.openlocfilehash: feb0be7f66bf0f407e54ef0830c13f0c4a8a6418
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79151128"
---
# <a name="generating-dataset-relations-from-xml-schema-xsd"></a><span data-ttu-id="0fb81-102">Génération de relations de DataSet à partir du schéma XML (XSD)</span><span class="sxs-lookup"><span data-stu-id="0fb81-102">Generating DataSet Relations from XML Schema (XSD)</span></span>
<span data-ttu-id="0fb81-103">Dans un objet <xref:System.Data.DataSet>, vous créez une association entre deux ou plusieurs colonnes en établissant une relation parent-enfant.</span><span class="sxs-lookup"><span data-stu-id="0fb81-103">In a <xref:System.Data.DataSet>, you form an association between two or more columns by creating a parent-child relation.</span></span> <span data-ttu-id="0fb81-104">Il existe trois façons de représenter une relation **DataSet** dans un schéma de définition XML Schema (XSD) :</span><span class="sxs-lookup"><span data-stu-id="0fb81-104">There are three ways to represent a **DataSet** relation within an XML Schema definition language (XSD) schema:</span></span>  
  
- <span data-ttu-id="0fb81-105">spécifier des types complexes imbriqués ;</span><span class="sxs-lookup"><span data-stu-id="0fb81-105">Specify nested complex types.</span></span>  
  
- <span data-ttu-id="0fb81-106">Utilisez l’annotation **msdata:Relation.**</span><span class="sxs-lookup"><span data-stu-id="0fb81-106">Use the **msdata:Relationship** annotation.</span></span>  
  
- <span data-ttu-id="0fb81-107">Spécifier un **xs:keyref** sans la **msdata:ConstraintOnly** annotation.</span><span class="sxs-lookup"><span data-stu-id="0fb81-107">Specify an **xs:keyref** without the **msdata:ConstraintOnly** annotation.</span></span>  
  
## <a name="nested-complex-types"></a><span data-ttu-id="0fb81-108">Types complexes imbriqués</span><span class="sxs-lookup"><span data-stu-id="0fb81-108">Nested Complex Types</span></span>  
 <span data-ttu-id="0fb81-109">Les définitions de types complexes imbriqués dans un schéma indiquent les relations parent-enfant des éléments.</span><span class="sxs-lookup"><span data-stu-id="0fb81-109">Nested complex type definitions in a schema indicate the parent-child relationships of the elements.</span></span> <span data-ttu-id="0fb81-110">Le fragment XML Schema suivant montre que **OrderDetail** est un élément enfant de l’élément **De l’Ordre.**</span><span class="sxs-lookup"><span data-stu-id="0fb81-110">The following XML Schema fragment shows that **OrderDetail** is a child element of the **Order** element.</span></span>  
  
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
  
 <span data-ttu-id="0fb81-111">Le processus de cartographie XML Schema crée des tables dans le **DataSet** qui correspondent aux types complexes imbriqués dans le schéma.</span><span class="sxs-lookup"><span data-stu-id="0fb81-111">The XML Schema mapping process creates tables in the **DataSet** that correspond to the nested complex types in the schema.</span></span> <span data-ttu-id="0fb81-112">Il crée également des colonnes**-** supplémentaires qui sont utilisées comme colonnes d’enfant parent pour les tables générées.</span><span class="sxs-lookup"><span data-stu-id="0fb81-112">It also creates additional columns that are used as parent**-** child columns for the generated tables.</span></span> <span data-ttu-id="0fb81-113">Notez que**-** ces colonnes d’enfants parents spécifient les relations, ce qui n’est pas la même chose que de spécifier les contraintes clés principales primaires/étrangères.</span><span class="sxs-lookup"><span data-stu-id="0fb81-113">Note that these parent**-** child columns specify relationships, which is not the same as specifying primary key/foreign key constraints.</span></span>  
  
## <a name="msdatarelationship-annotation"></a><span data-ttu-id="0fb81-114">Annotation msdata:Relationship</span><span class="sxs-lookup"><span data-stu-id="0fb81-114">msdata:Relationship Annotation</span></span>  
 <span data-ttu-id="0fb81-115">L’annotation **msdata:Relation** vous permet de spécifier explicitement les relations parent-enfant entre les éléments du schéma qui ne sont pas imbriqués.</span><span class="sxs-lookup"><span data-stu-id="0fb81-115">The **msdata:Relationship** annotation allows you to explicitly specify parent-child relationships between elements in the schema that are not nested.</span></span> <span data-ttu-id="0fb81-116">L’exemple suivant montre la structure de l’élément **relationnel.**</span><span class="sxs-lookup"><span data-stu-id="0fb81-116">The following example shows the structure of the **Relationship** element.</span></span>  
  
```xml  
<msdata:Relationship name="CustOrderRelationship"
msdata:parent=""
msdata:child=""
msdata:parentkey=""
msdata:childkey="" />  
```  
  
 <span data-ttu-id="0fb81-117">Les attributs de l’annotation **msdata:Relation** identifient les éléments impliqués dans la relation parent-enfant, ainsi que les éléments **parentkey** et **childkey** et les attributs impliqués dans la relation.</span><span class="sxs-lookup"><span data-stu-id="0fb81-117">The attributes of the **msdata:Relationship** annotation identify the elements involved in the parent-child relationship, as well as the **parentkey** and **childkey** elements and attributes involved in the relationship.</span></span> <span data-ttu-id="0fb81-118">Le processus de cartographie utilise ces informations pour générer des tableaux dans le **DataSet** et pour créer la principale relation clé clé/étrangère entre ces tables.</span><span class="sxs-lookup"><span data-stu-id="0fb81-118">The mapping process uses this information to generate tables in the **DataSet** and to create the primary key/foreign key relationship between these tables.</span></span>  
  
 <span data-ttu-id="0fb81-119">Par exemple, le fragment de schéma suivant spécifie les éléments **de l’Ordre** et **de l’Ordre à** la même échelle (non imbriqués).</span><span class="sxs-lookup"><span data-stu-id="0fb81-119">For example, the following schema fragment specifies **Order** and **OrderDetail** elements at the same level (not nested).</span></span> <span data-ttu-id="0fb81-120">Le schéma spécifie une **msdata:Relationship** annotation, qui spécifie la relation parent-enfant entre ces deux éléments.</span><span class="sxs-lookup"><span data-stu-id="0fb81-120">The schema specifies an **msdata:Relationship** annotation, which specifies the parent-child relationship between these two elements.</span></span> <span data-ttu-id="0fb81-121">Dans ce cas, une relation explicite doit être spécifiée à l’aide de **l’annotation msdata:Relation.**</span><span class="sxs-lookup"><span data-stu-id="0fb81-121">In this case, an explicit relationship must be specified using the **msdata:Relationship** annotation.</span></span>  
  
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
  
 <span data-ttu-id="0fb81-122">Le processus de cartographie utilise **l’élément relationnel** pour créer une relation parent-enfant entre la colonne **OrderNumber** dans le tableau **de l’Ordre** et la colonne **OrderNo** dans le tableau **OrderDetail** dans le **DataSet**.</span><span class="sxs-lookup"><span data-stu-id="0fb81-122">The mapping process uses the **Relationship** element to create a parent-child relationship between the **OrderNumber** column in the **Order** table and the **OrderNo** column in the **OrderDetail** table in the **DataSet**.</span></span> <span data-ttu-id="0fb81-123">Il ne spécifie que la relation ; il ne spécifie pas automatiquement de contraintes sur les valeurs de ces colonnes comme le font des contraintes de clé primaire/clé étrangère dans des bases de données relationnelles.</span><span class="sxs-lookup"><span data-stu-id="0fb81-123">The mapping process only specifies the relationship; it does not automatically specify any constraints on the values in these columns, as do the primary key/foreign key constraints in relational databases.</span></span>  
  
### <a name="in-this-section"></a><span data-ttu-id="0fb81-124">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="0fb81-124">In This Section</span></span>  
 [<span data-ttu-id="0fb81-125">Mapper les relations implicites entre éléments de schéma imbriqués</span><span class="sxs-lookup"><span data-stu-id="0fb81-125">Map Implicit Relations Between Nested Schema Elements</span></span>](map-implicit-relations-between-nested-schema-elements.md)  
 <span data-ttu-id="0fb81-126">Décrit les contraintes et les relations qui sont implicitement créées dans un **ensemble de données** lorsque des éléments imbriqués sont rencontrés dans XML Schema.</span><span class="sxs-lookup"><span data-stu-id="0fb81-126">Describes the constraints and relations that are implicitly created in a **DataSet** when nested elements are encountered in XML Schema.</span></span>  
  
 [<span data-ttu-id="0fb81-127">Mapper les relations spécifiées pour les éléments imbriqués</span><span class="sxs-lookup"><span data-stu-id="0fb81-127">Map Relations Specified for Nested Elements</span></span>](map-relations-specified-for-nested-elements.md)  
 <span data-ttu-id="0fb81-128">Décrit comment définir explicitement les relations dans un **DataSet** pour les éléments imbriqués dans XML Schema.</span><span class="sxs-lookup"><span data-stu-id="0fb81-128">Describes how to explicitly set relations in a **DataSet** for nested elements in XML Schema.</span></span>  
  
 [<span data-ttu-id="0fb81-129">Spécifier les relations entre éléments sans imbrication</span><span class="sxs-lookup"><span data-stu-id="0fb81-129">Specify Relations Between Elements with No Nesting</span></span>](specify-relations-between-elements-with-no-nesting.md)  
 <span data-ttu-id="0fb81-130">Décrit comment créer des relations dans un **ensemble de données** entre les éléments XML Schema qui ne sont pas imbriqués.</span><span class="sxs-lookup"><span data-stu-id="0fb81-130">Describes how to create relations in a **DataSet** between XML Schema elements that are not nested.</span></span>  
  
### <a name="related-sections"></a><span data-ttu-id="0fb81-131">Sections connexes</span><span class="sxs-lookup"><span data-stu-id="0fb81-131">Related Sections</span></span>  
 [<span data-ttu-id="0fb81-132">Dérivation de la structure relationnelle des DataSet à partir du schéma XML (XSD)</span><span class="sxs-lookup"><span data-stu-id="0fb81-132">Deriving DataSet Relational Structure from XML Schema (XSD)</span></span>](deriving-dataset-relational-structure-from-xml-schema-xsd.md)  
 <span data-ttu-id="0fb81-133">Décrit la structure relationnelle, ou schéma, d’un **DataSet** qui est créé à partir de XML Schema langage de définition (XSD) schéma.</span><span class="sxs-lookup"><span data-stu-id="0fb81-133">Describes the relational structure, or schema, of a **DataSet** that is created from XML Schema definition language (XSD) schema.</span></span>  
  
 [<span data-ttu-id="0fb81-134">Mappage des contraintes de schéma XML (XSD) aux contraintes de DataSet</span><span class="sxs-lookup"><span data-stu-id="0fb81-134">Mapping XML Schema (XSD) Constraints to DataSet Constraints</span></span>](mapping-xml-schema-xsd-constraints-to-dataset-constraints.md)  
 <span data-ttu-id="0fb81-135">Décrit les éléments XML Schema utilisés pour créer des contraintes clés uniques et étrangères dans un **DataSet**.</span><span class="sxs-lookup"><span data-stu-id="0fb81-135">Describes the XML Schema elements used to create unique and foreign key constraints in a **DataSet**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0fb81-136">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="0fb81-136">See also</span></span>

- [<span data-ttu-id="0fb81-137">Vue d'ensemble d’ADO.NET</span><span class="sxs-lookup"><span data-stu-id="0fb81-137">ADO.NET Overview</span></span>](../ado-net-overview.md)
