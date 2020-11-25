---
title: 'Modification avec rupture : modification du comportement de PublishDepsFilePath'
description: Découvrez la modification avec rupture dans .NET 5,0 où la propriété MSBuild PublishDepsFilePath est vide pour les applications à fichier unique.
ms.date: 09/17/2020
ms.openlocfilehash: 70631beff31aa3388e59f3b79875ef437351451a
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95761316"
---
# <a name="publishdepsfilepath-behavior-change"></a>Changement de comportement de PublishDepsFilePath

La `PublishDepsFilePath` propriété MSBuild est vide pour les applications à fichier unique. En outre, pour les applications qui ne comportent qu’un seul fichier, le *deps.jssur* le fichier peut ne pas être copié dans le répertoire de sortie jusqu’à la version ultérieure.

## <a name="version-introduced"></a>Version introduite

5.0

## <a name="change-description"></a>Description de la modification

Dans les versions précédentes de .NET, la `PublishDepsFilePath` propriété MSBuild est le chemin d’accès à l'deps.jsde l’application *sur* le fichier dans le répertoire de sortie pour les applications à fichier unique, et un chemin d’accès dans le répertoire intermédiaire pour les applications à fichier unique.

À compter de .NET 5,0, `PublishDepsFilePath` est vide pour les applications à fichier unique et une nouvelle `IntermediateDepsFilePath` propriété spécifie le *deps.jsà* l’emplacement dans le répertoire intermédiaire. En outre, pour les applications qui ne comportent qu’un seul fichier, le *deps.jssur* le fichier peut ne pas être copié dans le répertoire de sortie (autrement dit, le chemin d’accès spécifié par `PublishDepsFilePath` ) jusqu’à la version ultérieure de la Build.

## <a name="reason-for-change"></a>Motif de modification

Cette modification a été effectuée pour deux raisons :

- En raison de la refactorisation de la logique de publication afin de prendre en charge des [applications à fichier unique améliorées](https://github.com/dotnet/designs/blob/master/accepted/2020/single-file/design.md) dans .net 5.

- Dans les applications à fichier unique, pour vous aider à vous prémunir des cibles qui essaient de réécrire le *deps.jssur* le fichier une fois que *deps.jssur* a déjà été regroupé, sans aucun impact sur l’application. Pour cette raison, `PublishDepsFilePath` est vide pour les applications à fichier unique.

## <a name="recommended-action"></a>Action recommandée

Les cibles qui réécrivent le *deps.jssur* le fichier doivent généralement le faire à l’aide de la `IntermediateDepsFilePath` propriété.

## <a name="affected-apis"></a>API affectées

N/A

<!--

### Affected APIs

Not detectable via API analysis.

### Category

MSBuild

-->
