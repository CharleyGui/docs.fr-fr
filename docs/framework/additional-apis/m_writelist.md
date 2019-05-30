---
title: Champ de Connection.m_WriteList
ms.date: 05/01/2017
topic_type:
- apiref
api_name:
- System.Net.Connection.m_WriteList
api_location:
- System.dll
api_type:
- Assembly
ms.assetid: 235503c1-1d01-4f59-895f-ae2cf15b3345
author: rpetrusha
ms.author: mairaw
ms.openlocfilehash: d138e0490e849ff26f540077ec7d23ae42737606
ms.sourcegitcommit: 621a5f6df00152006160987395b93b5b55f7ffcd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66300909"
---
# <a name="connectionmwritelist-field"></a><span data-ttu-id="00db7-102">Connection.m\_WriteList champ</span><span class="sxs-lookup"><span data-stu-id="00db7-102">Connection.m\_WriteList Field</span></span>

<span data-ttu-id="00db7-103">`Connection.m_WriteList` est un <xref:System.Collections.ArrayList> de <xref:System.Net.HttpWebRequest> les objets qui sont la file d’attente d’être envoyés via HTTP.</span><span class="sxs-lookup"><span data-stu-id="00db7-103">`Connection.m_WriteList` is an <xref:System.Collections.ArrayList> of <xref:System.Net.HttpWebRequest> objects that are queued up to be sent over HTTP.</span></span>

## <a name="syntax"></a><span data-ttu-id="00db7-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="00db7-104">Syntax</span></span>
  
```csharp  
private ArrayList m_WriteList
```

> [!WARNING]
> <span data-ttu-id="00db7-105">Le `Connection.m_WriteList` champ est privé et n’est pas destiné à être utilisé directement dans votre code.</span><span class="sxs-lookup"><span data-stu-id="00db7-105">The `Connection.m_WriteList` field is private and is not meant to be used directly in your code.</span></span>
> 
> <span data-ttu-id="00db7-106">Microsoft ne prend pas en charge l’utilisation de ce champ dans une application de production en toute circonstance.</span><span class="sxs-lookup"><span data-stu-id="00db7-106">Microsoft does not support the use of this field in a production application under any circumstance.</span></span>

## <a name="requirements"></a><span data-ttu-id="00db7-107">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="00db7-107">Requirements</span></span>

<span data-ttu-id="00db7-108">**Espace de noms :** <xref:System.Net></span><span class="sxs-lookup"><span data-stu-id="00db7-108">**Namespace:** <xref:System.Net></span></span>

<span data-ttu-id="00db7-109">**Assembly :** Système (dans System.dll)</span><span class="sxs-lookup"><span data-stu-id="00db7-109">**Assembly:** System (in System.dll)</span></span>

<span data-ttu-id="00db7-110">**Versions du .NET framework :** Disponible à partir de 2.0.</span><span class="sxs-lookup"><span data-stu-id="00db7-110">**.NET Framework versions:** Available since 2.0.</span></span>
