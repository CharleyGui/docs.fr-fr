---
title: Créer un projet LINQ to DataSet dans Visual Studio
ms.date: 08/15/2018
ms.assetid: 49ba6cb0-cdd2-4571-aeaa-25bf0f40e9b3
ms.openlocfilehash: 91032766248b11e51b90aa788b1c64c140347c25
ms.sourcegitcommit: 32a575bf4adccc901f00e264f92b759ced633379
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/04/2019
ms.locfileid: "74802028"
---
# <a name="how-to-create-a-linq-to-dataset-project-in-visual-studio"></a>Comment : créer un projet LINQ to DataSet dans Visual Studio

Les différents types de projets LINQ requièrent certaines références d’assembly et les espaces de noms importésC#(Visual Basic) ou les directives [using](../../../csharp/language-reference/keywords/using-directive.md) (). La configuration minimale requise pour LINQ est une référence à *System. Core. dll* et une directive `using` pour <xref:System.Linq>.

Ces exigences sont fournies par défaut si vous créez un projet C# d’application console dans Visual Studio 2017 ou une version ultérieure. Si vous mettez à niveau un projet à partir d’une version antérieure de Visual Studio, vous devrez peut-être fournir manuellement ces références liées à LINQ.

LINQ to DataSet requiert deux références supplémentaires à *System. Data. dll* et *System. Data. DataSetExtensions. dll*.

> [!NOTE]
> Si vous effectuez une génération à partir d’une invite de commandes, vous devez référencer manuellement les dll liées à LINQ dans *%ProgramFiles%\Reference Assemblies\Microsoft\Framework\v3.5*.

## <a name="to-enable-linq-to-dataset-functionality"></a>Pour activer les fonctionnalités LINQ to DataSet

Procédez comme suit pour activer LINQ to DataSet fonctionnalité dans un projet existant.

1. Ajoutez des références à **System. Core**, **System. Data**et **System. Data. DataSetExtensions**.

   Dans **Explorateur de solutions**, cliquez avec le bouton droit sur le nœud **références** et sélectionnez **Ajouter une référence**. Dans la boîte de dialogue **Gestionnaire de références** , sélectionnez **System. Core**, **System. Data**et **System. Data. DataSetExtensions**. Sélectionnez **OK**.

1. Ajoutez des directives [using](../../../csharp/language-reference/keywords/using-directive.md) (ou des [instructions Imports](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md) dans Visual Basic) pour **System. Data** et **System. Linq**.

   ```csharp
   using System.Data;
   using System.Linq;
   ```

1. Si vous le souhaitez, ajoutez une directive `using` (ou une instruction `Imports`) pour **System. Data. Common** ou **System. Data. SqlClient**, selon la façon dont vous vous connectez à la base de données.

## <a name="see-also"></a>Voir aussi

- [Prise en main de LINQ to DataSet](getting-started-linq-to-dataset.md)
