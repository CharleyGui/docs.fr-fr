---
title: Mapper les contraintes keyref de schéma XML (XSD) aux contraintes de DataSet
ms.date: 03/30/2017
ms.assetid: 5b634fea-cc1e-4f6b-9454-10858105b1c8
ms.openlocfilehash: 902b79b73f494ced0f54b29babff1b2e767bd47a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79150881"
---
# <a name="map-keyref-xml-schema-xsd-constraints-to-dataset-constraints"></a><span data-ttu-id="f9c43-102">Mapper les contraintes keyref de schéma XML (XSD) aux contraintes de DataSet</span><span class="sxs-lookup"><span data-stu-id="f9c43-102">Map keyref XML Schema (XSD) Constraints to DataSet Constraints</span></span>
<span data-ttu-id="f9c43-103">**L’élément keyref** vous permet d’établir des liens entre les éléments d’un document.</span><span class="sxs-lookup"><span data-stu-id="f9c43-103">The **keyref** element allows you to establish links between elements within a document.</span></span> <span data-ttu-id="f9c43-104">Le résultat est similaire à une relation de clé étrangère dans une base de données relationnelle.</span><span class="sxs-lookup"><span data-stu-id="f9c43-104">This is similar to a foreign key relationship in a relational database.</span></span> <span data-ttu-id="f9c43-105">Si un schéma spécifie **l’élément keyref,** l’élément est converti au cours du processus de <xref:System.Data.DataSet>cartographie du schéma en une contrainte clé étrangère correspondante sur les colonnes dans les tableaux de la .</span><span class="sxs-lookup"><span data-stu-id="f9c43-105">If a schema specifies the **keyref** element, the element is converted during the schema mapping process to a corresponding foreign key constraint on the columns in the tables of the <xref:System.Data.DataSet>.</span></span> <span data-ttu-id="f9c43-106">Par défaut, **l’élément keyref** génère également une relation, avec les propriétés **ParentTable**, **ChildTable**, **ParentColumn**et **ChildColumn** spécifiées sur la relation.</span><span class="sxs-lookup"><span data-stu-id="f9c43-106">By default, the **keyref** element also generates a relation, with the **ParentTable**, **ChildTable**, **ParentColumn**, and **ChildColumn** properties specified on the relation.</span></span>  
  
 <span data-ttu-id="f9c43-107">Le tableau suivant décrit les attributs **msdata** que vous pouvez spécifier dans l’élément **keyref.**</span><span class="sxs-lookup"><span data-stu-id="f9c43-107">The following table outlines the **msdata** attributes you can specify in the **keyref** element.</span></span>  
  
