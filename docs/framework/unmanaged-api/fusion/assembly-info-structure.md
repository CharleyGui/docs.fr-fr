---
title: ASSEMBLY_INFO, structure
ms.date: 03/30/2017
api_name:
- ASSEMBLY_INFO
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- ASSEMBLY_INFO
helpviewer_keywords:
- ASSEMBLY_INFO structure [.NET Framework fusion]
ms.assetid: b3cbb47c-457f-4083-8895-49562ca99ab8
topic_type:
- apiref
ms.openlocfilehash: a43d5e15c02a97ff10a6a5afd439cadebb6b33d2
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73109212"
---
# <a name="assembly_info-structure"></a><span data-ttu-id="19a3f-102">ASSEMBLY_INFO, structure</span><span class="sxs-lookup"><span data-stu-id="19a3f-102">ASSEMBLY_INFO Structure</span></span>
<span data-ttu-id="19a3f-103">Contient des informations sur un assembly qui est inscrit dans le Global Assembly Cache.</span><span class="sxs-lookup"><span data-stu-id="19a3f-103">Contains information about an assembly that is registered in the global assembly cache.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="19a3f-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="19a3f-104">Syntax</span></span>  
  
```cpp  
typedef struct _ASSEMBLY_INFO {  
    ULONG           cbAssemblyInfo;  
    DWORD           dwAssemblyFlags;  
    ULARGE_INTEGER  uliAssemblySizeInKB;  
    LPWSTR          pszCurrentAssemblyPathBuf;  
    ULONG           cchBuf;  
} ASSEMBLY_INFO;  
```  
  
## <a name="members"></a><span data-ttu-id="19a3f-105">Membres</span><span class="sxs-lookup"><span data-stu-id="19a3f-105">Members</span></span>  
  
|<span data-ttu-id="19a3f-106">Membre</span><span class="sxs-lookup"><span data-stu-id="19a3f-106">Member</span></span>|<span data-ttu-id="19a3f-107">Description</span><span class="sxs-lookup"><span data-stu-id="19a3f-107">Description</span></span>|  
|------------|-----------------|  
|`cbAssemblyInfo`|<span data-ttu-id="19a3f-108">Taille, en octets, de la structure.</span><span class="sxs-lookup"><span data-stu-id="19a3f-108">The size, in bytes, of the structure.</span></span> <span data-ttu-id="19a3f-109">Ce champ est réservé à une future extensibilité.</span><span class="sxs-lookup"><span data-stu-id="19a3f-109">This field is reserved for future extensibility.</span></span>|  
|`dwAssemblyFlags`|<span data-ttu-id="19a3f-110">Indicateurs qui indiquent les détails de l’installation de l’assembly.</span><span class="sxs-lookup"><span data-stu-id="19a3f-110">Flags that indicate installation details about the assembly.</span></span> <span data-ttu-id="19a3f-111">Les valeurs suivantes sont prises en charge :</span><span class="sxs-lookup"><span data-stu-id="19a3f-111">The following values are supported:</span></span><br /><br /> <span data-ttu-id="19a3f-112">-La valeur ASSEMBLYINFO_FLAG_INSTALLED, qui indique que l’assembly est installé.</span><span class="sxs-lookup"><span data-stu-id="19a3f-112">-   The ASSEMBLYINFO_FLAG_INSTALLED value, which indicates that the assembly is installed.</span></span> <span data-ttu-id="19a3f-113">La version actuelle du .NET Framework affecte toujours la valeur à `dwAssemblyFlags`.</span><span class="sxs-lookup"><span data-stu-id="19a3f-113">The current version of the .NET Framework always sets `dwAssemblyFlags` to this value.</span></span><br /><span data-ttu-id="19a3f-114">-La valeur ASSEMBLYINFO_FLAG_PAYLOADRESIDENT, qui indique que l’assembly est un résident de charge utile.</span><span class="sxs-lookup"><span data-stu-id="19a3f-114">-   The ASSEMBLYINFO_FLAG_PAYLOADRESIDENT value, which indicates that the assembly is a payload resident.</span></span> <span data-ttu-id="19a3f-115">La version actuelle de la .NET Framework ne définit jamais `dwAssemblyFlags` à cette valeur.</span><span class="sxs-lookup"><span data-stu-id="19a3f-115">The current version of the .NET Framework never sets `dwAssemblyFlags` to this value.</span></span>|  
|`uliAssemblySizeInKB`|<span data-ttu-id="19a3f-116">Taille totale, en kilo-octets, des fichiers que l’assembly contient.</span><span class="sxs-lookup"><span data-stu-id="19a3f-116">The total size, in kilobytes, of the files that the assembly contains.</span></span>|  
|`pszCurrentAssemblyPathBuf`|<span data-ttu-id="19a3f-117">Pointeur vers une mémoire tampon de chaîne qui contient le chemin d’accès actuel au fichier manifeste.</span><span class="sxs-lookup"><span data-stu-id="19a3f-117">A pointer to a string buffer that holds the current path to the manifest file.</span></span> <span data-ttu-id="19a3f-118">Le chemin d’accès doit se terminer par un caractère null.</span><span class="sxs-lookup"><span data-stu-id="19a3f-118">The path must end with a null character.</span></span>|  
|`cchBuf`|<span data-ttu-id="19a3f-119">Nombre de caractères larges, y compris la marque de fin null, que `pszCurrentAssemblyPathBuf` contient.</span><span class="sxs-lookup"><span data-stu-id="19a3f-119">The number of wide characters, including the null terminator, that `pszCurrentAssemblyPathBuf` contains.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="19a3f-120">spécifications</span><span class="sxs-lookup"><span data-stu-id="19a3f-120">Requirements</span></span>  
 <span data-ttu-id="19a3f-121">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="19a3f-121">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="19a3f-122">**En-tête :** Fusion. h</span><span class="sxs-lookup"><span data-stu-id="19a3f-122">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="19a3f-123">**Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="19a3f-123">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="19a3f-124">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="19a3f-124">See also</span></span>

- [<span data-ttu-id="19a3f-125">Structures de fusion</span><span class="sxs-lookup"><span data-stu-id="19a3f-125">Fusion Structures</span></span>](fusion-structures.md)
- [<span data-ttu-id="19a3f-126">Global Assembly Cache</span><span class="sxs-lookup"><span data-stu-id="19a3f-126">Global Assembly Cache</span></span>](../../app-domains/gac.md)
