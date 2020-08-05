---
title: Sécurisation des données d'état
description: Déclarez les données d’État comme des variables privées ou internes pour limiter l’accès à celle-ci. Ces données sont toujours accessibles via la réflexion, la sérialisation et le débogage.
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- security [.NET], state data
- code security, state data
- secure coding, state data
- state data security
ms.assetid: 12671309-2877-43fe-a3df-6863507e712d
ms.openlocfilehash: 73bd0ace28e5b9661cc86d6749ceef9aa4c9ac92
ms.sourcegitcommit: b7a8b09828bab4e90f66af8d495ecd7024c45042
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87557123"
---
# <a name="securing-state-data"></a>Sécurisation des données d'état

Les applications qui gèrent des données sensibles ou participent aux processus décisionnels de sécurité doivent conserver le contrôle des données. Elles doivent absolument empêcher tout code potentiellement malveillant d’accéder directement aux données. La meilleure façon de protéger les données en mémoire est de les déclarer en tant que variables privées ou internes (avec une portée limitée au même assembly). Toutefois, même ces données sont soumises à un accès dont vous devez avoir conscience :  
  
- À l’aide de mécanismes de réflexion, du code hautement fiable pouvant référencer votre objet est susceptible d’obtenir et de définir des membres privés.  
  
- En s’appuyant sur la sérialisation, le code hautement fiable peut efficacement obtenir et définir des membres privés, s’il peut accéder aux données correspondantes de la forme sérialisée de l’objet.  
  
- En mode de débogage, ces données peuvent être lues.  
  
 Assurez-vous qu’aucune de vos méthodes ou propriétés n’expose involontairement ces valeurs.  
  
## <a name="see-also"></a>Voir aussi

- [Instructions de codage sécurisé](secure-coding-guidelines.md)
- [Sécurité ASP.NET Core](/aspnet/core/security/)
