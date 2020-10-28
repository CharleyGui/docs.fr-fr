---
title: Analyseurs de code pour .NET Framework
titleSuffix: ''
description: Découvrez comment utiliser les analyseurs dans le package des analyseurs de .NET Framework pour rechercher et résoudre les problèmes dans votre code.
author: billwagner
ms.author: wiwagn
ms.date: 10/23/2020
ms.openlocfilehash: 69dfbc9f9645c7f602ffbce46308b241c119fd96
ms.sourcegitcommit: 279fb6e8d515df51676528a7424a1df2f0917116
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2020
ms.locfileid: "92687903"
---
# <a name="code-analysis"></a>Analyse du code

Vous pouvez utiliser des analyseurs de code pour rechercher des problèmes potentiels dans votre code d’application .NET Framework. Les analyseurs détectent les problèmes potentiels et suggèrent des correctifs pour eux.

Les analyseurs de code basés sur Roslyn s’exécutent de manière interactive dans Visual Studio lorsque vous écrivez votre code ou dans le cadre d’une build d’intégration continue. Vous devez ajouter les analyseurs à votre projet le plus tôt possible dans le cycle de développement. Plus tôt vous trouvez les problèmes potentiels dans votre code, plus ils sont faciles à corriger. Les analyseurs signalent les problèmes dans le code existant et avertissent les nouveaux problèmes au fur et à mesure que vous continuez le développement.

## <a name="install-and-configure-analyzers"></a>Installer et configurer des analyseurs

L’Analyseur .NET Framework est livré dans le package NuGet [Microsoft.NetFramework.Analyzers](https://www.nuget.org/packages/Microsoft.NetFramework.Analyzers/). Ce package fournit des analyseurs spécifiques aux API .NET Framework, qui incluent des analyseurs de sécurité. Le package est inclus dans le [package Microsoft. CodeAnalysis. FxCopAnalyzers.](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers)par conséquent, si vous installez ce package, il n’est pas nécessaire d’installer les analyseurs de .NET Framework séparément.

Installez le package NuGet sur chaque projet où vous souhaitez que les analyseurs s’exécutent. Il suffit qu’un seul développeur les ajoute au projet. Le package de l’analyseur est une dépendance de projet et il s’exécute sur la machine de chaque développeur une fois qu’il dispose de la solution mise à jour.

Pour installer le package, cliquez avec le bouton droit sur le projet, puis sélectionnez « gérer les dépendances ». Dans l’Explorateur NuGet, recherchez « Microsoft. NETFramework. Analyzers ». Installez la dernière version stable dans tous les projets de votre solution.

## <a name="use-the-analyzers"></a>Utiliser les analyseurs

Une fois le package NuGet installé, générez votre solution. L’analyseur signale les éventuels problèmes qu’il trouve dans votre code base. Les problèmes sont signalés sous forme d’avertissements dans la fenêtre Liste d’erreurs de Visual Studio, comme le montre l’image suivante :

![Problèmes signalés par les analyseurs de .NET Framework.](./media/framework-analyzers-2.png)

Au fil de l’écriture du code, vous voyez des marques ondulées sous les problèmes potentiels de votre code.
Pointez sur un problème pour obtenir plus d’informations et consulter des suggestions pour tout correctif possible, comme illustré dans l’image suivante :

![Rapport interactif des problèmes détectés par les analyseurs de code.](./media/framework-analyzers-1.png)

Pour plus d’informations, consultez [analyse du code dans Visual Studio](/visualstudio/code-quality/roslyn-analyzers-overview).

## <a name="types-of-rules"></a>Types de règles

Les analyseurs examinent le code dans votre solution et les avertissements de surface avec un `CA` préfixe. Pour obtenir la liste de tous les avertissements possibles, consultez [règles de qualité du code](../fundamentals/code-analysis/quality-rules/index.md). Seuls certains de ces avertissements s’appliquent à .NET Framework API, notamment :

- [CA1058 : Les types ne doivent pas étendre certains types de base](../fundamentals/code-analysis/quality-rules/ca1058.md)

- [CA2153 : Ne pas intercepter des exceptions d’état endommagé](../fundamentals/code-analysis/quality-rules/ca2153.md)

- [CA2229 : Implémentez des constructeurs de sérialisation](../fundamentals/code-analysis/quality-rules/ca2229.md)

- [CA2235 : Marquez tous les champs non sérialisés](../fundamentals/code-analysis/quality-rules/ca2235.md)

- [CA2237 : Marquez les types ISerializable comme étant sérialisables](../fundamentals/code-analysis/quality-rules/ca2237.md)

- [CA3075 : Traitement du DTD non sécurisé dans XML](../fundamentals/code-analysis/quality-rules/ca3075.md)

- [CA5350 : n’utilisez pas d’algorithmes de chiffrement faibles](../fundamentals/code-analysis/quality-rules/ca5350.md)

- [CA5351 n’utilisez pas d’algorithmes de chiffrement rompus](../fundamentals/code-analysis/quality-rules/ca5351.md)

## <a name="see-also"></a>Voir aussi

- [Analyse du code dans Visual Studio](/visualstudio/code-quality/roslyn-analyzers-overview)
- [Analyse du code dans le kit de développement logiciel (SDK) .NET](../fundamentals/code-analysis/overview.md)
