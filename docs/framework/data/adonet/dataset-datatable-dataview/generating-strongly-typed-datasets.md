---
title: Génération de datasets fortement typés
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 54333cbf-bb43-4314-a7d4-6dc1dd1c44b3
ms.openlocfilehash: 198d7f616d843a3c90b8d32cf33096ee253d2935
ms.sourcegitcommit: 34593b4d0be779699d38a9949d6aec11561657ec
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/11/2019
ms.locfileid: "66832737"
---
# <a name="generating-strongly-typed-datasets"></a><span data-ttu-id="d7611-102">Génération de datasets fortement typés</span><span class="sxs-lookup"><span data-stu-id="d7611-102">Generating Strongly Typed DataSets</span></span>
<span data-ttu-id="d7611-103">Étant donné un schéma XML qui est conforme avec le langage XML Schema definition (XSD) standard, vous pouvez générer fortement typé <xref:System.Data.DataSet> à l’aide de l’outil XSD.exe fourni avec le Kit de développement logiciel (SDK) Windows.</span><span class="sxs-lookup"><span data-stu-id="d7611-103">Given an XML Schema that complies with the XML Schema definition language (XSD) standard, you can generate a strongly typed <xref:System.Data.DataSet> using the XSD.exe tool provided with the Windows Software Development Kit (SDK).</span></span>  
  
 <span data-ttu-id="d7611-104">(Pour créer un xsd à partir des tables de base de données, consultez <xref:System.Data.DataSet.WriteXmlSchema%2A> ou [utilisation de Datasets dans Visual Studio](/visualstudio/data-tools/dataset-tools-in-visual-studio)).</span><span class="sxs-lookup"><span data-stu-id="d7611-104">(To create an xsd from database tables, see <xref:System.Data.DataSet.WriteXmlSchema%2A> or [Working with Datasets in Visual Studio](/visualstudio/data-tools/dataset-tools-in-visual-studio)).</span></span>  
  
 <span data-ttu-id="d7611-105">Le code suivant montre la syntaxe permettant de générer un **DataSet** à l’aide de cet outil.</span><span class="sxs-lookup"><span data-stu-id="d7611-105">The following code shows the syntax for generating a **DataSet** using this tool.</span></span>  
  
