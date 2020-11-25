---
title: Comparaison d'objets à l'aide de XmlNameTable
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 8d94e041-d340-4ddf-9a2c-d7319e3f4f86
ms.openlocfilehash: 5e0f5de6fd956bcaaf30b592e04c432a5f824c52
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95734099"
---
# <a name="object-comparison-using-xmlnametable"></a><span data-ttu-id="fb63e-102">Comparaison d'objets à l'aide de XmlNameTable</span><span class="sxs-lookup"><span data-stu-id="fb63e-102">Object Comparison Using XmlNameTable</span></span>

<span data-ttu-id="fb63e-103">Durant la création d'un objet **XmlDocument**, une table de noms est spécialement créée à l'intention de ce document.</span><span class="sxs-lookup"><span data-stu-id="fb63e-103">**XmlDocuments**, when created, have a name table created specifically for that document.</span></span> <span data-ttu-id="fb63e-104">Quand les données XML sont chargées dans le document ou que de nouveaux éléments ou attributs sont créés, les noms d'attributs et d'éléments sont placés dans **XmlNameTable**.</span><span class="sxs-lookup"><span data-stu-id="fb63e-104">When XML is loaded into the document, or new elements or attributes are created, the attribute and element names are put into the **XmlNameTable**.</span></span> <span data-ttu-id="fb63e-105">Vous pouvez également créer un **XmlDocument** en utilisant un **NameTable** existant issu d'un autre document.</span><span class="sxs-lookup"><span data-stu-id="fb63e-105">You can also create an **XmlDocument** using an existing **NameTable** from another document.</span></span> <span data-ttu-id="fb63e-106">Quand des **XmlDocument** sont créés avec le constructeur qui prend un paramètre **XmlNameTable**, le document a accès aux préfixes, aux espaces de noms et aux noms de nœud déjà stockés dans **XmlNameTable**.</span><span class="sxs-lookup"><span data-stu-id="fb63e-106">When **XmlDocuments** are created with the constructor that takes an **XmlNameTable** parameter, the document has access to the node names, namespaces, and prefixes already stored in the **XmlNameTable**.</span></span> <span data-ttu-id="fb63e-107">Quelle que soit la manière dont les noms sont chargés dans la table de noms, une fois les noms stockés dans la table, ils peuvent être comparés rapidement par la comparaison d'objets et non au moyen de la comparaison de chaînes.</span><span class="sxs-lookup"><span data-stu-id="fb63e-107">Regardless of how the name table is loaded with names, once the names are stored in the table, names can be compared quickly using object comparison instead of string comparison.</span></span> <span data-ttu-id="fb63e-108">Des chaînes peuvent également être ajoutées à la table de noms à l'aide de la <xref:System.Xml.NameTable.Add%2A>.</span><span class="sxs-lookup"><span data-stu-id="fb63e-108">Strings can also be added to the name table using the <xref:System.Xml.NameTable.Add%2A>.</span></span> <span data-ttu-id="fb63e-109">L'exemple de code suivant illustre la création d'une table de noms et l'ajout de la chaîne **MyString** à cette table.</span><span class="sxs-lookup"><span data-stu-id="fb63e-109">The following code sample shows a name table being created and the string **MyString** being added to the table.</span></span> <span data-ttu-id="fb63e-110">Un **XmlDocument** est ensuite créé au moyen de cette table, et les noms d'éléments et d'attributs de **Myfile.xml** sont ajoutés à la table de noms existante.</span><span class="sxs-lookup"><span data-stu-id="fb63e-110">After that, an **XmlDocument** is created using that table, and the element and attribute names in **Myfile.xml** are added to the existing name table.</span></span>  
  
```vb  
Dim nt As New NameTable()  
nt.Add("MyString")  
Dim doc As New XmlDocument(nt)  
doc.Load("Myfile.xml")  
```  
  
```csharp  
NameTable nt = new NameTable();  
nt.Add("MyString");  
XmlDocument doc = new XmlDocument(nt);  
doc.Load("Myfile.xml");  
```  
  
 <span data-ttu-id="fb63e-111">L'exemple de code suivant illustre la création d'un document, l'ajout de deux nouveaux éléments au document, qui les ajoute par ailleurs à sa table de noms, et l'exécution d'une comparaison d'objets sur les noms.</span><span class="sxs-lookup"><span data-stu-id="fb63e-111">The following code example shows the creation of a document, two new elements being added to the document, which also adds them to the document name table, and the object comparison on the names.</span></span>  
  
```vb  
Dim doc1 As XmlDocument = imp.CreateDocument()  
Dim node1 As XmlElement = doc.CreateElement("node1")  
Dim doc2 As XmlDocument = imp.CreateDocument()  
Dim node2 As XmlElement = doc.CreateElement("node2")  
if (CType(node1.Name, object) = CType(node2.Name, object))  
```  
  
```csharp  
XmlDocument doc1 = imp.CreateDocument();  
node1 = doc1.CreateElement ("node1");  
XmlDocument doc2 = imp.CreateDocument();  
node2 = doc2.CreateElement ("node1");  
if (((object)node1.Name) == ((object)node2.Name))  
{ ...  
```  
  
 <span data-ttu-id="fb63e-112">Le scénario ci-avant, qui montre une table de noms passée entre deux documents, est courant lorsque le même type de document est traité de façon répétée (tel que des documents de commande sur un site de commerce électronique), ces documents étant conformes à un schéma en langage XSD (XML Schema Definition) ou une définition de type de document (DTD) et contenant une répétition des mêmes chaînes.</span><span class="sxs-lookup"><span data-stu-id="fb63e-112">The above scenario of a name table passed between two documents is typical when the same type of document is being processed repeatedly, such as order documents at an ecommerce site, which conform to an XML Schema definition language (XSD) schema or document type definition (DTD) and the same strings are repeated.</span></span> <span data-ttu-id="fb63e-113">L'utilisation de la même table de noms permet d'améliorer les performances puisque le même nom d'élément se retrouve dans plusieurs documents.</span><span class="sxs-lookup"><span data-stu-id="fb63e-113">Using the same name table gives a performance improvement, as the same element name occurs in multiple documents.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fb63e-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="fb63e-114">See also</span></span>

- [<span data-ttu-id="fb63e-115">DOM (Document Object Model) XML</span><span class="sxs-lookup"><span data-stu-id="fb63e-115">XML Document Object Model (DOM)</span></span>](xml-document-object-model-dom.md)
