---
title: Convention d’appel de DLL incorrecte
ms.date: 07/20/2015
f1_keywords:
- vbrID49
ms.assetid: 7c7def45-b0ab-450f-ad3f-4383dfd9aed7
ms.openlocfilehash: 0481bd5e4dfe7a24dff454d0754b519509fa967f
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90875734"
---
# <a name="bad-dll-calling-convention"></a>Convention d’appel de DLL incorrecte

Les arguments passés à une bibliothèque de liens dynamiques (DLL) doivent correspondre exactement à ceux attendus par la routine. Les conventions d’appel traitent le nombre, le type et l’ordre des arguments. Votre programme peut appeler une routine dans une DLL qui reçoit un type ou un nombre d’arguments incorrect.  
  
## <a name="to-correct-this-error"></a>Pour corriger cette erreur  
  
1. Assurez-vous que tous les types d’arguments correspondent à ceux spécifiés dans la déclaration de la routine que vous appelez.  
  
2. Assurez-vous que vous passez le même nombre d’arguments spécifiés dans la déclaration de la routine que vous appelez.  
  
3. Si la routine DLL attend des arguments par valeur, assurez-vous que `ByVal` est spécifié pour ces arguments dans la déclaration pour la routine.  
  
## <a name="see-also"></a>Voir aussi

- [Types d’erreurs](../../programming-guide/language-features/error-types.md)
- [Call (instruction)](../statements/call-statement.md)
- [Declare Statement](../statements/declare-statement.md)
