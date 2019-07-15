---
ms.openlocfilehash: c0a281b05f453b68495e6fa6fca45f3f36a204a3
ms.sourcegitcommit: d55e14eb63588830c0ba1ea95a24ce6c57ef8c8c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/11/2019
ms.locfileid: "67804571"
---
### <a name="xsd-schema-validation-now-correctly-detects-violations-of-unique-constraints-if-compound-keys-are-used-and-one-key-is-empty"></a>La validation de schéma XSD détecte désormais les violations de contraintes uniques si des clés composées sont utilisées et que l’une d’elles est vide

|   |   |
|---|---|
|Détails|Les versions du .NET Framework antérieures à 4.6 contenaient un bogue qui empêchait la validation XSD de détecter les contraintes uniques des clés composées si l’une d’elles était vide. Dans le .NET Framework 4.6, ce problème est résolu. La validation est désormais plus précise. Toutefois, il se peut que du code XML ne soit plus validé, alors qu’il l’était dans les versions précédentes.|
|Suggestion|Si une validation moins précise du .NET Framework 4.0 est nécessaire, l’application de validation peut cibler la version 4.5 (ou antérieure) du .NET Framework. Toutefois, quand vous reciblez vers .NET Framework 4.6, effectuez une revue du code pour vérifier que les clés composées en double (comme décrit plus haut) ne sont pas censées être validées.|
|Portée|Microsoft Edge|
|Version|4.6|
|Type|Reciblage|

