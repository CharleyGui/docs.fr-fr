---
title: 'Comment : accéder aux propriétés spécifiques à HTTP'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: f8848c7e-f5c5-4d42-b86d-9951ff8f4146
ms.openlocfilehash: 68ad6b2c55cd5cc467e53441caa778ea10b994fb
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/15/2020
ms.locfileid: "79180850"
---
# <a name="how-to-access-http-specific-properties"></a><span data-ttu-id="cd3d7-102">Comment : accéder aux propriétés spécifiques à HTTP</span><span class="sxs-lookup"><span data-stu-id="cd3d7-102">How to: Access HTTP-Specific Properties</span></span>
<span data-ttu-id="cd3d7-103">Cet exemple montre comment désactiver le comportement HTTP **Keep-alive** et obtenir le numéro de version du protocole du serveur web.</span><span class="sxs-lookup"><span data-stu-id="cd3d7-103">This sample shows how to turn off the HTTP **Keep-alive** behavior and get the protocol version number from the Web server.</span></span>  
  
## <a name="example"></a><span data-ttu-id="cd3d7-104"> Exemple</span><span class="sxs-lookup"><span data-stu-id="cd3d7-104">Example</span></span>  
  
```vb  
Dim HttpWReq As HttpWebRequest= _  
    CType(WebRequest.Create("http://www.contoso.com"), HttpWebRequest)  
' Turn off connection keep-alives.  
HttpWReq.KeepAlive = False  
  
Dim HttpWResp As HttpWebResponse = _  
    CType(HttpWReq.GetResponse(), HttpWebResponse)  
  
' Get the HTTP protocol version number returned by the server.  
Dim ver As String = HttpWResp.ProtocolVersion.ToString()  
HttpWResp.Close()  
```  
  
```csharp  
HttpWebRequest HttpWReq =
    (HttpWebRequest)WebRequest.Create("http://www.contoso.com");  
// Turn off connection keep-alives.  
HttpWReq.KeepAlive = false;  
  
HttpWebResponse HttpWResp = (HttpWebResponse)HttpWReq.GetResponse();  
  
// Get the HTTP protocol version number returned by the server.  
String ver = HttpWResp.ProtocolVersion.ToString();  
HttpWResp.Close();  
```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="cd3d7-105">Compilation du code</span><span class="sxs-lookup"><span data-stu-id="cd3d7-105">Compiling the Code</span></span>  
 <span data-ttu-id="cd3d7-106">Cet exemple nécessite :</span><span class="sxs-lookup"><span data-stu-id="cd3d7-106">This example requires:</span></span>  
  
- <span data-ttu-id="cd3d7-107">Références à l’espace de noms **System.Net**.</span><span class="sxs-lookup"><span data-stu-id="cd3d7-107">References to the **System.Net** namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cd3d7-108">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="cd3d7-108">See also</span></span>

- [<span data-ttu-id="cd3d7-109">Accès à Internet par le biais d’un proxy</span><span class="sxs-lookup"><span data-stu-id="cd3d7-109">Accessing the Internet Through a Proxy</span></span>](accessing-the-internet-through-a-proxy.md)
- [<span data-ttu-id="cd3d7-110">Utilisation de protocoles d’application</span><span class="sxs-lookup"><span data-stu-id="cd3d7-110">Using Application Protocols</span></span>](using-application-protocols.md)
- [<span data-ttu-id="cd3d7-111">HTTP</span><span class="sxs-lookup"><span data-stu-id="cd3d7-111">HTTP</span></span>](http.md)
