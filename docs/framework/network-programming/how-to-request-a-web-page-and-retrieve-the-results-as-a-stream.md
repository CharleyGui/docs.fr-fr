---
title: 'Comment : demander une page web et récupérer les résultats sous forme de flux'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d32b7f35-29d8-4fb7-ad71-d219edc5e359
ms.openlocfilehash: 65bda268cd77959dbcd786c365d0a30c324b89ce
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/15/2020
ms.locfileid: "71393107"
---
# <a name="how-to-request-a-web-page-and-retrieve-the-results-as-a-stream"></a>Comment : demander une page web et récupérer les résultats sous forme de flux

Cet exemple montre comment demander une page web et récupérer les résultats sous forme de flux.
  
## <a name="example"></a> Exemple

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

## <a name="compiling-the-code"></a>Compilation du code

 Cet exemple nécessite :

- Références aux espaces de noms <xref:System.IO> et <xref:System.Net>.

## <a name="see-also"></a>Voir aussi

- [Demande de données](requesting-data.md)
