---
title: Mapper les contraintes uniques de schéma XML (XSD) aux contraintes de DataSet
ms.date: 03/30/2017
ms.assetid: 56da90bf-21d3-4d1a-8bb8-de908866b78d
ms.openlocfilehash: 8bcf705ce4415929e685be79f813846bbb40bb36
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79150842"
---
# <a name="map-unique-xml-schema-xsd-constraints-to-dataset-constraints"></a><span data-ttu-id="a8ae9-102">Mapper les contraintes uniques de schéma XML (XSD) aux contraintes de DataSet</span><span class="sxs-lookup"><span data-stu-id="a8ae9-102">Map unique XML Schema (XSD) Constraints to DataSet Constraints</span></span>
<span data-ttu-id="a8ae9-103">Dans un schéma de définition XML Schema (XSD), l’élément **unique** spécifie la contrainte d’unicité sur un élément ou un attribut.</span><span class="sxs-lookup"><span data-stu-id="a8ae9-103">In an XML Schema definition language (XSD) schema, the **unique** element specifies the uniqueness constraint on an element or attribute.</span></span> <span data-ttu-id="a8ae9-104">Dans le processus de conversion d'un schéma XML en schéma relationnel, la contrainte unique spécifiée sur un élément ou un attribut du schéma XML est mappée à une contrainte unique dans l'objet <xref:System.Data.DataTable> de l'objet <xref:System.Data.DataSet> correspondant qui est généré.</span><span class="sxs-lookup"><span data-stu-id="a8ae9-104">In the process of translating an XML Schema into a relational schema, the unique constraint specified on an element or attribute in the XML Schema is mapped to a unique constraint in the <xref:System.Data.DataTable> in the corresponding <xref:System.Data.DataSet> that is generated.</span></span>  
  
 <span data-ttu-id="a8ae9-105">Le tableau suivant décrit les attributs **msdata** que vous pouvez spécifier dans **l’élément unique.**</span><span class="sxs-lookup"><span data-stu-id="a8ae9-105">The following table outlines the **msdata** attributes that you can specify in the **unique** element.</span></span>  
  
|<span data-ttu-id="a8ae9-106">Nom de l’attribut</span><span class="sxs-lookup"><span data-stu-id="a8ae9-106">Attribute name</span></span>|<span data-ttu-id="a8ae9-107">Description</span><span class="sxs-lookup"><span data-stu-id="a8ae9-107">Description</span></span>|  
|--------------------|-----------------|  
|<span data-ttu-id="a8ae9-108">**msdata:ConstraintName**</span><span class="sxs-lookup"><span data-stu-id="a8ae9-108">**msdata:ConstraintName**</span></span>|<span data-ttu-id="a8ae9-109">Si cet attribut est spécifié, sa valeur est utilisée comme nom de la contrainte.</span><span class="sxs-lookup"><span data-stu-id="a8ae9-109">If this attribute is specified, its value is used as the constraint name.</span></span> <span data-ttu-id="a8ae9-110">Dans le cas contraire, l’attribut de **nom** fournit la valeur du nom de contrainte.</span><span class="sxs-lookup"><span data-stu-id="a8ae9-110">Otherwise, the **name** attribute provides the value of the constraint name.</span></span>|  
|<span data-ttu-id="a8ae9-111">**msdata:PrimaryKey**</span><span class="sxs-lookup"><span data-stu-id="a8ae9-111">**msdata:PrimaryKey**</span></span>|<span data-ttu-id="a8ae9-112">Si `PrimaryKey="true"` elle est présente dans **l’élément unique,** une contrainte unique est créée avec la propriété **IsPrimaryKey** définie pour **vrai**.</span><span class="sxs-lookup"><span data-stu-id="a8ae9-112">If `PrimaryKey="true"` is present in the **unique** element, a unique constraint is created with the **IsPrimaryKey** property set to **true**.</span></span>|  
  
 <span data-ttu-id="a8ae9-113">L’exemple suivant montre un schéma XML qui utilise **l’élément unique** pour spécifier une contrainte d’unicité.</span><span class="sxs-lookup"><span data-stu-id="a8ae9-113">The following example shows an XML Schema that uses the **unique** element to specify a uniqueness constraint.</span></span>  
  
```xml  
<xs:schema id="SampleDataSet"
            xmlns:xs="http://www.w3.org/2001/XMLSchema"
            xmlns:msdata="urn:schemas-microsoft-com:xml-msdata">  
  <xs:element name="Customers">  
    <xs:complexType>  
      <xs:sequence>  
        <xs:element name="CustomerID" type="xs:integer"
           minOccurs="0"/>  
        <xs:element name="CompanyName" type="xs:string"
           minOccurs="0"/>  
       <xs:element name="Phone" type="xs:string" />  
     </xs:sequence>  
   </xs:complexType>  
 </xs:element>  
  
 <xs:element name="SampleDataSet" msdata:IsDataSet="true">  
  <xs:complexType>  
    <xs:choice maxOccurs="unbounded">  
      <xs:element ref="Customers" />  
    </xs:choice>  
  </xs:complexType>  
   <xs:unique     msdata:ConstraintName="UCustID"     name="UniqueCustIDConstr" >       <xs:selector xpath=".//Customers" />       <xs:field xpath="CustomerID" />     </xs:unique>  
</xs:element>  
</xs:schema>  
```  
  
 <span data-ttu-id="a8ae9-114">**L’élément unique** dans le schéma précise que pour tous les éléments **clients** dans une instance de document, la valeur de **l’élément** enfant CustomerID doit être unique.</span><span class="sxs-lookup"><span data-stu-id="a8ae9-114">The **unique** element in the schema specifies that for all **Customers** elements in a document instance, the value of the **CustomerID** child element must be unique.</span></span> <span data-ttu-id="a8ae9-115">Lors de la construction du **DataSet**, le processus de cartographie lit ce schéma et génère le tableau suivant :</span><span class="sxs-lookup"><span data-stu-id="a8ae9-115">In building the **DataSet**, the mapping process reads this schema and generates the following table:</span></span>  
  
