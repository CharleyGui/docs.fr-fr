---
title: 'Procédure : remplacer une sélection de proxy global'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 0da481a9-b414-4230-beb0-e3ceba882fe5
ms.openlocfilehash: 44845fb67aac4ff9ab9dda8cf4934153c8c4f23c
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71048270"
---
# <a name="how-to-override-a-global-proxy-selection"></a>Procédure : remplacer une sélection de proxy global
Cet exemple envoie une **WebRequest** à `www.contoso.com` qui substitue la sélection de proxy global avec un serveur proxy nommé `alternateproxy` sur le port 80.  
  
## <a name="example"></a>Exemple  
  
```csharp  
WebRequest req = WebRequest.Create("http://www.contoso.com/");  
req.Proxy = new WebProxy("http://alternateproxy:80/");  
```  
  
```vb  
Dim req As WebRequest = WebRequest.Create("http://www.contoso.com/")  
req.Proxy = New WebProxy("http://alternateproxy:80/")  
```  
  
## <a name="compiling-the-code"></a>Compilation du code  
 Cet exemple nécessite :  
  
- Une [directive `using`](../../csharp/language-reference/keywords/using-directive.md) pour l’espace de noms **System.Net**.  
  
## <a name="see-also"></a>Voir aussi

- [Utilisation de protocoles d’application](using-application-protocols.md)
- [Accès à Internet via un proxy](accessing-the-internet-through-a-proxy.md)
