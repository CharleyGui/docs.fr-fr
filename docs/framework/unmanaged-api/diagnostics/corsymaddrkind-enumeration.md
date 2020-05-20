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
ms.openlocfilehash: 5991b0abaedabe2337cd754c7bd19f96c5e9b685
ms.sourcegitcommit: 9a4488a3625866335e83a20da5e9c5286b1f034c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/15/2020
ms.locfileid: "83420615"
---
# <a name="corsymaddrkind-enumeration"></a><span data-ttu-id="e02f1-102">CorSymAddrKind, énumération</span><span class="sxs-lookup"><span data-stu-id="e02f1-102">CorSymAddrKind Enumeration</span></span>
<span data-ttu-id="e02f1-103">Indique le type d’adresse mémoire.</span><span class="sxs-lookup"><span data-stu-id="e02f1-103">Indicates the type of memory address.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e02f1-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e02f1-104">Syntax</span></span>  
  
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
  
## <a name="members"></a><span data-ttu-id="e02f1-105">Membres</span><span class="sxs-lookup"><span data-stu-id="e02f1-105">Members</span></span>  
  
|<span data-ttu-id="e02f1-106">Membre</span><span class="sxs-lookup"><span data-stu-id="e02f1-106">Member</span></span>|<span data-ttu-id="e02f1-107">Description</span><span class="sxs-lookup"><span data-stu-id="e02f1-107">Description</span></span>|  
|------------|-----------------|  
|`ADDR_IL_OFFSET`|<span data-ttu-id="e02f1-108">Indique une variable locale MSIL (Microsoft Intermediate Language) ou un index de paramètre.</span><span class="sxs-lookup"><span data-stu-id="e02f1-108">Indicates a Microsoft intermediate language (MSIL) local variable or parameter index.</span></span>|  
|`ADDR_NATIVE_RVA`|<span data-ttu-id="e02f1-109">Indique une adresse virtuelle relative dans un module.</span><span class="sxs-lookup"><span data-stu-id="e02f1-109">Indicates a relative virtual address into a module.</span></span>|  
|`ADDR_NATIVE_REGISTER`|<span data-ttu-id="e02f1-110">Indique un registre de l’UC.</span><span class="sxs-lookup"><span data-stu-id="e02f1-110">Indicates a CPU register.</span></span>|  
|`ADDR_NATIVE_REGREL`|<span data-ttu-id="e02f1-111">Indique que la première adresse est un registre et que la deuxième adresse est un décalage.</span><span class="sxs-lookup"><span data-stu-id="e02f1-111">Indicates that the first address is a register and the second address is an offset.</span></span>|  
|`ADDR_NATIVE_OFFSET`|<span data-ttu-id="e02f1-112">Indique un offset à partir d’une adresse de base.</span><span class="sxs-lookup"><span data-stu-id="e02f1-112">Indicates an offset from a base address.</span></span>|  
|`ADDR_NATIVE_REGREG`|<span data-ttu-id="e02f1-113">Indique que la première adresse est la partie basse d’un registre et que la deuxième adresse est la partie haute.</span><span class="sxs-lookup"><span data-stu-id="e02f1-113">Indicates that the first address is the low portion of a register, and the second address is the high portion.</span></span>|  
|`ADDR_NATIVE_REGSTK`|<span data-ttu-id="e02f1-114">Indique que la première adresse est la partie basse d’un registre, la deuxième est la partie haute et la troisième est un décalage.</span><span class="sxs-lookup"><span data-stu-id="e02f1-114">Indicates that the first address is the low portion of a register, the second is the high portion, and the third is an offset.</span></span>|  
|`ADDR_NATIVE_STKREG`|<span data-ttu-id="e02f1-115">Indique que la première adresse est un registre, la deuxième est un décalage et la troisième la partie haute du Registre.</span><span class="sxs-lookup"><span data-stu-id="e02f1-115">Indicates that the first address is a register, the second is an offset, and the third is the high portion of the register.</span></span>|  
|`ADDR_BITFIELD`|<span data-ttu-id="e02f1-116">Indique que la première adresse est le début d’un champ et la deuxième adresse la longueur du champ.</span><span class="sxs-lookup"><span data-stu-id="e02f1-116">Indicates that the first address is the start of a field and the second address is the field length.</span></span>|  
|`ADDR_NATIVE_ISECTOFFSET`|<span data-ttu-id="e02f1-117">Indique que la première adresse est la section et que la deuxième adresse est un décalage.</span><span class="sxs-lookup"><span data-stu-id="e02f1-117">Indicates that the first address is the section and the second address is an offset.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="e02f1-118">Conditions requises</span><span class="sxs-lookup"><span data-stu-id="e02f1-118">Requirements</span></span>  
 <span data-ttu-id="e02f1-119">**En-tête :** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="e02f1-119">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e02f1-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e02f1-120">See also</span></span>

- [<span data-ttu-id="e02f1-121">Énumérations du magasin de symboles de diagnostics</span><span class="sxs-lookup"><span data-stu-id="e02f1-121">Diagnostics Symbol Store Enumerations</span></span>](diagnostics-symbol-store-enumerations.md)
