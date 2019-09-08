---
title: Génération de datasets fortement typés
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 54333cbf-bb43-4314-a7d4-6dc1dd1c44b3
ms.openlocfilehash: f1c1fd77bed700fae8e5a658da8b267120518ca9
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70786306"
---
# <a name="generating-strongly-typed-datasets"></a><span data-ttu-id="85d9e-102">Génération de datasets fortement typés</span><span class="sxs-lookup"><span data-stu-id="85d9e-102">Generating Strongly Typed DataSets</span></span>
<span data-ttu-id="85d9e-103">À partir d’un schéma XML conforme à la norme XSD (XML Schema Definition Language), vous pouvez générer un fortement typé <xref:System.Data.DataSet> à l’aide de l’outil Xsd. exe fourni avec le kit de développement logiciel (SDK) Windows.</span><span class="sxs-lookup"><span data-stu-id="85d9e-103">Given an XML Schema that complies with the XML Schema definition language (XSD) standard, you can generate a strongly typed <xref:System.Data.DataSet> using the XSD.exe tool provided with the Windows Software Development Kit (SDK).</span></span>  
  
 <span data-ttu-id="85d9e-104">(Pour créer un XSD à partir de tables de <xref:System.Data.DataSet.WriteXmlSchema%2A> base de données, consultez ou [utilisation de datasets dans Visual Studio](/visualstudio/data-tools/dataset-tools-in-visual-studio)).</span><span class="sxs-lookup"><span data-stu-id="85d9e-104">(To create an xsd from database tables, see <xref:System.Data.DataSet.WriteXmlSchema%2A> or [Working with Datasets in Visual Studio](/visualstudio/data-tools/dataset-tools-in-visual-studio)).</span></span>  
  
 <span data-ttu-id="85d9e-105">Le code suivant montre la syntaxe permettant de générer un **DataSet** à l’aide de cet outil.</span><span class="sxs-lookup"><span data-stu-id="85d9e-105">The following code shows the syntax for generating a **DataSet** using this tool.</span></span>  
  
