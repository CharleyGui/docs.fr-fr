---
title: Fonction ForwardTranslateAccelerator-informations de référence sur les API non managées WPF
titleSuffix: ''
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- ForwardTranslateAccelerator
api_location:
- PresentationHost_v0400.dll
ms.assetid: fff47a86-9d9f-4176-9530-10e1876e393f
ms.openlocfilehash: f6e8208ffe2c186234f30f31e346ca6b1d0be4c0
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76747036"
---
# <a name="forwardtranslateaccelerator-function-wpf-unmanaged-api-reference"></a>ForwardTranslateAccelerator, fonction (référence des API non managées WPF)
Cette API prend en charge l’infrastructure Windows Presentation Foundation (WPF) et n’est pas destinée à être utilisée directement à partir de votre code.  
  
 Utilisé par l’infrastructure Windows Presentation Foundation (WPF) pour la gestion de Windows.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT ForwardTranslateAccelerator(  
   MSG* pMsg,   
   VARIANT_BOOL appUnhandled  
)  
```  
  
## <a name="parameters"></a>Paramètres  
 pMsg  
 Pointeur vers un message.  
  
 appUnhandled  
 `true` lorsque l’application a déjà eu la possibilité de gérer le message d’entrée, mais ne l’a pas gérée ; Sinon, `false`.  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** Consultez [.NET Framework Configuration système requise](../../get-started/system-requirements.md).  
  
 **DLL**  
  
 Dans les .NET Framework 3,0 et 3,5 : PresentationHostDLL. dll  
  
 Dans le .NET Framework 4 et versions ultérieures : PresentationHost_v0400. dll  
  
 **Version de .NET Framework :** [!INCLUDE[net_current_v30plus](../../../../includes/net-current-v30plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [Référence des API non managées WPF](wpf-unmanaged-api-reference.md)
