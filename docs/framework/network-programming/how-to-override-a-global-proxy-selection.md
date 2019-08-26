---
title: 'Procédure : remplacer une sélection de proxy global'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 0da481a9-b414-4230-beb0-e3ceba882fe5
ms.openlocfilehash: e5f4dc22ad75dc4d4f7dc30f44e6ae304403ef16
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69914528"
---
# <a name="how-to-override-a-global-proxy-selection"></a><span data-ttu-id="12ee7-102">Procédure : remplacer une sélection de proxy global</span><span class="sxs-lookup"><span data-stu-id="12ee7-102">How to: Override a Global Proxy Selection</span></span>
<span data-ttu-id="12ee7-103">Cet exemple envoie une **WebRequest** à `www.contoso.com` qui substitue la sélection de proxy global avec un serveur proxy nommé `alternateproxy` sur le port 80.</span><span class="sxs-lookup"><span data-stu-id="12ee7-103">This example sends a **WebRequest** to `www.contoso.com` that overrides the global proxy selection with a proxy server named `alternateproxy` on port 80.</span></span>  
  
## <a name="example"></a><span data-ttu-id="12ee7-104">Exemple</span><span class="sxs-lookup"><span data-stu-id="12ee7-104">Example</span></span>  
  
```csharp  
WebRequest req = WebRequest.Create("http://www.contoso.com/");  
req.Proxy = new WebProxy("http://alternateproxy:80/");  
```  
  
```vb  
Dim req As WebRequest = WebRequest.Create("http://www.contoso.com/")  
req.Proxy = New WebProxy("http://alternateproxy:80/")  
```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="12ee7-105">Compilation du code</span><span class="sxs-lookup"><span data-stu-id="12ee7-105">Compiling the Code</span></span>  
 <span data-ttu-id="12ee7-106">Cet exemple nécessite :</span><span class="sxs-lookup"><span data-stu-id="12ee7-106">This example requires:</span></span>  
  
- <span data-ttu-id="12ee7-107">Une [directive `using`](../../csharp/language-reference/keywords/using-directive.md) pour l’espace de noms **System.Net**.</span><span class="sxs-lookup"><span data-stu-id="12ee7-107">A [`using` directive](../../csharp/language-reference/keywords/using-directive.md) for the **System.Net** namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="12ee7-108">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="12ee7-108">See also</span></span>

- [<span data-ttu-id="12ee7-109">Utilisation de protocoles d’application</span><span class="sxs-lookup"><span data-stu-id="12ee7-109">Using Application Protocols</span></span>](../../../docs/framework/network-programming/using-application-protocols.md)
- [<span data-ttu-id="12ee7-110">Accès à Internet via un proxy</span><span class="sxs-lookup"><span data-stu-id="12ee7-110">Accessing the Internet Through a Proxy</span></span>](../../../docs/framework/network-programming/accessing-the-internet-through-a-proxy.md)
