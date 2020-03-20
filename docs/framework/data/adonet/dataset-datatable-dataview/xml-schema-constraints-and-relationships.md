---
title: Contraintes et relations du schéma XML
ms.date: 03/30/2017
ms.assetid: 165bc2bc-60a1-40e0-9b89-7c68ef979079
ms.openlocfilehash: 2388d7c277ba1f01bea8d419e5aedf487b843ed7
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79150712"
---
# <a name="xml-schema-constraints-and-relationships"></a><span data-ttu-id="10925-102">Contraintes et relations du schéma XML</span><span class="sxs-lookup"><span data-stu-id="10925-102">XML Schema Constraints and Relationships</span></span>
<span data-ttu-id="10925-103">Dans un schéma de définition XML Schema (XSD), vous pouvez spécifier les contraintes (contraintes uniques, clés et keyref) et les relations (à l’aide de **l’annotation msdata:Relation).**</span><span class="sxs-lookup"><span data-stu-id="10925-103">In an XML Schema definition language (XSD) schema, you can specify constraints (unique, key, and keyref constraints) and relationships (using the **msdata:Relationship** annotation).</span></span> <span data-ttu-id="10925-104">Cette rubrique explique comment les contraintes et relations spécifiées dans un schéma XML sont interprétées pour générer l'objet <xref:System.Data.DataSet>.</span><span class="sxs-lookup"><span data-stu-id="10925-104">This topic explains how the constraints and relationships specified in an XML Schema are interpreted to generate the <xref:System.Data.DataSet>.</span></span>  
  
 <span data-ttu-id="10925-105">En général, dans un schéma XML, vous spécifiez **l’annotation msdata:Relation** si vous voulez générer uniquement des relations dans le **DataSet**.</span><span class="sxs-lookup"><span data-stu-id="10925-105">In general, in an XML Schema, you specify the **msdata:Relationship** annotation if you want to generate only relationships in the **DataSet**.</span></span> <span data-ttu-id="10925-106">Pour plus d’informations, voir [Generating DataSet Relations de XML Schema (XSD)](generating-dataset-relations-from-xml-schema-xsd.md).</span><span class="sxs-lookup"><span data-stu-id="10925-106">For more information, see [Generating DataSet Relations from XML Schema (XSD)](generating-dataset-relations-from-xml-schema-xsd.md).</span></span> <span data-ttu-id="10925-107">Vous spécifiez des contraintes (uniques, clés et keyref) si vous souhaitez générer des contraintes dans le **DataSet**.</span><span class="sxs-lookup"><span data-stu-id="10925-107">You specify constraints (unique, key, and keyref) if you want to generate constraints in the **DataSet**.</span></span> <span data-ttu-id="10925-108">Notez que les contraintes key et keyref peuvent aussi servir à générer des relations, comme expliqué plus loin dans cette rubrique.</span><span class="sxs-lookup"><span data-stu-id="10925-108">Note that the key and keyref constraints are also used to generate relationships, as explained later in this topic.</span></span>  
  
## <a name="generating-a-relationship-from-key-and-keyref-constraints"></a><span data-ttu-id="10925-109">Génération d'une relation à partir des contraintes key et keyref</span><span class="sxs-lookup"><span data-stu-id="10925-109">Generating a Relationship from key and keyref Constraints</span></span>  
 <span data-ttu-id="10925-110">Au lieu de spécifier **l’annotation msdata:Relation,** vous pouvez spécifier les contraintes clés et keyref, qui sont utilisés pendant le processus de cartographie XML Schema pour générer non seulement les contraintes, mais aussi la relation dans le **DataSet**.</span><span class="sxs-lookup"><span data-stu-id="10925-110">Instead of specifying the **msdata:Relationship** annotation, you can specify key and keyref constraints, which are used during the XML Schema mapping process to generate not only the constraints but also the relationship in the **DataSet**.</span></span> <span data-ttu-id="10925-111">Toutefois, si `msdata:ConstraintOnly="true"` vous spécifiez dans **l’élément keyref,** le **DataSet** n’inclura que les contraintes et n’inclura pas la relation.</span><span class="sxs-lookup"><span data-stu-id="10925-111">However, if you specify `msdata:ConstraintOnly="true"` in the **keyref** element, the **DataSet** will include only the constraints and will not include the relationship.</span></span>  
  
 <span data-ttu-id="10925-112">L’exemple suivant montre un schéma XML qui comprend des éléments **Order** et **OrderDetail,** qui ne sont pas imbriqués.</span><span class="sxs-lookup"><span data-stu-id="10925-112">The following example shows an XML Schema that includes **Order** and **OrderDetail** elements, which are not nested.</span></span> <span data-ttu-id="10925-113">Le schéma spécifie également des contraintes key et keyref.</span><span class="sxs-lookup"><span data-stu-id="10925-113">The schema also specifies key and keyref constraints.</span></span>  
  
