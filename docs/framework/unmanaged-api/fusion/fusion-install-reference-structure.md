---
title: FUSION_INSTALL_REFERENCE, structure
ms.date: 03/30/2017
api_name:
- FUSION_INSTALL_REFERENCE
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- FUSION_INSTALL_REFERENCE
helpviewer_keywords:
- FUSION_INSTALL_REFERENCE structure [.NET Framework fusion]
ms.assetid: ae181ec8-36bf-4ed1-9a02-ca27d417c80b
topic_type:
- apiref
ms.openlocfilehash: d5ff08e62b94d7f164b103ae0535bb62e4e60aea
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95688807"
---
# <a name="fusion_install_reference-structure"></a><span data-ttu-id="f3980-102">FUSION_INSTALL_REFERENCE, structure</span><span class="sxs-lookup"><span data-stu-id="f3980-102">FUSION_INSTALL_REFERENCE Structure</span></span>

<span data-ttu-id="f3980-103">Représente une référence qu’une application effectue vers un assembly que l’application a installé dans le Global Assembly Cache.</span><span class="sxs-lookup"><span data-stu-id="f3980-103">Represents a reference that an application makes to an assembly that the application has installed in the global assembly cache.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f3980-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f3980-104">Syntax</span></span>  
  
```cpp  
typedef struct _FUSION_INSTALL_REFERENCE_ {  
    DWORD    cbSize,  
    DWORD    dwFlags,  
    GUID     guidScheme,  
    LPCWSTR  szIdentifier,  
    LPCWSTR  szNonCanonicalData  
} FUSION_INSTALL_REFERENCE, *LPFUSION_INSTALL_REFERENCE;  
```  
  
## <a name="members"></a><span data-ttu-id="f3980-105">Membres</span><span class="sxs-lookup"><span data-stu-id="f3980-105">Members</span></span>  
  
