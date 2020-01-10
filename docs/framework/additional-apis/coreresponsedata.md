---
title: CoreResponseData, classe
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
ms.openlocfilehash: fd0ffb982c22b0a8b6cb5dd677faafb9921bf5d9
ms.sourcegitcommit: 9a97c76e141333394676bc5d264c6624b6f45bcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/08/2020
ms.locfileid: "75741021"
---
# <a name="coreresponsedata-class"></a><span data-ttu-id="39e79-102">CoreResponseData, classe</span><span class="sxs-lookup"><span data-stu-id="39e79-102">CoreResponseData Class</span></span>

<span data-ttu-id="39e79-103">La classe `CoreResponseData` représente l’analyse des en-têtes HTTP et du corps de la réponse.</span><span class="sxs-lookup"><span data-stu-id="39e79-103">The `CoreResponseData` class represents the parsing of the HTTP headers and the response body.</span></span>

## <a name="syntax"></a><span data-ttu-id="39e79-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="39e79-104">Syntax</span></span>
  
```csharp
internal class CoreResponseData
```

> [!WARNING]
> <span data-ttu-id="39e79-105">Cette API est interne et n’est pas destinée à être utilisée directement dans votre code.</span><span class="sxs-lookup"><span data-stu-id="39e79-105">This API is internal, and it is not meant to be used directly in your code.</span></span> <span data-ttu-id="39e79-106">Au lieu de cela, vous devez utiliser un <xref:System.Diagnostics.DiagnosticSource> pour raccorder du code réseau.</span><span class="sxs-lookup"><span data-stu-id="39e79-106">Instead, you should use a <xref:System.Diagnostics.DiagnosticSource> to hook networking code.</span></span> <span data-ttu-id="39e79-107">Consultez le [Guide de l’utilisateur DiagnosticSource](https://github.com/dotnet/runtime/blob/master/src/libraries/System.Diagnostics.DiagnosticSource/src/DiagnosticSourceUsersGuide.md).</span><span class="sxs-lookup"><span data-stu-id="39e79-107">See [DiagnosticSource User's Guide](https://github.com/dotnet/runtime/blob/master/src/libraries/System.Diagnostics.DiagnosticSource/src/DiagnosticSourceUsersGuide.md).</span></span>
> 
> <span data-ttu-id="39e79-108">Microsoft ne prend pas en charge l’utilisation de cette classe dans une application de production en l’absence de toute circonstance.</span><span class="sxs-lookup"><span data-stu-id="39e79-108">Microsoft does not support the use of this class in a production application under any circumstance.</span></span>

## <a name="requirements"></a><span data-ttu-id="39e79-109">Configuration requise pour</span><span class="sxs-lookup"><span data-stu-id="39e79-109">Requirements</span></span>

<span data-ttu-id="39e79-110">**Espace de noms :** <xref:System.Net></span><span class="sxs-lookup"><span data-stu-id="39e79-110">**Namespace:** <xref:System.Net></span></span>

<span data-ttu-id="39e79-111">**Assembly :** Système (dans System. dll)</span><span class="sxs-lookup"><span data-stu-id="39e79-111">**Assembly:** System (in System.dll)</span></span>

<span data-ttu-id="39e79-112">**Versions de .NET Framework :** Disponible depuis 2,0.</span><span class="sxs-lookup"><span data-stu-id="39e79-112">**.NET Framework versions:** Available since 2.0.</span></span>
