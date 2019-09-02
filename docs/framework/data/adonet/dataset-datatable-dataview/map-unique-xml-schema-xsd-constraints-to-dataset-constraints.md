---
title: Mapper les contraintes uniques de schéma XML (XSD) aux contraintes de DataSet
ms.date: 03/30/2017
ms.assetid: 56da90bf-21d3-4d1a-8bb8-de908866b78d
ms.openlocfilehash: 231f23ccf47f60b902fdd5c66b63fe1a750445f9
ms.sourcegitcommit: 2d792961ed48f235cf413d6031576373c3050918
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/31/2019
ms.locfileid: "70203415"
---
# <a name="map-unique-xml-schema-xsd-constraints-to-dataset-constraints"></a><span data-ttu-id="85c10-102">Mapper les contraintes uniques de schéma XML (XSD) aux contraintes de DataSet</span><span class="sxs-lookup"><span data-stu-id="85c10-102">Map unique XML Schema (XSD) Constraints to DataSet Constraints</span></span>
<span data-ttu-id="85c10-103">Dans un schéma en langage XSD (XML Schema Definition), l’élément **unique** spécifie la contrainte d’unicité sur un élément ou un attribut.</span><span class="sxs-lookup"><span data-stu-id="85c10-103">In an XML Schema definition language (XSD) schema, the **unique** element specifies the uniqueness constraint on an element or attribute.</span></span> <span data-ttu-id="85c10-104">Dans le processus de conversion d'un schéma XML en schéma relationnel, la contrainte unique spécifiée sur un élément ou un attribut du schéma XML est mappée à une contrainte unique dans l'objet <xref:System.Data.DataTable> de l'objet <xref:System.Data.DataSet> correspondant qui est généré.</span><span class="sxs-lookup"><span data-stu-id="85c10-104">In the process of translating an XML Schema into a relational schema, the unique constraint specified on an element or attribute in the XML Schema is mapped to a unique constraint in the <xref:System.Data.DataTable> in the corresponding <xref:System.Data.DataSet> that is generated.</span></span>  
  
 <span data-ttu-id="85c10-105">Le tableau suivant présente les attributs **msdata** que vous pouvez spécifier dans l’élément **unique** .</span><span class="sxs-lookup"><span data-stu-id="85c10-105">The following table outlines the **msdata** attributes that you can specify in the **unique** element.</span></span>  
  
|<span data-ttu-id="85c10-106">Nom d'attribut</span><span class="sxs-lookup"><span data-stu-id="85c10-106">Attribute name</span></span>|<span data-ttu-id="85c10-107">Description</span><span class="sxs-lookup"><span data-stu-id="85c10-107">Description</span></span>|  
|--------------------|-----------------|  
|<span data-ttu-id="85c10-108">**msdata:ConstraintName**</span><span class="sxs-lookup"><span data-stu-id="85c10-108">**msdata:ConstraintName**</span></span>|<span data-ttu-id="85c10-109">Si cet attribut est spécifié, sa valeur est utilisée comme nom de la contrainte.</span><span class="sxs-lookup"><span data-stu-id="85c10-109">If this attribute is specified, its value is used as the constraint name.</span></span> <span data-ttu-id="85c10-110">Dans le cas contraire, l’attribut **Name** fournit la valeur du nom de la contrainte.</span><span class="sxs-lookup"><span data-stu-id="85c10-110">Otherwise, the **name** attribute provides the value of the constraint name.</span></span>|  
|<span data-ttu-id="85c10-111">**msdata:PrimaryKey**</span><span class="sxs-lookup"><span data-stu-id="85c10-111">**msdata:PrimaryKey**</span></span>|<span data-ttu-id="85c10-112">Si `PrimaryKey="true"` est présent dans l’élément **unique** , une contrainte unique est créée avec la valeur **true**affectée à la propriété **IsPrimaryKey** .</span><span class="sxs-lookup"><span data-stu-id="85c10-112">If `PrimaryKey="true"` is present in the **unique** element, a unique constraint is created with the **IsPrimaryKey** property set to **true**.</span></span>|  
  
 <span data-ttu-id="85c10-113">L’exemple suivant illustre un schéma XML qui utilise l’élément **unique** pour spécifier une contrainte d’unicité.</span><span class="sxs-lookup"><span data-stu-id="85c10-113">The following example shows an XML Schema that uses the **unique** element to specify a uniqueness constraint.</span></span>  
  
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
  
 <span data-ttu-id="85c10-114">L’élément **unique** dans le schéma spécifie que pour tous les éléments **Customers** dans une instance de document, la valeur de l’élément enfant **CustomerID** doit être unique.</span><span class="sxs-lookup"><span data-stu-id="85c10-114">The **unique** element in the schema specifies that for all **Customers** elements in a document instance, the value of the **CustomerID** child element must be unique.</span></span> <span data-ttu-id="85c10-115">Lors de la génération du **jeu de données**, le processus de mappage lit ce schéma et génère la table suivante:</span><span class="sxs-lookup"><span data-stu-id="85c10-115">In building the **DataSet**, the mapping process reads this schema and generates the following table:</span></span>  
  
