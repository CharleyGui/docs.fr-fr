---
title: Interopérabilité des exceptions
ms.date: 01/16/2020
ms.technology: dotnet-standard
helpviewer_keywords:
- unmanaged code, exceptions
- exceptions, unmanaged code
- interop, exceptions
- exceptions, interop
ms.openlocfilehash: 2aff71e97e1be0dbb584f4fe43c322cea86d2480
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76795174"
---
# <a name="working-with-interop-exceptions-in-unmanaged-code"></a>Utilisation d’exceptions d’interopérabilité dans du code non managé

L’interopérabilité des exceptions de code non managé est uniquement prise en charge sur les plateformes Windows. Des problèmes de portabilité se posent sur les plateformes non-Windows. Étant donné que l’ABI UNIX n’a aucune définition pour la gestion des exceptions, le code managé ne peut pas savoir comment les mécanismes d’exception fonctionnent en coulisses. Par conséquent, les exceptions peuvent aboutir à des comportements imprévisibles et des blocages.

## <a name="setjmplongjmp-behaviors"></a>Comportements setjmp/longjmp

L' `setjmp` interopérabilité `longjmp` avec les fonctions et C n’est pas prise en charge. Vous ne pouvez `longjmp` pas utiliser pour ignorer des frames managés.

Pour plus d’informations, consultez [la documentation longjmp](https://docs.microsoft.com/cpp/c-runtime-library/reference/longjmp).

## <a name="see-also"></a>Voir aussi

- [Exceptions](index.md)
- [Interopérabilité avec des bibliothèques natives](https://www.mono-project.com/docs/advanced/pinvoke/#runtime-exception-propagation)
