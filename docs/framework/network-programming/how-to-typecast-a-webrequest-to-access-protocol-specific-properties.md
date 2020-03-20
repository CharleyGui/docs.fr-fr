---
title: 'Comment : convertir une classe WebRequest pour accéder à des propriétés spécifiques au protocole'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d9a8eae2-7454-46f9-b43b-c98477c5bcde
ms.openlocfilehash: d38a40aa1e6e3db769aedfc440077721cdfaf06d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/15/2020
ms.locfileid: "79180757"
---
# <a name="how-to-typecast-a-webrequest-to-access-protocol-specific-properties"></a>Comment : convertir une classe WebRequest pour accéder à des propriétés spécifiques au protocole
Cet exemple montre comment effectuer un cast du type d’une classe WebRequest pour accéder à des propriétés spécifiques au protocole.  
  
## <a name="example"></a> Exemple  
  
```csharp  
HttpWebRequest httpreq =
   (HttpWebRequest) WebRequest.Create("http://www.contoso.com/");  
```  
  
```vb  
Dim httpreq As HttpWebRequest = _  
   CType(WebRequest.Create("http://www.contoso.com/"), HttpWebRequest)  
```  
  
## <a name="see-also"></a>Voir aussi

- [programmation de protocoles enfichables](programming-pluggable-protocols.md)