```  
Customers (CustomerID, CompanyName, Phone)  
```  
  
 <span data-ttu-id="85c10-116">Le processus de mappage crée également une contrainte unique sur la colonne **CustomerID** , comme indiqué dans le **jeu de données**suivant.</span><span class="sxs-lookup"><span data-stu-id="85c10-116">The mapping process also creates a unique constraint on the **CustomerID** column, as shown in the following **DataSet**.</span></span> <span data-ttu-id="85c10-117">(Par souci de simplicité, seules les propriétés pertinentes sont représentées.)</span><span class="sxs-lookup"><span data-stu-id="85c10-117">(For simplicity, only relevant properties are shown.)</span></span>  
  
```  
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
  
 <span data-ttu-id="85c10-118">Dans le **DataSet** généré, la propriété **IsPrimaryKey** a la valeur false pour la contrainte unique.</span><span class="sxs-lookup"><span data-stu-id="85c10-118">In the **DataSet** that is generated, the **IsPrimaryKey** property is set to **False** for the unique constraint.</span></span> <span data-ttu-id="85c10-119">La propriété **unique** sur la colonne indique que les valeurs de la colonne **CustomerID** doivent être uniques (mais elles peuvent être une référence null, comme spécifié par la propriété **AllowDBNull** de la colonne).</span><span class="sxs-lookup"><span data-stu-id="85c10-119">The **unique** property on the column indicates that the **CustomerID** column values must be unique (but they can be a null reference, as specified by the **AllowDBNull** property of the column).</span></span>  
  
 <span data-ttu-id="85c10-120">Si vous modifiez le schéma et définissez la valeur d’attribut **msdata: PrimaryKey** facultative sur **true**, la contrainte unique est créée sur la table.</span><span class="sxs-lookup"><span data-stu-id="85c10-120">If you modify the schema and set the optional **msdata:PrimaryKey** attribute value to **True**, the unique constraint is created on the table.</span></span> <span data-ttu-id="85c10-121">La propriété de la colonne **AllowDBNull** ala valeur false et la propriété **IsPrimaryKey** de la contrainte a la valeur **true**, ce qui fait de la colonne **CustomerID** une colonne de clé primaire.</span><span class="sxs-lookup"><span data-stu-id="85c10-121">The **AllowDBNull** column property is set to **False**, and the **IsPrimaryKey** property of the constraint set to **True**, thus making the **CustomerID** column a primary key column.</span></span>  
  
 <span data-ttu-id="85c10-122">Vous pouvez spécifier une contrainte unique sur une combinaison d'éléments ou d'attributs dans le schéma XML.</span><span class="sxs-lookup"><span data-stu-id="85c10-122">You can specify a unique constraint on a combination of elements or attributes in the XML Schema.</span></span> <span data-ttu-id="85c10-123">L’exemple suivant montre comment spécifier qu’une combinaison de valeurs **CustomerID** et **CompanyName** doit être unique pour tous les **clients** d’une instance, en ajoutant un autre élément **XS: Field** dans le schéma.</span><span class="sxs-lookup"><span data-stu-id="85c10-123">The following example demonstrates how to specify that a combination of **CustomerID** and **CompanyName** values must be unique for all **Customers** in any instance, by adding another **xs:field** element in the schema.</span></span>  
  
```xml  
      <xs:unique     
         msdata:ConstraintName="SomeName"    
         name="UniqueCustIDConstr" >   
  <xs:selector xpath=".//Customers" />   
  <xs:field xpath="CustomerID" />   
  <xs:field xpath="CompanyName" />   
</xs:unique>  
```  
  
 <span data-ttu-id="85c10-124">Il s’agit de la contrainte créée dans le **jeu de données**résultant.</span><span class="sxs-lookup"><span data-stu-id="85c10-124">This is the constraint that is created in the resulting **DataSet**.</span></span>  
  
```  
ConstraintName: SomeName  
  Table: Customers  
  Columns: CustomerID CompanyName   
  IsPrimaryKey: False  
```  
  
## <a name="see-also"></a><span data-ttu-id="85c10-125">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="85c10-125">See also</span></span>

- [<span data-ttu-id="85c10-126">Mappage des contraintes de schéma XML (XSD) aux contraintes de DataSet</span><span class="sxs-lookup"><span data-stu-id="85c10-126">Mapping XML Schema (XSD) Constraints to DataSet Constraints</span></span>](mapping-xml-schema-xsd-constraints-to-dataset-constraints.md)
- [<span data-ttu-id="85c10-127">Génération de relations de DataSet à partir du schéma XML (XSD)</span><span class="sxs-lookup"><span data-stu-id="85c10-127">Generating DataSet Relations from XML Schema (XSD)</span></span>](generating-dataset-relations-from-xml-schema-xsd.md)
- [<span data-ttu-id="85c10-128">Fournisseurs managés ADO.NET et centre de développement DataSet</span><span class="sxs-lookup"><span data-stu-id="85c10-128">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
