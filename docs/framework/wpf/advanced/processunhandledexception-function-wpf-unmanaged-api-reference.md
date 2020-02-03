---
title: Fonction ProcessUnhandledException-informations de référence sur les API non managées WPF
titleSuffix: ''
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- ProcessUnhandledException
api_location:
- PresentationHost_v0400.dll
ms.assetid: 495ce5f6-bb4d-4b30-807a-c3c35f1ca95c
ms.openlocfilehash: 757e5ac3aa2dc4c87b210b026998523bd82045c1
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76743922"
---
# <a name="processunhandledexception-function-wpf-unmanaged-api-reference"></a>ProcessUnhandledException, fonction (référence des API non managées WPF)
Cette API prend en charge l’infrastructure Windows Presentation Foundation (WPF) et n’est pas destinée à être utilisée directement à partir de votre code.  
  
 Utilisé par l’infrastructure Windows Presentation Foundation (WPF) pour la gestion des exceptions.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
void __stdcall ProcessUnhandledException(  
   __in_ecount(1) BSTR errorMsg  
)  
```  
  
## <a name="parameters"></a>Paramètres  
 errorMsg  
 Message d'erreur.  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** Consultez [.NET Framework Configuration système requise](../../get-started/system-requirements.md).  
  
 **DLL**  
  
 Dans les .NET Framework 3,0 et 3,5 : PresentationHostDLL. dll  
  
 Dans le .NET Framework 4 et versions ultérieures : PresentationHost_v0400. dll  
  
 **Version de .NET Framework :** [!INCLUDE[net_current_v30plus](../../../../includes/net-current-v30plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [Référence des API non managées WPF](wpf-unmanaged-api-reference.md)
