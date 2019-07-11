---
title: AssemblyAttributesGoHereS
ms.date: 03/30/2017
api_name:
- System.Runtime.CompilerServices.AssemblyAttributesGoHereS
api_location:
- mscorlib.dll
api_type:
- Assembly
f1_keywords:
- AssemblyAttributesGoHereS
helpviewer_keywords:
- AssemblyAttributesGoHereS type
- Alink API, AssemblyAttributesGoHereS type
ms.assetid: 4e817f35-a2bc-4403-9e6f-f731e6b9fe23
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 135938c4ed91423145ca46b743620f4236f7f818
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67742261"
---
# <a name="assemblyattributesgoheres"></a><span data-ttu-id="e37fd-102">AssemblyAttributesGoHereS</span><span class="sxs-lookup"><span data-stu-id="e37fd-102">AssemblyAttributesGoHereS</span></span>

<span data-ttu-id="e37fd-103">Utilisé par ALink en tant qu'espace réservé pour stocker des informations sur les attributs personnalisés.</span><span class="sxs-lookup"><span data-stu-id="e37fd-103">Used by ALink as a placeholder to store information about custom attributes.</span></span>

## <a name="syntax"></a><span data-ttu-id="e37fd-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e37fd-104">Syntax</span></span>

```csharp
internal sealed class AssemblyAttributesGoHereS
```

## <a name="remarks"></a><span data-ttu-id="e37fd-105">Notes</span><span class="sxs-lookup"><span data-stu-id="e37fd-105">Remarks</span></span>

<span data-ttu-id="e37fd-106">Les références à ce type peuvent être incorporées dans les netmodules dont les sources contiennent des attributs personnalisés d'assembly.</span><span class="sxs-lookup"><span data-stu-id="e37fd-106">References to this type might be embedded inside netmodules whose sources contain assembly custom attributes.</span></span> <span data-ttu-id="e37fd-107">Quand vous générez un manifeste d'assembly à partir d'un ou plusieurs netmodules qui contiennent des références à ces types, ALink utilise les informations associées à ces références pour émettre des attributs personnalisés réels.</span><span class="sxs-lookup"><span data-stu-id="e37fd-107">When building an assembly manifest from one or more netmodules that contain references to these types, ALink uses information attached to these references to emit real custom attributes.</span></span> <span data-ttu-id="e37fd-108">Par conséquent, ce type n'est jamais instancié et ses références sont utilisées uniquement dans le cadre du processus de génération et n'ont aucune utilité dans l'assembly final.</span><span class="sxs-lookup"><span data-stu-id="e37fd-108">As such, this type is never instantiated, and references to it are used only as part of the build process and serve no purpose in the final assembly.</span></span>

<span data-ttu-id="e37fd-109">Les références à ce type indiquent des attributs personnalisés qui sont liés à la sécurité et ne peuvent pas être utilisés plusieurs fois.</span><span class="sxs-lookup"><span data-stu-id="e37fd-109">References to this type indicate custom attributes that are security related and are not multiple-use.</span></span>

<span data-ttu-id="e37fd-110">Ces types sont marqués « internes » dans le .NET Framework et se trouvent dans le <xref:System.Runtime.CompilerServices> espace de noms.</span><span class="sxs-lookup"><span data-stu-id="e37fd-110">These types are marked "internal" within the .NET Framework and are located in the <xref:System.Runtime.CompilerServices> namespace.</span></span>

## <a name="requirements"></a><span data-ttu-id="e37fd-111">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="e37fd-111">Requirements</span></span>

<span data-ttu-id="e37fd-112">mscorlib.dll</span><span class="sxs-lookup"><span data-stu-id="e37fd-112">mscorlib.dll</span></span>

## <a name="see-also"></a><span data-ttu-id="e37fd-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e37fd-113">See also</span></span>

- [<span data-ttu-id="e37fd-114">AssemblyAttributesGoHere</span><span class="sxs-lookup"><span data-stu-id="e37fd-114">AssemblyAttributesGoHere</span></span>](assemblyattributesgohere.md)
- [<span data-ttu-id="e37fd-115">AssemblyAttributesGoHereM</span><span class="sxs-lookup"><span data-stu-id="e37fd-115">AssemblyAttributesGoHereM</span></span>](assemblyattributesgoherem.md)
- [<span data-ttu-id="e37fd-116">AssemblyAttributesGoHereSM</span><span class="sxs-lookup"><span data-stu-id="e37fd-116">AssemblyAttributesGoHereSM</span></span>](assemblyattributesgoheresm.md)
