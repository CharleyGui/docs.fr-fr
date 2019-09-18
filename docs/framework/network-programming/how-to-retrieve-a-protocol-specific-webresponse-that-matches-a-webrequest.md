---
title: 'Procédure : récupérer une classe WebResponse spécifique au protocole qui correspond à une classe WebRequest'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d8c90785-f16b-42a5-8439-ed2f731b2ba8
ms.openlocfilehash: 0cb2d11306f52df767d8c053e8ab745696bb8e47
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71048137"
---
# <a name="how-to-retrieve-a-protocol-specific-webresponse-that-matches-a-webrequest"></a><span data-ttu-id="f8558-102">Procédure : récupérer une classe WebResponse spécifique au protocole qui correspond à une classe WebRequest</span><span class="sxs-lookup"><span data-stu-id="f8558-102">How to: Retrieve a Protocol-Specific WebResponse that Matches a WebRequest</span></span>
<span data-ttu-id="f8558-103">Cet exemple montre comment récupérer une classe WebResponse spécifique au protocole qui correspond à une classe WebRequest.</span><span class="sxs-lookup"><span data-stu-id="f8558-103">This example shows how to retrieve a protocol-specific WebResponse that matches a WebRequest.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f8558-104">Exemple</span><span class="sxs-lookup"><span data-stu-id="f8558-104">Example</span></span>  
  
```csharp  
WebRequest req = WebRequest.Create("http://www.contoso.com/");  
WebResponse resp = req.GetResponse();  
```  
  
```vb  
Dim req As WebRequest = WebRequest.Create("http://www.contoso.com")  
Dim resp As WebResponse = req.GetResponse()  
```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="f8558-105">Compilation du code</span><span class="sxs-lookup"><span data-stu-id="f8558-105">Compiling the Code</span></span>  
 <span data-ttu-id="f8558-106">Cet exemple nécessite :</span><span class="sxs-lookup"><span data-stu-id="f8558-106">This example requires:</span></span>  
  
- <span data-ttu-id="f8558-107">Références à l’espace de noms **System.Net**.</span><span class="sxs-lookup"><span data-stu-id="f8558-107">References to the **System.Net** namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f8558-108">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f8558-108">See also</span></span>

- [<span data-ttu-id="f8558-109">Demande de données</span><span class="sxs-lookup"><span data-stu-id="f8558-109">Requesting Data</span></span>](requesting-data.md)
