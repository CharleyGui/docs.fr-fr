---
title: Récapitulatif concernant les arborescences d’expressions
description: Récapitule la façon dont vous pouvez utiliser des arborescences d’expressions pour créer des programmes dynamiques qui interprètent du code en tant que données et génèrent de nouvelles fonctionnalités en fonction de ce code.
ms.date: 06/20/2016
ms.technology: csharp-advanced-concepts
ms.assetid: eb687ebd-1149-4453-9fc1-12a084495a66
ms.openlocfilehash: 513244a987e295c81cfb5d00d9a0cfd6912074e0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79145889"
---
# <a name="expression-trees-summary"></a>Récapitulatif concernant les arborescences d’expressions

[Précédent -- Traduction d’expressions](expression-trees-translating.md)

Dans cette série, vous avez vu comment utiliser des *arborescences d’expressions* pour créer des programmes dynamiques qui interprètent du code en tant que données et génèrent de nouvelles fonctionnalités en fonction de ce code.

Vous pouvez examiner des arborescences d’expressions pour comprendre l’intention d’un algorithme. Vous pouvez non seulement examiner ce code, mais aussi créer de nouvelles arborescences d’expressions qui représentent des versions modifiées du code d’origine.

Vous pouvez également utiliser des arborescences d’expressions pour examiner un algorithme, et traduire celui-ci dans un autre langage ou environnement.

## <a name="limitations"></a>Limites

Certains éléments de langage C# récents ne se traduisent pas correctement en arborescences d’expressions. Les arborescences d’expressions ne peuvent pas contenir d’expressions `await` ou d’expressions lambda `async`. La plupart des fonctionnalités ajoutées dans la version 6 de C# n’apparaissent pas exactement telles qu’écrites dans les arborescences d’expressions. Au lieu de cela, les nouvelles fonctionnalités sont exposées dans les arborescences d’expressions dans la syntaxe antérieure équivalente. Cette limitation n’est peut-être pas aussi importante que vous pourriez le penser. En fait, elle signifie que votre code qui interprète des arborescences d’expressions continuera probablement de fonctionner de la même manière lors de l’introduction de nouvelles fonctionnalités de langage.

Même avec ces limitations, les arborescences d’expressions vous permettent de créer des algorithmes dynamiques qui reposent sur l’interprétation et la modification de code représenté sous la forme d’une structure de données. C’est un outil puissant et l’une des fonctionnalités de l’écosystème .NET qui permet aux bibliothèques enrichies telles qu’Entity Framework d’accomplir leur travail.
