---
title: Outil d'analyse de la composition (Mefx)
description: En savoir plus sur l’outil d’analyse de composition (Mefx), qui analyse les fichiers DLL et EXE qui contiennent des parties Managed Extensibility Framework (MEF) dans .NET.
ms.date: 03/30/2017
helpviewer_keywords:
- Composition Analysis Tool [MEF]
- MEF, Composition Analysis Tool
- Mefx [MEF], Composition Analysis Tool
ms.assetid: c48a7f93-83bb-4a06-aea0-d8e7bd1502ad
ms.openlocfilehash: a7c76bfe169a23322a5a0cdfe0d2e2e5d82f0346
ms.sourcegitcommit: 7e42488c2f8f63f6d499b5f8fb1dec5bac9ad254
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/28/2021
ms.locfileid: "98957873"
---
# <a name="composition-analysis-tool-mefx"></a>Outil d'analyse de la composition (Mefx)

L'outil d'analyse de composition (Mefx) est une application en ligne de commande qui analyse les fichiers de bibliothèque (.dll) et d'application (.exe) contenant des éléments de Managed Extensibility Framework (MEF). L'objectif principal de Mefx est d'offrir aux développeurs un moyen de diagnostiquer les échecs de composition dans leurs applications MEF sans avoir à ajouter du code de traçage encombrant à l'application elle-même. Il peut également permettre de comprendre les éléments d'une bibliothèque fournie par un tiers. Cette rubrique explique comment utiliser Mefx et fournit une référence pour sa syntaxe.  
  
<a name="getting_mefx"></a>

## <a name="getting-mefx"></a>Obtention de Mefx  

 Mefx est disponible sur GitHub à l’adresse [Managed Extensibility Framework](https://github.com/MicrosoftArchive/mef/releases/tag/4.0). Il vous suffit de télécharger l'outil et de le décompresser.  
  
<a name="basic_syntax"></a>

## <a name="basic-syntax"></a>Syntaxe de base  

 Mefx est appelé à partir de la ligne de commande au format suivant :  
  
```console
mefx [files and directories] [action] [options]  
```  
  
 Le premier jeu d'arguments spécifie les fichiers et répertoires à partir desquels charger les éléments à analyser. Spécifiez un fichier avec le commutateur `/file:` et un répertoire avec le commutateur `/directory:` . Vous pouvez spécifier plusieurs fichiers ou répertoires, comme indiqué dans l'exemple suivant :  
  
```console  
mefx /file:MyAddIn.dll /directory:Program\AddIns [action...]  
```  
  
> [!NOTE]
> Chaque .dll ou .exe ne doit être chargé qu'une seule fois. Si un fichier est chargé plusieurs fois, l'outil peut retourner des informations incorrectes.  
  
 Une fois dressée la liste des fichiers et des répertoires, vous devez spécifier une commande ainsi que toutes les options de cette commande.  
  
<a name="listing_available_parts"></a>

## <a name="listing-available-parts"></a>Liste des éléments disponibles  

 Utilisez l'action `/parts` pour répertorier tous les éléments déclarés dans les fichiers chargés. Le résultat est une simple liste de noms d'éléments.  
  
```console
mefx /file:MyAddIn.dll /parts  
MyAddIn.AddIn  
MyAddIn.MemberPart  
```  
  
 Pour plus d'informations sur les éléments, utilisez l'option `/verbose` . Vous obtiendrez ainsi plus d'informations pour tous les éléments disponibles. Pour obtenir plus d'informations sur un seul élément, utilisez l'action `/type` au lieu de `/parts`.  
  
```console  
mefx /file:MyAddIn.dll /type:MyAddIn.AddIn /verbose  
[Part] MyAddIn.MemberPart from: AssemblyCatalog (Assembly=" MyAddIn, Version=1.0.0.0, Culture=neutral, PublicKeyToken=null")  
  [Export] MyAddIn.MemberPart (ContractName=" MyAddIn.MemberPart")  
```  
  
<a name="listing_imports_and_exports"></a>

## <a name="listing-imports-and-exports"></a>Liste des importations et exportations  

 Les actions `/imports` et `/exports` répertorient tous les éléments importés et exportés, respectivement. Vous pouvez également répertorier les éléments qui importent ou exportent un type particulier à l'aide des actions `/importers` ou `/exporters` .  
  
```console  
mefx /file:MyAddIn.dll /importers:MyAddin.MemberPart  
MyAddin.AddIn  
```  
  
 Vous pouvez également appliquer l'option `/verbose` à ces actions.  
  
<a name="finding_rejected_parts"></a>

## <a name="finding-rejected-parts"></a>Recherche d'éléments rejetés  

 Une fois que Mefx a chargé les éléments disponibles, il utilise le moteur de composition MEF pour les composer. Les éléments qui ne peuvent pas être correctement composés sont les éléments *rejetés*. Pour répertorier tous les éléments rejetés, utilisez l'action `/rejected` .  
  
 Vous pouvez utiliser l'option `/verbose` avec l'action `/rejected` pour imprimer des informations détaillées sur les éléments rejetés. Dans l'exemple suivant, la DLL `ClassLibrary1` contient l'élément `AddIn` , qui importe les éléments `MemberPart` et `ChainOne` . `ChainOne` importe `ChainTwo`, mais `ChainTwo` n'existe pas. Cela signifie que `ChainOne` est rejeté, ce qui conduit au rejet de l'élément `AddIn` .  
  
```console  
mefx /file:ClassLibrary1.dll /rejected /verbose  
```  
  
 Voici la sortie complète de la commande précédente :  
  
```output
[Part] ClassLibrary1.AddIn from: AssemblyCatalog (Assembly="ClassLibrary1, Version=1.0.0.0, Culture=neutral, PublicKeyToken=null")  
  [Export] ClassLibrary1.AddIn (ContractName="ClassLibrary1.AddIn")  
  [Import] ClassLibrary1.AddIn.memberPart (ContractName="ClassLibrary1.MemberPart")  
    [SatisfiedBy] ClassLibrary1.MemberPart (ContractName="ClassLibrary1.MemberPart") from: ClassLibrary1.MemberPart from: AssemblyCatalog (Assembly="ClassLibrar  
y1, Version=1.0.0.0, Culture=neutral, PublicKeyToken=null")  
  [Import] ClassLibrary1.AddIn.chain (ContractName="ClassLibrary1.ChainOne")  
    [Exception] System.ComponentModel.Composition.ImportCardinalityMismatchException: No valid exports were found that match the constraint '((exportDefinition.ContractName == "ClassLibrary1.ChainOne") AndAlso (exportDefinition.Metadata.ContainsKey("ExportTypeIdentity") AndAlso "ClassLibrary1.ChainOne".Equals(exportDefinition.Metadata.get_Item("ExportTypeIdentity"))))', invalid exports may have been rejected.  
   at System.ComponentModel.Composition.Hosting.ExportProvider.GetExports(ImportDefinition definition, AtomicComposition atomicComposition)  
   at Microsoft.ComponentModel.Composition.Diagnostics.CompositionInfo.AnalyzeImportDefinition(ExportProvider host, IEnumerable`1 availableParts, ImportDefinition id)  
    [Unsuitable] ClassLibrary1.ChainOne (ContractName="ClassLibrary1.ChainOne")  
