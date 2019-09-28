---
title: 'Procédure : demander une page web et récupérer les résultats sous forme de flux'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d32b7f35-29d8-4fb7-ad71-d219edc5e359
ms.openlocfilehash: 65bda268cd77959dbcd786c365d0a30c324b89ce
ms.sourcegitcommit: da2dd2772fcf32b44eb18b1cbe8affd17b1753c9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/27/2019
ms.locfileid: "71393107"
---
# <a name="how-to-request-a-web-page-and-retrieve-the-results-as-a-stream"></a><span data-ttu-id="b74b9-102">Procédure : demander une page web et récupérer les résultats sous forme de flux</span><span class="sxs-lookup"><span data-stu-id="b74b9-102">How to: Request a Web Page and Retrieve the Results as a Stream</span></span>

<span data-ttu-id="b74b9-103">Cet exemple montre comment demander une page web et récupérer les résultats sous forme de flux.</span><span class="sxs-lookup"><span data-stu-id="b74b9-103">This example shows how to request a Web page and retrieve the results in a stream.</span></span>
  
## <a name="example"></a><span data-ttu-id="b74b9-104">Exemple</span><span class="sxs-lookup"><span data-stu-id="b74b9-104">Example</span></span>

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

## <a name="compiling-the-code"></a><span data-ttu-id="b74b9-105">Compilation du code</span><span class="sxs-lookup"><span data-stu-id="b74b9-105">Compiling the Code</span></span>

 <span data-ttu-id="b74b9-106">Cet exemple nécessite :</span><span class="sxs-lookup"><span data-stu-id="b74b9-106">This example requires:</span></span>

- <span data-ttu-id="b74b9-107">Références aux espaces de noms <xref:System.IO> et <xref:System.Net>.</span><span class="sxs-lookup"><span data-stu-id="b74b9-107">References to the <xref:System.IO> and <xref:System.Net> namespaces.</span></span>

## <a name="see-also"></a><span data-ttu-id="b74b9-108">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b74b9-108">See also</span></span>

- [<span data-ttu-id="b74b9-109">Demande de données</span><span class="sxs-lookup"><span data-stu-id="b74b9-109">Requesting Data</span></span>](requesting-data.md)
