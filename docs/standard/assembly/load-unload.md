---
title: 'Comment : charger et décharger des assemblys'
description: Le CLR charge automatiquement les assemblys .NET référencés par un programme. Vous pouvez également charger dynamiquement des assemblys spécifiques dans le domaine d’application actuel.
ms.date: 08/19/2019
ms.assetid: 6a4f490f-3576-471f-9533-003737cad4a3
ms.openlocfilehash: e6f1ede055dd3f68bced4eba527b2fc65f7d5715
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/13/2020
ms.locfileid: "83378681"
---
# <a name="how-to-load-and-unload-assemblies"></a>Comment : charger et décharger des assemblys
Les assemblys référencés par votre programme sont automatiquement chargés par le common language runtime, mais il est également possible de charger dynamiquement des assemblys spécifiques dans le domaine d’application actuel. Pour plus d’informations, consultez [Comment : charger des assemblys dans un domaine d’application](../../framework/app-domains/how-to-load-assemblies-into-an-application-domain.md).

Dans .NET Framework, il n’existe aucun moyen de décharger un assembly individuel sans décharger tous les domaines d’application qui le contiennent. Même si l’assembly passe hors de portée, le fichier d’assembly proprement dit restera chargé jusqu’à ce que tous les domaines d’application qui le contiennent soient déchargés. Dans .NET Core, la <xref:System.Runtime.Loader.AssemblyLoadContext?displayProperty=nameWithType> classe gère le déchargement des assemblys. Pour plus d’informations, consultez [comment utiliser et déboguer l’inchargement d’assembly dans .net Core](unloadability.md).

## <a name="load-and-unload-assemblies"></a>Charger et décharger des assemblys

Pour charger un assembly dans un domaine d’application, utilisez l’une des nombreuses méthodes de chargement contenues dans les classes <xref:System.AppDomain> et <xref:System.Reflection.Assembly> . Pour plus d’informations, consultez [Comment : charger des assemblys dans un domaine d’application](../../framework/app-domains/how-to-load-assemblies-into-an-application-domain.md). Notez que .NET Core ne prend en charge qu’un seul domaine d’application.

Pour décharger un assembly dans le .NET Framework, vous devez décharger tous les domaines d’application qui le contiennent. Pour décharger un domaine d’application, utilisez la <xref:System.AppDomain.Unload%2A?displayProperty=nameWithType> méthode. Pour plus d’informations, consultez [Comment : décharger un domaine d’application](../../framework/app-domains/how-to-unload-an-application-domain.md).

Si vous souhaitez décharger certains assemblys, mais pas d’autres dans une application .NET Framework, vous pouvez créer un nouveau domaine d’application, exécuter le code à l’intérieur de ce domaine, puis décharger ce domaine d’application. Pour plus d’informations, consultez [Comment : décharger un domaine d’application](../../framework/app-domains/how-to-unload-an-application-domain.md).  

## <a name="see-also"></a>Voir aussi

- [Guide de programmation C#](../../csharp/programming-guide/index.md)
- [Concepts de programmation (Visual Basic)](../../visual-basic/programming-guide/concepts/index.md)
- [Assemblys dans .NET](index.md)
- [Comment : charger des assemblys dans un domaine d’application](../../framework/app-domains/how-to-load-assemblies-into-an-application-domain.md)
