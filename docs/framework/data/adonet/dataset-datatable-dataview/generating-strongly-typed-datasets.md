---
title: Génération de datasets fortement typés
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 54333cbf-bb43-4314-a7d4-6dc1dd1c44b3
ms.openlocfilehash: 1c65389c8c5664f86f3f0c04829a2422908d72d1
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91202290"
---
# <a name="generating-strongly-typed-datasets"></a>Génération de datasets fortement typés

À partir d’un schéma XML conforme à la norme XSD (XML Schema Definition Language), vous pouvez générer un fortement typé <xref:System.Data.DataSet> à l’aide de l’outil XSD.exe fourni avec le kit de développement logiciel (SDK) Windows.  
  
 (Pour créer un XSD à partir de tables de base de données, consultez <xref:System.Data.DataSet.WriteXmlSchema%2A> ou [utilisation de datasets dans Visual Studio](/visualstudio/data-tools/dataset-tools-in-visual-studio)).  
  
 Le code suivant montre la syntaxe permettant de générer un **DataSet** à l’aide de cet outil.  
  
```console  
xsd.exe /d /l:CS XSDSchemaFileName.xsd /eld /n:XSDSchema.Namespace  
```  
  
 Dans cette syntaxe, la `/d` directive indique à l’outil de générer un **DataSet**, et `/l:` indique à l’outil le langage à utiliser (par exemple, C# ou Visual Basic .net). La `/eld` directive facultative spécifie que vous pouvez utiliser LINQ to DataSet pour effectuer une requête sur le **jeu de données généré.** Cette option est utilisée lorsque l'option `/d` est également spécifiée. Pour plus d’informations, consultez [interrogation de datasets typés](../querying-typed-datasets.md). La `/n:` directive facultative indique à l’outil de générer également un espace de noms pour le **DataSet** appelé **xsdschema. Namespace**. La commande donne en sortie un fichier XSDSchemaFileName.cs, qui peut être compilé et utilisé dans une application ADO.NET. Le code généré peut être compilé sous la forme d'une bibliothèque ou d'un module.  
  
 Le code suivant montre la syntaxe permettant de compiler le code généré sous la forme d'une bibliothèque à l'aide du compilateur C# (csc.exe).  
  
```console  
csc.exe /t:library XSDSchemaFileName.cs /r:System.dll /r:System.Data.dll  
```  
  
 La directive `/t:` donne à l'outil l'ordre de compiler en bibliothèque et les directives `/r:` spécifient les bibliothèques dépendantes requises pour la compilation. La commande donne en sortie un fichier XSDSchemaFileName.dll, qui peut être passé au compilateur au moment de la compilation d'une application ADO.NET avec la directive `/r:`.  
  
 Le code suivant montre la syntaxe permettant d'accéder à l'espace de noms passé à XSD.exe dans une application ADO.NET.  
  
```vb  
Imports XSDSchema.Namespace  
```  
  
```csharp  
using XSDSchema.Namespace;  
```  
  
 L’exemple de code suivant utilise un **DataSet** typé nommé **CustomerDataSet** pour charger une liste de clients à partir de la base de données **Northwind** . Une fois les données chargées à l’aide de la méthode **Fill** , l’exemple parcourt chaque client de la table **Customers** à l’aide de l’objet typé **CustomersRow** (**DataRow**). Cela permet d’accéder directement à la colonne **CustomerID** , par opposition au **DataColumnCollection**.  
  
```vb  
Dim customers As CustomerDataSet= New CustomerDataSet()  
Dim adapter As SqlDataAdapter New SqlDataAdapter( _  
  "SELECT * FROM dbo.Customers;", _  
  "Data Source=(local);Integrated " & _  
  "Security=SSPI;Initial Catalog=Northwind")  
  
adapter.Fill(customers, "Customers")  
  
Dim customerRow As CustomerDataSet.CustomersRow  
For Each customerRow In customers.Customers  
  Console.WriteLine(customerRow.CustomerID)  
Next  
```  
  
```csharp  
CustomerDataSet customers = new CustomerDataSet();  
SqlDataAdapter adapter = new SqlDataAdapter(  
  "SELECT * FROM dbo.Customers;",  
  "Data Source=(local);Integrated " +  
  "Security=SSPI;Initial Catalog=Northwind");  
  
adapter.Fill(customers, "Customers");  
  
foreach(CustomerDataSet.CustomersRow customerRow in customers.Customers)  
  Console.WriteLine(customerRow.CustomerID);  
```  
  
 Voici le schéma XML utilisé pour l’exemple :
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<xs:schema id="CustomerDataSet" xmlns="" xmlns:xs="http://www.w3.org/2001/XMLSchema" xmlns:msdata="urn:schemas-microsoft-com:xml-msdata">  
  <xs:element name="CustomerDataSet" msdata:IsDataSet="true">  
    <xs:complexType>  
      <xs:choice maxOccurs="unbounded">  
        <xs:element name="Customers">  
          <xs:complexType>  
            <xs:sequence>  
              <xs:element name="CustomerID" type="xs:string" minOccurs="0" />  
            </xs:sequence>  
          </xs:complexType>  
        </xs:element>  
      </xs:choice>  
    </xs:complexType>  
  </xs:element>  
</xs:schema>  
```  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Data.DataColumnCollection>
- <xref:System.Data.DataSet>
- [Datasets typés](typed-datasets.md)
- [DataSets, DataTables et DataViews](index.md)
- [Vue d'ensemble d’ADO.NET](../ado-net-overview.md)
