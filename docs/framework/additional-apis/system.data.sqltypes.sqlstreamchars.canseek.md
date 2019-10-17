---
title: Propriété SqlStreamChars. CanSeek (System. Data. SqlTypes)
author: stevestein
ms.author: sstein
ms.date: 12/19/2018
ms.technology: dotnet-data
topic_type:
- apiref
api_name:
- System.Data.SqlTypes.SqlStreamChars.CanSeek
- System.Data.SqlTypes.SqlStreamChars.get_CanSeek
api_location:
- System.Data.dll
api_type:
- Assembly
ms.openlocfilehash: eb32978f62b7d46f0abf715e2bca347592c0fda8
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72395777"
---
# <a name="sqlstreamcharscanseek-property"></a><span data-ttu-id="5fc90-102">SqlStreamChars. CanSeek, propriété</span><span class="sxs-lookup"><span data-stu-id="5fc90-102">SqlStreamChars.CanSeek Property</span></span>

<span data-ttu-id="5fc90-103">En cas de substitution dans une classe dérivée, obtient une valeur qui indique si le flux en cours prend en charge l’opération de recherche.</span><span class="sxs-lookup"><span data-stu-id="5fc90-103">When overridden in a derived class, gets a value that indicates whether the current steam supports the seek operation.</span></span> <span data-ttu-id="5fc90-104">L’assembly qui contient cette propriété a une relation Friend avec SQLAccess. dll.</span><span class="sxs-lookup"><span data-stu-id="5fc90-104">The assembly that contains this property has a friend relationship with SQLAccess.dll.</span></span> <span data-ttu-id="5fc90-105">Elle est destinée à être utilisée par SQL Server.</span><span class="sxs-lookup"><span data-stu-id="5fc90-105">It's intended for use by SQL Server.</span></span> <span data-ttu-id="5fc90-106">Pour les autres bases de données, utilisez le mécanisme d’hébergement fourni par cette base de données.</span><span class="sxs-lookup"><span data-stu-id="5fc90-106">For other databases, use the hosting mechanism provided by that database.</span></span>

```csharp
public abstract bool CanSeek { get; }
```

## <a name="property-value"></a><span data-ttu-id="5fc90-107">Valeur de la propriété</span><span class="sxs-lookup"><span data-stu-id="5fc90-107">Property value</span></span>

<xref:System.Boolean>\
<span data-ttu-id="5fc90-108">`true` si le flux actuel prend en charge l’opération de recherche ; dans le cas contraire, `false`.</span><span class="sxs-lookup"><span data-stu-id="5fc90-108">`true` if the current steam supports the seek operation; otherwise, `false`.</span></span>

## <a name="remarks"></a><span data-ttu-id="5fc90-109">Notes</span><span class="sxs-lookup"><span data-stu-id="5fc90-109">Remarks</span></span>

> [!WARNING]
> <span data-ttu-id="5fc90-110">La propriété `SqlStreamChars.CanSeek` est privée et n’est pas destinée à être utilisée directement dans votre code.</span><span class="sxs-lookup"><span data-stu-id="5fc90-110">The `SqlStreamChars.CanSeek` property is private and is not meant to be used directly in your code.</span></span>
>
> <span data-ttu-id="5fc90-111">Microsoft ne prend pas en charge l’utilisation de cette propriété dans une application de production en l’absence de toute circonstance.</span><span class="sxs-lookup"><span data-stu-id="5fc90-111">Microsoft does not support the use of this property in a production application under any circumstance.</span></span>

## <a name="requirements"></a><span data-ttu-id="5fc90-112">spécifications</span><span class="sxs-lookup"><span data-stu-id="5fc90-112">Requirements</span></span>

<span data-ttu-id="5fc90-113">**Espace de noms :** <xref:System.Data.SqlTypes></span><span class="sxs-lookup"><span data-stu-id="5fc90-113">**Namespace:** <xref:System.Data.SqlTypes></span></span>

<span data-ttu-id="5fc90-114">**Assembly :** System. Data (dans System. Data. dll)</span><span class="sxs-lookup"><span data-stu-id="5fc90-114">**Assembly:** System.Data (in System.Data.dll)</span></span>

<span data-ttu-id="5fc90-115">**Versions de .NET Framework :** Disponible depuis 2,0.</span><span class="sxs-lookup"><span data-stu-id="5fc90-115">**.NET Framework versions:** Available since 2.0.</span></span>
