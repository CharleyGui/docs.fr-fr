---
title: CorTypeAttr, énumération
ms.date: 03/30/2017
api_name:
- CorTypeAttr
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorTypeAttr
helpviewer_keywords:
- CorTypeAttr enumeration [.NET Framework metadata]
ms.assetid: 9bede0ec-5fdf-42a2-b5b7-bee64056acb6
topic_type:
- apiref
ms.openlocfilehash: b6936081ca3dbadb4f802a6856fafb53f6cef3fa
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/27/2020
ms.locfileid: "84008961"
---
# <a name="cortypeattr-enumeration"></a><span data-ttu-id="fbdba-102">CorTypeAttr, énumération</span><span class="sxs-lookup"><span data-stu-id="fbdba-102">CorTypeAttr Enumeration</span></span>
<span data-ttu-id="fbdba-103">Contient des valeurs qui indiquent les métadonnées de type.</span><span class="sxs-lookup"><span data-stu-id="fbdba-103">Contains values that indicate type metadata.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fbdba-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="fbdba-104">Syntax</span></span>  
  
```cpp  
typedef enum CorTypeAttr {  
  
    tdVisibilityMask        =   0x00000007,  
    tdNotPublic             =   0x00000000,  
    tdPublic                =   0x00000001,  
    tdNestedPublic          =   0x00000002,  
    tdNestedPrivate         =   0x00000003,  
    tdNestedFamily          =   0x00000004,  
    tdNestedAssembly        =   0x00000005,  
    tdNestedFamANDAssem     =   0x00000006,  
    tdNestedFamORAssem      =   0x00000007,  
  
    tdLayoutMask            =   0x00000018,  
    tdAutoLayout            =   0x00000000,  
    tdSequentialLayout      =   0x00000008,  
    tdExplicitLayout        =   0x00000010,  
  
    tdClassSemanticsMask    =   0x00000020,  
    tdClass                 =   0x00000000,  
    tdInterface             =   0x00000020,  
  
    tdAbstract              =   0x00000080,  
    tdSealed                =   0x00000100,  
    tdSpecialName           =   0x00000400,  
  
    tdImport                =   0x00001000,  
    tdSerializable          =   0x00002000,  
    tdWindowsRuntime        =   0x00004000,  
  
    tdStringFormatMask      =   0x00030000,  
    tdAnsiClass             =   0x00000000,  
    tdUnicodeClass          =   0x00010000,  
    tdAutoClass             =   0x00020000,  
    tdCustomFormatClass     =   0x00030000,  
    tdCustomFormatMask      =   0x00C00000,  
  
    tdBeforeFieldInit       =   0x00100000,  
    tdForwarder             =   0x00200000,  
  
    tdReservedMask          =   0x00040800,  
    tdRTSpecialName         =   0x00000800,  
    tdHasSecurity           =   0x00040000,  
  
} CorTypeAttr;  
```  
  
## <a name="members"></a><span data-ttu-id="fbdba-105">Membres</span><span class="sxs-lookup"><span data-stu-id="fbdba-105">Members</span></span>  
  
