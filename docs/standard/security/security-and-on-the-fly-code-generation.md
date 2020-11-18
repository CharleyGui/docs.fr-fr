---
title: Sécurité et génération de code immédiate
description: La génération de code pour le compte d’un code de confiance moindre qui s’exécute à un niveau de confiance supérieur est un problème de sécurité, en particulier lorsqu’un appelant peut influencer la génération de code.
ms.date: 07/15/2020
helpviewer_keywords:
- code security, on-the-fly code generation
- on-the-fly code generation
- security [.NET], on-the-fly code generation
- secure coding, on-the-fly code generation
ms.assetid: 6d221724-bb21-4d76-90c3-0ee2a2e69be2
ms.openlocfilehash: c94da31f464a5272dd3f3c9f767a40ba7ad88a47
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/18/2020
ms.locfileid: "94824146"
---
# <a name="security-and-on-the-fly-code-generation"></a>Sécurité et génération de code immédiate

Certaines bibliothèques fonctionnent en générant du code et en l'exécutant afin d'effectuer certaines opérations pour l'appelant. Le problème de base est la génération de code pour le compte de code d'un niveau de confiance moindre et son exécution à un niveau de confiance supérieur. Ce problème se complique quand l'appelant peut influencer la génération du code ; vous devez donc vous assurer que seul du code que vous estimez sécurisé est généré.  
  
Vous devez toujours savoir précisément quel code vous générez. Cela signifie que vous devez avoir un contrôle strict sur toutes les valeurs que vous recevez d'un utilisateur, qu'il s'agisse de chaînes entourées de guillemets (qui devraient être échappées, car elles ne peuvent pas inclure d'éléments de code inattendus), d'identificateurs (dont la validité doit être vérifiée) ou de tout autre élément. Les identificateurs peuvent être dangereux, car vous pouvez modifier un assembly compilé pour que ses identificateurs contiennent des caractères étranges qui risquent de le bloquer (bien qu'il s'agisse rarement d'une faille en matière de sécurité).  
  
Nous vous recommandons de générer votre code à l'aide de l'émission de réflexion, qui vous aide souvent à éviter la plupart de ces problèmes.  
  
Pendant la compilation du code, examinez s'il est possible pour un programme nuisible de le modifier. Existe-t-il un laps de temps durant lequel du code nuisible peut changer du code source sur le disque avant sa lecture par le compilateur ou avant le chargement par votre code du fichier .dll ? Si c’est le cas, vous devez protéger le répertoire contenant ces fichiers à l’aide d’une liste de contrôle d’accès dans le fichier système, en fonction de la situation.  
  
## <a name="see-also"></a>Voir aussi

- [Instructions de codage sécurisé](secure-coding-guidelines.md)
- [Sécurité ASP.NET Core](/aspnet/core/security/)
