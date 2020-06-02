---
title: Qu’est-ce que le code managé ?
description: Découvrez dans quelle mesure le code managé est du code dont l’exécution est gérée par un runtime, le Common Language Runtime (CLR).
ms.date: 06/20/2016
ms.technology: dotnet-standard
ms.assetid: 20bb7ea8-192e-4a96-8ef3-e10e1950fd3d
ms.openlocfilehash: 2d89fd48e4c05dc7ec7c27846a3580ee36b1886f
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84290082"
---
# <a name="what-is-managed-code"></a>Qu’est-ce que le code managé ?

Quand vous utilisez .NET Framework, vous rencontrez souvent le terme « code managé ». Ce document explique ce que signifie ce terme et fournit des informations supplémentaires sur le sujet.

Pour faire simple, le code managé est du code dont l’exécution est gérée par un runtime. Dans ce cas, le runtime en question est appelé le **Common Language Runtime** ou CLR, indépendamment de l’implémentation ([Mono](https://www.mono-project.com/) ou .NET Framework, ou .NET Core). CLR est chargé de prendre le code managé, de le compiler en code machine, puis de l’exécuter. Par ailleurs, le runtime fournit plusieurs services importants comme la gestion automatique de la mémoire, les limites de sécurité, la cohérence des types, etc.

Par opposition, le « code non managé » est la façon dont vous pouvez exécuter un programme C/C++. Dans un environnement non managé, le programmeur est responsable de presque tout. Le programme réel est, essentiellement, un fichier binaire que le système d’exploitation charge en mémoire et démarre. Tout le reste, depuis la gestion de la mémoire aux considérations de sécurité, est à la charge du programmeur.

Le code managé est écrit dans un des langages de haut niveau qui peuvent être exécutés sur .NET, tels que C#, Visual Basic ou F#. Quand vous compilez le code écrit dans ces langages avec leur compilateur respectif, vous n’obtenez pas de code machine. Vous obtenez un code en **langage intermédiaire** que le runtime compile ensuite et exécute. C++ est la seule exception à cette règle, car il peut également produire des fichiers binaires natifs, non managés qui s’exécutent sur Windows.

## <a name="intermediate-language--execution"></a>Langage intermédiaire et exécution

Qu’est-ce que le « langage intermédiaire » (ou IL en abrégé) ? Il s’agit d’un produit de compilation de code écrit dans des langages .NET de haut niveau. Quand vous compilez votre code écrit dans un de ces langages, vous obtenez un fichier binaire constitué de langage intermédiaire. Notez que le langage intermédiaire est indépendant de tout langage spécifique qui s’exécute sur le runtime. Il existe même une spécification distincte pour ce langage, que vous pouvez lire si vous le souhaitez.

Une fois que vous avez produit du langage intermédiaire à partir de votre code de haut niveau, vous pouvez l’exécuter. C’est là que le CLR intervient et démarre le processus de compilation **juste-à-temps**, ou **JIT-ing** de votre code à partir du langage intermédiaire en code machine qui peut être exécuté sur un processeur. De cette façon, le CLR sait exactement ce que votre code est en train de faire et peut donc le _gérer_ efficacement.

Le langage intermédiaire est parfois appelé langage CIL (Common Intermediate Language) ou langage MSIL (Microsoft Intermediate Language).

## <a name="unmanaged-code-interoperability"></a>Interopérabilité du code non managé

Bien entendu, le CLR permet de franchir les limites entre les environnements managé et non managé, et il y a beaucoup de code qui le fait, même dans les [bibliothèques de classes de base](framework-libraries.md). Cela s’appelle l’**interopérabilité** ou simplement **interop** en abrégé. Ces dispositions vous permettent, par exemple, d’encapsuler une bibliothèque non managée et d’y effectuer des appels. Toutefois, notez qu’une fois que vous l’avez fait, quand le code franchit les limites du runtime, la gestion réelle de l’exécution est à nouveau entre les mains du code non managé et subit donc les mêmes restrictions.

De la même manière, C# est un langage qui vous permet d’utiliser des constructions non managées comme les pointeurs directement dans le code en utilisant ce que l’on appelle le **contexte unsafe**, qui désigne un élément de code dont l’exécution n’est pas gérée par le CLR.

## <a name="more-resources"></a>Ressources complémentaires

* [Vue d’ensemble de l' .NET Framework](../framework/get-started/overview.md)
* [Pointeurs et code unsafe](../csharp/programming-guide/unsafe-code-pointers/index.md)
* [Interopérabilité native](./native-interop/index.md)
