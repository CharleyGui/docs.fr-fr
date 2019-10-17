---
title: Propriété SqlStreamChars. length (System. Data. SqlTypes)
author: stevestein
ms.author: sstein
ms.date: 12/19/2018
ms.technology: dotnet-data
topic_type:
- apiref
api_name:
- System.Data.SqlTypes.SqlStreamChars.Length
- System.Data.SqlTypes.SqlStreamChars.get_Length
api_location:
- System.Data.dll
api_type:
- Assembly
ms.openlocfilehash: 2171b10d1c0eb7bcad894cc44c5103bdab18b0a5
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72395609"
---
# <a name="sqlstreamcharslength-property"></a><span data-ttu-id="ab253-102">SqlStreamChars. Length, propriété</span><span class="sxs-lookup"><span data-stu-id="ab253-102">SqlStreamChars.Length Property</span></span>

<span data-ttu-id="ab253-103">En cas de substitution dans une classe dérivée, obtient la longueur du flux actuel.</span><span class="sxs-lookup"><span data-stu-id="ab253-103">When overridden in a derived class, gets the length of the current stream.</span></span> <span data-ttu-id="ab253-104">L’assembly qui contient cette propriété a une relation Friend avec SQLAccess. dll.</span><span class="sxs-lookup"><span data-stu-id="ab253-104">The assembly that contains this property has a friend relationship with SQLAccess.dll.</span></span> <span data-ttu-id="ab253-105">Elle est destinée à être utilisée par SQL Server.</span><span class="sxs-lookup"><span data-stu-id="ab253-105">It's intended for use by SQL Server.</span></span> <span data-ttu-id="ab253-106">Pour les autres bases de données, utilisez le mécanisme d’hébergement fourni par cette base de données.</span><span class="sxs-lookup"><span data-stu-id="ab253-106">For other databases, use the hosting mechanism provided by that database.</span></span>

## <a name="syntax"></a><span data-ttu-id="ab253-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ab253-107">Syntax</span></span>

```csharp
public abstract long Length { get; }
```

## <a name="property-value"></a><span data-ttu-id="ab253-108">Valeur de la propriété</span><span class="sxs-lookup"><span data-stu-id="ab253-108">Property value</span></span>

<xref:System.Int64>\
<span data-ttu-id="ab253-109">Longueur du flux.</span><span class="sxs-lookup"><span data-stu-id="ab253-109">The length of the stream.</span></span>

## <a name="remarks"></a><span data-ttu-id="ab253-110">Notes</span><span class="sxs-lookup"><span data-stu-id="ab253-110">Remarks</span></span>

> [!WARNING]
> <span data-ttu-id="ab253-111">La propriété `SqlStreamChars.Length` est privée et n’est pas destinée à être utilisée directement dans votre code.</span><span class="sxs-lookup"><span data-stu-id="ab253-111">The `SqlStreamChars.Length` property is private and is not meant to be used directly in your code.</span></span>
>
> <span data-ttu-id="ab253-112">Microsoft ne prend pas en charge l’utilisation de cette propriété dans une application de production en l’absence de toute circonstance.</span><span class="sxs-lookup"><span data-stu-id="ab253-112">Microsoft does not support the use of this property in a production application under any circumstance.</span></span>

## <a name="requirements"></a><span data-ttu-id="ab253-113">spécifications</span><span class="sxs-lookup"><span data-stu-id="ab253-113">Requirements</span></span>

<span data-ttu-id="ab253-114">**Espace de noms :** <xref:System.Data.SqlTypes></span><span class="sxs-lookup"><span data-stu-id="ab253-114">**Namespace:** <xref:System.Data.SqlTypes></span></span>

<span data-ttu-id="ab253-115">**Assembly :** System. Data (dans System. Data. dll)</span><span class="sxs-lookup"><span data-stu-id="ab253-115">**Assembly:** System.Data (in System.Data.dll)</span></span>

<span data-ttu-id="ab253-116">**Versions de .NET Framework :** Disponible depuis 2,0.</span><span class="sxs-lookup"><span data-stu-id="ab253-116">**.NET Framework versions:** Available since 2.0.</span></span>
