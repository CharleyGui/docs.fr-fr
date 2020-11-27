---
title: Fonctions de rappel
description: En savoir plus sur les fonctions de rappel, qui sont du code avec une application managée qui permet à une fonction DLL non managée d’effectuer une tâche.
ms.date: 03/30/2017
helpviewer_keywords:
- callback function
- platform invoke, calling unmanaged functions
ms.assetid: c0aa8533-3b3b-42e8-9f60-84919793098c
ms.openlocfilehash: 659f384f7bfc3a2326a40a9536c977d7c41ab076
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96283157"
---
# <a name="callback-functions"></a>Fonctions de rappel

Une fonction de rappel désigne du code figurant dans une application managée qui permet à une fonction DLL non managée d’effectuer une tâche. Les appels à une fonction de rappel sont indirectement passés depuis une application managée via une fonction DLL avant de revenir à l’implémentation managée. Certaines des nombreuses fonctions DLL appelées à l’aide de l’appel de code non managé nécessitent une fonction de rappel dans du code managé pour fonctionner correctement.  
  
 Pour appeler la plupart des fonctions DLL à partir d’un code managé, il vous suffit de créer une définition managée de la fonction, puis de l’appeler. La procédure est simple.  
  
 L’utilisation d’une fonction DLL nécessitant une fonction de rappel implique des étapes supplémentaires. Vous devez d’abord déterminer si la fonction nécessite un rappel en consultant la documentation sur la fonction. Vous devez ensuite créer la fonction de rappel dans votre application managée. Vous devez enfin appeler la fonction DLL, en passant un pointeur vers la fonction de rappel sous la forme d’un argument.

 L’illustration suivante résume la fonction de rappel et les étapes de l’implémentation :  
  
 ![Diagramme illustrant le processus de rappel de l’appel de code non managé.](./media/callback-functions/platform-invoke-callback-process.gif)  
  
 Les fonctions de rappel sont idéales dans les cas où une tâche est effectuée à maintes reprises. Elles sont aussi fréquemment utilisées avec des fonctions d’énumération, comme **EnumFontFamilies**, **EnumPrinters** et **EnumWindows**, dans l’interface API Windows. La fonction **EnumWindows** se décline dans toutes les fenêtres existantes de votre ordinateur ; dans chacune, elle appelle la fonction de rappel pour exécuter une tâche. Pour obtenir des instructions et un exemple, consultez [Guide pratique pour implémenter des fonctions de rappel](how-to-implement-callback-functions.md).  
  
## <a name="see-also"></a>Voir aussi

- [Procédure : implémenter des fonctions de rappel](how-to-implement-callback-functions.md)
- [Appel à une fonction DLL](calling-a-dll-function.md)
