---
title: Méthode SqlStreamChars. Write (Char [], Int32, Int32) (System. Data. SqlTypes)
author: stevestein
ms.author: sstein
ms.date: 12/20/2018
ms.technology: dotnet-data
topic_type:
- apiref
api_name:
- System.Data.SqlTypes.SqlStreamChars.Write
api_location:
- System.Data.dll
api_type:
- Assembly
ms.openlocfilehash: 9d952041122ceb3824712bd81cab7ce4789c9db8
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72395587"
---
# <a name="sqlstreamcharswritechar-int32-int32-method"></a><span data-ttu-id="70d1d-102">SqlStreamChars. Write (Char [], Int32, Int32), méthode</span><span class="sxs-lookup"><span data-stu-id="70d1d-102">SqlStreamChars.Write(Char[], Int32, Int32) Method</span></span>

<span data-ttu-id="70d1d-103">En cas de substitution dans une classe dérivée, écrit une séquence de caractères dans le flux actuel et avance la position actuelle dans ce flux du nombre de caractères écrits.</span><span class="sxs-lookup"><span data-stu-id="70d1d-103">When overridden in a derived class, writes a sequence of characters to the current stream and advances the current position within this stream by the number of characters written.</span></span> <span data-ttu-id="70d1d-104">L’assembly qui contient cette méthode a une relation Friend avec SQLAccess. dll.</span><span class="sxs-lookup"><span data-stu-id="70d1d-104">The assembly that contains this method has a friend relationship with SQLAccess.dll.</span></span> <span data-ttu-id="70d1d-105">Elle est destinée à être utilisée par SQL Server.</span><span class="sxs-lookup"><span data-stu-id="70d1d-105">It's intended for use by SQL Server.</span></span> <span data-ttu-id="70d1d-106">Pour les autres bases de données, utilisez le mécanisme d’hébergement fourni par cette base de données.</span><span class="sxs-lookup"><span data-stu-id="70d1d-106">For other databases, use the hosting mechanism provided by that database.</span></span>

```csharp
public abstract void Write (char[] buffer, int offset, int count);
```

## <a name="parameters"></a><span data-ttu-id="70d1d-107">Paramètres</span><span class="sxs-lookup"><span data-stu-id="70d1d-107">Parameters</span></span>

`buffer`  
<span data-ttu-id="70d1d-108">Tableau de caractères à écrire.</span><span class="sxs-lookup"><span data-stu-id="70d1d-108">A char array to write.</span></span>

`offset`  
<span data-ttu-id="70d1d-109">Décalage par rapport à Origin.</span><span class="sxs-lookup"><span data-stu-id="70d1d-109">An offset relative to origin.</span></span>

`count`  
<span data-ttu-id="70d1d-110">Nombre de caractères à écrire dans le flux actuel.</span><span class="sxs-lookup"><span data-stu-id="70d1d-110">The number of characters to be written to the current stream.</span></span>

## <a name="remarks"></a><span data-ttu-id="70d1d-111">Notes</span><span class="sxs-lookup"><span data-stu-id="70d1d-111">Remarks</span></span>

> [!WARNING]
> <span data-ttu-id="70d1d-112">La méthode `SqlStreamChars.Write` est privée et n’est pas destinée à être utilisée directement dans votre code.</span><span class="sxs-lookup"><span data-stu-id="70d1d-112">The `SqlStreamChars.Write` method is private and is not meant to be used directly in your code.</span></span>
>
> <span data-ttu-id="70d1d-113">Microsoft ne prend pas en charge l’utilisation de cette méthode en cas d’écriture dans une application de production.</span><span class="sxs-lookup"><span data-stu-id="70d1d-113">Microsoft does not support the use of this method write in a production application under any circumstance.</span></span>

## <a name="requirements"></a><span data-ttu-id="70d1d-114">spécifications</span><span class="sxs-lookup"><span data-stu-id="70d1d-114">Requirements</span></span>

<span data-ttu-id="70d1d-115">**Espace de noms :** <xref:System.Data.SqlTypes></span><span class="sxs-lookup"><span data-stu-id="70d1d-115">**Namespace:** <xref:System.Data.SqlTypes></span></span>

<span data-ttu-id="70d1d-116">**Assembly :** System. Data (dans System. Data. dll)</span><span class="sxs-lookup"><span data-stu-id="70d1d-116">**Assembly:** System.Data (in System.Data.dll)</span></span>

<span data-ttu-id="70d1d-117">**Versions de .NET Framework :** Disponible depuis 2,0.</span><span class="sxs-lookup"><span data-stu-id="70d1d-117">**.NET Framework versions:** Available since 2.0.</span></span>
