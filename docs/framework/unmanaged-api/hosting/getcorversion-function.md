---
title: GetCORVersion, fonction
ms.date: 03/30/2017
api_name:
- GetCORVersion
api_location:
- mscoree.dll
- mscoreei.dll
api_type:
- DLLExport
f1_keywords:
- GetCORVersion
helpviewer_keywords:
- GetCORVersion function [.NET Framework hosting]
ms.assetid: 2f09cd37-bf3a-4cc5-87b0-adc42a7eed31
topic_type:
- apiref
ms.openlocfilehash: 23d68e8e4bbd87779e3b49f0c40f5a5ab9f5124f
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83617215"
---
# <a name="getcorversion-function"></a><span data-ttu-id="17979-102">GetCORVersion, fonction</span><span class="sxs-lookup"><span data-stu-id="17979-102">GetCORVersion Function</span></span>
<span data-ttu-id="17979-103">Retourne le numéro de version du common language runtime (CLR) qui s’exécute dans le processus en cours.</span><span class="sxs-lookup"><span data-stu-id="17979-103">Returns the version number of the common language runtime (CLR) that is running in the current process.</span></span>  
  
 <span data-ttu-id="17979-104">Cette fonction a été dépréciée dans le .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="17979-104">This function has been deprecated in the .NET Framework 4.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="17979-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="17979-105">Syntax</span></span>  
  
```cpp  
HRESULT GetCORVersion (  
    [in] LPWSTR  pbuffer,  
    [in]  DWORD   cchBuffer,
    [out] DWORD*  dwlength  
);
```  
  
## <a name="parameters"></a><span data-ttu-id="17979-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="17979-106">Parameters</span></span>  
 `pbuffer`  
 <span data-ttu-id="17979-107">Pointeur vers une mémoire tampon dans laquelle le CLR retourne une chaîne spécifiant la version du runtime actuellement chargée dans le processus.</span><span class="sxs-lookup"><span data-stu-id="17979-107">A pointer to a buffer in which the CLR returns a string specifying the version of the runtime that is currently loaded into the process.</span></span> <span data-ttu-id="17979-108">La chaîne retournée prend la même forme que les chaînes passées à [CorBindToRuntimeEx](corbindtoruntimeex-function.md), par exemple, « v 1.0.1216 ».</span><span class="sxs-lookup"><span data-stu-id="17979-108">The returned string takes the same form as strings passed to [CorBindToRuntimeEx](corbindtoruntimeex-function.md), for example, "v1.0.1216".</span></span> <span data-ttu-id="17979-109">Si le runtime n’a pas encore été chargé dans le processus, la fonction retourne les informations de répertoire appropriées pour la version la plus récente du runtime installée sur l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="17979-109">If the runtime has not yet been loaded into the process, the function returns the appropriate directory information for the latest version of the runtime installed on the computer.</span></span>  
  
 `cchBuffer`  
 <span data-ttu-id="17979-110">Nombre de caractères `WCHAR` qui peuvent être contenus dans `pbuffer` .</span><span class="sxs-lookup"><span data-stu-id="17979-110">The number of characters (`WCHAR`s) that can be held in `pbuffer`.</span></span>  
  
 `dwLength`  
 <span data-ttu-id="17979-111">Pointeur vers le nombre de caractères réellement retournés dans `pbuffer` .</span><span class="sxs-lookup"><span data-stu-id="17979-111">A pointer to the number of characters actually returned in `pbuffer`.</span></span> <span data-ttu-id="17979-112">Si `pbuffer` est un pointeur null, le runtime retourne E_POINTER.</span><span class="sxs-lookup"><span data-stu-id="17979-112">If `pbuffer` is a null pointer, the runtime returns E_POINTER.</span></span> <span data-ttu-id="17979-113">Si le nombre de caractères est supérieur à la longueur de `pbuffer` , le runtime retourne ERROR_INSUFFICIENT_BUFFER.</span><span class="sxs-lookup"><span data-stu-id="17979-113">If the number of characters is greater then the length of `pbuffer` , the runtime returns ERROR_INSUFFICIENT_BUFFER.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="17979-114">Conditions requises</span><span class="sxs-lookup"><span data-stu-id="17979-114">Requirements</span></span>  
 <span data-ttu-id="17979-115">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="17979-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="17979-116">**En-tête :** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="17979-116">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="17979-117">**Bibliothèque :** MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="17979-117">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="17979-118">**Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="17979-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="17979-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="17979-119">See also</span></span>

- [<span data-ttu-id="17979-120">Fonction d'hébergement du CLR déconseillées</span><span class="sxs-lookup"><span data-stu-id="17979-120">Deprecated CLR Hosting Functions</span></span>](deprecated-clr-hosting-functions.md)
