---
title: CorSymAddrKind, énumération
ms.date: 03/30/2017
api_name:
- CorSymAddrKind
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorSymAddrKind
helpviewer_keywords:
- CorSymAddrKind enumeration [.NET Framework debugging]
ms.assetid: 3ef841c2-cade-42ee-ba34-2ef91d6d0879
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: ba24f5394ef8fb31d8bfa4e74ac59e7bd4af86d8
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67769865"
---
# <a name="corsymaddrkind-enumeration"></a><span data-ttu-id="06304-102">CorSymAddrKind, énumération</span><span class="sxs-lookup"><span data-stu-id="06304-102">CorSymAddrKind Enumeration</span></span>
<span data-ttu-id="06304-103">Indique le type d’adresse de mémoire.</span><span class="sxs-lookup"><span data-stu-id="06304-103">Indicates the type of memory address.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="06304-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="06304-104">Syntax</span></span>  
  
```cpp  
typedef enum CorSymAddrKind  
{  
    ADDR_IL_OFFSET          = 1,  
    ADDR_NATIVE_RVA         = 2,  
    ADDR_NATIVE_REGISTER    = 3,  
    ADDR_NATIVE_REGREL      = 4,  
    ADDR_NATIVE_OFFSET      = 5,  
    ADDR_NATIVE_REGREG      = 6,  
    ADDR_NATIVE_REGSTK      = 7,  
    ADDR_NATIVE_STKREG      = 8,  
    ADDR_BITFIELD           = 9,  
    ADDR_NATIVE_ISECTOFFSET = 10  
} CorSymAddrKind;  
```  
  
## <a name="members"></a><span data-ttu-id="06304-105">Membres</span><span class="sxs-lookup"><span data-stu-id="06304-105">Members</span></span>  
  
|<span data-ttu-id="06304-106">Membre</span><span class="sxs-lookup"><span data-stu-id="06304-106">Member</span></span>|<span data-ttu-id="06304-107">Description</span><span class="sxs-lookup"><span data-stu-id="06304-107">Description</span></span>|  
|------------|-----------------|  
|`ADDR_IL_OFFSET`|<span data-ttu-id="06304-108">Indique un index Microsoft intermediate language (MSIL) local variable ou un paramètre.</span><span class="sxs-lookup"><span data-stu-id="06304-108">Indicates a Microsoft intermediate language (MSIL) local variable or parameter index.</span></span>|  
|`ADDR_NATIVE_RVA`|<span data-ttu-id="06304-109">Indique une adresse virtuelle relative dans un module.</span><span class="sxs-lookup"><span data-stu-id="06304-109">Indicates a relative virtual address into a module.</span></span>|  
|`ADDR_NATIVE_REGISTER`|<span data-ttu-id="06304-110">Indique un Registre du processeur.</span><span class="sxs-lookup"><span data-stu-id="06304-110">Indicates a CPU register.</span></span>|  
|`ADDR_NATIVE_REGREL`|<span data-ttu-id="06304-111">Indique que la première adresse est un Registre et la deuxième adresse est un décalage.</span><span class="sxs-lookup"><span data-stu-id="06304-111">Indicates that the first address is a register and the second address is an offset.</span></span>|  
|`ADDR_NATIVE_OFFSET`|<span data-ttu-id="06304-112">Indique un décalage à partir d’une adresse de base.</span><span class="sxs-lookup"><span data-stu-id="06304-112">Indicates an offset from a base address.</span></span>|  
|`ADDR_NATIVE_REGREG`|<span data-ttu-id="06304-113">Indique que la première adresse est la partie basse d’un Registre, et la deuxième adresse est la partie haute.</span><span class="sxs-lookup"><span data-stu-id="06304-113">Indicates that the first address is the low portion of a register, and the second address is the high portion.</span></span>|  
|`ADDR_NATIVE_REGSTK`|<span data-ttu-id="06304-114">Indique que la première adresse est la partie basse d’un Registre, la seconde est la partie haute, et le troisième est un décalage.</span><span class="sxs-lookup"><span data-stu-id="06304-114">Indicates that the first address is the low portion of a register, the second is the high portion, and the third is an offset.</span></span>|  
|`ADDR_NATIVE_STKREG`|<span data-ttu-id="06304-115">Indique que la première adresse est un Registre, le second est un décalage, et le troisième est la partie haute du Registre.</span><span class="sxs-lookup"><span data-stu-id="06304-115">Indicates that the first address is a register, the second is an offset, and the third is the high portion of the register.</span></span>|  
|`ADDR_BITFIELD`|<span data-ttu-id="06304-116">Indique que la première adresse est le début d’un champ et la deuxième adresse est la longueur de champ.</span><span class="sxs-lookup"><span data-stu-id="06304-116">Indicates that the first address is the start of a field and the second address is the field length.</span></span>|  
|`ADDR_NATIVE_ISECTOFFSET`|<span data-ttu-id="06304-117">Indique que la première adresse est la section et la deuxième adresse est un décalage.</span><span class="sxs-lookup"><span data-stu-id="06304-117">Indicates that the first address is the section and the second address is an offset.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="06304-118">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="06304-118">Requirements</span></span>  
 <span data-ttu-id="06304-119">**En-tête :** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="06304-119">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="06304-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="06304-120">See also</span></span>

- [<span data-ttu-id="06304-121">Énumérations du magasin de symboles de diagnostics</span><span class="sxs-lookup"><span data-stu-id="06304-121">Diagnostics Symbol Store Enumerations</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-enumerations.md)
