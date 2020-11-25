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
ms.openlocfilehash: ed08d9f818f6fc180dbd655243488bf8a527ae11
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95725285"
---
# <a name="corsymvarflag-enumeration"></a><span data-ttu-id="b00ed-102">CorSymVarFlag, énumération</span><span class="sxs-lookup"><span data-stu-id="b00ed-102">CorSymVarFlag Enumeration</span></span>

<span data-ttu-id="b00ed-103">Indique si une variable est générée par le compilateur.</span><span class="sxs-lookup"><span data-stu-id="b00ed-103">Indicates whether a variable is compiler-generated.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b00ed-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b00ed-104">Syntax</span></span>  
  
```cpp  
typedef enum CorSymVarFlag
{  
    VAR_IS_COMP_GEN = 1  
} CorSymVarFlag;  
```  
  
## <a name="members"></a><span data-ttu-id="b00ed-105">Membres</span><span class="sxs-lookup"><span data-stu-id="b00ed-105">Members</span></span>  
  
|<span data-ttu-id="b00ed-106">Membre</span><span class="sxs-lookup"><span data-stu-id="b00ed-106">Member</span></span>|<span data-ttu-id="b00ed-107">Description</span><span class="sxs-lookup"><span data-stu-id="b00ed-107">Description</span></span>|  
|------------|-----------------|  
|`VAR_IS_COMP_GEN`|<span data-ttu-id="b00ed-108">Indique que la variable donnée est générée par le compilateur.</span><span class="sxs-lookup"><span data-stu-id="b00ed-108">Indicates that the given variable is compiler-generated.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="b00ed-109">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="b00ed-109">Requirements</span></span>  

 <span data-ttu-id="b00ed-110">**En-tête :** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="b00ed-110">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b00ed-111">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b00ed-111">See also</span></span>

- [<span data-ttu-id="b00ed-112">Énumérations du magasin de symboles de diagnostics</span><span class="sxs-lookup"><span data-stu-id="b00ed-112">Diagnostics Symbol Store Enumerations</span></span>](diagnostics-symbol-store-enumerations.md)
