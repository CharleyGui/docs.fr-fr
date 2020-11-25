---
title: AssemblyRefFlags, énumération
ms.date: 03/30/2017
api_name:
- AssemblyRefFlags
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- AssemblyRefFlags
helpviewer_keywords:
- AssemblyRefFlags enumeration [.NET Framework metadata]
ms.assetid: decd4f46-f3b2-466f-9501-e74f2b86b846
topic_type:
- apiref
ms.openlocfilehash: 0a99d2f79645bdc46ff4db86d7280614eeb1faf5
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95732760"
---
# <a name="assemblyrefflags-enumeration"></a><span data-ttu-id="a5337-102">AssemblyRefFlags, énumération</span><span class="sxs-lookup"><span data-stu-id="a5337-102">AssemblyRefFlags Enumeration</span></span>

<span data-ttu-id="a5337-103">Contient des valeurs qui décrivent les fonctionnalités d’une référence d’assembly.</span><span class="sxs-lookup"><span data-stu-id="a5337-103">Contains values that describe features of an assembly reference.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a5337-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a5337-104">Syntax</span></span>  
  
```cpp  
typedef enum {  
    arfFullOriginator = 0x0001  
} AssemblyRefFlags;  
```  
  
## <a name="members"></a><span data-ttu-id="a5337-105">Membres</span><span class="sxs-lookup"><span data-stu-id="a5337-105">Members</span></span>  
  
|<span data-ttu-id="a5337-106">Membre</span><span class="sxs-lookup"><span data-stu-id="a5337-106">Member</span></span>|<span data-ttu-id="a5337-107">Description</span><span class="sxs-lookup"><span data-stu-id="a5337-107">Description</span></span>|  
|------------|-----------------|  
|`arfFullOriginator`|<span data-ttu-id="a5337-108">Spécifie que la référence d’assembly contient des informations complètes et non hachées sur le serveur de publication de l’assembly.</span><span class="sxs-lookup"><span data-stu-id="a5337-108">Specifies that the assembly reference contains full, unhashed information about the publisher of the assembly.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="a5337-109">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="a5337-109">Requirements</span></span>  

 <span data-ttu-id="a5337-110">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a5337-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a5337-111">**En-tête :** Cor. h</span><span class="sxs-lookup"><span data-stu-id="a5337-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="a5337-112">**Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a5337-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a5337-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a5337-113">See also</span></span>

- [<span data-ttu-id="a5337-114">Énumérations de métadonnées</span><span class="sxs-lookup"><span data-stu-id="a5337-114">Metadata Enumerations</span></span>](metadata-enumerations.md)
- [<span data-ttu-id="a5337-115">IMetaDataAssemblyEmit, interface</span><span class="sxs-lookup"><span data-stu-id="a5337-115">IMetaDataAssemblyEmit Interface</span></span>](imetadataassemblyemit-interface.md)
- [<span data-ttu-id="a5337-116">DefineAssemblyRef, méthode</span><span class="sxs-lookup"><span data-stu-id="a5337-116">DefineAssemblyRef Method</span></span>](imetadataassemblyemit-defineassemblyref-method.md)
