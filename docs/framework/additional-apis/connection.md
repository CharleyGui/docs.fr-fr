---
title: Classe de connexion (System.Net)
description: En savoir plus sur la classe Connection dans .NET. Cette classe analyse les réponses du serveur, les demandes de file d’attente et les demandes de pipeline. Il se trouve dans l’espace de noms System.NET.
ms.date: 05/01/2017
ms.technology: dotnet-networking
topic_type:
- apiref
api_name:
- System.Net.Connection
api_location:
- System.dll
api_type:
- Assembly
ms.assetid: 6f0b8902-f31c-4ab9-a8c9-de43228995ec
ms.openlocfilehash: cb28724ed782fc5395dc74e9c59249ebdea44ddf
ms.sourcegitcommit: 45c8eed045779b70a47b23169897459d0323dc89
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/18/2020
ms.locfileid: "84989832"
---
# <a name="connection-class"></a><span data-ttu-id="0e5ac-105">Connection, classe</span><span class="sxs-lookup"><span data-stu-id="0e5ac-105">Connection Class</span></span>

<span data-ttu-id="0e5ac-106">La `Connection` classe analyse les réponses du serveur, les demandes de file d’attente et les demandes de pipeline.</span><span class="sxs-lookup"><span data-stu-id="0e5ac-106">The `Connection` class parses server responses, queue requests, and pipeline requests.</span></span>

## <a name="syntax"></a><span data-ttu-id="0e5ac-107">Syntax</span><span class="sxs-lookup"><span data-stu-id="0e5ac-107">Syntax</span></span>
  
```csharp  
internal class Connection : PooledStream
```

> [!WARNING]
> <span data-ttu-id="0e5ac-108">La `Connection` classe est interne et n’est pas destinée à être utilisée directement dans votre code.</span><span class="sxs-lookup"><span data-stu-id="0e5ac-108">The `Connection` class is internal and is not meant to be used directly in your code.</span></span>
>
> <span data-ttu-id="0e5ac-109">Microsoft ne prend pas en charge l’utilisation de cette classe dans une application de production en l’absence de toute circonstance.</span><span class="sxs-lookup"><span data-stu-id="0e5ac-109">Microsoft does not support the use of this class in a production application under any circumstance.</span></span>

## <a name="requirements"></a><span data-ttu-id="0e5ac-110">Spécifications</span><span class="sxs-lookup"><span data-stu-id="0e5ac-110">Requirements</span></span>

<span data-ttu-id="0e5ac-111">**Espace de noms :** <xref:System.Net></span><span class="sxs-lookup"><span data-stu-id="0e5ac-111">**Namespace:** <xref:System.Net></span></span>

<span data-ttu-id="0e5ac-112">**Assembly :** Système (en System.dll)</span><span class="sxs-lookup"><span data-stu-id="0e5ac-112">**Assembly:** System (in System.dll)</span></span>

<span data-ttu-id="0e5ac-113">**Versions de .NET Framework :** Disponible depuis 2,0.</span><span class="sxs-lookup"><span data-stu-id="0e5ac-113">**.NET Framework versions:** Available since 2.0.</span></span>
