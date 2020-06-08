---
title: 'Comment : demander une page web et récupérer les résultats sous forme de flux'
description: Cet exemple montre comment demander une page Web et récupérer les résultats dans un flux de la .NET Framework.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d32b7f35-29d8-4fb7-ad71-d219edc5e359
ms.openlocfilehash: bd57f9af6be29c783d044e785ebb36aaa8592df2
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84502481"
---
# <a name="how-to-request-a-web-page-and-retrieve-the-results-as-a-stream"></a><span data-ttu-id="4f71a-103">Comment : demander une page web et récupérer les résultats sous forme de flux</span><span class="sxs-lookup"><span data-stu-id="4f71a-103">How to: Request a Web Page and Retrieve the Results as a Stream</span></span>

<span data-ttu-id="4f71a-104">Cet exemple montre comment demander une page web et récupérer les résultats sous forme de flux.</span><span class="sxs-lookup"><span data-stu-id="4f71a-104">This example shows how to request a Web page and retrieve the results in a stream.</span></span>
  
## <a name="example"></a><span data-ttu-id="4f71a-105">Exemple</span><span class="sxs-lookup"><span data-stu-id="4f71a-105">Example</span></span>

```csharp
var myClient = new WebClient();
Stream response = myClient.OpenRead("https://docs.microsoft.com/dotnet/");
// The stream data is used here.
response.Close();
```

```vb
Dim myClient As New WebClient()
Dim response As Stream = myClient.OpenRead("https://docs.microsoft.com/dotnet/")
' The stream data is used here.
response.Close()
```

## <a name="compiling-the-code"></a><span data-ttu-id="4f71a-106">Compilation du code</span><span class="sxs-lookup"><span data-stu-id="4f71a-106">Compiling the Code</span></span>

 <span data-ttu-id="4f71a-107">Cet exemple nécessite :</span><span class="sxs-lookup"><span data-stu-id="4f71a-107">This example requires:</span></span>

- <span data-ttu-id="4f71a-108">Références aux espaces de noms <xref:System.IO> et <xref:System.Net>.</span><span class="sxs-lookup"><span data-stu-id="4f71a-108">References to the <xref:System.IO> and <xref:System.Net> namespaces.</span></span>

## <a name="see-also"></a><span data-ttu-id="4f71a-109">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4f71a-109">See also</span></span>

- [<span data-ttu-id="4f71a-110">Demande de données</span><span class="sxs-lookup"><span data-stu-id="4f71a-110">Requesting Data</span></span>](requesting-data.md)
