---
title: Noms d'assemblys et de DLL
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- names [.NET Framework], DLLs
- names [.NET Framework], assemblies
- assemblies [.NET Framework], names
- DLLs, names
ms.assetid: e800b610-31b4-4949-9c14-cb60e9f254be
ms.openlocfilehash: 138ae8154b0d10fb813f0c98ceb7c58a2471b780
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84291953"
---
# <a name="names-of-assemblies-and-dlls"></a>Noms d'assemblys et de DLL
Un assembly est l’unité de déploiement et d’identité des programmes de code managé. Bien que les assemblys puissent couvrir un ou plusieurs fichiers, en général un assembly mappe un à un avec une DLL. Par conséquent, cette section décrit uniquement les conventions d’affectation de noms de DLL, qui peuvent alors être mappées aux conventions d’affectation de noms d’assembly.

 ✔️ Choisissez des noms pour vos dll d’assembly qui suggèrent de grands blocs de fonctionnalités, tels que System. Data.

 Les noms d’assemblys et de DLL ne doivent pas nécessairement correspondre aux noms d’espaces de noms, mais il est raisonnable de suivre le nom de l’espace de noms lors de l’attribution de noms aux assemblys. Une bonne règle empirique consiste à nommer la DLL en fonction du préfixe commun des espaces de noms contenus dans l’assembly. Par exemple, un assembly avec deux espaces de noms, `MyCompany.MyTechnology.FirstFeature` et `MyCompany.MyTechnology.SecondFeature` , peut être appelé `MyCompany.MyTechnology.dll` .

 ✔️ ENVISAGER de nommer les dll selon le modèle suivant :

 `<Company>.<Component>.dll`

 où `<Component>` contient une ou plusieurs clauses séparées par des points. Par exemple :

 `Litware.Controls.dll`.

 *Parties © 2005, 2009 Microsoft Corporation. Tous droits réservés.*

 *Réimprimé avec l’autorisation de Pearson Education, Inc. et extrait de [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) par Krzysztof Cwalina et Brad Abrams, publié le 22 octobre 2008 par Addison-Wesley Professional dans le cadre de la série sur le développement Microsoft Windows.*

## <a name="see-also"></a>Voir aussi

- [Directives de conception d’infrastructure](index.md)
- [Instructions d’affectation de noms](naming-guidelines.md)