```xml  
<xs:schema id="MyDataSet" xmlns=""
            xmlns:xs="http://www.w3.org/2001/XMLSchema"
            xmlns:msdata="urn:schemas-microsoft-com:xml-msdata">  
  
 <xs:element name="MyDataSet" msdata:IsDataSet="true">  
  <xs:complexType>  
    <xs:choice maxOccurs="unbounded">  
      <xs:element name="OrderDetail">  
       <xs:complexType>  
         <xs:sequence>  
           <xs:element name="OrderNo" type="xs:integer" />  
           <xs:element name="ItemNo" type="xs:string" />  
         </xs:sequence>  
       </xs:complexType>  
      </xs:element>  
      <xs:element name="Order">  
        <xs:complexType>  
          <xs:sequence>  
            <xs:element name="OrderNumber" type="xs:integer" />  
            <xs:element name="EmpNumber" type="xs:integer" />  
          </xs:sequence>  
        </xs:complexType>  
      </xs:element>  
    </xs:choice>  
  </xs:complexType>  
  
  <xs:key name="OrderNumberKey"  >  
    <xs:selector xpath=".//Order" />  
    <xs:field xpath="OrderNumber" />  
  </xs:key>  
  
  <xs:keyref name="OrderNoRef" refer="OrderNumberKey">  
    <xs:selector xpath=".//OrderDetail" />  
    <xs:field xpath="OrderNo" />  
  </xs:keyref>  
 </xs:element>  
</xs:schema>  
```  
  
 <span data-ttu-id="10925-114">Le **DataSet** généré au cours du processus de cartographie XML Schema comprend les tables **Order** et **OrderDetail.**</span><span class="sxs-lookup"><span data-stu-id="10925-114">The **DataSet** that is generated during the XML Schema mapping process includes the **Order** and **OrderDetail** tables.</span></span> <span data-ttu-id="10925-115">En outre, le **DataSet** inclut les relations et les contraintes.</span><span class="sxs-lookup"><span data-stu-id="10925-115">In addition, the **DataSet** includes relationships and constraints.</span></span> <span data-ttu-id="10925-116">L'exemple suivant illustre ces relations et contraintes.</span><span class="sxs-lookup"><span data-stu-id="10925-116">The following example shows these relationships and constraints.</span></span> <span data-ttu-id="10925-117">Notez que le schéma ne précise pas la **msdata:Annotation relationnelle;** au lieu de cela, les contraintes clés et keyref sont utilisées pour générer la relation.</span><span class="sxs-lookup"><span data-stu-id="10925-117">Note that the schema does not specify the **msdata:Relationship** annotation; instead, the key and keyref constraints are used to generate the relation.</span></span>  
  
```text
....ConstraintName: OrderNumberKey  
....Type: UniqueConstraint  
....Table: Order  
....Columns: OrderNumber  
....IsPrimaryKey: False  
  
....ConstraintName: OrderNoRef  
....Type: ForeignKeyConstraint  
....Table: OrderDetail  
....Columns: OrderNo  
....RelatedTable: Order  
....RelatedColumns: OrderNumber  
  
..RelationName: OrderNoRef  
..ParentTable: Order  
..ParentColumns: OrderNumber  
..ChildTable: OrderDetail  
..ChildColumns: OrderNo  
..ParentKeyConstraint: OrderNumberKey  
..ChildKeyConstraint: OrderNoRef  
..Nested: False  
```  
  
 <span data-ttu-id="10925-118">Dans l’exemple précédent du schéma, les éléments **Order** and **OrderDetail** ne sont pas imbriqués.</span><span class="sxs-lookup"><span data-stu-id="10925-118">In the previous schema example, the **Order** and **OrderDetail** elements are not nested.</span></span> <span data-ttu-id="10925-119">Ils le sont dans l'exemple qui suit.</span><span class="sxs-lookup"><span data-stu-id="10925-119">In the following schema example, these elements are nested.</span></span> <span data-ttu-id="10925-120">Cependant, aucune **msdata:** L’annotation relationnelle est spécifiée; par conséquent, une relation implicite est supposée.</span><span class="sxs-lookup"><span data-stu-id="10925-120">However, no **msdata:Relationship** annotation is specified; therefore, an implicit relation is assumed.</span></span> <span data-ttu-id="10925-121">Pour plus d’informations, voir [Map Implicit Relations Between Nested Schema Elements](map-implicit-relations-between-nested-schema-elements.md).</span><span class="sxs-lookup"><span data-stu-id="10925-121">For more information, see [Map Implicit Relations Between Nested Schema Elements](map-implicit-relations-between-nested-schema-elements.md).</span></span> <span data-ttu-id="10925-122">Le schéma spécifie également des contraintes key et keyref.</span><span class="sxs-lookup"><span data-stu-id="10925-122">The schema also specifies key and keyref constraints.</span></span>  
  
