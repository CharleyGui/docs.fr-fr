---
title: Mapper les contraintes clés de schéma XML (XSD) aux contraintes de DataSet
ms.date: 03/30/2017
ms.assetid: 22664196-f270-4ebc-a169-70e16a83dfa1
ms.openlocfilehash: d6fcdae77c2f2ac07ea5cd16baf07cd5de36d25b
ms.sourcegitcommit: 2d792961ed48f235cf413d6031576373c3050918
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/31/2019
ms.locfileid: "70203464"
---
# <a name="map-key-xml-schema-xsd-constraints-to-dataset-constraints"></a><span data-ttu-id="3cd34-102">Mapper les contraintes clés de schéma XML (XSD) aux contraintes de DataSet</span><span class="sxs-lookup"><span data-stu-id="3cd34-102">Map key XML Schema (XSD) Constraints to DataSet Constraints</span></span>
<span data-ttu-id="3cd34-103">Dans un schéma, vous pouvez spécifier une contrainte de clé sur un élément ou un attribut à l’aide de l’élément **Key** .</span><span class="sxs-lookup"><span data-stu-id="3cd34-103">In a schema, you can specify a key constraint on an element or attribute using the **key** element.</span></span> <span data-ttu-id="3cd34-104">L'élément ou attribut sur lequel une contrainte de clé est spécifiée doit avoir des valeurs uniques dans toute instance du schéma et ne peut pas avoir de valeurs null.</span><span class="sxs-lookup"><span data-stu-id="3cd34-104">The element or attribute on which a key constraint is specified must have unique values in any schema instance, and cannot have null values.</span></span>  
  
 <span data-ttu-id="3cd34-105">La contrainte de clé est similaire à la contrainte unique, si ce n'est que la colonne sur laquelle une contrainte de clé est définie ne peut pas comporter de valeurs null.</span><span class="sxs-lookup"><span data-stu-id="3cd34-105">The key constraint is similar to the unique constraint, except that the column on which a key constraint is defined cannot have null values.</span></span>  
  
 <span data-ttu-id="3cd34-106">Le tableau suivant présente les attributs **msdata** que vous pouvez spécifier dans l’élément **Key** .</span><span class="sxs-lookup"><span data-stu-id="3cd34-106">The following table outlines the **msdata** attributes that you can specify in the **key** element.</span></span>  
  
|<span data-ttu-id="3cd34-107">Nom d'attribut</span><span class="sxs-lookup"><span data-stu-id="3cd34-107">Attribute name</span></span>|<span data-ttu-id="3cd34-108">Description</span><span class="sxs-lookup"><span data-stu-id="3cd34-108">Description</span></span>|  
|--------------------|-----------------|  
|<span data-ttu-id="3cd34-109">**msdata:ConstraintName**</span><span class="sxs-lookup"><span data-stu-id="3cd34-109">**msdata:ConstraintName**</span></span>|<span data-ttu-id="3cd34-110">Si cet attribut est spécifié, sa valeur est utilisée comme nom de la contrainte.</span><span class="sxs-lookup"><span data-stu-id="3cd34-110">If this attribute is specified, its value is used as the constraint name.</span></span> <span data-ttu-id="3cd34-111">Dans le cas contraire, l’attribut **Name** fournit la valeur du nom de la contrainte.</span><span class="sxs-lookup"><span data-stu-id="3cd34-111">Otherwise, the **name** attribute provides the value of the constraint name.</span></span>|  
|<span data-ttu-id="3cd34-112">**msdata:PrimaryKey**</span><span class="sxs-lookup"><span data-stu-id="3cd34-112">**msdata:PrimaryKey**</span></span>|<span data-ttu-id="3cd34-113">Si `PrimaryKey="true"` est présent, la propriété de contrainte **IsPrimaryKey** a la valeur **true**, ce qui en fait une clé primaire.</span><span class="sxs-lookup"><span data-stu-id="3cd34-113">If `PrimaryKey="true"` is present, the **IsPrimaryKey** constraint property is set to **true**, thus making it a primary key.</span></span> <span data-ttu-id="3cd34-114">La propriété de la colonne **AllowDBNull** ala valeur false, car les clés primaires ne peuvent pas avoir de valeurs NULL.</span><span class="sxs-lookup"><span data-stu-id="3cd34-114">The **AllowDBNull** column property is set to **false**, because primary keys cannot have null values.</span></span>|  
  
 <span data-ttu-id="3cd34-115">Lors de la conversion d’un schéma dans lequel une contrainte de clé est spécifiée, le processus de mappage crée une contrainte unique sur la table avec la propriété de colonne **AllowDBNull** définie sur **false** pour chaque colonne de la contrainte.</span><span class="sxs-lookup"><span data-stu-id="3cd34-115">In converting schema in which a key constraint is specified, the mapping process creates a unique constraint on the table with the **AllowDBNull** column property set to **false** for each column in the constraint.</span></span> <span data-ttu-id="3cd34-116">La propriété **IsPrimaryKey** de la contrainte unique a également la valeur **false** , sauf si `msdata:PrimaryKey="true"` vous avez spécifié sur l’élément **Key** .</span><span class="sxs-lookup"><span data-stu-id="3cd34-116">The **IsPrimaryKey** property of the unique constraint is also set to **false** unless you have specified `msdata:PrimaryKey="true"` on the **key** element.</span></span> <span data-ttu-id="3cd34-117">Ce mode de fonctionnement est identique à celui d'une contrainte unique dans le schéma faisant apparaître `PrimaryKey="true"`.</span><span class="sxs-lookup"><span data-stu-id="3cd34-117">This is identical to a unique constraint in the schema in which `PrimaryKey="true"`.</span></span>  
  
 <span data-ttu-id="3cd34-118">Dans l’exemple de schéma suivant, l’élément **Key** spécifie la contrainte de clé sur l’élément **CustomerID** .</span><span class="sxs-lookup"><span data-stu-id="3cd34-118">In the following schema example, the **key** element specifies the key constraint on the **CustomerID** element.</span></span>  
  
