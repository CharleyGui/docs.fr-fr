---
title: Charsets et marshaling - .NET
description: Découvrez l’impact des différentes valeurs du charset sur la façon dont .NET marshale les données en code natif.
ms.date: 01/18/2019
ms.openlocfilehash: 4be4bd5a968eb5c0d6959a0f378ee1223ed906ed
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75706385"
---
# <a name="charsets-and-marshaling"></a>Charsets et marshaling

La façon dont les valeurs `char` et les objets `string` et `System.Text.StringBuilder` sont marshalés dépend de la valeur du champ `CharSet` sur P/Invoke ou la structure. Pour définir le `CharSet` d’un P/Invoke, définissez le champ <xref:System.Runtime.InteropServices.DllImportAttribute.CharSet?displayProperty=nameWithType> lorsque vous déclarez votre P/Invoke. Pour définir le `CharSet` pour un type, définissez le <xref:System.Runtime.InteropServices.StructLayoutAttribute.CharSet?displayProperty=nameWithType> champ sur votre déclaration de classe ou de struct. Lorsque ces champs d’attribut ne sont pas définis, c’est au compilateur du langage de déterminer quel `CharSet` utiliser. C# et Visual Basic utilisent le <xref:System.Runtime.InteropServices.CharSet.Ansi> jeu de caractères par défaut.

Le tableau suivant présente la correspondance entre chaque charset et la représentation d’un caractère ou d’une chaîne après marshaling avec ce charset :

| Valeur `CharSet` | Windows            | .NET Core 2.2 et antérieur sur Unix | .NET Core 3.0 et ultérieur et Mono sur Unix |
|-----------------|--------------------|-----------------------------------|------------------------------------------|
| Ansi            | `char` (page de codes [Windows (ANSI) du système par défaut](/windows/win32/intl/code-pages))      | `char` (UTF-8)                    | `char` (UTF-8)                           |
| Unicode         | `wchar_t` (UTF-16) | `char16_t` (UTF-16)               | `char16_t` (UTF-16)                      |
| Auto            | `wchar_t` (UTF-16) | `char16_t` (UTF-16)               | `char` (UTF-8)                           |

Lorsque vous choisissez votre charset, renseignez-vous sur la représentation native attendue.
