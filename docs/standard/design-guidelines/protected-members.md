---
title: Membres protégés
ms.date: 10/22/2008
helpviewer_keywords:
- members [.NET Framework], protected
- protected members
- classes [.NET Framework], unsealed
- classes [.NET Framework], protected members
- unsealed classes
- customizing class behavior
ms.assetid: aa0b58ee-3956-494d-ab48-471ae5db8740
ms.openlocfilehash: a6f36ac4f994fdc3211cac619cc0b20f7b0335b1
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95730953"
---
# <a name="protected-members"></a>Membres protégés

Les membres protégés par eux-mêmes ne fournissent pas d’extensibilité, mais ils peuvent rendre l’extensibilité à l’aide d’une sous-classe plus puissante. Ils peuvent être utilisés pour exposer des options de personnalisation avancées sans compliquer inutilement l’interface publique principale.

 Les concepteurs de Framework doivent être vigilants avec les membres protégés, car le nom « protégé » peut avoir un sens de sécurité faux. Tout le monde peut sous-faire une classe non scellée et accéder à des membres protégés, de sorte que toutes les pratiques de codage défensives utilisées pour les membres publics s’appliquent aux membres protégés.

 ✔️ envisagez d’utiliser des membres protégés pour une personnalisation avancée.

 ✔️ Traitez les membres protégés dans des classes non scellées comme étant publics dans le cadre de la sécurité, de la documentation et de l’analyse de compatibilité.

 Tout le monde peut hériter d’une classe et accéder aux membres protégés.

 *Parties © 2005, 2009 Microsoft Corporation. Tous droits réservés.*

 *Réimprimé avec l’autorisation de Pearson Education, Inc. et extrait de [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) par Krzysztof Cwalina et Brad Abrams, publié le 22 octobre 2008 par Addison-Wesley Professional dans le cadre de la série sur le développement Microsoft Windows.*

## <a name="see-also"></a>Voir aussi

- [Directives de conception d’infrastructure](index.md)
- [Conception en vue de l’extensibilité](designing-for-extensibility.md)
