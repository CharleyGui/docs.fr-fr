---
title: Interopérabilité des exceptions
ms.date: 01/16/2020
helpviewer_keywords:
- unmanaged code, exceptions
- exceptions, unmanaged code
- interop, exceptions
- exceptions, interop
ms.openlocfilehash: db7c9943c298607aa91a4bd08ddc12bbafc872be
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/18/2020
ms.locfileid: "94830621"
---
# <a name="working-with-interop-exceptions-in-unmanaged-code"></a>Utilisation d’exceptions d’interopérabilité dans du code non managé

L’interopérabilité des exceptions de code non managé est uniquement prise en charge sur les plateformes Windows. Des problèmes de portabilité se posent sur les plateformes non-Windows. Étant donné que l’ABI UNIX n’a aucune définition pour la gestion des exceptions, le code managé ne peut pas savoir comment les mécanismes d’exception fonctionnent en coulisses. Par conséquent, les exceptions peuvent aboutir à des comportements imprévisibles et des blocages.

## <a name="setjmplongjmp-behaviors"></a>Comportements setjmp/longjmp

L’interopérabilité avec `setjmp` les `longjmp` fonctions et C n’est pas prise en charge. Vous ne pouvez pas utiliser `longjmp` pour ignorer des frames managés.

Pour plus d’informations, consultez [la documentation longjmp](/cpp/c-runtime-library/reference/longjmp).

## <a name="see-also"></a>Voir aussi

- [Exceptions](index.md)
- [Interopérabilité avec des bibliothèques natives](https://www.mono-project.com/docs/advanced/pinvoke/#runtime-exception-propagation)
