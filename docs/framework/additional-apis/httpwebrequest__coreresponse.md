---
title: HttpWebRequest. _CoreResponse Field
ms.date: 01/29/2018
topic_type:
- apiref
api_name:
- System.Net.HttpWebRequest._CoreResponse
api_location:
- System.dll
api_type:
- Assembly
author: stevewhims
ms.openlocfilehash: d16936f6984e73a886f5f48e05b53501ced63c1b
ms.sourcegitcommit: 9a97c76e141333394676bc5d264c6624b6f45bcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/08/2020
ms.locfileid: "75740446"
---
# <a name="httpwebrequest_coreresponse-field"></a><span data-ttu-id="32a71-102">HttpWebRequest.\_champ CoreResponse</span><span class="sxs-lookup"><span data-stu-id="32a71-102">HttpWebRequest.\_CoreResponse Field</span></span>

<span data-ttu-id="32a71-103">`HttpWebRequest._CoreResponse` est un objet ( [CoreResponseData](coreresponsedata.md) ou <xref:System.Exception>) qui contient le résultat de l’analyse de réponse http.</span><span class="sxs-lookup"><span data-stu-id="32a71-103">`HttpWebRequest._CoreResponse` is an object (either a [CoreResponseData](coreresponsedata.md) or an <xref:System.Exception>) containing the result of HTTP response parsing.</span></span>

## <a name="syntax"></a><span data-ttu-id="32a71-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="32a71-104">Syntax</span></span>
  
```csharp
private object _CoreResponse
```

> [!WARNING]
> <span data-ttu-id="32a71-105">Cette API n’est pas destinée à être utilisée directement dans votre code.</span><span class="sxs-lookup"><span data-stu-id="32a71-105">This API is not meant to be used directly in your code.</span></span> <span data-ttu-id="32a71-106">Au lieu de cela, vous devez utiliser un <xref:System.Diagnostics.DiagnosticSource> pour raccorder du code réseau.</span><span class="sxs-lookup"><span data-stu-id="32a71-106">Instead, you should use a <xref:System.Diagnostics.DiagnosticSource> to hook networking code.</span></span> <span data-ttu-id="32a71-107">Consultez le [Guide de l’utilisateur DiagnosticSource](https://github.com/dotnet/runtime/blob/master/src/libraries/System.Diagnostics.DiagnosticSource/src/DiagnosticSourceUsersGuide.md).</span><span class="sxs-lookup"><span data-stu-id="32a71-107">See [DiagnosticSource User's Guide](https://github.com/dotnet/runtime/blob/master/src/libraries/System.Diagnostics.DiagnosticSource/src/DiagnosticSourceUsersGuide.md).</span></span>
> 
> <span data-ttu-id="32a71-108">Microsoft ne prend pas en charge l’utilisation de cette classe dans une application de production en l’absence de toute circonstance.</span><span class="sxs-lookup"><span data-stu-id="32a71-108">Microsoft does not support the use of this class in a production application under any circumstance.</span></span>

## <a name="requirements"></a><span data-ttu-id="32a71-109">Configuration requise pour</span><span class="sxs-lookup"><span data-stu-id="32a71-109">Requirements</span></span>

<span data-ttu-id="32a71-110">**Espace de noms :** <xref:System.Net></span><span class="sxs-lookup"><span data-stu-id="32a71-110">**Namespace:** <xref:System.Net></span></span>

<span data-ttu-id="32a71-111">**Assembly :** Système (dans System. dll)</span><span class="sxs-lookup"><span data-stu-id="32a71-111">**Assembly:** System (in System.dll)</span></span>

<span data-ttu-id="32a71-112">**Versions de .NET Framework :** Disponible depuis 2,0.</span><span class="sxs-lookup"><span data-stu-id="32a71-112">**.NET Framework versions:** Available since 2.0.</span></span>
