---
title: Mapper les relations implicites entre éléments de schéma imbriqués
ms.date: 03/30/2017
ms.assetid: 6b25002a-352e-4d9b-bae3-15129458a355
ms.openlocfilehash: dc5b81fd06f2860283c8c5fa028af4b945e2b1e9
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79150961"
---
# <a name="map-implicit-relations-between-nested-schema-elements"></a><span data-ttu-id="3d784-102">Mapper les relations implicites entre éléments de schéma imbriqués</span><span class="sxs-lookup"><span data-stu-id="3d784-102">Map Implicit Relations Between Nested Schema Elements</span></span>
<span data-ttu-id="3d784-103">Un schéma en langage XSD (XML Schema Definition) peut présenter des types complexes imbriqués les uns dans les autres.</span><span class="sxs-lookup"><span data-stu-id="3d784-103">An XML Schema definition language (XSD) schema can have complex types nested inside one another.</span></span> <span data-ttu-id="3d784-104">Dans ce cas, le processus de mappage applique le mappage par défaut et crée les différents éléments suivants dans l'objet <xref:System.Data.DataSet> :</span><span class="sxs-lookup"><span data-stu-id="3d784-104">In this case, the mapping process applies default mapping and creates the following in the <xref:System.Data.DataSet>:</span></span>  
  
- <span data-ttu-id="3d784-105">Une table pour chacun des types complexes (parent et enfant).</span><span class="sxs-lookup"><span data-stu-id="3d784-105">One table for each of the complex types (parent and child).</span></span>  
  
- <span data-ttu-id="3d784-106">S’il n’existe aucune contrainte unique sur le parent, une colonne clé primaire supplémentaire par définition de tableau nommée *TableName*_Id où *TableName* est le nom de la table mère.</span><span class="sxs-lookup"><span data-stu-id="3d784-106">If no unique constraint exists on the parent, one additional primary key column per table definition named *TableName*_Id where *TableName* is the name of the parent table.</span></span>  
  
- <span data-ttu-id="3d784-107">Une contrainte clé primaire sur le tableau parent identifiant la colonne supplémentaire comme la clé principale (en fixant la propriété **IsPrimaryKey** à **True**).</span><span class="sxs-lookup"><span data-stu-id="3d784-107">A primary key constraint on the parent table identifying the additional column as the primary key (by setting the **IsPrimaryKey** property to **True**).</span></span> <span data-ttu-id="3d784-108">La contrainte est nommée selon le modèle Constraint\#, où \# est 1, 2, 3, etc.</span><span class="sxs-lookup"><span data-stu-id="3d784-108">The constraint is named Constraint\# where \# is 1, 2, 3, and so on.</span></span> <span data-ttu-id="3d784-109">Par exemple, le nom par défaut de la première contrainte est Constraint1.</span><span class="sxs-lookup"><span data-stu-id="3d784-109">For example, the default name for the first constraint is Constraint1.</span></span>  
  
- <span data-ttu-id="3d784-110">Une contrainte de clé étrangère sur la table enfant, qui identifie la colonne supplémentaire en tant que clé étrangère faisant référence à la clé primaire de la table parente.</span><span class="sxs-lookup"><span data-stu-id="3d784-110">A foreign key constraint on the child table identifying the additional column as the foreign key referring to the primary key of the parent table.</span></span> <span data-ttu-id="3d784-111">La contrainte est nommée *ParentTable_ChildTable* où *ParentTable* est le nom de la table mère et *ChildTable* est le nom de la table de l’enfant.</span><span class="sxs-lookup"><span data-stu-id="3d784-111">The constraint is named *ParentTable_ChildTable* where *ParentTable* is the name of the parent table and *ChildTable* is the name of the child table.</span></span>  
  
- <span data-ttu-id="3d784-112">Une relation de données entre les tables parente et enfant.</span><span class="sxs-lookup"><span data-stu-id="3d784-112">A data relation between the parent and child tables.</span></span>  
  
 <span data-ttu-id="3d784-113">L’exemple suivant montre un schéma où **OrderDetail** est un élément enfant de **l’Ordre**.</span><span class="sxs-lookup"><span data-stu-id="3d784-113">The following example shows a schema where **OrderDetail** is a child element of **Order**.</span></span>  
  
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
            <xs:element name="OrderNumber" type="xs:string" />  
            <xs:element name="EmpNumber" type="xs:string" />  
            <xs:element name="OrderDetail">  
              <xs:complexType>  
                <xs:sequence>  
                  <xs:element name="OrderNo" type="xs:string" />  
                  <xs:element name="ItemNo" type="xs:string" />  
                </xs:sequence>  
              </xs:complexType>  
            </xs:element>  
          </xs:sequence>  
         </xs:complexType>  
       </xs:element>  
     </xs:choice>  
   </xs:complexType>  
  </xs:element>  
