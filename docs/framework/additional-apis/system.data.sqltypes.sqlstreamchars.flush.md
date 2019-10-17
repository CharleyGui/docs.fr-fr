---
title: Méthode SqlStreamChars. Flush (System. Data. SqlTypes)
author: stevestein
ms.author: sstein
ms.date: 12/20/2018
ms.technology: dotnet-data
topic_type:
- apiref
api_name:
- System.Data.SqlTypes.SqlStreamChars.Flush
api_location:
- System.Data.dll
api_type:
- Assembly
ms.openlocfilehash: 38ade5ce38cfe5003b2d06c0d8bb2db1a20bc05b
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72395622"
---
# <a name="sqlstreamcharsflush-method"></a><span data-ttu-id="b56a6-102">SqlStreamChars. Flush, méthode</span><span class="sxs-lookup"><span data-stu-id="b56a6-102">SqlStreamChars.Flush Method</span></span>

<span data-ttu-id="b56a6-103">En cas de remplacement dans une classe dérivée, efface toutes les mémoires tampons pour ce flux et provoque l'écriture de toutes les données se trouvant dans des mémoires tampons sur l'appareil sous-jacent.</span><span class="sxs-lookup"><span data-stu-id="b56a6-103">When overridden in a derived class, clears all buffers for this stream and causes any buffered data to be written to the underlying device.</span></span> <span data-ttu-id="b56a6-104">L’assembly qui contient cette méthode a une relation Friend avec SQLAccess. dll.</span><span class="sxs-lookup"><span data-stu-id="b56a6-104">The assembly that contains this method has a friend relationship with SQLAccess.dll.</span></span> <span data-ttu-id="b56a6-105">Elle est destinée à être utilisée par SQL Server.</span><span class="sxs-lookup"><span data-stu-id="b56a6-105">It's intended for use by SQL Server.</span></span> <span data-ttu-id="b56a6-106">Pour les autres bases de données, utilisez le mécanisme d’hébergement fourni par cette base de données.</span><span class="sxs-lookup"><span data-stu-id="b56a6-106">For other databases, use the hosting mechanism provided by that database.</span></span>

## <a name="syntax"></a><span data-ttu-id="b56a6-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b56a6-107">Syntax</span></span>

```csharp
public abstract void Flush ();
```

## <a name="remarks"></a><span data-ttu-id="b56a6-108">Notes</span><span class="sxs-lookup"><span data-stu-id="b56a6-108">Remarks</span></span>

> [!WARNING]
> <span data-ttu-id="b56a6-109">La méthode `SqlStreamChars.Flush` est privée et n’est pas destinée à être utilisée directement dans votre code.</span><span class="sxs-lookup"><span data-stu-id="b56a6-109">The `SqlStreamChars.Flush` method is private and is not meant to be used directly in your code.</span></span>
>
> <span data-ttu-id="b56a6-110">Microsoft ne prend pas en charge l’utilisation de cette méthode dans une application de production en l’absence de toute circonstance.</span><span class="sxs-lookup"><span data-stu-id="b56a6-110">Microsoft does not support the use of this method in a production application under any circumstance.</span></span>

## <a name="requirements"></a><span data-ttu-id="b56a6-111">spécifications</span><span class="sxs-lookup"><span data-stu-id="b56a6-111">Requirements</span></span>

<span data-ttu-id="b56a6-112">**Espace de noms :** <xref:System.Data.SqlTypes></span><span class="sxs-lookup"><span data-stu-id="b56a6-112">**Namespace:** <xref:System.Data.SqlTypes></span></span>

<span data-ttu-id="b56a6-113">**Assembly :** System. Data (dans System. Data. dll)</span><span class="sxs-lookup"><span data-stu-id="b56a6-113">**Assembly:** System.Data (in System.Data.dll)</span></span>

<span data-ttu-id="b56a6-114">**Versions de .NET Framework :** Disponible depuis 2,0.</span><span class="sxs-lookup"><span data-stu-id="b56a6-114">**.NET Framework versions:** Available since 2.0.</span></span>
