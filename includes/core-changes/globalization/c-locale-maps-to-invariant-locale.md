---
ms.openlocfilehash: d2f24ab746c425199b5a3e0c79835da372fe8e14
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/07/2019
ms.locfileid: "72002893"
---
### <a name="c-locale-maps-to-the-invariant-locale"></a>Les paramètres régionaux « C » sont mappés aux paramètres régionaux invariants

.NET Core 2,2 et les versions antérieures dépendent du comportement ICU par défaut, qui mappe les paramètres régionaux « C » aux paramètres régionaux en_US_POSIX. Les paramètres régionaux en_US_POSIX ont un comportement de classement indésirable, car il ne prend pas en charge les comparaisons de chaînes ne respectant pas la casse. Étant donné que certaines distributions Linux définissent les paramètres régionaux « C » comme paramètres régionaux par défaut, les utilisateurs rencontraient un comportement inattendu. 

#### <a name="details"></a>Détails

À compter de .NET Core 3,0, le mappage de paramètres régionaux « C » a changé pour utiliser les paramètres régionaux invariants au lieu de en_US_POSIX. Les paramètres régionaux « C » du mappage invariant sont également appliqués à Windows pour des fins de cohérence.

Le mappage de « C » à la culture en_US_POSIX a provoqué la confusion chez les clients, car en_US_POSIX ne prend pas en charge les opérations de chaîne de tri/recherche sans respect de la casse. Étant donné que les paramètres régionaux « C » sont utilisés comme paramètres régionaux par défaut dans certains distributions Linux, les clients ont rencontré ce comportement indésirable sur ces systèmes d’exploitation. 

#### <a name="version-introduced"></a>Version introduite

3.0

### <a name="recommended-action"></a>Action recommandée

Rien de plus spécifique que la connaissance de cette modification. Cette modification affecte uniquement les applications qui utilisent le mappage de paramètres régionaux « C ».

### <a name="category"></a>Catégorie

Globalisation 

### <a name="affected-apis"></a>API affectées

Toutes les API de classement et de culture sont affectées par cette modification.

<!--

-->
