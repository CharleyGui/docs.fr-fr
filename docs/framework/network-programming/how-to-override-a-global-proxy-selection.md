---
title: 'Procédure : remplacer une sélection de proxy global'
description: Suivez cet exemple pour remplacer la sélection de proxy global en envoyant une WebRequest à une URL, qui remplace la sélection par un serveur proxy.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 0da481a9-b414-4230-beb0-e3ceba882fe5
ms.openlocfilehash: 8931cdc471b957447277c333ba482a0cec0e6aa5
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96265737"
---
# <a name="how-to-override-a-global-proxy-selection"></a><span data-ttu-id="a439d-103">Procédure : remplacer une sélection de proxy global</span><span class="sxs-lookup"><span data-stu-id="a439d-103">How to: Override a Global Proxy Selection</span></span>

<span data-ttu-id="a439d-104">Cet exemple envoie une **WebRequest** à `www.contoso.com` qui substitue la sélection de proxy global avec un serveur proxy nommé `alternateproxy` sur le port 80.</span><span class="sxs-lookup"><span data-stu-id="a439d-104">This example sends a **WebRequest** to `www.contoso.com` that overrides the global proxy selection with a proxy server named `alternateproxy` on port 80.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a439d-105"> Exemple</span><span class="sxs-lookup"><span data-stu-id="a439d-105">Example</span></span>  
  
```csharp  
WebRequest req = WebRequest.Create("http://www.contoso.com/");  
req.Proxy = new WebProxy("http://alternateproxy:80/");  
```  
  
```vb  
Dim req As WebRequest = WebRequest.Create("http://www.contoso.com/")  
req.Proxy = New WebProxy("http://alternateproxy:80/")  
```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="a439d-106">Compilation du code</span><span class="sxs-lookup"><span data-stu-id="a439d-106">Compiling the Code</span></span>  

 <span data-ttu-id="a439d-107">Cet exemple nécessite :</span><span class="sxs-lookup"><span data-stu-id="a439d-107">This example requires:</span></span>  
  
- <span data-ttu-id="a439d-108">[ `using` Directive](../../csharp/language-reference/keywords/using-directive.md) pour l’espace de noms **System.net** .</span><span class="sxs-lookup"><span data-stu-id="a439d-108">A [`using` directive](../../csharp/language-reference/keywords/using-directive.md) for the **System.Net** namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a439d-109">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a439d-109">See also</span></span>

- [<span data-ttu-id="a439d-110">Utilisation de protocoles d’application</span><span class="sxs-lookup"><span data-stu-id="a439d-110">Using Application Protocols</span></span>](using-application-protocols.md)
- [<span data-ttu-id="a439d-111">Accès à Internet via un proxy</span><span class="sxs-lookup"><span data-stu-id="a439d-111">Accessing the Internet Through a Proxy</span></span>](accessing-the-internet-through-a-proxy.md)
