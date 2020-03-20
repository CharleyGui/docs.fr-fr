---
title: 'Comment : inscrire un protocole personnalisé à l’aide de WebRequest'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 98ddbdb9-66b1-4080-92ad-51f5c447fcf8
ms.openlocfilehash: 05b6f6c3f0f1fc1b36b60e8b0dae50de2826aba4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/15/2020
ms.locfileid: "71048251"
---
# <a name="how-to-register-a-custom-protocol-using-webrequest"></a><span data-ttu-id="59a7a-102">Comment : inscrire un protocole personnalisé à l’aide de WebRequest</span><span class="sxs-lookup"><span data-stu-id="59a7a-102">How to: Register a Custom Protocol Using WebRequest</span></span>
<span data-ttu-id="59a7a-103">Cet exemple montre comment inscrire une classe spécifique à un protocole qui est définie ailleurs dans du code.</span><span class="sxs-lookup"><span data-stu-id="59a7a-103">This example shows how to register a protocol specific class that is defined elsewhere.</span></span> <span data-ttu-id="59a7a-104">Dans cet exemple, `CustomWebRequestCreator` est l’objet implémenté par l’utilisateur qui implémente la méthode **Create** utilisée pour retourner l’objet `CustomWebRequest`.</span><span class="sxs-lookup"><span data-stu-id="59a7a-104">In this example, `CustomWebRequestCreator` is the user-implemented object that implements the **Create** method that returns the `CustomWebRequest` object.</span></span> <span data-ttu-id="59a7a-105">L’exemple de code suppose que vous avez écrit le code `CustomWebRequest` qui implémente le protocole personnalisé.</span><span class="sxs-lookup"><span data-stu-id="59a7a-105">The code example assumes that you have written the `CustomWebRequest` code that implements the custom protocol.</span></span>  
  
## <a name="example"></a><span data-ttu-id="59a7a-106"> Exemple</span><span class="sxs-lookup"><span data-stu-id="59a7a-106">Example</span></span>  
  
```csharp  
WebRequest.RegisterPrefix("custom", new CustomWebRequestCreator());  
WebRequest req = WebRequest.Create("custom://customHost.contoso.com/");  
```  
  
```vb  
WebRequest.RegisterPrefix("custom", New CustomWebRequestCreator())  
Dim req As WebRequest = WebRequest.Create("custom://customHost.contoso.com/")  
```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="59a7a-107">Compilation du code</span><span class="sxs-lookup"><span data-stu-id="59a7a-107">Compiling the Code</span></span>  
 <span data-ttu-id="59a7a-108">Cet exemple nécessite :</span><span class="sxs-lookup"><span data-stu-id="59a7a-108">This example requires:</span></span>  
  
 <span data-ttu-id="59a7a-109">Références à l’espace de noms <xref:System.Net>.</span><span class="sxs-lookup"><span data-stu-id="59a7a-109">References to the <xref:System.Net> namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="59a7a-110">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="59a7a-110">See also</span></span>

- [<span data-ttu-id="59a7a-111">programmation de protocoles enfichables</span><span class="sxs-lookup"><span data-stu-id="59a7a-111">Programming Pluggable Protocols</span></span>](programming-pluggable-protocols.md)
