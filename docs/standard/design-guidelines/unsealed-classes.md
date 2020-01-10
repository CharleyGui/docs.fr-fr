---
title: Classes unsealed
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- classes [.NET Framework], unsealed
- unsealed classes
- inheritance, classes
ms.assetid: 9a3bd505-90f5-4053-9f0d-3cf5fa3d3ebf
ms.openlocfilehash: 8a5f1142674f83b5ef77f9f7e7e3518afd475e7d
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75709008"
---
# <a name="unsealed-classes"></a>Classes unsealed
Les classes sealed ne peuvent pas être héritées de, et elles empêchent l’extensibilité. En revanche, les classes qui peuvent être héritées de sont appelées « classes non scellées ».  
  
 **✓ CONSIDER** à l’aide des classes unsealed sans aucune ajouté des membres virtuels ou protégés comme un excellent moyen de fournir un peu coûteux encore apprécié extensibilité à une infrastructure.  
  
 Les développeurs souhaitent souvent hériter de classes non scellées afin d’ajouter des membres de commodité tels que des constructeurs personnalisés, de nouvelles méthodes ou des surcharges de méthode. Par exemple, `System.Messaging.MessageQueue` est déscellée et permet ainsi aux utilisateurs de créer des files d’attente personnalisées qui se trouvent par défaut dans un chemin d’accès de file d’attente particulier ou d’ajouter des méthodes personnalisées qui simplifient l’API pour des scénarios spécifiques.  
  
 Les classes sont déscellées par défaut dans la plupart des langages de programmation, et il s’agit également de la valeur par défaut recommandée pour la plupart des classes dans les infrastructures. L’extensibilité offerte par les types non scellés est grandement appréciée par les utilisateurs du Framework et très peu coûteuse à fournir en raison des coûts de test relativement faibles associés aux types non scellés.  
  
 *Parties © 2005, 2009 Microsoft Corporation. Tous droits réservés.*  
  
 *Réimprimé avec l’autorisation de Pearson Education, Inc. et extrait de [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) par Krzysztof Cwalina et Brad Abrams, publié le 22 octobre 2008 par Addison-Wesley Professional dans le cadre de la série sur le développement Microsoft Windows.*  
  
## <a name="see-also"></a>Voir aussi

- [Règles de conception de .NET Framework](../../../docs/standard/design-guidelines/index.md)
- [Conception en vue de l’extensibilité](../../../docs/standard/design-guidelines/designing-for-extensibility.md)
- [Scellement](../../../docs/standard/design-guidelines/sealing.md)
