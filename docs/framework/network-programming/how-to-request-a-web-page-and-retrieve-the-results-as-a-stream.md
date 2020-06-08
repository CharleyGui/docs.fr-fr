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
# <a name="how-to-request-a-web-page-and-retrieve-the-results-as-a-stream"></a>Comment : demander une page web et récupérer les résultats sous forme de flux

Cet exemple montre comment demander une page web et récupérer les résultats sous forme de flux.
  
## <a name="example"></a>Exemple

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