</xs:schema>  
```  
  
 <span data-ttu-id="3d784-114">Le processus de cartographie XML Schema crée ce qui suit dans le **DataSet**:</span><span class="sxs-lookup"><span data-stu-id="3d784-114">The XML Schema mapping process creates the following in the **DataSet**:</span></span>  
  
- <span data-ttu-id="3d784-115">Une **commande** et une table **OrderDetail.**</span><span class="sxs-lookup"><span data-stu-id="3d784-115">An **Order** and an **OrderDetail** table.</span></span>  
  
    ```text  
    Order(OrderNumber, EmpNumber, Order_Id)  
    OrderDetail(OrderNo, ItemNo, Order_Id)  
    ```  
  
- <span data-ttu-id="3d784-116">Une contrainte unique sur la table de **l’Ordre.**</span><span class="sxs-lookup"><span data-stu-id="3d784-116">A unique constraint on the **Order** table.</span></span> <span data-ttu-id="3d784-117">Notez que la propriété **IsPrimaryKey** est définie à **True**.</span><span class="sxs-lookup"><span data-stu-id="3d784-117">Note that the **IsPrimaryKey** property is set to **True**.</span></span>  
  
    ```text  
    ConstraintName: Constraint1  
    Type: UniqueConstraint  
    Table: Order  
    Columns: Order_Id
    IsPrimaryKey: True  
    ```  
  
- <span data-ttu-id="3d784-118">Une contrainte clé étrangère sur la table **OrderDetail.**</span><span class="sxs-lookup"><span data-stu-id="3d784-118">A foreign key constraint on the **OrderDetail** table.</span></span>  
  
    ```text  
    ConstraintName: Order_OrderDetail  
    Type: ForeignKeyConstraint  
    Table: OrderDetail  
    Columns: Order_Id
    RelatedTable: Order  
    RelatedColumns: Order_Id
    ```  
  
- <span data-ttu-id="3d784-119">Une relation entre les tables **Order** et **OrderDetail.**</span><span class="sxs-lookup"><span data-stu-id="3d784-119">A relationship between the **Order** and **OrderDetail** tables.</span></span> <span data-ttu-id="3d784-120">La propriété **nichée** pour cette relation est définie à **Vrai** parce que les éléments **De l’Ordre** et **de l’Ordre** sont imbriqués dans le schéma.</span><span class="sxs-lookup"><span data-stu-id="3d784-120">The **Nested** property for this relationship is set to **True** because the **Order** and **OrderDetail** elements are nested in the schema.</span></span>  
  
    ```text  
    ParentTable: Order  
    ParentColumns: Order_Id
    ChildTable: OrderDetail  
    ChildColumns: Order_Id
    ParentKeyConstraint: Constraint1  
    ChildKeyConstraint: Order_OrderDetail  
    RelationName: Order_OrderDetail  
    Nested: True  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="3d784-121">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3d784-121">See also</span></span>

- [<span data-ttu-id="3d784-122">Génération de relations de DataSet à partir du schéma XML (XSD)</span><span class="sxs-lookup"><span data-stu-id="3d784-122">Generating DataSet Relations from XML Schema (XSD)</span></span>](generating-dataset-relations-from-xml-schema-xsd.md)
- [<span data-ttu-id="3d784-123">Mappage des contraintes de schéma XML (XSD) aux contraintes de DataSet</span><span class="sxs-lookup"><span data-stu-id="3d784-123">Mapping XML Schema (XSD) Constraints to DataSet Constraints</span></span>](mapping-xml-schema-xsd-constraints-to-dataset-constraints.md)
- [<span data-ttu-id="3d784-124">Vue d'ensemble d’ADO.NET</span><span class="sxs-lookup"><span data-stu-id="3d784-124">ADO.NET Overview</span></span>](../ado-net-overview.md)
