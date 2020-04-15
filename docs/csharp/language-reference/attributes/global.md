---
title: 'Attributs réservés CMD : attributs mondiaux'
ms.date: 04/09/2020
description: Les attributs fournissent des métadonnées que le compilateur utilise pour comprendre plus de sémantique de votre programme
ms.openlocfilehash: f855f32cd7349da34ffbd20fededdf42c3023938
ms.sourcegitcommit: c91110ef6ee3fedb591f3d628dc17739c4a7071e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/15/2020
ms.locfileid: "81389855"
---
# <a name="reserved-attributes-assembly-level-attributes"></a>Attributs réservés : attributs de niveau d’assemblage

La plupart des attributs sont appliqués à des éléments de langage spécifiques, tels que les classes ou les méthodes. Toutefois, certains attributs sont globaux : ils s’appliquent à la totalité d’un assembly ou d’un module. Par exemple, l’attribut <xref:System.Reflection.AssemblyVersionAttribute> peut être utilisé pour incorporer des informations de version dans un assembly, de la manière suivante :

```csharp
[assembly: AssemblyVersion("1.0.0.0")]
```

Les attributs globaux apparaissent dans le `using` code source après toutes les directives de haut niveau et avant tout type, module ou déclarations d’espace de nom. Les attributs globaux peuvent apparaître dans plusieurs fichiers sources, mais les fichiers doivent être compilés en un seul passage. Visual Studio ajoute des attributs globaux au fichier AssemblyInfo.cs dans les projets cadre .NET. Ces attributs ne sont pas ajoutés aux projets .NET Core.

Les attributs d’assembly sont des valeurs qui fournissent des informations sur un assembly. Ils sont répartis dans les catégories suivantes :

- Attributs d’identité de l’assembly
- Attributs d’informations
- Attributs de manifeste de l’assembly

## <a name="assembly-identity-attributes"></a>Attributs d’identité de l’assembly

Trois attributs (avec un nom fort, le cas échéant), déterminent l’identité d’un assembly : nom, version et culture. Ces attributs constituent le nom complet de l’assembly et sont obligatoires quand vous le référencez le code. Vous pouvez définir la version et la culture d’un assembly en utilisant des attributs. Cependant, la valeur du nom est définie par le compilateur, le Visual Studio IDE dans la [boîte de dialogue d’information d’assemblage](/visualstudio/ide/reference/assembly-information-dialog-box), ou le Lien d’assemblage (Al.exe) lors de la création de l’assemblage. Le nom de l’assemblée est basé sur le manifeste d’assemblage. L’attribut <xref:System.Reflection.AssemblyFlagsAttribute> spécifie si plusieurs copies de l’assembly peuvent coexister.

Le tableau suivant présente les attributs d’identité.

|Attribut|Objectif|
|---------------|-------------|
|<xref:System.Reflection.AssemblyVersionAttribute>|Spécifie la version d’un assembly.|
|<xref:System.Reflection.AssemblyCultureAttribute>|Spécifie la culture prise en charge par l'assembly.|
|<xref:System.Reflection.AssemblyFlagsAttribute>|Spécifie si un assembly prend en charge l’exécution côte à côte sur le même ordinateur, dans le même processus ou dans le même domaine d’application.|

## <a name="informational-attributes"></a>Attributs d’informations

Vous utilisez des attributs d’information pour fournir des informations supplémentaires sur l’entreprise ou le produit d’un assemblage. Le tableau suivant présente les attributs d’informations définis dans l’espace de noms <xref:System.Reflection?displayProperty=nameWithType>.

|Attribut|Objectif|
|---------------|-------------|
|<xref:System.Reflection.AssemblyProductAttribute>|Spécifie un nom de produit pour un manifeste d’assemblage.|
|<xref:System.Reflection.AssemblyTrademarkAttribute>|Spécifie une marque de commerce pour un manifeste d’assemblage.|
|<xref:System.Reflection.AssemblyInformationalVersionAttribute>|Spécifie une version d’information pour un manifeste d’assemblage.|
|<xref:System.Reflection.AssemblyCompanyAttribute>|Spécifie un nom d’entreprise pour un manifeste d’assemblage.|
|<xref:System.Reflection.AssemblyCopyrightAttribute>|Définit un attribut personnalisé qui spécifie un copyright pour un manifeste d’assembly.|
|<xref:System.Reflection.AssemblyFileVersionAttribute>|Définit un numéro de version spécifique pour la ressource de version de fichier Win32.|
|<xref:System.CLSCompliantAttribute>|Indique si l’assembly est conforme à la spécification CLS (Common Language Specification).|

## <a name="assembly-manifest-attributes"></a>Attributs de manifeste de l’assembly

Vous pouvez utiliser les attributs de manifeste de l’assembly pour fournir des informations dans le manifeste de l’assembly. Les attributs incluent le titre, la description, l’alias par défaut et la configuration. Le tableau suivant présente les attributs de manifeste de l’assembly définis dans l’espace de noms <xref:System.Reflection?displayProperty=nameWithType>.

|Attribut|Objectif|
|---------------|-------------|
|<xref:System.Reflection.AssemblyTitleAttribute>|Spécifie un titre d’assemblage pour un manifeste d’assemblage.|
|<xref:System.Reflection.AssemblyDescriptionAttribute>|Spécifie une description d’assemblage pour un manifeste d’assemblage.|
|<xref:System.Reflection.AssemblyConfigurationAttribute>|Spécifie une configuration d’assemblage (comme la vente au détail ou le débogé) pour un manifeste d’assemblage.|
|<xref:System.Reflection.AssemblyDefaultAliasAttribute>|Définit un alias par défaut convivial pour un manifeste d’assembly.|
