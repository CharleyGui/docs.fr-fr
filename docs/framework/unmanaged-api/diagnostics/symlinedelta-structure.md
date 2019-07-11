---
title: SYMLINEDELTA, structure
ms.date: 03/30/2017
api_name:
- SYMLINEDELTA
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- SYMLINEDELTA
helpviewer_keywords:
- SYMLINEDELTA structure [.NET Framework debugging]
ms.assetid: 9634e995-d46d-4397-ab66-cc5781d11e4e
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: d98ebed2eb853d5dc8177b0b044bf654c3978494
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67744347"
---
# <a name="symlinedelta-structure"></a><span data-ttu-id="feab6-102">SYMLINEDELTA, structure</span><span class="sxs-lookup"><span data-stu-id="feab6-102">SYMLINEDELTA Structure</span></span>
<span data-ttu-id="feab6-103">Fournit des informations pour le Gestionnaire de symboles sur les méthodes qui ont été déplacées à la suite de modifications.</span><span class="sxs-lookup"><span data-stu-id="feab6-103">Provides information to the symbol handler about methods that were moved as a result of edits.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="feab6-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="feab6-104">Syntax</span></span>  
  
```cpp  
typedef struct _SYMLINEDELTA  
    {  
        mdMethodDef  mdMethod;  
        INT32        delta;  
    } SYMLINEDELTA;  
```  
  
## <a name="members"></a><span data-ttu-id="feab6-105">Membres</span><span class="sxs-lookup"><span data-stu-id="feab6-105">Members</span></span>  
  
|<span data-ttu-id="feab6-106">Membre</span><span class="sxs-lookup"><span data-stu-id="feab6-106">Member</span></span>|<span data-ttu-id="feab6-107">Description</span><span class="sxs-lookup"><span data-stu-id="feab6-107">Description</span></span>|  
|------------|-----------------|  
|`mdMethod`|<span data-ttu-id="feab6-108">Jeton de métadonnées de la méthode.</span><span class="sxs-lookup"><span data-stu-id="feab6-108">The method's metadata token.</span></span>|  
|`delta`|<span data-ttu-id="feab6-109">Le nombre de lignes de que la méthode a été déplacée.</span><span class="sxs-lookup"><span data-stu-id="feab6-109">The number of lines the method was moved.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="feab6-110">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="feab6-110">Requirements</span></span>  
 <span data-ttu-id="feab6-111">**En-tête :** CorSym.idl</span><span class="sxs-lookup"><span data-stu-id="feab6-111">**Header:** CorSym.idl</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="feab6-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="feab6-112">See also</span></span>

- [<span data-ttu-id="feab6-113">Structures du magasin de symboles de diagnostics</span><span class="sxs-lookup"><span data-stu-id="feab6-113">Diagnostics Symbol Store Structures</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-structures.md)
