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
# <a name="how-to-override-a-global-proxy-selection"></a>Procédure : remplacer une sélection de proxy global

Cet exemple envoie une **WebRequest** à `www.contoso.com` qui substitue la sélection de proxy global avec un serveur proxy nommé `alternateproxy` sur le port 80.  
  
## <a name="example"></a> Exemple  
  
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
  
- [ `using` Directive](../../csharp/language-reference/keywords/using-directive.md) pour l’espace de noms **System.net** .  
  
## <a name="see-also"></a>Voir aussi

- [Utilisation de protocoles d’application](using-application-protocols.md)
- [Accès à Internet via un proxy](accessing-the-internet-through-a-proxy.md)
