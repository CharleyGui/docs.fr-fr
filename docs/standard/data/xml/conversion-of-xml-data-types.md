---
title: Conversion des types de données XML
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: a2aa99ba-8239-4818-9281-f1d72ee40bde
ms.openlocfilehash: b0cdab8861ca50b40ce2b422fcc1acf16e2f2273
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75711088"
---
# <a name="conversion-of-xml-data-types"></a><span data-ttu-id="ad672-102">Conversion des types de données XML</span><span class="sxs-lookup"><span data-stu-id="ad672-102">Conversion of XML Data Types</span></span>
<span data-ttu-id="ad672-103">La majorité des méthodes présentes dans la classe **XmlConvert** sont utilisées pour la conversion de données entre le format de chaînes et le format fortement typé.</span><span class="sxs-lookup"><span data-stu-id="ad672-103">The majority of the methods found in an **XmlConvert** class are used to convert data between strings and strongly-typed formats.</span></span> <span data-ttu-id="ad672-104">Ces méthodes sont indépendantes des paramètres régionaux.</span><span class="sxs-lookup"><span data-stu-id="ad672-104">Methods are locale independent.</span></span> <span data-ttu-id="ad672-105">Cela signifie qu'elles ne prennent pas en compte les paramètres régionaux éventuels lors de la conversion.</span><span class="sxs-lookup"><span data-stu-id="ad672-105">This means that they do not take into account any locale settings when doing conversion.</span></span>  
  
## <a name="reading-string-as-types"></a><span data-ttu-id="ad672-106">Lecture de chaînes comme des types</span><span class="sxs-lookup"><span data-stu-id="ad672-106">Reading String as types</span></span>  
 <span data-ttu-id="ad672-107">L'exemple suivant lit une chaîne et la convertit en type **DateTime**.</span><span class="sxs-lookup"><span data-stu-id="ad672-107">The following sample reads a string and converts it to a **DateTime** type.</span></span>  
  
 <span data-ttu-id="ad672-108">En supposant l'entrée XML suivante :</span><span class="sxs-lookup"><span data-stu-id="ad672-108">Given the following XML input:</span></span>  
  
 <span data-ttu-id="ad672-109">**Input**</span><span class="sxs-lookup"><span data-stu-id="ad672-109">**Input**</span></span>  
  
```xml  
<Element>2001-02-27T11:13:23</Element>  
```  
  
 <span data-ttu-id="ad672-110">Ce code convertit la chaîne au format **DateTime** :</span><span class="sxs-lookup"><span data-stu-id="ad672-110">This code converts the string to the **DateTime** format:</span></span>  
  
```vb  
reader.ReadStartElement()  
Dim vDateTime As DateTime = XmlConvert.ToDateTime(reader.ReadString())  
Console.WriteLine(vDateTime)  
```  
  
```csharp  
reader.ReadStartElement();  
DateTime vDateTime = XmlConvert.ToDateTime(reader.ReadString());  
Console.WriteLine(vDateTime);  
```  
  
## <a name="writing-strings-as-types"></a><span data-ttu-id="ad672-111">Écriture de chaînes comme des types</span><span class="sxs-lookup"><span data-stu-id="ad672-111">Writing Strings as types</span></span>  
 <span data-ttu-id="ad672-112">L'exemple suivant lit un type **Int32** et le convertit en chaîne.</span><span class="sxs-lookup"><span data-stu-id="ad672-112">The following sample reads an **Int32** and converts it to a string.</span></span>  
  
 <span data-ttu-id="ad672-113">En supposant l'entrée XML suivante :</span><span class="sxs-lookup"><span data-stu-id="ad672-113">Given the following XML input:</span></span>  
  
 <span data-ttu-id="ad672-114">**Input**</span><span class="sxs-lookup"><span data-stu-id="ad672-114">**Input**</span></span>  
  
```xml  
<TestInt32>-2147483648</TestInt32>  
```  
  
 <span data-ttu-id="ad672-115">Ce code convertit le type **Int32** en type **String**:</span><span class="sxs-lookup"><span data-stu-id="ad672-115">This code converts the **Int32** into a **String**:</span></span>  
  
```vb  
Dim vInt32 As Int32 = -2147483648  
writer.WriteElementString("TestInt32", XmlConvert.ToString(vInt32))  
```  
  
```csharp  
Int32 vInt32=-2147483648;  
writer.WriteElementString("TestInt32",XmlConvert.ToString(vInt32));  
```  
  
## <a name="see-also"></a><span data-ttu-id="ad672-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ad672-116">See also</span></span>

- [<span data-ttu-id="ad672-117">Conversion de chaînes en types de données .NET Framework</span><span class="sxs-lookup"><span data-stu-id="ad672-117">Converting Strings to .NET Framework Data Types</span></span>](../../../../docs/standard/data/xml/converting-strings-to-dotnet-data-types.md)
- [<span data-ttu-id="ad672-118">Conversion de types .NET Framework en chaînes</span><span class="sxs-lookup"><span data-stu-id="ad672-118">Converting .NET Framework Types to Strings</span></span>](../../../../docs/standard/data/xml/converting-dotnet-types-to-strings.md)
