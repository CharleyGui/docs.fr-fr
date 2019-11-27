---
title: CorAssemblyFlags, énumération
ms.date: 03/30/2017
api_name:
- CorAssemblyFlags
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorAssemblyFlags
helpviewer_keywords:
- CorAssemblyFlags enumeration [.NET Framework metadata]
ms.assetid: bb8db3b6-d81d-49fc-b74c-dbc908a9eab9
topic_type:
- apiref
ms.openlocfilehash: fda890cee5f513ea8cf7e82e710f5451a860c49f
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74443910"
---
# <a name="corassemblyflags-enumeration"></a><span data-ttu-id="bfb47-102">CorAssemblyFlags, énumération</span><span class="sxs-lookup"><span data-stu-id="bfb47-102">CorAssemblyFlags Enumeration</span></span>
<span data-ttu-id="bfb47-103">Contient des valeurs qui décrivent les métadonnées appliquées à une compilation d'assembly.</span><span class="sxs-lookup"><span data-stu-id="bfb47-103">Contains values that describe the metadata applied to an assembly compilation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bfb47-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="bfb47-104">Syntax</span></span>  
  
```cpp  
typedef enum CorAssemblyFlags {  
  
    afPublicKey             =   0x0001,  
    afPA_None               =   0x0000,  
    afPA_MSIL               =   0x0010,  
    afPA_x86                =   0x0020,  
    afPA_IA64               =   0x0030,  
    afPA_AMD64              =   0x0040,  
    afPA_ARM                =   0x0050,  
    afPA_NoPlatform         =   0x0070,  
    afPA_Specified          =   0x0080,  
    afPA_Mask               =   0x0070,  
    afPA_FullMask           =   0x00F0,  
    afPA_Shift              =   0x0004,  
  
    afEnableJITcompileTracking  =   0x8000,  
    afDisableJITcompileOptimizer=   0x4000,  
  
    afRetargetable          =   0x0100,  
    afContentType_Default        =   0x0000,  
    afContentType_WindowsRuntime =   0x0200,  
    afContentType_Mask           =   0x0E00,  
  
} CorAssemblyFlags;  
```  
  
## <a name="members"></a><span data-ttu-id="bfb47-105">Membres</span><span class="sxs-lookup"><span data-stu-id="bfb47-105">Members</span></span>  
  