|<span data-ttu-id="f9c43-108">Nom de l’attribut</span><span class="sxs-lookup"><span data-stu-id="f9c43-108">Attribute name</span></span>|<span data-ttu-id="f9c43-109">Description</span><span class="sxs-lookup"><span data-stu-id="f9c43-109">Description</span></span>|  
|--------------------|-----------------|  
|<span data-ttu-id="f9c43-110">**msdata:ConstraintOnly**</span><span class="sxs-lookup"><span data-stu-id="f9c43-110">**msdata:ConstraintOnly**</span></span>|<span data-ttu-id="f9c43-111">Si **ConstraintOnlyMD "vrai"** est spécifié sur **l’élément keyref** dans le schéma, une contrainte est créée, mais aucune relation n’est créée.</span><span class="sxs-lookup"><span data-stu-id="f9c43-111">If **ConstraintOnly="true"** is specified on the **keyref** element in the schema, a constraint is created, but no relation is created.</span></span> <span data-ttu-id="f9c43-112">Si cet attribut n’est pas spécifié (ou est réglé sur **Faux),** la contrainte et la relation sont créées dans le **DataSet**.</span><span class="sxs-lookup"><span data-stu-id="f9c43-112">If this attribute is not specified (or is set to **False**), both the constraint and the relation are created in the **DataSet**.</span></span>|  
|<span data-ttu-id="f9c43-113">**msdata:ConstraintName**</span><span class="sxs-lookup"><span data-stu-id="f9c43-113">**msdata:ConstraintName**</span></span>|<span data-ttu-id="f9c43-114">Si l’attribut **ConstraintName** est spécifié, sa valeur est utilisée comme nom de la contrainte.</span><span class="sxs-lookup"><span data-stu-id="f9c43-114">If the **ConstraintName** attribute is specified, its value is used as the name of the constraint.</span></span> <span data-ttu-id="f9c43-115">Dans **le** cas contraire, l’attribut nom de l’élément **keyref** dans le schéma fournit le nom de contrainte dans le **DataSet**.</span><span class="sxs-lookup"><span data-stu-id="f9c43-115">Otherwise, the **name** attribute of the **keyref** element in the schema provides the constraint name in the **DataSet**.</span></span>|  
|<span data-ttu-id="f9c43-116">**msdata:UpdateRule**</span><span class="sxs-lookup"><span data-stu-id="f9c43-116">**msdata:UpdateRule**</span></span>|<span data-ttu-id="f9c43-117">Si l’attribut **UpdateRule** est spécifié dans **l’élément keyref** dans le schéma, sa valeur est attribuée à la propriété de contrainte **UpdateRule** dans le **DataSet**.</span><span class="sxs-lookup"><span data-stu-id="f9c43-117">If the **UpdateRule** attribute is specified in the **keyref** element in the schema, its value is assigned to the **UpdateRule** constraint property in the **DataSet**.</span></span> <span data-ttu-id="f9c43-118">Sinon, la propriété **UpdateRule** est réglée sur **Cascade**.</span><span class="sxs-lookup"><span data-stu-id="f9c43-118">Otherwise the **UpdateRule** property is set to **Cascade**.</span></span>|  
|<span data-ttu-id="f9c43-119">**msdata:DeleteRule**</span><span class="sxs-lookup"><span data-stu-id="f9c43-119">**msdata:DeleteRule**</span></span>|<span data-ttu-id="f9c43-120">Si l’attribut **DeleteRule** est spécifié dans **l’élément keyref** dans le schéma, sa valeur est attribuée à la propriété de contrainte **DeleteRule** dans le **DataSet**.</span><span class="sxs-lookup"><span data-stu-id="f9c43-120">If the **DeleteRule** attribute is specified in the **keyref** element in the schema, its value is assigned to the **DeleteRule** constraint property in the **DataSet**.</span></span> <span data-ttu-id="f9c43-121">Sinon, la propriété **DeleteRule** est réglée sur **Cascade**.</span><span class="sxs-lookup"><span data-stu-id="f9c43-121">Otherwise the **DeleteRule** property is set to **Cascade**.</span></span>|  
|<span data-ttu-id="f9c43-122">**msdata:AcceptRejectRule**</span><span class="sxs-lookup"><span data-stu-id="f9c43-122">**msdata:AcceptRejectRule**</span></span>|<span data-ttu-id="f9c43-123">Si **l’attribut AcceptRejectRule** est spécifié dans **l’élément keyref** dans le schéma, sa valeur est attribuée à la propriété de contrainte **AcceptRejectRule** dans le **DataSet**.</span><span class="sxs-lookup"><span data-stu-id="f9c43-123">If the **AcceptRejectRule** attribute is specified in the **keyref** element in the schema, its value is assigned to the **AcceptRejectRule** constraint property in the **DataSet**.</span></span> <span data-ttu-id="f9c43-124">Sinon, la propriété **AcceptRejectRule** est réglée à **Aucun**.</span><span class="sxs-lookup"><span data-stu-id="f9c43-124">Otherwise the **AcceptRejectRule** property is set to **None**.</span></span>|  
  
 <span data-ttu-id="f9c43-125">L’exemple suivant contient un schéma qui spécifie les relations **clés** et **Order** **clés** entre **l’élément enfant de l’Ordre** et **l’élément** enfant OrderNo de l’élément **OrderDetail.**</span><span class="sxs-lookup"><span data-stu-id="f9c43-125">The following example contains a schema that specifies the **key** and **keyref** relationships between the **OrderNumber** child element of the **Order** element and the **OrderNo** child element of the **OrderDetail** element.</span></span>  
  
 <span data-ttu-id="f9c43-126">Dans l’exemple, **l’élément enfant de l’ordrenumber** de l’élément **OrderDetail** se réfère à **l’élément** clé de l’ordre n’a pas d’enfant clé de l’élément **de l’Ordre.**</span><span class="sxs-lookup"><span data-stu-id="f9c43-126">In the example, the **OrderNumber** child element of the **OrderDetail** element refers to the **OrderNo** key child element of the **Order** element.</span></span>  
  
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
  
 <span data-ttu-id="f9c43-127">Le processus de cartographie des schémas de définition XML Schema (XSD) produit le **DataSet** suivant avec deux tableaux :</span><span class="sxs-lookup"><span data-stu-id="f9c43-127">The XML Schema definition language (XSD) schema mapping process produces the following **DataSet** with two tables:</span></span>  
  
