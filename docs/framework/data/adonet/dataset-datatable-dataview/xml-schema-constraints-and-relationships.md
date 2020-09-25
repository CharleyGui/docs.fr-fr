---
title: Contraintes et relations du schéma XML
ms.date: 03/30/2017
ms.assetid: 165bc2bc-60a1-40e0-9b89-7c68ef979079
ms.openlocfilehash: 5861386e42defa189aaa50a3af0bd95d7e9257fd
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91173703"
---
# <a name="xml-schema-constraints-and-relationships"></a><span data-ttu-id="1d59d-102">Contraintes et relations du schéma XML</span><span class="sxs-lookup"><span data-stu-id="1d59d-102">XML Schema Constraints and Relationships</span></span>

<span data-ttu-id="1d59d-103">Dans un schéma en langage XSD (XML Schema Definition), vous pouvez spécifier des contraintes (unique, Key et keyref) et des relations (à l’aide de l’annotation **msdata : Relationship** ).</span><span class="sxs-lookup"><span data-stu-id="1d59d-103">In an XML Schema definition language (XSD) schema, you can specify constraints (unique, key, and keyref constraints) and relationships (using the **msdata:Relationship** annotation).</span></span> <span data-ttu-id="1d59d-104">Cette rubrique explique comment les contraintes et relations spécifiées dans un schéma XML sont interprétées pour générer l'objet <xref:System.Data.DataSet>.</span><span class="sxs-lookup"><span data-stu-id="1d59d-104">This topic explains how the constraints and relationships specified in an XML Schema are interpreted to generate the <xref:System.Data.DataSet>.</span></span>  
  
 <span data-ttu-id="1d59d-105">En général, dans un schéma XML, vous spécifiez l’annotation **msdata : Relationship** si vous souhaitez générer uniquement des relations dans le **DataSet**.</span><span class="sxs-lookup"><span data-stu-id="1d59d-105">In general, in an XML Schema, you specify the **msdata:Relationship** annotation if you want to generate only relationships in the **DataSet**.</span></span> <span data-ttu-id="1d59d-106">Pour plus d’informations, consultez [génération de relations de DataSet à partir d’un schéma XML (XSD)](generating-dataset-relations-from-xml-schema-xsd.md).</span><span class="sxs-lookup"><span data-stu-id="1d59d-106">For more information, see [Generating DataSet Relations from XML Schema (XSD)](generating-dataset-relations-from-xml-schema-xsd.md).</span></span> <span data-ttu-id="1d59d-107">Vous spécifiez des contraintes (unique, Key et keyref) si vous souhaitez générer des contraintes dans le **DataSet**.</span><span class="sxs-lookup"><span data-stu-id="1d59d-107">You specify constraints (unique, key, and keyref) if you want to generate constraints in the **DataSet**.</span></span> <span data-ttu-id="1d59d-108">Notez que les contraintes key et keyref peuvent aussi servir à générer des relations, comme expliqué plus loin dans cette rubrique.</span><span class="sxs-lookup"><span data-stu-id="1d59d-108">Note that the key and keyref constraints are also used to generate relationships, as explained later in this topic.</span></span>  
  
