---
title: Format de fichier d’assembly .NET
description: Découvrez le format de fichier d’assembly .NET, qui sert à décrire et à contenir les bibliothèques et les applications .NET.
author: richlander
ms.date: 08/20/2019
ms.assetid: 6520323e-ff28-4c8a-ba80-e64a413199e6
ms.openlocfilehash: 1e98f0beb6756c9a02b2839eb88d6a5b13375786
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/18/2020
ms.locfileid: "94822189"
---
# <a name="net-assembly-file-format"></a>Format de fichier d’assembly .NET

.NET définit un format de fichier binaire, *assembly*, qui est utilisé pour décrire et contenir entièrement des programmes .net. Les assemblys sont utilisés pour les programmes eux-mêmes comme n’importe quelle bibliothèque dépendante. Un programme .NET peut être exécuté comme tout autre assembly, sans que d’autres artefacts soient nécessaires, en dehors de l’implémentation de .NET appropriée. Les dépendances natives, y compris les API du système d’exploitation, sont une préoccupation distincte et ne sont pas contenues dans le format d’assembly .NET, même si elles sont parfois décrites avec ce format (par exemple, WinRT).

> Chaque composant CLI inclut les métadonnées des déclarations, implémentations et références spécifiques de ce composant. Par conséquent, les métadonnées spécifiques du composant sont désignées comme les métadonnées de composant, et le composant qui en résulte est autodescriptif (d’après ECMA 335 I.9.1, Components and assemblies).

Le format est entièrement spécifié et normalisé sous [ECMA 335](https://www.ecma-international.org/publications/standards/Ecma-335.htm). Tous les compilateurs et les runtimes .NET utilisent ce format. La présence d’un format binaire documenté et rarement mis à jour a été un atout majeur (peut-être même une condition sine qua none) pour l’interopérabilité. Le format a été modifié de manière substantielle en 2005 (.NET 2.0) pour prendre en charge les génériques et l’architecture de processeur.

Le format est indépendant du processeur et du système d’exploitation. Il a été utilisé dans le cadre des implémentations de .NET qui ciblent plusieurs processeurs. Le format lui-même est hérité de Windows, il peut être implémenté sur n’importe quel système d’exploitation. La raison pour laquelle il est largement adopté pour l’interopérabilité du système d’exploitation est sans doute que la plupart des valeurs sont stockées dans un format Little Endian. Il n’a pas d’affinité particulière avec la taille du pointeur d’ordinateur (par exemple, 32 bits, 64 bits).

Le format d’assembly .NET est également très descriptif de la structure d’une bibliothèque ou d’un programme donné. Il décrit les composants internes d’un assembly, notamment les références d’assembly et les types définis et leur structure interne. Les API ou les outils peuvent lire et traiter ces informations pour l’affichage ou pour prendre des décisions de programmation.

## <a name="format"></a>Format

Le format binaire .NET est basé sur le format de [fichier PE](https://en.wikipedia.org/wiki/Portable_Executable) de Windows. En fait, les bibliothèques de classes .NET sont des fichiers Windows PE conformes qui ressemblent à première vue à des bibliothèques de liens dynamiques (DLL) Windows ou à des fichiers exécutables d’application (EXE). Il s’agit d’une caractéristique très utile dans Windows, car ces fichiers peuvent se faire passer pour des fichiers binaires exécutables natifs et recevoir le même traitement (par exemple, charge de système d’exploitation, outils PE).

![En-têtes d’assembly](../media/assembly-format/assembly-headers.png)

En-têtes d’assembly d’après ECMA 335 II.25.1, Structure of the runtime file format.

## <a name="process-the-assemblies"></a>Traiter les assemblys

Vous pouvez écrire des outils ou des API pour traiter les assemblys. Les informations d’assembly permettent de prendre des décisions de programmation au moment de l’exécution, de réécrire des assemblys, de fournir une API IntelliSense dans un éditeur et de générer de la documentation. <xref:System.Reflection?displayProperty=nameWithType>, <xref:System.Reflection.MetadataLoadContext?displayProperty=nameWithType> et [Mono.Cecil](https://www.mono-project.com/docs/tools+libraries/libraries/Mono.Cecil/) sont de bons exemples d’outils fréquemment utilisés à cet effet.
