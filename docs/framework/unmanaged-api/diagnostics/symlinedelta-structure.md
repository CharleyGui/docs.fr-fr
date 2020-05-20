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
ms.openlocfilehash: fb3b89d25b4c2e23c3980b167db4279246c4d27b
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83609298"
---
# <a name="symlinedelta-structure"></a><span data-ttu-id="acde9-102">SYMLINEDELTA, structure</span><span class="sxs-lookup"><span data-stu-id="acde9-102">SYMLINEDELTA Structure</span></span>
<span data-ttu-id="acde9-103">Fournit des informations au gestionnaire de symboles sur les méthodes qui ont été déplacées suite à des modifications.</span><span class="sxs-lookup"><span data-stu-id="acde9-103">Provides information to the symbol handler about methods that were moved as a result of edits.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="acde9-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="acde9-104">Syntax</span></span>  
  
```cpp  
typedef struct _SYMLINEDELTA  
    {  
        mdMethodDef  mdMethod;  
        INT32        delta;  
    } SYMLINEDELTA;  
```  
  
## <a name="members"></a><span data-ttu-id="acde9-105">Membres</span><span class="sxs-lookup"><span data-stu-id="acde9-105">Members</span></span>  
  
|<span data-ttu-id="acde9-106">Membre</span><span class="sxs-lookup"><span data-stu-id="acde9-106">Member</span></span>|<span data-ttu-id="acde9-107">Description</span><span class="sxs-lookup"><span data-stu-id="acde9-107">Description</span></span>|  
|------------|-----------------|  
|`mdMethod`|<span data-ttu-id="acde9-108">Jeton de métadonnées de la méthode.</span><span class="sxs-lookup"><span data-stu-id="acde9-108">The method's metadata token.</span></span>|  
|`delta`|<span data-ttu-id="acde9-109">Nombre de lignes dans lesquelles la méthode a été déplacée.</span><span class="sxs-lookup"><span data-stu-id="acde9-109">The number of lines the method was moved.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="acde9-110">Conditions requises</span><span class="sxs-lookup"><span data-stu-id="acde9-110">Requirements</span></span>  
 <span data-ttu-id="acde9-111">**En-tête :** CorSym. idl</span><span class="sxs-lookup"><span data-stu-id="acde9-111">**Header:** CorSym.idl</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="acde9-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="acde9-112">See also</span></span>

- [<span data-ttu-id="acde9-113">Structures du magasin de symboles de diagnostics</span><span class="sxs-lookup"><span data-stu-id="acde9-113">Diagnostics Symbol Store Structures</span></span>](diagnostics-symbol-store-structures.md)
