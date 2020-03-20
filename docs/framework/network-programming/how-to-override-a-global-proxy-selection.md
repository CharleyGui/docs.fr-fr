---
title: 'Comment : remplacer une sélection de proxy global'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 0da481a9-b414-4230-beb0-e3ceba882fe5
ms.openlocfilehash: 44845fb67aac4ff9ab9dda8cf4934153c8c4f23c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/15/2020
ms.locfileid: "71048270"
---
# <a name="how-to-override-a-global-proxy-selection"></a><span data-ttu-id="66a92-102">Comment : remplacer une sélection de proxy global</span><span class="sxs-lookup"><span data-stu-id="66a92-102">How to: Override a Global Proxy Selection</span></span>
<span data-ttu-id="66a92-103">Cet exemple envoie une **WebRequest** à `www.contoso.com` qui substitue la sélection de proxy global avec un serveur proxy nommé `alternateproxy` sur le port 80.</span><span class="sxs-lookup"><span data-stu-id="66a92-103">This example sends a **WebRequest** to `www.contoso.com` that overrides the global proxy selection with a proxy server named `alternateproxy` on port 80.</span></span>  
  
## <a name="example"></a><span data-ttu-id="66a92-104"> Exemple</span><span class="sxs-lookup"><span data-stu-id="66a92-104">Example</span></span>  
  
```csharp  
WebRequest req = WebRequest.Create("http://www.contoso.com/");  
req.Proxy = new WebProxy("http://alternateproxy:80/");  
```  
  
```vb  
Dim req As WebRequest = WebRequest.Create("http://www.contoso.com/")  
req.Proxy = New WebProxy("http://alternateproxy:80/")  
```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="66a92-105">Compilation du code</span><span class="sxs-lookup"><span data-stu-id="66a92-105">Compiling the Code</span></span>  
 <span data-ttu-id="66a92-106">Cet exemple nécessite :</span><span class="sxs-lookup"><span data-stu-id="66a92-106">This example requires:</span></span>  
  
- <span data-ttu-id="66a92-107">Une [ `using` directive](../../csharp/language-reference/keywords/using-directive.md) pour l’espace **de** System.Net nom.</span><span class="sxs-lookup"><span data-stu-id="66a92-107">A [`using` directive](../../csharp/language-reference/keywords/using-directive.md) for the **System.Net** namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="66a92-108">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="66a92-108">See also</span></span>

- [<span data-ttu-id="66a92-109">Utilisation de protocoles d’application</span><span class="sxs-lookup"><span data-stu-id="66a92-109">Using Application Protocols</span></span>](using-application-protocols.md)
- [<span data-ttu-id="66a92-110">Accès à Internet par le biais d’un proxy</span><span class="sxs-lookup"><span data-stu-id="66a92-110">Accessing the Internet Through a Proxy</span></span>](accessing-the-internet-through-a-proxy.md)
