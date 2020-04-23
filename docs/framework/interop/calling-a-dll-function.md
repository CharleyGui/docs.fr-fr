---
title: Appel à une fonction DLL
ms.date: 03/30/2017
helpviewer_keywords:
- unmanaged functions, calling
- unmanaged functions
- COM interop, platform invoke
- platform invoke, calling unmanaged functions
- interoperation with unmanaged code, platform invoke
- DLL functions
ms.assetid: 113646de-7ea0-4f0e-8df0-c46dab3e8733
ms.openlocfilehash: 14589544e05f6c59f4f58f7723fef40e75af9823
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73123717"
---
# <a name="calling-a-dll-function"></a>Appel à une fonction DLL
Même si l’appel à des fonctions DLL non managées est quasiment identique à l’appel à un autre code managé, certaines différences peuvent rendre les fonctions DLL déconcertantes au départ. Cette section présente des rubriques qui décrivent certaines questions relatives à des appels peu courants.  
  
 Les structures qui sont retournées par les appels de code non managé doivent être des types de données avec la même représentation dans le code managé et non managé. Ces types sont appelés *types blittables* parce qu’ils ne nécessitent pas de conversion (consultez [Types blittables et non blittables](blittable-and-non-blittable-types.md)). Pour appeler une fonction qui a une structure non blittable comme type de retour, vous pouvez définir un type d’assistance blittable de la même taille que le type non blittable et convertir les données après le retour de la fonction.  
  
## <a name="in-this-section"></a>Dans cette section  
 [Passage de structures](passing-structures.md)  
 Identifie les questions de passage de structures de données avec une disposition prédéfinie.  
  
 [Fonctions de rappel](callback-functions.md)  
 Fournit des informations de base sur les fonctions de rappel.  
  
 [Comment : implémenter des fonctions de rappel](how-to-implement-callback-functions.md)  
 Décrit comment implémenter des fonctions de rappel dans du code managé.  
  
## <a name="related-sections"></a>Sections connexes  
 [Consommation de fonctions DLL non managées](consuming-unmanaged-dll-functions.md)  
 Décrit comment appeler des fonctions DLL non managées à l’aide de l’appel de code non managé.  
  
 [Marshaling de données à l’aide de l’appel de code managé](marshaling-data-with-platform-invoke.md)  
 Décrit comment déclarer des paramètres de méthode et passer des arguments à des fonctions exportées par des bibliothèques non managées.
