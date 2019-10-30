---
title: Dérivation de la structure relationnelle des DataSet à partir du schéma XML (XSD)
ms.date: 03/30/2017
ms.assetid: 8f6cd04d-6197-4bc4-9096-8c51c7e4acae
ms.openlocfilehash: ef77030b4e847f91fea074b68e223ac622539048
ms.sourcegitcommit: ad800f019ac976cb669e635fb0ea49db740e6890
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/29/2019
ms.locfileid: "73040098"
---
# <a name="deriving-dataset-relational-structure-from-xml-schema-xsd"></a><span data-ttu-id="09347-102">Dérivation de la structure relationnelle des DataSet à partir du schéma XML (XSD)</span><span class="sxs-lookup"><span data-stu-id="09347-102">Deriving DataSet Relational Structure from XML Schema (XSD)</span></span>
<span data-ttu-id="09347-103">Cette section propose une vue d'ensemble de la façon dont le schéma relationnel d'un objet `DataSet` est construit à partir d'un document de schéma en langage XSD (XML Schema Definition).</span><span class="sxs-lookup"><span data-stu-id="09347-103">This section provides an overview of how the relational schema of a `DataSet` is built from an XML Schema definition language (XSD) schema document.</span></span> <span data-ttu-id="09347-104">En général, pour chaque `complexType` élément enfant d’un élément de schéma, une table est générée dans le `DataSet`.</span><span class="sxs-lookup"><span data-stu-id="09347-104">In general, for each `complexType` child element of a schema element, a table is generated in the `DataSet`.</span></span> <span data-ttu-id="09347-105">La structure de cette table est déterminée par la définition du type complexe.</span><span class="sxs-lookup"><span data-stu-id="09347-105">The table structure is determined by the definition of the complex type.</span></span> <span data-ttu-id="09347-106">Les tables sont créées dans le `DataSet` pour les éléments de niveau supérieur dans le schéma.</span><span class="sxs-lookup"><span data-stu-id="09347-106">Tables are created in the `DataSet` for top-level elements in the schema.</span></span> <span data-ttu-id="09347-107">Toutefois, une table est créée uniquement pour un élément `complexType` de niveau supérieur lorsque l’élément `complexType` est imbriqué dans un autre élément `complexType`, auquel cas l’élément `complexType` imbriqué est mappé à un `DataTable` dans le `DataSet`.</span><span class="sxs-lookup"><span data-stu-id="09347-107">However, a table is only created for a top-level `complexType` element when the `complexType` element is nested inside another `complexType` element, in which case the nested `complexType` element is mapped to a `DataTable` within the `DataSet`.</span></span>  
  
 <span data-ttu-id="09347-108">Pour plus d’informations sur le langage XSD, consultez World Wide Web Consortium la recommandation XML Schema [part 0 : Primer Recommendation](https://www.w3.org/TR/xmlschema-0/), [XML Schema Part 1 : structures Recommendation](https://www.w3.org/TR/xmlschema-1/)(en anglais) et [XML Schema Part 2 : Datatypes recommendation](https://www.w3.org/TR/xmlschema-2/)(en anglais).</span><span class="sxs-lookup"><span data-stu-id="09347-108">For more information about the XSD, see the World Wide Web Consortium (W3C) [XML Schema Part 0: Primer Recommendation](https://www.w3.org/TR/xmlschema-0/), the [XML Schema Part 1: Structures Recommendation](https://www.w3.org/TR/xmlschema-1/), and the [XML Schema Part 2: Datatypes Recommendation](https://www.w3.org/TR/xmlschema-2/).</span></span>  
  
 <span data-ttu-id="09347-109">L’exemple suivant illustre un schéma XML où `customers` est l’élément enfant de l’élément `MyDataSet`, qui est un élément de **DataSet** .</span><span class="sxs-lookup"><span data-stu-id="09347-109">The following example demonstrates an XML Schema where `customers` is the child element of the `MyDataSet` element, which is a **DataSet** element.</span></span>  
  
```xml  
<xs:schema id="SomeID"   
            xmlns=""   
            xmlns:xs="http://www.w3.org/2001/XMLSchema"   
            xmlns:msdata="urn:schemas-microsoft-com:xml-msdata">  
   <xs:element name="MyDataSet" msdata:IsDataSet="true">  
     <xs:complexType>  
       <xs:choice maxOccurs="unbounded">  
         <xs:element name="customers" >   
           <xs:complexType >  
             <xs:sequence>  
               <xs:element name="CustomerID" type="xs:integer"   
                            minOccurs="0" />  
               <xs:element name="CompanyName" type="xs:string"   
                            minOccurs="0" />  
               <xs:element name="Phone" type="xs:string" />  
             </xs:sequence>  
           </xs:complexType>  
          </xs:element>  
       </xs:choice>  
     </xs:complexType>  
   </xs:element>  
 </xs:schema>  
```  
  
 <span data-ttu-id="09347-110">Dans l'exemple précédent, l'élément `customers` est un élément de type complexe.</span><span class="sxs-lookup"><span data-stu-id="09347-110">In the preceding example, the element `customers` is a complex type element.</span></span> <span data-ttu-id="09347-111">Par conséquent, la définition du type complexe est analysée et le processus de mappage crée la table suivante.</span><span class="sxs-lookup"><span data-stu-id="09347-111">Therefore, the complex type definition is parsed, and the mapping process creates the following table.</span></span>  
  
```text  
Customers (CustomerID, CompanyName, Phone)  
```  
  
 <span data-ttu-id="09347-112">Le type de données de chaque colonne de la table est dérivé du type de schéma XML de l'élément ou de l'attribut spécifié correspondant.</span><span class="sxs-lookup"><span data-stu-id="09347-112">The data type of each column in the table is derived from the XML Schema type of the corresponding element or attribute specified.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="09347-113">Si l’élément `customers` est d’un type de données de schéma XML simple, tel qu’un **entier**, aucune table n’est générée.</span><span class="sxs-lookup"><span data-stu-id="09347-113">If the element `customers` is of a simple XML Schema data type such as **integer**, no table is generated.</span></span> <span data-ttu-id="09347-114">Des tables sont créées uniquement pour les éléments de niveau supérieur de type complexe.</span><span class="sxs-lookup"><span data-stu-id="09347-114">Tables are only created for the top-level elements that are complex types.</span></span>  
  
 <span data-ttu-id="09347-115">Dans le schéma XML suivant, l’élément de **schéma** a deux éléments enfants, `InStateCustomers` et `OutOfStateCustomers`.</span><span class="sxs-lookup"><span data-stu-id="09347-115">In the following XML Schema, the **Schema** element has two element children, `InStateCustomers` and `OutOfStateCustomers`.</span></span>  
  
```xml  
<xs:schema id="SomeID"   
            xmlns=""   
            xmlns:xs="http://www.w3.org/2001/XMLSchema"   
            xmlns:msdata="urn:schemas-microsoft-com:xml-msdata">  
   <xs:element name="InStateCustomers" type="customerType" />  
   <xs:element name="OutOfStateCustomers" type="customerType" />  
    <xs:complexType name="customerType" >  
  
     </xs:complexType>  
  
   <xs:element name="MyDataSet" msdata:IsDataSet="true">  
     <xs:complexType>  
       <xs:choice maxOccurs="unbounded">  
         <xs:element ref="customers" />  
       </xs:choice>  
     </xs:complexType>  
   </xs:element>  
 </xs:schema>  
```  
  
 <span data-ttu-id="09347-116">Les éléments enfants `InStateCustomers` et `OutOfStateCustomers` sont tous deux des éléments de type complexe (`customerType`).</span><span class="sxs-lookup"><span data-stu-id="09347-116">Both the `InStateCustomers` and the `OutOfStateCustomers` child elements are complex type elements (`customerType`).</span></span> <span data-ttu-id="09347-117">Par conséquent, le processus de mappage génère les deux tables identiques suivantes dans le `DataSet`.</span><span class="sxs-lookup"><span data-stu-id="09347-117">Therefore, the mapping process generates the following two identical tables in the `DataSet`.</span></span>  
  
```text  
InStateCustomers (CustomerID, CompanyName, Phone)  
OutOfStateCustomers (CustomerID, CompanyName, Phone)  
```  
  
## <a name="in-this-section"></a><span data-ttu-id="09347-118">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="09347-118">In This Section</span></span>  
 [<span data-ttu-id="09347-119">Mappage des contraintes de schéma XML (XSD) aux contraintes de DataSet</span><span class="sxs-lookup"><span data-stu-id="09347-119">Mapping XML Schema (XSD) Constraints to DataSet Constraints</span></span>](mapping-xml-schema-xsd-constraints-to-dataset-constraints.md)  
 <span data-ttu-id="09347-120">Décrit les éléments de schéma XML utilisés pour créer des contraintes de clé étrangère et uniques dans un `DataSet`.</span><span class="sxs-lookup"><span data-stu-id="09347-120">Describes the XML Schema elements used to create unique and foreign key constraints in a `DataSet`.</span></span>  
  
 [<span data-ttu-id="09347-121">Génération de relations de DataSet à partir du schéma XML (XSD)</span><span class="sxs-lookup"><span data-stu-id="09347-121">Generating DataSet Relations from XML Schema (XSD)</span></span>](generating-dataset-relations-from-xml-schema-xsd.md)  
 <span data-ttu-id="09347-122">Décrit les éléments de schéma XML utilisés pour créer des relations entre des colonnes de table dans un `DataSet`.</span><span class="sxs-lookup"><span data-stu-id="09347-122">Describes the XML Schema elements used to create relations between table columns in a `DataSet`.</span></span>  
  
 [<span data-ttu-id="09347-123">Contraintes et relations du schéma XML</span><span class="sxs-lookup"><span data-stu-id="09347-123">XML Schema Constraints and Relationships</span></span>](xml-schema-constraints-and-relationships.md)  
 <span data-ttu-id="09347-124">Décrit comment les relations sont créées implicitement lors de l’utilisation d’éléments de schéma XML pour créer des contraintes dans un `DataSet`.</span><span class="sxs-lookup"><span data-stu-id="09347-124">Describes how relations are created implicitly when using XML Schema elements to create constraints in a `DataSet`.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="09347-125">Rubriques connexes</span><span class="sxs-lookup"><span data-stu-id="09347-125">Related Sections</span></span>  
 [<span data-ttu-id="09347-126">Utilisation de XML dans un DataSet</span><span class="sxs-lookup"><span data-stu-id="09347-126">Using XML in a DataSet</span></span>](using-xml-in-a-dataset.md)  
 <span data-ttu-id="09347-127">Décrit comment charger et conserver la structure relationnelle et les données dans un `DataSet` en tant que données XML.</span><span class="sxs-lookup"><span data-stu-id="09347-127">Describes how to load and persist the relational structure and data in a `DataSet` as XML data.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="09347-128">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="09347-128">See also</span></span>

- [<span data-ttu-id="09347-129">Vue d’ensemble d’ADO.NET</span><span class="sxs-lookup"><span data-stu-id="09347-129">ADO.NET Overview</span></span>](../ado-net-overview.md)
