---
title: Activation du débogage JIT-attach
description: Activez le débogage d’attachement juste-à-temps (JIT) pour attacher un débogueur à un processus lorsque vous rencontrez des erreurs. Elle peut être déclenchée par certaines méthodes ou fonctions.
ms.date: 03/30/2017
helpviewer_keywords:
- JIT-attach debugging
- debugging [.NET Framework], JIT-attach debugging
ms.assetid: f91fc5f7-de5a-4f23-b6ac-f450e63c662e
ms.openlocfilehash: d1190c51a9cc6b5322ec832e0d35bc01dc855b12
ms.sourcegitcommit: a2c8b19e813a52b91facbb5d7e3c062c7188b457
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/26/2020
ms.locfileid: "85416042"
---
# <a name="enabling-jit-attach-debugging"></a>Activation du débogage JIT-attach
Débogage JIT-attach est l’expression utilisée pour décrire l’attachement d’un débogueur à un processus quand vous rencontrez des erreurs. Le débogage JIT-attach peut aussi être déclenché par des méthodes ou des fonctions spécifiques.  
  
 Le débogage JIT-attach est utilisé dans les conditions d’erreur suivantes :  
  
- Exceptions non gérées (dans le code natif et managé)  
  
- Méthode <xref:System.Environment.FailFast%2A?displayProperty=nameWithType> ou fonction [RaiseFailFastException](/windows/win32/api/errhandlingapi/nf-errhandlingapi-raisefailfastexception) (famille Windows 7)  
  
- Erreurs irrécupérables du runtime  
  
 Le débogage JIT-attach est également déclenché par des appels aux fonctions et méthodes suivantes :  
  
- Méthode<xref:System.Diagnostics.Debugger.Launch%2A?displayProperty=nameWithType> .  
  
- Méthode<xref:System.Diagnostics.Debugger.Break%2A?displayProperty=nameWithType> .  
  
- Fonction [DebugBreak](/windows/win32/api/debugapi/nf-debugapi-debugbreak) (Win32)  
  
 Avant le .NET Framework 4, les .NET Framework fournissaient des clés de Registre distinctes pour contrôler le comportement des débogueurs natifs et gérés. À partir de la .NET Framework 4, le contrôle est consolidé sous une clé de Registre unique : HKEY_LOCAL_MACHINE \SOFTWARE\Microsoft\Windows NT\Current Version\AeDebug. Les valeurs que vous pouvez définir pour cette clé déterminent si un débogueur est appelé et, dans l’affirmative, s’il est appelé avec une boîte de dialogue qui nécessite une interaction utilisateur. Pour plus d’informations sur la définition de cette clé de Registre, consultez [configuration du débogage automatique](/windows/win32/debug/configuring-automatic-debugging).  
  
## <a name="see-also"></a>Voir aussi

- [Débogage, traçage et profilage](index.md)
- [Simplification du débogage d’une image](making-an-image-easier-to-debug.md)
