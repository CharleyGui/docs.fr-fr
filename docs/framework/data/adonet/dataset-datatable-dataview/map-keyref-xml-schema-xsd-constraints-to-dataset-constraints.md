---
title: Mapper les contraintes keyref de schéma XML (XSD) aux contraintes de DataSet
ms.date: 03/30/2017
ms.assetid: 5b634fea-cc1e-4f6b-9454-10858105b1c8
ms.openlocfilehash: fe53232b6818b5bb28b433c4a473b6381b8e9083
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91198559"
---
# <a name="map-keyref-xml-schema-xsd-constraints-to-dataset-constraints"></a><span data-ttu-id="08006-102">Mapper les contraintes keyref de schéma XML (XSD) aux contraintes de DataSet</span><span class="sxs-lookup"><span data-stu-id="08006-102">Map keyref XML Schema (XSD) Constraints to DataSet Constraints</span></span>

<span data-ttu-id="08006-103">L’élément **keyref** vous permet d’établir des liens entre des éléments dans un document.</span><span class="sxs-lookup"><span data-stu-id="08006-103">The **keyref** element allows you to establish links between elements within a document.</span></span> <span data-ttu-id="08006-104">Le résultat est similaire à une relation de clé étrangère dans une base de données relationnelle.</span><span class="sxs-lookup"><span data-stu-id="08006-104">This is similar to a foreign key relationship in a relational database.</span></span> <span data-ttu-id="08006-105">Si un schéma spécifie l’élément **keyref** , l’élément est converti pendant le processus de mappage de schéma en une contrainte de clé étrangère correspondante sur les colonnes dans les tables de <xref:System.Data.DataSet> .</span><span class="sxs-lookup"><span data-stu-id="08006-105">If a schema specifies the **keyref** element, the element is converted during the schema mapping process to a corresponding foreign key constraint on the columns in the tables of the <xref:System.Data.DataSet>.</span></span> <span data-ttu-id="08006-106">Par défaut, l’élément **keyref** génère également une relation, avec les **Propriétés ParentTable**, **ChildTable**, **ParentColumn**et **ChildColumn** spécifiées sur la relation.</span><span class="sxs-lookup"><span data-stu-id="08006-106">By default, the **keyref** element also generates a relation, with the **ParentTable**, **ChildTable**, **ParentColumn**, and **ChildColumn** properties specified on the relation.</span></span>  
  
 <span data-ttu-id="08006-107">Le tableau suivant présente les attributs **msdata** que vous pouvez spécifier dans l’élément **keyref** .</span><span class="sxs-lookup"><span data-stu-id="08006-107">The following table outlines the **msdata** attributes you can specify in the **keyref** element.</span></span>  
  
