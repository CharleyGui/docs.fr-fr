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
ms.openlocfilehash: 98c6ed4657dc69554a9fcca27145f65c621492f4
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95683729"
---
# <a name="createalink-function"></a><span data-ttu-id="74b9a-102">CreateALink, fonction</span><span class="sxs-lookup"><span data-stu-id="74b9a-102">CreateALink Function</span></span>

<span data-ttu-id="74b9a-103">Crée une instance de l’Assembly Linker et définit un pointeur vers l’interface spécifiée.</span><span class="sxs-lookup"><span data-stu-id="74b9a-103">Creates an instance of the Assembly Linker and sets a pointer to the specified interface.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="74b9a-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="74b9a-104">Syntax</span></span>  
  
```cpp  
HRESULT CreateALink (  
   REFIID riid,  
   IUnknown **ppInterface  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="74b9a-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="74b9a-105">Parameters</span></span>  
  
|<span data-ttu-id="74b9a-106">Paramètre</span><span class="sxs-lookup"><span data-stu-id="74b9a-106">Parameter</span></span>|<span data-ttu-id="74b9a-107">Description</span><span class="sxs-lookup"><span data-stu-id="74b9a-107">Description</span></span>|  
|---------------|-----------------|  
|`riid`|<span data-ttu-id="74b9a-108">Nom physique de l’une des interfaces de l’éditeur de liens de l’assembly.</span><span class="sxs-lookup"><span data-stu-id="74b9a-108">The physical name of one of the Assembly Linker interfaces.</span></span>|  
|`ppInterface`|<span data-ttu-id="74b9a-109">Emplacement qui, en cas de réussite de l’opération, contient un pointeur vers l' `riid` interface.</span><span class="sxs-lookup"><span data-stu-id="74b9a-109">The location that on successful completion contains a pointer to the `riid` interface.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="74b9a-110">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="74b9a-110">Requirements</span></span>  

 <span data-ttu-id="74b9a-111">**Bibliothèque**: alink.dll</span><span class="sxs-lookup"><span data-stu-id="74b9a-111">**Library**: alink.dll</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="74b9a-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="74b9a-112">See also</span></span>

- [<span data-ttu-id="74b9a-113">Al.exe (Assembly Linker)</span><span class="sxs-lookup"><span data-stu-id="74b9a-113">Al.exe (Assembly Linker)</span></span>](../../tools/al-exe-assembly-linker.md)
