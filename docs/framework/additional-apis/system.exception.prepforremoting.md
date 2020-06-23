---
title: Exception. PrepForRemoting, méthode (System)
description: Passez en revue la méthode exception. PrepForRemoting dans .NET. La méthode ajoute la trace de la pile côté serveur au message avant que l’exception ne soit levée à nouveau sur le client.
ms.date: 10/08/2019
topic_type:
- apiref
api_name:
- System.Exception.PrepForRemoting
api_location:
- mscorlib.dll
api_type:
- Assembly
ms.openlocfilehash: 9ceb73499ae3bb308975e6db5b961bfe40165ba3
ms.sourcegitcommit: 1c37a894c923bea021a3cc38ce7cba946357bbe1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2020
ms.locfileid: "85105261"
---
# <a name="exceptionprepforremoting-method"></a><span data-ttu-id="6f6b9-104">Exception.PrepForRemoting, méthode</span><span class="sxs-lookup"><span data-stu-id="6f6b9-104">Exception.PrepForRemoting Method</span></span>

<span data-ttu-id="6f6b9-105">Conserve la trace de la pile côté serveur en l’ajoutant au message avant que l’exception ne soit levée à nouveau sur le site d’appel client.</span><span class="sxs-lookup"><span data-stu-id="6f6b9-105">Preserves the server-side stack trace by appending it to the message before the exception is rethrown at the client call site.</span></span>

```csharp
internal Exception PrepForRemoting();
```

## <a name="returns"></a><span data-ttu-id="6f6b9-106">Retours</span><span class="sxs-lookup"><span data-stu-id="6f6b9-106">Returns</span></span>

<xref:System.Exception>  
<span data-ttu-id="6f6b9-107">Cette instance de l'objet <xref:System.Exception>.</span><span class="sxs-lookup"><span data-stu-id="6f6b9-107">This <xref:System.Exception> instance.</span></span>

## <a name="remarks"></a><span data-ttu-id="6f6b9-108">Remarques</span><span class="sxs-lookup"><span data-stu-id="6f6b9-108">Remarks</span></span>

> [!WARNING]
> <span data-ttu-id="6f6b9-109">La `Exception.PrepForRemoting` méthode est interne et n’est pas destinée à être utilisée directement dans votre code.</span><span class="sxs-lookup"><span data-stu-id="6f6b9-109">The `Exception.PrepForRemoting` method is internal and is not meant to be used directly in your code.</span></span>
>
> <span data-ttu-id="6f6b9-110">Microsoft ne prend pas en charge l’utilisation de cette méthode dans une application de production en l’absence de toute circonstance.</span><span class="sxs-lookup"><span data-stu-id="6f6b9-110">Microsoft does not support the use of this method in a production application under any circumstance.</span></span>

## <a name="requirements"></a><span data-ttu-id="6f6b9-111">Spécifications</span><span class="sxs-lookup"><span data-stu-id="6f6b9-111">Requirements</span></span>

<span data-ttu-id="6f6b9-112">**Espace de noms :** <xref:System></span><span class="sxs-lookup"><span data-stu-id="6f6b9-112">**Namespace:** <xref:System></span></span>

<span data-ttu-id="6f6b9-113">**Assembly :** mscorlib.dll (dans mscorlib.dll)</span><span class="sxs-lookup"><span data-stu-id="6f6b9-113">**Assembly:** mscorlib.dll (in mscorlib.dll)</span></span>

<span data-ttu-id="6f6b9-114">**Versions de .NET Framework :** Disponible depuis 1,0.</span><span class="sxs-lookup"><span data-stu-id="6f6b9-114">**.NET Framework versions:** Available since 1.0.</span></span>