## <a name="generating-a-relationship-from-key-and-keyref-constraints"></a><span data-ttu-id="1d59d-109">Génération d'une relation à partir des contraintes key et keyref</span><span class="sxs-lookup"><span data-stu-id="1d59d-109">Generating a Relationship from key and keyref Constraints</span></span>  

 <span data-ttu-id="1d59d-110">Au lieu de spécifier l’annotation **msdata : Relationship** , vous pouvez spécifier des contraintes Key et keyref, qui sont utilisées pendant le processus de mappage du schéma XML pour générer non seulement les contraintes, mais également la relation dans le **DataSet**.</span><span class="sxs-lookup"><span data-stu-id="1d59d-110">Instead of specifying the **msdata:Relationship** annotation, you can specify key and keyref constraints, which are used during the XML Schema mapping process to generate not only the constraints but also the relationship in the **DataSet**.</span></span> <span data-ttu-id="1d59d-111">Toutefois, si vous spécifiez `msdata:ConstraintOnly="true"` dans l’élément **keyref** , le **DataSet** inclut uniquement les contraintes et n’inclut pas la relation.</span><span class="sxs-lookup"><span data-stu-id="1d59d-111">However, if you specify `msdata:ConstraintOnly="true"` in the **keyref** element, the **DataSet** will include only the constraints and will not include the relationship.</span></span>  
  
 <span data-ttu-id="1d59d-112">L’exemple suivant illustre un schéma XML qui comprend des éléments **Order** et **OrderDetail** , qui ne sont pas imbriqués.</span><span class="sxs-lookup"><span data-stu-id="1d59d-112">The following example shows an XML Schema that includes **Order** and **OrderDetail** elements, which are not nested.</span></span> <span data-ttu-id="1d59d-113">Le schéma spécifie également des contraintes key et keyref.</span><span class="sxs-lookup"><span data-stu-id="1d59d-113">The schema also specifies key and keyref constraints.</span></span>  
  
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
  
 <span data-ttu-id="1d59d-114">Le **DataSet** généré pendant le processus de mappage du schéma XML comprend les tables **Order** et **OrderDetail** .</span><span class="sxs-lookup"><span data-stu-id="1d59d-114">The **DataSet** that is generated during the XML Schema mapping process includes the **Order** and **OrderDetail** tables.</span></span> <span data-ttu-id="1d59d-115">En outre, le **DataSet** comprend des relations et des contraintes.</span><span class="sxs-lookup"><span data-stu-id="1d59d-115">In addition, the **DataSet** includes relationships and constraints.</span></span> <span data-ttu-id="1d59d-116">L'exemple suivant illustre ces relations et contraintes.</span><span class="sxs-lookup"><span data-stu-id="1d59d-116">The following example shows these relationships and constraints.</span></span> <span data-ttu-id="1d59d-117">Notez que le schéma ne spécifie pas l’annotation **msdata : Relationship** ; au lieu de cela, les contraintes Key et keyref sont utilisées pour générer la relation.</span><span class="sxs-lookup"><span data-stu-id="1d59d-117">Note that the schema does not specify the **msdata:Relationship** annotation; instead, the key and keyref constraints are used to generate the relation.</span></span>  
  
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
  
 <span data-ttu-id="1d59d-118">Dans l’exemple de schéma précédent, les éléments **Order** et **OrderDetail** ne sont pas imbriqués.</span><span class="sxs-lookup"><span data-stu-id="1d59d-118">In the previous schema example, the **Order** and **OrderDetail** elements are not nested.</span></span> <span data-ttu-id="1d59d-119">Ils le sont dans l'exemple qui suit.</span><span class="sxs-lookup"><span data-stu-id="1d59d-119">In the following schema example, these elements are nested.</span></span> <span data-ttu-id="1d59d-120">Toutefois, aucune annotation **msdata : Relationship** n’est spécifiée ; par conséquent, une relation implicite est supposée.</span><span class="sxs-lookup"><span data-stu-id="1d59d-120">However, no **msdata:Relationship** annotation is specified; therefore, an implicit relation is assumed.</span></span> <span data-ttu-id="1d59d-121">Pour plus d’informations, consultez [mapper les relations implicites entre les éléments de schéma imbriqués](map-implicit-relations-between-nested-schema-elements.md).</span><span class="sxs-lookup"><span data-stu-id="1d59d-121">For more information, see [Map Implicit Relations Between Nested Schema Elements](map-implicit-relations-between-nested-schema-elements.md).</span></span> <span data-ttu-id="1d59d-122">Le schéma spécifie également des contraintes key et keyref.</span><span class="sxs-lookup"><span data-stu-id="1d59d-122">The schema also specifies key and keyref constraints.</span></span>  
  
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
  
 <span data-ttu-id="1d59d-123">Le **jeu de données** résultant du processus de mappage du schéma XML comprend deux tables :</span><span class="sxs-lookup"><span data-stu-id="1d59d-123">The **DataSet** resulting from the XML Schema mapping process includes two tables:</span></span>  
  
```text  
Order(OrderNumber, EmpNumber, Order_Id)  
OrderDetail(OrderNumber, ItemNumber, Order_Id)  
```  
  
 <span data-ttu-id="1d59d-124">Le **DataSet** comprend également les deux relations (une basée sur l’annotation **msdata : Relationship** et l’autre basée sur les contraintes Key et keyref) et diverses contraintes.</span><span class="sxs-lookup"><span data-stu-id="1d59d-124">The **DataSet** also includes the two relationships (one based on the **msdata:relationship** annotation and the other based on the key and keyref constraints) and various constraints.</span></span> <span data-ttu-id="1d59d-125">L'exemple suivant illustre ces relations et contraintes.</span><span class="sxs-lookup"><span data-stu-id="1d59d-125">The following example shows the relations and constraints.</span></span>  
  
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
  
 <span data-ttu-id="1d59d-126">Si une contrainte keyref faisant référence à une table imbriquée contient l’annotation **msdata : IsNested = "true"** , le **DataSet** crée une seule relation imbriquée basée sur la contrainte keyref et la contrainte unique/Key associée.</span><span class="sxs-lookup"><span data-stu-id="1d59d-126">If a keyref constraint referring to a nested table contains the **msdata:IsNested="true"** annotation, the **DataSet** will create a single nested relationship that is based on the keyref constraint and the related unique/key constraint.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1d59d-127">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="1d59d-127">See also</span></span>

- [<span data-ttu-id="1d59d-128">Dérivation de la structure relationnelle des DataSet à partir du schéma XML (XSD)</span><span class="sxs-lookup"><span data-stu-id="1d59d-128">Deriving DataSet Relational Structure from XML Schema (XSD)</span></span>](deriving-dataset-relational-structure-from-xml-schema-xsd.md)
- [<span data-ttu-id="1d59d-129">Vue d'ensemble d’ADO.NET</span><span class="sxs-lookup"><span data-stu-id="1d59d-129">ADO.NET Overview</span></span>](../ado-net-overview.md)