|<span data-ttu-id="08006-108">Nom de l’attribut</span><span class="sxs-lookup"><span data-stu-id="08006-108">Attribute name</span></span>|<span data-ttu-id="08006-109">Description</span><span class="sxs-lookup"><span data-stu-id="08006-109">Description</span></span>|  
|--------------------|-----------------|  
|<span data-ttu-id="08006-110">**msdata:ConstraintOnly**</span><span class="sxs-lookup"><span data-stu-id="08006-110">**msdata:ConstraintOnly**</span></span>|<span data-ttu-id="08006-111">Si **ConstraintOnly = "true"** est spécifié sur l’élément **keyref** du schéma, une contrainte est créée, mais aucune relation n’est créée.</span><span class="sxs-lookup"><span data-stu-id="08006-111">If **ConstraintOnly="true"** is specified on the **keyref** element in the schema, a constraint is created, but no relation is created.</span></span> <span data-ttu-id="08006-112">Si cet attribut n’est pas spécifié (ou a la valeur **false**), la contrainte et la relation sont créées dans le **DataSet**.</span><span class="sxs-lookup"><span data-stu-id="08006-112">If this attribute is not specified (or is set to **False**), both the constraint and the relation are created in the **DataSet**.</span></span>|  
|<span data-ttu-id="08006-113">**msdata:ConstraintName**</span><span class="sxs-lookup"><span data-stu-id="08006-113">**msdata:ConstraintName**</span></span>|<span data-ttu-id="08006-114">Si l’attribut **ConstraintName** est spécifié, sa valeur est utilisée comme nom de la contrainte.</span><span class="sxs-lookup"><span data-stu-id="08006-114">If the **ConstraintName** attribute is specified, its value is used as the name of the constraint.</span></span> <span data-ttu-id="08006-115">Dans le cas contraire, l’attribut **Name** de l’élément **keyref** dans le schéma fournit le nom de la contrainte dans le **DataSet**.</span><span class="sxs-lookup"><span data-stu-id="08006-115">Otherwise, the **name** attribute of the **keyref** element in the schema provides the constraint name in the **DataSet**.</span></span>|  
|<span data-ttu-id="08006-116">**msdata:UpdateRule**</span><span class="sxs-lookup"><span data-stu-id="08006-116">**msdata:UpdateRule**</span></span>|<span data-ttu-id="08006-117">Si l’attribut **UpdateRule** est spécifié dans l’élément **keyref** du schéma, sa valeur est assignée à la propriété **UpdateRule** de la contrainte dans le **DataSet**.</span><span class="sxs-lookup"><span data-stu-id="08006-117">If the **UpdateRule** attribute is specified in the **keyref** element in the schema, its value is assigned to the **UpdateRule** constraint property in the **DataSet**.</span></span> <span data-ttu-id="08006-118">Sinon, la propriété **UpdateRule** a la valeur **cascade**.</span><span class="sxs-lookup"><span data-stu-id="08006-118">Otherwise the **UpdateRule** property is set to **Cascade**.</span></span>|  
|<span data-ttu-id="08006-119">**msdata:DeleteRule**</span><span class="sxs-lookup"><span data-stu-id="08006-119">**msdata:DeleteRule**</span></span>|<span data-ttu-id="08006-120">Si l’attribut **DeleteRule** est spécifié dans l’élément **keyref** du schéma, sa valeur est assignée à la propriété de contrainte **DeleteRule** dans le **DataSet**.</span><span class="sxs-lookup"><span data-stu-id="08006-120">If the **DeleteRule** attribute is specified in the **keyref** element in the schema, its value is assigned to the **DeleteRule** constraint property in the **DataSet**.</span></span> <span data-ttu-id="08006-121">Sinon, la propriété **DeleteRule** a la valeur **cascade**.</span><span class="sxs-lookup"><span data-stu-id="08006-121">Otherwise the **DeleteRule** property is set to **Cascade**.</span></span>|  
|<span data-ttu-id="08006-122">**msdata:AcceptRejectRule**</span><span class="sxs-lookup"><span data-stu-id="08006-122">**msdata:AcceptRejectRule**</span></span>|<span data-ttu-id="08006-123">Si l’attribut **AcceptRejectRule** est spécifié dans l’élément **keyref** du schéma, sa valeur est assignée à la propriété **AcceptRejectRule** de la contrainte dans le **DataSet**.</span><span class="sxs-lookup"><span data-stu-id="08006-123">If the **AcceptRejectRule** attribute is specified in the **keyref** element in the schema, its value is assigned to the **AcceptRejectRule** constraint property in the **DataSet**.</span></span> <span data-ttu-id="08006-124">Sinon, la propriété **AcceptRejectRule** est définie sur **None**.</span><span class="sxs-lookup"><span data-stu-id="08006-124">Otherwise the **AcceptRejectRule** property is set to **None**.</span></span>|  
  
 <span data-ttu-id="08006-125">L’exemple suivant contient un schéma qui spécifie les relations **Key** et **keyref** entre l’élément enfant **OrderNumber** de l’élément **Order** et l’élément enfant **OrderNo** de l’élément **OrderDetail** .</span><span class="sxs-lookup"><span data-stu-id="08006-125">The following example contains a schema that specifies the **key** and **keyref** relationships between the **OrderNumber** child element of the **Order** element and the **OrderNo** child element of the **OrderDetail** element.</span></span>  
  
 <span data-ttu-id="08006-126">Dans l’exemple, l’élément enfant **OrderNumber** de l’élément **OrderDetail** fait référence à l’élément enfant de la clé **OrderNo** de l’élément **Order** .</span><span class="sxs-lookup"><span data-stu-id="08006-126">In the example, the **OrderNumber** child element of the **OrderDetail** element refers to the **OrderNo** key child element of the **Order** element.</span></span>  
  
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
  
 <span data-ttu-id="08006-127">Le processus de mappage de schéma en langage XSD (XML Schema Definition) génère le **jeu de données** suivant avec deux tables :</span><span class="sxs-lookup"><span data-stu-id="08006-127">The XML Schema definition language (XSD) schema mapping process produces the following **DataSet** with two tables:</span></span>  
  
