---
title: 'Comment : activer un WebRequest pour utiliser un proxy pour communiquer avec Internet'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 63c0ef2c-44b5-4c54-9804-ba0b9b001ac7
ms.openlocfilehash: 8b38973e4cb2c83ce32b8a08e54d828a8eeef879
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/15/2020
ms.locfileid: "73039538"
---
# <a name="how-to-enable-a-webrequest-to-use-a-proxy-to-communicate-with-the-internet"></a><span data-ttu-id="b7e7a-102">Comment : activer un WebRequest pour utiliser un proxy pour communiquer avec Internet</span><span class="sxs-lookup"><span data-stu-id="b7e7a-102">How to: Enable a WebRequest to Use a Proxy to Communicate With the Internet</span></span>

<span data-ttu-id="b7e7a-103">Cet exemple crée une instance proxy globale qui permet à tout <xref:System.Net.WebRequest> d’utiliser un proxy pour communiquer avec Internet.</span><span class="sxs-lookup"><span data-stu-id="b7e7a-103">This example creates a global proxy instance that will enable any <xref:System.Net.WebRequest> to use a proxy to communicate with the Internet.</span></span> <span data-ttu-id="b7e7a-104">L’exemple suppose que le serveur proxy est nommé `webproxy` et qu’il communique sur le port 80, le port HTTP standard.</span><span class="sxs-lookup"><span data-stu-id="b7e7a-104">The example assumes that the proxy server is named `webproxy` and that it communicates on port 80, the standard HTTP port.</span></span>

## <a name="example"></a><span data-ttu-id="b7e7a-105"> Exemple</span><span class="sxs-lookup"><span data-stu-id="b7e7a-105">Example</span></span>

```csharp
var proxyObject = new WebProxy("http://webproxy:80/");
GlobalProxySelection.Select = proxyObject;
```

```vb
Dim proxyObject As New WebProxy("http://webproxy:80/")
GlobalProxySelection.Select = proxyObject
```

## <a name="compiling-the-code"></a><span data-ttu-id="b7e7a-106">Compilation du code</span><span class="sxs-lookup"><span data-stu-id="b7e7a-106">Compiling the Code</span></span>

<span data-ttu-id="b7e7a-107">Cet exemple nécessite :</span><span class="sxs-lookup"><span data-stu-id="b7e7a-107">This example requires:</span></span>

- <span data-ttu-id="b7e7a-108">Une directive C [ `using` pour](../../csharp/language-reference/keywords/using-directive.md) l’espace de nom **System.Net.**</span><span class="sxs-lookup"><span data-stu-id="b7e7a-108">A C# [`using` directive](../../csharp/language-reference/keywords/using-directive.md) for the **System.Net** namespace.</span></span>
- <span data-ttu-id="b7e7a-109">Une [ `Imports` déclaration](../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md) de base visuelle pour **l’espace** de nom System.Net.</span><span class="sxs-lookup"><span data-stu-id="b7e7a-109">A Visual Basic [`Imports` statement](../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md) for the **System.Net** namespace.</span></span>

## <a name="see-also"></a><span data-ttu-id="b7e7a-110">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b7e7a-110">See also</span></span>

- [<span data-ttu-id="b7e7a-111">Utilisation de protocoles d’application</span><span class="sxs-lookup"><span data-stu-id="b7e7a-111">Using Application Protocols</span></span>](using-application-protocols.md)
- [<span data-ttu-id="b7e7a-112">Accès à Internet par le biais d’un proxy</span><span class="sxs-lookup"><span data-stu-id="b7e7a-112">Accessing the Internet Through a Proxy</span></span>](accessing-the-internet-through-a-proxy.md)