```xml  
<xs:schema id="MyDataSet" xmlns=""
            xmlns:xs="http://www.w3.org/2001/XMLSchema"
            xmlns:msdata="urn:schemas-microsoft-com:xml-msdata">  
  
 <xs:element name="MyDataSet" msdata:IsDataSet="true">  
  <xs:complexType>  
    <xs:choice maxOccurs="unbounded">  
  
      <xs:element name="Order">  
        <xs:complexType>  
          <xs:sequence>  
            <xs:element name="OrderNumber" type="xs:integer" />  
            <xs:element name="EmpNumber" type="xs:integer" />  
  
            <xs:element name="OrderDetail">  
              <xs:complexType>  
                <xs:sequence>  
                  <xs:element name="OrderNo" type="xs:integer" />  
                  <xs:element name="ItemNo" type="xs:string" />  
                </xs:sequence>  
              </xs:complexType>  
            </xs:element>  
          </xs:sequence>  
        </xs:complexType>  
      </xs:element>  
    </xs:choice>  
  </xs:complexType>  
  
  <xs:key name="OrderNumberKey"  >  
    <xs:selector xpath=".//Order" />  
    <xs:field xpath="OrderNumber" />  
  </xs:key>  
  
  <xs:keyref name="OrderNoRef" refer="OrderNumberKey">  
    <xs:selector xpath=".//OrderDetail" />  
    <xs:field xpath="OrderNo" />  
  </xs:keyref>  
 </xs:element>  
</xs:schema>  
```  
  
 <span data-ttu-id="10925-123">Le **DataSet** résultant du processus de cartographie XML Schema comprend deux tableaux :</span><span class="sxs-lookup"><span data-stu-id="10925-123">The **DataSet** resulting from the XML Schema mapping process includes two tables:</span></span>  
  
```text  
Order(OrderNumber, EmpNumber, Order_Id)  
OrderDetail(OrderNumber, ItemNumber, Order_Id)  
```  
  
 <span data-ttu-id="10925-124">Le **DataSet** comprend également les deux relations (l’une basée sur la **msdata:annotation relationnelle** et l’autre basée sur les contraintes clés et clés) et diverses contraintes.</span><span class="sxs-lookup"><span data-stu-id="10925-124">The **DataSet** also includes the two relationships (one based on the **msdata:relationship** annotation and the other based on the key and keyref constraints) and various constraints.</span></span> <span data-ttu-id="10925-125">L'exemple suivant illustre ces relations et contraintes.</span><span class="sxs-lookup"><span data-stu-id="10925-125">The following example shows the relations and constraints.</span></span>  
  
```text
..RelationName: Order_OrderDetail  
..ParentTable: Order  
..ParentColumns: Order_Id  
..ChildTable: OrderDetail  
..ChildColumns: Order_Id  
..ParentKeyConstraint: Constraint1  
..ChildKeyConstraint: Order_OrderDetail  
..Nested: True  
  
..RelationName: OrderNoRef  
..ParentTable: Order  
..ParentColumns: OrderNumber  
..ChildTable: OrderDetail  
..ChildColumns: OrderNo  
..ParentKeyConstraint: OrderNumberKey  
..ChildKeyConstraint: OrderNoRef  
..Nested: False  
  
..ConstraintName: OrderNumberKey  
..Type: UniqueConstraint  
..Table: Order  
..Columns: OrderNumber  
..IsPrimaryKey: False  
  
..ConstraintName: Constraint1  
..Type: UniqueConstraint  
..Table: Order  
..Columns: Order_Id  
..IsPrimaryKey: True  
  
..ConstraintName: Order_OrderDetail  
..Type: ForeignKeyConstraint  
..Table: OrderDetail  
..Columns: Order_Id  
..RelatedTable: Order  
..RelatedColumns: Order_Id  
  
..ConstraintName: OrderNoRef  
..Type: ForeignKeyConstraint  
..Table: OrderDetail  
..Columns: OrderNo  
..RelatedTable: Order  
..RelatedColumns: OrderNumber  
```  
  
 <span data-ttu-id="10925-126">Si une contrainte de clé se référant à une table imbriquée contient **l’annotation msdata:IsNestedMD "vrai",** le **DataSet** créera une seule relation imbriquée qui est basée sur la contrainte keyref et la contrainte unique/clé connexe.</span><span class="sxs-lookup"><span data-stu-id="10925-126">If a keyref constraint referring to a nested table contains the **msdata:IsNested="true"** annotation, the **DataSet** will create a single nested relationship that is based on the keyref constraint and the related unique/key constraint.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="10925-127">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="10925-127">See also</span></span>

- [<span data-ttu-id="10925-128">Dérivation de la structure relationnelle des DataSet à partir du schéma XML (XSD)</span><span class="sxs-lookup"><span data-stu-id="10925-128">Deriving DataSet Relational Structure from XML Schema (XSD)</span></span>](deriving-dataset-relational-structure-from-xml-schema-xsd.md)
- [<span data-ttu-id="10925-129">Vue d'ensemble d’ADO.NET</span><span class="sxs-lookup"><span data-stu-id="10925-129">ADO.NET Overview</span></span>](../ado-net-overview.md)
