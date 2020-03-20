---
title: Mapper les relations spécifiées pour les éléments imbriqués
ms.date: 03/30/2017
ms.assetid: 24a2d3e5-4af7-4f9a-ab7a-fe6684c9e4fe
ms.openlocfilehash: cd652f51f01dcfa16a8b707f35c658043c20670d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79150894"
---
# <a name="map-relations-specified-for-nested-elements"></a><span data-ttu-id="9eff0-102">Mapper les relations spécifiées pour les éléments imbriqués</span><span class="sxs-lookup"><span data-stu-id="9eff0-102">Map Relations Specified for Nested Elements</span></span>
<span data-ttu-id="9eff0-103">Un schéma peut inclure une **msdata:Relationship** annotation pour spécifier explicitement la cartographie entre deux éléments du schéma.</span><span class="sxs-lookup"><span data-stu-id="9eff0-103">A schema can include an **msdata:Relationship** annotation to explicitly specify the mapping between any two elements in the schema.</span></span> <span data-ttu-id="9eff0-104">Les deux éléments spécifiés dans **msdata:Relation** peut être imbriqué dans le schéma, mais n’ont pas à être.</span><span class="sxs-lookup"><span data-stu-id="9eff0-104">The two elements specified in **msdata:Relationship** can be nested in the schema, but do not have to be.</span></span> <span data-ttu-id="9eff0-105">Le processus de cartographie utilise **msdata:Relation** dans le schéma pour générer la clé principale / relation clé étrangère entre les deux colonnes.</span><span class="sxs-lookup"><span data-stu-id="9eff0-105">The mapping process uses **msdata:Relationship** in the schema to generate the primary key/foreign key relationship between the two columns.</span></span>  
  
 <span data-ttu-id="9eff0-106">L’exemple suivant montre un schéma XML dans lequel **l’élément OrderDetail** est un élément enfant de **l’Ordre**.</span><span class="sxs-lookup"><span data-stu-id="9eff0-106">The following example shows an XML Schema in which the **OrderDetail** element is a child element of **Order**.</span></span> <span data-ttu-id="9eff0-107">La **msdata:Relation** identifie cette relation parent-enfant et précise que la colonne **OrderNumber** de la table de **l’Ordre** qui en résulte est liée à la colonne **OrderNo** de la table **OrderDetail** résultant.</span><span class="sxs-lookup"><span data-stu-id="9eff0-107">The **msdata:Relationship** identifies this parent-child relationship and specifies that the **OrderNumber** column of the resulting **Order** table is related to the **OrderNo** column of the resulting **OrderDetail** table.</span></span>  
  
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
          <xs:annotation>  
           <xs:appinfo>  
            <msdata:Relationship name="OrdODRelation"
                                msdata:parent="Order"
                                msdata:child="OrderDetail"
                                msdata:parentkey="OrderNumber"
                                msdata:childkey="OrderNo"/>  
           </xs:appinfo>  
          </xs:annotation>  
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
  
 <span data-ttu-id="9eff0-108">Le processus de mappage du schéma XML crée les éléments suivants dans le <xref:System.Data.DataSet> :</span><span class="sxs-lookup"><span data-stu-id="9eff0-108">The XML Schema mapping process creates the following in the <xref:System.Data.DataSet>:</span></span>  
  
- <span data-ttu-id="9eff0-109">Une **commande** et une table **OrderDetail.**</span><span class="sxs-lookup"><span data-stu-id="9eff0-109">An **Order** and an **OrderDetail** table.</span></span>  
  
    ```text  
    Order(OrderNumber, EmpNumber)  
    OrderDetail(OrderNo, ItemNo)  
    ```  
  
- <span data-ttu-id="9eff0-110">Une relation entre les tables **Order** et **OrderDetail.**</span><span class="sxs-lookup"><span data-stu-id="9eff0-110">A relationship between the **Order** and **OrderDetail** tables.</span></span> <span data-ttu-id="9eff0-111">La propriété **nichée** pour cette relation est définie à **Vrai** parce que les éléments **De l’Ordre** et **de l’Ordre** sont imbriqués dans le schéma.</span><span class="sxs-lookup"><span data-stu-id="9eff0-111">The **Nested** property for this relationship is set to **True** because the **Order** and **OrderDetail** elements are nested in the schema.</span></span>  
  
    ```text  
    ParentTable: Order  
    ParentColumns: OrderNumber
    ChildTable: OrderDetail  
    ChildColumns: OrderNo
    RelationName: OrdODRelation  
    Nested: True  
    ```  
  
 <span data-ttu-id="9eff0-112">Le processus de mappage ne crée aucune contrainte.</span><span class="sxs-lookup"><span data-stu-id="9eff0-112">The mapping process does not create any constraints.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9eff0-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9eff0-113">See also</span></span>

- [<span data-ttu-id="9eff0-114">Génération de relations de DataSet à partir du schéma XML (XSD)</span><span class="sxs-lookup"><span data-stu-id="9eff0-114">Generating DataSet Relations from XML Schema (XSD)</span></span>](generating-dataset-relations-from-xml-schema-xsd.md)
- [<span data-ttu-id="9eff0-115">Mappage des contraintes de schéma XML (XSD) aux contraintes de DataSet</span><span class="sxs-lookup"><span data-stu-id="9eff0-115">Mapping XML Schema (XSD) Constraints to DataSet Constraints</span></span>](mapping-xml-schema-xsd-constraints-to-dataset-constraints.md)
- [<span data-ttu-id="9eff0-116">Vue d'ensemble d’ADO.NET</span><span class="sxs-lookup"><span data-stu-id="9eff0-116">ADO.NET Overview</span></span>](../ado-net-overview.md)
