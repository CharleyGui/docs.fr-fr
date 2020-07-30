---
title: Comparaison entre propriétés et indexeurs - Guide de programmation C#
description: Comparez la manière dont les indexeurs en C# sont similaires aux propriétés. À l’exception des différences, les règles définies pour les accesseurs de propriété s’appliquent aux accesseurs de l’indexeur.
ms.date: 07/20/2015
helpviewer_keywords:
- properties [C#], vs. indexers
- indexers [C#], vs. properties
ms.assetid: 3358a89f-44a0-4a4d-bf8c-07237a90af39
ms.openlocfilehash: b83ce3db3d4b53fb7bcc5f3b3cd603a375d5d473
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/28/2020
ms.locfileid: "87299173"
---
# <a name="comparison-between-properties-and-indexers-c-programming-guide"></a>Comparaison entre propriétés et indexeurs (Guide de programmation C#)
Les indexeurs sont semblables aux propriétés. À l’exception des différences répertoriées dans le tableau suivant, toutes les règles définies pour les accesseurs des propriétés s’appliquent également aux accesseurs des indexeurs.  
  
|Propriété|Indexeur|  
|--------------|-------------|  
|Permet aux méthodes d’être appelées comme si elles étaient des membres de données publics.|Permet aux éléments d’une collection interne d’un objet d’être accessibles à l’aide de la notation de tableau sur l’objet lui-même.|  
|Accessible par le biais d’un nom simple.|Accessible par le biais d’un index.|  
|Peut être un membre statique ou un membre d’instance.|Doit être un membre d’instance.|  
|Un accesseur [get](../../language-reference/keywords/get.md) d’une propriété n’a aucun paramètre.|Un accesseur `get` d’un indexeur possède la même liste de paramètres formels que l’indexeur.|  
|Un accesseur [set](../../language-reference/keywords/set.md) d’une propriété contient le paramètre `value` implicite.|Un accesseur `set` d’un indexeur possède la même liste de paramètres formels que l’indexeur, outre le paramètre [value](../../language-reference/keywords/value.md).|  
|Prend en charge la syntaxe abrégée avec les [propriétés implémentées automatiquement](../classes-and-structs/auto-implemented-properties.md).|Prend en charge les membres expression-bodied pour les indexeurs get-only.|  
  
## <a name="see-also"></a>Voir aussi

- [Guide de programmation C#](../index.md)
- [Indexeurs](./index.md)
- [Propriétés](../classes-and-structs/properties.md)
