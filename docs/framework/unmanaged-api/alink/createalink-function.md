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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 24f7e2d5a547b78ceb4808feaf581c6f49807cf7
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70787616"
---
# <a name="createalink-function"></a><span data-ttu-id="e57db-102">CreateALink, fonction</span><span class="sxs-lookup"><span data-stu-id="e57db-102">CreateALink Function</span></span>
<span data-ttu-id="e57db-103">Crée une instance de l’Assembly Linker et définit un pointeur vers l’interface spécifiée.</span><span class="sxs-lookup"><span data-stu-id="e57db-103">Creates an instance of the Assembly Linker and sets a pointer to the specified interface.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e57db-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e57db-104">Syntax</span></span>  
  
```cpp  
HRESULT CreateALink (  
   REFIID riid,  
   IUnknown **ppInterface  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e57db-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="e57db-105">Parameters</span></span>  
  
|<span data-ttu-id="e57db-106">Paramètre</span><span class="sxs-lookup"><span data-stu-id="e57db-106">Parameter</span></span>|<span data-ttu-id="e57db-107">Description</span><span class="sxs-lookup"><span data-stu-id="e57db-107">Description</span></span>|  
|---------------|-----------------|  
|`riid`|<span data-ttu-id="e57db-108">Nom physique de l’une des interfaces de l’éditeur de liens de l’assembly.</span><span class="sxs-lookup"><span data-stu-id="e57db-108">The physical name of one of the Assembly Linker interfaces.</span></span>|  
|`ppInterface`|<span data-ttu-id="e57db-109">Emplacement qui, en cas de réussite de l’opération, `riid` contient un pointeur vers l’interface.</span><span class="sxs-lookup"><span data-stu-id="e57db-109">The location that on successful completion contains a pointer to the `riid` interface.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="e57db-110">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="e57db-110">Requirements</span></span>  
 <span data-ttu-id="e57db-111">**Bibliothèque**: ALink. dll</span><span class="sxs-lookup"><span data-stu-id="e57db-111">**Library**: alink.dll</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e57db-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e57db-112">See also</span></span>

- [<span data-ttu-id="e57db-113">Al.exe (Assembly Linker)</span><span class="sxs-lookup"><span data-stu-id="e57db-113">Al.exe (Assembly Linker)</span></span>](../../tools/al-exe-assembly-linker.md)
