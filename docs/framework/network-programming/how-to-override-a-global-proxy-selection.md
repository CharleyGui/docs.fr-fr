---
title: 'Procédure : remplacer une sélection de proxy global'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 0da481a9-b414-4230-beb0-e3ceba882fe5
ms.openlocfilehash: 44845fb67aac4ff9ab9dda8cf4934153c8c4f23c
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71048270"
---
# <a name="how-to-override-a-global-proxy-selection"></a><span data-ttu-id="bb2d5-102">Procédure : remplacer une sélection de proxy global</span><span class="sxs-lookup"><span data-stu-id="bb2d5-102">How to: Override a Global Proxy Selection</span></span>
<span data-ttu-id="bb2d5-103">Cet exemple envoie une **WebRequest** à `www.contoso.com` qui substitue la sélection de proxy global avec un serveur proxy nommé `alternateproxy` sur le port 80.</span><span class="sxs-lookup"><span data-stu-id="bb2d5-103">This example sends a **WebRequest** to `www.contoso.com` that overrides the global proxy selection with a proxy server named `alternateproxy` on port 80.</span></span>  
  
## <a name="example"></a><span data-ttu-id="bb2d5-104">Exemple</span><span class="sxs-lookup"><span data-stu-id="bb2d5-104">Example</span></span>  
  
```csharp  
WebRequest req = WebRequest.Create("http://www.contoso.com/");  
req.Proxy = new WebProxy("http://alternateproxy:80/");  
```  
  
```vb  
Dim req As WebRequest = WebRequest.Create("http://www.contoso.com/")  
req.Proxy = New WebProxy("http://alternateproxy:80/")  
```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="bb2d5-105">Compilation du code</span><span class="sxs-lookup"><span data-stu-id="bb2d5-105">Compiling the Code</span></span>  
 <span data-ttu-id="bb2d5-106">Cet exemple nécessite :</span><span class="sxs-lookup"><span data-stu-id="bb2d5-106">This example requires:</span></span>  
  
- <span data-ttu-id="bb2d5-107">Une [directive `using`](../../csharp/language-reference/keywords/using-directive.md) pour l’espace de noms **System.Net**.</span><span class="sxs-lookup"><span data-stu-id="bb2d5-107">A [`using` directive](../../csharp/language-reference/keywords/using-directive.md) for the **System.Net** namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bb2d5-108">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="bb2d5-108">See also</span></span>

- [<span data-ttu-id="bb2d5-109">Utilisation de protocoles d’application</span><span class="sxs-lookup"><span data-stu-id="bb2d5-109">Using Application Protocols</span></span>](using-application-protocols.md)
- [<span data-ttu-id="bb2d5-110">Accès à Internet via un proxy</span><span class="sxs-lookup"><span data-stu-id="bb2d5-110">Accessing the Internet Through a Proxy</span></span>](accessing-the-internet-through-a-proxy.md)
