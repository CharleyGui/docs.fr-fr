---
title: Propriété SqlStreamChars. IsNull (System. Data. SqlTypes)
author: stevestein
ms.author: sstein
ms.date: 12/19/2018
ms.technology: dotnet-data
topic_type:
- apiref
api_name:
- System.Data.SqlTypes.SqlStreamChars.IsNull
- System.Data.SqlTypes.SqlStreamChars.get_IsNull
api_location:
- System.Data.dll
api_type:
- Assembly
ms.openlocfilehash: d80f653724b3ef0a1cadb69a5f72b1d9455597d6
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72395735"
---
# <a name="sqlstreamcharsisnull-property"></a><span data-ttu-id="ffc3d-102">SqlStreamChars. IsNull, propriété</span><span class="sxs-lookup"><span data-stu-id="ffc3d-102">SqlStreamChars.IsNull Property</span></span>

<span data-ttu-id="ffc3d-103">En cas de substitution dans une classe dérivée, obtient une valeur qui indique si le flux est `null`.</span><span class="sxs-lookup"><span data-stu-id="ffc3d-103">When overridden in a derived class, gets a value that indicates whether the stream is `null`.</span></span> <span data-ttu-id="ffc3d-104">L’assembly qui contient cette propriété a une relation Friend avec SQLAccess. dll.</span><span class="sxs-lookup"><span data-stu-id="ffc3d-104">The assembly that contains this property has a friend relationship with SQLAccess.dll.</span></span> <span data-ttu-id="ffc3d-105">Elle est destinée à être utilisée par SQL Server.</span><span class="sxs-lookup"><span data-stu-id="ffc3d-105">It's intended for use by SQL Server.</span></span> <span data-ttu-id="ffc3d-106">Pour les autres bases de données, utilisez le mécanisme d’hébergement fourni par cette base de données.</span><span class="sxs-lookup"><span data-stu-id="ffc3d-106">For other databases, use the hosting mechanism provided by that database.</span></span>

## <a name="syntax"></a><span data-ttu-id="ffc3d-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ffc3d-107">Syntax</span></span>

```csharp
public abstract bool IsNull { get; }
```

## <a name="property-value"></a><span data-ttu-id="ffc3d-108">Valeur de la propriété</span><span class="sxs-lookup"><span data-stu-id="ffc3d-108">Property value</span></span>

<xref:System.Boolean>\
<span data-ttu-id="ffc3d-109">`true` si le flux est `null` ; dans le cas contraire, `false`.</span><span class="sxs-lookup"><span data-stu-id="ffc3d-109">`true` if the stream is `null`; otherwise, `false`.</span></span>

## <a name="remarks"></a><span data-ttu-id="ffc3d-110">Notes</span><span class="sxs-lookup"><span data-stu-id="ffc3d-110">Remarks</span></span>

> [!WARNING]
> <span data-ttu-id="ffc3d-111">La propriété `SqlStreamChars.IsNull` est privée et n’est pas destinée à être utilisée directement dans votre code.</span><span class="sxs-lookup"><span data-stu-id="ffc3d-111">The `SqlStreamChars.IsNull` property is private and is not meant to be used directly in your code.</span></span>
>
> <span data-ttu-id="ffc3d-112">Microsoft ne prend pas en charge l’utilisation de cette propriété dans une application de production en l’absence de toute circonstance.</span><span class="sxs-lookup"><span data-stu-id="ffc3d-112">Microsoft does not support the use of this property in a production application under any circumstance.</span></span>

## <a name="requirements"></a><span data-ttu-id="ffc3d-113">spécifications</span><span class="sxs-lookup"><span data-stu-id="ffc3d-113">Requirements</span></span>

<span data-ttu-id="ffc3d-114">**Espace de noms :** <xref:System.Data.SqlTypes></span><span class="sxs-lookup"><span data-stu-id="ffc3d-114">**Namespace:** <xref:System.Data.SqlTypes></span></span>

<span data-ttu-id="ffc3d-115">**Assembly :** System. Data (dans System. Data. dll)</span><span class="sxs-lookup"><span data-stu-id="ffc3d-115">**Assembly:** System.Data (in System.Data.dll)</span></span>

<span data-ttu-id="ffc3d-116">**Versions de .NET Framework :** Disponible depuis 2,0.</span><span class="sxs-lookup"><span data-stu-id="ffc3d-116">**.NET Framework versions:** Available since 2.0.</span></span>
