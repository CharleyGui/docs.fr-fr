---
title: LINQ to Objects (C#)
ms.date: 07/20/2015
ms.assetid: c5c2c178-3529-4f6c-b3df-2d5267af7f22
ms.openlocfilehash: c488e49283f3e30ea729adf111fd9ca297039838
ms.sourcegitcommit: a241301495a84cc8c64fe972330d16edd619868b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/01/2020
ms.locfileid: "84241563"
---
# <a name="linq-to-objects-c"></a>LINQ to Objects (C#)
« LINQ to Objects » fait référence à l’utilisation directe de requêtes LINQ avec n’importe quelle collection <xref:System.Collections.IEnumerable> ou <xref:System.Collections.Generic.IEnumerable%601>, sans utiliser de fournisseur LINQ ou d’API intermédiaire comme [LINQ to SQL](../../../../framework/data/adonet/sql/linq/index.md) ou [LINQ to XML](./linq-to-xml-overview.md). Vous pouvez utiliser LINQ pour interroger des collections énumérables telles que <xref:System.Collections.Generic.List%601>, <xref:System.Array> ou <xref:System.Collections.Generic.Dictionary%602>. La collection peut être définie par l’utilisateur ou être retournée par une API .NET.  
  
 Fondamentalement, LINQ to Objects représente une nouvelle approche des collections. Auparavant, vous deviez écrire des boucles `foreach` complexes pour spécifier comment récupérer les données d'une collection. Avec l’approche LINQ, vous écrivez du code déclaratif qui décrit ce que vous voulez récupérer.  
  
 De plus, les requêtes LINQ offrent trois avantages principaux par rapport aux boucles `foreach` classiques :  
  
1. Elles sont plus concises et lisibles, en particulier durant le filtrage de plusieurs conditions.  
  
2. Elles fournissent de puissantes fonctionnalités de filtrage, de classement et de regroupement avec un minimum de code d'application.  
  
3. Elles peuvent être portées vers d'autres sources de données avec peu ou pas de changements.  
  
 En général, plus l’opération que vous voulez effectuer sur les données est complexe, plus vous avez intérêt à utiliser LINQ à la place des techniques d’itération classiques.  
  
 Cette section a pour objectif de montrer l’approche basée sur LINQ avec quelques exemples sélectionnés. Elle ne se veut pas exhaustive.  
  
## <a name="in-this-section"></a>Dans cette section  
 [LINQ et chaînes (C#)](./linq-and-strings.md)  
 Explique comment LINQ peut être utilisé pour interroger et transformer des chaînes et des collections de chaînes. Inclut également des liens vers les rubriques qui présentent ces principes.  
  
 [LINQ et la réflexion (C#)](how-to-query-an-assembly-s-metadata-with-reflection-linq.md)  
 Contient un lien vers un exemple qui montre comment LINQ utilise la réflexion.  
  
 [LINQ et répertoires de fichiers (C#)](./linq-and-file-directories.md)  
 Explique comment LINQ peut être utilisé pour interagir avec les systèmes de fichiers. Inclut également des liens vers les rubriques qui présentent ces concepts.  
  
 [Comment interroger un ArrayList avec LINQ (C#)](./how-to-query-an-arraylist-with-linq.md)  
 Montre comment interroger une ArrayList en C#.  
  
 [Comment ajouter des méthodes personnalisées pour les requêtes LINQ (C#)](./how-to-add-custom-methods-for-linq-queries.md)  
 Explique comment étendre l'ensemble des méthodes utilisables pour les requêtes LINQ en ajoutant des méthodes d'extension à l'interface <xref:System.Collections.Generic.IEnumerable%601>.  
  
 [LINQ (Language-Integrated Query) (C#)](./index.md)  
 Fournit des liens vers des rubriques qui présentent LINQ, ainsi que des exemples de code effectuant des requêtes.
