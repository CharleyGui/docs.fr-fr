---
title: LPOVERLAPPED_COMPLETION_ROUTINE (pointeur fonction)
ms.date: 03/30/2017
api_name:
- LPOVERLAPPED_COMPLETION_ROUTINE
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- LPOVERLAPPED_COMPLETION_ROUTINE
helpviewer_keywords:
- LPOVERLAPPED_COMPLETION_ROUTINE function pointer [.NET Framework hosting]
ms.assetid: 5fb645d9-b818-401c-8c2c-c30d86de58ba
topic_type:
- apiref
ms.openlocfilehash: c0bdd9e59f5794dbb0d447dc2cc6cb682bfdf09f
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/27/2020
ms.locfileid: "84008480"
---
# <a name="lpoverlapped_completion_routine-function-pointer"></a><span data-ttu-id="f895d-102">LPOVERLAPPED_COMPLETION_ROUTINE (pointeur fonction)</span><span class="sxs-lookup"><span data-stu-id="f895d-102">LPOVERLAPPED_COMPLETION_ROUTINE Function Pointer</span></span>
<span data-ttu-id="f895d-103">Pointe vers une fonction qui avertit l’hôte lorsqu’une e/s avec chevauchement (c’est-à-dire, asynchrone) sur un appareil est terminée.</span><span class="sxs-lookup"><span data-stu-id="f895d-103">Points to a function that notifies the host when an overlapped (that is, asynchronous) I/O to a device has completed.</span></span>  
  
 <span data-ttu-id="f895d-104">Ce pointeur de fonction est déconseillé dans le .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="f895d-104">This function pointer has been deprecated in the .NET Framework 4.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f895d-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f895d-105">Syntax</span></span>  
  
```cpp  
typedef VOID (*LPOVERLAPPED_COMPLETION_ROUTINE) (  
    [in] DWORD  dwErrorCode,  
    [in] DWORD  dwNumberOfBytesTransfered,  
    [in] LPVOID lpOverlapped  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f895d-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="f895d-106">Parameters</span></span>  
 `dwErrorCode`  
 <span data-ttu-id="f895d-107">dans Valeur qui est un code d’erreur si l’appareil a été fermé ; Sinon, cette valeur est égale à zéro.</span><span class="sxs-lookup"><span data-stu-id="f895d-107">[in] A value that is an error code if the device has been closed; otherwise, this value is zero.</span></span>  
  
 <span data-ttu-id="f895d-108">La fermeture d’un appareil entraîne la fin immédiate de toutes les e/s en attente sur l’appareil.</span><span class="sxs-lookup"><span data-stu-id="f895d-108">Closing a device causes all pending I/O to the device to be completed immediately.</span></span>  
  
 `dwNumberOfBytesTransfered`  
 <span data-ttu-id="f895d-109">dans Nombre d’octets transférés par l’opération d’e/s.</span><span class="sxs-lookup"><span data-stu-id="f895d-109">[in] The number of bytes transferred by the I/O operation.</span></span>  
  
 `lpOverlapped`  
 <span data-ttu-id="f895d-110">dans Pointeur vers une structure qui contient des informations à utiliser pour terminer la requête d’e/s.</span><span class="sxs-lookup"><span data-stu-id="f895d-110">[in] A pointer to a structure that contains information to be used to complete the I/O request.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f895d-111">Remarques</span><span class="sxs-lookup"><span data-stu-id="f895d-111">Remarks</span></span>  
 <span data-ttu-id="f895d-112">La fonction vers laquelle `LPOVERLAPPED_COMPLETION_ROUTINE` pointe est une fonction de rappel et doit être implémentée par le writer de l’application d’hébergement.</span><span class="sxs-lookup"><span data-stu-id="f895d-112">The function to which `LPOVERLAPPED_COMPLETION_ROUTINE` points is a callback function and must be implemented by the writer of the hosting application.</span></span> <span data-ttu-id="f895d-113">La fonction de rappel permet à l’hôte de traiter la requête d’e/s terminée.</span><span class="sxs-lookup"><span data-stu-id="f895d-113">The callback function allows the host to process the completed I/O request.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f895d-114">Spécifications</span><span class="sxs-lookup"><span data-stu-id="f895d-114">Requirements</span></span>  
 <span data-ttu-id="f895d-115">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f895d-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f895d-116">**En-tête :** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="f895d-116">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="f895d-117">**Bibliothèque :** MSCorWks. dll</span><span class="sxs-lookup"><span data-stu-id="f895d-117">**Library:** MSCorWks.dll</span></span>  
  
 <span data-ttu-id="f895d-118">**Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f895d-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f895d-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f895d-119">See also</span></span>

- [<span data-ttu-id="f895d-120">Fonction d'hébergement du CLR déconseillées</span><span class="sxs-lookup"><span data-stu-id="f895d-120">Deprecated CLR Hosting Functions</span></span>](deprecated-clr-hosting-functions.md)
