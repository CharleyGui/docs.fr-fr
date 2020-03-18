---
title: Comment construire LINQ à XML exemples (C)
ms.date: 07/20/2015
ms.assetid: e5d18fa1-2704-48fe-a44b-1564f97c9e9c
ms.openlocfilehash: 289a13daed7e3c871156bf50c6fa04c113c0cd13
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "74141454"
---
# <a name="how-to-build-linq-to-xml-examples-c"></a><span data-ttu-id="32653-102">Comment construire LINQ à XML exemples (C)</span><span class="sxs-lookup"><span data-stu-id="32653-102">How to build LINQ to XML examples (C#)</span></span>
<span data-ttu-id="32653-103">Les différents extraits et exemples présentés dans cette documentation utilisent des classes et des types de différents espaces de noms.</span><span class="sxs-lookup"><span data-stu-id="32653-103">The various snippets and examples in this documentation use classes and types from a variety of namespaces.</span></span> <span data-ttu-id="32653-104">Lors de la compilation de code Visual C#, vous devez fournir des directives `using` appropriées.</span><span class="sxs-lookup"><span data-stu-id="32653-104">When compiling C# code, you need to supply appropriate `using` directives.</span></span>  
  
## <a name="example"></a><span data-ttu-id="32653-105"> Exemple</span><span class="sxs-lookup"><span data-stu-id="32653-105">Example</span></span>  
 <span data-ttu-id="32653-106">Le code suivant contient les directives `using` requises pour la génération et l'exécution des exemples C#.</span><span class="sxs-lookup"><span data-stu-id="32653-106">The following code contains the `using` directives that the C# examples require to build and run.</span></span> <span data-ttu-id="32653-107">Toutes les directives `using` ne sont pas requises pour tous les exemples.</span><span class="sxs-lookup"><span data-stu-id="32653-107">Not all `using` directives are required for every example.</span></span>  
  
```csharp  
using System;  
using System.Diagnostics;  
using System.Collections;  
using System.Collections.Generic;  
using System.Collections.Specialized;  
using System.Text;  
using System.Linq;  
using System.Xml;  
using System.Xml.Linq;  
using System.Xml.Schema;  
using System.Xml.XPath;  
using System.Xml.Xsl;  
using System.IO;  
using System.Threading;  
using System.Reflection;  
using System.IO.Packaging;  
```  
  
## <a name="see-also"></a><span data-ttu-id="32653-108">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="32653-108">See also</span></span>

- [<span data-ttu-id="32653-109">Vue d’ensemble de la programmation LINQ to XML (C#)</span><span class="sxs-lookup"><span data-stu-id="32653-109">LINQ to XML Programming Overview (C#)</span></span>](./linq-to-xml-overview.md)