```text  
Customers (CustomerID, CompanyName, Phone)  
```  
  
 <span data-ttu-id="a8ae9-116">Le processus de cartographie crée également une contrainte unique sur la colonne **CustomerID,** comme le montre le **DataSet**suivant .</span><span class="sxs-lookup"><span data-stu-id="a8ae9-116">The mapping process also creates a unique constraint on the **CustomerID** column, as shown in the following **DataSet**.</span></span> <span data-ttu-id="a8ae9-117">(Par souci de simplicité, seules les propriétés pertinentes sont représentées.)</span><span class="sxs-lookup"><span data-stu-id="a8ae9-117">(For simplicity, only relevant properties are shown.)</span></span>  
  
```text  
      DataSetName: MyDataSet  
TableName: Customers  
  ColumnName: CustomerID  
      AllowDBNull: True  
      Unique: True  
  ConstraintName: UcustID       Type: UniqueConstraint  
      Table: Customers  
      Columns: CustomerID
      IsPrimaryKey: False  
```  
  
 <span data-ttu-id="a8ae9-118">Dans le **DataSet** qui est généré, la propriété **IsPrimaryKey** est définie à **False** pour la contrainte unique.</span><span class="sxs-lookup"><span data-stu-id="a8ae9-118">In the **DataSet** that is generated, the **IsPrimaryKey** property is set to **False** for the unique constraint.</span></span> <span data-ttu-id="a8ae9-119">La propriété **unique** sur la colonne indique que les valeurs de colonne **CustomerID** doivent être uniques (mais elles peuvent être une référence nulle, comme le précise la propriété **AllowDBNull** de la colonne).</span><span class="sxs-lookup"><span data-stu-id="a8ae9-119">The **unique** property on the column indicates that the **CustomerID** column values must be unique (but they can be a null reference, as specified by the **AllowDBNull** property of the column).</span></span>  
  
 <span data-ttu-id="a8ae9-120">Si vous modifiez le schéma et définissez la valeur d’attribut **msdata:PrimaryKey** optionnelle à **True**, la contrainte unique est créée sur la table.</span><span class="sxs-lookup"><span data-stu-id="a8ae9-120">If you modify the schema and set the optional **msdata:PrimaryKey** attribute value to **True**, the unique constraint is created on the table.</span></span> <span data-ttu-id="a8ae9-121">La propriété de colonne **AllowDBNull** est réglée à **False**, et la propriété **IsPrimaryKey** de la contrainte définie à **True**, faisant ainsi de la colonne **CustomerID** une colonne principale.</span><span class="sxs-lookup"><span data-stu-id="a8ae9-121">The **AllowDBNull** column property is set to **False**, and the **IsPrimaryKey** property of the constraint set to **True**, thus making the **CustomerID** column a primary key column.</span></span>  
  
 <span data-ttu-id="a8ae9-122">Vous pouvez spécifier une contrainte unique sur une combinaison d'éléments ou d'attributs dans le schéma XML.</span><span class="sxs-lookup"><span data-stu-id="a8ae9-122">You can specify a unique constraint on a combination of elements or attributes in the XML Schema.</span></span> <span data-ttu-id="a8ae9-123">L’exemple suivant montre comment spécifier qu’une combinaison de valeurs **CustomerID** et **CompanyName** doit être unique pour tous les **clients** dans n’importe quel cas, en ajoutant un autre élément **xs:field** dans le schéma.</span><span class="sxs-lookup"><span data-stu-id="a8ae9-123">The following example demonstrates how to specify that a combination of **CustomerID** and **CompanyName** values must be unique for all **Customers** in any instance, by adding another **xs:field** element in the schema.</span></span>  
  
```xml  
      <xs:unique
         msdata:ConstraintName="SomeName"
         name="UniqueCustIDConstr" >
  <xs:selector xpath=".//Customers" />
  <xs:field xpath="CustomerID" />
  <xs:field xpath="CompanyName" />
</xs:unique>  
```  
  
 <span data-ttu-id="a8ae9-124">C’est la contrainte qui est créée dans le **DataSet**résultant .</span><span class="sxs-lookup"><span data-stu-id="a8ae9-124">This is the constraint that is created in the resulting **DataSet**.</span></span>  
  
```text  
ConstraintName: SomeName  
  Table: Customers  
  Columns: CustomerID CompanyName
  IsPrimaryKey: False  
```  
  
## <a name="see-also"></a><span data-ttu-id="a8ae9-125">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a8ae9-125">See also</span></span>

- [<span data-ttu-id="a8ae9-126">Mappage des contraintes de schéma XML (XSD) aux contraintes de DataSet</span><span class="sxs-lookup"><span data-stu-id="a8ae9-126">Mapping XML Schema (XSD) Constraints to DataSet Constraints</span></span>](mapping-xml-schema-xsd-constraints-to-dataset-constraints.md)
- [<span data-ttu-id="a8ae9-127">Génération de relations de DataSet à partir du schéma XML (XSD)</span><span class="sxs-lookup"><span data-stu-id="a8ae9-127">Generating DataSet Relations from XML Schema (XSD)</span></span>](generating-dataset-relations-from-xml-schema-xsd.md)
- [<span data-ttu-id="a8ae9-128">Vue d'ensemble d’ADO.NET</span><span class="sxs-lookup"><span data-stu-id="a8ae9-128">ADO.NET Overview</span></span>](../ado-net-overview.md)
