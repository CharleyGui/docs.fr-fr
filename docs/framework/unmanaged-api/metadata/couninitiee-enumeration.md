---
title: COUNINITIEE, énumération
ms.date: 03/30/2017
api_name:
- COUNINITIEE
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- COUNINITIEE
helpviewer_keywords:
- COUNINITIEE enumeration [.NET Framework metadata]
ms.assetid: c42baa79-f469-4330-95a2-baf7f021c2fc
topic_type:
- apiref
ms.openlocfilehash: 14942680a79c4d1fcc69092a4f752738db1fb0b0
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/27/2020
ms.locfileid: "84008912"
---
# <a name="couninitiee-enumeration"></a><span data-ttu-id="3eac9-102">COUNINITIEE, énumération</span><span class="sxs-lookup"><span data-stu-id="3eac9-102">COUNINITIEE Enumeration</span></span>
<span data-ttu-id="3eac9-103">Spécifie les constantes utilisées par [CoUninitializeEE,](../hosting/couninitializeee-function.md) lors de l’initialisation du Common Language Runtime.</span><span class="sxs-lookup"><span data-stu-id="3eac9-103">Specifies constants used by [CoUninitializeEE](../hosting/couninitializeee-function.md) when initializing the common language runtime.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3eac9-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3eac9-104">Syntax</span></span>  
  
```cpp  
typedef enum tagCOUNINITEE  
{  
    COUNINITEE_DEFAULT  = 0x0,
    COUNINITEE_DLL      = 0x1  
} COUNINITIEE;  
```  
  
## <a name="members"></a><span data-ttu-id="3eac9-105">Membres</span><span class="sxs-lookup"><span data-stu-id="3eac9-105">Members</span></span>  
  
|<span data-ttu-id="3eac9-106">Membre</span><span class="sxs-lookup"><span data-stu-id="3eac9-106">Member</span></span>|<span data-ttu-id="3eac9-107">Description</span><span class="sxs-lookup"><span data-stu-id="3eac9-107">Description</span></span>|  
|------------|-----------------|  
|`COUNINITEE_DEFAULT`|<span data-ttu-id="3eac9-108">Indique le mode d’initialisation par défaut.</span><span class="sxs-lookup"><span data-stu-id="3eac9-108">Indicates default uninitialization mode.</span></span>|  
|`COUNINITEE_DLL`|<span data-ttu-id="3eac9-109">Indique le mode d’initialisation pour le déchargement d’un assembly.</span><span class="sxs-lookup"><span data-stu-id="3eac9-109">Indicates uninitialization mode for unloading an assembly.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="3eac9-110">Spécifications</span><span class="sxs-lookup"><span data-stu-id="3eac9-110">Requirements</span></span>  
 <span data-ttu-id="3eac9-111">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3eac9-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3eac9-112">**En-tête :** Cor. h</span><span class="sxs-lookup"><span data-stu-id="3eac9-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="3eac9-113">**Bibliothèque :** Inclus en tant que ressource dans MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="3eac9-113">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="3eac9-114">**Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3eac9-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3eac9-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3eac9-115">See also</span></span>

- [<span data-ttu-id="3eac9-116">Énumérations de métadonnées</span><span class="sxs-lookup"><span data-stu-id="3eac9-116">Metadata Enumerations</span></span>](metadata-enumerations.md)