```text  
OrderDetail(OrderNo, ItemNo) and  
Order(OrderNumber, EmpNumber)  
```  
  
 <span data-ttu-id="f9c43-128">En outre, le **DataSet** définit les contraintes suivantes :</span><span class="sxs-lookup"><span data-stu-id="f9c43-128">In addition, the **DataSet** defines the following constraints:</span></span>  
  
- <span data-ttu-id="f9c43-129">Une contrainte unique sur la table de **l’Ordre.**</span><span class="sxs-lookup"><span data-stu-id="f9c43-129">A unique constraint on the **Order** table.</span></span>  
  
    ```text
              Table: Order  
    Columns: OrderNumber
    ConstraintName: OrderNumberKey  
    Type: UniqueConstraint  
    IsPrimaryKey: False  
    ```  
  
- <span data-ttu-id="f9c43-130">Une relation entre les tables **Order** et **OrderDetail.**</span><span class="sxs-lookup"><span data-stu-id="f9c43-130">A relationship between the **Order** and **OrderDetail** tables.</span></span> <span data-ttu-id="f9c43-131">La propriété **nichée** est réglée à **Faux** parce que les deux éléments ne sont pas imbriqués dans le schéma.</span><span class="sxs-lookup"><span data-stu-id="f9c43-131">The **Nested** property is set to **False** because the two elements are not nested in the schema.</span></span>  
  
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
  
- <span data-ttu-id="f9c43-132">Une contrainte clé étrangère sur la table **OrderDetail.**</span><span class="sxs-lookup"><span data-stu-id="f9c43-132">A foreign key constraint on the **OrderDetail** table.</span></span>  
  
    ```text  
              ConstraintName: OrderNoRef  
    Type: ForeignKeyConstraint  
    Table: OrderDetail  
    Columns: OrderNo
    RelatedTable: Order  
    RelatedColumns: OrderNumber
    ```  
  
## <a name="see-also"></a><span data-ttu-id="f9c43-133">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f9c43-133">See also</span></span>

- [<span data-ttu-id="f9c43-134">Mappage des contraintes de schéma XML (XSD) aux contraintes de DataSet</span><span class="sxs-lookup"><span data-stu-id="f9c43-134">Mapping XML Schema (XSD) Constraints to DataSet Constraints</span></span>](mapping-xml-schema-xsd-constraints-to-dataset-constraints.md)
- [<span data-ttu-id="f9c43-135">Génération de relations de DataSet à partir du schéma XML (XSD)</span><span class="sxs-lookup"><span data-stu-id="f9c43-135">Generating DataSet Relations from XML Schema (XSD)</span></span>](generating-dataset-relations-from-xml-schema-xsd.md)
- [<span data-ttu-id="f9c43-136">Vue d'ensemble d’ADO.NET</span><span class="sxs-lookup"><span data-stu-id="f9c43-136">ADO.NET Overview</span></span>](../ado-net-overview.md)
