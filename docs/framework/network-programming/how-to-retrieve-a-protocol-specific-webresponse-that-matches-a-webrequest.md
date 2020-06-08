---
title: 'Comment : récupérer une classe WebResponse spécifique au protocole qui correspond à une classe WebRequest'
description: Découvrez comment récupérer une WebResponse spécifique au protocole qui correspond à une WebRequest dans le .NET Framework.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d8c90785-f16b-42a5-8439-ed2f731b2ba8
ms.openlocfilehash: 15b1912a7bd951df7f3c14eb96251c2bdf237b4f
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84502455"
---
# <a name="how-to-retrieve-a-protocol-specific-webresponse-that-matches-a-webrequest"></a><span data-ttu-id="4638c-103">Comment : récupérer une classe WebResponse spécifique au protocole qui correspond à une classe WebRequest</span><span class="sxs-lookup"><span data-stu-id="4638c-103">How to: Retrieve a Protocol-Specific WebResponse that Matches a WebRequest</span></span>
<span data-ttu-id="4638c-104">Cet exemple montre comment récupérer une classe WebResponse spécifique au protocole qui correspond à une classe WebRequest.</span><span class="sxs-lookup"><span data-stu-id="4638c-104">This example shows how to retrieve a protocol-specific WebResponse that matches a WebRequest.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4638c-105">Exemple</span><span class="sxs-lookup"><span data-stu-id="4638c-105">Example</span></span>  
  
```csharp  
WebRequest req = WebRequest.Create("http://www.contoso.com/");  
WebResponse resp = req.GetResponse();  
```  
  
```vb  
Dim req As WebRequest = WebRequest.Create("http://www.contoso.com")  
Dim resp As WebResponse = req.GetResponse()  
```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="4638c-106">Compilation du code</span><span class="sxs-lookup"><span data-stu-id="4638c-106">Compiling the Code</span></span>  
 <span data-ttu-id="4638c-107">Cet exemple nécessite :</span><span class="sxs-lookup"><span data-stu-id="4638c-107">This example requires:</span></span>  
  
- <span data-ttu-id="4638c-108">Références à l’espace de noms **System.Net**.</span><span class="sxs-lookup"><span data-stu-id="4638c-108">References to the **System.Net** namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4638c-109">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4638c-109">See also</span></span>

- [<span data-ttu-id="4638c-110">Demande de données</span><span class="sxs-lookup"><span data-stu-id="4638c-110">Requesting Data</span></span>](requesting-data.md)
