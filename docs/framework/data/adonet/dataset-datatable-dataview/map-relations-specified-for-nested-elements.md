---
title: Mapper les relations spécifiées pour les éléments imbriqués
ms.date: 03/30/2017
ms.assetid: 24a2d3e5-4af7-4f9a-ab7a-fe6684c9e4fe
ms.openlocfilehash: f758e1ef2c3786a102dc6bb5f6dd217b20dc5b55
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91198546"
---
# <a name="map-relations-specified-for-nested-elements"></a><span data-ttu-id="5cc52-102">Mapper les relations spécifiées pour les éléments imbriqués</span><span class="sxs-lookup"><span data-stu-id="5cc52-102">Map Relations Specified for Nested Elements</span></span>

<span data-ttu-id="5cc52-103">Un schéma peut inclure une annotation **msdata : Relationship** pour spécifier explicitement le mappage entre deux éléments quelconques dans le schéma.</span><span class="sxs-lookup"><span data-stu-id="5cc52-103">A schema can include an **msdata:Relationship** annotation to explicitly specify the mapping between any two elements in the schema.</span></span> <span data-ttu-id="5cc52-104">Les deux éléments spécifiés dans **msdata : Relationship** peuvent être imbriqués dans le schéma, mais n’ont pas besoin d’être.</span><span class="sxs-lookup"><span data-stu-id="5cc52-104">The two elements specified in **msdata:Relationship** can be nested in the schema, but do not have to be.</span></span> <span data-ttu-id="5cc52-105">Le processus de mappage utilise l' **Annotation msdata : Relationship** dans le schéma pour générer la relation clé primaire/clé étrangère entre les deux colonnes.</span><span class="sxs-lookup"><span data-stu-id="5cc52-105">The mapping process uses **msdata:Relationship** in the schema to generate the primary key/foreign key relationship between the two columns.</span></span>  
  
 <span data-ttu-id="5cc52-106">L’exemple suivant illustre un schéma XML dans lequel l’élément **OrderDetail** est un élément enfant de **Order**.</span><span class="sxs-lookup"><span data-stu-id="5cc52-106">The following example shows an XML Schema in which the **OrderDetail** element is a child element of **Order**.</span></span> <span data-ttu-id="5cc52-107">L' **Annotation msdata : Relationship** identifie cette relation parent-enfant et spécifie que la colonne **OrderNumber** de la table **Order** obtenue est associée à la colonne **OrderNo** de la table **OrderDetail** résultante.</span><span class="sxs-lookup"><span data-stu-id="5cc52-107">The **msdata:Relationship** identifies this parent-child relationship and specifies that the **OrderNumber** column of the resulting **Order** table is related to the **OrderNo** column of the resulting **OrderDetail** table.</span></span>  
  
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
  
 <span data-ttu-id="5cc52-108">Le processus de mappage du schéma XML crée les éléments suivants dans le <xref:System.Data.DataSet> :</span><span class="sxs-lookup"><span data-stu-id="5cc52-108">The XML Schema mapping process creates the following in the <xref:System.Data.DataSet>:</span></span>  
  
- <span data-ttu-id="5cc52-109">Une **commande Order** et une table **OrderDetail** .</span><span class="sxs-lookup"><span data-stu-id="5cc52-109">An **Order** and an **OrderDetail** table.</span></span>  
  
    ```text  
    Order(OrderNumber, EmpNumber)  
    OrderDetail(OrderNo, ItemNo)  
    ```  
  
- <span data-ttu-id="5cc52-110">Relation entre les tables **Order** et **OrderDetail** .</span><span class="sxs-lookup"><span data-stu-id="5cc52-110">A relationship between the **Order** and **OrderDetail** tables.</span></span> <span data-ttu-id="5cc52-111">La propriété **Nested** de cette relation a la valeur **true** , car les éléments **Order** et **OrderDetail** sont imbriqués dans le schéma.</span><span class="sxs-lookup"><span data-stu-id="5cc52-111">The **Nested** property for this relationship is set to **True** because the **Order** and **OrderDetail** elements are nested in the schema.</span></span>  
  
    ```text  
    ParentTable: Order  
    ParentColumns: OrderNumber
    ChildTable: OrderDetail  
    ChildColumns: OrderNo
    RelationName: OrdODRelation  
    Nested: True  
    ```  
  
 <span data-ttu-id="5cc52-112">Le processus de mappage ne crée aucune contrainte.</span><span class="sxs-lookup"><span data-stu-id="5cc52-112">The mapping process does not create any constraints.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5cc52-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="5cc52-113">See also</span></span>

- [<span data-ttu-id="5cc52-114">Génération de relations de DataSet à partir du schéma XML (XSD)</span><span class="sxs-lookup"><span data-stu-id="5cc52-114">Generating DataSet Relations from XML Schema (XSD)</span></span>](generating-dataset-relations-from-xml-schema-xsd.md)
- [<span data-ttu-id="5cc52-115">Mappage des contraintes de schéma XML (XSD) aux contraintes de DataSet</span><span class="sxs-lookup"><span data-stu-id="5cc52-115">Mapping XML Schema (XSD) Constraints to DataSet Constraints</span></span>](mapping-xml-schema-xsd-constraints-to-dataset-constraints.md)
- [<span data-ttu-id="5cc52-116">Vue d'ensemble d’ADO.NET</span><span class="sxs-lookup"><span data-stu-id="5cc52-116">ADO.NET Overview</span></span>](../ado-net-overview.md)
