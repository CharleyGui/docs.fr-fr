---
title: Modification des propriétés de préfixe d'espace de noms
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: d5c87cbe-4d69-429f-aad5-3103c2ca2770
ms.openlocfilehash: b1df520d00d3a98b2e518092d4eff51b5d0b7741
ms.sourcegitcommit: 00aa62e2f469c2272a457b04e66b4cc3c97a800b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/28/2020
ms.locfileid: "78158023"
---
# <a name="changing-namespace-prefix-properties"></a><span data-ttu-id="52e21-102">Modification des propriétés de préfixe d'espace de noms</span><span class="sxs-lookup"><span data-stu-id="52e21-102">Changing Namespace Prefix Properties</span></span>
<span data-ttu-id="52e21-103">La classe **XmlNode** vous permet de modifier le préfixe d'espace de noms associé à un nœud précis.</span><span class="sxs-lookup"><span data-stu-id="52e21-103">The **XmlNode** class allows you to change the namespace prefix associated with a given node.</span></span> <span data-ttu-id="52e21-104">Par exemple, le code suivant montre la modification du préfixe d'un élément.</span><span class="sxs-lookup"><span data-stu-id="52e21-104">For example, the following code shows the prefix of an element being changed.</span></span>  
  
```vb  
Dim doc as XmlDocument = new XmlDocument()  
doc.LoadXml("<a:test xmlns:a='123' xmlns:b='456'/>")  
Dim e as XmlElement = doc.DocumentElement  
e.Prefix = "b"  
Console.WriteLine(doc.InnerXml)  
```  
  
```csharp  
XmlDocument doc = new XmlDocument();  
doc.LoadXml("<a:test xmlns:a='123' xmlns:b='456'/>");  
XmlElement e = doc.DocumentElement;
e.Prefix = "b";  
Console.WriteLine(doc.InnerXml);  
```  
  
 <span data-ttu-id="52e21-105">**Sortie**</span><span class="sxs-lookup"><span data-stu-id="52e21-105">**Output**</span></span>  
  
```xml  
<b:test xmlns:a="123" xmlns:b="456" />  
```  
  
 <span data-ttu-id="52e21-106">La modification du préfixe d'un nœud n'entraîne pas la modification de son espace de noms.</span><span class="sxs-lookup"><span data-stu-id="52e21-106">Changing the prefix of a node does not change its namespace.</span></span> <span data-ttu-id="52e21-107">Ce dernier peut être défini uniquement au moment de la création du nœud.</span><span class="sxs-lookup"><span data-stu-id="52e21-107">The namespace can only be set when the node is created.</span></span> <span data-ttu-id="52e21-108">Lorsque vous rendez persistante l’arborescence, de nouveaux attributs d’espace de noms peuvent ne plus être persistants pour satisfaire le préfixe défini.</span><span class="sxs-lookup"><span data-stu-id="52e21-108">When you persist the tree, new namespace attributes may be persisted out to satisfy the prefix you set.</span></span> <span data-ttu-id="52e21-109">Si le nouvel espace de noms ne peut pas être créé, le préfixe est modifié de telle sorte que le nœud préserve son nom local et son espace de noms.</span><span class="sxs-lookup"><span data-stu-id="52e21-109">If the new namespace cannot be created, then the prefix is changed so the node preserves its local name and namespace.</span></span> <span data-ttu-id="52e21-110">L'exemple suivant illustre l'ajout d'un attribut d'espace de noms.</span><span class="sxs-lookup"><span data-stu-id="52e21-110">The following example shows a namespace attribute being added.</span></span>  
  
```vb  
Dim doc as XmlDocument = new XmlDocument()  
doc.LoadXml("<test xmlns='123'/>")  
Dim e as XmlElement = doc.DocumentElement  
e.Prefix = "a"  
Console.WriteLine(doc.InnerXml)  
```  
  
```csharp  
XmlDocument doc = new XmlDocument();  
doc.LoadXml("<test xmlns='123'/>");  
XmlElement e = doc.DocumentElement;
e.Prefix = "a";  
Console.WriteLine(doc.InnerXml);  
```  
  
 <span data-ttu-id="52e21-111">**Sortie**</span><span class="sxs-lookup"><span data-stu-id="52e21-111">**Output**</span></span>  
  
```xml  
<a:test xmlns="123" xmlns:a="123" />  
```  
  
 <span data-ttu-id="52e21-112">Quand l’arborescence a été rendue persistante sous la forme d’une chaîne à la suite de l’appel à **doc.InnerXml**, l’attribut `xmlns:a='123'` a été ajouté pour préserver l’espace de noms de l’élément `test`.</span><span class="sxs-lookup"><span data-stu-id="52e21-112">When the tree was persisted to a string as a result of the call to **doc.InnerXml**, the `xmlns:a='123'` attribute was added to preserve the namespace of the `test` element.</span></span> <span data-ttu-id="52e21-113">Sa valeur était `'123'` et est restée `'123'`.</span><span class="sxs-lookup"><span data-stu-id="52e21-113">It was `'123'`, and it remained `'123'`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="52e21-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="52e21-114">See also</span></span>

- [<span data-ttu-id="52e21-115">DOM (Document Object Model) XML</span><span class="sxs-lookup"><span data-stu-id="52e21-115">XML Document Object Model (DOM)</span></span>](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
