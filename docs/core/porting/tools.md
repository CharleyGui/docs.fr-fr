---
title: Outils de portage vers .NET Core
description: Découvrez certains des outils que vous pouvez utiliser pour effectuer un portage vers .NET Core
author: cartermp
ms.author: mairaw
ms.date: 12/07/2018
ms.openlocfilehash: d0b74b5708f31922b72fa0e236c8bbe69ae06217
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65632255"
---
# <a name="tools-to-help-with-porting-to-net-core"></a>Outils facilitant le portage vers .NET Core

Les outils présentés dans cet article peuvent vous être utiles dans le cadre d’un portage :

* [.NET Portability Analyzer](../../standard/analyzers/portability-analyzer.md) : chaîne d’outils capable de générer un rapport sur la portabilité de votre code entre .NET Framework et .NET Core :  En tant qu’[outil en ligne de commande](https://github.com/Microsoft/dotnet-apiport/releases) En tant qu’[extension Visual Studio](https://visualstudiogallery.msdn.microsoft.com/1177943e-cfb7-4822-a8a6-e56c7905292b)
* [.NET API Analyzer](../../standard/analyzers/api-analyzer.md) : analyseur Roslyn qui découvre les risques potentiels liés à la compatibilité des API C# sur différentes plateformes et détecte les appels aux API dépréciées.

En outre, vous pouvez essayer de porter des solutions plus petites ou des projets individuels au format de fichier de projet .NET Core avec l’outil [CsprojToVs2017](https://github.com/hvanbakel/CsprojToVs2017).

> [!WARNING] 
> CsprojToVs2017 est un outil tiers. Il n’existe aucune garantie que cet outil fonctionne pour tous vos projets, et il peut entraîner de légères modifications du comportement dont vous dépendez. CsprojToVs2017 doit être utilisé comme un _point de départ_ qui automatise les tâches de base pouvant être automatisées. Ce n’est pas une solution garantie pour la migration de formats de fichiers projet.
