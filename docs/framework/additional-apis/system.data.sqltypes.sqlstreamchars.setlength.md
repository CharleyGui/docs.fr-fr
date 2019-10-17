---
title: Méthode SqlStreamChars. SetLength (Int64) (System. Data. SqlTypes)
author: stevestein
ms.author: sstein
ms.date: 12/20/2018
ms.technology: dotnet-data
topic_type:
- apiref
api_name:
- System.Data.SqlTypes.SqlStreamChars.SetLength
api_location:
- System.Data.dll
api_type:
- Assembly
ms.openlocfilehash: 291d6e9395581f2370dafc728521a314d54a686d
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72395723"
---
# <a name="sqlstreamcharssetlengthint64-method"></a><span data-ttu-id="87904-102">Méthode SqlStreamChars. SetLength (Int64)</span><span class="sxs-lookup"><span data-stu-id="87904-102">SqlStreamChars.SetLength(Int64) Method</span></span>

<span data-ttu-id="87904-103">En cas de substitution dans une classe dérivée, libère les ressources utilisées par le flux.</span><span class="sxs-lookup"><span data-stu-id="87904-103">When overridden in a derived class, releases the resources used by the stream.</span></span> <span data-ttu-id="87904-104">L’assembly qui contient cette méthode a une relation Friend avec SQLAccess. dll.</span><span class="sxs-lookup"><span data-stu-id="87904-104">The assembly that contains this method has a friend relationship with SQLAccess.dll.</span></span> <span data-ttu-id="87904-105">Elle est destinée à être utilisée par SQL Server.</span><span class="sxs-lookup"><span data-stu-id="87904-105">It's intended for use by SQL Server.</span></span> <span data-ttu-id="87904-106">Pour les autres bases de données, utilisez le mécanisme d’hébergement fourni par cette base de données.</span><span class="sxs-lookup"><span data-stu-id="87904-106">For other databases, use the hosting mechanism provided by that database.</span></span>

```csharp
public abstract void SetLength (long value);
```

## <a name="parameters"></a><span data-ttu-id="87904-107">Paramètres</span><span class="sxs-lookup"><span data-stu-id="87904-107">Parameters</span></span>

`value`\
<span data-ttu-id="87904-108">Longueur souhaitée du flux actuel en octets.</span><span class="sxs-lookup"><span data-stu-id="87904-108">The desired length of the current stream in bytes.</span></span>

## <a name="remarks"></a><span data-ttu-id="87904-109">Notes</span><span class="sxs-lookup"><span data-stu-id="87904-109">Remarks</span></span>

> [!WARNING]
> <span data-ttu-id="87904-110">La méthode `SqlStreamChars.SetLength` est privée et n’est pas destinée à être utilisée directement dans votre code.</span><span class="sxs-lookup"><span data-stu-id="87904-110">The `SqlStreamChars.SetLength` method is private and is not meant to be used directly in your code.</span></span>
>
> <span data-ttu-id="87904-111">Microsoft ne prend pas en charge l’utilisation de cette méthode dans une application de production en l’absence de toute circonstance.</span><span class="sxs-lookup"><span data-stu-id="87904-111">Microsoft does not support the use of this method in a production application under any circumstance.</span></span>

## <a name="requirements"></a><span data-ttu-id="87904-112">spécifications</span><span class="sxs-lookup"><span data-stu-id="87904-112">Requirements</span></span>

<span data-ttu-id="87904-113">**Espace de noms :** <xref:System.Data.SqlTypes></span><span class="sxs-lookup"><span data-stu-id="87904-113">**Namespace:** <xref:System.Data.SqlTypes></span></span>

<span data-ttu-id="87904-114">**Assembly :** System. Data (dans System. Data. dll)</span><span class="sxs-lookup"><span data-stu-id="87904-114">**Assembly:** System.Data (in System.Data.dll)</span></span>

<span data-ttu-id="87904-115">**Versions de .NET Framework :** Disponible depuis 2,0.</span><span class="sxs-lookup"><span data-stu-id="87904-115">**.NET Framework versions:** Available since 2.0.</span></span>
