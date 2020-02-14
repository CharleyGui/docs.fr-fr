---
title: Exception. PrepForRemoting, méthode (System)
ms.date: 10/08/2019
topic_type:
- apiref
api_name:
- System.Exception.PrepForRemoting
api_location:
- mscorlib.dll
api_type:
- Assembly
ms.openlocfilehash: ce1c24578690a1643b7f5af0e44eaae95ed7b0a2
ms.sourcegitcommit: 9c54866bcbdc49dbb981dd55be9bbd0443837aa2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/14/2020
ms.locfileid: "77214899"
---
# <a name="exceptionprepforremoting-method"></a><span data-ttu-id="6fe4d-102">Exception.PrepForRemoting, méthode</span><span class="sxs-lookup"><span data-stu-id="6fe4d-102">Exception.PrepForRemoting Method</span></span>

<span data-ttu-id="6fe4d-103">Conserve la trace de la pile côté serveur en l’ajoutant au message avant que l’exception ne soit levée à nouveau sur le site d’appel client.</span><span class="sxs-lookup"><span data-stu-id="6fe4d-103">Preserves the server-side stack trace by appending it to the message before the exception is rethrown at the client call site.</span></span>

```csharp
internal Exception PrepForRemoting();
```

## <a name="returns"></a><span data-ttu-id="6fe4d-104">Retours</span><span class="sxs-lookup"><span data-stu-id="6fe4d-104">Returns</span></span>

<xref:System.Exception>  
<span data-ttu-id="6fe4d-105">Cette instance de l'objet <xref:System.Exception>.</span><span class="sxs-lookup"><span data-stu-id="6fe4d-105">This <xref:System.Exception> instance.</span></span>

## <a name="remarks"></a><span data-ttu-id="6fe4d-106">Notes</span><span class="sxs-lookup"><span data-stu-id="6fe4d-106">Remarks</span></span>

> [!WARNING]
> <span data-ttu-id="6fe4d-107">La méthode `Exception.PrepForRemoting` est interne et n’est pas destinée à être utilisée directement dans votre code.</span><span class="sxs-lookup"><span data-stu-id="6fe4d-107">The `Exception.PrepForRemoting` method is internal and is not meant to be used directly in your code.</span></span>
>
> <span data-ttu-id="6fe4d-108">Microsoft ne prend pas en charge l’utilisation de cette méthode dans une application de production en l’absence de toute circonstance.</span><span class="sxs-lookup"><span data-stu-id="6fe4d-108">Microsoft does not support the use of this method in a production application under any circumstance.</span></span>

## <a name="requirements"></a><span data-ttu-id="6fe4d-109">Spécifications</span><span class="sxs-lookup"><span data-stu-id="6fe4d-109">Requirements</span></span>

<span data-ttu-id="6fe4d-110">**Espace de noms :** <xref:System></span><span class="sxs-lookup"><span data-stu-id="6fe4d-110">**Namespace:** <xref:System></span></span>

<span data-ttu-id="6fe4d-111">**Assembly :** mscorlib. dll (dans mscorlib. dll)</span><span class="sxs-lookup"><span data-stu-id="6fe4d-111">**Assembly:** mscorlib.dll (in mscorlib.dll)</span></span>

<span data-ttu-id="6fe4d-112">**Versions de .NET Framework :** Disponible depuis 1,0.</span><span class="sxs-lookup"><span data-stu-id="6fe4d-112">**.NET Framework versions:** Available since 1.0.</span></span>
