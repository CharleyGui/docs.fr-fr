---
title: ICorDebugILFrame, interface
ms.date: 03/30/2017
api_name:
- ICorDebugILFrame
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugILFrame
helpviewer_keywords:
- ICorDebugILFrame interface [.NET Framework debugging]
ms.assetid: d5cf5056-da4d-4629-914d-afe42a5393df
topic_type:
- apiref
ms.openlocfilehash: 4f34fdf9a0eeb47e027cc874afee5bd04f5bd9bc
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95712389"
---
# <a name="icordebugilframe-interface"></a><span data-ttu-id="e391d-102">ICorDebugILFrame, interface</span><span class="sxs-lookup"><span data-stu-id="e391d-102">ICorDebugILFrame Interface</span></span>

<span data-ttu-id="e391d-103">Représente un frame de pile de code MSIL (Microsoft Intermediate Language).</span><span class="sxs-lookup"><span data-stu-id="e391d-103">Represents a stack frame of Microsoft intermediate language (MSIL) code.</span></span> <span data-ttu-id="e391d-104">Cette interface est une sous-classe de l’interface ICorDebugFrame.</span><span class="sxs-lookup"><span data-stu-id="e391d-104">This interface is a subclass of the ICorDebugFrame interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="e391d-105">Méthodes</span><span class="sxs-lookup"><span data-stu-id="e391d-105">Methods</span></span>  
  
