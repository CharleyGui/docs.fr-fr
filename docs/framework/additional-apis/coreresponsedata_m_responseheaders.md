---
title: Champ CoreResponseData. m_ResponseHeaders
ms.date: 01/29/2018
topic_type:
- apiref
api_name:
- System.Net.CoreResponseData.m_ResponseHeaders
api_location:
- System.dll
api_type:
- Assembly
author: stevewhims
ms.openlocfilehash: df0b592a5f85d4c99dee4ecb60963f4abb560a13
ms.sourcegitcommit: 9a97c76e141333394676bc5d264c6624b6f45bcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/08/2020
ms.locfileid: "75741004"
---
# <a name="coreresponsedatam_responseheaders-field"></a><span data-ttu-id="ebc2d-102">CoreResponseData. m\_champ ResponseHeaders</span><span class="sxs-lookup"><span data-stu-id="ebc2d-102">CoreResponseData.m\_ResponseHeaders Field</span></span>

<span data-ttu-id="ebc2d-103">`CoreResponseData.m_ResponseHeaders` est un <xref:System.Net.WebHeaderCollection> d’en-têtes associés à la réponse du serveur.</span><span class="sxs-lookup"><span data-stu-id="ebc2d-103">`CoreResponseData.m_ResponseHeaders` is a <xref:System.Net.WebHeaderCollection> of headers associated with the server response.</span></span>

## <a name="syntax"></a><span data-ttu-id="ebc2d-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ebc2d-104">Syntax</span></span>
  
```csharp
public WebHeaderCollection m_ResponseHeaders
```

> [!WARNING]
> <span data-ttu-id="ebc2d-105">Cette API n’est pas destinée à être utilisée directement dans votre code.</span><span class="sxs-lookup"><span data-stu-id="ebc2d-105">This API is not meant to be used directly in your code.</span></span> <span data-ttu-id="ebc2d-106">Au lieu de cela, vous devez utiliser un <xref:System.Diagnostics.DiagnosticSource> pour raccorder du code réseau.</span><span class="sxs-lookup"><span data-stu-id="ebc2d-106">Instead, you should use a <xref:System.Diagnostics.DiagnosticSource> to hook networking code.</span></span> <span data-ttu-id="ebc2d-107">Consultez le [Guide de l’utilisateur DiagnosticSource](https://github.com/dotnet/runtime/blob/master/src/libraries/System.Diagnostics.DiagnosticSource/src/DiagnosticSourceUsersGuide.md).</span><span class="sxs-lookup"><span data-stu-id="ebc2d-107">See [DiagnosticSource User's Guide](https://github.com/dotnet/runtime/blob/master/src/libraries/System.Diagnostics.DiagnosticSource/src/DiagnosticSourceUsersGuide.md).</span></span>
> 
> <span data-ttu-id="ebc2d-108">Microsoft ne prend pas en charge l’utilisation de cette classe dans une application de production en l’absence de toute circonstance.</span><span class="sxs-lookup"><span data-stu-id="ebc2d-108">Microsoft does not support the use of this class in a production application under any circumstance.</span></span>

## <a name="requirements"></a><span data-ttu-id="ebc2d-109">Configuration requise pour</span><span class="sxs-lookup"><span data-stu-id="ebc2d-109">Requirements</span></span>

<span data-ttu-id="ebc2d-110">**Espace de noms :** <xref:System.Net></span><span class="sxs-lookup"><span data-stu-id="ebc2d-110">**Namespace:** <xref:System.Net></span></span>

<span data-ttu-id="ebc2d-111">**Assembly :** Système (dans System. dll)</span><span class="sxs-lookup"><span data-stu-id="ebc2d-111">**Assembly:** System (in System.dll)</span></span>

<span data-ttu-id="ebc2d-112">**Versions de .NET Framework :** Disponible depuis 2,0.</span><span class="sxs-lookup"><span data-stu-id="ebc2d-112">**.NET Framework versions:** Available since 2.0.</span></span>
