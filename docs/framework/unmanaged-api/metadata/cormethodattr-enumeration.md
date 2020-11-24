---
title: CorMethodAttr, énumération
ms.date: 03/30/2017
api_name:
- CorMethodAttr
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorMethodAttr
helpviewer_keywords:
- CorMethodAttr enumeration [.NET Framework metadata]
ms.assetid: 4e0c3521-e54d-43c1-9857-cc76b49b8ffc
topic_type:
- apiref
ms.openlocfilehash: 6c3e721c24da217eaf2e8857377359e1c51b7b59
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95677010"
---
# <a name="cormethodattr-enumeration"></a><span data-ttu-id="90dd3-102">CorMethodAttr, énumération</span><span class="sxs-lookup"><span data-stu-id="90dd3-102">CorMethodAttr Enumeration</span></span>

<span data-ttu-id="90dd3-103">Contient des valeurs qui décrivent les fonctionnalités d’une méthode.</span><span class="sxs-lookup"><span data-stu-id="90dd3-103">Contains values that describe the features of a method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="90dd3-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="90dd3-104">Syntax</span></span>  
  
```cpp  
typedef enum CorMethodAttr {  
  
    mdMemberAccessMask          =   0x0007,  
    mdPrivateScope              =   0x0000,  
    mdPrivate                   =   0x0001,  
    mdFamANDAssem               =   0x0002,  
    mdAssem                     =   0x0003,  
    mdFamily                    =   0x0004,  
    mdFamORAssem                =   0x0005,  
    mdPublic                    =   0x0006,  
  
    mdStatic                    =   0x0010,  
    mdFinal                     =   0x0020,  
    mdVirtual                   =   0x0040,  
    mdHideBySig                 =   0x0080,  
  
    mdVtableLayoutMask          =   0x0100,  
    mdReuseSlot                 =   0x0000,  
    mdNewSlot                   =   0x0100,  
  
    mdCheckAccessOnOverride     =   0x0200,  
    mdAbstract                  =   0x0400,  
    mdSpecialName               =   0x0800,  
  
    mdPinvokeImpl               =   0x2000,  
    mdUnmanagedExport           =   0x0008,  
  
    mdReservedMask              =   0xd000,  
    mdRTSpecialName             =   0x1000,  
    mdHasSecurity               =   0x4000,  
    mdRequireSecObject          =   0x8000,  
  
} CorMethodAttr;  
```  
  
## <a name="members"></a><span data-ttu-id="90dd3-105">Membres</span><span class="sxs-lookup"><span data-stu-id="90dd3-105">Members</span></span>  
  
