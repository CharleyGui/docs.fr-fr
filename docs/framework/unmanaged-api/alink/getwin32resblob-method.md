---
title: GetWin32ResBlob, méthode
ms.date: 03/30/2017
api_name:
- IALink.GetWin32ResBlob
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- GetWin32ResBlob
helpviewer_keywords:
- GetWin32ResBlob method
ms.assetid: 36997e04-f9f6-4254-a041-6767ac6c51d9
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: b26f08548ac964fae2f4d64db50167add327eb2d
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70777371"
---
# <a name="getwin32resblob-method"></a><span data-ttu-id="581c3-102">GetWin32ResBlob, méthode</span><span class="sxs-lookup"><span data-stu-id="581c3-102">GetWin32ResBlob Method</span></span>
<span data-ttu-id="581c3-103">Récupère l’objet blob de ressources Win32.</span><span class="sxs-lookup"><span data-stu-id="581c3-103">Retrieves Win32 resource blob.</span></span> <span data-ttu-id="581c3-104">Appelez cette méthode après avoir défini les options d’assembly.</span><span class="sxs-lookup"><span data-stu-id="581c3-104">Call this method after setting assembly options.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="581c3-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="581c3-105">Syntax</span></span>  
  
```cpp  
HRESULT GetWin32ResBlob(  
    mdAssembly    AssemblyID,  
    mdToken       FileToken,  
    BOOL          fDll,  
    LPCWSTR       pszIconFile,  
    const void**  ppResBlob,  
    DWORD*        pcbResBlob  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="581c3-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="581c3-106">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="581c3-107">ID de l’assembly.</span><span class="sxs-lookup"><span data-stu-id="581c3-107">ID of the assembly.</span></span>  
  
 `FileToken`  
 <span data-ttu-id="581c3-108">Jeton de fichier utilisé pour récupérer le nom de fichier à utiliser lors de la construction de la ressource de version Win32</span><span class="sxs-lookup"><span data-stu-id="581c3-108">File token used to retrieve the filename to be used when constructing the Win32 Version resource</span></span>  
  
 `fDll`  
 <span data-ttu-id="581c3-109">TRUE si le fichier est une DLL, false pour un EXE.</span><span class="sxs-lookup"><span data-stu-id="581c3-109">TRUE if file is a DLL, false for an EXE.</span></span>  
  
 `pszIconFile`  
 <span data-ttu-id="581c3-110">Icône facultative à insérer dans l’objet blob de ressources.</span><span class="sxs-lookup"><span data-stu-id="581c3-110">Optional icon to insert into the resource blob.</span></span>  
  
 `ppResBlob`  
 <span data-ttu-id="581c3-111">Reçoit l’objet blob de ressources.</span><span class="sxs-lookup"><span data-stu-id="581c3-111">Receives the resource blob.</span></span>  
  
 `pcbResBlob`  
 <span data-ttu-id="581c3-112">Reçoit la taille de l’objet BLOB.</span><span class="sxs-lookup"><span data-stu-id="581c3-112">Receives the size of the blob.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="581c3-113">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="581c3-113">Return Value</span></span>  
 <span data-ttu-id="581c3-114">Retourne S_OK si la méthode est réussie.</span><span class="sxs-lookup"><span data-stu-id="581c3-114">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="581c3-115">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="581c3-115">Requirements</span></span>  
 <span data-ttu-id="581c3-116">Requiert ALink. h</span><span class="sxs-lookup"><span data-stu-id="581c3-116">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="581c3-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="581c3-117">See also</span></span>

- [<span data-ttu-id="581c3-118">IALink, interface</span><span class="sxs-lookup"><span data-stu-id="581c3-118">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="581c3-119">IALink2, interface</span><span class="sxs-lookup"><span data-stu-id="581c3-119">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="581c3-120">API ALink</span><span class="sxs-lookup"><span data-stu-id="581c3-120">ALink API</span></span>](index.md)