|<span data-ttu-id="fbdba-106">Membre</span><span class="sxs-lookup"><span data-stu-id="fbdba-106">Member</span></span>|<span data-ttu-id="fbdba-107">Description</span><span class="sxs-lookup"><span data-stu-id="fbdba-107">Description</span></span>|  
|------------|-----------------|  
|`tdVisibilityMask`|<span data-ttu-id="fbdba-108">Utilisé pour les informations de visibilité du type.</span><span class="sxs-lookup"><span data-stu-id="fbdba-108">Used for type visibility information.</span></span>|  
|`tdNotPublic`|<span data-ttu-id="fbdba-109">Spécifie que le type n’est pas dans la portée publique.</span><span class="sxs-lookup"><span data-stu-id="fbdba-109">Specifies that the type is not in public scope.</span></span>|  
|`tdPublic`|<span data-ttu-id="fbdba-110">Spécifie que le type est dans une portée publique.</span><span class="sxs-lookup"><span data-stu-id="fbdba-110">Specifies that the type is in public scope.</span></span>|  
|`tdNestedPublic`|<span data-ttu-id="fbdba-111">Spécifie que le type est imbriqué avec une visibilité publique.</span><span class="sxs-lookup"><span data-stu-id="fbdba-111">Specifies that the type is nested with public visibility.</span></span>|  
|`tdNestedPrivate`|<span data-ttu-id="fbdba-112">Spécifie que le type est imbriqué avec une visibilité privée.</span><span class="sxs-lookup"><span data-stu-id="fbdba-112">Specifies that the type is nested with private visibility.</span></span>|  
|`tdNestedFamily`|<span data-ttu-id="fbdba-113">Spécifie que le type est imbriqué avec la visibilité de la famille.</span><span class="sxs-lookup"><span data-stu-id="fbdba-113">Specifies that the type is nested with family visibility.</span></span>|  
|`tdNestedAssembly`|<span data-ttu-id="fbdba-114">Spécifie que le type est imbriqué avec la visibilité de l’assembly.</span><span class="sxs-lookup"><span data-stu-id="fbdba-114">Specifies that the type is nested with assembly visibility.</span></span>|  
|`tdNestedFamANDAssem`|<span data-ttu-id="fbdba-115">Spécifie que le type est imbriqué avec la visibilité de la famille et de l’assembly.</span><span class="sxs-lookup"><span data-stu-id="fbdba-115">Specifies that the type is nested with family and assembly visibility.</span></span>|  
|`tdNestedFamORAssem`|<span data-ttu-id="fbdba-116">Spécifie que le type est imbriqué avec une visibilité Family ou assembly.</span><span class="sxs-lookup"><span data-stu-id="fbdba-116">Specifies that the type is nested with family or assembly visibility.</span></span>|  
|`tdLayoutMask`|<span data-ttu-id="fbdba-117">Obtient des informations de disposition pour le type.</span><span class="sxs-lookup"><span data-stu-id="fbdba-117">Gets layout information for the type.</span></span>|  
|`tdAutoLayout`|<span data-ttu-id="fbdba-118">Spécifie que les champs de ce type sont disposés automatiquement.</span><span class="sxs-lookup"><span data-stu-id="fbdba-118">Specifies that the fields of this type are laid out automatically.</span></span>|  
|`tdSequentialLayout`|<span data-ttu-id="fbdba-119">Spécifie que les champs de ce type sont disposés de manière séquentielle.</span><span class="sxs-lookup"><span data-stu-id="fbdba-119">Specifies that the fields of this type are laid out sequentially.</span></span>|  
|`tdExplicitLayout`|<span data-ttu-id="fbdba-120">Spécifie que la disposition des champs est fournie explicitement.</span><span class="sxs-lookup"><span data-stu-id="fbdba-120">Specifies that field layout is supplied explicitly.</span></span>|  
|`tdClassSemanticsMask`|<span data-ttu-id="fbdba-121">Obtient des informations sémantiques sur le type.</span><span class="sxs-lookup"><span data-stu-id="fbdba-121">Gets semantic information about the type.</span></span>|  
|`tdClass`|<span data-ttu-id="fbdba-122">Spécifie que le type est une classe.</span><span class="sxs-lookup"><span data-stu-id="fbdba-122">Specifies that the type is a class.</span></span>|  
|`tdInterface`|<span data-ttu-id="fbdba-123">Spécifie que le type est une interface.</span><span class="sxs-lookup"><span data-stu-id="fbdba-123">Specifies that the type is an interface.</span></span>|  
|`tdAbstract`|<span data-ttu-id="fbdba-124">Spécifie que le type est abstrait.</span><span class="sxs-lookup"><span data-stu-id="fbdba-124">Specifies that the type is abstract.</span></span>|  
|`tdSealed`|<span data-ttu-id="fbdba-125">Spécifie que le type ne peut pas être étendu.</span><span class="sxs-lookup"><span data-stu-id="fbdba-125">Specifies that the type cannot be extended.</span></span>|  
|`tdSpecialName`|<span data-ttu-id="fbdba-126">Spécifie que le nom de la classe est spécial.</span><span class="sxs-lookup"><span data-stu-id="fbdba-126">Specifies that the class name is special.</span></span> <span data-ttu-id="fbdba-127">Son nom décrit comment.</span><span class="sxs-lookup"><span data-stu-id="fbdba-127">Its name describes how.</span></span>|  
|`tdImport`|<span data-ttu-id="fbdba-128">Spécifie que le type est importé.</span><span class="sxs-lookup"><span data-stu-id="fbdba-128">Specifies that the type is imported.</span></span>|  
|`tdSerializable`|<span data-ttu-id="fbdba-129">Spécifie que le type est sérialisable.</span><span class="sxs-lookup"><span data-stu-id="fbdba-129">Specifies that the type is serializable.</span></span>|  
|`tdWindowsRuntime`|<span data-ttu-id="fbdba-130">Spécifie que ce type est un type de Windows Runtime.</span><span class="sxs-lookup"><span data-stu-id="fbdba-130">Specifies that this type is a Windows Runtime type.</span></span>|  
|`tdStringFormatMask`|<span data-ttu-id="fbdba-131">Obtient des informations sur la façon dont les chaînes sont encodées et mises en forme.</span><span class="sxs-lookup"><span data-stu-id="fbdba-131">Gets information about how strings are encoded and formatted.</span></span>|  
|`tdAnsiClass`|<span data-ttu-id="fbdba-132">Spécifie que ce type interprète un LPTSTR comme ANSI.</span><span class="sxs-lookup"><span data-stu-id="fbdba-132">Specifies that this type interprets an LPTSTR as ANSI.</span></span>|  
|`tdUnicodeClass`|<span data-ttu-id="fbdba-133">Spécifie que ce type interprète un LPTSTR comme Unicode.</span><span class="sxs-lookup"><span data-stu-id="fbdba-133">Specifies that this type interprets an LPTSTR as Unicode.</span></span>|  
|`tdAutoClass`|<span data-ttu-id="fbdba-134">Spécifie que ce type interprète un LPTSTR automatiquement.</span><span class="sxs-lookup"><span data-stu-id="fbdba-134">Specifies that this type interprets an LPTSTR automatically.</span></span>|  
|`tdCustomFormatClass`|<span data-ttu-id="fbdba-135">Spécifie que le type a un encodage non standard, comme spécifié par `CustomFormatMask` .</span><span class="sxs-lookup"><span data-stu-id="fbdba-135">Specifies that the type has a non-standard encoding, as specified by `CustomFormatMask`.</span></span>|  
|`tdCustomFormatMask`|<span data-ttu-id="fbdba-136">Utilisez ce masque pour obtenir des informations d’encodage non standard pour une interopérabilité native.</span><span class="sxs-lookup"><span data-stu-id="fbdba-136">Use this mask to get non-standard encoding information for native interop.</span></span> <span data-ttu-id="fbdba-137">La signification des valeurs de ces deux bits n’est pas spécifiée.</span><span class="sxs-lookup"><span data-stu-id="fbdba-137">The meaning of the values of these two bits is unspecified.</span></span>|  
|`tdBeforeFieldInit`|<span data-ttu-id="fbdba-138">Spécifie que le type doit être initialisé avant la première tentative d’accès à un champ statique.</span><span class="sxs-lookup"><span data-stu-id="fbdba-138">Specifies that the type must be initialized before the first attempt to access a static field.</span></span>|  
|`tdForwarder`|<span data-ttu-id="fbdba-139">Spécifie que le type est exporté et un redirecteur de type.</span><span class="sxs-lookup"><span data-stu-id="fbdba-139">Specifies that the type is exported, and a type forwarder.</span></span>|  
|`tdReservedMask`|<span data-ttu-id="fbdba-140">Cet indicateur et les indicateurs ci-dessous sont utilisés en interne par le common language runtime.</span><span class="sxs-lookup"><span data-stu-id="fbdba-140">This flag and the flags below are used internally by the common language runtime.</span></span>|  
|`tdRTSpecialName`|<span data-ttu-id="fbdba-141">Spécifie que le common language runtime doit vérifier l’encodage du nom.</span><span class="sxs-lookup"><span data-stu-id="fbdba-141">Specifies that the common language runtime should check the name encoding.</span></span>|  
|`tdHasSecurity`|<span data-ttu-id="fbdba-142">Spécifie que la sécurité est associée au type.</span><span class="sxs-lookup"><span data-stu-id="fbdba-142">Specifies that the type has security associated with it.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="fbdba-143">Spécifications</span><span class="sxs-lookup"><span data-stu-id="fbdba-143">Requirements</span></span>  
 <span data-ttu-id="fbdba-144">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fbdba-144">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fbdba-145">**En-tête :** CorHdr. h</span><span class="sxs-lookup"><span data-stu-id="fbdba-145">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="fbdba-146">**Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fbdba-146">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fbdba-147">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="fbdba-147">See also</span></span>

- [<span data-ttu-id="fbdba-148">Énumérations de métadonnées</span><span class="sxs-lookup"><span data-stu-id="fbdba-148">Metadata Enumerations</span></span>](metadata-enumerations.md)
