---
title: Exception. PrepForRemoting, méthode (System)
author: mairaw
ms.author: mairaw
ms.date: 10/08/2019
topic_type:
- apiref
api_name:
- System.Exception.PrepForRemoting
api_location:
- mscorlib.dll
api_type:
- Assembly
ms.openlocfilehash: 057390d64f70d3cb8eba7d4b29b94570fdca77e3
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72405031"
---
# <a name="exceptionprepforremoting-method"></a><span data-ttu-id="4b0d5-102">Exception. PrepForRemoting, méthode</span><span class="sxs-lookup"><span data-stu-id="4b0d5-102">Exception.PrepForRemoting Method</span></span>

<span data-ttu-id="4b0d5-103">Conserve la trace de la pile côté serveur en l’ajoutant au message avant que l’exception ne soit levée à nouveau sur le site d’appel client.</span><span class="sxs-lookup"><span data-stu-id="4b0d5-103">Preserves the server-side stack trace by appending it to the message before the exception is rethrown at the client call site.</span></span>

```csharp
internal Exception PrepForRemoting();
```

## <a name="returns"></a><span data-ttu-id="4b0d5-104">Returns (Retours)</span><span class="sxs-lookup"><span data-stu-id="4b0d5-104">Returns</span></span>

<xref:System.Exception>  
<span data-ttu-id="4b0d5-105">Cette instance de l'objet <xref:System.Exception>.</span><span class="sxs-lookup"><span data-stu-id="4b0d5-105">This <xref:System.Exception> instance.</span></span>

## <a name="remarks"></a><span data-ttu-id="4b0d5-106">Notes</span><span class="sxs-lookup"><span data-stu-id="4b0d5-106">Remarks</span></span>

> [!WARNING]
> <span data-ttu-id="4b0d5-107">La méthode `Exception.PrepForRemoting` est interne et n’est pas destinée à être utilisée directement dans votre code.</span><span class="sxs-lookup"><span data-stu-id="4b0d5-107">The `Exception.PrepForRemoting` method is internal and is not meant to be used directly in your code.</span></span>
>
> <span data-ttu-id="4b0d5-108">Microsoft ne prend pas en charge l’utilisation de cette méthode dans une application de production en l’absence de toute circonstance.</span><span class="sxs-lookup"><span data-stu-id="4b0d5-108">Microsoft does not support the use of this method in a production application under any circumstance.</span></span>

## <a name="requirements"></a><span data-ttu-id="4b0d5-109">spécifications</span><span class="sxs-lookup"><span data-stu-id="4b0d5-109">Requirements</span></span>

<span data-ttu-id="4b0d5-110">**Espace de noms :** <xref:System></span><span class="sxs-lookup"><span data-stu-id="4b0d5-110">**Namespace:** <xref:System></span></span>

<span data-ttu-id="4b0d5-111">**Assembly :** mscorlib. dll (dans mscorlib. dll)</span><span class="sxs-lookup"><span data-stu-id="4b0d5-111">**Assembly:** mscorlib.dll (in mscorlib.dll)</span></span>

<span data-ttu-id="4b0d5-112">**Versions de .NET Framework :** Disponible depuis 1,0.</span><span class="sxs-lookup"><span data-stu-id="4b0d5-112">**.NET Framework versions:** Available since 1.0.</span></span>
