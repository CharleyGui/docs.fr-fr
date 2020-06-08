---
title: 'Comment : activer un WebRequest pour utiliser un proxy pour communiquer avec Internet'
description: Découvrez comment créer une instance de proxy globale pour permettre à n’importe quelle WebRequest d’utiliser un proxy pour communiquer avec Internet dans le .NET Framework.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 63c0ef2c-44b5-4c54-9804-ba0b9b001ac7
ms.openlocfilehash: 0fc33cea3f5a7fe4669b110e53e71afdb9561c23
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84502533"
---
# <a name="how-to-enable-a-webrequest-to-use-a-proxy-to-communicate-with-the-internet"></a><span data-ttu-id="4842c-103">Comment : activer un WebRequest pour utiliser un proxy pour communiquer avec Internet</span><span class="sxs-lookup"><span data-stu-id="4842c-103">How to: Enable a WebRequest to Use a Proxy to Communicate With the Internet</span></span>

<span data-ttu-id="4842c-104">Cet exemple crée une instance proxy globale qui permet à tout <xref:System.Net.WebRequest> d’utiliser un proxy pour communiquer avec Internet.</span><span class="sxs-lookup"><span data-stu-id="4842c-104">This example creates a global proxy instance that will enable any <xref:System.Net.WebRequest> to use a proxy to communicate with the Internet.</span></span> <span data-ttu-id="4842c-105">L’exemple suppose que le serveur proxy est nommé `webproxy` et qu’il communique sur le port 80, le port HTTP standard.</span><span class="sxs-lookup"><span data-stu-id="4842c-105">The example assumes that the proxy server is named `webproxy` and that it communicates on port 80, the standard HTTP port.</span></span>

## <a name="example"></a><span data-ttu-id="4842c-106">Exemple</span><span class="sxs-lookup"><span data-stu-id="4842c-106">Example</span></span>

```csharp
var proxyObject = new WebProxy("http://webproxy:80/");
GlobalProxySelection.Select = proxyObject;
```

```vb
Dim proxyObject As New WebProxy("http://webproxy:80/")
GlobalProxySelection.Select = proxyObject
```

## <a name="compiling-the-code"></a><span data-ttu-id="4842c-107">Compilation du code</span><span class="sxs-lookup"><span data-stu-id="4842c-107">Compiling the Code</span></span>

<span data-ttu-id="4842c-108">Cet exemple nécessite :</span><span class="sxs-lookup"><span data-stu-id="4842c-108">This example requires:</span></span>

- <span data-ttu-id="4842c-109">[ `using` Directive](../../csharp/language-reference/keywords/using-directive.md) C# pour l’espace de noms **System.net** .</span><span class="sxs-lookup"><span data-stu-id="4842c-109">A C# [`using` directive](../../csharp/language-reference/keywords/using-directive.md) for the **System.Net** namespace.</span></span>
- <span data-ttu-id="4842c-110">[ `Imports` Instruction](../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md) Visual Basic pour l’espace de noms **System.net** .</span><span class="sxs-lookup"><span data-stu-id="4842c-110">A Visual Basic [`Imports` statement](../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md) for the **System.Net** namespace.</span></span>

## <a name="see-also"></a><span data-ttu-id="4842c-111">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4842c-111">See also</span></span>

- [<span data-ttu-id="4842c-112">Utilisation de protocoles d’application</span><span class="sxs-lookup"><span data-stu-id="4842c-112">Using Application Protocols</span></span>](using-application-protocols.md)
- [<span data-ttu-id="4842c-113">Accès à Internet via un proxy</span><span class="sxs-lookup"><span data-stu-id="4842c-113">Accessing the Internet Through a Proxy</span></span>](accessing-the-internet-through-a-proxy.md)