```text  
OrderDetail(OrderNo, ItemNo) and  
Order(OrderNumber, EmpNumber)  
```  
  
 <span data-ttu-id="08006-128">En outre, le **jeu de données** définit les contraintes suivantes :</span><span class="sxs-lookup"><span data-stu-id="08006-128">In addition, the **DataSet** defines the following constraints:</span></span>  
  
- <span data-ttu-id="08006-129">Contrainte unique sur la table **Order** .</span><span class="sxs-lookup"><span data-stu-id="08006-129">A unique constraint on the **Order** table.</span></span>  
  
    ```text
              Table: Order  
    Columns: OrderNumber
    ConstraintName: OrderNumberKey  
    Type: UniqueConstraint  
    IsPrimaryKey: False  
    ```  
  
- <span data-ttu-id="08006-130">Relation entre les tables **Order** et **OrderDetail** .</span><span class="sxs-lookup"><span data-stu-id="08006-130">A relationship between the **Order** and **OrderDetail** tables.</span></span> <span data-ttu-id="08006-131">La propriété **Nested** a la valeur **false** , car les deux éléments ne sont pas imbriqués dans le schéma.</span><span class="sxs-lookup"><span data-stu-id="08006-131">The **Nested** property is set to **False** because the two elements are not nested in the schema.</span></span>  
  
    ```text
              ParentTable: Order  
    ParentColumns: OrderNumber
    ChildTable: OrderDetail  
    ChildColumns: OrderNo
    ParentKeyConstraint: OrderNumberKey  
    ChildKeyConstraint: OrderNoRef  
    RelationName: OrderNoRef  
    Nested: False  
    ```  
  
- <span data-ttu-id="08006-132">Contrainte de clé étrangère sur la table **OrderDetail** .</span><span class="sxs-lookup"><span data-stu-id="08006-132">A foreign key constraint on the **OrderDetail** table.</span></span>  
  
    ```text  
              ConstraintName: OrderNoRef  
    Type: ForeignKeyConstraint  
    Table: OrderDetail  
    Columns: OrderNo
    RelatedTable: Order  
    RelatedColumns: OrderNumber
    ```  
  
## <a name="see-also"></a><span data-ttu-id="08006-133">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="08006-133">See also</span></span>

- [<span data-ttu-id="08006-134">Mappage des contraintes de schéma XML (XSD) aux contraintes de DataSet</span><span class="sxs-lookup"><span data-stu-id="08006-134">Mapping XML Schema (XSD) Constraints to DataSet Constraints</span></span>](mapping-xml-schema-xsd-constraints-to-dataset-constraints.md)
- [<span data-ttu-id="08006-135">Génération de relations de DataSet à partir du schéma XML (XSD)</span><span class="sxs-lookup"><span data-stu-id="08006-135">Generating DataSet Relations from XML Schema (XSD)</span></span>](generating-dataset-relations-from-xml-schema-xsd.md)
- [<span data-ttu-id="08006-136">Vue d'ensemble d’ADO.NET</span><span class="sxs-lookup"><span data-stu-id="08006-136">ADO.NET Overview</span></span>](../ado-net-overview.md)
