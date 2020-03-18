---
title: Relations entre les fonctionnalités de langage et les types de bibliothèque | Microsoft Docs
description: Les fonctionnalités de langage se basent souvent sur les types de bibliothèque pour l’implémentation. Vous devez donc bien comprendre ces relations.
ms.date: 07/20/2017
ms.openlocfilehash: dfae7972af0a251a92700d7d33bd6f971eb1870e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "61706024"
---
# <a name="relationships-between-language-features-and-library-types"></a>Relations entre les fonctionnalités de langage et les types de bibliothèque

La définition du langage C# nécessite une bibliothèque standard avec certains types et certains membres accessibles sur ces types. Le compilateur génère du code qui a besoin d’utiliser ces types et membres pour de nombreuses fonctionnalités de langage différentes. Quand cela est nécessaire, il existe des packages NuGet qui contiennent tous les types à utiliser pour des versions plus récentes du langage si vous écrivez du code destiné à des environnements où ces types ou membres n’ont pas encore été déployés.

Cette dépendance sur les fonctionnalités de la bibliothèque standard fait partie du langage C# depuis le début. Dans la première version, il y avait les types suivants :

* <xref:System.Exception> : utilisé pour toutes les exceptions générées par le compilateur.
* <xref:System.String> : le type `string` C# est un synonyme de <xref:System.String>.
* <xref:System.Int32> : synonyme de `int`.

Cette première version était simple : le compilateur et la bibliothèque standard étaient fournis ensemble, et il n’y avait qu’une seule version de chacun.

Dans les versions ultérieures de C#, de nouveaux types ou membres ont parfois été ajoutés aux dépendances. Par exemple, <xref:System.Runtime.CompilerServices.INotifyCompletion>, <xref:System.Runtime.CompilerServices.CallerFilePathAttribute> et <xref:System.Runtime.CompilerServices.CallerMemberNameAttribute>. C# 7.0 poursuit dans ce sens en ajoutant une dépendance sur <xref:System.ValueTuple> pour implémenter la fonctionnalité de langage [tuples](../tuples.md).

L’équipe de conception du langage s’efforce de réduire la surface d’exposition des types et des membres requis dans une bibliothèque standard conforme. Cet objectif s’ajoute à la nécessité de conserver une conception épurée à mesure que de nouvelles fonctionnalités de bibliothèque sont incorporées au langage. De nouvelles fonctionnalités seront ajoutées dans les futures versions du langage C# qui nécessiteront de nouveaux types et membres dans une bibliothèque standard. Il est donc important de bien comprendre comment gérer ces dépendances dans votre travail.

## <a name="managing-your-dependencies"></a>Gestion des dépendances

Les outils du compilateur C# sont maintenant dissociés du cycle de mise en production des bibliothèques .NET sur les plateformes prises en charge. En effet, les bibliothèques .NET n’ont pas toutes les mêmes cycles de mise en production : le .NET Framework sur Windows est fourni en tant que mise à jour Windows Update, .NET Core est fourni selon une planification distincte, et les versions Xamarin des mises à jour de bibliothèque sont fournies avec les outils Xamarin pour chaque plateforme cible.

La plupart du temps, ces changements passeront inaperçus pour les utilisateurs. Toutefois, si vous utilisez une version du langage plus récente qui fait appel à des fonctionnalités actuellement non disponibles dans les bibliothèques .NET sur cette plateforme, vous devez référencer les packages NuGet pour fournir ces nouveaux types nécessaires.
Une fois que les plateformes prises en charge par votre application auront été mises à jour avec les nouvelles versions de framework, vous pourrez supprimer la référence ajoutée.

Grâce à cette dissociation, vous pouvez utiliser les nouvelles fonctionnalités de langage même quand vous ciblez des machines qui n’ont pas le framework approprié.
