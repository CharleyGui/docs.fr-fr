---
title: SetManifestFile, méthode
ms.date: 03/30/2017
api_name:
- IALink3.SetManifestFile
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- SetManifestFile
helpviewer_keywords:
- SetManifestFile method
ms.assetid: 1b33de4c-19cb-4a36-a93f-8675b2a36d58
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: b293c30060107d18c6b609efc82c4128a73cc1c7
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70787206"
---
# <a name="setmanifestfile-method"></a><span data-ttu-id="c7d48-102">SetManifestFile, méthode</span><span class="sxs-lookup"><span data-stu-id="c7d48-102">SetManifestFile Method</span></span>
<span data-ttu-id="c7d48-103">Vous permet de spécifier ou de réinitialiser le fichier manifeste que l’éditeur de liens utilise lorsqu’il crée l’assembly.</span><span class="sxs-lookup"><span data-stu-id="c7d48-103">Enables you to specify or reset the manifest file that the linker uses when it creates the assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c7d48-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c7d48-104">Syntax</span></span>  
  
```cpp  
HRESULT SetManifestFile(  
    LPCWSTR pszFile  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="c7d48-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="c7d48-105">Parameters</span></span>  
 `pszFile`  
  
 <span data-ttu-id="c7d48-106">Nom du fichier manifeste dont le contenu est placé dans l’objet blob de ressources Win32.</span><span class="sxs-lookup"><span data-stu-id="c7d48-106">The name of the manifest file whose contents are put into the Win32 resources blob.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c7d48-107">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="c7d48-107">Return Value</span></span>  
 <span data-ttu-id="c7d48-108">Retourne S_OK si la méthode est réussie.</span><span class="sxs-lookup"><span data-stu-id="c7d48-108">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c7d48-109">Notes</span><span class="sxs-lookup"><span data-stu-id="c7d48-109">Remarks</span></span>  
 <span data-ttu-id="c7d48-110">Appelez-le avant de demander le Win32ResBlob.</span><span class="sxs-lookup"><span data-stu-id="c7d48-110">Call this before asking for the Win32ResBlob.</span></span> <span data-ttu-id="c7d48-111">La valeur du `pszFile` paramètre est le nom du fichier manifeste dont le contenu est lu et placé dans les ressources Win32 avec l’ID RT_MANIFEST.</span><span class="sxs-lookup"><span data-stu-id="c7d48-111">The value of the `pszFile` parameter is the name of the manifest file whose contents are read and put in the Win32 resources with ID of RT_MANIFEST.</span></span> <span data-ttu-id="c7d48-112">En cas d’appel à l’aide d’un paramètre de valeur NULL, tout manifeste précédemment lu est effacé.</span><span class="sxs-lookup"><span data-stu-id="c7d48-112">When called by using a parameter of NULL, any previously read manifest is cleared.</span></span> <span data-ttu-id="c7d48-113">Cela permet à l’un de réinitialiser l’état de l’éditeur de liens à celui du temps d’initialisation.</span><span class="sxs-lookup"><span data-stu-id="c7d48-113">This enables one to reset the state of the linker to that of initialization time.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c7d48-114">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="c7d48-114">Requirements</span></span>  
 <span data-ttu-id="c7d48-115">Requiert aLink. h</span><span class="sxs-lookup"><span data-stu-id="c7d48-115">Requires aLink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c7d48-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c7d48-116">See also</span></span>

- [<span data-ttu-id="c7d48-117">IALink3, interface</span><span class="sxs-lookup"><span data-stu-id="c7d48-117">IALink3 Interface</span></span>](ialink3-interface.md)
- [<span data-ttu-id="c7d48-118">API ALink</span><span class="sxs-lookup"><span data-stu-id="c7d48-118">ALink API</span></span>](index.md)
- [<span data-ttu-id="c7d48-119">IALink, interface</span><span class="sxs-lookup"><span data-stu-id="c7d48-119">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="c7d48-120">Al.exe (Assembly Linker)</span><span class="sxs-lookup"><span data-stu-id="c7d48-120">Al.exe (Assembly Linker)</span></span>](../../tools/al-exe-assembly-linker.md)