|<span data-ttu-id="bfb47-106">Membre</span><span class="sxs-lookup"><span data-stu-id="bfb47-106">Member</span></span>|<span data-ttu-id="bfb47-107">Description</span><span class="sxs-lookup"><span data-stu-id="bfb47-107">Description</span></span>|  
|------------|-----------------|  
|`afPublicKey`|<span data-ttu-id="bfb47-108">Indique que la référence d’assembly contient la clé publique déhachée complète.</span><span class="sxs-lookup"><span data-stu-id="bfb47-108">Indicates that the assembly reference holds the full, unhashed public key.</span></span>|  
|`afPA_None`|<span data-ttu-id="bfb47-109">Indique que l’architecture du processeur n’est pas spécifiée.</span><span class="sxs-lookup"><span data-stu-id="bfb47-109">Indicates that the processor architecture is unspecified.</span></span>|  
|`afPA_MSIL`|<span data-ttu-id="bfb47-110">Indique que l’architecture du processeur est neutre (PE32).</span><span class="sxs-lookup"><span data-stu-id="bfb47-110">Indicates that the processor architecture is neutral (PE32).</span></span>|  
|`afPA_x86`|<span data-ttu-id="bfb47-111">Indique que l’architecture du processeur est x86 (PE32).</span><span class="sxs-lookup"><span data-stu-id="bfb47-111">Indicates that the processor architecture is x86 (PE32).</span></span>|  
|`afPA_IA64`|<span data-ttu-id="bfb47-112">Indique que l’architecture du processeur est Itanium (PE32 +).</span><span class="sxs-lookup"><span data-stu-id="bfb47-112">Indicates that the processor architecture is Itanium (PE32+).</span></span>|  
|`afPA_AMD64`|<span data-ttu-id="bfb47-113">Indique que l’architecture du processeur est AMD x64 (PE32 +).</span><span class="sxs-lookup"><span data-stu-id="bfb47-113">Indicates that the processor architecture is AMD X64 (PE32+).</span></span>|  
|`afPA_ARM`|<span data-ttu-id="bfb47-114">Indique que l’architecture du processeur est ARM (PE32).</span><span class="sxs-lookup"><span data-stu-id="bfb47-114">Indicates that the processor architecture is ARM (PE32).</span></span>|  
|`afPA_NoPlatform`|<span data-ttu-id="bfb47-115">Indique que l’assembly est un assembly de référence ; autrement dit, elle s’applique à n’importe quelle architecture, mais ne peut pas être exécutée sur n’importe quelle architecture.</span><span class="sxs-lookup"><span data-stu-id="bfb47-115">Indicates that the assembly is a reference assembly; that is, it applies to any architecture but cannot run on any architecture.</span></span> <span data-ttu-id="bfb47-116">Ainsi, l’indicateur est le même que `afPA_Mask`.</span><span class="sxs-lookup"><span data-stu-id="bfb47-116">Thus, the flag is the same as `afPA_Mask`.</span></span>|  
|`afPA_Specified`|<span data-ttu-id="bfb47-117">Indique que les indicateurs de l’architecture du processeur doivent être propagés à l’enregistrement `AssemblyRef`.</span><span class="sxs-lookup"><span data-stu-id="bfb47-117">Indicates that the processor architecture flags should be propagated to the `AssemblyRef` record.</span></span>|  
|`afPA_Mask`|<span data-ttu-id="bfb47-118">Masque qui décrit l’architecture du processeur.</span><span class="sxs-lookup"><span data-stu-id="bfb47-118">A mask that describes the processor architecture.</span></span>|  
|`afPA_FullMask`|<span data-ttu-id="bfb47-119">Spécifie que la description de l’architecture du processeur est incluse.</span><span class="sxs-lookup"><span data-stu-id="bfb47-119">Specifies that the processor architecture description is included.</span></span>|  
|`afPA_Shift`|<span data-ttu-id="bfb47-120">Indique un nombre de décalages dans les indicateurs d’architecture de processeur vers et à partir de l’index.</span><span class="sxs-lookup"><span data-stu-id="bfb47-120">Indicates a shift count in the processor architecture flags to and from the index.</span></span>|  
|`afEnableJITcompileTracking`|<span data-ttu-id="bfb47-121">Indique la valeur correspondante de la <xref:System.Diagnostics.DebuggableAttribute.DebuggingModes> du <xref:System.Diagnostics.DebuggableAttribute>.</span><span class="sxs-lookup"><span data-stu-id="bfb47-121">Indicates the corresponding value from the <xref:System.Diagnostics.DebuggableAttribute.DebuggingModes> of the <xref:System.Diagnostics.DebuggableAttribute>.</span></span>|  
|`afDisableJITcompileOptimizer`|<span data-ttu-id="bfb47-122">Indique la valeur correspondante de la <xref:System.Diagnostics.DebuggableAttribute.DebuggingModes> du <xref:System.Diagnostics.DebuggableAttribute>.</span><span class="sxs-lookup"><span data-stu-id="bfb47-122">Indicates the corresponding value from the <xref:System.Diagnostics.DebuggableAttribute.DebuggingModes> of the <xref:System.Diagnostics.DebuggableAttribute>.</span></span>|  
|`afRetargetable`|<span data-ttu-id="bfb47-123">Indique que l’assembly peut être reciblé au moment de l’exécution vers un assembly d’un autre serveur de publication.</span><span class="sxs-lookup"><span data-stu-id="bfb47-123">Indicates that the assembly can be retargeted at run time to an assembly from a different publisher.</span></span>|  
|`afContentType_Mask`|<span data-ttu-id="bfb47-124">Masque qui décrit le type de contenu.</span><span class="sxs-lookup"><span data-stu-id="bfb47-124">A mask that describes the content type.</span></span>|  
|`afContentType_Default`|<span data-ttu-id="bfb47-125">Indique le type de contenu par défaut.</span><span class="sxs-lookup"><span data-stu-id="bfb47-125">Indicates the default content type.</span></span>|  
|`afContentType_WindowsRuntime`|<span data-ttu-id="bfb47-126">Indique le type de contenu Windows Runtime.</span><span class="sxs-lookup"><span data-stu-id="bfb47-126">Indicates the Windows Runtime content type.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="bfb47-127">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="bfb47-127">Requirements</span></span>  
 <span data-ttu-id="bfb47-128">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bfb47-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bfb47-129">**En-tête :** CorHdr. h</span><span class="sxs-lookup"><span data-stu-id="bfb47-129">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="bfb47-130">**Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bfb47-130">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bfb47-131">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="bfb47-131">See also</span></span>

- [<span data-ttu-id="bfb47-132">Énumérations de métadonnées</span><span class="sxs-lookup"><span data-stu-id="bfb47-132">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
