---
title: Activation du débogage JIT-attach
ms.date: 03/30/2017
helpviewer_keywords:
- JIT-attach debugging
- debugging [.NET Framework], JIT-attach debugging
ms.assetid: f91fc5f7-de5a-4f23-b6ac-f450e63c662e
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 005395beabd956767b59e0cebd563fe883f6fe53
ms.sourcegitcommit: 155012a8a826ee8ab6aa49b1b3a3b532e7b7d9bd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2019
ms.locfileid: "66489797"
---
# <a name="enabling-jit-attach-debugging"></a>Activation du débogage JIT-attach
Débogage JIT-attach est l’expression utilisée pour décrire l’attachement d’un débogueur à un processus quand vous rencontrez des erreurs. Le débogage JIT-attach peut aussi être déclenché par des méthodes ou des fonctions spécifiques.  
  
 Le débogage JIT-attach est utilisé dans les conditions d’erreur suivantes :  
  
- Exceptions non gérées (dans le code natif et managé)  
  
- Méthode <xref:System.Environment.FailFast%2A?displayProperty=nameWithType> ou fonction [RaiseFailFastException](https://go.microsoft.com/fwlink/?LinkId=182107) (famille Windows 7)  
  
- Erreurs irrécupérables du runtime  
  
 Le débogage JIT-attach est également déclenché par des appels aux fonctions et méthodes suivantes :  
  
- Méthode<xref:System.Diagnostics.Debugger.Launch%2A?displayProperty=nameWithType> .  
  
- Méthode<xref:System.Diagnostics.Debugger.Break%2A?displayProperty=nameWithType> .  
  
- Fonction [DebugBreak](https://go.microsoft.com/fwlink/?LinkId=182106) (Win32)  
  
 Avant le .NET Framework 4, .NET Framework n’offrait des clés de Registre distinctes pour contrôler le comportement des débogueurs natifs et managés. À compter de .NET Framework 4, le contrôle est consolidé sous une clé de Registre unique : HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows NT\Current Version\AeDebug. Les valeurs que vous pouvez définir pour cette clé déterminent si un débogueur est appelé et, dans l’affirmative, s’il est appelé avec une boîte de dialogue qui nécessite une interaction utilisateur. Pour plus d’informations sur la définition de cette clé de Registre, consultez [configuration du débogage automatique](https://go.microsoft.com/fwlink/?LinkId=181767).  
  
## <a name="see-also"></a>Voir aussi

- [Débogage, traçage et profilage](../../../docs/framework/debug-trace-profile/index.md)
- [Simplification du débogage d’une image](../../../docs/framework/debug-trace-profile/making-an-image-easier-to-debug.md)
