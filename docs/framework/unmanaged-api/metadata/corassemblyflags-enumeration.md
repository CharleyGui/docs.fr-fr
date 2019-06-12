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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 43bfec471fbcfc481e178f6610e0318e9538ee34
ms.sourcegitcommit: 5bc85ad81d96b8dc2a90ce53bada475ee5662c44
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/12/2019
ms.locfileid: "67025771"
---
# <a name="corassemblyflags-enumeration"></a><span data-ttu-id="f707f-102">CorAssemblyFlags, énumération</span><span class="sxs-lookup"><span data-stu-id="f707f-102">CorAssemblyFlags Enumeration</span></span>
<span data-ttu-id="f707f-103">Contient des valeurs qui décrivent les métadonnées appliquées à une compilation d'assembly.</span><span class="sxs-lookup"><span data-stu-id="f707f-103">Contains values that describe the metadata applied to an assembly compilation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f707f-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f707f-104">Syntax</span></span>  
  
```  
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
  
## <a name="members"></a><span data-ttu-id="f707f-105">Membres</span><span class="sxs-lookup"><span data-stu-id="f707f-105">Members</span></span>  
  
|<span data-ttu-id="f707f-106">Membre</span><span class="sxs-lookup"><span data-stu-id="f707f-106">Member</span></span>|<span data-ttu-id="f707f-107">Description</span><span class="sxs-lookup"><span data-stu-id="f707f-107">Description</span></span>|  
|------------|-----------------|  
|`afPublicKey`|<span data-ttu-id="f707f-108">Indique que la référence d’assembly conserve la clé publique complète et non hachée.</span><span class="sxs-lookup"><span data-stu-id="f707f-108">Indicates that the assembly reference holds the full, unhashed public key.</span></span>|  
|`afPA_None`|<span data-ttu-id="f707f-109">Indique que l’architecture de processeur n’est pas spécifiée.</span><span class="sxs-lookup"><span data-stu-id="f707f-109">Indicates that the processor architecture is unspecified.</span></span>|  
|`afPA_MSIL`|<span data-ttu-id="f707f-110">Indique que l’architecture de processeur est neutre (PE32 +).</span><span class="sxs-lookup"><span data-stu-id="f707f-110">Indicates that the processor architecture is neutral (PE32).</span></span>|  
|`afPA_x86`|<span data-ttu-id="f707f-111">Indique que l’architecture de processeur est x86 (PE32 +).</span><span class="sxs-lookup"><span data-stu-id="f707f-111">Indicates that the processor architecture is x86 (PE32).</span></span>|  
|`afPA_IA64`|<span data-ttu-id="f707f-112">Indique que l’architecture de processeur est Itanium (PE32 +).</span><span class="sxs-lookup"><span data-stu-id="f707f-112">Indicates that the processor architecture is Itanium (PE32+).</span></span>|  
|`afPA_AMD64`|<span data-ttu-id="f707f-113">Indique que l’architecture de processeur est AMD X64 (PE32 +).</span><span class="sxs-lookup"><span data-stu-id="f707f-113">Indicates that the processor architecture is AMD X64 (PE32+).</span></span>|  
|`afPA_ARM`|<span data-ttu-id="f707f-114">Indique que l’architecture de processeur ARM (PE32 +).</span><span class="sxs-lookup"><span data-stu-id="f707f-114">Indicates that the processor architecture is ARM (PE32).</span></span>|  
|`afPA_NoPlatform`|<span data-ttu-id="f707f-115">Indique que l’assembly est un assembly de référence ; Autrement dit, elle s’applique à n’importe quelle architecture mais ne peut pas s’exécuter sur n’importe quelle architecture.</span><span class="sxs-lookup"><span data-stu-id="f707f-115">Indicates that the assembly is a reference assembly; that is, it applies to any architecture but cannot run on any architecture.</span></span> <span data-ttu-id="f707f-116">Par conséquent, l’indicateur est identique à `afPA_Mask`.</span><span class="sxs-lookup"><span data-stu-id="f707f-116">Thus, the flag is the same as `afPA_Mask`.</span></span>|  
|`afPA_Specified`|<span data-ttu-id="f707f-117">Indique que les indicateurs de l’architecture processeur doivent être propagés à la `AssemblyRef` enregistrement.</span><span class="sxs-lookup"><span data-stu-id="f707f-117">Indicates that the processor architecture flags should be propagated to the `AssemblyRef` record.</span></span>|  
|`afPA_Mask`|<span data-ttu-id="f707f-118">Masque qui décrit l’architecture de processeur.</span><span class="sxs-lookup"><span data-stu-id="f707f-118">A mask that describes the processor architecture.</span></span>|  
|`afPA_FullMask`|<span data-ttu-id="f707f-119">Spécifie que la description d’architecture de processeur est incluse.</span><span class="sxs-lookup"><span data-stu-id="f707f-119">Specifies that the processor architecture description is included.</span></span>|  
|`afPA_Shift`|<span data-ttu-id="f707f-120">Indique une valeur du décalage dans les indicateurs de l’architecture processeur vers et à partir de l’index.</span><span class="sxs-lookup"><span data-stu-id="f707f-120">Indicates a shift count in the processor architecture flags to and from the index.</span></span>|  
|`afEnableJITcompileTracking`|<span data-ttu-id="f707f-121">Indique la valeur correspondante à partir de la <xref:System.Diagnostics.DebuggableAttribute.DebuggingModes> de la <xref:System.Diagnostics.DebuggableAttribute>.</span><span class="sxs-lookup"><span data-stu-id="f707f-121">Indicates the corresponding value from the <xref:System.Diagnostics.DebuggableAttribute.DebuggingModes> of the <xref:System.Diagnostics.DebuggableAttribute>.</span></span>|  
|`afDisableJITcompileOptimizer`|<span data-ttu-id="f707f-122">Indique la valeur correspondante à partir de la <xref:System.Diagnostics.DebuggableAttribute.DebuggingModes> de la <xref:System.Diagnostics.DebuggableAttribute>.</span><span class="sxs-lookup"><span data-stu-id="f707f-122">Indicates the corresponding value from the <xref:System.Diagnostics.DebuggableAttribute.DebuggingModes> of the <xref:System.Diagnostics.DebuggableAttribute>.</span></span>|  
|`afRetargetable`|<span data-ttu-id="f707f-123">Indique que l’assembly peut être reciblé au moment de l’exécution à un assembly à partir d’un éditeur différent.</span><span class="sxs-lookup"><span data-stu-id="f707f-123">Indicates that the assembly can be retargeted at run time to an assembly from a different publisher.</span></span>|  
|`afContentType_Mask`|<span data-ttu-id="f707f-124">Masque qui décrit le type de contenu.</span><span class="sxs-lookup"><span data-stu-id="f707f-124">A mask that describes the content type.</span></span>|  
|`afContentType_Default`|<span data-ttu-id="f707f-125">Indique le type de contenu par défaut.</span><span class="sxs-lookup"><span data-stu-id="f707f-125">Indicates the default content type.</span></span>|  
|`afContentType_WindowsRuntime`|<span data-ttu-id="f707f-126">Indique le type de contenu de Windows Runtime.</span><span class="sxs-lookup"><span data-stu-id="f707f-126">Indicates the Windows Runtime content type.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="f707f-127">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="f707f-127">Requirements</span></span>  
 <span data-ttu-id="f707f-128">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f707f-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f707f-129">**En-tête :** CorHdr.h</span><span class="sxs-lookup"><span data-stu-id="f707f-129">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="f707f-130">**Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f707f-130">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f707f-131">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f707f-131">See also</span></span>

- [<span data-ttu-id="f707f-132">Énumérations de métadonnées</span><span class="sxs-lookup"><span data-stu-id="f707f-132">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
