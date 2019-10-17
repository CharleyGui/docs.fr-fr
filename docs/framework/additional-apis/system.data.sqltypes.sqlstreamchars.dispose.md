---
title: Méthode SqlStreamChars. Dispose (Boolean) (System. Data. SqlTypes)
author: stevestein
ms.author: sstein
ms.date: 12/20/2018
ms.technology: dotnet-data
topic_type:
- apiref
api_name:
- System.Data.SqlTypes.SqlStreamChars.Dispose
api_location:
- System.Data.dll
api_type:
- Assembly
ms.openlocfilehash: 44dc97835b8a7141064e8de4d2d5325c40be5a34
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72395765"
---
# <a name="sqlstreamcharsdisposeboolean-method"></a><span data-ttu-id="a0faf-102">Méthode SqlStreamChars. Dispose (Boolean)</span><span class="sxs-lookup"><span data-stu-id="a0faf-102">SqlStreamChars.Dispose(Boolean) Method</span></span>

<span data-ttu-id="a0faf-103">En cas de substitution dans une classe dérivée, libère les ressources utilisées par le flux.</span><span class="sxs-lookup"><span data-stu-id="a0faf-103">When overridden in a derived class, releases the resources used by the stream.</span></span> <span data-ttu-id="a0faf-104">L’assembly qui contient cette méthode a une relation Friend avec SQLAccess. dll.</span><span class="sxs-lookup"><span data-stu-id="a0faf-104">The assembly that contains this method has a friend relationship with SQLAccess.dll.</span></span> <span data-ttu-id="a0faf-105">Elle est destinée à être utilisée par SQL Server.</span><span class="sxs-lookup"><span data-stu-id="a0faf-105">It's intended for use by SQL Server.</span></span> <span data-ttu-id="a0faf-106">Pour les autres bases de données, utilisez le mécanisme d’hébergement fourni par cette base de données.</span><span class="sxs-lookup"><span data-stu-id="a0faf-106">For other databases, use the hosting mechanism provided by that database.</span></span>

```csharp
protected virtual void Dispose (bool disposing);
```

## <a name="parameters"></a><span data-ttu-id="a0faf-107">Paramètres</span><span class="sxs-lookup"><span data-stu-id="a0faf-107">Parameters</span></span>

`disposing`\
<span data-ttu-id="a0faf-108">`true` pour libérer les ressources managées et non managées ; `false` pour ne libérer que les ressources non managées.</span><span class="sxs-lookup"><span data-stu-id="a0faf-108">`true` to release both managed and unmanaged resources; `false` to release only unmanaged resources.</span></span>

## <a name="remarks"></a><span data-ttu-id="a0faf-109">Notes</span><span class="sxs-lookup"><span data-stu-id="a0faf-109">Remarks</span></span>

> [!WARNING]
> <span data-ttu-id="a0faf-110">La méthode `SqlStreamChars.Dispose` est privée et n’est pas destinée à être utilisée directement dans votre code.</span><span class="sxs-lookup"><span data-stu-id="a0faf-110">The `SqlStreamChars.Dispose` method is private and is not meant to be used directly in your code.</span></span>
>
> <span data-ttu-id="a0faf-111">Microsoft ne prend pas en charge l’utilisation de cette méthode dans une application de production en l’absence de toute circonstance.</span><span class="sxs-lookup"><span data-stu-id="a0faf-111">Microsoft does not support the use of this method in a production application under any circumstance.</span></span>

## <a name="requirements"></a><span data-ttu-id="a0faf-112">spécifications</span><span class="sxs-lookup"><span data-stu-id="a0faf-112">Requirements</span></span>

<span data-ttu-id="a0faf-113">**Espace de noms :** <xref:System.Data.SqlTypes></span><span class="sxs-lookup"><span data-stu-id="a0faf-113">**Namespace:** <xref:System.Data.SqlTypes></span></span>

<span data-ttu-id="a0faf-114">**Assembly :** System. Data (dans System. Data. dll)</span><span class="sxs-lookup"><span data-stu-id="a0faf-114">**Assembly:** System.Data (in System.Data.dll)</span></span>

<span data-ttu-id="a0faf-115">**Versions de .NET Framework :** Disponible depuis 2,0.</span><span class="sxs-lookup"><span data-stu-id="a0faf-115">**.NET Framework versions:** Available since 2.0.</span></span>