```xml  
<xs:schema id="cod"  
            xmlns:xs="http://www.w3.org/2001/XMLSchema"   
            xmlns:msdata="urn:schemas-microsoft-com:xml-msdata">  
  <xs:element name="Customers">  
    <xs:complexType>  
      <xs:sequence>  
        <xs:element name="CustomerID" type="xs:string" minOccurs="0" />  
        <xs:element name="CompanyName" type="xs:string" minOccurs="0" />  
       <xs:element name="Phone" type="xs:string" />  
     </xs:sequence>  
   </xs:complexType>  
 </xs:element>  
<xs:element name="MyDataSet" msdata:IsDataSet="true">  
  <xs:complexType>  
    <xs:choice maxOccurs="unbounded">  
      <xs:element ref="Customers" />  
    </xs:choice>  
  </xs:complexType>  
   <xs:key  msdata:PrimaryKey="true"  
       msdata:ConstraintName="KeyCustID"  
          name="KeyConstCustomerID" >  
     <xs:selector xpath=".//Customers" />  
     <xs:field xpath="CustomerID" />  
    </xs:key>  
 </xs:element>  
</xs:schema>   
```  
  
 <span data-ttu-id="3cd34-119">L’élément **Key** spécifie que les valeurs de l’élément enfant **CustomerID** de l’élément **Customers** doivent avoir des valeurs uniques et ne peuvent pas avoir de valeurs NULL.</span><span class="sxs-lookup"><span data-stu-id="3cd34-119">The **key** element specifies that the values of the **CustomerID** child element of the **Customers** element must have unique values and cannot have null values.</span></span> <span data-ttu-id="3cd34-120">En convertissant le schéma en langage XSD (XML Schema Definition), le processus de mappage crée la table suivante :</span><span class="sxs-lookup"><span data-stu-id="3cd34-120">In translating the XML Schema definition language (XSD) schema, the mapping process creates the following table:</span></span>  
  
```  
Customers(CustomerID, CompanyName, Phone)  
```  
  
 <span data-ttu-id="3cd34-121">Le mappage de schéma XML crée également un **UniqueConstraint** sur la colonne **CustomerID** , comme indiqué dans le <xref:System.Data.DataSet>code suivant.</span><span class="sxs-lookup"><span data-stu-id="3cd34-121">The XML Schema mapping also creates a **UniqueConstraint** on the **CustomerID** column, as shown in the following <xref:System.Data.DataSet>.</span></span> <span data-ttu-id="3cd34-122">(Par souci de simplicité, seules les propriétés pertinentes sont représentées.)</span><span class="sxs-lookup"><span data-stu-id="3cd34-122">(For simplicity, only relevant properties are shown.)</span></span>  
  
```  
      DataSetName: MyDataSet  
TableName: customers  
  ColumnName: CustomerID  
      AllowDBNull: False  
      Unique: True  
  ConstraintName: KeyCustID  
      Table: customers  
      Columns: CustomerID   
      IsPrimaryKey: True  
```  
  
 <span data-ttu-id="3cd34-123">Dans le **DataSet** généré, la propriété **IsPrimaryKey** de **UniqueConstraint** a la valeur **true** car le schéma spécifie `msdata:PrimaryKey="true"` dans l’élément **Key** .</span><span class="sxs-lookup"><span data-stu-id="3cd34-123">In the **DataSet** that is generated, the **IsPrimaryKey** property of the **UniqueConstraint** is set to **true** because the schema specifies `msdata:PrimaryKey="true"` in the **key** element.</span></span>  
  
 <span data-ttu-id="3cd34-124">La valeur de la propriété **ConstraintName** de **UniqueConstraint** dans le **DataSet** est la valeur de l’attribut **msdata: ConstraintName** spécifié dans l’élément **Key** du schéma.</span><span class="sxs-lookup"><span data-stu-id="3cd34-124">The value of the **ConstraintName** property of the **UniqueConstraint** in the **DataSet** is the value of the **msdata:ConstraintName** attribute specified in the **key** element in the schema.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3cd34-125">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3cd34-125">See also</span></span>

- [<span data-ttu-id="3cd34-126">Mappage des contraintes de schéma XML (XSD) aux contraintes de DataSet</span><span class="sxs-lookup"><span data-stu-id="3cd34-126">Mapping XML Schema (XSD) Constraints to DataSet Constraints</span></span>](mapping-xml-schema-xsd-constraints-to-dataset-constraints.md)
- [<span data-ttu-id="3cd34-127">Génération de relations de DataSet à partir du schéma XML (XSD)</span><span class="sxs-lookup"><span data-stu-id="3cd34-127">Generating DataSet Relations from XML Schema (XSD)</span></span>](generating-dataset-relations-from-xml-schema-xsd.md)
- [<span data-ttu-id="3cd34-128">Fournisseurs managés ADO.NET et centre de développement DataSet</span><span class="sxs-lookup"><span data-stu-id="3cd34-128">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