|<span data-ttu-id="e391d-106">Méthode</span><span class="sxs-lookup"><span data-stu-id="e391d-106">Method</span></span>|<span data-ttu-id="e391d-107">Description</span><span class="sxs-lookup"><span data-stu-id="e391d-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="e391d-108">CanSetIP, méthode</span><span class="sxs-lookup"><span data-stu-id="e391d-108">CanSetIP Method</span></span>](icordebugilframe-cansetip-method.md)|<span data-ttu-id="e391d-109">Obtient une valeur qui indique s’il est possible de définir en toute sécurité le pointeur d’instruction à l’emplacement d’offset spécifié.</span><span class="sxs-lookup"><span data-stu-id="e391d-109">Gets a value that indicates whether it is safe to set the instruction pointer to the specified offset location.</span></span>|  
|[<span data-ttu-id="e391d-110">EnumerateArguments, méthode</span><span class="sxs-lookup"><span data-stu-id="e391d-110">EnumerateArguments Method</span></span>](icordebugilframe-enumeratearguments-method.md)|<span data-ttu-id="e391d-111">Obtient un énumérateur pour les arguments dans ce frame.</span><span class="sxs-lookup"><span data-stu-id="e391d-111">Gets an enumerator for the arguments in this frame.</span></span>|  
|[<span data-ttu-id="e391d-112">EnumerateLocalVariables, méthode</span><span class="sxs-lookup"><span data-stu-id="e391d-112">EnumerateLocalVariables Method</span></span>](icordebugilframe-enumeratelocalvariables-method.md)|<span data-ttu-id="e391d-113">Obtient un énumérateur pour les variables locales dans ce frame.</span><span class="sxs-lookup"><span data-stu-id="e391d-113">Gets an enumerator for the local variables in this frame.</span></span>|  
|[<span data-ttu-id="e391d-114">GetArgument, méthode</span><span class="sxs-lookup"><span data-stu-id="e391d-114">GetArgument Method</span></span>](icordebugilframe-getargument-method.md)|<span data-ttu-id="e391d-115">Obtient la valeur de l’argument spécifié dans ce frame de pile MSIL.</span><span class="sxs-lookup"><span data-stu-id="e391d-115">Gets the value of the specified argument in this MSIL stack frame.</span></span>|  
|[<span data-ttu-id="e391d-116">GetIP, méthode</span><span class="sxs-lookup"><span data-stu-id="e391d-116">GetIP Method</span></span>](icordebugilframe-getip-method.md)|<span data-ttu-id="e391d-117">Obtient la valeur du pointeur d’instruction et une valeur de combinaison au niveau du bit qui décrit comment la valeur du pointeur d’instruction a été obtenue.</span><span class="sxs-lookup"><span data-stu-id="e391d-117">Gets the value of the instruction pointer and a bitwise combination value that describes how the value of the instruction pointer was obtained.</span></span>|  
|[<span data-ttu-id="e391d-118">GetLocalVariable, méthode</span><span class="sxs-lookup"><span data-stu-id="e391d-118">GetLocalVariable Method</span></span>](icordebugilframe-getlocalvariable-method.md)|<span data-ttu-id="e391d-119">Obtient la valeur de la variable locale spécifiée dans ce frame de pile MSIL.</span><span class="sxs-lookup"><span data-stu-id="e391d-119">Gets the value of the specified local variable in this MSIL stack frame.</span></span>|  
|[<span data-ttu-id="e391d-120">GetStackDepth, méthode</span><span class="sxs-lookup"><span data-stu-id="e391d-120">GetStackDepth Method</span></span>](icordebugilframe-getstackdepth-method.md)|<span data-ttu-id="e391d-121">Non implémenté.</span><span class="sxs-lookup"><span data-stu-id="e391d-121">Not implemented.</span></span>|  
|[<span data-ttu-id="e391d-122">GetStackValue, méthode</span><span class="sxs-lookup"><span data-stu-id="e391d-122">GetStackValue Method</span></span>](icordebugilframe-getstackvalue-method.md)|<span data-ttu-id="e391d-123">Non implémenté.</span><span class="sxs-lookup"><span data-stu-id="e391d-123">Not implemented.</span></span>|  
|[<span data-ttu-id="e391d-124">SetIP, méthode</span><span class="sxs-lookup"><span data-stu-id="e391d-124">SetIP Method</span></span>](icordebugilframe-setip-method.md)|<span data-ttu-id="e391d-125">Définit le pointeur d’instruction à l’emplacement d’offset spécifié dans le code MSIL.</span><span class="sxs-lookup"><span data-stu-id="e391d-125">Sets the instruction pointer to the specified offset location in the MSIL code.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e391d-126">Remarques</span><span class="sxs-lookup"><span data-stu-id="e391d-126">Remarks</span></span>  

 <span data-ttu-id="e391d-127">L' `ICorDebugILFrame` interface est une interface ICorDebugFrame spécialisée.</span><span class="sxs-lookup"><span data-stu-id="e391d-127">The `ICorDebugILFrame` interface is a specialized ICorDebugFrame interface.</span></span> <span data-ttu-id="e391d-128">Il est utilisé pour les frames de code MSIL ou pour les frames compilés juste-à-temps (JIT).</span><span class="sxs-lookup"><span data-stu-id="e391d-128">It is used either for MSIL code frames or for just-in-time (JIT) compiled frames.</span></span> <span data-ttu-id="e391d-129">Les frames compilés juste-à-temps implémentent à la fois l’interface `ICorDebugILFrame` et l’interface ICorDebugNativeFrame.</span><span class="sxs-lookup"><span data-stu-id="e391d-129">The JIT-compiled frames implement both the `ICorDebugILFrame` interface and the ICorDebugNativeFrame interface.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="e391d-130">Cette interface ne prend pas en charge l'appel à distance, que ce soit entre ordinateurs ou entre processus.</span><span class="sxs-lookup"><span data-stu-id="e391d-130">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e391d-131">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="e391d-131">Requirements</span></span>  

 <span data-ttu-id="e391d-132">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e391d-132">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e391d-133">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="e391d-133">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e391d-134">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e391d-134">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e391d-135">**Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e391d-135">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e391d-136">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e391d-136">See also</span></span>

- [<span data-ttu-id="e391d-137">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="e391d-137">Debugging Interfaces</span></span>](debugging-interfaces.md)
