---
title: Datasets typés
ms.date: 03/30/2017
ms.assetid: 033d2548-cf24-4c05-8179-67d8b009c048
ms.openlocfilehash: 33876cb9f614a93cab2fa3fd9d056f94dd1e9038
ms.sourcegitcommit: 2d792961ed48f235cf413d6031576373c3050918
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/31/2019
ms.locfileid: "70203152"
---
# <a name="typed-datasets"></a>Datasets typés
En plus d'un accès par liaison tardive aux valeurs via des variables faiblement typées, l'objet <xref:System.Data.DataSet> permet un accès aux données par l'intermédiaire d'une métaphore fortement typée. Les tables et les colonnes qui font partie du **jeu de données** sont accessibles à l’aide de noms conviviaux et de variables fortement typées.  
  
 Un **DataSet** typé est une classe qui dérive d’un **DataSet**. En tant que tel, il hérite de toutes les méthodes, événements et propriétés d’un **jeu de données**. En outre, un **DataSet** typé fournit des méthodes, des événements et des propriétés fortement typés. Cela signifie que vous pouvez accéder à des tables et à des colonnes par leur nom au lieu d'utiliser les méthodes associées à des collections. Outre l’amélioration de la lisibilité du code, un **DataSet** typé permet également à l’éditeur de code Visual Studio .net de compléter automatiquement les lignes au fur et à mesure que vous tapez.  
  
 En outre, le **DataSet** fortement typé fournit l’accès aux valeurs en tant que type correct au moment de la compilation. Avec un **DataSet**fortement typé, les erreurs d’incompatibilité de types sont interceptées lorsque le code est compilé et non au moment de l’exécution.  
  
## <a name="in-this-section"></a>Dans cette section  
 [Génération de DataSets fortement typés](generating-strongly-typed-datasets.md)  
 Décrit comment créer et utiliser un **DataSet**fortement typé.  
  
 [Annotation de DataSets typés](annotating-typed-datasets.md)  
 Décrit comment annoter le schéma en langage XSD (XML Schema Definition) utilisé pour générer un **DataSet**fortement typé, afin de fournir des noms conviviaux aux éléments de **DataSet** sans altérer le schéma sous-jacent.  
  
## <a name="see-also"></a>Voir aussi

- [DataSets, DataTables et DataViews](index.md)
- [Fournisseurs managés ADO.NET et centre de développement DataSet](https://go.microsoft.com/fwlink/?LinkId=217917)
