---
title: Fichiers de configuration prédéfinis (analyse du code)
description: En savoir plus sur l’utilisation de fichiers editorconfig et d’ensembles de règles prédéfinis pour cibler des types spécifiques d’analyse du code.
ms.date: 09/24/2020
ms.topic: conceptual
ms.openlocfilehash: 4937dcab1183fa3f63be4afc71627a7c7c08c6bd
ms.sourcegitcommit: 665f8fc55258356f4d2f4a6585b750c974b26675
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/30/2020
ms.locfileid: "96587690"
---
# <a name="predefined-configuration-files"></a>Fichiers de configuration prédéfinis

Des fichiers EditorConfig et des [ensembles de règles](/visualstudio/code-quality/using-rule-sets-to-group-code-analysis-rules) prédéfinis sont disponibles, ce qui vous permet d’activer rapidement et facilement une catégorie de règles de qualité du code, telles que des règles de sécurité ou de conception. En activant une catégorie spécifique de règles, vous pouvez identifier des problèmes ciblés et des conditions spécifiques. Pour accéder à ces fichiers prédéfinis, installez le package de l’analyseur NuGet [Microsoft. CodeAnalysis. netanalyzer](https://github.com/dotnet/roslyn-analyzers#microsoftcodeanalysisnetanalyzers) .

[Microsoft. CodeAnalysis. Netanalyzers](https://github.com/dotnet/roslyn-analyzers#microsoftcodeanalysisnetanalyzers) comprend des fichiers EditorConfig prédéfinis et des ensembles de règles pour les catégories de règles suivantes :

- Toutes les règles
- Dataflow
- Conception
- Documentation
- Globalisation
- Interopérabilité
- Maintenabilité
- Dénomination
- Performances
- Porté depuis FxCop
- Fiabilité
- Sécurité
- Usage

Chacune de ces catégories de règles a un fichier de EditorConfig ou d’ensemble de règles pour :

- Activer toutes les règles de la catégorie (et désactiver toutes les autres règles)
- Utilisez la gravité par défaut de chaque règle et activez le paramètre par défaut (et désactivez toutes les autres règles).

> [!TIP]
> La catégorie « toutes les règles » dispose d’un EditorConfig ou d’un fichier d’ensemble de règles supplémentaire pour désactiver toutes les règles. Utilisez ce fichier pour supprimer rapidement les avertissements ou erreurs de l’analyseur dans un projet.

## <a name="predefined-editorconfig-files"></a>Fichiers EditorConfig prédéfinis

Les fichiers EditorConfig prédéfinis pour le package de l’analyseur Microsoft. CodeAnalysis. netanalyzer se trouvent dans le sous-répertoire *EditorConfig* de l’emplacement où le package NuGet a été installé. Par exemple, le fichier EditorConfig pour activer toutes les règles de sécurité se trouve à l’emplacement suivant : *EditorConfig/SecurityRulesEnabled/. EditorConfig*.

Copiez le fichier *. editorconfig* choisi dans le répertoire racine de votre projet.

## <a name="predefined-rule-sets"></a>Ensembles de règles prédéfinis

Les fichiers d’ensemble de règles prédéfinis pour le package de l’analyseur Microsoft. CodeAnalysis. netanalyzer sont situés *dans le sous* -répertoire RuleSet de où le package NuGet a été installé. Par exemple, le fichier d’ensemble de règles permettant d’activer toutes les règles de sécurité se trouve dans *RuleSet/SecurityRulesEnabled. RuleSet*. Copiez un ou plusieurs ensembles de règles et collez-les dans le répertoire qui contient votre projet.

## <a name="see-also"></a>Voir aussi

- [Configuration des analyseurs](https://github.com/dotnet/roslyn-analyzers/blob/master/docs/Analyzer%20Configuration.md)
- [Options de règle de style de code .NET pour EditorConfig](code-style-rule-options.md)
