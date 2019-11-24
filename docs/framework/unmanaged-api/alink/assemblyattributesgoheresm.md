---
title: AssemblyAttributesGoHereSM Class (System.Runtime.CompilerServices)
ms.date: 03/30/2017
api_name:
- System.Runtime.CompilerServices.AssemblyAttributesGoHereSM
api_location:
- mscorlib.dll
api_type:
- Assembly
f1_keywords:
- AssemblyAttributesGoHereSM
helpviewer_keywords:
- AssemblyAttributesGoHereSM type
- Alink API, AssemblyAttributesGoHereSM type
ms.assetid: 4cf9bf39-1527-49e0-a0e9-55e7a018bf66
topic_type:
- apiref
ms.openlocfilehash: 379ba20ebf675bec71e6e5f5bcfc0dc2fbd1f92c
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74446597"
---
# <a name="assemblyattributesgoheresm-class"></a><span data-ttu-id="029c2-102">AssemblyAttributesGoHereSM Class</span><span class="sxs-lookup"><span data-stu-id="029c2-102">AssemblyAttributesGoHereSM Class</span></span>

<span data-ttu-id="029c2-103">Utilisé par ALink en tant qu'espace réservé pour stocker des informations sur les attributs personnalisés.</span><span class="sxs-lookup"><span data-stu-id="029c2-103">Used by ALink as a placeholder to store information about custom attributes.</span></span>

## <a name="syntax"></a><span data-ttu-id="029c2-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="029c2-104">Syntax</span></span>

```csharp
internal sealed class AssemblyAttributesGoHereSM
```

## <a name="remarks"></a><span data-ttu-id="029c2-105">Notes</span><span class="sxs-lookup"><span data-stu-id="029c2-105">Remarks</span></span>

<span data-ttu-id="029c2-106">Les références à ce type peuvent être incorporées dans les netmodules dont les sources contiennent des attributs personnalisés d'assembly.</span><span class="sxs-lookup"><span data-stu-id="029c2-106">References to this type might be embedded inside netmodules whose sources contain assembly custom attributes.</span></span> <span data-ttu-id="029c2-107">Quand vous générez un manifeste d'assembly à partir d'un ou plusieurs netmodules qui contiennent des références à ces types, ALink utilise les informations associées à ces références pour émettre des attributs personnalisés réels.</span><span class="sxs-lookup"><span data-stu-id="029c2-107">When building an assembly manifest from one or more netmodules that contain references to these types, ALink uses information attached to these references to emit real custom attributes.</span></span> <span data-ttu-id="029c2-108">Par conséquent, ce type n'est jamais instancié et ses références sont utilisées uniquement dans le cadre du processus de génération et n'ont aucune utilité dans l'assembly final.</span><span class="sxs-lookup"><span data-stu-id="029c2-108">As such, this type is never instantiated, and references to it are used only as part of the build process and serve no purpose in the final assembly.</span></span>

<span data-ttu-id="029c2-109">Les références à ce type indiquent des attributs personnalisés qui sont liés à la sécurité et qui peuvent être utilisés plusieurs fois.</span><span class="sxs-lookup"><span data-stu-id="029c2-109">References to this type indicate custom attributes that are security related and multiple-use.</span></span>

<span data-ttu-id="029c2-110">These types are marked "internal" within the .NET Framework and are located in the <xref:System.Runtime.CompilerServices> namespace.</span><span class="sxs-lookup"><span data-stu-id="029c2-110">These types are marked "internal" within the .NET Framework and are located in the <xref:System.Runtime.CompilerServices> namespace.</span></span>

## <a name="requirements"></a><span data-ttu-id="029c2-111">spécifications</span><span class="sxs-lookup"><span data-stu-id="029c2-111">Requirements</span></span>

<span data-ttu-id="029c2-112">mscorlib.dll</span><span class="sxs-lookup"><span data-stu-id="029c2-112">mscorlib.dll</span></span>

## <a name="see-also"></a><span data-ttu-id="029c2-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="029c2-113">See also</span></span>

- [<span data-ttu-id="029c2-114">AssemblyAttributesGoHere</span><span class="sxs-lookup"><span data-stu-id="029c2-114">AssemblyAttributesGoHere</span></span>](assemblyattributesgohere.md)
- [<span data-ttu-id="029c2-115">AssemblyAttributesGoHereM</span><span class="sxs-lookup"><span data-stu-id="029c2-115">AssemblyAttributesGoHereM</span></span>](assemblyattributesgoherem.md)
- [<span data-ttu-id="029c2-116">AssemblyAttributesGoHereS</span><span class="sxs-lookup"><span data-stu-id="029c2-116">AssemblyAttributesGoHereS</span></span>](assemblyattributesgoheres.md)
