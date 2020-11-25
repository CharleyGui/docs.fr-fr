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
ms.openlocfilehash: a3a45a13073cf422064d28554a274e068db6f517
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95727508"
---
# <a name="lpoverlapped_completion_routine-function-pointer"></a>LPOVERLAPPED_COMPLETION_ROUTINE (pointeur fonction)

Pointe vers une fonction qui avertit l’hôte lorsqu’une e/s avec chevauchement (c’est-à-dire, asynchrone) sur un appareil est terminée.  
  
 Ce pointeur de fonction est déconseillé dans le .NET Framework 4.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
typedef VOID (*LPOVERLAPPED_COMPLETION_ROUTINE) (  
    [in] DWORD  dwErrorCode,  
    [in] DWORD  dwNumberOfBytesTransfered,  
    [in] LPVOID lpOverlapped  
);  
```  
  
## <a name="parameters"></a>Paramètres  

 `dwErrorCode`  
 dans Valeur qui est un code d’erreur si l’appareil a été fermé ; Sinon, cette valeur est égale à zéro.  
  
 La fermeture d’un appareil entraîne la fin immédiate de toutes les e/s en attente sur l’appareil.  
  
 `dwNumberOfBytesTransfered`  
 dans Nombre d’octets transférés par l’opération d’e/s.  
  
 `lpOverlapped`  
 dans Pointeur vers une structure qui contient des informations à utiliser pour terminer la requête d’e/s.  
  
## <a name="remarks"></a>Remarques  

 La fonction vers laquelle `LPOVERLAPPED_COMPLETION_ROUTINE` pointe est une fonction de rappel et doit être implémentée par le writer de l’application d’hébergement. La fonction de rappel permet à l’hôte de traiter la requête d’e/s terminée.  
  
## <a name="requirements"></a>Configuration requise  

 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** MSCorEE. h  
  
 **Bibliothèque :** MSCorWks.dll  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [Fonction d'hébergement du CLR déconseillées](deprecated-clr-hosting-functions.md)
