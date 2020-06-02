---
title: Création d'un document XML
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: 877e9c62-b082-4bfb-bc5b-f47297eb30ef
ms.openlocfilehash: 577d353a30c986d198140b4596ae1a7e199ddd6e
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84291979"
---
# <a name="xml-document-creation"></a><span data-ttu-id="562e2-102">Création d'un document XML</span><span class="sxs-lookup"><span data-stu-id="562e2-102">XML Document Creation</span></span>
<span data-ttu-id="562e2-103">Il existe deux façons de créer un document XML.</span><span class="sxs-lookup"><span data-stu-id="562e2-103">There are two ways to create an XML document.</span></span> <span data-ttu-id="562e2-104">L'une consiste à créer un objet **XmlDocument**, sans paramètre.</span><span class="sxs-lookup"><span data-stu-id="562e2-104">One way is to create an **XmlDocument** with no parameters.</span></span> <span data-ttu-id="562e2-105">L'autre consiste à créer un objet **XmlDocument** et à le passer à XmlNameTable sous la forme d'un paramètre.</span><span class="sxs-lookup"><span data-stu-id="562e2-105">The other way is to create an **XmlDocument** and pass it an XmlNameTable as a parameter.</span></span> <span data-ttu-id="562e2-106">L'exemple suivant indique comment créer un nouveau **XmlDocument** vide dépourvu de paramètre.</span><span class="sxs-lookup"><span data-stu-id="562e2-106">The following example shows how to create a new, empty **XmlDocument** using no parameters.</span></span>  
  
```vb  
Dim doc As New XmlDocument()  
```  
  
```csharp  
XmlDocument doc = new XmlDocument();  
```  
  
 <span data-ttu-id="562e2-107">Une fois le document créé, vous pouvez y charger des données à partir d'une chaîne, d'un flux, d'une URL, d'un lecteur de texte ou d'une classe dérivée **XmlReader** à l'aide de la méthode **Load**.</span><span class="sxs-lookup"><span data-stu-id="562e2-107">Once a document is created, you can load it with data from a string, stream, URL, text reader, or an **XmlReader** derived class using the **Load** method.</span></span> <span data-ttu-id="562e2-108">Il existe également une autre méthode de chargement, appelée **LoadXML**, qui lit le contenu XML d'une chaîne.</span><span class="sxs-lookup"><span data-stu-id="562e2-108">There is also another load method, the **LoadXML** method, which reads XML from a string.</span></span> <span data-ttu-id="562e2-109">Pour plus d'informations sur les diverses méthodes **Load**, consultez [Lecture d'un document XML vers le DOM](reading-an-xml-document-into-the-dom.md).</span><span class="sxs-lookup"><span data-stu-id="562e2-109">For more information on the various **Load** methods, see [Reading an XML Document into the DOM](reading-an-xml-document-into-the-dom.md).</span></span>  
  
 <span data-ttu-id="562e2-110">Il existe une classe appelée **XmlNameTable**.</span><span class="sxs-lookup"><span data-stu-id="562e2-110">There is a class called the **XmlNameTable**.</span></span> <span data-ttu-id="562e2-111">Cette classe est une table d'objets chaîne atomisés.</span><span class="sxs-lookup"><span data-stu-id="562e2-111">This class is a table of atomized string objects.</span></span> <span data-ttu-id="562e2-112">Cette table constitue un moyen efficace pour que l'analyseur XML utilise le même objet chaîne pour tous les noms d'éléments et d'attributs répétés dans un document XML.</span><span class="sxs-lookup"><span data-stu-id="562e2-112">This table provides an efficient means for the XML parser to use the same string object for all repeated element and attribute names in an XML document.</span></span> <span data-ttu-id="562e2-113">Un objet **XmlNameTable** est créé automatiquement lors de la création d'un document, comme le montre l'exemple ci-avant, et est chargé avec des noms d'attributs et d'éléments lors du chargement du document.</span><span class="sxs-lookup"><span data-stu-id="562e2-113">An **XmlNameTable** is automatically created when a document is created as shown above and is loaded with attribute and element names when the document is loaded.</span></span> <span data-ttu-id="562e2-114">Si vous disposez déjà d'un document possédant une table de noms, et que ces noms pourraient être employés utilement dans un autre document, vous pouvez créer un nouveau document à l'aide de la méthode **Load** qui prend **XmlNameTable** comme paramètre.</span><span class="sxs-lookup"><span data-stu-id="562e2-114">If you already have a document with a name table, and those names would be useful in another document, you can create a new document using the **Load** method that takes an **XmlNameTable** as a parameter.</span></span> <span data-ttu-id="562e2-115">Lorsque le document est créé avec cette méthode, il utilise le **XmlNameTable** existant avec tous les attributs et éléments déjà chargés en son sein à partir de l'autre document.</span><span class="sxs-lookup"><span data-stu-id="562e2-115">When the document is created with this method, it uses the existing **XmlNameTable** with all the attributes and elements already loaded into it from the other document.</span></span> <span data-ttu-id="562e2-116">Celui-ci peut être employé pour comparer efficacement des noms d'éléments et d'attributs.</span><span class="sxs-lookup"><span data-stu-id="562e2-116">It can be used for efficiently comparing element and attribute names.</span></span> <span data-ttu-id="562e2-117">Pour plus d'informations sur **XmlNameTable**, consultez [Comparaison d'objets à l'aide de XmlNameTable](object-comparison-using-xmlnametable.md).</span><span class="sxs-lookup"><span data-stu-id="562e2-117">For more information on the **XmlNameTable**, see [Object Comparison Using XmlNameTable](object-comparison-using-xmlnametable.md).</span></span> <span data-ttu-id="562e2-118">Pour référence, consultez <xref:System.Xml.XmlNameTable>.</span><span class="sxs-lookup"><span data-stu-id="562e2-118">For reference, see <xref:System.Xml.XmlNameTable>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="562e2-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="562e2-119">See also</span></span>

- [<span data-ttu-id="562e2-120">DOM (Document Object Model) XML</span><span class="sxs-lookup"><span data-stu-id="562e2-120">XML Document Object Model (DOM)</span></span>](xml-document-object-model-dom.md)
