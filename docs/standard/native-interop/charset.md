---
title: Charsets et marshaling - .NET
description: Découvrez l’impact des différentes valeurs du charset sur la façon dont .NET marshale les données en code natif.
author: jkoritzinsky
ms.author: jekoritz
ms.date: 01/18/2019
ms.openlocfilehash: a29d53f8e422da1a78e131110972d83987c5464a
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/25/2019
ms.locfileid: "75337918"
---
# <a name="charsets-and-marshaling"></a>Charsets et marshaling

La façon dont les valeurs `char` et les objets `string` et `System.Text.StringBuilder` sont marshalés dépend de la valeur du champ `CharSet` sur P/Invoke ou la structure. Pour définir le `CharSet` d’un P/Invoke, définissez le champ <xref:System.Runtime.InteropServices.DllImportAttribute.CharSet?displayProperty=nameWithType> lorsque vous déclarez votre P/Invoke. Pour définir le `CharSet` pour un type, définissez le champ <xref:System.Runtime.InteropServices.StructLayoutAttribute.CharSet?displayProperty=nameWithType> sur votre déclaration de classe ou de struct. Lorsque ces champs d’attribut ne sont pas définis, c’est au compilateur du langage de déterminer quel `CharSet` utiliser. C#et Visual Basic utiliser le jeu de caractères <xref:System.Runtime.InteropServices.CharSet.Ansi> par défaut.

Le tableau suivant présente la correspondance entre chaque charset et la représentation d’un caractère ou d’une chaîne après marshaling avec ce charset :

| Valeur de `CharSet` | Portail            | .NET Core 2.2 et antérieur sur Unix | .NET Core 3.0 et ultérieur et Mono sur Unix |
|-----------------|--------------------|-----------------------------------|------------------------------------------|
| Ansi            | `char` (page de codes [Windows (ANSI) du système par défaut](/windows/win32/intl/code-pages))      | `char` (UTF-8)                    | `char` (UTF-8)                           |
| Unicode         | `wchar_t` (UTF-16) | `char16_t` (UTF-16)               | `char16_t` (UTF-16)                      |
| Auto            | `wchar_t` (UTF-16) | `char16_t` (UTF-16)               | `char` (UTF-8)                           |

Lorsque vous choisissez votre charset, renseignez-vous sur la représentation native attendue.
