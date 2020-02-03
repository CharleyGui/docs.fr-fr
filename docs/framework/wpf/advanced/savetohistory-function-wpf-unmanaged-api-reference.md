---
title: Fonction SaveToHistory-informations de référence sur les API non managées WPF
titleSuffix: ''
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- SaveToHistory
api_location:
- PresentationHost_v0400.dll
ms.assetid: 6dd101a3-44ad-4143-b228-772156f9b8ff
ms.openlocfilehash: 7337e5dc23a3dce5de8270902bce228c49bc6edb
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76731751"
---
# <a name="savetohistory-function-wpf-unmanaged-api-reference"></a>SaveToHistory, fonction (référence des API non managées WPF)
Cette API prend en charge l’infrastructure Windows Presentation Foundation (WPF) et n’est pas destinée à être utilisée directement à partir de votre code.  
  
 Utilisé par l’infrastructure Windows Presentation Foundation (WPF) pour la gestion de Windows.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT SaveToHistory(  
   __in_ecount(1) IStream* pHistoryStream  
)  
```  
  
## <a name="parameters"></a>Paramètres  
 pHistoryStream  
 Pointeur vers le flux d’historique.  
  
## <a name="requirements"></a>Configuration requise  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** Consultez [.NET Framework Configuration système requise](../../get-started/system-requirements.md).  
  
 **DLL**  
  
 Dans les .NET Framework 3,0 et 3,5 : PresentationHostDLL. dll  
  
 Dans le .NET Framework 4 et versions ultérieures : PresentationHost_v0400. dll  
  
 **Version de .NET Framework :** [!INCLUDE[net_current_v30plus](../../../../includes/net-current-v30plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [Référence des API non managées WPF](wpf-unmanaged-api-reference.md)
