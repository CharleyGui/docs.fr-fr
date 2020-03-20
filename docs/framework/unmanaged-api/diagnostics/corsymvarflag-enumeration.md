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
ms.openlocfilehash: 21e92d8f2fb80c4c41d516ef281bf4fc8a75f4e1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176641"
---
# <a name="corsymvarflag-enumeration"></a><span data-ttu-id="0309c-102">CorSymVarFlag, énumération</span><span class="sxs-lookup"><span data-stu-id="0309c-102">CorSymVarFlag Enumeration</span></span>
<span data-ttu-id="0309c-103">Indique si une variable est générée par le compilateur.</span><span class="sxs-lookup"><span data-stu-id="0309c-103">Indicates whether a variable is compiler-generated.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0309c-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0309c-104">Syntax</span></span>  
  
```cpp  
typedef enum CorSymVarFlag
{  
    VAR_IS_COMP_GEN = 1  
} CorSymVarFlag;  
```  
  
## <a name="members"></a><span data-ttu-id="0309c-105">Membres</span><span class="sxs-lookup"><span data-stu-id="0309c-105">Members</span></span>  
  
|<span data-ttu-id="0309c-106">Membre</span><span class="sxs-lookup"><span data-stu-id="0309c-106">Member</span></span>|<span data-ttu-id="0309c-107">Description</span><span class="sxs-lookup"><span data-stu-id="0309c-107">Description</span></span>|  
|------------|-----------------|  
|`VAR_IS_COMP_GEN`|<span data-ttu-id="0309c-108">Indique que la variable donnée est générée par le compilateur.</span><span class="sxs-lookup"><span data-stu-id="0309c-108">Indicates that the given variable is compiler-generated.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="0309c-109">Spécifications</span><span class="sxs-lookup"><span data-stu-id="0309c-109">Requirements</span></span>  
 <span data-ttu-id="0309c-110">**En-tête:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="0309c-110">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0309c-111">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="0309c-111">See also</span></span>

- [<span data-ttu-id="0309c-112">Énumérations du magasin de symboles de diagnostics</span><span class="sxs-lookup"><span data-stu-id="0309c-112">Diagnostics Symbol Store Enumerations</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-enumerations.md)
