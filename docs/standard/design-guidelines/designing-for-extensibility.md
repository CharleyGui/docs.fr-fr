---
title: Conception en vue de l'extensibilité
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- extending class libraries
- extensibility with class libraries in .NET Framework
- class library design guidelines [.NET Framework], extensibility
- class library extensibility [.NET Framework]
ms.assetid: 1cdb8740-871a-456c-9bd9-db96ca8d79b3
ms.openlocfilehash: cd5db2d1e299df1b3d0f706ebc507e6855b72505
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75709463"
---
# <a name="designing-for-extensibility"></a>Conception en vue de l'extensibilité
Un aspect important de la conception d’une infrastructure consiste à s’assurer que l’extensibilité de l’infrastructure a été soigneusement étudiée. Cela nécessite que vous compreniez les coûts et les avantages associés à différents mécanismes d’extensibilité. Ce chapitre vous aide à choisir les mécanismes d’extensibilité (sous-classe, événements, membres virtuels, rappels, etc.) qui répondent le mieux aux besoins de votre infrastructure.  
  
 Il existe de nombreuses façons d’autoriser l’extensibilité dans les infrastructures. Ils vont de moins puissants mais moins coûteux à très puissants, mais onéreux. Pour toute exigence d’extensibilité donnée, vous devez choisir le mécanisme d’extensibilité le moins coûteux qui répond aux exigences. Gardez à l’esprit qu’il est généralement possible d’ajouter plus d’extensibilité ultérieurement, mais vous ne pouvez jamais le retirer sans introduire de modifications avec rupture.  
  
## <a name="in-this-section"></a>Dans cette section  
 [Classes unsealed](../../../docs/standard/design-guidelines/unsealed-classes.md)  
 [Membres protégés](../../../docs/standard/design-guidelines/protected-members.md)  
 [Événements et rappels](../../../docs/standard/design-guidelines/events-and-callbacks.md)  
 [Membres virtuels](../../../docs/standard/design-guidelines/virtual-members.md)  
 [Abstractions (types et interfaces abstraits)](../../../docs/standard/design-guidelines/abstractions-abstract-types-and-interfaces.md)  
 [Classes de base pour l’implémentation d’abstractions](../../../docs/standard/design-guidelines/base-classes-for-implementing-abstractions.md)  
 [Scellement](../../../docs/standard/design-guidelines/sealing.md)  
 *Parties © 2005, 2009 Microsoft Corporation. Tous droits réservés.*  
  
 *Réimprimé avec l’autorisation de Pearson Education, Inc. et extrait de [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) par Krzysztof Cwalina et Brad Abrams, publié le 22 octobre 2008 par Addison-Wesley Professional dans le cadre de la série sur le développement Microsoft Windows.*  
  
## <a name="see-also"></a>Voir aussi

- [Règles de conception de .NET Framework](../../../docs/standard/design-guidelines/index.md)