from: ClassLibrary1.ChainOne from: AssemblyCatalog (Assembly="ClassLibrary1, Version=1.0.0.0, Culture=neutral, PublicKeyToken=null")  
      [Because] PartDefinitionIsRejected, The part providing the export is rejected because of other issues.  
  
[Part] ClassLibrary1.ChainOne from: AssemblyCatalog (Assembly="ClassLibrary1, Version=1.0.0.0, Culture=neutral, PublicKeyToken=null")  
  [Primary Rejection]  
  [Export] ClassLibrary1.ChainOne (ContractName="ClassLibrary1.ChainOne")  
  [Import] ClassLibrary1.ChainOne.chain (ContractName="ClassLibrary1.ChainTwo")  
    [Exception] System.ComponentModel.Composition.ImportCardinalityMismatchException: No valid exports were found that match the constraint '((exportDefinition.ContractName == "ClassLibrary1.ChainTwo") AndAlso (exportDefinition.Metadata.ContainsKey("ExportTypeIdentity") AndAlso "ClassLibrary1.ChainTwo".Equals(exportDefinition.Metadata.get_Item("ExportTypeIdentity"))))', invalid exports may have been rejected.  
   at System.ComponentModel.Composition.Hosting.ExportProvider.GetExports(ImportDefinition definition, AtomicComposition atomicComposition)  
   at Microsoft.ComponentModel.Composition.Diagnostics.CompositionInfo.AnalyzeImportDefinition(ExportProvider host, IEnumerable`1 availableParts, ImportDefinition id)  
```  
  
 Les informations intéressantes sont contenues dans les résultats `[Exception]` et `[Unsuitable]` . Le résultat `[Exception]` fournit des informations sur les raisons du rejet d'un élément. Le résultat `[Unsuitable]` indique les raisons pour lesquelles un élément qui devrait correspondre ne peut pas servir à remplir une importation. Dans ce cas, c'est parce que cet élément a lui-même été rejeté en raison d'importations manquantes.  
  
<a name="analyzing_primary_causes"></a>

## <a name="analyzing-primary-causes"></a>Analyse des causes principales  

 Si plusieurs éléments sont liés dans une longue chaîne de dépendance, un problème impliquant un élément vers le bas peut entraîner le rejet de la chaîne entière. Le diagnostic de ces problèmes peut être difficile, car la cause première de l'échec n'est pas toujours évidente. Pour résoudre le problème, vous pouvez utiliser l'action `/causes` , qui tente de trouver la cause première d'un rejet en cascade.  
  
 L'utilisation de l'action `/causes` sur l'exemple précédent indique uniquement les informations relatives à `ChainOne`, dont l'importation vide est la cause première du rejet de `AddIn`. L'action `/causes` peut être utilisée dans les options normales et `/verbose` .  
  
> [!NOTE]
> Dans la plupart des cas, Mefx peut diagnostiquer la cause première d'un échec en cascade. Toutefois, dans les cas où des éléments sont ajoutés par programmation à un conteneur, les cas impliquant des conteneurs hiérarchiques ou des implémentations `ExportProvider` personnalisées, Mefx ne peut pas diagnostiquer la cause. En général, les cas décrits précédemment doivent être évités autant que possible, car les échecs sont généralement difficiles à diagnostiquer.  
  
<a name="white_lists"></a>

## <a name="allow-lists"></a>Listes verte

 L'option `/whitelist` vous permet de spécifier un fichier texte qui répertorie les éléments devant être rejetés. Les rejets inattendus seront alors signalés. Cela peut être utile lorsque vous analysez une bibliothèque incomplète ou qu’une sous-bibliothèque ne contient pas de dépendances. L'option `/whitelist` peut être appliquée aux actions `/rejected` ou `/causes` .  
  
 Supposons un fichier nommé test.txt contenant le texte « ClassLibrary1.ChainOne ». Si vous exécutez l' `/rejected` action avec l' `/whitelist` option dans l’exemple précédent, elle génère la sortie suivante :  
  
```console
mefx /file:ClassLibrary1.dll /rejected /whitelist:test.txt  
[Unexpected] ClassLibrary1.AddIn  
ClassLibrary1.ChainOne  
```
