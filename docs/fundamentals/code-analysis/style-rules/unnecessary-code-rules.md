---
title: Règles de code inutiles
description: En savoir plus sur les règles de code inutiles de l’analyse du code
ms.date: 09/30/2020
ms.topic: reference
author: gewarren
ms.author: gewarren
dev_langs:
- CSharp
- VB
ms.openlocfilehash: 16c4ba0e4bee2388736bf9813a3e8290d8d4da32
ms.sourcegitcommit: 48466b8fb7332ececff5dc388f19f6b3ff503dd4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/05/2020
ms.locfileid: "96588413"
---
# <a name="unnecessary-code-rules"></a>Règles de code inutiles

Les règles de code inutiles identifient des parties différentes de la base de code qui ne sont pas nécessaires et peuvent être refactorées ou supprimées. La présence d’un code inutile indique l’un des problèmes suivants :

- Lisibilité : code qui dégrade inutilement la lisibilité. Par exemple, [IDE0001](ide0001.md) signale les qualifications de nom de type inutiles.
- Maintenabilité : le code qui n’est plus utilisé après la refactorisation et est inutilement géré. Par exemple, [IDE0051](ide0051.md) signale les champs, les propriétés, les événements et les méthodes privés inutilisés.
- Performances : calcul inutile qui n’a pas d’effets secondaires et entraîne une surcharge de performance inutile. Par exemple, [IDE0059](ide0059.md) signale les assignations de valeurs inutilisées où l’expression pour calculer une valeur n’a aucun effet secondaire.
- Fonctionnalité : problème fonctionnel dans le code conduisant à un rendu redondant du code requis. Par exemple, [IDE0060](ide0060.md) signale les paramètres inutilisés où la méthode ignore accidentellement un paramètre d’entrée.

Les règles de cette section concernent les règles de code inutiles suivantes :

- [Simplifier le nom (IDE0001)](ide0001.md)
- [Simplifier l’accès aux membres (IDE0002)](ide0002.md)
- [Supprimer le cast inutile (IDE0004)](ide0004.md)
- [Supprimer l’importation inutile (IDE0005)](ide0005.md)
- [Supprimer le code inaccessible (IDE0035)](ide0035.md)
- [Supprimer un membre privé inutilisé (IDE0051)](ide0051.md)
- [Supprimer un membre privé non lu (IDE0052)](ide0052.md)
- [Supprimer la valeur de l’expression inutilisée (IDE0058)](ide0058.md)
- [Supprimer l’assignation de valeur inutile (IDE0059)](ide0059.md)
- [Supprimer le paramètre inutilisé (IDE0060)](ide0060.md)
- [Supprimer la suppression inutile (IDE0079)](ide0079.md)
- [Supprimez l’opérateur de suppression inutile (IDE0080)](ide0080.md) -C# uniquement.
- [Supprimer « ByVal » (IDE0081)](ide0081.md) -Visual Basic uniquement.
- [Supprimer l’opérateur d’égalité inutile (IDE0100)](ide0100.md)
- [Supprimer les suppressions inutiles (IDE0110)](ide0110.md) -C# uniquement.

Certaines de ces règles comportent des options pour configurer le comportement de la règle :

- [csharp_style_unused_value_expression_statement_preference (IDE0058)](ide0058.md#csharp_style_unused_value_expression_statement_preference)
- [visual_basic_style_unused_value_expression_statement_preference (IDE0058)](ide0058.md#visual_basic_style_unused_value_expression_statement_preference)
- [csharp_style_unused_value_assignment_preference (IDE0059)](ide0059.md#csharp_style_unused_value_assignment_preference)
- [visual_basic_style_unused_value_assignment_preference (IDE0059)](ide0059.md#visual_basic_style_unused_value_assignment_preference)
- [dotnet_code_quality_unused_parameters (IDE0060)](ide0060.md#dotnet_code_quality_unused_parameters)
- [dotnet_remove_unnecessary_suppression_exclusions (IDE0079)](ide0079.md#dotnet_remove_unnecessary_suppression_exclusions)

## <a name="see-also"></a>Voir aussi

- [Règles du langage de style de code](language-rules.md)
- [Référence des règles de style de code](index.md)
