---
title: Consommation de fonctions DLL non managées
ms.date: 03/30/2017
helpviewer_keywords:
- unmanaged functions, calling
- COM interop, DLL functions
- unmanaged functions
- COM interop, platform invoke
- platform invoke, about platform invoke
- DLL functions, consuming unmanaged
- interoperation with unmanaged code, DLL functions
- interoperation with unmanaged code, platform invoke
- platform invoke
- DLL functions
ms.assetid: eca7606e-ebfb-4f47-b8d9-289903fdc045
ms.openlocfilehash: 7ec1f129dcc19300dd5a4e7c5e627d9e0edf29a1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79399972"
---
# <a name="consuming-unmanaged-dll-functions"></a>Consommation de fonctions DLL non managées
L’appel de code non managé est un service qui permet au code managé d’appeler des fonctions non managées implémentées dans des bibliothèques de liens dynamiques (DLL), telles que celles de l’API Windows. Il localise et appelle une fonction exportée, puis marshale ses arguments (entiers, chaînes, tableaux, structures, etc) au-delà des limites d’interopérabilité, selon les besoins.  
  
 Cette section présente les tâches liées à la consommation de fonctions DLL non managées et fournit plus d’informations sur l’appel de code non managé (PInvoke). Outre les tâches suivantes, cette section comprend des remarques d'ordre général, ainsi qu'un lien vers des informations supplémentaires et des exemples.  
  
#### <a name="to-consume-exported-dll-functions"></a>Pour consommer des fonctions DLL exportées  
  
1. [Identifiez les fonctions dans les DLL](identifying-functions-in-dlls.md).  
  
     Vous devez au minimum spécifier le nom de la fonction et le nom de la DLL qui la contient.  
  
2. [Créez une classe censée contenir des fonctions DLL](creating-a-class-to-hold-dll-functions.md).  
  
     Vous pouvez utiliser une classe existante, créer une classe pour chaque fonction non managée ou bien créer une classe contenant un ensemble de fonctions non managées associées.  
  
3. [Créez des prototypes dans du code managé](creating-prototypes-in-managed-code.md).  
  
     [Visual Basic] Utilisez l’instruction **Declare** avec les mots clés **Function** et **Lib**. Dans certains cas rares, vous pouvez utiliser **DllImportAttribute** avec les mots clés **Shared Function**. Ces cas sont expliqués plus loin dans cette section.  
  
     [C] Utilisez le **DllImportAttribute** pour identifier le DLL et la fonction. Marquez la méthode avec les modificateurs **static** et **extern**.  
  
     [C++] Utilisez **DllImportAttribute** pour identifier la DLL et la fonction. Marquez la méthode ou la fonction wrapper avec **extern "C"**.  
  
4. [Appelez une fonction DLL](calling-a-dll-function.md).  
  
     Appelez la méthode sur votre classe managée comme vous le feriez pour toute autre méthode managée. Le [passage de structures](passing-structures.md) et l’[implémentation de fonctions de rappel](callback-functions.md) sont des cas spéciaux.  
  
 Pour afficher des exemples montrant comment construire des déclarations .NET à utiliser avec l’appel de code non managé, consultez [Marshaling de données à l’aide de l’appel de code non managé](marshaling-data-with-platform-invoke.md).  
  
## <a name="a-closer-look-at-platform-invoke"></a>Présentation détaillée de l'appel de code non managé  
 L’appel de code non managé s’appuie sur les métadonnées pour localiser les fonctions exportées et marshaler leurs arguments au moment de l’exécution. L'illustration ci-dessous montre ce processus.  
  
 ![Diagramme illustrant un appel de code non managé.](./media/consuming-unmanaged-dll-functions/platform-invoke-call.gif)  
  
 Quand un appel de code non managé appelle une fonction non managée, il exécute les actions suivantes :  
  
1. Il recherche la DLL contenant la fonction.  
  
2. Il charge la DLL dans la mémoire.  
  
3. Il localise l'adresse de la fonction dans la mémoire et transmet ses arguments sur la pile, en marshalant les données selon les besoins.  
  
    > [!NOTE]
    > La localisation et le chargement de la DLL, et la localisation de l'adresse de la fonction dans la mémoire, se produisent uniquement lors du premier appel à la fonction.  
  
4. Il cède le contrôle à la fonction non managée.  
  
 L'appel de code non managé lève des exceptions générées par la fonction non managée pour l'appelant managé.

## <a name="see-also"></a>Voir aussi

- [Interopération avec code non traité](index.md)
- [Exemples d’appel de code non managé](platform-invoke-examples.md)
- [Marshaling d’interopérabilité](interop-marshaling.md)
