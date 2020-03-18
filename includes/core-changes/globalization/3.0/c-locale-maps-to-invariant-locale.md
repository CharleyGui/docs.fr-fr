---
ms.openlocfilehash: d35de48dd22003c851cf5dba9e8517ec48b9217b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "74567781"
---
### <a name="c-locale-maps-to-the-invariant-locale"></a>Cartes locales "C" à l’invariant local

.NET Core 2.2 et les versions antérieures dépendent du comportement par défaut de l’USI, qui cartographie le lieu "C" au en_US_POSIX local. Le en_US_POSIX local a un comportement de collation indésirable, car il ne prend pas en charge les comparaisons de chaînes insensibles au cas. Parce que certaines distributions Linux définir le "C" local comme le lieu par défaut, les utilisateurs ont connu un comportement inattendu.

#### <a name="change-description"></a>Description de la modification

En commençant par .NET Core 3.0, la cartographie locale "C" a changé pour utiliser le local invariant au lieu de en_US_POSIX. Le local "C" à la cartographie invariante est également appliqué à Windows pour la cohérence.

La cartographie du « C » pour en_US_POSIX culture a causé la confusion des clients, parce que en_US_POSIX ne prend pas en charge les opérations insensibles de tri/de chaîne de recherche de cas. Parce que le "C" local est utilisé comme un lieu par défaut dans certains des distros Linux, les clients ont connu ce comportement indésirable sur ces systèmes d’exploitation.

#### <a name="version-introduced"></a>Version introduite

3.0

### <a name="recommended-action"></a>Action recommandée

Rien de plus spécifique que la prise de conscience de ce changement. Ce changement n’affecte que les applications qui utilisent la cartographie locale « C ».

### <a name="category"></a>Category

Globalisation

### <a name="affected-apis"></a>API affectées

Toutes les API de collation et de culture sont affectées par ce changement.

<!--

-->