```  
xsd.exe /d /l:CS XSDSchemaFileName.xsd /eld /n:XSDSchema.Namespace  
```  
  
 <span data-ttu-id="d7611-106">Dans cette syntaxe, la `/d` directive indique à l’outil pour générer un **DataSet**et le `/l:` indique le langage à utiliser (par exemple, c# ou Visual Basic .NET).</span><span class="sxs-lookup"><span data-stu-id="d7611-106">In this syntax, the `/d` directive tells the tool to generate a **DataSet**, and the `/l:` tells the tool what language to use (for example, C# or Visual Basic .NET).</span></span> <span data-ttu-id="d7611-107">Le paramètre facultatif `/eld` directive spécifie que vous pouvez utiliser [!INCLUDE[linq_dataset](../../../../../includes/linq-dataset-md.md)] à interroger le généré **jeu de données.**</span><span class="sxs-lookup"><span data-stu-id="d7611-107">The optional `/eld` directive specifies that you can use [!INCLUDE[linq_dataset](../../../../../includes/linq-dataset-md.md)] to query against the generated **DataSet.**</span></span> <span data-ttu-id="d7611-108">Cette option est utilisée lorsque l'option `/d` est également spécifiée.</span><span class="sxs-lookup"><span data-stu-id="d7611-108">This option is used when the `/d` option is also specified.</span></span> <span data-ttu-id="d7611-109">Pour plus d’informations, consultez [interrogation de DataSets typés](../../../../../docs/framework/data/adonet/querying-typed-datasets.md).</span><span class="sxs-lookup"><span data-stu-id="d7611-109">For more information, see [Querying Typed DataSets](../../../../../docs/framework/data/adonet/querying-typed-datasets.md).</span></span> <span data-ttu-id="d7611-110">Le paramètre facultatif `/n:` directive indique à l’outil génère également un espace de noms pour le **DataSet** appelé **XSDSchema.Namespace**.</span><span class="sxs-lookup"><span data-stu-id="d7611-110">The optional `/n:` directive tells the tool to also generate a namespace for the **DataSet** called **XSDSchema.Namespace**.</span></span> <span data-ttu-id="d7611-111">La commande donne en sortie un fichier XSDSchemaFileName.cs, qui peut être compilé et utilisé dans une application ADO.NET.</span><span class="sxs-lookup"><span data-stu-id="d7611-111">The output of the command is XSDSchemaFileName.cs, which can be compiled and used in an ADO.NET application.</span></span> <span data-ttu-id="d7611-112">Le code généré peut être compilé sous la forme d'une bibliothèque ou d'un module.</span><span class="sxs-lookup"><span data-stu-id="d7611-112">The generated code can be compiled as a library or a module.</span></span>  
  
 <span data-ttu-id="d7611-113">Le code suivant montre la syntaxe permettant de compiler le code généré sous la forme d'une bibliothèque à l'aide du compilateur C# (csc.exe).</span><span class="sxs-lookup"><span data-stu-id="d7611-113">The following code shows the syntax for compiling the generated code as a library using the C# compiler (csc.exe).</span></span>  
  
```  
csc.exe /t:library XSDSchemaFileName.cs /r:System.dll /r:System.Data.dll  
```  
  
 <span data-ttu-id="d7611-114">La directive `/t:` donne à l'outil l'ordre de compiler en bibliothèque et les directives `/r:` spécifient les bibliothèques dépendantes requises pour la compilation.</span><span class="sxs-lookup"><span data-stu-id="d7611-114">The `/t:` directive tells the tool to compile to a library, and the `/r:` directives specify dependent libraries required to compile.</span></span> <span data-ttu-id="d7611-115">La commande donne en sortie un fichier XSDSchemaFileName.dll, qui peut être passé au compilateur au moment de la compilation d'une application ADO.NET avec la directive `/r:`.</span><span class="sxs-lookup"><span data-stu-id="d7611-115">The output of the command is XSDSchemaFileName.dll, which can be passed to the compiler when compiling an ADO.NET application with the `/r:` directive.</span></span>  
  
 <span data-ttu-id="d7611-116">Le code suivant montre la syntaxe permettant d'accéder à l'espace de noms passé à XSD.exe dans une application ADO.NET.</span><span class="sxs-lookup"><span data-stu-id="d7611-116">The following code shows the syntax for accessing the namespace passed to XSD.exe in an ADO.NET application.</span></span>  
  
```vb  
Imports XSDSchema.Namespace  
```  
  
```csharp  
using XSDSchema.Namespace;  
```  
  
 <span data-ttu-id="d7611-117">L’exemple de code suivant utilise un typé **DataSet** nommé **CustomerDataSet** pour charger une liste de clients à partir de la **Northwind** base de données.</span><span class="sxs-lookup"><span data-stu-id="d7611-117">The following code example uses a typed **DataSet** named **CustomerDataSet** to load a list of customers from the **Northwind** database.</span></span> <span data-ttu-id="d7611-118">Une fois que les données sont chargées à l’aide de la **remplir** (méthode), l’exemple boucle sur chaque client dans le **clients** table à l’aide de typée **CustomersRow** ( **DataRow**) objet.</span><span class="sxs-lookup"><span data-stu-id="d7611-118">Once the data is loaded using the **Fill** method, the example loops through each customer in the **Customers** table using the typed **CustomersRow** (**DataRow**) object.</span></span> <span data-ttu-id="d7611-119">Cela offre un accès direct à la **CustomerID** colonne, plutôt que via le **DataColumnCollection**.</span><span class="sxs-lookup"><span data-stu-id="d7611-119">This provides direct access to the **CustomerID** column, as opposed to through the **DataColumnCollection**.</span></span>  
  
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
  
 <span data-ttu-id="d7611-120">Vous trouverez ci-après le schéma XML utilisé pour l'exemple.</span><span class="sxs-lookup"><span data-stu-id="d7611-120">Following is the XML Schema used for the example.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="d7611-121">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d7611-121">See also</span></span>

- <xref:System.Data.DataColumnCollection>
- <xref:System.Data.DataSet>
- [<span data-ttu-id="d7611-122">Datasets typés</span><span class="sxs-lookup"><span data-stu-id="d7611-122">Typed DataSets</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/typed-datasets.md)
- [<span data-ttu-id="d7611-123">DataSets, DataTables et DataViews</span><span class="sxs-lookup"><span data-stu-id="d7611-123">DataSets, DataTables, and DataViews</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)
- [<span data-ttu-id="d7611-124">Fournisseurs managés ADO.NET et centre de développement DataSet</span><span class="sxs-lookup"><span data-stu-id="d7611-124">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
