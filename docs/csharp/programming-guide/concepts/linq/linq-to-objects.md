---
title: LINQ to Objects (C#)
description: En savoir plus sur LINQ to Objects en C#, qui utilise des requêtes LINQ avec n’importe quelle collection IEnumerable ou IEnumerable <T> sans fournisseur LINQ ou API intermédiaire.
ms.date: 07/20/2015
ms.assetid: c5c2c178-3529-4f6c-b3df-2d5267af7f22
ms.openlocfilehash: 575708f14487670a4371d470dcdcf650b03c3175
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91202524"
---
# <a name="linq-to-objects-c"></a>LINQ to Objects (C#)

« LINQ to Objects » fait référence à l’utilisation directe de requêtes LINQ avec n’importe quelle collection <xref:System.Collections.IEnumerable> ou <xref:System.Collections.Generic.IEnumerable%601>, sans utiliser de fournisseur LINQ ou d’API intermédiaire comme [LINQ to SQL](../../../../framework/data/adonet/sql/linq/index.md) ou [LINQ to XML](../../../../standard/linq/linq-xml-overview.md). Vous pouvez utiliser LINQ pour interroger des collections énumérables telles que <xref:System.Collections.Generic.List%601>, <xref:System.Array> ou <xref:System.Collections.Generic.Dictionary%602>. La collection peut être définie par l’utilisateur ou être retournée par une API .NET.  
  
 Fondamentalement, LINQ to Objects représente une nouvelle approche des collections. Auparavant, vous deviez écrire des boucles `foreach` complexes pour spécifier comment récupérer les données d'une collection. Avec l’approche LINQ, vous écrivez du code déclaratif qui décrit ce que vous voulez récupérer.  
  
 De plus, les requêtes LINQ offrent trois avantages principaux par rapport aux boucles `foreach` classiques :  
  
- Elles sont plus concises et lisibles, en particulier durant le filtrage de plusieurs conditions.  
  
- Elles fournissent de puissantes fonctionnalités de filtrage, de classement et de regroupement avec un minimum de code d'application.  
  
- Elles peuvent être portées vers d'autres sources de données avec peu ou pas de changements.  
  
 En général, plus l’opération que vous souhaitez effectuer sur les données est complexe, plus vous réaliserez d’avantages en utilisant LINQ au lieu des techniques d’itération traditionnelles.  
  
 Cette section a pour objectif de montrer l’approche basée sur LINQ avec quelques exemples sélectionnés. Elle n’est pas destinée à être exhaustive.  
  
## <a name="in-this-section"></a>Dans cette section  

 [LINQ et chaînes (C#)](./linq-and-strings.md)  
 Explique comment LINQ peut être utilisé pour interroger et transformer des chaînes et des collections de chaînes. Contient également des liens vers des articles qui illustrent ces principes.  
  
 [LINQ et la réflexion (C#)](how-to-query-an-assembly-s-metadata-with-reflection-linq.md)  
 Contient un lien vers un exemple qui montre comment LINQ utilise la réflexion.  
  
 [LINQ et répertoires de fichiers (C#)](./linq-and-file-directories.md)  
 Explique comment LINQ peut être utilisé pour interagir avec les systèmes de fichiers. Contient également des liens vers des articles qui illustrent ces concepts.  
  
 [Comment interroger un ArrayList avec LINQ (C#)](./how-to-query-an-arraylist-with-linq.md)  
 Montre comment interroger une ArrayList en C#.  
  
 [Comment ajouter des méthodes personnalisées pour les requêtes LINQ (C#)](./how-to-add-custom-methods-for-linq-queries.md)  
 Explique comment étendre l'ensemble des méthodes utilisables pour les requêtes LINQ en ajoutant des méthodes d'extension à l'interface <xref:System.Collections.Generic.IEnumerable%601>.  
  
 [LINQ (Language-Integrated Query) (C#)](./index.md)  
 Fournit des liens vers des articles qui expliquent LINQ et fournissent des exemples de code qui effectuent des requêtes.
