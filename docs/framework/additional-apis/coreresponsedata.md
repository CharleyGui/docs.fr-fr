---
title: CoreResponseData, classe
description: Comprendre la classe CoreResponseData, qui représente l’analyse des en-têtes HTTP et du corps de la réponse. Il se trouve dans l’espace de noms System.Net dans .NET.
ms.date: 01/29/2018
topic_type:
- apiref
api_name:
- System.Net.CoreResponseData
api_location:
- System.dll
api_type:
- Assembly
author: stevewhims
ms.openlocfilehash: 8248cc20f6528a1c3bc64c9b9339a3a3000d03a0
ms.sourcegitcommit: 45c8eed045779b70a47b23169897459d0323dc89
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/18/2020
ms.locfileid: "84989802"
---
# <a name="coreresponsedata-class"></a><span data-ttu-id="da373-104">CoreResponseData, classe</span><span class="sxs-lookup"><span data-stu-id="da373-104">CoreResponseData Class</span></span>

<span data-ttu-id="da373-105">La `CoreResponseData` classe représente l’analyse des en-têtes HTTP et du corps de la réponse.</span><span class="sxs-lookup"><span data-stu-id="da373-105">The `CoreResponseData` class represents the parsing of the HTTP headers and the response body.</span></span>

## <a name="syntax"></a><span data-ttu-id="da373-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="da373-106">Syntax</span></span>
  
```csharp
internal class CoreResponseData
```

> [!WARNING]
> <span data-ttu-id="da373-107">Cette API est interne et n’est pas destinée à être utilisée directement dans votre code.</span><span class="sxs-lookup"><span data-stu-id="da373-107">This API is internal, and it is not meant to be used directly in your code.</span></span> <span data-ttu-id="da373-108">Au lieu de cela, vous devez utiliser un <xref:System.Diagnostics.DiagnosticSource> pour raccorder du code de mise en réseau.</span><span class="sxs-lookup"><span data-stu-id="da373-108">Instead, you should use a <xref:System.Diagnostics.DiagnosticSource> to hook networking code.</span></span> <span data-ttu-id="da373-109">Consultez le [Guide de l’utilisateur DiagnosticSource](https://github.com/dotnet/runtime/blob/master/src/libraries/System.Diagnostics.DiagnosticSource/src/DiagnosticSourceUsersGuide.md).</span><span class="sxs-lookup"><span data-stu-id="da373-109">See [DiagnosticSource User's Guide](https://github.com/dotnet/runtime/blob/master/src/libraries/System.Diagnostics.DiagnosticSource/src/DiagnosticSourceUsersGuide.md).</span></span>
>
> <span data-ttu-id="da373-110">Microsoft ne prend pas en charge l’utilisation de cette classe dans une application de production en l’absence de toute circonstance.</span><span class="sxs-lookup"><span data-stu-id="da373-110">Microsoft does not support the use of this class in a production application under any circumstance.</span></span>

## <a name="requirements"></a><span data-ttu-id="da373-111">Spécifications</span><span class="sxs-lookup"><span data-stu-id="da373-111">Requirements</span></span>

<span data-ttu-id="da373-112">**Espace de noms :** <xref:System.Net></span><span class="sxs-lookup"><span data-stu-id="da373-112">**Namespace:** <xref:System.Net></span></span>

<span data-ttu-id="da373-113">**Assembly :** Système (en System.dll)</span><span class="sxs-lookup"><span data-stu-id="da373-113">**Assembly:** System (in System.dll)</span></span>

<span data-ttu-id="da373-114">**Versions de .NET Framework :** Disponible depuis 2,0.</span><span class="sxs-lookup"><span data-stu-id="da373-114">**.NET Framework versions:** Available since 2.0.</span></span>
