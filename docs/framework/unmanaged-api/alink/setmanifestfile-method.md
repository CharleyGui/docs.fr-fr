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
ms.openlocfilehash: a4518e93db887dbdc4397636479be8bf5a705c2d
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95733722"
---
# <a name="setmanifestfile-method"></a><span data-ttu-id="25c2e-102">SetManifestFile, méthode</span><span class="sxs-lookup"><span data-stu-id="25c2e-102">SetManifestFile Method</span></span>

<span data-ttu-id="25c2e-103">Vous permet de spécifier ou de réinitialiser le fichier manifeste que l’éditeur de liens utilise lorsqu’il crée l’assembly.</span><span class="sxs-lookup"><span data-stu-id="25c2e-103">Enables you to specify or reset the manifest file that the linker uses when it creates the assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="25c2e-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="25c2e-104">Syntax</span></span>  
  
```cpp  
HRESULT SetManifestFile(  
    LPCWSTR pszFile  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="25c2e-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="25c2e-105">Parameters</span></span>  

 `pszFile`  
  
 <span data-ttu-id="25c2e-106">Nom du fichier manifeste dont le contenu est placé dans l’objet blob de ressources Win32.</span><span class="sxs-lookup"><span data-stu-id="25c2e-106">The name of the manifest file whose contents are put into the Win32 resources blob.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="25c2e-107">Valeur renvoyée</span><span class="sxs-lookup"><span data-stu-id="25c2e-107">Return Value</span></span>  

 <span data-ttu-id="25c2e-108">Retourne S_OK si la méthode est réussie.</span><span class="sxs-lookup"><span data-stu-id="25c2e-108">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="25c2e-109">Remarques</span><span class="sxs-lookup"><span data-stu-id="25c2e-109">Remarks</span></span>  

 <span data-ttu-id="25c2e-110">Appelez-le avant de demander le Win32ResBlob.</span><span class="sxs-lookup"><span data-stu-id="25c2e-110">Call this before asking for the Win32ResBlob.</span></span> <span data-ttu-id="25c2e-111">La valeur du `pszFile` paramètre est le nom du fichier manifeste dont le contenu est lu et placé dans les ressources Win32 avec l’ID de RT_MANIFEST.</span><span class="sxs-lookup"><span data-stu-id="25c2e-111">The value of the `pszFile` parameter is the name of the manifest file whose contents are read and put in the Win32 resources with ID of RT_MANIFEST.</span></span> <span data-ttu-id="25c2e-112">En cas d’appel à l’aide d’un paramètre de valeur NULL, tout manifeste précédemment lu est effacé.</span><span class="sxs-lookup"><span data-stu-id="25c2e-112">When called by using a parameter of NULL, any previously read manifest is cleared.</span></span> <span data-ttu-id="25c2e-113">Cela permet à l’un de réinitialiser l’état de l’éditeur de liens à celui du temps d’initialisation.</span><span class="sxs-lookup"><span data-stu-id="25c2e-113">This enables one to reset the state of the linker to that of initialization time.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="25c2e-114">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="25c2e-114">Requirements</span></span>  

 <span data-ttu-id="25c2e-115">Requiert aLink. h</span><span class="sxs-lookup"><span data-stu-id="25c2e-115">Requires aLink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="25c2e-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="25c2e-116">See also</span></span>

- [<span data-ttu-id="25c2e-117">IALink3, interface</span><span class="sxs-lookup"><span data-stu-id="25c2e-117">IALink3 Interface</span></span>](ialink3-interface.md)
- [<span data-ttu-id="25c2e-118">API ALink</span><span class="sxs-lookup"><span data-stu-id="25c2e-118">ALink API</span></span>](index.md)
- [<span data-ttu-id="25c2e-119">IALink, interface</span><span class="sxs-lookup"><span data-stu-id="25c2e-119">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="25c2e-120">Al.exe (Assembly Linker)</span><span class="sxs-lookup"><span data-stu-id="25c2e-120">Al.exe (Assembly Linker)</span></span>](../../tools/al-exe-assembly-linker.md)
