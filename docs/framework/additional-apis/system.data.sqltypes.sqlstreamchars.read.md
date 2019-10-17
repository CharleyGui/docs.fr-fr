---
title: Méthode SqlStreamChars. Read (Char [], Int32, Int32) (System. Data. SqlTypes)
author: stevestein
ms.author: sstein
ms.date: 12/20/2018
ms.technology: dotnet-data
topic_type:
- apiref
api_name:
- System.Data.SqlTypes.SqlStreamChars.Read
api_location:
- System.Data.dll
api_type:
- Assembly
ms.openlocfilehash: 9c8a1526e75fdc304022e74a7cc52506762489ea
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72395752"
---
# <a name="sqlstreamcharsreadchar-int32-int32-method"></a><span data-ttu-id="eff74-102">Méthode SqlStreamChars. Read (Char [], Int32, Int32)</span><span class="sxs-lookup"><span data-stu-id="eff74-102">SqlStreamChars.Read(Char[], Int32, Int32) Method</span></span>

<span data-ttu-id="eff74-103">En cas de substitution dans une classe dérivée, lit le jeu de caractères suivant dans le flux d’entrée.</span><span class="sxs-lookup"><span data-stu-id="eff74-103">When overridden in a derived class, reads the next set of characters from the input stream.</span></span> <span data-ttu-id="eff74-104">L’assembly qui contient cette méthode a une relation Friend avec SQLAccess. dll.</span><span class="sxs-lookup"><span data-stu-id="eff74-104">The assembly that contains this method has a friend relationship with SQLAccess.dll.</span></span> <span data-ttu-id="eff74-105">Elle est destinée à être utilisée par SQL Server.</span><span class="sxs-lookup"><span data-stu-id="eff74-105">It's intended for use by SQL Server.</span></span> <span data-ttu-id="eff74-106">Pour les autres bases de données, utilisez le mécanisme d’hébergement fourni par cette base de données.</span><span class="sxs-lookup"><span data-stu-id="eff74-106">For other databases, use the hosting mechanism provided by that database.</span></span>

```csharp
public abstract int Read (char[] buffer, int offset, int count);
```

## <a name="parameters"></a><span data-ttu-id="eff74-107">Paramètres</span><span class="sxs-lookup"><span data-stu-id="eff74-107">Parameters</span></span>

`buffer`\
<span data-ttu-id="eff74-108">Tableau de caractères à lire.</span><span class="sxs-lookup"><span data-stu-id="eff74-108">A char array to read.</span></span>

`offset`\
<span data-ttu-id="eff74-109">Décalage par rapport à Origin.</span><span class="sxs-lookup"><span data-stu-id="eff74-109">An offset relative to origin.</span></span>

`count`\
<span data-ttu-id="eff74-110">Nombre de caractères à lire à partir du flux actuel.</span><span class="sxs-lookup"><span data-stu-id="eff74-110">The number of characters to be read from the current stream.</span></span>

## <a name="returns"></a><span data-ttu-id="eff74-111">Returns (Retours)</span><span class="sxs-lookup"><span data-stu-id="eff74-111">Returns</span></span>

<xref:System.Int32>\
<span data-ttu-id="eff74-112">Nombre total de caractères lus dans la mémoire tampon.</span><span class="sxs-lookup"><span data-stu-id="eff74-112">The total number of characters read into the buffer.</span></span>

## <a name="remarks"></a><span data-ttu-id="eff74-113">Notes</span><span class="sxs-lookup"><span data-stu-id="eff74-113">Remarks</span></span>

> [!WARNING]
> <span data-ttu-id="eff74-114">La méthode `SqlStreamChars.Read` est privée et n’est pas destinée à être utilisée directement dans votre code.</span><span class="sxs-lookup"><span data-stu-id="eff74-114">The `SqlStreamChars.Read` method is private and is not meant to be used directly in your code.</span></span>
>
> <span data-ttu-id="eff74-115">Microsoft ne prend pas en charge l’utilisation de cette méthode dans une application de production en l’absence de toute circonstance.</span><span class="sxs-lookup"><span data-stu-id="eff74-115">Microsoft does not support the use of this method in a production application under any circumstance.</span></span>

## <a name="requirements"></a><span data-ttu-id="eff74-116">spécifications</span><span class="sxs-lookup"><span data-stu-id="eff74-116">Requirements</span></span>

<span data-ttu-id="eff74-117">**Espace de noms :** <xref:System.Data.SqlTypes></span><span class="sxs-lookup"><span data-stu-id="eff74-117">**Namespace:** <xref:System.Data.SqlTypes></span></span>

<span data-ttu-id="eff74-118">**Assembly :** System. Data (dans System. Data. dll)</span><span class="sxs-lookup"><span data-stu-id="eff74-118">**Assembly:** System.Data (in System.Data.dll)</span></span>

<span data-ttu-id="eff74-119">**Versions de .NET Framework :** Disponible depuis 2,0.</span><span class="sxs-lookup"><span data-stu-id="eff74-119">**.NET Framework versions:** Available since 2.0.</span></span>
