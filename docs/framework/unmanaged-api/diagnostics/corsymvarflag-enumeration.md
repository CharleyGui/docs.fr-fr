---
title: CorSymVarFlag, énumération
ms.date: 03/30/2017
api_name:
- CorSymVarFlag
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorSymVarFlag
helpviewer_keywords:
- CorSymVarFlag enumeration [.NET Framework debugging]
ms.assetid: c3f7d307-4047-4f9a-be8c-f152fca42fd0
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: e5b387ee7fd4cc0088c90d2b8278fbf18bb36f51
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67755682"
---
# <a name="corsymvarflag-enumeration"></a><span data-ttu-id="fd2ba-102">CorSymVarFlag, énumération</span><span class="sxs-lookup"><span data-stu-id="fd2ba-102">CorSymVarFlag Enumeration</span></span>
<span data-ttu-id="fd2ba-103">Indique si une variable est générée par le compilateur.</span><span class="sxs-lookup"><span data-stu-id="fd2ba-103">Indicates whether a variable is compiler-generated.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fd2ba-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="fd2ba-104">Syntax</span></span>  
  
```cpp  
typedef enum CorSymVarFlag   
{  
    VAR_IS_COMP_GEN = 1  
} CorSymVarFlag;  
```  
  
## <a name="members"></a><span data-ttu-id="fd2ba-105">Membres</span><span class="sxs-lookup"><span data-stu-id="fd2ba-105">Members</span></span>  
  
|<span data-ttu-id="fd2ba-106">Membre</span><span class="sxs-lookup"><span data-stu-id="fd2ba-106">Member</span></span>|<span data-ttu-id="fd2ba-107">Description</span><span class="sxs-lookup"><span data-stu-id="fd2ba-107">Description</span></span>|  
|------------|-----------------|  
|`VAR_IS_COMP_GEN`|<span data-ttu-id="fd2ba-108">Indique que la variable donnée est généré par le compilateur.</span><span class="sxs-lookup"><span data-stu-id="fd2ba-108">Indicates that the given variable is compiler-generated.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="fd2ba-109">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="fd2ba-109">Requirements</span></span>  
 <span data-ttu-id="fd2ba-110">**En-tête :** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="fd2ba-110">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fd2ba-111">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="fd2ba-111">See also</span></span>

- [<span data-ttu-id="fd2ba-112">Énumérations du magasin de symboles de diagnostics</span><span class="sxs-lookup"><span data-stu-id="fd2ba-112">Diagnostics Symbol Store Enumerations</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-enumerations.md)
