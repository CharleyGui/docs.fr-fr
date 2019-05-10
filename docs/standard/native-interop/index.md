---
title: Interopérabilité native - .NET
description: Découvrez comment interagir avec les composants natifs dans .NET.
author: jkoritzinsky
ms.author: jekoritz
ms.date: 01/18/2019
ms.openlocfilehash: b01ea9c17db6da32755309d9c1c2359cecaa1155
ms.sourcegitcommit: ca2ca60e6f5ea327f164be7ce26d9599e0f85fe4
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/06/2019
ms.locfileid: "65062712"
---
# <a name="native-interoperability"></a>Interopérabilité native

Les articles suivants montrent les différentes façons d’utiliser l’« interopérabilité native » dans .NET.

Voici quelques raisons qui peuvent vous inciter à appeler du code natif :

* Les systèmes d’exploitation sont fournis avec un volume important d’API qui ne sont pas présentes dans les bibliothèques de classes managées. Un bon exemple pour ce scénario est l’accès à des fonctions de gestion de matériel ou de gestion de système d’exploitation.
* La communication avec d’autres composants qui ont ou peuvent produire des ABI de style C (ABI natifs), comme du code Java qui est exposé via l’[interface JNI (Java Native Interface)](https://docs.oracle.com/javase/8/docs/technotes/guides/jni/) ou tout autre langage managé qui peut produire un composant natif.
* Sur Windows, la plupart des logiciels qui sont installés, comme la suite Microsoft Office, inscrivent des composants COM qui représentent leurs programmes et permettent aux développeurs de les automatiser ou de les utiliser. Cela nécessite également l’interopérabilité native.

La liste précédente n’englobe pas toutes les situations et scénarios potentiels dans lesquels le développeur voudrait/aimerait/devrait interagir avec des composants natifs. La bibliothèque de classes .NET, par exemple, utilise la prise en charge de l’interopérabilité native pour implémenter un certain nombre de ses API, comme la prise en charge et la manipulation de la console, l’accès au système de fichiers, etc. Toutefois, il est important de noter qu’il existe une option si nécessaire.

> [!NOTE]
> La plupart des exemples de cette section sont présentés pour les trois plateformes prises en charge de .NET Core (Windows, Linux et Mac OS). Toutefois, pour certains exemples courts et illustratifs, seuls des noms de fichiers et des extensions Windows sont cités (par exemple, « dll » pour les bibliothèques). Cela ne signifie pas que ces fonctionnalités ne sont pas disponibles sur Linux ou Mac OS, il s’agit d’un choix purement pratique.

## <a name="see-also"></a>Voir aussi

- [Appel de code non managé (P/Invoke)](pinvoke.md)
- [Marshaling de types](type-marshaling.md)
- [Meilleures pratiques pour l’interopérabilité native](best-practices.md)
