---
title: HttpWebRequest. _CoreResponse Field
description: En savoir plus sur le champ HttpWebRequest. _CoreResponse dans .NET. Ce champ est un objet CoreResponseData ou exception contenant le résultat de l’analyse de la réponse HTTP.
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
ms.openlocfilehash: 5093ec7ed2c3b94931dcd622ae9ccdb42feffa18
ms.sourcegitcommit: 45c8eed045779b70a47b23169897459d0323dc89
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/18/2020
ms.locfileid: "84989746"
---
# <a name="httpwebrequest_coreresponse-field"></a><span data-ttu-id="056e7-104">HttpWebRequest. \_ Champ CoreResponse</span><span class="sxs-lookup"><span data-stu-id="056e7-104">HttpWebRequest.\_CoreResponse Field</span></span>

<span data-ttu-id="056e7-105">`HttpWebRequest._CoreResponse`est un objet ( [CoreResponseData](coreresponsedata.md) ou <xref:System.Exception> ) qui contient le résultat de l’analyse de la réponse http.</span><span class="sxs-lookup"><span data-stu-id="056e7-105">`HttpWebRequest._CoreResponse` is an object (either a [CoreResponseData](coreresponsedata.md) or an <xref:System.Exception>) containing the result of HTTP response parsing.</span></span>

## <a name="syntax"></a><span data-ttu-id="056e7-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="056e7-106">Syntax</span></span>
  
```csharp
private object _CoreResponse
```

> [!WARNING]
> <span data-ttu-id="056e7-107">Cette API n’est pas destinée à être utilisée directement dans votre code.</span><span class="sxs-lookup"><span data-stu-id="056e7-107">This API is not meant to be used directly in your code.</span></span> <span data-ttu-id="056e7-108">Au lieu de cela, vous devez utiliser un <xref:System.Diagnostics.DiagnosticSource> pour raccorder du code de mise en réseau.</span><span class="sxs-lookup"><span data-stu-id="056e7-108">Instead, you should use a <xref:System.Diagnostics.DiagnosticSource> to hook networking code.</span></span> <span data-ttu-id="056e7-109">Consultez le [Guide de l’utilisateur DiagnosticSource](https://github.com/dotnet/runtime/blob/master/src/libraries/System.Diagnostics.DiagnosticSource/src/DiagnosticSourceUsersGuide.md).</span><span class="sxs-lookup"><span data-stu-id="056e7-109">See [DiagnosticSource User's Guide](https://github.com/dotnet/runtime/blob/master/src/libraries/System.Diagnostics.DiagnosticSource/src/DiagnosticSourceUsersGuide.md).</span></span>
>
> <span data-ttu-id="056e7-110">Microsoft ne prend pas en charge l’utilisation de cette classe dans une application de production en l’absence de toute circonstance.</span><span class="sxs-lookup"><span data-stu-id="056e7-110">Microsoft does not support the use of this class in a production application under any circumstance.</span></span>

## <a name="requirements"></a><span data-ttu-id="056e7-111">Spécifications</span><span class="sxs-lookup"><span data-stu-id="056e7-111">Requirements</span></span>

<span data-ttu-id="056e7-112">**Espace de noms :** <xref:System.Net></span><span class="sxs-lookup"><span data-stu-id="056e7-112">**Namespace:** <xref:System.Net></span></span>

<span data-ttu-id="056e7-113">**Assembly :** Système (en System.dll)</span><span class="sxs-lookup"><span data-stu-id="056e7-113">**Assembly:** System (in System.dll)</span></span>

<span data-ttu-id="056e7-114">**Versions de .NET Framework :** Disponible depuis 2,0.</span><span class="sxs-lookup"><span data-stu-id="056e7-114">**.NET Framework versions:** Available since 2.0.</span></span>
