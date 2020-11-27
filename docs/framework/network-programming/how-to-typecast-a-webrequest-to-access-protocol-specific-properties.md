---
title: 'Procédure : caster une classe WebRequest en vue d’accéder aux propriétés spécifiques au protocole'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d9a8eae2-7454-46f9-b43b-c98477c5bcde
ms.openlocfilehash: 09bd551dad77358b1503871c6ee100a869adf75b
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96253425"
---
# <a name="how-to-typecast-a-webrequest-to-access-protocol-specific-properties"></a><span data-ttu-id="00d4e-102">Procédure : caster une classe WebRequest en vue d’accéder aux propriétés spécifiques au protocole</span><span class="sxs-lookup"><span data-stu-id="00d4e-102">How to: Typecast a WebRequest to Access Protocol Specific Properties</span></span>

<span data-ttu-id="00d4e-103">Cet exemple montre comment effectuer un cast du type d’une classe WebRequest pour accéder à des propriétés spécifiques au protocole.</span><span class="sxs-lookup"><span data-stu-id="00d4e-103">This example shows how to typecast a WebRequest so that you can access protocol specific properties.</span></span>  
  
## <a name="example"></a><span data-ttu-id="00d4e-104">Exemple</span><span class="sxs-lookup"><span data-stu-id="00d4e-104">Example</span></span>  
  
```csharp  
HttpWebRequest httpreq =
   (HttpWebRequest) WebRequest.Create("http://www.contoso.com/");  
```  
  
```vb  
Dim httpreq As HttpWebRequest = _  
   CType(WebRequest.Create("http://www.contoso.com/"), HttpWebRequest)  
```  
  
## <a name="see-also"></a><span data-ttu-id="00d4e-105">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="00d4e-105">See also</span></span>

- [<span data-ttu-id="00d4e-106">programmation de protocoles enfichables</span><span class="sxs-lookup"><span data-stu-id="00d4e-106">Programming Pluggable Protocols</span></span>](programming-pluggable-protocols.md)