|<span data-ttu-id="f3980-106">Membre</span><span class="sxs-lookup"><span data-stu-id="f3980-106">Member</span></span>|<span data-ttu-id="f3980-107">Description</span><span class="sxs-lookup"><span data-stu-id="f3980-107">Description</span></span>|  
|------------|-----------------|  
|`cbSize`|<span data-ttu-id="f3980-108">Taille de la structure en octets.</span><span class="sxs-lookup"><span data-stu-id="f3980-108">The size of the structure in bytes.</span></span>|  
|`dwFlags`|<span data-ttu-id="f3980-109">Réservé pour une future extensibilité.</span><span class="sxs-lookup"><span data-stu-id="f3980-109">Reserved for future extensibility.</span></span> <span data-ttu-id="f3980-110">Cette valeur doit être 0 (zéro).</span><span class="sxs-lookup"><span data-stu-id="f3980-110">This value must be 0 (zero).</span></span>|  
|`guidScheme`|<span data-ttu-id="f3980-111">Entité qui ajoute la référence.</span><span class="sxs-lookup"><span data-stu-id="f3980-111">The entity that adds the reference.</span></span> <span data-ttu-id="f3980-112">Ce champ peut prendre l’une des valeurs suivantes :</span><span class="sxs-lookup"><span data-stu-id="f3980-112">This field can have one of the following values:</span></span><br /><br /> <span data-ttu-id="f3980-113">-FUSION_REFCOUNT_MSI_GUID : l’assembly est référencé par une application qui a été installée à l’aide de l’Microsoft Windows Installer.</span><span class="sxs-lookup"><span data-stu-id="f3980-113">-   FUSION_REFCOUNT_MSI_GUID: The assembly is referenced by an application that was installed using the Microsoft Windows Installer.</span></span> <span data-ttu-id="f3980-114">Le `szIdentifier` champ a la valeur `MSI` et le `szNonCanonicalData` champ a la valeur `Windows Installer` .</span><span class="sxs-lookup"><span data-stu-id="f3980-114">The `szIdentifier` field is set to `MSI`, and the `szNonCanonicalData` field is set to `Windows Installer`.</span></span> <span data-ttu-id="f3980-115">Ce schéma est utilisé pour les assemblys côte à côte Windows.</span><span class="sxs-lookup"><span data-stu-id="f3980-115">This scheme is used for Windows side-by-side assemblies.</span></span><br /><span data-ttu-id="f3980-116">-FUSION_REFCOUNT_UNINSTALL_SUBKEY_GUID : l’assembly est référencé par une application qui s’affiche dans l’interface **Ajout/suppression de programmes** .</span><span class="sxs-lookup"><span data-stu-id="f3980-116">-   FUSION_REFCOUNT_UNINSTALL_SUBKEY_GUID: The assembly is referenced by an application that appears in the **Add/Remove Programs** interface.</span></span> <span data-ttu-id="f3980-117">Le `szIdentifier` champ fournit le jeton qui inscrit l’application auprès de l’interface **Ajout/suppression de programmes** .</span><span class="sxs-lookup"><span data-stu-id="f3980-117">The `szIdentifier` field provides the token that registers the application with the **Add/Remove Programs** interface.</span></span><br /><span data-ttu-id="f3980-118">-FUSION_REFCOUNT_FILEPATH_GUID : l’assembly est référencé par une application qui est représentée par un fichier dans le système de fichiers.</span><span class="sxs-lookup"><span data-stu-id="f3980-118">-   FUSION_REFCOUNT_FILEPATH_GUID: The assembly is referenced by an application that is represented by a file in the file system.</span></span> <span data-ttu-id="f3980-119">Le `szIdentifier` champ fournit le chemin d’accès à ce fichier.</span><span class="sxs-lookup"><span data-stu-id="f3980-119">The `szIdentifier` field provides the path to this file.</span></span><br /><span data-ttu-id="f3980-120">-FUSION_REFCOUNT_OPAQUE_STRING_GUID : l’assembly est référencé par une application qui est représentée uniquement par une chaîne opaque.</span><span class="sxs-lookup"><span data-stu-id="f3980-120">-   FUSION_REFCOUNT_OPAQUE_STRING_GUID: The assembly is referenced by an application that is represented only by an opaque string.</span></span> <span data-ttu-id="f3980-121">Le `szIdentifier` champ fournit cette chaîne opaque.</span><span class="sxs-lookup"><span data-stu-id="f3980-121">The `szIdentifier` field provides this opaque string.</span></span> <span data-ttu-id="f3980-122">La Global Assembly Cache ne vérifie pas l’existence de références opaques lorsque vous supprimez cette valeur.</span><span class="sxs-lookup"><span data-stu-id="f3980-122">The global assembly cache does not check for the existence of opaque references when you remove this value.</span></span><br /><span data-ttu-id="f3980-123">-FUSION_REFCOUNT_OSINSTALL_GUID : cette valeur est réservée.</span><span class="sxs-lookup"><span data-stu-id="f3980-123">-   FUSION_REFCOUNT_OSINSTALL_GUID: This value is reserved.</span></span>|  
|`szIdentifier`|<span data-ttu-id="f3980-124">Chaîne unique qui identifie l’application qui a installé l’assembly dans le Global Assembly Cache.</span><span class="sxs-lookup"><span data-stu-id="f3980-124">A unique string that identifies the application that installed the assembly in the global assembly cache.</span></span> <span data-ttu-id="f3980-125">Sa valeur dépend de la valeur du `guidScheme` champ.</span><span class="sxs-lookup"><span data-stu-id="f3980-125">Its value depends upon the value of the `guidScheme` field.</span></span>|  
|`szNonCanonicalData`|<span data-ttu-id="f3980-126">Chaîne qui est comprise uniquement par l’entité qui ajoute la référence.</span><span class="sxs-lookup"><span data-stu-id="f3980-126">A string that is understood only by the entity that adds the reference.</span></span> <span data-ttu-id="f3980-127">Le Global Assembly Cache stocke cette chaîne, mais ne l’utilise pas.</span><span class="sxs-lookup"><span data-stu-id="f3980-127">The global assembly cache stores this string, but does not use it.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="f3980-128">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="f3980-128">Requirements</span></span>  

 <span data-ttu-id="f3980-129">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f3980-129">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f3980-130">**En-tête :** Fusion. h</span><span class="sxs-lookup"><span data-stu-id="f3980-130">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="f3980-131">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f3980-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f3980-132">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f3980-132">See also</span></span>

- [<span data-ttu-id="f3980-133">Structures de fusion</span><span class="sxs-lookup"><span data-stu-id="f3980-133">Fusion Structures</span></span>](fusion-structures.md)
- [<span data-ttu-id="f3980-134">Global Assembly Cache</span><span class="sxs-lookup"><span data-stu-id="f3980-134">Global Assembly Cache</span></span>](../../app-domains/gac.md)
