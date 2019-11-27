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
ms.openlocfilehash: a1e83e4b8cb6603029f3b42b1a3b9ba4810c9039
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74438012"
---
# <a name="symlinedelta-structure"></a><span data-ttu-id="5a8f0-102">SYMLINEDELTA, structure</span><span class="sxs-lookup"><span data-stu-id="5a8f0-102">SYMLINEDELTA Structure</span></span>
<span data-ttu-id="5a8f0-103">Fournit des informations au gestionnaire de symboles sur les méthodes qui ont été déplacées suite à des modifications.</span><span class="sxs-lookup"><span data-stu-id="5a8f0-103">Provides information to the symbol handler about methods that were moved as a result of edits.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5a8f0-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5a8f0-104">Syntax</span></span>  
  
```cpp  
typedef struct _SYMLINEDELTA  
    {  
        mdMethodDef  mdMethod;  
        INT32        delta;  
    } SYMLINEDELTA;  
```  
  
## <a name="members"></a><span data-ttu-id="5a8f0-105">Membres</span><span class="sxs-lookup"><span data-stu-id="5a8f0-105">Members</span></span>  
  
|<span data-ttu-id="5a8f0-106">Membre</span><span class="sxs-lookup"><span data-stu-id="5a8f0-106">Member</span></span>|<span data-ttu-id="5a8f0-107">Description</span><span class="sxs-lookup"><span data-stu-id="5a8f0-107">Description</span></span>|  
|------------|-----------------|  
|`mdMethod`|<span data-ttu-id="5a8f0-108">Jeton de métadonnées de la méthode.</span><span class="sxs-lookup"><span data-stu-id="5a8f0-108">The method's metadata token.</span></span>|  
|`delta`|<span data-ttu-id="5a8f0-109">Nombre de lignes dans lesquelles la méthode a été déplacée.</span><span class="sxs-lookup"><span data-stu-id="5a8f0-109">The number of lines the method was moved.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="5a8f0-110">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="5a8f0-110">Requirements</span></span>  
 <span data-ttu-id="5a8f0-111">**En-tête :** CorSym. idl</span><span class="sxs-lookup"><span data-stu-id="5a8f0-111">**Header:** CorSym.idl</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5a8f0-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="5a8f0-112">See also</span></span>

- [<span data-ttu-id="5a8f0-113">Structures du magasin de symboles de diagnostics</span><span class="sxs-lookup"><span data-stu-id="5a8f0-113">Diagnostics Symbol Store Structures</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-structures.md)
