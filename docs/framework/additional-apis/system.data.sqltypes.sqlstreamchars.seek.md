---
title: Méthode SqlStreamChars. Seek (Int64, SeekOrigin) (System. Data. SqlTypes)
author: stevestein
ms.author: sstein
ms.date: 12/20/2018
ms.technology: dotnet-data
topic_type:
- apiref
api_name:
- System.Data.SqlTypes.SqlStreamChars.Seek
api_location:
- System.Data.dll
api_type:
- Assembly
ms.openlocfilehash: db8aba0a86c140ba62af8056011226532d415951
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72395593"
---
# <a name="sqlstreamcharsseekint64-seekorigin-method"></a><span data-ttu-id="3f1bc-102">SqlStreamChars. Seek (Int64, SeekOrigin), méthode</span><span class="sxs-lookup"><span data-stu-id="3f1bc-102">SqlStreamChars.Seek(Int64, SeekOrigin) Method</span></span>

<span data-ttu-id="3f1bc-103">En cas de remplacement dans une classe dérivée, définit la position dans le flux actuel.</span><span class="sxs-lookup"><span data-stu-id="3f1bc-103">When overridden in a derived class, sets the position within the current stream.</span></span> <span data-ttu-id="3f1bc-104">L’assembly qui contient cette méthode a une relation Friend avec SQLAccess. dll.</span><span class="sxs-lookup"><span data-stu-id="3f1bc-104">The assembly that contains this method has a friend relationship with SQLAccess.dll.</span></span> <span data-ttu-id="3f1bc-105">Elle est destinée à être utilisée par SQL Server.</span><span class="sxs-lookup"><span data-stu-id="3f1bc-105">It's intended for use by SQL Server.</span></span> <span data-ttu-id="3f1bc-106">Pour les autres bases de données, utilisez le mécanisme d’hébergement fourni par cette base de données.</span><span class="sxs-lookup"><span data-stu-id="3f1bc-106">For other databases, use the hosting mechanism provided by that database.</span></span>

```csharp
public abstract long Seek (long offset, System.IO.SeekOrigin origin);
```

## <a name="parameters"></a><span data-ttu-id="3f1bc-107">Paramètres</span><span class="sxs-lookup"><span data-stu-id="3f1bc-107">Parameters</span></span>

`offset`\
<span data-ttu-id="3f1bc-108">Offset d’octet par rapport à `origin`.</span><span class="sxs-lookup"><span data-stu-id="3f1bc-108">A byte offset relative to `origin`.</span></span>

`origin`\
<span data-ttu-id="3f1bc-109">L’une des valeurs d’énumération qui indique le point de référence à partir duquel obtenir la nouvelle position.</span><span class="sxs-lookup"><span data-stu-id="3f1bc-109">One of the enumeration values that indicates the reference point from which to obtain the new position.</span></span>

## <a name="returns"></a><span data-ttu-id="3f1bc-110">Returns (Retours)</span><span class="sxs-lookup"><span data-stu-id="3f1bc-110">Returns</span></span>

<xref:System.Int32>\
<span data-ttu-id="3f1bc-111">Nouvelle position dans le flux actuel.</span><span class="sxs-lookup"><span data-stu-id="3f1bc-111">The new position within the current stream.</span></span>

## <a name="remarks"></a><span data-ttu-id="3f1bc-112">Notes</span><span class="sxs-lookup"><span data-stu-id="3f1bc-112">Remarks</span></span>

> [!WARNING]
> <span data-ttu-id="3f1bc-113">La méthode `SqlStreamChars.Seek` est privée et n’est pas destinée à être utilisée directement dans votre code.</span><span class="sxs-lookup"><span data-stu-id="3f1bc-113">The `SqlStreamChars.Seek` method is private and is not meant to be used directly in your code.</span></span>
>
> <span data-ttu-id="3f1bc-114">Microsoft ne prend pas en charge l’utilisation de cette méthode dans une application de production en l’absence de toute circonstance.</span><span class="sxs-lookup"><span data-stu-id="3f1bc-114">Microsoft does not support the use of this method in a production application under any circumstance.</span></span>

## <a name="requirements"></a><span data-ttu-id="3f1bc-115">spécifications</span><span class="sxs-lookup"><span data-stu-id="3f1bc-115">Requirements</span></span>

<span data-ttu-id="3f1bc-116">**Espace de noms :** <xref:System.Data.SqlTypes></span><span class="sxs-lookup"><span data-stu-id="3f1bc-116">**Namespace:** <xref:System.Data.SqlTypes></span></span>

<span data-ttu-id="3f1bc-117">**Assembly :** System. Data (dans System. Data. dll)</span><span class="sxs-lookup"><span data-stu-id="3f1bc-117">**Assembly:** System.Data (in System.Data.dll)</span></span>

<span data-ttu-id="3f1bc-118">**Versions de .NET Framework :** Disponible depuis 2,0.</span><span class="sxs-lookup"><span data-stu-id="3f1bc-118">**.NET Framework versions:** Available since 2.0.</span></span>
