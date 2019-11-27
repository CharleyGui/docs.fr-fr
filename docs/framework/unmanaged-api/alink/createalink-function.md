---
title: CreateALink, fonction
ms.date: 03/30/2017
api_name:
- CreateALink
api_location:
- alink.dll
api_type:
- DLLExport
f1_keywords:
- CreateALink
helpviewer_keywords:
- CreateALink function
- Alink API, CreateALink function
ms.assetid: fc73bcb9-6af6-44d8-bc39-2f4400325dae
topic_type:
- apiref
ms.openlocfilehash: 9165a4db7e65fb0f409a902b06d32e9c2988aa69
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74446556"
---
# <a name="createalink-function"></a><span data-ttu-id="43a17-102">CreateALink, fonction</span><span class="sxs-lookup"><span data-stu-id="43a17-102">CreateALink Function</span></span>
<span data-ttu-id="43a17-103">Crée une instance de l’Assembly Linker et définit un pointeur vers l’interface spécifiée.</span><span class="sxs-lookup"><span data-stu-id="43a17-103">Creates an instance of the Assembly Linker and sets a pointer to the specified interface.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="43a17-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="43a17-104">Syntax</span></span>  
  
```cpp  
HRESULT CreateALink (  
   REFIID riid,  
   IUnknown **ppInterface  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="43a17-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="43a17-105">Parameters</span></span>  
  
|<span data-ttu-id="43a17-106">Paramètre</span><span class="sxs-lookup"><span data-stu-id="43a17-106">Parameter</span></span>|<span data-ttu-id="43a17-107">Description</span><span class="sxs-lookup"><span data-stu-id="43a17-107">Description</span></span>|  
|---------------|-----------------|  
|`riid`|<span data-ttu-id="43a17-108">Nom physique de l’une des interfaces de l’éditeur de liens de l’assembly.</span><span class="sxs-lookup"><span data-stu-id="43a17-108">The physical name of one of the Assembly Linker interfaces.</span></span>|  
|`ppInterface`|<span data-ttu-id="43a17-109">Emplacement qui, en cas de réussite de l’opération, contient un pointeur vers l’interface `riid`.</span><span class="sxs-lookup"><span data-stu-id="43a17-109">The location that on successful completion contains a pointer to the `riid` interface.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="43a17-110">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="43a17-110">Requirements</span></span>  
 <span data-ttu-id="43a17-111">**Bibliothèque**: ALink. dll</span><span class="sxs-lookup"><span data-stu-id="43a17-111">**Library**: alink.dll</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="43a17-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="43a17-112">See also</span></span>

- [<span data-ttu-id="43a17-113">Al.exe (Assembly Linker)</span><span class="sxs-lookup"><span data-stu-id="43a17-113">Al.exe (Assembly Linker)</span></span>](../../tools/al-exe-assembly-linker.md)