|<span data-ttu-id="90dd3-106">Membre</span><span class="sxs-lookup"><span data-stu-id="90dd3-106">Member</span></span>|<span data-ttu-id="90dd3-107">Description</span><span class="sxs-lookup"><span data-stu-id="90dd3-107">Description</span></span>|  
|------------|-----------------|  
|`mdMemberAccessMask`|<span data-ttu-id="90dd3-108">Spécifie l’accès au membre.</span><span class="sxs-lookup"><span data-stu-id="90dd3-108">Specifies member access.</span></span>|  
|`mdPrivateScope`|<span data-ttu-id="90dd3-109">Spécifie que le membre ne peut pas être référencé.</span><span class="sxs-lookup"><span data-stu-id="90dd3-109">Specifies that the member cannot be referenced.</span></span>|  
|`mdPrivate`|<span data-ttu-id="90dd3-110">Spécifie que le membre est accessible uniquement par le type parent.</span><span class="sxs-lookup"><span data-stu-id="90dd3-110">Specifies that the member is accessible only by the parent type.</span></span>|  
|`mdFamANDAssem`|<span data-ttu-id="90dd3-111">Spécifie que le membre est accessible par les sous-types uniquement dans cet assembly.</span><span class="sxs-lookup"><span data-stu-id="90dd3-111">Specifies that the member is accessible by subtypes only in this assembly.</span></span>|  
|`mdAssem`|<span data-ttu-id="90dd3-112">Spécifie que le membre est accessibly par toute personne de l’assembly.</span><span class="sxs-lookup"><span data-stu-id="90dd3-112">Specifies that the member is accessibly by anyone in the assembly.</span></span>|  
|`mdFamily`|<span data-ttu-id="90dd3-113">Spécifie que le membre est accessible uniquement par type et sous-types.</span><span class="sxs-lookup"><span data-stu-id="90dd3-113">Specifies that the member is accessible only by type and subtypes.</span></span>|  
|`mdFamORAssem`|<span data-ttu-id="90dd3-114">Spécifie que le membre est accessible par les classes dérivées et par d’autres types dans son assembly.</span><span class="sxs-lookup"><span data-stu-id="90dd3-114">Specifies that the member is accessible by derived classes and by other types in its assembly.</span></span>|  
|`mdPublic`|<span data-ttu-id="90dd3-115">Spécifie que le membre est accessible par tous les types ayant accès à la portée.</span><span class="sxs-lookup"><span data-stu-id="90dd3-115">Specifies that the member is accessible by all types with access to the scope.</span></span>|  
|`mdStatic`|<span data-ttu-id="90dd3-116">Spécifie que le membre est défini dans le cadre du type plutôt qu’en tant que membre d’une instance.</span><span class="sxs-lookup"><span data-stu-id="90dd3-116">Specifies that the member is defined as part of the type rather than as a member of an instance.</span></span>|  
|`mdFinal`|<span data-ttu-id="90dd3-117">Spécifie que la méthode ne peut pas être substituée.</span><span class="sxs-lookup"><span data-stu-id="90dd3-117">Specifies that the method cannot be overridden.</span></span>|  
|`mdVirtual`|<span data-ttu-id="90dd3-118">Spécifie que la méthode peut être substituée.</span><span class="sxs-lookup"><span data-stu-id="90dd3-118">Specifies that the method can be overridden.</span></span>|  
|`mdHideBySig`|<span data-ttu-id="90dd3-119">Spécifie que la méthode masque par nom et par signature, plutôt que simplement par nom.</span><span class="sxs-lookup"><span data-stu-id="90dd3-119">Specifies that the method hides by name and signature, rather than just by name.</span></span>|  
|`mdVtableLayoutMask`|<span data-ttu-id="90dd3-120">Spécifie la disposition de la table virtuelle.</span><span class="sxs-lookup"><span data-stu-id="90dd3-120">Specifies virtual table layout.</span></span>|  
|`mdReuseSlot`|<span data-ttu-id="90dd3-121">Spécifie que l’emplacement utilisé pour cette méthode dans la table virtuelle doit être réutilisé.</span><span class="sxs-lookup"><span data-stu-id="90dd3-121">Specifies that the slot used for this method in the virtual table be reused.</span></span> <span data-ttu-id="90dd3-122">Il s’agit de la valeur par défaut.</span><span class="sxs-lookup"><span data-stu-id="90dd3-122">This is the default.</span></span>|  
|`mdNewSlot`|<span data-ttu-id="90dd3-123">Spécifie que la méthode obtient toujours un nouvel emplacement dans la table virtuelle.</span><span class="sxs-lookup"><span data-stu-id="90dd3-123">Specifies that the method always gets a new slot in the virtual table.</span></span>|  
|`mdCheckAccessOnOverride`|<span data-ttu-id="90dd3-124">Spécifie que la méthode peut être substituée par les mêmes types auxquels elle est visible.</span><span class="sxs-lookup"><span data-stu-id="90dd3-124">Specifies that the method can be overridden by the same types to which it is visible.</span></span>|  
|`mdAbstract`|<span data-ttu-id="90dd3-125">Spécifie que la méthode n’est pas implémentée.</span><span class="sxs-lookup"><span data-stu-id="90dd3-125">Specifies that the method is not implemented.</span></span>|  
|`mdSpecialName`|<span data-ttu-id="90dd3-126">Spécifie que la méthode est spéciale et que son nom décrit comment.</span><span class="sxs-lookup"><span data-stu-id="90dd3-126">Specifies that the method is special, and that its name describes how.</span></span>|  
|`mdPinvokeImpl`|<span data-ttu-id="90dd3-127">Spécifie que l’implémentation de la méthode est transférée à l’aide de PInvoke.</span><span class="sxs-lookup"><span data-stu-id="90dd3-127">Specifies that the method implementation is forwarded using PInvoke.</span></span>|  
|`mdUnmanagedExport`|<span data-ttu-id="90dd3-128">Spécifie que la méthode est une méthode managée exportée vers du code non managé.</span><span class="sxs-lookup"><span data-stu-id="90dd3-128">Specifies that the method is a managed method exported to unmanaged code.</span></span>|  
|`mdReservedMask`|<span data-ttu-id="90dd3-129">Réservé à un usage interne par la common language runtime.</span><span class="sxs-lookup"><span data-stu-id="90dd3-129">Reserved for internal use by the common language runtime.</span></span>|  
|`mdRTSpecialName`|<span data-ttu-id="90dd3-130">Spécifie que le common language runtime doit vérifier l’encodage du nom de la méthode.</span><span class="sxs-lookup"><span data-stu-id="90dd3-130">Specifies that the common language runtime should check the encoding of the method name.</span></span>|  
|`mdHasSecurity`|<span data-ttu-id="90dd3-131">Spécifie que la méthode est associée à la sécurité.</span><span class="sxs-lookup"><span data-stu-id="90dd3-131">Specifies that the method has security associated with it.</span></span>|  
|`mdRequireSecObject`|<span data-ttu-id="90dd3-132">Spécifie que la méthode appelle une autre méthode contenant du code de sécurité.</span><span class="sxs-lookup"><span data-stu-id="90dd3-132">Specifies that the method calls another method containing security code.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="90dd3-133">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="90dd3-133">Requirements</span></span>  

 <span data-ttu-id="90dd3-134">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="90dd3-134">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="90dd3-135">**En-tête :** CorHdr. h</span><span class="sxs-lookup"><span data-stu-id="90dd3-135">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="90dd3-136">**Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="90dd3-136">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="90dd3-137">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="90dd3-137">See also</span></span>

- [<span data-ttu-id="90dd3-138">Énumérations de métadonnées</span><span class="sxs-lookup"><span data-stu-id="90dd3-138">Metadata Enumerations</span></span>](metadata-enumerations.md)