```  
xsd.exe /d /l:CS XSDSchemaFileName.xsd /eld /n:XSDSchema.Namespace  
```  
  
 <span data-ttu-id="85d9e-106">Dans cette syntaxe, la `/d` directive indique à l’outil de générer un **DataSet**, et `/l:` indique à l’outil le langage à utiliser (par exemple C# , ou Visual Basic .net).</span><span class="sxs-lookup"><span data-stu-id="85d9e-106">In this syntax, the `/d` directive tells the tool to generate a **DataSet**, and the `/l:` tells the tool what language to use (for example, C# or Visual Basic .NET).</span></span> <span data-ttu-id="85d9e-107">La directive `/eld` facultative spécifie que vous pouvez utiliser LINQ to DataSet pour effectuer une requête sur le **jeu de données généré.**</span><span class="sxs-lookup"><span data-stu-id="85d9e-107">The optional `/eld` directive specifies that you can use LINQ to DataSet to query against the generated **DataSet.**</span></span> <span data-ttu-id="85d9e-108">Cette option est utilisée lorsque l'option `/d` est également spécifiée.</span><span class="sxs-lookup"><span data-stu-id="85d9e-108">This option is used when the `/d` option is also specified.</span></span> <span data-ttu-id="85d9e-109">Pour plus d’informations, consultez [interrogation de datasets typés](../querying-typed-datasets.md).</span><span class="sxs-lookup"><span data-stu-id="85d9e-109">For more information, see [Querying Typed DataSets](../querying-typed-datasets.md).</span></span> <span data-ttu-id="85d9e-110">La directive `/n:` facultative indique à l’outil de générer également un espace de noms pour le **DataSet** appelé **xsdschema. Namespace**.</span><span class="sxs-lookup"><span data-stu-id="85d9e-110">The optional `/n:` directive tells the tool to also generate a namespace for the **DataSet** called **XSDSchema.Namespace**.</span></span> <span data-ttu-id="85d9e-111">La commande donne en sortie un fichier XSDSchemaFileName.cs, qui peut être compilé et utilisé dans une application ADO.NET.</span><span class="sxs-lookup"><span data-stu-id="85d9e-111">The output of the command is XSDSchemaFileName.cs, which can be compiled and used in an ADO.NET application.</span></span> <span data-ttu-id="85d9e-112">Le code généré peut être compilé sous la forme d'une bibliothèque ou d'un module.</span><span class="sxs-lookup"><span data-stu-id="85d9e-112">The generated code can be compiled as a library or a module.</span></span>  
  
 <span data-ttu-id="85d9e-113">Le code suivant montre la syntaxe permettant de compiler le code généré sous la forme d'une bibliothèque à l'aide du compilateur C# (csc.exe).</span><span class="sxs-lookup"><span data-stu-id="85d9e-113">The following code shows the syntax for compiling the generated code as a library using the C# compiler (csc.exe).</span></span>  
  
```  
csc.exe /t:library XSDSchemaFileName.cs /r:System.dll /r:System.Data.dll  
```  
  
 <span data-ttu-id="85d9e-114">La directive `/t:` donne à l'outil l'ordre de compiler en bibliothèque et les directives `/r:` spécifient les bibliothèques dépendantes requises pour la compilation.</span><span class="sxs-lookup"><span data-stu-id="85d9e-114">The `/t:` directive tells the tool to compile to a library, and the `/r:` directives specify dependent libraries required to compile.</span></span> <span data-ttu-id="85d9e-115">La commande donne en sortie un fichier XSDSchemaFileName.dll, qui peut être passé au compilateur au moment de la compilation d'une application ADO.NET avec la directive `/r:`.</span><span class="sxs-lookup"><span data-stu-id="85d9e-115">The output of the command is XSDSchemaFileName.dll, which can be passed to the compiler when compiling an ADO.NET application with the `/r:` directive.</span></span>  
  
 <span data-ttu-id="85d9e-116">Le code suivant montre la syntaxe permettant d'accéder à l'espace de noms passé à XSD.exe dans une application ADO.NET.</span><span class="sxs-lookup"><span data-stu-id="85d9e-116">The following code shows the syntax for accessing the namespace passed to XSD.exe in an ADO.NET application.</span></span>  
  
```vb  
Imports XSDSchema.Namespace  
```  
  
```csharp  
using XSDSchema.Namespace;  
```  
  
 <span data-ttu-id="85d9e-117">L’exemple de code suivant utilise un **DataSet** typé nommé **CustomerDataSet** pour charger une liste de clients à partir de la base de données **Northwind** .</span><span class="sxs-lookup"><span data-stu-id="85d9e-117">The following code example uses a typed **DataSet** named **CustomerDataSet** to load a list of customers from the **Northwind** database.</span></span> <span data-ttu-id="85d9e-118">Une fois les données chargées à l’aide de la méthode **Fill** , l’exemple parcourt chaque client de la table **Customers** à l’aide de l’objet typé **CustomersRow** (**DataRow**).</span><span class="sxs-lookup"><span data-stu-id="85d9e-118">Once the data is loaded using the **Fill** method, the example loops through each customer in the **Customers** table using the typed **CustomersRow** (**DataRow**) object.</span></span> <span data-ttu-id="85d9e-119">Cela permet d’accéder directement à la colonne **CustomerID** , par opposition au **DataColumnCollection**.</span><span class="sxs-lookup"><span data-stu-id="85d9e-119">This provides direct access to the **CustomerID** column, as opposed to through the **DataColumnCollection**.</span></span>  
  
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
  
 <span data-ttu-id="85d9e-120">Vous trouverez ci-après le schéma XML utilisé pour l'exemple.</span><span class="sxs-lookup"><span data-stu-id="85d9e-120">Following is the XML Schema used for the example.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="85d9e-121">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="85d9e-121">See also</span></span>

- <xref:System.Data.DataColumnCollection>
- <xref:System.Data.DataSet>
- [<span data-ttu-id="85d9e-122">Datasets typés</span><span class="sxs-lookup"><span data-stu-id="85d9e-122">Typed DataSets</span></span>](typed-datasets.md)
- [<span data-ttu-id="85d9e-123">DataSets, DataTables et DataViews</span><span class="sxs-lookup"><span data-stu-id="85d9e-123">DataSets, DataTables, and DataViews</span></span>](index.md)
- [<span data-ttu-id="85d9e-124">Vue d’ensemble d’ADO.NET</span><span class="sxs-lookup"><span data-stu-id="85d9e-124">ADO.NET Overview</span></span>](../ado-net-overview.md)
